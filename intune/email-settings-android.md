---
title: E-postinställningar för Android och Android Enterprise i Microsoft Intune – Azure | Microsoft Docs
description: Skapa e-postprofiler för en enhetskonfiguration som använder Exchange-servrar och hämta attribut från Azure Active Directory. Aktivera SSL eller SMIME, autentisera användare med certifikat eller användarnamn/lösenord, samt synkronisera e-post och scheman på Android-enheter och Android-arbetsprofilenheter med hjälp av Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: ffe25f7e4870f2ea6969d1261f33c69362d75469
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032035"
---
# <a name="android-and-android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Enhetsinställningar för Android- och Android Enterprise-enheter för att konfigurera e-post, autentisering och synkronisering i Intune

Den här artikeln beskriver de olika e-postinställningar som du kan styra på Android- och Android Enterprise-enheter. Som en del av din lösning för hantering av mobilenheter kan du använda dessa inställningar till att konfigurera en e-postserver, använda SSL för att kryptera e-postmeddelanden och mycket mer.

Som en Intune-administratör kan du skapa och tilldela e-postinställningar till följande Android-enheter:

- Android Samsung Knox Standard
- Android enterprise

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](email-settings-configure.md).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **E-postserver**: Ange värddatornamnet för din Exchange-server.
- **Kontonamn**: Ange visningsnamnet för e-postkontot. Namnet visas för användare på deras enheter.
- **Användarnamnattribut från AAD**: Namnet är det attribut som Intune hämtar från Azure Active Directory (AAD). Intune genererar användarnamnet som används av den här profilen. Alternativen är:
  - **User Principal Name**: Hämtar namnet, till exempel `user1` eller `user1@contoso.com`
  - **Användarnamn**: Hämtar enbart namnet, till exempel `user1`
  - **SAM-kontonamn**: Kräver domänen, till exempel `domain\user1`. sAM-kontonamnet kan bara användas med Android-enheter. Android enterprise stöds inte.

    Ange även:  
    - **Källa för användardomännamn**: Välj **AAD** (Azure Active Directory) eller **Anpassat**.

      När du väljer att hämta attributen från **AAD** anger du:
      - **Attribut för användardomännamn från AAD**: Välj att hämta attributet **Fullständigt domännamn** eller **NetBIOS-namn** för användaren

      När du väljer att använda **anpassade** attribut anger du:
      - **Anpassat domännamn som används**: Ange ett värde som Intune använder för domännamnet, till exempel `contoso.com` eller `contoso`

- **E-postadressattribut från AAD**: Välj hur e-postadressen för användaren ska genereras. Välj **UPN (User Principal Name)** (`user1@contoso.com` eller `user1`) om du vill använda det fullständiga huvudnamnet som e-postadress eller **Primär SMTP-adress** (`user1@contoso.com`) om du vill använda den primära SMTP-adressen för att logga in på Exchange.

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

- **Innehållstyp som ska synkroniseras:** Välj vilka typer av innehåll som enheterna ska synkroniseras från:
  - **Kontakter**
  - **Kalender**
  - **aktiviteter**

## <a name="android-enterprise"></a>Android enterprise

- **E-postapp**: Välj antingen **Gmail** eller **Nine Work**
- **E-postserver**: Värddatornamnet för din Exchange-server.
- **Användarnamnattribut från AAD**: Namnet är attributet i Active Directory (AD) eller Azure AD som används för att generera användarnamnet för den här e-postprofilen. Välj **Primär SMTP-adress**, t.ex. user1@contoso.comeller **Användarens huvudnamn (UPN)** som user1 eller user1@contoso.com.
- **E-postadressattribut från AAD**: Hur e-postadressen för användaren på varje enhet genereras. Välj **User Principal Name** för att använda det fullständiga huvudnamnet som e-postadress eller **Användarnamn**.
- **Autentiseringsmetod**: Välj antingen **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som används av e-postprofilen.
  - Om du valde **Certifikat**, väljer du en klients SCEP- eller PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.
- **SSL**: Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **Antal e-postmeddelanden som ska synkroniseras**: Ange hur många dagars e-post som ska synkroniseras, eller välj **Obegränsat** om du vill synkronisera alla tillgängliga e-postmeddelanden.
- **Innehållstyp som ska synkroniseras** (enbart Nine Work): Välj vilka typer av innehåll som enheterna ska synkroniseras från:
  - **Kontakter**
  - **Kalender**
  - **aktiviteter**

## <a name="next-steps"></a>Nästa steg
[Konfigurera e-postinställningar i Intune](email-settings-configure.md)
