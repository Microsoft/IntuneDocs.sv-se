---
title: Uppgradera eller använd S-läge för 10 Windows-enheter med Microsoft Intune – Azure | Microsoft Docs
description: Skapa en enhetsprofil i Microsoft Intune för att uppgradera Windows 10-enheter till andra versioner. Du kan till exempel uppgradera från Windows 10 Professional till Windows 10 Enterprise. Du kan också aktivera eller avaktivera S-läge på en enhet med konfigurationsprofilen. Se även de uppgraderingssökvägar som stöds för Windows 10 Pro, N Edition, Education, Cloud, Enterprise, Core, Holographic och Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f0e4ba42559a068ebefb453aba18060803dc36e0
ms.sourcegitcommit: f3974c810e172f345853dacd7f2ca0abc11b1a5b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/11/2018
ms.locfileid: "44389633"
---
# <a name="use-a-configuration-profile-to-upgrade-windows-10-or-switch-from-s-mode-in-intune"></a>Använd en konfigurationsprofil för att uppgradera Windows 10 eller växla från S-läge i Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Konfigurera en uppgraderingsprofil i Intune för att automatiskt uppgradera enheter som kör Windows 10-versioner till en annan utgåva. Se även uppgraderingssökvägar som stöds.

## <a name="before-you-begin"></a>Innan du börjar
Innan du uppgraderar enheter till den senaste versionen behöver du något av följande:

- En giltig produktnyckel för att installera den uppdaterade versionen av Windows på alla enheter som du riktar principen mot (för Windows 10 Desktop-versioner). Du kan använda antingen multipla aktiveringsnycklar (MAK) eller nyckelhanteringsserver (KMS). För Windows 10 Mobile- och Windows 10 Holographic-versioner kan du använda licensfil från Microsoft som innehåller licensinformationen för att installera den nya Windows-versionen på alla enheter som du riktar principen mot.
- De Windows 10-enheter som du riktar principen mot måste vara registrerade i Microsoft Intune. Du kan inte använda versionsuppgraderingsprincipen för datorer som kör Intune-klientprogrammet.

## <a name="supported-upgrade-paths"></a>Stödda uppgraderingssökvägar
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


<!-- Testing a new table on 3/5/18 

The following lists provide the supported upgrade paths for the Windows 10 edition upgrade profile. The Windows 10 edition to upgrade to is in bold followed by the list of supported editions that you can upgrade from:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N edition**    
- Windows 10 Pro N edition
- Windows 10 Pro Education N edition
- Windows 10 Cloud N edition
- Windows 10 Enterprise N edition
- Windows 10 Core N edition
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N edition**
- Windows 10 Cloud N edition
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile -->

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

## <a name="upgrade-the-edition"></a>Uppgradera versionen

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange ett **namn** och en **beskrivning** för profilen. Ange något i stil med `Windows 10 edition upgrade`
4. För **Plattform** väljer du **Windows 10 och senare**.
5. För **Profiltyp** väljer du **Uppgradering av utgåva**.
6. I egenskaperna **Uppgradering av utgåva** anger du följande inställningar:

   - **Utgåva att uppgradera till**: Välj vilken Windows 10-utgåva som du uppgraderar till. De enheter som omfattas av principen uppgraderas till den valda utgåvan.
   - **Produktnyckel**: Ange produktnyckeln som du har fått från Microsoft. När du har skapat en princip som innehåller en produktnyckel går den inte att uppdatera och den är dold av säkerhetsskäl. Om du vill ändra produktnyckeln måste du ange hela nyckeln igen.
   - **Licensfil**: för **Windows 10 Holographic för företag** eller **Windows 10 Mobile-version** väljer du **Bläddra** och går till den licensfil som du har fått från Microsoft. Licensfilen innehåller licensinformation för de utgåvor som du uppgraderar målenheterna till.

7. Klicka på **OK** för att spara ändringarna. Välj **Skapa** för att skapa profilen.

## <a name="switch-out-of-s-mode"></a>Växla från S-läge

[S-läget för Windows 10](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) är utformat för säkerhet och prestanda. Om dina enheter endast kör appar från Microsoft Store kan du använda S-läge för att skydda dina enheter. Om dina enheter använder appar som inte är tillgängliga i Microsoft Store kommer du att växla från S-läget. Att lämna S-läget kan inte ångras. Och när du har lämnat S-läget kan du inte gå tillbaka till S-läget för Windows 10.

Följande steg visar hur du skapar en profil som kontrollerar S-läget på Windows 10-enheter (1809 eller senare).

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange ett **namn** och en **beskrivning** för profilen. Ange något i stil med `Windows 10 switch off S mode`
4. För **Plattform** väljer du **Windows 10 och senare**.
5. För **Profiltyp** väljer du **Uppgradering av utgåva**.
6. Välj **Växla läge (endast Windows Insider)** och välj egenskapen **Växla från S-läge**. Alternativen är:

    - **Ingen konfiguration**: en enhet i S-läge förblir i S-läge. En slutanvändare kan ange att enheten ska växla från S-läget.
    - **Bli kvar i S-läge**: användaren kan inte växla från S-läget.
    - **Växla**: Växlar enheten från S-läge.

7. Klicka på **OK** för att spara ändringarna. Välj **Skapa** för att skapa profilen.

Profilen skapas och visas i profilerna.

## <a name="next-steps"></a>Nästa steg

[Tilldela den här profilen](device-profile-assign.md) till dina grupper.

>[!NOTE]
>Om du senare tar bort principtilldelningen återställs inte Windows-versionen på enheten och den fortsätter att fungera normalt.
