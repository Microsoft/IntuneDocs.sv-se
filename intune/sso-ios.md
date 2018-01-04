---
title: "Konfigurera enkel inloggning för Intune för iOS-enheter"
titlesuffix: Azure portal
description: "Läs mer om hur du konfigurerar enkel inloggning för Intune för iOS-enheter."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/7/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ff71239a360b09ca831a6e99f5f7a759b08f5d56
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/08/2017
---
# <a name="configure-intune-for-ios-device-single-sign-on"></a>Konfigurera enkel inloggning för Intune för iOS-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

De flesta verksamhetsspecifika appar kräver av säkerhetsskäl någon nivå av användarautentisering. I många fall måste användaren skriva samma autentiseringsuppgifter flera gånger, vilket kan vara frustrerande. För att förbättra användarupplevelsen kan utvecklare skapa appar som använder enkel inloggning och på så sätt minska antalet gånger användaren behöver ange autentiseringsuppgifterna.

För att kunna använda enkel inloggning för iOS-enheter måste du uppfylla följande villkor:

- En app måste ha kodats för att söka efter arkivet för autentiseringsuppgifter i nyttolasten för enkel inloggning på iOS-enheten.
- Intune måste ha konfigurerats för enkel inloggning för iOS-enheter.

## <a name="to-configure-intune-for-ios-device-single-sign-on"></a>Så här konfigurerar du enkel inloggning för Intune för iOS-enheter


1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
2. Välj **Profiler** på bladet **Enhetskonfiguration**.
3. På profilbladet väljer du **Skapa profil**, anger ett namn och en beskrivning och konfigurerar följande inställningar:
   - **Plattform**: Välj **iOS**. 
   - **Profiltyp**: Välj **Enhetsfunktioner**.
4. På bladet **Enhetsfunktioner** väljer du **Enkel inloggning**.

   ![Bladet Enkel inloggning](./media/sso-blade.png)

2. Ta hjälp av följande sammanfattningstabell när du fyller i fältet på bladet **Enkel inloggning**. Mer information finns i avsnitten efter tabellen.
   
   |Fält  |Anteckningar|
   |---------|---------|
   |**Användarnamnattribut från AAD**|Det attribut som Intune granskar för varje användare i AAD och som fylls i respektive fält (till exempel UPN) innan XML-nyttolasten som installeras på enheten genereras.|
   |**Område**|Domändelen i webbadressen.|
   |**URL-prefix som används för enkel inloggning**|Alla URL:er i din organisation som kräver användarautentisering med enkel inloggning|
   |**Appar som ska använda enkel inloggning**|Appar på slutanvändarens enhet som använder nyttolasten för enkel inloggning.|
   |**Förnyelsecertifikat för autentiseringsuppgifter**|Om du använder certifikat för autentisering väljer du det SCEP- eller PFX-certifikat som distribueras till användaren som autentiseringscertifikat.|

I avsnitten nedan finns mer detaljerad information om varje fält för enkel inloggning.

### <a name="username-attribute-from-aad-and-realm"></a>Användarnamnattribut från AAD och Område

- Om **Användarens unika namn** har valts för det här fältet tolkas det på följande sätt:

   ![Användarnamnattribut](media/User-name-attribute.png)

   Du kan också skriva över området med egen text i textrutan **Område**.

   Contoso kan exempelvis ha flera delområden, till exempel Europa, Asien och Nordamerika. De kanske vill att användarna i Asien ska använda SSO-nyttolasten och att UPN måste ha formatet *username@asia.contoso.com*. Om du väljer **Användarens unika namn** hämtas i det här fallet området för varje användare från AAD som bara kan vara *contoso.com*. Du kan alltså skapa den här nyttolasten särskilt för användare i Asien och skriva över området med värdet *asia.contoso.com*. Nu blir slutanvändarens UPN *username@asia.contoso.com* och inte *username@contoso.com*.

- Om du väljer **Enhets-ID** väljer Intune automatiskt ID för Intune-enhet.

   Som standard behöver appar bara använda enhets-ID. Men om din app förutom enhets-ID också använder området, kan du skriva området i textrutan **Område**.

   > [!NOTE]
   > Normalt ska du lämna området tomt om du använder enhets-ID.

### <a name="url-prefixes-that-will-use-single-sign-on"></a>URL-prefix som används för enkel inloggning

Här skriver du alla URL:er i organisationen som kräver användarautentisering.

När en användare till exempel ansluter till någon av dessa platser använder iOS-enheten autentiseringsuppgifterna för enkel inloggning och användaren behöver inte ange ytterligare autentiseringsuppgifter. Om du har aktiverat multifaktorautentisering måste användarna ange en autentisering till.

> [!NOTE]
> Dessa URL:er måste vara ett fullständigt domännamn i korrekt format. Apple kräver att dessa ska vara i formatet `http://<yourURL.domain>`

Mönster för URL-matchning måste börja med antingen `http://` eller `https://`. En enkel strängmatchning utförs, så URL-prefixet `http://www.contoso.com/` matchar inte `http://www.contoso.com:80/`. Med iOS 9.0 eller senare kan ett enskilt jokertecken * användas för att ange alla matchande värden. `http://*.contoso.com/` matchar till exempel både `http://store.contoso.com/` och `http://www.contoso.com`.
Mönstren `http://.com` och `https://.com` matchar alla HTTP- respektive HTTPS-adresser.

### <a name="apps-that-will-use-single-sign-on"></a>Appar som ska använda enkel inloggning

Ange vilka appar på slutanvändarens enhet som använder nyttolasten för enkel inloggning.

Matrisen `AppIdentifierMatches` måste innehålla strängar som matchar appsamlings-ID:n. Dessa strängar kan vara exakta matchningar (till exempel `com.contoso.myapp`) eller ange en specifik prefixmatchning för samlings-ID:t med hjälp av jokertecknet (*). Jokertecknet måste komma efter en punkt (.), och får bara förekomma en gång, i slutet av strängen (till exempel `com.contoso.*`). När ett jokertecken används beviljas alla appar vars samlings-ID börjar med prefixet åtkomst till kontot.

Fältet **Appnamn** används för att lägga till ett användarvänligt namn som hjälper dig att identifiera samlings-ID:t.

### <a name="credential-renewal-certificate"></a>Förnyelsecertifikat för autentiseringsuppgifter

Om du autentiserar slutanvändarna med certifikat (inte lösenord) använder du det här fältet för att välja det SCEP- eller PFX-certifikat som ska distribueras till användaren som autentiseringscertifikat. Vanligtvis är detta samma certifikat som distribueras till användaren för andra profiler, till exempel VPN, WiFi eller e-post.

## <a name="next-steps"></a>Nästa steg

Mer information om hur du konfigurerar funktioner för enheter finns i [Så här konfigurerar du enhetens funktionsinställningar i Microsoft Intune](device-features-configure.md).