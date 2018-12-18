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
ms.openlocfilehash: 1b83a380620704e9e3f616cee77b33d577c86c0d
ms.sourcegitcommit: 88f760abcea7348a0c6d00b533b54a6ff68d3985
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977277"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Inställningar för leveransoptimering för Windows 10 (och senare) i Microsoft Intune

Den här artikeln visar en lista och beskriver alla leveransoptimeringsinställningar som du kan konfigurera för Windows 10-enheter. Dessa inställningar läggs till en profil för enhetskonfiguration som sedan tilldelas eller distribueras till dina enheter med Microsoft Intune. 

[Uppdateringar av leveransoptimering](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) är en bra resurs där du kan lära dig mer om leveransoptimering i Windows 10.

## <a name="settings"></a>Inställningar

**Leveransoptimering av nedladdningsläge**: Välj hur uppdateringar ska levereras till dina enheter. Alternativen är:

- **Inte konfigurerad**: Slutanvändarna uppdaterar sina enheter med egna metoder, vilket kan vara att använda **Windows-uppdateringar** eller de inställningar för **leveransoptimering** som är tillgängliga i operativsystemet.
- **Endast HTTP, ingen peering**: Hämta endast uppdateringar från Internet. Hämta inte uppdateringar från andra datorer i nätverket (vilket kallas peering eller peer-to-peer).
- **HTTP blandat med peering bakom samma NAT, HTTP blandat med peering i privat grupp**: Hämta uppdateringar från Internet och från andra datorer i nätverket. Peering sker på enheter på samma Active Directory-webbplats (om sådan finns) eller i samma domän. När du väljer det här alternativet överskrider peeringen dina NAT IP-adresser.
- **HTTP blandat med Internet-peering**: Hämta uppdateringar från Internet och från andra datorer i nätverket.
- **Läge för enkel nedladdning utan peering**: Hämtar uppdateringar från Internet, direkt från uppdateringsägare som Microsoft. Molntjänsterna för leveransoptimering kontaktas inte.
- **Förbigångsläge**: Hämta uppdateringar genom att använda Background Intelligent Transfer Service (BITS). Använd inte leveransoptimering.

## <a name="move-from-existing-update-rings-to-delivery-optimization"></a>Flytta från befintliga uppdateringsringar till leveransoptimering

**Programuppdateringar – Windows 10-uppdateringsringar** har ersatts av inställningarna för **leveransoptimering**. Du kan lätt ändra dina befintliga uppdateringsringar så att du kan använda inställningarna för **leveransoptimering**. Steg:

1. Skapa en konfigurationsprofil för leveransoptimering:

    1. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil** i Intune.
    2. Ange ett **namn** och en **beskrivning** för profilen.
    3. Välj **Windows 10 och senare** som **Plattform**. Välj **leveransoptimering** som **Profiltyp**.
    4. Välj **Inställningar**. När det gäller **Leveransoptimeringens nedladdningsläge** väljer du samma läge som används av den befintliga programuppdateringsringen. Alternativen är:
        - **Inte konfigurerat**
        - **Endast HTTP, ingen peering**
        - **HTTP blandat med peering bakom samma NAT HTTP blandat med peering i privat grupp**
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
