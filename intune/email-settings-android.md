---
title: "E-postinställningar i Microsoft Intune för enheter som kör Android och Android for Work"
titleSuffix: 
description: "Läs om Microsoft Intune-inställningar som du kan använda för att konfigurera e-postinställningar på enheter som kör Android och Android for Work."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a68607be7cbd84d5a9e9080d0a8608bce85edd22
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>E-postprofilinställningar i Microsoft Intune för enheter som kör Android och Android for Work

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som en Intune-administratör kan du skapa och tilldela e-postinställningar till följande Android-enheter:
- [Android Samsung Knox Standard](#android-samsung-knox-standard-email-settings)
- [Android for Work](#android-for-work-email-settings)

## <a name="android-samsung-knox-standard-email-settings"></a>E-postinställningar för Android Samsung Knox Standard
- **E-postserver** – Värdnamnet för din Exchange-server.
- **Kontonamn** – Visningsnamnet för e-postkontot som det visas för användare på deras enheter.
- **Användarnamn-attribut från AAD** – Det här namnet är attributet i Active Directory (AD) eller Azure AD som används för att generera användarnamnet för e-postprofilen. Välj **Primär SMTP-adress**, t.ex. user1@contoso.comeller **Användarens huvudnamn (UPN)** som user1 eller user1@contoso.com.
- **E-postadressattribut från AAD** – Hur e-postadressen för användaren på varje enhet ska skapas. Välj **Primär SMTP-adress** för att använda den primära SMTP-adressen för att logga in på Exchange eller använd **UPN (User Principal Name)** om du vill använda det fullständiga huvudnamnet som e-postadress.
- **Autentiseringsmetod** – Välj antingen **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som ska användas av e-postprofilen.
    - Om du valde **Certifikat**, väljer du en klients SCEP- eller PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.

### <a name="security-settings"></a>Säkerhetsinställningar

- **SSL** – Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **S/MIME** – Skicka utgående e-post med S/MIME-kryptering.
    - Om du valde **Certifikat**, väljer du en klients SCEP- eller PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.

### <a name="synchronization-settings"></a>Synkroniseringsinställningar

- **Mängd e-post som ska synkroniseras** – Välj antalet dagar med e-post som du vill synkronisera eller välj **Obegränsad** för att synkronisera alla tillgängliga e-postmeddelanden.
- **Synkroniseringsschema** – Välj det schema som ska användas av enheterna som ska synkronisera data från Exchange-servern. Du kan även välja **Efter hand som meddelanden kommer**, vilket synkroniserar data när den kommer eller **Manuell**, där enhetens användare måste starta synkroniseringen.

### <a name="content-sync-settings"></a>Synkroniseringsinställningar för innehåll

- **Innehållstyp som ska synkroniseras** – Välj vilka innehållstyper som du vill synkronisera till enheterna från:
    - **Kontakter**
    - **Kalender**
    - **aktiviteter**

## <a name="android-for-work-email-settings"></a>E-postinställningar för Android for Work

- **E-postapp** – välj antingen **Gmail** eller **Nine Work**
- **E-postserver** – Värdnamnet för din Exchange-server.
- **Användarnamn-attribut för AAD** – Det här namnet är attributet i Active Directory (AD) eller Azure AD, som används för att generera användarnamnet för den här e-postprofilen. Välj **Primär SMTP-adress**, t.ex. user1@contoso.comeller **Användarens huvudnamn (UPN)** som user1 eller user1@contoso.com.
- **E-postadressattribut från AAD** – Hur e-postadressen för användaren på varje enhet ska skapas. Välj **User Principal Name** för att använda det fullständiga huvudnamnet som e-postadress eller **Användarnamn**.
- **Autentiseringsmetod** – Välj antingen **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som ska användas av e-postprofilen.
    - Om du valde **Certifikat**, väljer du en klients SCEP- eller PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.
- **SSL** – Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **Mängd e-post som ska synkroniseras** – Välj antalet dagar med e-post som du vill synkronisera eller välj **Obegränsad** för att synkronisera alla tillgängliga e-postmeddelanden.
- **Innehållstyp att synkronisera** (enbart Nine Work) – välj den innehållstyp som du vill synkronisera enheter från:
    - **Kontakter**
    - **Kalender**
    - **aktiviteter**
