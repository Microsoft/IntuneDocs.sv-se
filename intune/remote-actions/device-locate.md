---
title: Hitta borttappade iOS-enheter med Microsoft Intune – Azure | Microsoft Docs
description: Leta upp förlorade eller stulna iOS-enheter med hjälp av funktionen för att hitta enhet i Microsoft Intune. Få information om säkerhet och sekretess när du använder åtgärden för att hitta enhet.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c438ebeaae8a7259efb74089f51a6ca92003cfea
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509477"
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Hitta borttappade eller stulna iOS-enheter med Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Med åtgärden **Hitta enhet** kan du visa platsen för en förlorad eller stulen iOS-enhet på en karta. Enheten måste vara i övervakat läge. Innan du använder åtgärden ser du till att enheten är i [borttappat läge](device-lost-mode.md).

## <a name="supported-platforms"></a>Plattformar som stöds

- iOS 9.3 och senare

Den här funktionen stöds inte för följande system: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Hitta en förlorad eller stulen enhet

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Enheter** och sedan **Alla enheter**.
4. Välj en iOS-enhet i listan över de enheter du hanterar och välj **...Mer**. Välj sedan fjärråtgärden **Hitta enhet**.
5. När enheten har hittats visas dess plats i **Hitta enhet**.
    ![Skärmbild för Hitta enhet med Intune i Azure](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>Aktivera ljudavisering för borttappat läge på en iOS-enhet

Om någon har tappat bort sin iOS 9.3-enhet eller senare enhet kan du via fjärranslutning utlösa en ljudavisering på enheten så att användaren kan hitta den. Enheten måste vara i [Borttappat läge](device-lost-mode.md).

I [Intune i Azure Portal](https://aka.ms/intuneportal), välj **Enheter** > **Alla enheter** > välj en iOS-enhet > **Översikt**  >  **Mer** > **Spela upp ljud för Borttappat läge (övervaka endast)** .

Ljudet fortsätter att spelas upp tills användaren inaktiverar ljudet på enheten eller enheten tas bort från Borttappat läge.


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Information om säkerhet och sekretess för åtgärderna för borttappat läge och hitta enhet
- Ingen platsinformation för enheten skickas till Intune förrän du har aktiverat den här åtgärden.
- När du använder åtgärden Hitta enhet kan enhetens latitud- och longitudkoordinater hämtas med hjälp av Graph API.
- Data lagras i 24 timmar och tas sedan bort. Du kan inte ta bort platsdata manuellt.
- Platsinformationen krypteras både under lagring och vid överföring.
- När du konfigurerar borttappat läge kan du anpassa ett meddelande som visas på låsskärmen. Ta med information i meddelandet som hjälper den som hittar enheten att återlämna den.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för aktivering av Hitta enhet öppnar du **Enheter** och väljer **Enhetsåtgärder**.
