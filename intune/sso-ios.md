---
title: Lägga till enkel inloggning för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: I Microsoft Intune kan du skapa, konfigurera, tillåta eller aktivera enkel inloggning (SSO) för iOS-enheter och använda det i stället för lösenord för autentisering mot din organisations resurser och data. Om du vill använda enkel inloggning skapar du en enhetskonfigurationsprofil och anger UPN, enhets-ID:t, dina appar och ett certifikat för att autentisera användaren och enheten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c4d19807ecfcc33b957d5f6582f095427dbf978e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190208"
---
# <a name="use-single-sign-on-ios-device-in-microsoft-intune"></a>Använda iOS-enheter med enkel inloggning i Microsoft Intune

De flesta verksamhetsspecifika appar kräver av säkerhetsskäl någon nivå av användarautentisering. I många fall kräver den här autentiseringen att användaren anger samma autentiseringsuppgifter flera gånger, vilket är frustrerande. För att förbättra användarupplevelsen kan utvecklare skapa appar som använder enkel inloggning (SSO) och på så sätt minska antalet gånger användaren behöver ange autentiseringsuppgifterna.

Den här artikeln beskriver hur du aktiverar enkel inloggning för iOS-enheter med hjälp av en enhetskonfigurationsprofil i Microsoft Intune.

## <a name="before-you-begin"></a>Innan du börjar

Kontrollera att du har en app som har kodats för att söka efter arkivet för autentiseringsuppgifter i nyttolasten för enkel inloggning på iOS-enheten.

## <a name="create-the-sso-profile"></a>Skapa profilen för enkel inloggning

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande inställningar:

    - **Namn**: Ange ett namn för profilen, till exempel `ios sso profile`.
    - **Beskrivning**: Ange en beskrivning med nyckeltermer som hjälper dig att hitta profilen i listan.
    - **Plattform**: Välj **iOS**.
    - **Profiltyp**: Välj **Enhetsfunktioner**.

4. Välj **Enkel inloggning**.

    ![Fönstret Enkel inloggning](./media/sso-blade.png)

5. Ange följande inställningar: 

    - **Användarnamnattribut från AAD**: Intune söker efter det här attributet för varje användare i Azure AD. Intune fyller sedan i respektive fält (till exempel UPN) innan XML-nyttolasten som installeras på enheten genereras. Alternativen är:
    
        - **Användarens huvudnamn**: UPN parsas på följande sätt:

            ![Användarnamnattribut](media/User-name-attribute.png)

            Du kan också skriva över området med texten som du anger i textrutan **Område**.

            Contoso kan exempelvis ha flera delområden, till exempel Europa, Asien och Nordamerika. De kanske vill att användarna i Asien ska använda SSO-nyttolasten och att UPN måste ha formatet `username@asia.contoso.com`. Om du väljer **Användarens unika namn** hämtas i detta fall som standard området för varje användare från Azure AD, som kanske är *contoso.com*. Du kan alltså skapa den här nyttolasten särskilt för användare i Asien och skriva över området med värdet *asia.contoso.com*. Nu blir slutanvändarens UPN username@asia.contoso.com i stället för username@contoso.com.

        - **ID för Intune-enhet**: Intune väljer automatiskt ID:t för Intune-enheten. 

            Som standard behöver appar bara använda enhets-ID. Men om din app använder området *och* enhets-ID:t kan du skriva området i textrutan **Område**.

            > [!NOTE]
            > Som standard bör du lämna området tomt om du använder enhets-ID.

    - **Område**: Domändelen i URL:en.
    
    - **URL-prefix som används för enkel inloggning**: **Lägg till** alla URL:er i din organisation som kräver användarautentisering via enkel inloggning. 

        När en användare exempelvis ansluter till någon av dessa platser använder iOS-enheten autentiseringsuppgifterna för enkel inloggning. Användaren behöver inte ange ytterligare autentiseringsuppgifter. Om du har aktiverat multifaktorautentisering måste användarna ange en autentisering till.

        > [!NOTE]
        > Dessa URL:er måste vara ett fullständigt domännamn i korrekt format. Apple kräver att URL:erna har formatet `http://<yourURL.domain>`.

        Mönster för URL-matchning måste börja med antingen `http://` eller `https://`. En enkel strängmatchning utförs, så URL-prefixet `http://www.contoso.com/` matchar inte `http://www.contoso.com:80/`. Om du har iOS 10.0 eller senare kan ett enskilt jokertecken (\*) användas för att ange alla matchande värden. `http://*.contoso.com/` matchar till exempel både `http://store.contoso.com/` och `http://www.contoso.com`.

        Mönstren `http://.com` och `https://.com` matchar alla HTTP- respektive HTTPS-adresser.
    
    - **Appar som ska använda enkel inloggning**: **Lägg till** appar på slutanvändarnas enheter som kan använda enkel inloggning. 

        Matrisen `AppIdentifierMatches` måste innehålla strängar som matchar appsamlings-ID:n. Dessa strängar kan vara exakta matchningar (till exempel `com.contoso.myapp`), eller så anger du en prefixmatchning för paket-ID:t med jokertecknet \*. Jokertecknet måste komma efter en punkt (.), och får bara förekomma en gång, i slutet av strängen (till exempel `com.contoso.*`). När ett jokertecken används beviljas alla appar vars samlings-ID börjar med prefixet åtkomst till kontot.

        Använd **appnamn** för att ange ett användarvänligt namn som hjälper dig att identifiera paket-ID:t.
    
    - **Förnyelsecertifikat för autentiseringsuppgifter**: Om du använder certifikat för autentisering (inte lösenord) väljer du det SCEP- eller PFX-certifikat som har distribuerats till användaren som autentiseringscertifikat. Vanligtvis är det här samma certifikat som distribueras till användaren för andra profiler, till exempel VPN, WiFi eller e-post.

6. Välj **OK** > **OK** > **Skapa** för att spara dina ändringar och skapa profilen. När den har skapats visas den i listan **Enhetskonfiguration – profiler**. 

## <a name="next-steps"></a>Nästa steg

Mer information om hur du konfigurerar funktioner för enheter finns i [Så här konfigurerar du enhetens funktionsinställningar i Microsoft Intune](device-features-configure.md).

[Tilldela den här profilen](device-profile-assign.md) till dina iOS-enheter.
