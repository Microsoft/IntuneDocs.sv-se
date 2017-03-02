---
title: "Tilldela appar till grupper | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: När du har lagt till en app till Intune, behöver du tilldela den till grupper av användare eller enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 638ad0d87c19c9e40e96b42d18e5c4342f40a156
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Tilldela appar till grupper med Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

När du har lagt till en app till Intune, behöver du dela den till användare och enheter. Det gör du genom att tilldela den.

Appar kan tilldelas till enheter oavsett om de hanteras av Intune eller inte. Använd följande tabell för att förstå de olika alternativen för att tilldela appar till användare och enheter:

||||
|-|-|-|-|
|&nbsp;|Enheter registrerade med Intune|Enheter ej registrerade med Intune|
|Tilldela till användare|Ja|Ja|
|Tilldela till enheter|Ja|Nej|
|Tilldela omslutna appar eller appar med Intune SDK (för appskyddsprinciper)|Ja|Ja|
|Tilldela appar som är tillgängliga|Ja|Ja|
|Tilldela appar vid behov|Ja|Nej|
|Avinstallera appar|Ja|Ja|
|Slutanvändarna installerar tillgängliga appar från företagsportalappen|Ja|Nej|
|Slutanvändarna installerar tillgängliga appar från den webbaserade företagsportalen|Ja|Ja|

> [!NOTE]
> För närvarande kan du tilldela iOS- och Android-appar (både branschspecifika och butiksköpta appar) till enheter som inte har registrerats med Intune.

## <a name="how-to-assign-an-app"></a>Så här tilldelar du en app

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Hantera appar** på **Intune**-bladet.
1. Välj **Hantera** > **Appar** i arbetsbelastningen **Hantera appar**.
2. I listan på appbladet klickar du på den app som du vill tilldela.
3. På bladet <*appnamn*>- **Översikt** väljer du **Hantera** > **Tilldelningar**.
4. Välj **Välj grupper**, klicka sedan på bladet **Välj grupper** och välj de Azure AD-grupper som du vill tilldela appen.
5. För varje app som du väljer ska du också välja en av följande **tilldelningstyper** för appen:
    - **Tillgänglig** – Användarna installerar appen från företagsportalappen eller webbplatsen.
    - **Inte tillämpligt** – Appen varken installeras eller visas i företagsportalen.
    - **Obligatoriskt** – Appen installeras på enheter i valda grupper.
    - **Avinstallera** – Appen avinstalleras från enheter i valda grupper.
    - **Tillgänglig med eller utan registrering** – Tilldela den här appen till grupper av användare vars enheter inte har registrerats med Intune. Se tabellen ovan för hjälp.
6. När du är klar väljer du **Spara**.

Appen har nu tilldelats den grupp som du valde.

Du hittar mer information i [Hur du övervakar appar](monitor-apps.md) som hjälper dig att övervaka apptilldelningar.

