---
title: Skapa Intune-enhetens konfigurationsprofiler
titlesuffix: Azure portal
description: "Så här skapar du enhetskonfigurationsprofiler i Intune.”"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 05/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ab7a2f905a7eec33204516e07f0a5d2cda4e1d95
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-create-device-configuration-profiles-in-microsoft-intune"></a>Så här skapar du enhetens konfigurationsprofiler i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
2. På bladet visas en lista med profiler. Välj **Skapa profil**.
3. På bladet **Skapa profil** anger du följande objekt:
    - **Namn** – Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning** – Ange en valfri beskrivning av profilen.
    - **Plattform** – Välj plattformstyp för profilen som du vill skapa.
    - **Profiltyp** – Välj typ för den profil som du vill skapa. Listan över tillgängliga typer varierar beroende på vilken plattform du väljer.
    - **Inställningar** – Se följande avsnitt för information om inställningarna för varje profiltyp:
        -  [Inställningar av enhetsfunktion](device-features-configure.md)
        -  [Inställningar för enhetsbegränsning](device-restrictions-configure.md)
        -  [E-postinställningar](email-settings-configure.md)
        -  [VPN-inställningar](vpn-settings-configure.md)
        -  [Trådlösa inställningar](wi-fi-settings-configure.md)
        -  [Inställningar för uppgradering av Windows 10](edition-upgrade-configure-windows-10.md)
        -  [Certifikatinställningar](certificates-configure.md)
        -  [Inställningar för Windows informationsskydd](windows-information-protection-configure.md)
        -  [Utbildningsinställningar](education-settings-configure.md)
        -  [Anpassade inställningar](custom-settings-configure.md)

    ![Skapa enhetsprofil](./media/create-device-profile.png)
4. När du är klar med att konfigurera inställningar går du till bladet **Skapa profil** och väljer **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).


### <a name="next-steps"></a>Nästa steg
Information om hur du tilldelar enhetsprofiler finns i [Så här tilldelar du enhetsprofiler med Microsoft Intune](device-profile-assign.md).
