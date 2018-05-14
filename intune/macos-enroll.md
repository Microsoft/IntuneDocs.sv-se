---
title: Konfigurera registrering för macOS-enheter
titlesuffix: Microsoft Intune
description: Läs om hur du konfigurerar registreringen av macOS-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4f8cddb69ac85e45acde8a846df3b5413c3b75bf
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2018
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Konfigurera registrering för macOS-enheter i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

Be slutanvändarna att gå till [företagsportalens webbplats](https://portal.manage.microsoft.com) och följa anvisningarna för att registrera sina enheter. Du kan även skicka dem en länk till stegen för registrering online: [Registrera en macOS-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Information om andra slutanvändaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](end-user-educate.md)
- [Använd din macOS-enhet med Intune](/intune-user-help/using-your-macos-device-with-intune)

## <a name="enroll-virtual-macos-machines-for-testing"></a>Registrera virtuella macOS-datorer för testning

> [!NOTE]
> Virtuella macOS-datorer stöds endast för testning. Du bör inte använda virtuella macOS-datorer som produktionsenheter för dina slutanvändare. 

Du kan registrera virtuella macOS-datorer för testning med antingen Parallels Desktop eller VMware Fusion. 

För Parallels Desktop måste du ange maskinvarutyp och serienummer för de virtuella datorerna så att Intune kan identifiera dem. Följ Parallels anvisningar för [inställning av maskinvarutyp](http://kb.parallels.com/123594) och [serienummer](http://kb.parallels.com/123455) och ange de nödvändiga inställningarna för testning. Vi rekommenderar att du matchar maskinvarutypen på enheten som kör de virtuella datorerna med maskinvarutypen för de virtuella datorer som du skapar. Du hittar den här maskinvarutypen i **Apple-menyn** > **Om denna Mac** > **Systemrapport** > **Modellidentifierare**. 

För VMware Fusion behöver du [redigera .vmx-filen](https://kb.vmware.com/s/article/1014782) och ange maskinvarumodell samt serienummer för den virtuella datorn. Vi rekommenderar att du matchar maskinvarutypen på enheten som kör de virtuella datorerna med maskinvarutypen för de virtuella datorer som du skapar. Du hittar den här maskinvarutypen i **Apple-menyn** > **Om denna Mac** > **Systemrapport** > **Modellidentifierare**. 

## <a name="user-approved-enrollment"></a>Registrering av användargodkänd

MDM-registrering av användargodkänd är en typ av macOS-registrering som du kan använda för att hantera vissa känsliga inställningar. Mer information finns i [Apples supportdokumentation](https://support.apple.com/HT208019).

För att vara användargodkänd måste, slutanvändaren efter registrering med hjälp av macOS-företagsportalen, manuellt ange godkännande med hjälp av systeminställningarna. Instruktioner för att göra detta tillhandahålls av macOS-företagsportal för användare av macOS 10.13.2 och senare.

Om du vill ta reda på om en enhet är användargodkänd, gå till Intune-portalen och välj sedan **Enheter** > **Alla enheter**> Välj enhet > **Maskinvara**. Markera fältet **Användargodkänd**.