---
title: Konfigurera e-postinställningarna för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista över alla e-postinställningar du kan konfigurera och lägga till för iOS-enheter i Microsoft Intune, till exempel Exchange-servrar, och hämta attribut från Azure Active Directory. Du kan även aktivera SSL, autentisera användare med certifikat eller användarnamn/lösenord och synkronisera e-post på iOS-enheter med hjälp enhetskonfigurationsprofiler i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4cbf9c29a1e694726b1b42f7072eea859f812751
ms.sourcegitcommit: 8c25aeefb7cbc6444a8596af22fccd1c5426877a
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72593803"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Lägga till e-postinställningar för iOS-enheter i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

I Microsoft Intune kan du skapa och konfigurera att e-posten ansluts till en e-postserver, välja hur användare autentiseras, använda S/MIME för kryptering med mera.

Den här artikeln listar och beskriver alla e-postinställningar tillgängliga för enheter som kör iOS. Du kan skapa en enhetskonfigurationsprofil att skicka eller distribuera dessa e-postinställningar till dina iOS-enheter.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](../email-settings-configure.md).

> [!NOTE]
> De här inställningarna är tillgängliga för alla registrerings typer. Mer information om registrerings typerna finns i [iOS-registrering](../ios-enroll.md).

## <a name="email-settings"></a>E-postinställningar

- **E-postserver**: Ange värdnamnet för din Exchange-server.
- **Kontonamn**: Ange visningsnamnet för e-postkontot. Namnet visas för användare på deras enheter.
- **Användarnamnattribut från AAD**: Namnet är attributet som Intune hämtar från Azure Active Directory (AAD). Intune genererar användarnamnet som används av den här profilen. Alternativen är:
  - **UPN (User Principal Name)** : Hämtar namnet, till exempel `user1` eller `user1@contoso.com`
  - **Primär SMTP-adress**: Hämtar namnet i e-postadressformat, till exempel `user1@contoso.com`
  - **sAM-kontonamn**: Kräver domänen, till exempel `domain\user1`.

    Ange även:  
    - **Källa för användardomännamn**: Välj **AAD** (Azure Active Directory) eller **Anpassat**.

      När du väljer att hämta attributen från **AAD** anger du:
      - **Attribut för användardomännamn från AAD**: Välj att hämta attributet för **Fullständigt domännamn** eller **NetBIOS-namn** för användaren

      När du väljer att använda **anpassade** attribut anger du:
      - **Anpassat domännamn att använda**: Ange ett värde som Intune använder för domännamnet, till exempel `contoso.com` eller `contoso`

- **E-postadressattribut från AAD**: Välj hur e-postadressen för användaren ska skapas. Välj **User principal name** (`user1@contoso.com` eller `user1`) för att använda det fullständiga huvudnamnet som e-postadress. Välj **Primär SMTP-adress** (`user1@contoso.com`) för att använd den primära SMTP-adressen för att logga in på Exchange.
- **Autentiseringsmetod**: Välj **Användarnamn och lösenord**, **Certifikat** eller **Härledd autentiseringsuppgift** som autentiseringsmetod för e-postprofilen. Azure-multifaktorautentisering stöds inte.
  - Om du valde **Certifikat**, väljer du en SCEP- eller PKCS-certifikatprofil som du har skapat tidigare och som ska användas för att autentisera Exchange-anslutningen.
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

- **S/MIME**: **Aktivera S/MIME** för att tillåta användare att signera och/eller kryptera e-post i den inbyggda e-postappen i iOS. 

  När du använder S/MIME med ett e-postmeddelande bekräftar du avsändarens äkthet och meddelandets integritet och sekretess.

  - **S/MIME-signering aktiverad**: Välj **Aktivera** för att tillåta användare att digitalt signera utgående e-post för det angivna kontot. Med signering kan användare som får meddelanden vara säkra på att meddelandet kommer från den specifika avsändaren och inte från någon som låtsas vara avsändaren. **Inaktivera** tillåter inte användare att digitalt signera meddelandet.
    - **Tillåt användare att ändra inställning**: Välj **Aktivera** för att tillåta användare att ändra S/MIME-signeringsbeteendet. **Inaktivera** förhindrar användarna att ändra S/MIME-signeringsinställningen du har konfigurerat. Tillgängligt i iOS 12 och senare.

  - **S/MIME-signeringscertifikat**: Välj ett befintligt PKCS- eller SCEP-certifikatprofil som används för signering av e-postmeddelanden.
    - **Tillåt användare att ändra inställning**: Välj **Aktivera** för att tillåta användare att ändra signeringscertifikatet. **Inaktivera** förhindrar användare att ändra signeringscertifikatet och tvingar användare att använda certifikatet du har konfigurerat. Tillgängligt i iOS 12 och senare.

  - **Kryptera som standard**: **Aktivera** krypterar alla meddelanden som standardbeteende. **Inaktivera** krypterar inte alla meddelanden som standardbeteende.
    - **Tillåt användare att ändra inställning**: Välj **Aktivera** för att tillåta användare att ändra standardkrypteringsbeteendet. **Inaktivera** förhindrar användarna att ändra standardbeteendet för kryptering och tvingar dem att använda den inställning du har konfigurerat. Tillgängligt i iOS 12 och senare.

  - **Framtvinga kryptering per meddelande**: Med kryptering per meddelande kan användarna välja vilka e-postmeddelanden som krypteras innan de skickas. Välj **Aktivera** för att visa alternativet för kryptering per meddelande när du skapar ett nytt e-postmeddelande. Användarna kan sedan välja eller välja bort kryptering per meddelande. **Inaktivera** förhindrar att alternativet för kryptering per meddelande visas.

    Om inställningen **Kryptera som standard** är aktiverad och kryptering per meddelande aktiveras kan användarna välja bort kryptering per meddelande. Om inställningen **Kryptera som standard** är inaktiverad och kryptering per meddelande aktiveras kan användarna välja kryptering per meddelande.

  - **S/MIME-krypteringscertifikat**: Välj ett befintligt PKCS- eller SCEP-certifikatprofil som används för kryptering av e-postmeddelanden.
    - **Tillåt användare att ändra inställning**: Välj **Aktivera** för att tillåta användare att ändra krypteringscertifikatet. **Inaktivera** förhindrar användare att ändra krypteringscertifikatet och tvingar användare att använda certifikatet du har konfigurerat. Tillgängligt i iOS 12 och senare.
- **Mängd e-post att synkroniseras**: Välj antalet dagars e-post som du vill synkronisera. Eller välj **Obegränsat** om du vill synkronisera all tillgänglig e-post.
- **Tillåt att meddelanden flyttas till andra e-postkonton**: **Aktivera** ger användarna möjlighet att flytta e-postmeddelanden mellan olika konton som användarna har konfigurerat på sina enheter.
- **Tillåt e-postmeddelande från program från tredje part**: **Aktivera** tillåter användare att välja den här profilen som standardkonto för att skicka e-post. Det tillåter att tredjepartsprogram öppnar e-post i den interna e-postappen, t.ex. bifoga filer till e-post.
- **Synkronisera senast använda e-postadresser**: **Aktivera** låter användarna synkronisera listan över e-postadresser som nyligen har använts på enheten med servern.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).

Konfigurera e-postinställningar på [Android](../email-settings-android.md)-, [Android Enterprise](../email-settings-android-enterprise.md)-, [Windows 10](email-settings-windows-10.md)-och [Windows Phone 8,1](email-settings-windows-phone-8-1.md) -enheter.
