---
title: Konfigurera enkel inloggning till Microsoft Intune för iOS-enheter
titlesuffix: ''
description: Läs mer om att konfigurera enkel inloggning till Microsoft Intune för iOS-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1aaffb2da1f4ec081b59ff6ca1922d983008f77
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="configure-microsoft-intune-for-ios-device-single-sign-on"></a>Konfigurera enkel inloggning till Microsoft Intune för iOS-enheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

De flesta verksamhetsspecifika appar kräver av säkerhetsskäl någon nivå av användarautentisering. I många fall måste användaren skriva samma autentiseringsuppgifter flera gånger, vilket kan vara frustrerande. För att förbättra användarupplevelsen kan utvecklare skapa appar som använder enkel inloggning och på så sätt minska antalet gånger användaren behöver ange autentiseringsuppgifterna.

För att kunna använda enkel inloggning för iOS-enheter måste du uppfylla följande villkor:

- En app måste ha kodats för att söka efter arkivet för autentiseringsuppgifter i nyttolasten för enkel inloggning på iOS-enheten.
- Intune måste ha konfigurerats för enkel inloggning för iOS-enheter.

## <a name="to-configure-intune-for-ios-device-single-sign-on"></a>Så här konfigurerar du enkel inloggning för Intune för iOS-enheter


1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enhetskonfiguration**.
4. I fönstret **Enhetskonfiguration** under avsnittet **Hantera** väljer du **Profiler**.
5. I fönstret Profiler väljer du **Skapa profil**.
6. Ange ett namn och en beskrivning och konfigurera följande inställningar:
   - **Plattform**: Välj **iOS**.
   - **Profiltyp**: Välj **Enhetsfunktioner**.
7. I fönstret **Enhetsfunktioner** väljer du **Enkel inloggning**.

   ![Fönstret Enkel inloggning](./media/sso-blade.png)

8. Ta hjälp av följande sammanfattningstabell när du fyller i fälten i fönstret **Enkel inloggning**. Mer information finns i avsnitten efter tabellen.

   |Fält  |Obs!|
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

Mönster för URL-matchning måste börja med antingen `http://` eller `https://`. En enkel strängmatchning utförs, så URL-prefixet `http://www.contoso.com/` matchar inte `http://www.contoso.com:80/`. Om du har iOS 9.0 eller senare kan ett enskilt jokertecken \* användas för att ange alla matchande värden. `http://*.contoso.com/` matchar till exempel både `http://store.contoso.com/` och `http://www.contoso.com`.
Mönstren `http://.com` och `https://.com` matchar alla HTTP- respektive HTTPS-adresser.

### <a name="apps-that-will-use-single-sign-on"></a>Appar som ska använda enkel inloggning

Ange vilka appar på slutanvändarens enhet som använder nyttolasten för enkel inloggning.

Matrisen `AppIdentifierMatches` måste innehålla strängar som matchar appsamlings-ID:n. De här strängarna kan vara exakta träffar (till exempel: `com.contoso.myapp`) eller ange en prefixmatchning för samlings-ID:t med hjälp av jokertecknet \*. Jokertecknet måste komma efter en punkt (.), och får bara förekomma en gång, i slutet av strängen (till exempel `com.contoso.*`). När ett jokertecken används beviljas alla appar vars samlings-ID börjar med prefixet åtkomst till kontot.

Fältet **Appnamn** används för att lägga till ett användarvänligt namn som hjälper dig att identifiera samlings-ID:t.

### <a name="credential-renewal-certificate"></a>Förnyelsecertifikat för autentiseringsuppgifter

Om du autentiserar slutanvändarna med certifikat (inte lösenord) använder du det här fältet för att välja det SCEP- eller PFX-certifikat som ska distribueras till användaren som autentiseringscertifikat. Vanligtvis är detta samma certifikat som distribueras till användaren för andra profiler, till exempel VPN, WiFi eller e-post.

## <a name="next-steps"></a>Nästa steg

Mer information om hur du konfigurerar funktioner för enheter finns i [Så här konfigurerar du enhetens funktionsinställningar i Microsoft Intune](device-features-configure.md).
