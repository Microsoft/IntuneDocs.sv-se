---
title: Registrera macOS-enheter i Intune
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs mer om hur du registrerar macOS-enheter i Intune Azure-förhandsversionen."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c10a28a51e9f6bed99a657cd940b00f3114e4588
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Registrera macOS-enheter i Intune Azure-förhandsversionen

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Med Intune kan du hantera macOS-enheter. För att aktivera hantering av enheter måste användarna registrera sina enheter genom att gå till [Företagsportalens webbplats](http://portal.manage.microsoft.com) och följa anvisningarna. När macOS-enheter hanteras kan du [skapa anpassade inställningar för macOS-enheter](custom settings-macos.md). Fler funktioner kommer snart att bli tillgängliga.

## <a name="prerequisites"></a>Förutsättningar

Uppfyll följande krav innan du konfigurerar registreringen av macOS-enheter:

- [Konfigurera domäner](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Ange MDM-utfärdare](mdm-authority-set.md)
- [Skapa grupper](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Konfigurera företagsportalen](company-portal-app.md)
- Tilldela användarlicenser i [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Hämta ett Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)

## <a name="set-up-macos-enrollment"></a>Konfigurera registrering av macOS

Som standard tillåter Intune redan registrering av macOS-enheter.

Se [Ange begränsningar för enhetstyp](enrollment-restrictions-set.md#set-device-type-restrictions) för att blockera macOS-enheter från registrering.

Se [Ange begränsningar för enhetsgräns](enrollment-restrictions-set.md#set-device-limit-restrictions) för att ange det maximala antalet enheter som en användare kan registrera.

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurserna

Du måste be slutanvändarna att gå till [företagsportalens webbplats](http://portal.manage.microsoft.com) och följa anvisningarna för att registrera sina enheter. Du kan även skicka dem en länk till stegen för registrering online: [Registrera en macOS-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Information om andra slutanvändaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [Använda en iOS- eller macOS-enhet med Intune](https://docs.microsoft.com/intune-user-help/using-your-ios-or-mac-os-x-device-with-intune)

