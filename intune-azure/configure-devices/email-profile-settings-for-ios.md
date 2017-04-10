---
title: "E-postinställningar för iOS-enheter i Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs mer om de Intune-inställningar som du kan använda för att konfigurera e-postinställningar på iOS-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9f0fa6af-3669-439a-bd0d-75d8b1a0b135
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 78f99bba07180c06f979fec997a7bfb749d879c8
ms.openlocfilehash: f18fd3ceee5c73a96444092691c590c7d9a7419c
ms.lasthandoff: 02/24/2017


---

# <a name="email-profile-settings-for-ios-devices-in-microsoft-intune"></a>E-postprofilinställningar för iOS-enheter i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **E-postserver** – Värdnamnet för din Exchange-server.
- **Kontonamn** – Visningsnamnet för e-postkontot som kommer att visas på användarnas enheter.
- **Användarnamnattribut för AAD** – Det här är attributet i Active Directory (AD) eller Azure AD som används för att generera användarnamn för den här e-postprofilen. Välj **Primär SMTP-adress**, t.ex. **user1@contoso.com** eller **Användarens huvudnamn (UPN)** som **user1** eller **user1@contoso.com**.
- **E-postadressattribut från AAD** – Hur e-postadressen för användaren på varje enhet ska skapas. Välj **Primär SMTP-adress** om du vill använda den primära SMTP-adressen för att logga in på Exchange eller använd **UPN (User Principal Name)** om du vill använda det fullständiga huvudnamnet som e-postadress.
- **Autentiseringsmetod** – Välj antingen **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som ska användas av e-postprofilen.
    - Om du valde **Certifikat**, väljer du en SCEP- eller PKCS-certifikatprofil som du har skapat tidigare och som ska användas för att autentisera Exchange-anslutningen.
- **SSL** – Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **S/MIME** – Skicka utgående e-post med S/MIME-signering.
    - Om du valde **Certifikat**, väljer du en SCEP- eller PKCS-certifikatprofil som du har skapat tidigare och som ska användas för att autentisera Exchange-anslutningen.
- **Mängd e-post som ska synkroniseras** – Välj antalet dagar med e-post som du vill synkronisera eller välj **Obegränsad** för att synkronisera alla tillgängliga e-postmeddelanden.
- **Tillåt att meddelanden flyttas till andra e-postkonton** – Detta ger användarna möjlighet att flytta e-postmeddelanden mellan olika konton som de har konfigurerat på sin enhet.
- **Tillåt att e-post skickas från tredjepartsprogram** – Tillåt att användaren väljer den här profilen som standardkonto för att skicka e-post och att appar från andra leverantörer öppnar e-post i den interna e-postappen, till exempel för att bifoga filer i e-postmeddelanden.
- **Synkronisera senast använda e-postadresser** – Det här alternativet låter användarna synkronisera listan över e-postadresser som nyligen har använts på enheten med servern.

