---
title: Konfigurera e-postinställningarna för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista över alla e-postinställningar du kan konfigurera och lägga till för iOS-enheter i Microsoft Intune, till exempel Exchange-servrar, och hämta attribut från Azure Active Directory. Du kan även aktivera SSL, autentisera användare med certifikat eller användarnamn/lösenord och synkronisera e-post på iOS-enheter med hjälp enhetskonfigurationsprofiler i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 73de0ac94ff02e43fe73ca6357f6008ba71e3b93
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74390823"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Lägga till e-postinställningar för iOS-enheter i Microsoft Intune

I Microsoft Intune kan du skapa och konfigurera att e-posten ansluts till en e-postserver, välja hur användare autentiseras, använda S/MIME för kryptering med mera.

Den här artikeln listar och beskriver alla e-postinställningar tillgängliga för enheter som kör iOS. Du kan skapa en enhetskonfigurationsprofil att skicka eller distribuera dessa e-postinställningar till dina iOS-enheter.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](../email-settings-configure.md).

> [!NOTE]
> De här inställningarna är tillgängliga för alla registrerings typer. Mer information om registrerings typerna finns i [iOS-registrering](../ios-enroll.md).

## <a name="exchange-activesync-account-settings"></a>Inställningar för Exchange ActiveSync-konto

- **E-postserver**: Ange värdnamnet för din Exchange-server.
- **Kontonamn**: Ange visningsnamnet för e-postkontot. Namnet visas för användare på deras enheter.
- **Användarnamnattribut från AAD**: Namnet är attributet som Intune hämtar från Azure Active Directory (AAD). Intune genererar användarnamnet som används av den här profilen. Alternativen är:
  - **UPN (User Principal Name)** : Hämtar namnet, till exempel `user1` eller `user1@contoso.com`
  - **Primär SMTP-adress**: Hämtar namnet i e-postadressformat, till exempel `user1@contoso.com`
  - **sAM-kontonamn**: Kräver domänen, till exempel `domain\user1`. Ange även:  
    - **Källa för användardomännamn**: Välj **AAD** (Azure Active Directory) eller **Anpassat**.
      - **AAD**: Hämta attribut från Azure AD. Ange även:
        - **Attribut för användardomännamn från AAD**: Välj att hämta attributet för **Fullständigt domännamn** (`contoso.com`) eller **NetBIOS-namn** (`contoso`) för användaren.

      - **Anpassad**: Hämta attributen från ett eget domän namn. Ange även:
        - **Anpassat domännamn att använda**: Ange ett värde som Intune använder för domännamnet, till exempel `contoso.com` eller `contoso`.

- **E-postadressattribut från AAD**: Välj hur e-postadressen för användaren ska skapas. Alternativen är:
  - **Användarhuvudnamn**: Använd det fullständiga huvudnamnet som e-postadress, till exempel `user1@contoso.com` eller `user1`.
  - **Primär SMTP-adress**: Använd den primära SMTP-adressen för att logga in på Exchange, till exempel `user1@contoso.com`.
- **Autentiseringsmetod**: Välj hur användare ska autentiseras mot e-postservern. Alternativen är:
  - **Certifikat**: Väljer du en SCEP-klient eller PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen. Det här alternativet ger användarna en säkrare och sömlös upplevelse.
  - **Användar namn och lösen ord**: användarna uppmanas att ange sitt användar namn och lösen ord.
  - **Härledd autentiseringsuppgift**: Använd ett certifikat som härletts från en användares smartkort. Mer information finns [i Använd härledda autentiseringsuppgifter i Microsoft Intune](../protect/derived-credentials.md).

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
> Genom att konfigurera de här inställningarna distribueras en ny profil till enheten, även när en befintlig e-postprofil uppdateras för att inkludera dessa inställningar. Användarna uppmanas att ange sitt lösen ord för Exchange ActiveSync-kontot. De här inställningarna börjar gälla när lösen ordet anges.

- **Exchange-data som ska synkroniseras**: när du använder Exchange ActiveSync väljer du de Exchange-tjänster som synkroniseras på enheten: kalender, kontakter, påminnelser, anteckningar och e-post. Alternativen är:
  - **Alla data** (standard): synkronisering har Aktiver ATS för alla tjänster.
  - **Endast e-post**: synkronisering har endast Aktiver ATS för e-post. Synkronisering har inaktiverats för de andra tjänsterna.
  - **Endast kalender**: synkronisering har Aktiver ATS enbart för kalender. Synkronisering har inaktiverats för de andra tjänsterna.
  - **Endast kalender och kontakter**: synkronisering är bara aktive rad för kalender och kontakter. Synkronisering har inaktiverats för de andra tjänsterna.
  - **Endast kontakter**: synkronisering är endast aktive rad för kontakter. Synkronisering har inaktiverats för de andra tjänsterna.

  Den här funktionen gäller för:  
  - iOS 13.0 och senare
  - iPadOS 13.0 och senare

- **Tillåt användare att ändra synkroniseringsinställningar**: Välj om användarna ska kunna ändra Exchange ActiveSync-inställningarna för Exchange-tjänsterna på enheten: kalender, kontakter, påminnelser, anteckningar och e-post. Alternativen är:

  - **Ja** (standard): användare kan ändra synkroniseringen för alla tjänster. Om du väljer **Ja** kan du göra ändringar i *alla* tjänster.
  - **Nej**: användarna kan inte ändra synkroniseringsinställningar för alla tjänster. Om du väljer **inga** blockeras ändringar av *alla* tjänster.

  > [!TIP]
  > Om du konfigurerade **Exchange-data till Sync** -inställningen för att endast synkronisera vissa tjänster rekommenderar vi att du väljer **Nej** för den här inställningen. Om du väljer **Nej** förhindras användare från att ändra Exchange-tjänsten som synkroniseras.

  Den här funktionen gäller för:  
  - iOS 13.0 och senare
  - iPadOS 13.0 och senare

## <a name="exchange-activesync-email-settings"></a>E-postinställningar för Exchange ActiveSync

- **S/MIME**: s/MIME använder e-postcertifikat som ger extra säkerhet för din e-postkommunikation genom signering, kryptering och dekryptering. När du använder S/MIME med ett e-postmeddelande bekräftar du avsändarens äkthet och meddelandets integritet och sekretess.

  Alternativen är:

  - **Inaktivera S/MIME** (standard): Använd inte ett S/MIME-e-postcertifikat för att signera, kryptera eller dekryptera e-post.
  - **Aktivera S/MIME**: Tillåter användare att signera och/eller kryptera e-post i den inbyggda e-postappen i iOS. Ange även:

    - **S/MIME-signering aktive rad**: **inaktivera** (standard) tillåter inte att användare signerar meddelandet digitalt. **Aktivera** tillåter användare att digitalt signera utgående e-post för det angivna kontot. Med signering kan användare som får meddelanden vara säkra på att meddelandet kommer från den specifika avsändaren och inte från någon som låtsas vara avsändaren.
      - **Tillåt att användaren ändrar inställningen**: **Aktivera** tillåter användare att ändra signerings alternativen. **Inaktivera** (standard) förhindrar att användare ändrar signeringen och tvingar användarna att använda den signering som du har konfigurerat.
      - **Typ av signerings certifikat**: dina alternativ:
        - **Inte konfigurerad**: Intune uppdaterar eller ändrar inte den här inställningen.
        - **Ingen**: som administratör tvingar du inte ett speciellt certifikat. Välj det här alternativet så att användarna kan välja sina egna certifikat.
        - **Härledd autentiseringsuppgift**: Använd ett certifikat som härletts från en användares smartkort. Mer information finns [i Använd härledda autentiseringsuppgifter i Microsoft Intune](../protect/derived-credentials.md).
        - **Certifikat**: Välj ett befintligt PKCS- eller SCEP-certifikatprofil som används för signering av e-postmeddelanden.
      - **Tillåt att användaren ändrar inställningen**: **Aktivera** tillåter användare att ändra signerings certifikatet. **Inaktivera** (standard) förhindrar användare att ändra signeringscertifikatet och tvingar användare att använda certifikatet du har konfigurerat.

        Den här funktionen gäller för:  
        - iOS 12 och senare
        - iPadOS 12 och senare

    - **Kryptera som standard**: **Aktivera** krypterar alla meddelanden som standardbeteende. **Inaktivera** (standard) krypterar inte alla meddelanden som standardbeteende.
      - **Tillåt användare att ändra inställning**: **Aktivera** tillåter användare att ändra standardkrypteringsbeteendet. **Inaktivera** förhindrar användarna att ändra standardbeteendet för kryptering och tvingar dem att använda den kryptering du har konfigurerat.

        Den här funktionen gäller för:  
        - iOS 12 och senare
        - iPadOS 12 och senare

    - **Framtvinga kryptering per meddelande**: Med kryptering per meddelande kan användarna välja vilka e-postmeddelanden som krypteras innan de skickas.

      **Aktivera** visar alternativet för kryptering per meddelande när du skapar ett nytt e-postmeddelande. Användarna kan sedan välja eller välja bort kryptering per meddelande. Om inställningen **Kryptera som standard** också är aktiverad och kryptering per meddelande aktiveras kan användarna välja bort kryptering per meddelande.

      **Inaktivera** (standard) förhindrar att alternativet för kryptering per meddelande visas. Om inställningen **Kryptera som standard** också är aktiverad och kryptering per meddelande aktiveras kan användarna välja bort kryptering per meddelande.

      - **Krypterings certifikat typ**: dina alternativ:
        - **Inte konfigurerad**: Intune uppdaterar eller ändrar inte den här inställningen.
        - **Ingen**: som administratör tvingar du inte ett speciellt certifikat. Välj det här alternativet så att användarna kan välja sina egna certifikat.
        - **Härledd autentiseringsuppgift**: Använd ett certifikat som härletts från en användares smartkort. Mer information finns [i Använd härledda autentiseringsuppgifter i Microsoft Intune](../protect/derived-credentials.md).
        - **Certifikat**: Välj ett befintligt PKCS- eller SCEP-certifikatprofil som används för signering av e-postmeddelanden.
      - **Tillåt användare att ändra inställning**: **Aktivera** tillåter användare att ändra krypteringscertifikatet. **Inaktivera** (standard) förhindrar användare att ändra krypteringscertifikatet och tvingar användare att använda certifikatet du har konfigurerat.

        Den här funktionen gäller för:  
        - iOS 12 och senare
        - iPadOS 12 och senare

- **Mängd e-post att synkroniseras**: Välj antalet dagars e-post som du vill synkronisera. Eller välj **Obegränsat** om du vill synkronisera all tillgänglig e-post.
- **Tillåt att meddelanden flyttas till andra e-postkonton**: **Aktivera** (standard) ger användarna möjlighet att flytta e-postmeddelanden mellan olika konton som användarna har konfigurerat på sina enheter.
- **Tillåt e-postmeddelande från program från tredje part**: **Aktivera** (standard) tillåter användare att välja den här profilen som standardkonto för att skicka e-post. Det tillåter att tredjepartsprogram öppnar e-post i den interna e-postappen, t.ex. bifoga filer till e-post.
- **Synkronisera senast använda e-postadresser**: **Aktivera** (standard) låter användarna synkronisera listan över e-postadresser som nyligen har använts på enheten med servern.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).

Konfigurera e-postinställningar på [Android](../email-settings-android.md)-, [Android Enterprise](../email-settings-android-enterprise.md)-, [Windows 10](email-settings-windows-10.md)-och [Windows Phone 8,1](email-settings-windows-phone-8-1.md) -enheter.
