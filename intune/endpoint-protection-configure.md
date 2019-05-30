---
title: Konfigurera inställningar för slutpunktsskydd i Microsoft Intune – Azure | Microsoft Docs
description: Skapa inställningar för slutpunktsskydd när du skapar en profil för macOS- eller Windows 10-enheter i Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 184781a315dcaeaac9540294746a9c2cd85da917
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041908"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Lägga till inställningar för slutpunktsskydd i Intune

Med Intune kan du använda profiler för enhetskonfiguration för att hantera vanliga säkerhetsfunktioner för slutpunkter på enheter, inklusive:
- Brandvägg 
- BitLocker
- Tillåta och blockera appar  
- Windows Defender och kryptering

Du kan till exempel skapa en profil för slutpunktsskydd som endast tillåter att macOS-användare installerar appar från Mac App Store. Du kan också aktivera Windows SmartScreen när appar körs på Windows 10-enheter.

Innan du skapar en profil ska du läsa följande artiklar om de inställningar för skydd av slutpunkter som Intune kan hantera för varje plattform som stöds: 
   - [Inställningar för macOS](endpoint-protection-macos.md)
   - [Inställningar för Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Skapa en enhetsprofil med inställningar för slutpunktsskydd

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=20909).
3. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
4. Ange **Namn** och **Beskrivning** för slutpunktsskyddsprofilen.
5. Välj den enhetsplattform på vilken du vill tillämpa anpassade inställningar från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för inställning av enhetsbegränsningar:
   - **macOS**
   - **Windows 10 och senare**
6. Välj **Endpoint Protection** i listrutan **Profiltyp**. 
7. Vilka inställningar du kan konfigurera varierar beroende på vilken plattform du väljer. Se:
   - [Inställningar för macOS](endpoint-protection-macos.md)
   - [Inställningar för Windows 10](endpoint-protection-windows-10.md)  

8. När du har konfigurerat tillämpliga inställningar väljer du **Skapa** på sidan **Skapa profil**.

   Profilen skapas och visas på sidan med profillistan. Om du vill tilldela profilen till grupper kan du läsa [Tilldela enhetsprofiler](device-profile-assign.md).


## <a name="next-steps"></a>Nästa steg  

Om du vill tilldela profilen till grupper kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).
