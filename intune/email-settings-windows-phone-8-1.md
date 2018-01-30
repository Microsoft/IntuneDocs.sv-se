---
title: "E-postinställningar för Windows Phone 8.1 i Intune"
titleSuffix: Azure portal
description: "Läs om de Intune-inställningar du kan använda för att konfigurera e-postanslutningar på Windows Phone 8.1-enheter.”"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 352d6bd9-ec8c-439e-be3a-ad3daf307df2
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 14b39932bb6bf2ee32fea8e51603fc055436dbe9
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="email-profile-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>E-postprofilinställningar för Windows Phone 8.1-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


- **Använd alla inställningar endast för Windows Phone 8.1** – Detta är en inställning som du kan konfigurera i den klassiska Intune-portalen. Den här inställningen kan inte ändras i Azure-portalen. Om inställningen anges till **Konfigurerad**, tillämpas inställningar endast på Windows Phone 8.1-enheter. Om inställningen anges till **Inte konfigurerad**, gäller de här inställningarna även för Windows 10 Mobile-enheter.
- **E-postserver** – Värdnamnet för din Exchange-server.
- **Kontonamn** – Visningsnamnet för e-postkontot som kommer att visas på användarnas enheter.
- **Användarnamnattribut för AAD** – Det här är attributet i Active Directory (AD) eller Azure AD som används för att generera användarnamn för den här e-postprofilen. Välj **Primär SMTP-adress**, t.ex. **user1@contoso.com** eller **Användarens huvudnamn (UPN)** som **user1** eller **user1@contoso.com**.
- **E-postadressattribut från AAD** – Hur e-postadressen för användaren på varje enhet ska skapas. Välj **Primär SMTP-adress** om du vill använda den primära SMTP-adressen för att logga in på Exchange eller använd **UPN (User Principal Name)** om du vill använda det fullständiga huvudnamnet som e-postadress.


## <a name="security-settings"></a>Säkerhetsinställningar

- **SSL** – Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.



## <a name="synchronization-settings"></a>Synkroniseringsinställningar

- **Mängd e-post som ska synkroniseras** – Välj antalet dagar med e-post som du vill synkronisera eller välj **Obegränsad** för att synkronisera alla tillgängliga e-postmeddelanden.
- **Synkroniseringsschema** – Välj det schema som ska användas av enheterna som ska synkronisera data från Exchange-servern. Du kan även välja **Efter hand som meddelanden kommer** varvid data synkroniseras när de anländer eller **Manuell** där enhetens användare måste starta synkroniseringen.

## <a name="content-sync-settings"></a>Synkroniseringsinställningar för innehåll

- **Innehållstyp som ska synkroniseras** – Välj vilka innehållstyper som du vill synkronisera till enheterna från:
    - **Kontakter**
    - **Kalender**
    - **aktiviteter**
