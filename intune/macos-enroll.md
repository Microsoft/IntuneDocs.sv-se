---
title: Registrera macOS-enheter i Intune
titlesuffix: Azure portal
description: "Lär dig hur du registrerar macOS-enheter i Intune.\""
keywords: 
author: ErikjeMS
ms.author: erikje
nmanager: dougeby
ms.date: 10/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8528b3ec28499657b1eb39e1b981f92be3ab83ca
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="enroll-macos-devices-in-intune"></a>Registrera macOS-enheter i Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med Intune kan du hantera macOS-enheter. För att aktivera hantering av enheter måste användarna registrera sina enheter genom att gå till [Företagsportalens webbplats](http://portal.manage.microsoft.com) och följa anvisningarna. När macOS-enheter hanteras kan du [skapa anpassade inställningar för macOS-enheter](custom-settings-macos.md). Fler funktioner kommer snart att bli tillgängliga.

## <a name="prerequisites"></a>Krav

Uppfyll följande krav innan du konfigurerar registreringen av macOS-enheter:

- [Konfigurera domäner](custom-domain-name-configure.md)
- [Ange MDM-utfärdare](mdm-authority-set.md)
- [Skapa grupper](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Konfigurera företagsportalen](company-portal-app.md)
- Tilldela användarlicenser i [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Hämta ett Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)

## <a name="set-up-macos-enrollment"></a>Konfigurera registrering av macOS

Som standard tillåter Intune redan registrering av macOS-enheter.

Se [Ange begränsningar för enhetstyp](enrollment-restrictions-set.md) för att blockera macOS-enheter från registrering.

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurserna

Be slutanvändarna att gå till [företagsportalens webbplats](http://portal.manage.microsoft.com) och följa anvisningarna för att registrera sina enheter. Du kan även skicka dem en länk till stegen för registrering online: [Registrera en macOS-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Information om andra slutanvändaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](end-user-educate.md)
- [Använda en iOS- eller macOS-enhet med Intune](https://docs.microsoft.com/intune-user-help/using-your-ios-or-mac-os-x-device-with-intune)
