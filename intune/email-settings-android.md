---
title: "Intune e-postinställningar för Android- och Android for Work-enheter"
titleSuffix: Azure portal
description: "Läs om de Intune-inställningar som du kan använda för att konfigurera e-postanslutningar på Android-enheter.”"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4d3458cc-fcaa-4648-b13f-bf1f0616c1c5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 436db2f645a3f2e787cb27a8c110630a8fbb1f38
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="email-profile-settings-for-android--devices-in-microsoft-intune"></a>E-postprofilinställningar för Android-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som en Intune-administratör kan du skapa och tilldela e-postinställningar till följande Android-enheter:
- [Android Samsung KNOX Standard](#android-samsung-knox-standard-email-settings)
- [Android for Work](#android-for-work-email-settings)

## <a name="android-samsung-knox-standard-email-settings"></a>E-postinställningar för Android Samsung KNOX Standard
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
