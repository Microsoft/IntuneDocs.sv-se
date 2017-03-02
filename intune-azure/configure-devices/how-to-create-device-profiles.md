---
title: "Skapa Intune-enhetens konfigurationsprofiler | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Information om hur du skapar Intune-enhetens konfigurationsprofiler."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 908169c47d9eaa583c775c8ed06acea233040e50
ms.lasthandoff: 02/16/2017


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
        -  [Inställningar för enhetsbegränsning](/intune-azure/configure-devices/how-to-configure-device-restrictions)
        -  [E-postinställningar](/intune-azure/configure-devices/how-to-configure-email-settings)
        -  [VPN-inställningar](/intune-azure/configure-devices/how-to-configure-vpn-settings)
        -  [Trådlösa inställningar](/intune-azure/configure-devices/how-to-configure-wi-fi-settings)
        -  [Inställningar för uppgradering av Windows 10](/intune-azure/configure-devices/how-to-configure-windows-10-edition-upgrade)
        -  [Certifikatinställningar](/intune-azure/configure-devices/how-to-configure-certificates)
        -  [Inställningar för Windows informationsskydd](/intune-azure/configure-devices/how-to-configure-windows-information-protection)
        -  [Utbildningsinställningar](/intune-azure/configure-devices/education-settings-for-ios.md)
        -  [Anpassade inställningar](/intune-azure/configure-devices/how-to-configure-custom-settings)

    ![Skapa enhetsprofil](./media/create-device-profile.png)
4. När du är klar med att konfigurera inställningar går du till bladet **Skapa profil** och väljer **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](how-to-assign-device-profiles.md).


### <a name="next-steps"></a>Nästa steg
Information om hur du tilldelar enhetsprofiler finns i [Så här tilldelar du enhetsprofiler med Microsoft Intune](/intune-azure/configure-devices/how-to-assign-device-profiles).

