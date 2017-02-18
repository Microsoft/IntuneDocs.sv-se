---
title: Distribuera appar | Microsoft Docs
description: "Det här avsnittet förklarar begrepp som du behöver förstå innan du börjar distribuera appar med Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: efa8245020b961797405a6f8b90df7e7b172b4c3


---

# <a name="deploy-apps-with-microsoft-intune"></a>Distribuera appar med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet förklarar några av de begrepp som du behöver förstå innan du börjar distribuera appar med Microsoft Intune.


## <a name="app-deployment-actions"></a>Appdistributionsåtgärder
När du distribuerar appar kan du välja någon av följande distributionsåtgärder:

-   **Nödvändig installation** – Appen installeras på enheten utan att det krävs någon åtgärd från användaren.

    > [!TIP]
    > När det gäller iOS-enheter som inte är i övervakat läge, samt alla Android-enheter, måste användaren godkänna apperbjudandet innan appen kan installeras.
    >
    >  Om en användare avinstallerar en app som du har distribuerat som en nödvändig installation installeras appen automatiskt om av Intune efter nästa inventeringscykel, som vanligtvis sker var sjunde dag.

-   **Tillgänglig installation** – Appen visas i företagsportalen och användare kan installera den på begäran.

-   **Avinstallera** – Appen avinstalleras från enheten.

-   **Ej tillämpligt** – Appen visas inte i företagsportalen och installeras inte på några enheter.

#### <a name="understand-which-deployment-actions-are-available-for-each-installer-type"></a>Distributionsåtgärder som är tillgängliga för olika typer av installationsprogram

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
> [!TIP]
> Om du väljer både användar- och enhetsgrupper när du distribuerar appar, kan du bara distribuera appen som en **Tillgänglig installation**.

## <a name="deployment-conflicts"></a>Distributionskonflikter
När två distributioner, med samma distributionsåtgärd, tas emot av en enhet gäller följande regler:

-   Distributioner till en enhetsgrupp har företräde framför distributioner till en användargrupp. Men om en app distribueras till en användargrupp med distributionsåtgärden **Tillgänglig**, och samma app också distribueras till en enhetsgrupp med distributionåtgärden **Inte tillämplig**, görs appen tillgänglig i företagsportalen, varifrån användare kan installera den.

-   En installationsåtgärd har företräde framför en avinstallationsåtgärd.

-   Om både en nödvändig och en tillgänglig installation tas emot av en enhet kombineras åtgärderna. Användaren kan alltså installera den tillgängliga appen från företagsportalen innan den nödvändiga installationen påbörjas.


## <a name="next-steps"></a>Nästa steg

Lär dig hur du [distribuerar appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).



<!--HONumber=Dec16_HO5-->


