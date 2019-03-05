---
title: E-postinställningar för Android i Microsoft Intune – Azure | Microsoft Docs
description: Skapa e-postprofiler för en enhetskonfiguration som använder Exchange-servrar och hämta attribut från Azure Active Directory. Aktivera SSL eller SMIME, autentisera användare med certifikat eller användarnamn/lösenord, samt synkronisera e-post och scheman på Android-enheter och Samsung Knox-enheter med hjälp av Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53f1c95fdbdd9d779fb339e4820a3e7000573e60
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236934"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Enhetsinställningar för Android-enheter för att konfigurera e-post, autentisering och synkronisering i Intune

Den här artikeln beskriver de olika e-postinställningar som du kan styra på Android- och Samsung Knox-enheter i Intune. Som en del av din lösning för hantering av mobilenheter kan du använda dessa inställningar till att konfigurera en e-postserver, använda SSL för att kryptera e-postmeddelanden och mycket mer.

Som en Intune-administratör kan du skapa och tilldela e-postinställningar till följande Android Samsung Knox-standardenheter.

Mer information om e-postprofiler i Intune finns i [Konfigurera e-postinställningar](email-settings-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](email-settings-configure.md#create-a-device-profile).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **E-postserver**: Ange värddatornamnet för din Exchange-server. Ange till exempel `outlook.office365.com`.
- **Kontonamn**: Ange visningsnamnet för e-postkontot. Namnet visas för användare på deras enheter.
- **Användarnamnattribut från AAD**: Namnet är det attribut som Intune hämtar från Azure Active Directory (Azure AD). Intune genererar användarnamnet som används av den här profilen. Alternativen är:
  - **User Principal Name**: Hämtar namnet, till exempel `user1` eller `user1@contoso.com`
  - **Användarnamn**: Hämtar enbart namnet, till exempel `user1`
  - **SAM-kontonamn**: Kräver domänen, till exempel `domain\user1`. sAM-kontonamnet används bara med Android-enheter.

    Ange även:  
    - **Källa för användardomännamn**: Välj **AAD** (Azure Active Directory) eller **Anpassat**.

      När du väljer att hämta attributen från **AAD** anger du:
      - **Attribut för användardomännamn från AAD**: Välj att hämta attributet **Fullständigt domännamn** eller **NetBIOS-namn** för användaren

      När du väljer att använda **anpassade** attribut anger du:
      - **Anpassat domännamn som används**: Ange ett värde som Intune använder för domännamnet, till exempel `contoso.com` eller `contoso`

- **E-postadressattribut från AAD**: Det här är det e-postattributet som Intune hämtar från Azure Active Directory. Intune genererar den e-postadress som används av den här profilen. Alternativen är:
  - **Användarens huvudnamn (UPN)**:  Använder det fullständiga huvudnamnet, till exempel `user1@contoso.com` eller `user1` som e-postadress.
  - **Primär SMTP-adress**: Använder den primära SMTP-adressen, till exempel `user1@contoso.com`, för att logga in på Exchange.

- **Autentiseringsmetod**: Välj antingen **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som används av e-postprofilen.
  - Om du väljer **Certifikat** så väljer du en klients SCEP- eller PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.

### <a name="security-settings"></a>Säkerhetsinställningar

- **SSL**: Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **S/MIME**: Skicka utgående e-post med S/MIME-kryptering.
  - Om du väljer **Certifikat** så väljer du en klients SCEP- eller PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.

### <a name="synchronization-settings"></a>Synkroniseringsinställningar

- **Antal e-postmeddelanden som ska synkroniseras**: Ange hur många dagars e-post som ska synkroniseras, eller välj **Obegränsat** om du vill synkronisera alla tillgängliga e-postmeddelanden.
- **Synkroniseringsschema**: Välj det schema som ska användas av enheterna när de synkroniserar data från Exchange-servern. Du kan även välja **Efter hand som meddelanden kommer**, vilket synkroniserar data när den kommer eller **Manuell**, där enhetens användare måste starta synkroniseringen.

### <a name="content-sync-settings"></a>Synkroniseringsinställningar för innehåll

- **Innehållstyp som ska synkroniseras:** Välj vilka typer av innehåll du vill synkronisera på enheterna. **Inte konfigurerad** inaktiverar den här inställningen. När värdet **Inte konfigurerad** har valts och om en slutanvändare aktiverar synkronisering på enheten, inaktiveras synkronisering igen när enheten synkroniseras med Intune i och med att principen genomdrivs. 

  Du kan synkronisera följande innehåll:  
  - **Kontakter**: Välj **Aktivera** för att tillåta användare att synkronisera kontakter till sina enheter.
  - **Kalender**: Välj **Aktivera** för att tillåta användare att synkronisera kalendern till sina enheter.
  - **Uppgifter**: Välj **Aktivera** för att tillåta användare att synkronisera uppgifter till sina enheter.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också skapa e-postprofiler för [Android Enterprise – arbetsprofil](email-settings-android-enterprise.md), [iOS](email-settings-ios.md), [Windows 10 och senare](email-settings-windows-10.md) och [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
