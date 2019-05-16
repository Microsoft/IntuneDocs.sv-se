---
title: Registrera Android Enterprise-arbetsprofilenheter i Intune
titleSuffix: Microsoft Intune
description: Läs om hur du registrerar Android Enterprise-arbetsprofilenheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66574fe66f90b73d8ebf5835c5b16e93276579e4
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568225"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Konfigurera registrering av Android Enterprise-arbetsprofilenheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune hjälper dig att distribuera appar och inställningar till Android Enterprise-arbetsprofilenheter för att arbetsrelaterad och personlig information ska kunna hållas isär. Specifik information om Android Enterprise finns i [Krav för Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Du kan konfigurera Android Enterprise-arbetsprofilhantering så här:

1. [Anslut ditt Intune-klientorganisationskonto till ditt Android Enterprise-konto](connect-intune-android-enterprise.md).
2. Ange inställningar för Android Enterprise-arbetsprofilregistreringen. Android Enterprise-arbetsprofiler [stöds bara på vissa Android-enheter](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Alla enheter som har stöd för Android Enterprise-arbetsprofiler stöder även normal Android-hantering. Med Intune kan du ange hur enheter med stöd för Android Enterprise-arbetsprofiler ska hanteras inifrån [Registreringsbegränsningar](enrollment-restrictions-set.md).
    - **Blockera (ange som standard)**:  Alla Android-enheter, inklusive enheter som stöder Android Enterprise-arbetsprofiler, registreras som konventionella Android-enheter.
    - **Tillåt**: Alla enheter som stöder Android Enterprise-arbetsprofiler registreras som Android Enterprise-arbetsprofilenheter. Alla Android-enheter som inte stöder Android Enterprise-arbetsprofiler registreras som konventionella Android-enheter.
3. [Berätta för dina användare hur de registrerar sina enheter](/intune-user-help/enroll-your-device-in-intune-android).


Om du vill registrera enheter i Android Enterprise-arbetsprofiler, men enheterna redan har registrerats som vanliga Android-enheter, måste de enheterna först avregistreras och sedan registreras på nytt.

Om du registrerar Android Enterprise-arbetsprofilenheter med hjälp av ett konto för [Enhetsregistreringshanteraren](device-enrollment-manager-enroll.md), går det att registrera högst 10 enheter per konto.

Mer information finns i [Data som Intune skickar till Google](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Godkänn företagsportalappen i den hanterade Google Play-butiken

För att användarna alltid ska ha åtkomst till den senaste versionen av företagsportalappen, måste du godkänna appen för Android i den hanterade Google Play-butiken. När du godkänner den ser du till att varje användare får automatiska uppdateringar. Om du inte godkänner den kommer företagsportalappen till slut att bli inaktuell och kan därmed inte ta emot viktiga felkorrigeringar eller nya funktioner när Microsoft släpper dem.

Så här godkänner du Intune-företagsportalen:

1.  Bläddra till företagsportalappen i [den hanterade Google Play-butiken](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Logga in på den hanterade Google Play-butiken med samma Google-konto som du använde när du konfigurerade bindningen för Android Enterprise.
3.  Klicka på **Godkänn** för att öppna en ny dialogruta.
4.  Granska behörigheterna i den här dialogrutan och klicka sedan på **Godkänn**. Du måste tillåta dessa behörigheter för att företagsportalappen ska kunna hantera arbetsprofilen på enheten.
5.  Välj **Keep approved when app requests new permissions** (Behåll godkända när appen begär nya behörigheter) och klicka sedan på **Spara.**

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Nästa steg för Android Enterprise-arbetsprofiler
- [Distribuera Android Enterprise-arbetsprofilappar](apps-add-android-for-work.md)
- [Lägga till konfigurationsprinciper för Android Enterprise-arbetsprofiler](device-profiles.md)
