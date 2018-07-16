---
title: E-postinställningar för Android- och Android-arbetsprofilenheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa en e-postprofil för enhetskonfiguration som använder Exchange-servrar och hämtar attribut från Azure Active Directory. Du kan även aktivera SSL eller SMIME, autentisera användare med certifikat eller användarnamn/lösenord och synkronisera e-post och scheman på Android- och Android-arbetsprofilenheter med hjälp av Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 136ccb6079b16c13098c1dbd6ca49e8254c14f89
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905775"
---
# <a name="email-profile-settings-for-devices-running-android-and-android-enterprise---intune"></a>E-postprofilinställningar för enheter som kör Android och Android enterprise – Intune

Använd e-postprofilinställningarna till att konfigurera dina enheter som kör Android.

Som en Intune-administratör kan du skapa och tilldela e-postinställningar till följande Android-enheter:

- Android Samsung Knox Standard
- Android enterprise

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **E-postserver**: Ange värdnamnet för din Exchange-server.
- **Kontonamn**: Ange visningsnamnet för e-postkontot. Namnet visas för användare på deras enheter.
- **Användarnamnattribut från AAD**: Namnet är attributet som Intune hämtar från Azure Active Directory (AAD). Intune genererar användarnamnet som används av den här profilen. Alternativen är:
  - **UPN (User Principal Name)**: Hämtar namnet, till exempel `user1` eller `user1@contoso.com`
  - **Användarnamn**: Hämtar bara namnet, till exempel `user1`
  - **sAM-kontonamn**: Kräver domänen, till exempel `domain\user1`. sAM-kontonamnet kan bara användas med Android-enheter. Android enterprise stöds inte.

    Ange även:  
    - **Källa för användardomännamn**: Välj **AAD** (Azure Active Directory) eller **Anpassat**.

      När du väljer att hämta attributen från **AAD** anger du:
      - **Attribut för användardomännamn från AAD**: Välj att hämta attributet för **Fullständigt domännamn** eller **NetBIOS-namn** för användaren

      När du väljer att använda **anpassade** attribut anger du:
      - **Anpassat domännamn att använda**: Ange ett värde som Intune använder för domännamnet, till exempel `contoso.com` eller `contoso`

- **E-postadressattribut från AAD**: Välj hur e-postadressen för användaren ska skapas. Välj **UPN (User Principal Name)** (`user1@contoso.com` eller `user1`) om du vill använda det fullständiga huvudnamnet som e-postadress eller **Primär SMTP-adress** (`user1@contoso.com`) om du vill använda den primära SMTP-adressen för att logga in på Exchange.

- **Autentiseringsmetod**: Välj antingen **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som ska användas av e-postprofilen.
  - Om du väljer **Certifikat** så väljer du en klients SCEP- eller PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.

### <a name="security-settings"></a>Säkerhetsinställningar

- **SSL**: Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **S/MIME**: Skicka utgående e-post med S/MIME-kryptering.
  - Om du väljer **Certifikat** så väljer du en klients SCEP- eller PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.

### <a name="synchronization-settings"></a>Synkroniseringsinställningar

- **Mängd e-post som ska synkroniseras**: Välj antalet dagar med e-post som du vill synkronisera eller välj **Obegränsad** för att synkronisera alla tillgängliga e-postmeddelanden.
- **Synkroniseringsschema**: Välj det schema som ska användas av enheterna som ska synkronisera data från Exchange-servern. Du kan även välja **Efter hand som meddelanden kommer**, vilket synkroniserar data när den kommer eller **Manuell**, där enhetens användare måste starta synkroniseringen.

### <a name="content-sync-settings"></a>Synkroniseringsinställningar för innehåll

- **Innehållstyp som ska synkroniseras**: Välj vilka innehållstyper som du vill synkronisera till enheterna från:
  - **Kontakter**
  - **Kalender**
  - **aktiviteter**

## <a name="android-enterprise"></a>Android enterprise

- **E-postapp**: Välj antingen **Gmail** eller **Nine Work**
- **E-postserver**: Värdnamnet för din Exchange-server.
- **Användarnamn-attribut för AAD**: Det här namnet är attributet i Active Directory (AD) eller Azure AD, som används för att generera användarnamnet för den här e-postprofilen. Välj **Primär SMTP-adress**, t.ex. user1@contoso.comeller **Användarens huvudnamn (UPN)** som user1 eller user1@contoso.com.
- **E-postadressattribut från AAD**: Hur e-postadressen för användaren på varje enhet ska skapas. Välj **User Principal Name** för att använda det fullständiga huvudnamnet som e-postadress eller **Användarnamn**.
- **Autentiseringsmetod**: Välj antingen **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som ska användas av e-postprofilen.
  - Om du valde **Certifikat**, väljer du en klients SCEP- eller PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.
- **SSL**: Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **Mängd e-post som ska synkroniseras**: Välj antalet dagar med e-post som du vill synkronisera eller välj **Obegränsad** för att synkronisera alla tillgängliga e-postmeddelanden.
- **Innehållstyp att synkronisera** (enbart Nine Work): välj den innehållstyp som du vill synkronisera enheter från:
  - **Kontakter**
  - **Kalender**
  - **aktiviteter**

## <a name="next-steps"></a>Nästa steg
[Konfigurera e-postinställningar i Intune](email-settings-configure.md)
