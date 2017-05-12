---
title: "Skapa Intune-enhetens konfigurationsprofiler | Förhandsversion av Intune Azure"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Information om hur du skapar Intune-enhetens konfigurationsprofiler."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 74a905ed2ba9ec04ae14df96fcd3f6b6caf1241c
ms.contentlocale: sv-se
ms.lasthandoff: 05/10/2017


---

# <a name="how-to-create-device-configuration-profiles-in-microsoft-intune"></a>Så här skapar du enhetens konfigurationsprofiler i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
2. På bladet visas en lista med profiler. Välj **Skapa profil**.
3. Ange följande på bladet **Skapa profil**:
    - **Namn** – Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning** – Ange en valfri beskrivning av profilen.
    - **Plattform** – Välj plattformstyp för profilen som du vill skapa.
    - **Profiltyp** – Välj typ för den profil som du vill skapa. Listan över tillgängliga typer varierar beroende på vilken plattform som du har valt.
    - **Inställningar** – Se följande avsnitt för information om inställningarna för varje profiltyp:
        -  [Inställningar av enhetsfunktion](how-to-configure-device-features.md)
        -  [Inställningar för enhetsbegränsning](how-to-configure-device-restrictions.md)
        -  [E-postinställningar](how-to-configure-email-settings.md)
        -  [VPN-inställningar](how-to-configure-vpn-settings.md)
        -  [Trådlösa inställningar](how-to-configure-wi-fi-settings.md)
        -  [Inställningar för uppgradering av Windows 10](how-to-configure-windows-10-edition-upgrade.md)
        -  [Certifikatinställningar](how-to-configure-certificates.md)
        -  [Inställningar för Windows informationsskydd](how-to-configure-windows-information-protection.md)
        -  [Utbildningsinställningar](how-to-configure-education-settings.md)
        -  [Anpassade inställningar](how-to-configure-custom-settings.md)

    ![Skapa enhetsprofil](./media/create-device-profile.png)
4. När du är klar med att konfigurera inställningar går du till bladet **Skapa profil** och väljer **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](how-to-assign-device-profiles.md).


### <a name="next-steps"></a>Nästa steg
Information om hur du tilldelar enhetsprofiler finns i [Så här tilldelar du enhetsprofiler med Microsoft Intune](how-to-assign-device-profiles.md).

