---
title: Registrera Android-arbetsprofilenheter i Intune
titlesuffix: Microsoft Intune
description: Lär dig hur du registrerar Android-arbetsprofilenheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fc1943781dcf95209b575cdb6e36d5065275626f
ms.sourcegitcommit: 40b1d82df99f09a75a17065cdd0e84d8038f460a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/22/2018
ms.locfileid: "40255078"
---
# <a name="set-up-enrollment-of-android-work-profile-devices"></a>Konfigurera registrering av Android-arbetsprofilenheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune hjälper dig att distribuera appar och inställningar till Android-arbetsprofilenheter för att se till att arbetsrelaterad och personlig information hålls isär. Specifik information om Android enterprise finns i [Krav för Android enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Du kan konfigurera Android-arbetsprofilhantering så här:

1. [Anslut ditt Intune-klientkonto till ditt Android enterprise-konto](connect-intune-android-enterprise.md).
2. Ange inställningar för Android-arbetsprofilregistrering. Android-arbetsprofiler [stöds bara på vissa Android-enheter](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Alla enheter som har stöd för Android-arbetsprofiler stöder även konventionell Android-hantering. Intune gör det möjligt att ange hur enheter med stöd för Android-arbetsprofiler ska hanteras inifrån [Registreringsbegränsningar](enrollment-restrictions-set.md).
    - **Blockera (ange som standard)**: Alla Android-enheter, inklusive enheter som stöder Android-arbetsprofiler, registreras som konventionella Android-enheter.
    - **Tillåt**: Alla enheter som stöder Android-arbetsprofiler registreras som Android-arbetsprofilenheter. Alla Android-enheter som inte stöder Android-arbetsprofiler registreras som konventionella Android-enheter.
3. [Berätta för dina användare hur de registrerar sina enheter](/intune-user-help/enroll-your-device-in-intune-android).


Om du vill registrera enheter i Android-arbetsprofiler, men enheterna redan har registrerats som vanliga Android-enheter, måste de enheterna först avregistreras och sedan registreras på nytt.

Om du registrerar Android-arbetsprofilenheter med hjälp av ett konto för [Enhetsregistreringshanterare](device-enrollment-manager-enroll.md) går det att registrera högst 10 enheter per konto.

Mer information finns i [Data som Intune skickar till Google](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Godkänn företagsportalappen i den hanterade Google Play-butiken

För att garantera att användarna alltid har åtkomst till den senaste versionen av appen Företagsportal måste du godkänna appen Företagsportal för Android i Managed Google Play Butik. När du godkänner den ser du till att varje användare får automatiska uppdateringar. Om du inte godkänner den kommer företagsportalappen till slut att bli inaktuell och kan därmed inte ta emot viktiga felkorrigeringar eller nya funktioner när Microsoft släpper dem.

Så här godkänner du Intune-företagsportalen:

1.  Bläddra till appen Företagsportal i [hanterade Google Play Butik](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Logga in på Managed Google Play Butik med samma Google-konto som du använde när du konfigurerade bindningen för Android för företag.
3.  Klicka på **Godkänn** för att öppna en ny dialogruta.
4.  Granska behörigheterna i den här dialogrutan och klicka sedan på **Godkänn**. Du måste tillåta dessa behörigheter för att företagsportalappen ska kunna hantera arbetsprofilen på enheten.
5.  Välj **Keep approved when app requests new permissions** (Behåll godkända när appen begär nya behörigheter) och klicka sedan på **Spara.**

## <a name="next-steps-for-android-work-profiles"></a>Nästa steg för Android-arbetsprofiler
- [Distribuera Android-arbetsprofilappar](store-apps-android.md)
- [Lägga till konfigurationsprinciper för Android-arbetsprofiler](device-profiles.md)
