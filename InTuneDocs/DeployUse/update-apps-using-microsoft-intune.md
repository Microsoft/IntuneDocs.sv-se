---
# required metadata

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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Uppdatera appar med Microsoft Intune
Microsoft Intune kan hjälpa dig att hantera appuppdateringar. Använd informationen i det här avsnittet för att förstå hur du kan uppdatera appar när en ny version krävs.

## Så här uppdaterar du appar
När en ny version av en app som du har distribuerat släpps kan du uppdatera och distribuera den senare versionen av programmet med Intune. Du kan endast ersätta en distribution med en senare version av samma program (med samma ID). Du kan inte använda app-uppdateringar för att uppdatera en distribution med ett annat app-paket.

> [!IMPORTANT]
> När du distribuerar en app med en distributionsåtgärd för **Krävd installation** och sedan ändrar distributionsåtgärden till **Tillgänglig installation**, installeras uppdateringar till appen inte automatiskt på enheter som installerade appen innan distributionsändringen gjordes. Om du vill åtgärda problemet kan du göra följande:
> 
> -   Gå till företagsportalen, välj den installerade appen och klicka på **Installera**.
> -   Ändra distributionsåtgärden till **Avinstallera**, och när appen har avinstallerats, distribuera appen igen med en distributionsåtgärd för **Tillgängliga installationer**.

### Så här uppdaterar du en app

1.  Gå till [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) och klicka på **Appar** &gt; **Appar**.

2.  Från listan **Appar** väljer du den app som du vill uppdatera och klickar sedan på **Redigera**.

3.  I guiden **Redigera programvara** anger du ny information för app-paket.

4.  Klicka på **Uppdatera**när du är klar.

När enheter kontroller efter tillgängliga appar nästa gång uppdateras appen automatiskt till den senaste versionen.





<!--HONumber=May16_HO2-->


