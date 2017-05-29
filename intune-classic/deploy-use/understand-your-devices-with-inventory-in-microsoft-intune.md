---
title: "Förstå dina enheter med inventering | Microsoft Docs"
description: "Använd Intune för att visa information om maskinvara för enheterna du hanterar."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 59b6a72a17490d7c4aada6bee5caaaac2ba0979c
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="understand-your-devices-with-inventory-in-microsoft-intune"></a>Förstå dina enheter inventering i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Med Microsoft Intune kan du visa inventeringen för registrerade enheter och Windows-datorer som kör Intune-klientprogrammet.
Vanligtvis samlar Intune in inventering från hanterade enheter var sjunde dag. Det gör att det kan dröja ett tag innan nyligen gjorda ändringar återspeglas i rapporterna, t.ex. om enhetsnamnet eller mängden ledigt lagringsutrymme ändras.

## <a name="whats-collected-from-enrolled-devices"></a>Vad samlas in från registrerade enheter?
Om du vill se inventeringen som samlas in av mobila enheter kör du [Rapporter om inventering av mobila enheter](understand-microsoft-intune-operations-by-using-reports.md). Intune samlar in följande inventering från registrerade enheter:

|Egenskap|Samlas in av|
|------------|-----------------------|
|**Namn**|All -enheter|
|**Operativsystem**|All -enheter|
|**Tillverkare**|All -enheter|
|**Modell**|All -enheter|
|**Hanteringskanal**|All -enheter|
|**AAD-registrerad**|Alla enheter utom Mac OS X|
|**Kompatibel**|All -enheter|
|**EAS-aktiverad**|Alla enheter utom Mac OS X|
|**Aktiverings-ID för EAS**|Alla enheter utom Mac OS X|
|**Aktiveringstid för EAS**|Alla enheter utom Mac OS X|
|**Hanteringstillstånd**|All -enheter|
|**E-postadress**|All -enheter|
|**Exchange ActiveSync ID**|All -enheter|
|**Jailbrokad eller rotad**|Endast iOS- och Android-enheter|
|**Unikt enhets-ID**|Alla enheter utom Exchange ActiveSync|
|**Serienummer**|iOS-, Mac OS X-, Android-, Windows 8.1- och Windows 10 Desktop-enheter|
|**Totalt lagringsutrymme**|iOS-, Mac OS X-, Windows 8.1-, Windows 10 Desktop- och Windows 10 Mobile-enheter|
|**Ledigt lagringsutrymme**|iOS-, Mac OS X-, Windows 8.1- och Windows 10 Desktop-enheter|
|**Telefonnummer**<br>Telefoner som kategoriserats som företagets identifieras med sina fullständiga telefonnummer (till exempel när du kör en inventeringsrapport för mobila enheter). BYOD-telefonnummer maskeras med &#42;, och bara de sista fyra siffrorna visas.|iOS-, Android- och Windows Phone-enheter|
|**IMEI**|Exchange ActiveSync-, iOS-, Android- och Windows Phone-enheter|
|**MEID**<br>MEID (Mobile Equipment Identifier)|Endast iOS-enheter|
|**MAC för Wi-Fi**|Alla enheter utom Exchange ActiveSync|
|**Abonnentens operatör**|Endast iOS- och Android-enheter|
|**Mobilteknik**|Endast iOS- och Android-enheter|
|**Övervakas**|Endast iOS-enheter|
|**Status för aktiveringslås**|Endast iOS-enheter|
|**Registreringsdatum**|All -enheter|
|**Senast uppdaterad**|All -enheter|
|**MAC för Ethernet**|Endast Mac OS X-enheter|
|**Aktiveringslåset är aktiverat**|Endast iOS-enheter|
|**Kryptering är aktiverat**|All -enheter|

## <a name="whats-collected-from-windows-pcs"></a>Det här samlas in från Windows-datorer
> [!IMPORTANT]
> Det här avsnittet gäller endast för Windows-datorer som kör Intunes Windows-PC-klientprogramvara.

Om du vill visa inventeringen som samlas in av Windows-datorer kör du [datorinventeringsrapporterna](understand-microsoft-intune-operations-by-using-reports.md). Intune samlar in följande inventering från Windows-datorer:

-   **Namn**

-   **Chassityp**

-   **Tillverkare**

-   **Modell**

-   **Operativsystem**

-   **TPM-version**

-   **Totalt diskutrymme**

-   **Använt diskutrymme**

-   **Ledigt diskutrymme**

-   **Namn på operativsystemdisk**

-   **Diskutrymme på operativsystem**

-   **Ledigt diskutrymme på operativsystem**

-   **Fysiskt minne**

-   **Processornamn**

-   **Processorarkitektur**

-   **Processorhastighet**

-   **IP-adress**

-   **Serienummer**

-   **Senast inloggade användare**

-   **Tilldelad användare**

-   **Senast uppdaterad**

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->

