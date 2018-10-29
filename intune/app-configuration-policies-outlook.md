---
title: Outlook-inställningar för iOS- och Android-enheter i Microsoft Intune
description: Skapa en konfigurationsprincip för att ställa in Microsoft Outlook-inställningar som körs på iOS- och Android-enheter.
keywords: ''
author: Erikre
ms.author: erikre
ms.reviewer: smithre4
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 24ed1a895dd3e4cad6111b40913b43fa9c6a3cec
ms.sourcegitcommit: 11bd3dbbc9dd762df7c6d20143f2171799712547
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2018
ms.locfileid: "48903530"
---
# <a name="microsoft-outlook-configuration-settings"></a>Microsoft Outlook-konfigurationsinställningar 

Använd en konfigurationsprincip för att ställa in Microsoft Outlook-inställningar som körs på iOS- och Android-enheter. 

Information om hur du skapar en appkonfigurationsprincip för hanterade iOS-enheter finns i [Lägga till appkonfigurationsprinciper för hanterade iOS-enheter](app-configuration-policies-use-ios.md). Information om hur du skapar en appkonfigurationsprincip för hanterade Android-enheter finns i [Lägga till appkonfigurationsprinciper för hanterade Android-enheter](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Konfigurationsinställningar

När du lägger till en konfigurationsprincip i Intune kan du ange specifika inställningar för att konfigurera Microsoft Outlook. I fönstret **Konfigurationsinställningar** kan du ange e-postkontokonfigurationen.

### <a name="basic-authentication-email-account-settings"></a>E-postkontoinställningar för grundläggande autentisering
Outlook för iOS och Android erbjuder Exchangeadministratörer möjlighet att ”pusha” kontokonfigurationer till sina lokala användare som använder grundläggande autentisering med ActiveSync-protokollet. Mer information finns i [Kontokonfiguration i Outlook för iOS och Android med grundläggande autentisering](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/account-setup). Om du vill aktivera konfiguration av kontoinstallation kan du konfigurera följande inställningar:

- **E-postserver**: Ange namnet på den lokala Exchange-servern (t.ex. mail.contoso.com).
- **Namn på e-postkonto**: Ange visningsnamnet för e-postkontot. Namnet visas för användare på deras enheter.
- **Användarnamnattribut från AAD**: Namnet är attributet som Intune hämtar från Azure Active Directory (Azure AD). Intune genererar användarnamnet som används av den här profilen. Alternativen är:
  - **UPN (User Principal Name)**: Hämtar namnet, till exempel `user1` eller `user1@contoso.com`
  - **Primär SMTP-adress**: Hämtar namnet i e-postadressformat, till exempel `user1@contoso.com`
- **E-postadressattribut från AAD**: Välj hur e-postadressen för användaren ska skapas. Välj **UPN (User Principal Name)** (`user1@contoso.com` eller `user1`) om du vill använda det fullständiga huvudnamnet som e-postadress eller **Primär SMTP-adress** (`user1@contoso.com`) om du vill använda den primära SMTP-adressen för att logga in på Exchange. Rekommendationen är att välja **Primär SMTP-adress**.
- **Kontodomän**: (Valfritt) Domänen för kontot.

## <a name="next-steps"></a>Nästa steg
[Konfigurera e-postinställningar i Intune](email-settings-configure.md)

