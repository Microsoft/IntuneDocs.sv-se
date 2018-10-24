---
title: Outlook-inställningar för iOS- och Android-enheter i Microsoft Intune
description: Skapa en konfigurationsprincip för att ställa in Microsoft Outlook-inställningar som körs på iOS- och Android-enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7fc9f34bbd3d14ac4291582247b1e45169c2cccc
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828939"
---
# <a name="microsoft-outlook-configuration-settings"></a>Microsoft Outlook-konfigurationsinställningar 

Använd en konfigurationsprincip för att ställa in Microsoft Outlook-inställningar som körs på iOS- och Android-enheter. 

Information om hur du skapar en appkonfigurationsprincip för hanterade iOS-enheter finns i [Lägga till appkonfigurationsprinciper för hanterade iOS-enheter](app-configuration-policies-use-ios.md). Information om hur du skapar en appkonfigurationsprincip för hanterade Android-enheter finns i [Lägga till appkonfigurationsprinciper för hanterade Android-enheter](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Konfigurationsinställningar

När du lägger till en konfigurationsprincip i Intune kan du ange specifika inställningar för att konfigurera Microsoft Outlook. I fönstret **Konfigurationsinställningar** kan du ange e-postkontokonfigurationen.

### <a name="email-account-settings"></a>E-postkontoinställningar

Följande konfigurationsinställningar är specifika för Microsoft Outlook.

- **E-postserver**: Ange värdnamnet för din Exchange-server.
- **Namn på e-postkonto**: Ange visningsnamnet för e-postkontot. Namnet visas för användare på deras enheter.
- **Användarnamnattribut från AAD**: Namnet är attributet som Intune hämtar från Azure Active Directory (AAD). Intune genererar användarnamnet som används av den här profilen. Alternativen är:
  - **UPN (User Principal Name)**: Hämtar namnet, till exempel `user1` eller `user1@contoso.com`
  - **Primär SMTP-adress**: Hämtar namnet i e-postadressformat, till exempel `user1@contoso.com`
  - **sAM-kontonamn**: Kräver domänen, till exempel `domain\user1`.

    Ange även:  
    - **Källa för användardomännamn**: Välj **AAD** (Azure Active Directory) eller **Anpassat**.

      När du väljer att hämta attributen från **AAD** anger du:
      - **Attribut för användardomännamn från AAD**: Välj att hämta attributet för **Fullständigt domännamn** eller **NetBIOS-namn** för användaren

      När du väljer att använda **anpassade** attribut anger du:
      - **Anpassat domännamn att använda**: Ange ett värde som Intune använder för domännamnet, till exempel `contoso.com` eller `contoso`

- **E-postadressattribut från AAD**: Välj hur e-postadressen för användaren ska skapas. Välj **UPN (User Principal Name)** (`user1@contoso.com` eller `user1`) om du vill använda det fullständiga huvudnamnet som e-postadress eller **Primär SMTP-adress** (`user1@contoso.com`) om du vill använda den primära SMTP-adressen för att logga in på Exchange.
- **Kontodomän**: (Valfritt) Domänen för kontot.

## <a name="next-steps"></a>Nästa steg
[Konfigurera e-postinställningar i Intune](email-settings-configure.md)

