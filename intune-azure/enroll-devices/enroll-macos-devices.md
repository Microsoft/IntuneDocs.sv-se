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
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 6fcbeb30fb11b6bc8def3a1c245bff56b3f7cca4
ms.contentlocale: sv-se
ms.lasthandoff: 05/10/2017


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Registrera macOS-enheter i Intune Azure-förhandsversionen

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Med Intune kan du hantera macOS-enheter. För att aktivera hantering av enheter måste användarna registrera sina enheter genom att gå till [Företagsportalens webbplats](http://portal.manage.microsoft.com) och följa anvisningarna. När macOS-enheter hanteras kan du [skapa anpassade inställningar för macOS-enheter](../configure-devices/custom-for-macos.md). Fler funktioner kommer snart att bli tillgängliga.

## <a name="prerequisites"></a>Förutsättningar

Uppfyll följande krav innan du konfigurerar registreringen av macOS-enheter:

- [Konfigurera domäner](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Ange MDM-utfärdare](set-mdm-authority.md)
- [Skapa grupper](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Konfigurera företagsportalen](../manage-apps/company-portal-app.md)
- Tilldela användarlicenser i [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Hämta ett Apple MDM-pushcertifikat](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>Konfigurera registrering av macOS

Som standard tillåter Intune redan registrering av macOS-enheter.

Se [Ange begränsningar för enhetstyp](set-enrollment-restrictions.md#set-device-type-restrictions) för att blockera macOS-enheter från registrering.

Se [Ange begränsningar för enhetsgräns](set-enrollment-restrictions.md#set-device-limit-restrictions) för att ange det maximala antalet enheter som en användare kan registrera.

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurserna

Du måste be slutanvändarna att gå till [företagsportalens webbplats](http://portal.manage.microsoft.com) och följa anvisningarna för att registrera sina enheter. Du kan även skicka dem en länk till stegen för registrering online: [Registrera en macOS-enhet i Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos).

Information om andra slutanvändaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [Använda en iOS- eller macOS-enhet med Intune](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)

