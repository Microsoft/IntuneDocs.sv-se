---
title: "Konfigurera registrering för macOS-enheter"
titlesuffix: Microsoft Intune
description: "Läs om hur du konfigurerar registreringen av macOS-enheter i Intune."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 77a1551321079765f00f0e35d57211ae4c99e5a6
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Konfigurera registrering för macOS-enheter i Intune

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

## <a name="user-owned-ios-devices-byod"></a>Användarägda iOS-enheter (BYOD)

Du kan låta användare registrera sina personliga enheter för Intune-hantering, vilket kallas "bring your own device" eller BYOD. När du uppfyller kraven och har tilldelat licenser till användarna, kan de ladda ned företagsportalappen för macOS från App Store och följa instruktionerna för registrering i appen.

## <a name="company-owned-ios-devices"></a>Företagsägda iOS-enheter
För organisationer som köper enheter till sina användare, stöder Intune registrering av företagsägda macOS-enheter med ett konto för [enhetsregistreringshanteraren](device-enrollment-manager-enroll.md).

## <a name="set-up-macos-enrollment"></a>Konfigurera registrering av macOS

Som standard tillåter Intune redan registrering av macOS-enheter.

Se [Ange begränsningar för enhetstyp](enrollment-restrictions-set.md) för att blockera macOS-enheter från registrering.

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurserna

Be slutanvändarna att gå till [företagsportalens webbplats](http://portal.manage.microsoft.com) och följa anvisningarna för att registrera sina enheter. Du kan även skicka dem en länk till stegen för registrering online: [Registrera en macOS-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Information om andra slutanvändaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](end-user-educate.md)
- [Använd din macOS-enhet med Intune](/intune-user-help/using-your-macos-device-with-intune)
