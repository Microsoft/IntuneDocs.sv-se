---
title: Uppdatera appar
description: "I det här avsnittet beskrivs hur du uppdaterar appar när en ny version krävs."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d974a3c8fd69ee970991af96afe2011c6d07db2a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="update-apps-using-microsoft-intune"></a>Uppdatera appar med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune kan hjälpa dig att hantera appuppdateringar. I det här avsnittet beskrivs hur du uppdaterar appar när en ny version krävs.

## <a name="how-to-update-apps"></a>Så här uppdaterar du appar
När det släpps en ny version av en app som du har distribuerat kan du uppdatera och distribuera den nya versionen med Intune. Du kan endast ersätta en distribution med en senare version av samma program (som har samma ID). Du kan inte använda app-uppdateringar för att uppdatera en distribution med ett annat app-paket.

### <a name="app-identifiers"></a>Appidentifierare
En appidentifierare är en egenskap som unikt identifierar en app. Du kan inte installera flera exemplar av en app med samma identifierare. Några exempel på appidentifierare:

- **iOS** – Paket-ID (till exempel com.microsoft.excel)
- **Android** – Paket-ID (till exempel com.microsoft.excel)
- **Windows Phone** – (xap installer) Använd produkt-ID (GUID)
- **Windows** (appx/appxbundle) – Använd fullständigt paketnamn



> [!IMPORTANT]
> När du distribuerar en app med en distributionsåtgärd för **Krävd installation** och sedan ändrar distributionsåtgärden till **Tillgänglig installation**, installeras uppdateringar till appen inte automatiskt på enheter som installerade appen innan distributionsändringen gjordes. Om du vill åtgärda problemet kan du göra följande:
>
> -   Gå till företagsportalen, välj den installerade appen och välj **Installera**.
> -   Ändra distributionsåtgärden till **Avinstallera**, och när appen har avinstallerats, distribuera appen igen med en distributionsåtgärd för **Tillgängliga installationer**.

### <a name="to-update-an-app"></a>Så här uppdaterar du en app

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Appar** &gt; **Appar**.

2.  Från listan **Appar** väljer du den app som du vill uppdatera. Välj sedan **Redigera**.

3.  I guiden **Redigera programvara** anger du ny information för app-paket.

4.  Välj **Uppdatera** när du är klar.

När enheter kontroller efter tillgängliga appar nästa gång uppdateras appen automatiskt till den senaste versionen.
För appar som har installerats från ett appaket (affärsspecifika appar) uppgraderas appen automatiskt för både nödvändiga och tillgängliga distributioner, så länge appen har samma identifierare.

För appar som distribueras med en länk till en butik hanteras uppdateringen av den butik som appen hämtats från.
