---
title: Konfigurera registrering för macOS-enheter
titlesuffix: Microsoft Intune
description: Läs om hur du konfigurerar registreringen av macOS-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5ffd2dca10db3df6abdcd5fa9603f1f58a37a078
ms.sourcegitcommit: e0d55bdda1a818ffe4cfc0ef0592833e22f65a89
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290544"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Konfigurera registrering för macOS-enheter i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I Intune kan du hantera macOS-enheter för att ge användarna åtkomst till företagets e-post och appar.

Som Intune-administratör kan du ställa in registrering av företagsägda och egna macOS-enheter (”bring your own device” eller BYOD). 

## <a name="prerequisites"></a>Krav

Uppfyll följande krav innan du konfigurerar registreringen av macOS-enheter:

- [Konfigurera domäner](custom-domain-name-configure.md)
- [Ange MDM-utfärdare](mdm-authority-set.md)
- [Skapa grupper](groups-add.md)
- [Konfigurera företagsportalen](company-portal-app.md)
- Tilldela användarlicenser i [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Hämta ett Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>Användarägda macOS-enheter (BYOD)

Du kan låta användarna registrera sina egna enheter för Intune-hantering, vilket kallas ”bring your own device” eller BYOD. När du har slutfört förutsättningarna och tilldelat användarlicenser kan användarna registrera sina enheter genom att:
- gå till [webbplatsen för företagsportalen](https://portal.manage.microsoft.com) eller
- ladda ned appen Företagsportal.
Du kan även skicka dem en länk till registrering online: [Registrera din macOS-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Information om andra slutanvändaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](end-user-educate.md)
- [Använd din macOS-enhet med Intune](/intune-user-help/using-your-macos-device-with-intune)

## <a name="company-owned-macos-devices"></a>Företagsägda macOS-enheter
Intune har stöd för följande registreringsmetoder för macOS-enheter som ägs av företaget, i organisationer som köper enheter till sina användare:
- [Apples program för enhetsregistrering (DEP)](device-enrollment-program-enroll-macos.md): Företag kan köpa macOS-enheter via Apples program för enhetsregistrering (DEP). Med DEP kan du distribuera en registreringsprofil ”over-the-air” för att hantera enheter.
- [Enhetsregistreringshanteraren (DEM)](device-enrollment-manager-enroll.md): Du kan använda ett DEM-konto till att registrera upp till 1 000 enheter.

## <a name="block-macos-enrollment"></a>Blockera macOS-registrering
Som standard kan macOS-enheter registreras i Intune. Se [Ange begränsningar för enhetstyp](enrollment-restrictions-set.md) för att blockera macOS-enheter från registrering.

## <a name="enroll-virtual-macos-machines-for-testing"></a>Registrera virtuella macOS-datorer för testning

> [!NOTE]
> Virtuella macOS-datorer stöds endast för testning. Du bör inte använda virtuella macOS-datorer som produktionsenheter för dina slutanvändare. 

Du kan registrera virtuella macOS-datorer för testning med antingen Parallels Desktop eller VMware Fusion. 

För Parallels Desktop måste du ange maskinvarutyp och serienummer för de virtuella datorerna så att Intune kan identifiera dem. Följ Parallels anvisningar för inställning av maskinvarutyp och [serienummer](http://kb.parallels.com/123455) och ange de nödvändiga inställningarna för testning. Vi rekommenderar att du matchar maskinvarutypen på enheten som kör de virtuella datorerna med maskinvarutypen för de virtuella datorer som du skapar. Du hittar den här maskinvarutypen i **Apple-menyn** > **Om denna Mac** > **Systemrapport** > **Modellidentifierare**. 

För VMware Fusion behöver du [redigera .vmx-filen](https://kb.vmware.com/s/article/1014782) och ange maskinvarumodell samt serienummer för den virtuella datorn. Vi rekommenderar att du matchar maskinvarutypen på enheten som kör de virtuella datorerna med maskinvarutypen för de virtuella datorer som du skapar. Du hittar den här maskinvarutypen i **Apple-menyn** > **Om denna Mac** > **Systemrapport** > **Modellidentifierare**. 

## <a name="user-approved-enrollment"></a>Registrering av användargodkänd

MDM-registrering av användargodkänd är en typ av macOS-registrering som du kan använda för att hantera vissa känsliga inställningar. Mer information finns i [Apples supportdokumentation](https://support.apple.com/HT208019).

För att vara användargodkänd måste, slutanvändaren efter registrering med hjälp av macOS-företagsportalen, manuellt ange godkännande med hjälp av systeminställningarna. Instruktioner för att göra detta tillhandahålls av macOS-företagsportal för användare av macOS 10.13.2 och senare.

Om du vill ta reda på om en enhet är användargodkänd, gå till Intune-portalen och välj sedan **Enheter** > **Alla enheter**> Välj enhet > **Maskinvara**. Markera fältet **Användargodkänd**.

## <a name="next-steps"></a>Nästa steg

När macOS-enheter registreras kan du [skapa anpassade inställningar för enheterna](custom-settings-macos.md).
