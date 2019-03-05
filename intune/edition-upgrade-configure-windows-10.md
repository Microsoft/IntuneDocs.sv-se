---
title: Uppgradera eller använd S-läge för 10 Windows-enheter – Microsoft Intune – Azure | Microsoft Docs
description: Använda Microsoft Intune för att uppgradera Windows 10-enheter till en annan utgåva eller aktivera S-läge. Administratörer kan använda en profil för enhetskonfiguration för att uppgradera Windows 10 Professional till Windows 10 Enterprise och aktivera eller växla från S-läge. Se de uppgraderingssökvägar som stöds för Windows 10 Pro, N Edition, Education, Cloud, Enterprise, Core, Holographic och Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 26a8718247142ef2ed3f509dc185207b1e99e82f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233329"
---
# <a name="upgrade-windows-10-editions-or-enable-s-mode-on-devices-using-microsoft-intune"></a>Uppgradera Windows 10-utgåvor eller aktivera S-läge på enheter med Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Som en del av din lösning för hantering av mobila enheter kan du uppgradera Windows 10-enheter. Exempelvis kan du uppgradera dina Windows 10 Professional-enheter till Windows 10 Enterprise. Eller om du vill aktivera S-mobil så att enheter endast kör appar från Microsoft Store.

[S-läget för Windows 10](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) är utformat för säkerhet och prestanda. Om dina enheter endast kör appar från Microsoft Store kan du använda S-läge för att skydda dina enheter. Om dina enheter använder appar som inte är tillgängliga i Microsoft Store kommer du att växla från S-läget. Att lämna S-läget kan inte ångras. Och när du har lämnat S-läget kan du inte gå tillbaka till S-läget för Windows 10.

Den här funktionen gäller för:

- Windows 10 och senare
- Windows 10 1809 eller senare för S-läge
- Windows 10 Holographic for Business

Dessa funktioner är tillgängliga i Intune och kan konfigureras av administratören. Intune använder ”konfigurationsprofiler” till att skapa och anpassa inställningarna efter din organisations behov. När du har lagt till dessa funktioner i en profil, kan du skicka eller distribuera profilen till Windows 10-enheter i din organisation. När du distribuerar profilen uppgraderas enheter automatiskt i Intune eller S-läget aktiveras.

Den här artikeln innehåller uppgraderingsvägar som stöds och visar hur du skapar enhetens konfigurationsprofil. Du kan också se alla tillgängliga uppgraderingar och S-inställningar för [Windows 10](edition-upgrade-windows-settings.md).

> [!NOTE]
> Om du tar bort principtilldelningen senare återställs inte Windows-versionen på enheten. Enheten fortsätter att köras normalt.

## <a name="prerequisites"></a>Krav

Innan du uppgraderar enheter måste du ha följande förutsättningar:

- En giltig produktnyckel för att installera den uppdaterade versionen av Windows på alla enheter som du riktar principen mot (för Windows 10 Desktop-versioner). Du kan använda antingen multipla aktiveringsnycklar (MAK) eller nyckelhanteringsserver (KMS).
- Du kan använda en licensfil för Windows 10 Mobile- och Windows 10 Holographic-versioner. Licensfilen som innehåller licensinformationen för att installera den uppdaterade versionen på alla enheter som du har som mål med principen.
- De Windows 10-enheter som du riktar principen mot måste vara registrerade i Microsoft Intune. Du kan inte använda versionsuppgraderingsprincipen för datorer som kör Intune-klientprogrammet.

## <a name="supported-upgrade-paths"></a>Uppgraderingsvägar som stöds

Följande tabell innehåller uppgraderingsvägar som stöds för Windows 10-utgåvans uppgraderingsprofil.

| Uppgradera från | Uppgradera till |
|---|---|
| Windows 10 Pro | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education |
| Windows 10 Pro N edition | Windows 10 Education N edition <br/>Windows 10 Enterprise N edition <br/>Windows 10 Pro Education N edition | 
| Windows 10 Pro Education | Windows 10 Education | 
| Windows 10 Pro Education N edition | Windows 10 Education N edition |
| Windows 10 Cloud | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro <br/>Windows 10 Pro Education | 
| Windows 10 Cloud N edition | Windows 10 Education N edition <br/>Windows 10 Enterprise N edition <br/>Windows 10 Pro N edition <br/>Windows 10 Pro Education N edition | 
| Windows 10 Enterprise | Windows 10 Education | 
| Windows 10 Enterprise N edition | Windows 10 Education N edition | 
| Windows 10 Core | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education | 
| Windows 10 Core N edition | Windows 10 Education N edition <br/>Windows 10 Enterprise N edition <br/>Windows 10 Pro Education N edition | 
| Windows 10 Holographic | Windows 10 Holographic for Business |
| Windows 10 Mobil | Windows 10 Mobile Enterprise |

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="create-the-profile"></a>Skapa profilen

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen. Ange något i stil med `Windows 10 edition upgrade profile` eller `Windows 10 switch off S mode`.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj plattform:  

        - **Windows 10 och senare**

    - **Profiltyp**: Välj **Uppgradering av utgåva**.
    - **Inställningar**: Ange vilka inställningar som du vill konfigurera. En lista med alla inställningar och vad de gör finns i:

        - [Windows 10-uppgradering och S-läge](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. Välj **OK** > **Skapa** för att spara ändringarna. 

Profilen skapas och visas i listan. Kom ihåg att [tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

## <a name="next-steps"></a>Nästa steg

När profilen har skapats är den klar att tilldelas. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Visa uppgraderingen och S-inställningar för [Windows 10](edition-upgrade-windows-settings.md)- och [Windows Holographic for Business](holographic-upgrade.md)-enheter.
