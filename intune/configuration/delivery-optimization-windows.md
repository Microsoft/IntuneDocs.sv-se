---
title: Leveransoptimeringsinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera hur Windows 10-enheter som du hanterar med Intune använder leveransoptimering. Skapa en enhetskonfigurationsprofil i Intune med vilken du kan installera uppdateringar från Internet. Se även hur du kan ersätta befintliga uppdateringsringar med en leveransoptimeringsprofil.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/10/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 9fb4aab6b02c6ad6a5d2f18ca9d15beafc12d58a
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124817"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Inställningar för leveransoptimering i Microsoft Intune

Med Intune kan du använda inställningar för leveransoptimering till dina Windows 10-enheter för att minska bandbreddsförbrukningen när enheterna laddar ned program och uppdateringar. Konfigurera leveransoptimering som en del av dina enhetskonfigurationsprofiler.  

Den här artikeln beskriver hur du konfigurerar inställningar för leveransoptimering som en del av en profil för enhetskonfiguration. När du har skapat en profil tilldelar eller distribuerar du profilen till Windows 10-enheterna. 

En lista med de inställningar för leveransoptimering som Intune stöder finns i [Inställningar för leveransoptimering för Intune](../delivery-optimization-settings.md).  

Information om leveransoptimering i Windows 10 finns i [Uppdateringar av leveransoptimering](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) i Windows-dokumentationen.  

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.

3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **Windows 10 och senare**.
    - **Profiltyp**: Välj **Leveransoptimering**.

4. Välj **Inställningar** > **Konfigurera** och definiera hur du vill att uppdateringar och appar ska laddas ned. Information om tillgängliga inställningar finns i [Inställningar för leveransoptimering för Intune](../delivery-optimization-settings.md).

5. Välj **OK** > **Skapa** när du är klar för att spara dina ändringar.

Profilen skapas och visas i listan. Sedan [tilldelar du profilen](device-profile-assign.md) och [övervakar dess status](device-profile-monitor.md).

<!-- ## Move existing update rings to delivery optimization

**Delivery optimization** settings replace **Software updates – Windows 10 Update Rings**. Your existing update rings can be easily changed to use the **Delivery optimization** settings. To maintain the same settings when you create a delivery optimization profile, use the same *Delivery optimization download mode* and then set the same settings as you already use. However, you can choose to reconfigure delivery optimization settings to take advantage of the full range of addition settings that the Delivery Optimization profile can manage. 
-->

## <a name="remove-delivery-optimization-from-windows-10-update-rings"></a>Ta bort leveransoptimering från Windows 10-uppdateringsgrupper

Leveransoptimering konfigurerades tidigare som en del av programuppdateringsgrupperna. Från och med februari 2019 konfigureras inställningarna för leveransoptimering som en del av en enhetskonfigurationsprofil med leveransoptimering, med ytterligare inställningar som påverkar mer än leveransen av programuppdateringar till enheter. Om du inte redan har gjort det tar du bort inställningen för leveransoptimering från dina uppdateringsgrupper genom att ange den som *Inte konfigurerad*. Sedan använder du en leveransoptimeringsprofil för att hantera det större intervallet av tillgängliga alternativ.

1. Skapa en enhetskonfigurationsprofil för leveransoptimering:

    1. I administrationscentret för Microsoft Endpoint Manager väljer du **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
    2. Ange följande egenskaper:

        - **Namn**: Ange ett beskrivande namn på den nya profilen.
        - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
        - **Plattform**: Välj **Windows 10 och senare**.
        - **Profiltyp**: Välj **Leveransoptimering**.
        - **Inställningar**: För **Nedladdningsläge för leveransoptimering** väljer du samma läge som används av den befintliga programuppdateringsringen såvida du inte vill ändra de inställningar som du tillämpar på dina enheter. Alternativen är:
            - **Inte konfigurerat**
            - **Endast HTTP, ingen peering**
            - **HTTP blandat med peering bakom samma NAT**
            - **HTTP blandat med peering i en privat grupp**
            - **HTTP blandat med Internet-peering**
            - **Läge för enkel nedladdning utan peering**
            - **Förbigångsläge**
    3. Konfigurera eventuella ytterligare inställningar som du vill hantera.

2. Tilldela den här nya profilen till samma enheter och användare som den befintliga programuppdateringsringen. I [Tilldela profilen](device-profile-assign.md) listas stegen.

3. Ta bort konfiguration för den befintliga programringen:
    1. I administrationscentret för Microsoft Endpoint Manager går du till **Programuppdateringar** > Windows 10-uppdateringsringar.
    2. Välj din uppdateringsring i listan.
    3. Gå till inställningarna och ställ in **Leveransoptimeringens nedladdningsläge** på **Inte konfigurerad**.
    4. **OK** > **Spara** ändringarna.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).  
Visa [inställningarna för leveransoptimering](../delivery-optimization-settings.md) för Intune.
