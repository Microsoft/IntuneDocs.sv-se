---
title: E-postinställningar för Windows 10-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa en e-postprofil för enhetskonfiguration som använder Exchange-servrar och hämtar attribut från Azure Active Directory. Du kan även aktivera SSL och synkronisera e-post och scheman på Windows 10-enheter med Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9882749ec90f2a1de4edf53535a79d893ca60e63
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72492806"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>E-postprofilinställningar för enheter som kör Windows 10 – Intune

Använd e-postprofilinställningarna till att konfigurera E-post-appen på dina enheter som kör Windows 10.

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

- **E-postadressattribut från AAD**: Välj hur e-postadressen för användaren ska skapas. Välj **UPN (User Principal Name)** (`user1@contoso.com` eller `user1`) om du vill använda det fullständiga huvudnamnet som e-postadress eller **Primär SMTP-adress** (`user1@contoso.com`) om du vill använda den primära SMTP-adressen för att logga in på Exchange.

## <a name="security-settings"></a>Säkerhetsinställningar

- **SSL**: Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.

## <a name="synchronization-settings"></a>Synkroniseringsinställningar

- **Mängd e-post att synkroniseras**: Välj antalet dagars e-post som du vill synkronisera. Eller välj **Obegränsat** om du vill synkronisera all tillgänglig e-post.
- **Synkroniseringsschema**: Välj schema för enheter för att synkronisera data från Exchange-servern. Du kan även välja **När meddelanden anländer**, som synkroniserar data så snart de anländer eller **Manuellt**, där användaren måste initiera synkroniseringen.

## <a name="content-sync-settings"></a>Synkroniseringsinställningar för innehåll

- **Innehållstyp som ska synkroniseras**: Välj vilka innehållstyper som du vill synkronisera till enheterna från:
  - **Kontakter**
  - **Kalender**
  - **aktiviteter**

## <a name="next-steps"></a>Nästa steg
[Konfigurera e-postinställningar i Intune](../email-settings-configure.md)
