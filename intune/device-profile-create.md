---
title: "Skapa enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs"
description: "Lägga till eller konfigurera en enhetsprofil i Microsoft Intune, till exempel välja plattformstyp och konfigurera inställningar i Azure Portal"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c40fd13a46a61ec0ee05efba7ece7653f5de90ca
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Skapa en enhetsprofil i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Skapa profilen
1. I [Azure Portal](https://portal.azure.com) väljer du **Alla tjänster** och söker efter **Microsoft Intune**.

2. I **Microsoft Intune** väljer du **Enhetskonfiguration**, **Profiler** och sedan **Skapa profil**.

3. Ange följande egenskaper: 

    - **Namn**: Ange ett beskrivande namn på den nya profilen
    - **Beskrivning**: Valfritt men rekommenderat. Ange en beskrivning av profilen.
    - **Plattform**: Välj plattformstyp:  

        - **Android**
        - **Android for Work**
        - **iOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 och senare**
        - **Windows 10 och senare**

    - **Profiltyp**: Välj vilken typ du vill skapa. Listans innehåll beror på vilken plattform du väljer.
    - **Inställningar**: Läs en beskrivning av inställningarna för varje profiltyp i följande avsnitt:

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

    ![Ange inställningar för att skapa en enhetsprofil](./media/create-device-profile.png)

4. Välj **Skapa** när du är klar. 

Profilen skapas och visas i listan. Information om hur du tilldelar den här profilen till grupper finns i [Tilldela enhetsprofiler](device-profile-assign.md).


## <a name="next-steps"></a>Nästa steg
Information om hur du tilldelar enhetsprofiler finns i [Så här tilldelar du enhetsprofiler med Microsoft Intune](device-profile-assign.md).