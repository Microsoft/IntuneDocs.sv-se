---
title: Uppdatera appar | Microsoft Intune
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
ms.sourcegitcommit: 0581d1476fba5bedcdd4446df20f8f92b151f41b
ms.openlocfilehash: 9e5b8f4a467e8e58cc2f8fa495b5f008eee7e35b


---

# Uppdatera appar med Microsoft Intune
Microsoft Intune kan hjälpa dig att hantera appuppdateringar. Använd informationen i det här avsnittet för att förstå hur du kan uppdatera appar när en ny version krävs.

## Så här uppdaterar du appar
När en ny version av en app som du har distribuerat släpps kan du uppdatera och distribuera den senare versionen av programmet med Intune. Du kan endast ersätta en distribution med en senare version av samma program (med samma ID). Du kan inte använda app-uppdateringar för att uppdatera en distribution med ett annat app-paket.

> [!IMPORTANT]
> När du distribuerar en app med en distributionsåtgärd för **Krävd installation** och sedan ändrar distributionsåtgärden till **Tillgänglig installation**, installeras uppdateringar till appen inte automatiskt på enheter som installerade appen innan distributionsändringen gjordes. Om du vill åtgärda problemet kan du göra följande:
> 
> -   Gå till företagsportalen, välj den installerade appen och välj **Installera**.
> -   Ändra distributionsåtgärden till **Avinstallera**, och när appen har avinstallerats, distribuera appen igen med en distributionsåtgärd för **Tillgängliga installationer**.

### Så här uppdaterar du en app

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Appar** &gt; **Appar**.

2.  Från listan **Appar** väljer du den app som du vill uppdatera. Välj sedan **Redigera**.

3.  I guiden **Redigera programvara** anger du ny information för app-paket.

4.  Välj **Uppdatera** när du är klar.

När enheter kontroller efter tillgängliga appar nästa gång uppdateras appen automatiskt till den senaste versionen.
Appar som installerats från ett appaket (affärsspecifika appar) uppgraderas appen automatiskt både för nödvändiga och tillgängliga distributioner, så länge appen har samma identifierare.
För appar som distribueras med en länk till en butik hanteras uppdateringen av den butik som appen hämtats från.






<!--HONumber=Jun16_HO3-->


