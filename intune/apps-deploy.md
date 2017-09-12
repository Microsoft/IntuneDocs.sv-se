---
title: Tilldela appar till grupper
titlesuffix: Azure portal
description: "När du har lagt till en app till Intune, behöver du tilldela den till grupper med användare eller enheter.”"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 51abb6daad11b9d6036396dcc5a5ce8f2a2c4ac4
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Tilldela appar till grupper med Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

När du har lagt till en app i Intune kan du tilldela det till användare och enheter.

Appar kan tilldelas till enheter oavsett om de hanteras av Intune eller inte. Använd följande tabell för att förstå de olika alternativen för att tilldela appar till användare och enheter:

||||
|-|-|-|-|
|&nbsp;|Enheter registrerade med Intune|Enheter ej registrerade med Intune|
|Tilldela till användare|Ja|Ja|
|Tilldela till enheter|Ja|Nej|
|Tilldela omslutna appar eller appar med Intune SDK (för appskyddsprinciper)|Ja|Ja|
|Tilldela appar som är tillgängliga|Ja|Ja|
|Tilldela appar vid behov|Ja|Nej|
|Avinstallera appar|Ja|Nej|
|Slutanvändarna installerar tillgängliga appar från företagsportalappen|Ja|Nej|
|Slutanvändarna installerar tillgängliga appar från den webbaserade företagsportalen|Ja|Ja|

> [!NOTE]
> För närvarande kan du tilldela iOS- och Android-appar (både branschspecifika och butiksköpta appar) till enheter som inte har registrerats med Intune.

## <a name="how-to-assign-an-app"></a>Så här tilldelar du en app

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.
1. Välj **Hantera** > **Appar** i arbetsbelastningen **Mobilappar**.
2. I listan på appbladet klickar du på den app som du vill tilldela.
3. På bladet <*appnamn*>- **Översikt** väljer du **Hantera** > **Tilldelningar**.
4. Välj **Välj grupper**, klicka sedan på bladet **Välj grupper** och välj de Azure AD-grupper som du vill tilldela appen.
5. För varje app som du väljer ska du också välja en av följande **tilldelningstyper** för appen:
    - **Tillgänglig** – Användarna installerar appen från företagsportalappen eller webbplatsen.
    - **Inte tillämpligt** – Appen varken installeras eller visas i företagsportalen.
    - **Obligatoriskt** – Appen installeras på enheter i valda grupper.
    - **Avinstallera** – Appen avinstalleras från enheter i valda grupper.
    - **Tillgänglig med eller utan registrering** – Tilldela den här appen till grupper av användare vars enheter inte har registrerats med Intune.
6. **Endast för iOS-appar** – Om du har skapat en iOS VPN-profil som innehåller VPN-inställningar per app kan du välja det under **VPN**. VPN-anslutningen öppnas när appen körs. Mer information finns i [VPN-inställningar för iOS-enheter](vpn-settings-ios.md).
6. När du är klar väljer du **Spara**.

Appen har nu tilldelats till de grupper du valde.

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Lösa konflikter mellan appavsikter

Ibland har samma app tilldelats flera grupper, men med olika avsikter. I dessa fall kan du använda följande tabellen till att utröna den resulterande avsikten.

||||
|-|-|-|
|Avsikt för grupp 1|Avsikt för grupp 2|Resulterande avsikt|
|Nödvändig för användare|Tillgänglig för användare|Nödvändig och Tillgänglig|
|Nödvändig för användare|Inte tillgänglig för användare|Obligatoriskt|
|Nödvändig för användare|Avinstallation av användare|Obligatoriskt|
|Tillgänglig för användare|Inte tillgänglig för användare|Inte tillgängligt|
|Tillgänglig för användare|Avinstallation av användare|Avinstallera|
|Inte tillgänglig för användare|Avinstalleras för användare|Avinstallera
|Nödvändig för användare|Nödvändig för enhet|Båda finns, hanteras som nödvändig av gateway 
|Nödvändig för användare|Avinstalleras för enhet|Båda finns, matchas som nödvändig av gateway 
|Tillgänglig för användare|Nödvändig för enhet|Båda finns, matchas som nödvändig av gateway (nödvändig och tillgänglig)
|Tillgänglig för användare|Avinstalleras för enhet|Båda finns, matchas som tillgänglig av gateway.<br>Appen visas i företagsportalen.<br>Appen avinstalleras om den redan har installerats (som nödvändig app med föregående avsikt).<br>Avinstallationsavsikten åsidosätts dock om appen installeras genom att användaren klickar på Installera i företagsportalen.|
|Inte tillgänglig för användare|Nödvändig för enhet|Obligatoriskt|
|Inte tillgänglig för användare|Avinstalleras för enhet|Avinstallera|
|Avinstalleras för användare|Nödvändig för enhet|Båda finns, matchas som nödvändig av gateway|
|Avinstalleras för användare|Avinstalleras för enhet|Både finns, matchas som avinstallation av gateway|
|Nödvändig för enhet|Avinstalleras för enhet|Obligatoriskt|
|Nödvändig och tillgänglig för användare|Tillgänglig för användare|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Avinstalleras för användare|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Inte tillgänglig för användare|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Nödvändig för enhet|Båda finns, nödvändig och tillgänglig
|Nödvändig och tillgänglig för användare|Inte tillgänglig för enhet|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Avinstalleras för enhet|Båda finns, matchas som nödvändig av gateway. Nödvändig och tillgänglig
|Inte tillgänglig för användare|Inte tillgänglig för enhet|Inte tillgängligt|
|Tillgänglig för användare|Inte tillgänglig för enhet|Tillgänglig|
|Nödvändig för användare|Inte tillgänglig för enhet|Obligatoriskt|
|Tillgänglig för användare utan registrering|Nödvändig och tillgänglig för användare|Nödvändig och Tillgänglig
|Tillgänglig för användare utan registrering|Nödvändig för användare|Obligatoriskt
|Tillgänglig för användare utan registrering|Inte tillgänglig för användare|Inte tillgängligt
|Tillgänglig för användare utan registrering|Tillgänglig för användare|Tillgänglig|
|Tillgänglig för användare utan registrering|Nödvändig för enhet|Nödvändig och tillgänglig utan registrering|
|Tillgänglig för användare utan registrering|Inte tillgänglig för enhet|Tillgänglig utan registrering|
|Tillgänglig för användare utan registrering|Avinstalleras för enhet|Avinstalleras och tillgänglig utan registrering.<br>Avinstallationsavsikten åsidosätts inte om användaren inte har installerat appen från företagsportalen.<br>Om användaren installerar appen från företagsportalen prioriteras installation framför avinstallation.|

>[!NOTE]
>Endast för hanterade iOS Store-appar. När du lägger till dem i Intune och tilldelar dem som Nödvändiga skapas de automatiskt med både avsikterna Nödvändig och Tillgänglig.

## <a name="next-steps"></a>Nästa steg

Du hittar mer information i [Hur du övervakar appar](apps-monitor.md) som hjälper dig att övervaka apptilldelningar.
