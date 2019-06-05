---
title: Leveransoptimeringsinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera hur Windows 10-enheter som du hanterar med Intune använder leveransoptimering. Skapa en enhetskonfigurationsprofil i Intune med vilken du kan installera uppdateringar från Internet. Se även hur du kan ersätta befintliga uppdateringsringar med en leveransoptimeringsprofil.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 4190d84fda46e4be3cdc4c4f7bfe4ac8a1852ebc
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373950"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Inställningar för leveransoptimering i Microsoft Intune

Med Intune kan du använda inställningar för leveransoptimering för dina Windows 10-enheter för att minska bandbreddsförbrukningen när de enheterna laddar ned program och uppdateringar. Leveransoptimering konfigureras som en del av dina profiler för enhetskonfiguration.  

Den här artikeln beskriver hur du konfigurerar inställningar för leveransoptimering som en del av en profil för enhetskonfiguration. När du har skapat en profil tilldelar eller distribuerar du profilen till Windows 10-enheterna. 

En lista över inställningar för leveransoptimering som Intune stöder finns i [Inställningar för leveransoptimering för Intune](delivery-optimization-settings.md).  

Information om leveransoptimering i Windows 10 finns i [Uppdateringar av leveransoptimering](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) i Windows-dokumentationen.  


> [!NOTE]
> **Programuppdateringar – Windows 10-uppdateringsringar** har ersatts av inställningarna för **leveransoptimering**. Du kan ändra dina befintliga uppdateringsringar så att du kan använda inställningarna för **leveransoptimering**. [Flytta befintliga uppdateringsringar till leveransoptimering](#move-existing-update-rings-to-delivery-optimization) (i den här artikeln) 
## <a name="create-the-profile"></a>Skapa profilen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.

3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj plattform:  

        - **Windows 10 och senare**

    - **Profiltyp**: Välj **Leveransoptimering**.
    - **Inställningar**: Konfigurera inställningar som definierar hur du vill att uppdateringar och appar ska laddas ned. Information om tillgängliga inställningar finns i [Inställningar för leveransoptimering för Intune](delivery-optimization-settings.md).

4. Välj **OK** > **Skapa** när du är klar för att spara dina ändringar.

Profilen skapas och visas i listan. Sedan [tilldelar du profilen](device-profile-assign.md) och [övervakar dess status](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Flytta befintliga uppdateringsringar till leveransoptimering

Inställningarna för **leveransoptimering** ersätter **Programuppdateringar – Windows 10-uppdateringsringar**. Du kan lätt ändra dina befintliga uppdateringsringar så att du kan använda inställningarna för **leveransoptimering**. Om du vill behålla samma inställningar när du skapar en profil för leveransoptimering använder du samma *Nedladdningsläge för leveransoptimering* och anger sedan samma inställningar som du redan använder. Du kan dock välja att konfigurera om inställningar för leveransoptimering för att dra nytta av ett komplett utbud av ytterligare inställningar som profilen för leveransoptimering kan hantera.

1. Skapa en konfigurationsprofil för leveransoptimering:

    1. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil** i Intune.
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
1. Tilldela den här nya profilen till samma enheter och användare som den befintliga programuppdateringsringen. I [Tilldela profilen](device-profile-assign.md) listas stegen.

3. Ta bort konfiguration för den befintliga programringen:
    1. Gå till **Programuppdateringar** > Windows 10-uppdateringsringar i Intune.
    2. Välj din uppdateringsring i listan.
    3. Gå till inställningarna och ställ in **Leveransoptimeringens nedladdningsläge** på **Inte konfigurerad**.
    4. **OK** > **Spara** ändringarna.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).  
Visa [inställningarna för leveransoptimering](delivery-optimization-settings.md) för Intune.
