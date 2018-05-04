---
title: Data Google skickar till Intune
titleSuffix: Microsoft Intune
description: Lista över data som Google skickar till Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 368205b63fcd360adf66f964c6cae087f6da3dfc
ms.sourcegitcommit: 2162ed46d939b4a9b85fa4e7e9943f2fb5948f1e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/20/2018
---
# <a name="data-google-sends-to-intune"></a>Data Google skickar till Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Om hantering av Android-företagsenheter är aktiverat på en enhet, upprättar Microsoft Intune en anslutning med Google och användar- och enhetsinformation delas mellan Intune och Google. Du måste skapa ett Google-konto innan Microsoft Intune kan upprätta någon anslutning.

I följande tabell visas de data som Google skickar till Intune när enhetshantering är aktiverat på en enhet:


| Data Google skickar till Intune | Information | Används för | Exempel |
|:---:|:---:|:---:|:---:|
| Företagsdata | Kundens företagsidentifierare i Google. | Länkar kundinformation mellan Intune och Google. | **enterpriseId** exempel: LC04eik8a6.<br>**Namn**. Administratörnamnet såsom det angavs när du konfigurerade Android-företag. Exempel: Joe Smith.<br>**E-post till administratör**. YourAdmin@gmail.com som användes när du konfigurerade Android-företag. |
| Programdata | Data för hanterade program på Play Store. | Inriktning av programmet till användare eller enheter som tillgängligt eller obligatoriskt. | **Programnamn** exempel: Contoso Warehouse Inventory Application.<br>**Unik identifierare som representerar programmet** exempel: app:com.Contoso.Warehouse.InventoryTracking |
| Tjänstkonto | Unikt internt Google-tjänstkonto för användning med specifika kundsamtal. | Används för att göra anrop till Google för kundens räkning (för att visa appar och enheter) | **Namn** exempel: InternalAccount@InternalService.com.<br>**Nycklar** exempel: ServiceAccountPassword |


Om du vill sluta använda Androids enhetshantering för företag med Microsoft Intune och ta bort data, måste du både inaktivera enhetshanteringen i Microsoft Intune och även ta bort ditt Google-konto. Läs mer i Google-kontot om hur du utför kontohanteringen.


