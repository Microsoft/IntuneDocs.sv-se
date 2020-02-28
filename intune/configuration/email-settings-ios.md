---
title: Konfigurera e-postinställningarna för iOS/iPadOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista över alla e-postinställningar du kan konfigurera och lägga till för iOS- och iPadOS-enheter i Microsoft Intune, t.ex. Exchange-servrar, och hämta attribut från Azure Active Directory. Du kan även aktivera SSL, autentisera användare med certifikat eller användarnamn/lösenord och synkronisera e-post på iOS/iPadOS-enheter med hjälp enhetskonfigurationsprofiler i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ea06c50b1da237d4a822e80a8085b3b51913cec
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512814"
---
# <a name="add-e-mail-settings-for-ios-and-ipados-devices-in-microsoft-intune"></a>Lägga till e-postinställningar för iOS- och iPadOS-enheter i Microsoft Intune

I Microsoft Intune kan du skapa och konfigurera att e-posten ansluts till en e-postserver, välja hur användare autentiseras, använda S/MIME för kryptering med mera.

Den här artikeln listar och beskriver alla e-postinställningar tillgängliga för enheter som kör iOS/iPadOS. Du kan skapa en enhetskonfigurationsprofil för att skicka eller distribuera dessa e-postinställningar till dina iOS/iPadOS-enheter.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](../email-settings-configure.md).

> [!NOTE]
> De här inställningarna är tillgängliga för alla registreringstyper. Mer information om de olika registreringstyperna finns i [iOS/iPadOS-registrering](../ios-enroll.md).

## <a name="exchange-activesync-account-settings"></a>Inställningar för Exchange ActiveSync-konto

- **E-postserver**: Ange värddatornamnet för din Exchange-server.
- **Kontonamn**: Ange visningsnamnet för e-postkontot. Namnet visas för användare på deras enheter.
- **Användarnamnattribut från AAD**: Namnet är det attribut som Intune hämtar från Azure Active Directory (AAD). Intune genererar användarnamnet som används av den här profilen. Alternativen är:
  - **User Principal Name**: Hämtar namnet, till exempel `user1` eller `user1@contoso.com`
  - **Primär SMTP-adress**: Hämtar namnet i e-postadressformat, som `user1@contoso.com`
  - **SAM-kontonamn**: Kräver domänen, till exempel `domain\user1`. Ange även:  
    - **Källa för användardomännamn**: Välj **AAD** (Azure Active Directory) eller **Anpassat**.
      - **AAD**: Hämta attribut från Azure AD. Ange även:
        - **Attribut för användardomännamn från AAD**: Välj att hämta attributet **Fullständigt domännamn** (`contoso.com`) eller **NetBIOS-namn** (`contoso`) för användaren.

      - **Anpassad**: Hämta attributen från ett anpassat domännamn. Ange även:
        - **Anpassat domännamn som används**: Ange ett värde som Intune använder för domännamnet, exempelvis `contoso.com` eller `contoso`.

- **E-postadressattribut från AAD**: Välj hur e-postadressen för användaren ska genereras. Alternativen är:
  - **Användarens huvudnamn (UPN)** : Använder det fullständiga huvudnamnet som e-postadress, t.ex. `user1@contoso.com` eller `user1`.
  - **Primär SMTP-adress**: Använder den primära SMTP-adressen för att logga in, t.ex. `user1@contoso.com`, för att logga in på Exchange.
- **Autentiseringsmetod**: Välj hur användarna ska autentiseras mot e-postservern. Alternativen är:
  - **Certifikat**: Välj en SCEP-klient eller PKCS-certifikatsprofil som du har skapat tidigare för att autentisera Exchange-anslutningen. Det här alternativet ger användarna en säkrare och smidigare upplevelse.
  - **Användarnamn och lösenord**: Användarna uppmanas att ange användarnamn och lösenord.
  - **Härledd autentiseringsuppgift**: Använd ett certifikat som härletts från en användares smartkort. Mer information finns i [Använd härledda autentiseringsuppgifter i Microsoft Intune](../protect/derived-credentials.md).

  >[!NOTE]
  > Azure-multifaktorautentisering stöds inte.
  
- **SSL**: **Aktivera** använder Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **OAuth**: **Aktivera** använder Open Authorization-kommunikation (OAuth) för att skicka e-post, ta emot e-post och kommunicera med Exchange. Om din OAuth-server använder certifikatautentisering väljer du **Certifikat** som **autentiseringsmetod** och inkluderar certifikatet med profilen. Annars väljer du **Användarnamn och lösenord** som **Autentiseringsmetod**. När du använder OAuth ska du se till att:

  - Bekräfta att din e-postlösning stöder OAuth innan du riktar in den här profilen på dina användare. Office 365 Exchange Online stöder OAuth. Lokalt Exchange och andra partner eller tredjepartslösningar stöder kanske inte OAuth. Lokalt Exchange kan konfigureras för modern autentisering (se blogginlägget [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) (Vi presenterar modern hybridautentisering för lokalt Exchange)).

    Om e-postprofilen använder OAuth och e-posttjänsten inte stöder det förefaller alternativet **Ange nytt lösenord** inte fungera. Till exempel händer ingenting när användaren väljer **Ange lösenordet igen** i Apples enhetsinställningar.

  - När OAuth har aktiverats har slutanvändarna en annan inloggningsfunktion för e-post med ”Modern autentisering” med stöd för multifaktorautentisering (MFA). 

  - Vissa organisationer inaktiverar slutanvändarens möjlighet att utföra [programåtkomst med självbetjäning](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). I det här scenariot kan inloggningsmetoden Modern autentisering misslyckas tills en administratör skapar företagsappen ”iOS-konton” och ger användarna åtkomst till appen i Azure AD.

    Standardåtgärden är att lägga till ett program med hjälp av den funktion i [Programåtkomstpanelen](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) som heter **Lägg till app** **utan företagsgodkännande**. Mer information finns i [tilldela användare till program](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > När du aktiverar OAuth händer följande:  
  > 1. En ny profil skickas till enheter som redan har konfigurerats som mål.
  > 2. Slutanvändarna uppmanas att ange sina autentiseringsuppgifter igen.

## <a name="exchange-activesync-profile-configuration"></a>Konfiguration av Exchange ActiveSync-profil

> [!IMPORTANT]
> Genom att konfigurera de här inställningarna distribuerar du en ny profil till enheten, även när en befintlig e-postprofil uppdateras för att inkludera de här inställningarna. Användarna uppmanas att ange sitt lösenord till sitt  Exchange ActiveSync-konto. De här inställningarna börjar gälla när lösenordet har angetts.

- **Exchange-data att synkronisera**: När du använder Exchange ActiveSync, så välj de Exchange-tjänster som ska synkroniseras på enheten: kalender, kontakter, påminnelser, anteckningar och e-post. Alternativen är:
  - **Alla data** (standard): Synkronisering har aktiverats för alla tjänster.
  - **Endast e-post**: Synkronisering har endast aktiverats för e-post. Synkronisering har inaktiverats för övriga tjänster.
  - **Endast kalender**: Synkronisering har aktiverats enbart för kalendern. Synkronisering har inaktiverats för övriga tjänster.
  - **Endast kalender och kontakter**: Synkronisering har bara aktiverats för kalender och kontakter. Synkronisering har inaktiverats för övriga tjänster.
  - **Endast kontakter**: Synkronisering har bara aktiverats för kontakter. Synkronisering har inaktiverats för övriga tjänster.

  Den här funktionen gäller för:  
  - iOS 13.0 och senare
  - iPadOS 13.0 och senare

- **Tillåt användare att ändra synkroniseringsinställningar**: Välj om användarna ska kunna ändra Exchange ActiveSync-inställningarna för enhetens Exchange-tjänster: kalender, kontakter, påminnelser, anteckningar och e-post. Alternativen är:

  - **Ja** (standard): Användare kan ändra synkroniseringen för alla tjänster. Om du väljer **Ja** tillåter du ändringar i *alla* tjänster.
  - **Nej**: Användarna kan inte ändra synkroniseringsinställningarna för alla tjänster. Om du väljer **Nej** så blockeras ändringar av *alla* tjänster.

  > [!TIP]
  > Om du konfigurerade inställningen **Exchange-data att synkronisera** till att endast synkronisera vissa tjänster, så rekommenderar vi att du väljer **Nej** för den här inställningen. Om du väljer **Nej** förhindras användare från att ändra den Exchange-tjänst som synkroniseras.

  Den här funktionen gäller för:  
  - iOS 13.0 och senare
  - iPadOS 13.0 och senare

## <a name="exchange-activesync-email-settings"></a>E-postinställningar för Exchange ActiveSync

- **S/MIME**: S/MIME använder e-postcertifikat som innebär extra säkerhet för dina e-postmeddelanden genom signering, kryptering och dekryptering. När du använder S/MIME med ett e-postmeddelande bekräftar du avsändarens äkthet och meddelandets integritet och sekretess.

  Alternativen är:

  - **Inaktivera S/MIME** (standard): Använd inte S/MIME-e-postcertifikat för att signera, kryptera eller dekryptera e-post.
  - **Aktivera S/MIME**: Tillåter användare att signera och/eller kryptera e-post i den inbyggda e-postappen i iOS/iPadOS. Ange även:

    - **S/MIME-signering aktiverad**: **Inaktivera** (standard) tillåter inte att användare signerar meddelanden digitalt. **Aktivera** tillåter användare att digitalt signera utgående e-post för det angivna kontot. Med signering kan användare som får meddelanden vara säkra på att meddelandet kommer från den specifika avsändaren och inte från någon som låtsas vara avsändaren.
      - **Tillåt användaren att ändra inställningen**: **Aktivera** tillåter användare att ändra signeringsalternativen. **Inaktivera** (standard) förhindrar användarna från att ändra signeringen och tvingar dem att använda den signering som du har konfigurerat.
      - **Typ av signeringscertifikat**: Dina alternativ:
        - **Inte konfigurerad**: Intune varken uppdaterar eller ändrar den här inställningen.
        - **Ingen**: Som administratör framtvingar du inte något speciellt certifikat. Välj det här alternativet om du vill att användarna ska kunna välja sina egna certifikat.
        - **Härledd autentiseringsuppgift**: Använd ett certifikat som härletts från en användares smartkort. Mer information finns i [Använd härledda autentiseringsuppgifter i Microsoft Intune](../protect/derived-credentials.md).
        - **Certifikat**: Välj ett befintligt PKCS- eller SCEP-certifikatprofil som används för signering av e-postmeddelanden.
      - **Tillåt att användaren ändrar inställningen**: **Aktivera** tillåter användare att ändra signeringscertifikatet. **Inaktivera** (standard) förhindrar användare att ändra signeringscertifikatet och tvingar användare att använda certifikatet du har konfigurerat.

        Den här funktionen gäller för:  
        - iOS 12 och senare
        - iPadOS 12 och senare

    - **Kryptera som standard**: **Aktivera** krypterar alla meddelanden som standardbeteende. **Inaktivera** (standard) krypterar inte alla meddelanden som standardbeteende.
      - **Tillåt användare att ändra inställning**: **Aktivera** tillåter användarna att ändra standardbeteendet för kryptering. **Inaktivera** förhindrar användarna att ändra standardbeteendet för kryptering och tvingar dem att använda den kryptering du har konfigurerat.

        Den här funktionen gäller för:  
        - iOS 12 och senare
        - iPadOS 12 och senare

    - **Framtvinga kryptering per meddelande**: Med kryptering per meddelande kan användarna välja vilka e-postmeddelanden som krypteras innan de skickas.

      **Aktivera** visar alternativet för kryptering per meddelande när du skapar ett nytt e-postmeddelande. Användarna kan sedan välja eller välja bort kryptering per meddelande. Om inställningen **Kryptera som standard** också är aktiverad och kryptering per meddelande aktiveras kan användarna välja bort kryptering per meddelande.

      **Inaktivera** (standard) förhindrar att alternativet för kryptering per meddelande visas. Om inställningen **Kryptera som standard** också är aktiverad och kryptering per meddelande aktiveras kan användarna välja bort kryptering per meddelande.

      - **Typ av krypteringscertifikat**: Dina alternativ:
        - **Inte konfigurerad**: Intune varken uppdaterar eller ändrar den här inställningen.
        - **Ingen**: Som administratör framtvingar du inte något speciellt certifikat. Välj det här alternativet om du vill att användarna ska kunna välja sina egna certifikat.
        - **Härledd autentiseringsuppgift**: Använd ett certifikat som härletts från en användares smartkort. Mer information finns i [Använd härledda autentiseringsuppgifter i Microsoft Intune](../protect/derived-credentials.md).
        - **Certifikat**: Välj ett befintligt PKCS- eller SCEP-certifikatprofil som används för signering av e-postmeddelanden.
      - **Tillåt användare att ändra inställning**: **Aktivera** tillåter användarna att ändra krypteringscertifikatet. **Inaktivera** (standard) förhindrar användare att ändra krypteringscertifikatet och tvingar användare att använda certifikatet du har konfigurerat.

        Den här funktionen gäller för:  
        - iOS 12 och senare
        - iPadOS 12 och senare

- **Antal e-postmeddelanden som ska synkroniseras**: Välj det antal dagar med e-post du vill synkronisera. Eller välj **Obegränsat** om du vill synkronisera all tillgänglig e-post.
- **Tillåt att meddelanden flyttas till andra e-postkonton**: **Aktivera** (standard) tillåter användarna att flytta e-postmeddelanden mellan olika konton som de har konfigurerat på sina enheter.
- **Tillåt att e-post skickas från tredjepartsprogram**: **Aktivera** (standard) tillåter användarna att välja den här profilen som standardkonto för att skicka e-post. Det tillåter att tredjepartsprogram öppnar e-post i den interna e-postappen, t.ex. bifoga filer till e-post.
- **Synkronisera nyligen använda e-postadresser**: **Aktivera** (standard) tillåter användarna att synkronisera listan över e-postadresser som har använts nyligen på enheten med servern.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).

Konfigurera e-postinställningar på [Android](../email-settings-android.md)-, [Android Enterprise](../email-settings-android-enterprise.md)-, [Windows 10](email-settings-windows-10.md)- och [Windows Phone 8.1](email-settings-windows-phone-8-1.md)-enheter.
