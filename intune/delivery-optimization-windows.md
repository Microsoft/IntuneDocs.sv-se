---
title: Leveransoptimeringsinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera hur programuppdateringar ska levereras till dina enheter med de leveransoptimerande molntjänster som är tillgängliga i Windows 10 och senare. Skapa en enhetskonfigurationsprofil i Intune med vilken du kan installera uppdateringar från Internet. Se även hur du kan ersätta befintliga uppdateringsringar med en leveransoptimeringsprofil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a59cab5f709897e064b315193b292cb46dc2f2e
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831555"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Inställningar för leveransoptimering för Windows 10 (och senare) i Microsoft Intune

> [!NOTE]
> **Programuppdateringar – Windows 10-uppdateringsringar** har ersatts av inställningarna för **leveransoptimering**. Du kan ändra dina befintliga uppdateringsringar så att du kan använda inställningarna för **leveransoptimering**. [Flytta befintliga uppdateringsringar till leveransoptimering](#move-existing-update-rings-to-delivery-optimization) (i den här artikeln) visar stegen. 


Den här funktionen gäller för följande plattform:

- Windows 10 och senare

Den här artikeln visar en lista och beskriver alla leveransoptimeringsinställningar som du kan konfigurera för Windows 10-enheter. Dessa inställningar läggs till en profil för enhetskonfiguration som sedan tilldelas eller distribueras till dina enheter med Microsoft Intune.

[Uppdateringar av leveransoptimering](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) är en bra resurs där du kan lära dig mer om leveransoptimering i Windows 10.

## <a name="create-the-profile"></a>Skapa profilen

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.

2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.

3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj plattform:  

        - **Windows 10 och senare**

    - **Profiltyp**: Välj **Leveransoptimering**.
    - **Inställningar**: Välj hur du vill att uppdateringarna laddas ner. Alternativen är: 

        - **Inte konfigurerad**: Slutanvändarna uppdaterar sina enheter med egna metoder, vilket kan vara att använda **Windows-uppdateringar** eller de inställningar för **leveransoptimering** som är tillgängliga i operativsystemet.
        - **Endast HTTP, ingen peering**: Hämta endast uppdateringar från Internet. Hämta inte uppdateringar från andra datorer i nätverket (vilket kallas peering eller peer-to-peer).
        - **HTTP blandat med peering bakom samma NAT**: Hämta uppdateringar från Internet och från andra datorer i nätverket. 
        - **HTTP blandat med peering i en privat grupp**: Peering sker på enheter på samma Active Directory-webbplats (om sådan finns) eller i samma domän. När du väljer det här alternativet överskrider peeringen dina NAT IP-adresser.
        - **HTTP blandat med Internet-peering**: Hämta uppdateringar från Internet och från andra datorer i nätverket.
        - **Läge för enkel nedladdning utan peering**: Hämtar uppdateringar från Internet, direkt från uppdateringsägare som Microsoft. Molntjänsterna för leveransoptimering kontaktas inte.
        - **Förbigångsläge**: Hämta uppdateringar genom att använda Background Intelligent Transfer Service (BITS). Använd inte leveransoptimering.

4. Välj **OK** > **Skapa** när du är klar för att spara dina ändringar.

Profilen skapas och visas i listan. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Flytta befintliga uppdateringsringar till leveransoptimering

**Programuppdateringar – Windows 10-uppdateringsringar** har ersatts av inställningarna för **leveransoptimering**. Du kan lätt ändra dina befintliga uppdateringsringar så att du kan använda inställningarna för **leveransoptimering**. Steg:

1. Skapa en konfigurationsprofil för leveransoptimering:

    1. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil** i Intune.
    2. Ange följande egenskaper:

        - **Namn**: Ange ett beskrivande namn på den nya profilen.
        - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
        - **Plattform**: Välj **Windows 10 och senare**.
        - **Profiltyp**: Välj **Leveransoptimering**.
        - **Inställningar**: När det gäller **Leveransoptimeringens nedladdningsläge** väljer du samma läge som används av den befintliga programuppdateringsringen. Alternativen är:
            - **Inte konfigurerat**
            - **Endast HTTP, ingen peering**
            - **HTTP blandat med peering bakom samma NAT**
            - **HTTP blandat med peering i en privat grupp**
            - **HTTP blandat med Internet-peering**
            - **Läge för enkel nedladdning utan peering**
            - **Förbigångsläge**

2. Tilldela den här nya profilen till samma enheter och användare som den befintliga programuppdateringsringen. I [Tilldela profilen](device-profile-assign.md) listas stegen.

3. Ta bort konfiguration för den befintliga programringen:
    1. Gå till **Programuppdateringar** > Windows 10-uppdateringsringar i Intune.
    2. Välj din uppdateringsring i listan.
    3. Gå till inställningarna och ställ in **Leveransoptimeringens nedladdningsläge** på **Inte konfigurerad**.
    4. **OK** > **Spara** ändringarna.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
