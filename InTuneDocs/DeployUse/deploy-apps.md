---
title: Distribuera appar | Microsoft Intune
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.sourcegitcommit: e6b995118e66fd146a68b49ce4decdcbd1fe3572
ms.openlocfilehash: a68cb85602bd585539147c7d7d38c0d906f2b1f7


---

# Distribuera appar med Microsoft Intune

Det här avsnittet förklarar några av de begrepp som du behöver förstå innan du börjar distribuera appar med Microsoft Intune.


## Appdistributionsåtgärder
När du distribuerar appar kan du välja någon av följande distributionsåtgärder:

-   **Nödvändig installation** – Appen installeras på enheten utan att det krävs någon åtgärd från slutanvändaren.

    > [!TIP] När det gäller iOS-enheter som inte är i övervakat läge, samt alla Android-enheter, måste användaren godkänna apperbjudandet innan appen kan installeras.
    > 
    >  Om en slutanvändare avinstallerar en app som du har distribuerat som en nödvändig installation installeras appen automatiskt om av Intune efter nästa inventeringscykel, som vanligtvis sker var sjunde dag.

-   **Tillgänglig installation** – Appen visas i företagsportalen och slutanvändare kan installera den på begäran.

-   **Avinstallera** – Appen avinstalleras från enheten.

-   **Ej tillämpligt** – Appen visas inte i företagsportalen och installeras inte på några enheter.

#### Distributionsåtgärder som är tillgängliga för olika typer av installationsprogram

|Installationstyp|Nödvändig installation|Tillgänglig installation|Avinstallera|Inte tillämpligt|
|------------------|--------------------|---------------------|-------------|------------------|
|Windows-app-paket (distribuerad till en användargrupp)|Ja|Ja|Ja|Ja|
|Windows-appaket (distribuerad till en enhetsgrupp)|Ja|Nej|Ja|Ja|
|App-paket för mobila enheter (distribuerad till en användargrupp)|Ja|Ja|Ja|Ja|
|App-paket för mobila enheter (distribuerad till en enhetsgrupp)|Ja|Nej|Ja|Ja|
|Windows Installer (distribuerad till en användargrupp)|Nej|Ja|Nej|Ja|
|Windows Installer (distribuerad till en enhetsgrupp)|Ja|Nej|Ja|Ja|
|Extern länk (distribuerad till en användargrupp)|Nej|Ja|Nej|Ja|
|Extern länk (distribuerad till en enhetsgrupp)|Nej|Nej|Nej|Nej|
|Hanterad iOS-app från App Store (distribuerad till en användargrupp)|Ja|Ja|Ja|Ja|
|Hanterad iOS-app från App Store (distribuerad till en enhetsgrupp)|Ja|Nej|Ja|Ja|
> [!TIP] När du distribuerar appar, om du väljer både användar- och enhetsgrupper, kan du bara distribuera appen som en **Tillgänglig installation**.

## Distributionskonflikter
När två distributioner, med samma distributionsåtgärd, tas emot av en enhet gäller följande regler:

-   Distributioner till en enhetsgrupp har företräde framför distributioner till en användargrupp. Men om en app distribueras till en användargrupp med distributionsåtgärden **Tillgänglig** och samma app också distribueras till en enhetsgrupp med distributionåtgärden **Inte tillämplig**görs appen tillgänglig i företagsportalen, varifrån användare kan installera den.

-   En installationsåtgärd har företräde framför en avinstallationsåtgärd.

-   Om både en nödvändig och en tillgänglig installation tas emot av en enhet kombineras åtgärderna (appen är både nödvändig och tillgänglig, vilket betyder att slutanvändaren kan installera den från företagsportalen innan den nödvändiga installationen påbörjas).


## Nästa steg

Lär dig hur du [distribuerar appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).



<!--HONumber=Jun16_HO3-->


