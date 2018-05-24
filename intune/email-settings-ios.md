---
title: E-postinställningar för iOS-enheter i Microsoft Intune
titleSuffix: ''
description: Läs om Microsoft Intune-inställningar som du kan använda för att konfigurera e-postinställningar på enheter som kör iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fe791dce88878fdbde7c62e59452a53ac08ef06b
ms.sourcegitcommit: af0cc27b05bf0743f7d0970f5f3822f0aab346af
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-ios"></a>E-postprofilinställningar i Microsoft Intune för enheter som kör iOS 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Den här artikeln visar de e-postprofilinställningar som du kan konfigurera för enheter som kör iOS.

## <a name="email-settings"></a>E-postinställningar

- **E-postserver** – Värdnamnet för din Exchange-server.
- **Kontonamn** – Visningsnamnet för e-postkontot som det visas för användare på deras enheter.
- **Användarnamnattribut för AAD** – Det här är attributet i Active Directory (AD) eller Azure AD som används för att generera användarnamn för den här e-postprofilen. Välj **Primär SMTP-adress**, t.ex. **user1@contoso.com** eller **Användarens huvudnamn (UPN)** som **user1** eller **user1@contoso.com**.
- **E-postadressattribut från AAD** – Hur e-postadressen för användaren på varje enhet ska skapas. Välj **Primär SMTP-adress** om du vill använda den primära SMTP-adressen för att logga in på Exchange eller använd **UPN (User Principal Name)** om du vill använda det fullständiga huvudnamnet som e-postadress.
- **Autentiseringsmetod** – Välj antingen **Användarnamn och lösenord** eller **Certifikat** som autentiseringsmetod som används av e-postprofilen (**Observera**: Azure-multifaktorautentisering stöds inte).
    - Om du valde **Certifikat**, väljer du en SCEP- eller PKCS-certifikatprofil som du har skapat tidigare och som ska användas för att autentisera Exchange-anslutningen.
- **SSL** – Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **S/MIME** – Skicka utgående e-post med S/MIME-signering.
    - Om du valde **Certifikat** väljer du en PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.
- **Mängd e-post som ska synkroniseras** – Välj antalet dagar med e-post som du vill synkronisera eller välj **Obegränsad** för att synkronisera alla tillgängliga e-postmeddelanden.
- **Tillåt att meddelanden flyttas till andra e-postkonton** – Detta ger användarna möjlighet att flytta e-postmeddelanden mellan olika konton som de har konfigurerat på sin enhet.
- **Tillåt att e-post skickas från tredjepartsprogram** – Tillåt att användaren väljer den här profilen som standardkonto för att skicka e-post och att appar från andra leverantörer öppnar e-post i den interna e-postappen, till exempel för att bifoga filer i e-postmeddelanden.
- **Synkronisera senast använda e-postadresser** – Det här alternativet låter användarna synkronisera listan över e-postadresser som nyligen har använts på enheten med servern.
