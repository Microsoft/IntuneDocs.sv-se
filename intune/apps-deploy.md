---
title: Tilldela appar till grupper i Microsoft Intune
titlesuffix: ''
description: Lär dig hur du tilldelar en Intune-app till grupper av användare eller enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 99eb2c70994fcb2b6ed116530f4a82d8db7bcb9b
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2018
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Tilldela appar till grupper med Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

När du har lagt till en app till Microsoft Intune kan du tilldela appen till användare och enheter.

Du kan tilldela en app till en enhet om enheten hanteras av Intune. 

I följande tabell visas de olika alternativen för att tilldela appar till användare och enheter:

||||
|-|-|-|-|
|&nbsp;|**Enheter som registrerats med Intune**|**Enheter som inte registrerats med Intune**|
|Tilldela till användare|Ja|Ja|
|Tilldela till enheter|Ja|Nej|
|Tilldela omslutna appar eller appar med Intune SDK (för skydd av apprinciper)|Ja|Ja|
|Tilldela appar som är tillgängliga|Ja|Ja|
|Tilldela appar vid behov|Ja|Nej|
|Avinstallera appar|Ja|Nej|
|Ta emot appuppdateringar från Intune|Ja|Nej|
|Slutanvändare installerar tillgängliga appar från företagsportalappen|Ja|Nej|
|Slutanvändare installerar tillgängliga appar från den webbaserade företagsportal|Ja|Ja|

> [!NOTE]
> För närvarande kan du tilldela iOS- och Android-appar (verksamhetsspecifika och butiksköpta appar) till enheter som inte är registrerade med Intune.
>
> För att ta emot app-uppdateringar på enheter som inte är registrerade med Intune, måste enhetsanvändare gå till sin organisations företagsportal och manuellt installera app-uppdateringarna.

## <a name="to-assign-an-app"></a>Så här tilldelar du en app

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I **Intune**-menyn väljer du **Mobilappar**.
4. I avsnittet**Hantera** på menyn, väljer du **Appar**.
5. I fönstret **Appar** välj den app som du vill tilldela.
6. I avsnittet**Hantera** på menyn, väljer du **Tilldelningar**.
7. Välj **Lägg till grupp** för att öppna fönstret **Lägg till grupp** som är relaterat till appen.
8. Välj en **Tilldelningstyp** för den specifika appen:
   - **Tillgänglig för registrerade enheter**: Användarna installerar appen från företagsportalappen eller webbplatsen.
   - **Tillgänglig med eller utan registrering**: Tilldela den här appen till grupper av användare vars enheter inte har registrerats med Intune. Typen **Android for Work-app** stöder inte det här alternativet. 
   - **Obligatoriskt**: Appen installeras på enheter i valda grupper.
   - **Avinstallera**: Appen avinstalleras från enheter i valda grupper.

     > [!NOTE]
     > **Endast för iOS-appar**: Om du har skapat en iOS VPN-profil som innehåller VPN-inställningar per app kan du välja VPN-profilen under **VPN**. VPN-anslutningen öppnas när appen körs. Mer information finns i [VPN-inställningar för iOS-enheter](vpn-settings-ios.md).

9. Välj **Inkluderade grupper** för att välja vilka grupper av användare som ska påverkas av den här apptilldelningen.
10. Klicka på **Välj** när du har valt en eller flera grupper som ska inkluderas.
11. Klicka på **OK** i fönstret **Tilldela** för att slutföra valet av inkluderade grupper.
12. Välj **Exkludera grupper** om du vill undanta grupper av användare så att de inte påverkas av den här apptilldelningen.
13. Om du har valt att undanta grupper i **Välj grupper**, klicka på **Välj**.
14. I fönstret **Lägg till grupp** väljer du **OK**.
15. I appfönstret **Tilldelningar** väljer du **Spara**.

Appen har nu tilldelats till de grupper du valde. Mer information om hur du inkluderar och exkluderar apptilldelningar finns i [Inkludera och exkludera apptilldelningar](apps-inc-exl-assignments.md).

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Lösa konflikter mellan appavsikter

Ibland har samma app tilldelats flera grupper, men med olika avsikter. Informationen i tabellen nedan kan hjälpa dig att förstå resulterande avsikt när detta inträffar:

||||
|-|-|-|
|**Avsikt för grupp 1**|**Avsikt för grupp 2**|**Resulterande avsikt**|
|Nödvändig för användare|Tillgänglig för användare|Nödvändig och Tillgänglig|
|Nödvändig för användare|Inte tillgänglig för användare|Obligatoriskt|
|Nödvändig för användare|Avinstalleras för användare|Obligatoriskt|
|Tillgänglig för användare|Inte tillgänglig för användare|Inte tillgängligt|
|Tillgänglig för användare|Avinstallation av användare|Avinstallera|
|Inte tillgänglig för användare|Avinstalleras för användare|Avinstallera
|Nödvändig för användare|Nödvändig för enhet|Båda finns, hanteras som nödvändig av gateway
|Nödvändig för användare|Avinstalleras för enhet|Båda finns, löses som nödvändig av gateway
|Tillgänglig för användare|Nödvändig för enhet|Båda finns, matchas som nödvändig av gateway (nödvändig och tillgänglig)
|Tillgänglig för användare|Avinstalleras för enhet|Båda finns, matchas som tillgänglig av gateway.<br><br>Appen visas i företagsportalen.<br><br>Appen avinstalleras om den redan har installerats (som nödvändig app med föregående avsikt).<br><br>Om användaren väljer **Installera i företagsportalen** installeras appen och avinstallationen åsidosätts.|
|Inte tillgänglig för användare|Nödvändig för enhet|Obligatoriskt|
|Inte tillgänglig för användare|Avinstalleras för enhet|Avinstallera|
|Avinstalleras för användare|Nödvändig för enhet|Båda finns, löses som nödvändig av gateway|
|Avinstalleras för användare|Avinstalleras för enhet|Både finns, matchas som avinstallation av gateway|
|Nödvändig för enhet|Avinstalleras för enhet|Obligatoriskt|
|Nödvändig och tillgänglig för användare|Tillgänglig för användare|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Avinstalleras för användare|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Inte tillgänglig för användare|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Nödvändig för enhet|Båda finns, nödvändig och tillgänglig
|Nödvändig och tillgänglig för användare|Inte tillgänglig för enhet|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Avinstalleras för enhet|Båda finns, matchas som nödvändig av gateway (nödvändig och tillgänglig)
|Inte tillgänglig för användare|Inte tillgänglig för enhet|Inte tillgängligt|
|Tillgänglig för användare|Inte tillgänglig för enhet|Tillgänglig|
|Nödvändig för användare|Inte tillgänglig för enhet|Obligatoriskt|
|Tillgänglig för användare utan registrering|Nödvändig och tillgänglig för användare|Nödvändig och Tillgänglig
|Tillgänglig för användare utan registrering|Nödvändig för användare|Obligatoriskt
|Tillgänglig för användare utan registrering|Inte tillgänglig för användare|Inte tillgängligt
|Tillgänglig för användare utan registrering|Tillgänglig för användare|Tillgänglig|
|Tillgänglig för användare utan registrering|Nödvändig för enhet|Nödvändig och tillgänglig utan registrering|
|Tillgänglig för användare utan registrering|Inte tillgänglig för enhet|Tillgänglig utan registrering|
|Tillgänglig för användare utan registrering|Avinstalleras för enhet|Avinstalleras och tillgänglig utan registrering.<br><br>Avinstallationsavsikten åsidosätts inte om användaren inte har installerat appen från företagsportalen.<br><br>Om användaren installerar appen från företagsportalen prioriteras installation framför avinstallation.|

> [!NOTE]
> Endast för hanterade iOS Store-appar. När du lägger till dem i Microsoft Intune och tilldelar dem som **Nödvändiga** skapas apparna automatiskt med både avsikten **Nödvändig** och **Tillgänglig**.

## <a name="next-steps"></a>Nästa steg

Mer information om hur du övervakar apptilldelningar finns i [Hur du övervakar appar](apps-monitor.md).
