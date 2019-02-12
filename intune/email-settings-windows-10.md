---
title: E-postinställningar för Windows 10-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa en e-postprofil för enhetskonfiguration som använder Exchange-servrar och hämtar attribut från Azure Active Directory. Du kan även aktivera SSL och synkronisera e-post och scheman på Windows 10-enheter med Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bf9581fe81aea3d2671da0adb2d37bbc203875c8
ms.sourcegitcommit: 4bd992da609b8bcc85edc2d64fe8128546aa4617
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2019
ms.locfileid: "55303539"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>E-postprofilinställningar för enheter som kör Windows 10 – Intune

Använd e-postprofilinställningarna till att konfigurera E-post-appen på dina enheter som kör Windows 10.

- **E-postserver**: Ange värddatornamnet för din Exchange-server.
- **Kontonamn**: Ange visningsnamnet för e-postkontot. Namnet visas för användare på deras enheter.
- **Användarnamnattribut från AAD**: Namnet är det attribut som Intune hämtar från Azure Active Directory (AAD). Intune genererar användarnamnet som används av den här profilen. Alternativen är:
  - **User Principal Name**: Hämtar namnet, till exempel `user1` eller `user1@contoso.com`
  - **Primär SMTP-adress**: Hämtar namnet i e-postadressformat, som `user1@contoso.com`
  - **SAM-kontonamn**: Kräver domänen, till exempel `domain\user1`.

    Ange även:  
    - **Källa för användardomännamn**: Välj **AAD** (Azure Active Directory) eller **Anpassat**.

      När du väljer att hämta attributen från **AAD** anger du:
      - **Attribut för användardomännamn från AAD**: Välj att hämta attributet **Fullständigt domännamn** eller **NetBIOS-namn** för användaren

      När du väljer att använda **anpassade** attribut anger du:
      - **Anpassat domännamn som används**: Ange ett värde som Intune använder för domännamnet, till exempel `contoso.com` eller `contoso`

- **E-postadressattribut från AAD**: Välj hur e-postadressen för användaren ska genereras. Välj **UPN (User Principal Name)** (`user1@contoso.com` eller `user1`) om du vill använda det fullständiga huvudnamnet som e-postadress eller **Primär SMTP-adress** (`user1@contoso.com`) om du vill använda den primära SMTP-adressen för att logga in på Exchange.

## <a name="security-settings"></a>Säkerhetsinställningar

- **SSL**: Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.

## <a name="synchronization-settings"></a>Synkroniseringsinställningar

- **Antal e-postmeddelanden som ska synkroniseras**: Välj det antal dagar med e-post du vill synkronisera. Eller välj **Obegränsat** om du vill synkronisera all tillgänglig e-post.
- **Synkroniseringsschema**: Välj schema för enheter för att synkronisera data från Exchange-servern. Du kan även välja **När meddelanden anländer**, som synkroniserar data så snart de anländer eller **Manuellt**, där användaren måste initiera synkroniseringen.

## <a name="content-sync-settings"></a>Synkroniseringsinställningar för innehåll

- **Innehållstyp som ska synkroniseras:** Välj vilka typer av innehåll som enheterna ska synkroniseras från:
  - **Kontakter**
  - **Kalender**
  - **aktiviteter**

## <a name="next-steps"></a>Nästa steg
[Konfigurera e-postinställningar i Intune](email-settings-configure.md)
