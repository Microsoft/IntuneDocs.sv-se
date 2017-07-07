---
title: Konfigurera uppgraderingar av Windows 10 med Intune
titleSuffix: Intune on Azure
description: "Läs hur du använder Intune för att uppgradera Windows 10-enheter som du hanterar till andra versioner.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 30cea0ecfa62e9bbc0200d15eff94782d48a81fa
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>Så här konfigurerar du uppgraderingar av Windows 10 i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd informationen i det här avsnittet för att lära dig hur du konfigurerar en Windows 10-uppgraderingsprofil. Med den här profilen kan du automatiskt uppgradera enheter som kör någon av följande Windows 10-versioner till en annan utgåva:

- Windows 10 Home
- Windows 10 Holographic
- Windows 10 Mobil


Följande uppgraderingsvägar stöds:

- Från Windows 10 Pro till Windows 10 Enterprise
- Från Windows 10 Home till Windows 10 Education
- Från Windows 10 Mobile till Windows 10 Mobile Enterprise
- Från Windows 10 Holographic Pro till Windows 10 Holographic Enterprise


## <a name="before-you-start"></a>Innan du börjar
Innan du börjar uppgradera enheter till den senaste versionen behöver du något av följande:

- En produktnyckel som är giltig för att installera den nya versionen av Windows på alla enheter som du riktar principen mot (för Windows 10 Desktop-versioner). Du kan använda antingen multipla aktiveringsnycklar (MAK) eller nyckelhanteringsserver (KMS). eller En licensfil från Microsoft som innehåller licensinformation för att installera den nya Windows-versionen på alla enheter som berörs av principen (för Windows 10 Mobile- och Windows 10 Holographic-versioner).
- Windows 10-målenheterna måste vara registrerade i Microsoft Intune. Du kan inte använda versionsuppgraderingsprincipen för datorer som kör Intune-klientprogrammet.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Skapa en enhetsprofil med inställningar för enhetsbegränsningar

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för versionsuppgraderingsprofilen.
5. I listrutan **Plattform** väljer du **Windows 10 och senare**.
6. I listrutan **Profiltyp** väljer du **Uppgradering av utgåva**.
7. På bladet **Uppgradering av utgåva** konfigurerar du följande:
    - **Utgåva att uppgradera från** – I listrutan väljer du den Windows 10-version som du vill uppgradera på enheterna.
    - **Utgåva att uppgradera till** – I listrutan väljer du den version av Windows 10 Desktop, Windows 10 Holographic eller Windows 10 Mobile som du vill uppgradera målenheterna till.
    - **Produktnyckel** – Ange produktnyckeln som du har fått från Microsoft. Den kan användas för att uppgradera alla Windows 10 Desktop-enheter.<br>När du har skapat en princip som innehåller en produktnyckel går det inte att redigera produktnyckeln senare. Det beror på att nyckeln döljs av säkerhetsskäl. Om du vill ändra produktnyckeln måste du ange hela nyckeln igen.
    - **Licensfil** – Klicka på **Bläddra** och välj den licensfil som du har fått från Microsoft. Filen innehåller licensinformation för den Windows Holographic- eller Windows 10 Mobile-version som du vill uppgradera målenheterna till.
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).

