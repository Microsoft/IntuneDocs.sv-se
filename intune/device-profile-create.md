---
title: Skapa enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Lägga till eller konfigurera en enhetsprofil i Microsoft Intune, till exempel välja plattformstyp och konfigurera inställningar i Azure-portalen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3d46960e6ea7e2ae9bed6c0016ddc309bd15f572
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Skapa en enhetsprofil i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Skapa profilen
1. I [Azure Portal](https://portal.azure.com) väljer du **Alla tjänster** och söker efter **Microsoft Intune**.

2. I **Microsoft Intune** väljer du **Enhetskonfiguration** och sedan **Profiler**. Välj sedan **Skapa profil**.

3. Ange följande egenskaper:

   - **Namn**: Ange ett beskrivande namn på den nya profilen.
   - **Beskrivning:** Ange en beskrivning för profilen. (Detta är valfritt, men rekommenderas.)
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

     ![Skärmbild av Skapa profil](./media/create-device-profile.png)

4. Välj **Skapa** när du är klar.

Profilen skapas och visas i listan.


## <a name="next-steps"></a>Nästa steg
Information om hur du tilldelar enhetsprofiler finns i [Så här tilldelar du enhetsprofiler med Microsoft Intune](device-profile-assign.md).
