---
title: "Välj hur du vill registrera mobila enheter"
description: "Bestäm hur du ska registrera mobila enheter i Intune genom att besvara några enkla frågor"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed9250aa-e894-4eac-92b8-5f1a3748e255
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.custom: intune-classic EXPIERIMENT
ms.openlocfilehash: e978a9df5d0c0e2e94f484c5e683a970f66dc945
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="choose-how-to-enroll-mobile-devices"></a>Välj hur du vill registrera mobila enheter

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Dina svar på dessa frågor hjälper dig att avgöra den bästa registreringsmetoden för de enheter som du hanterar.

## <a name="how-will-you-manage-shared-ios-devices"></a>**Hur ska du hantera dina delade iOS-enheter?**

> [!div class="button"]
[DEP-registrering av iOS >](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
> [!div class="button"]
[Direktregistrering av iOS >](/intune-classic/deploy-use/ios-direct-enrollment-in-microsoft-intune)
> [!div class="button"]
[DEM-registrering >](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Apples enhetsregistreringsprogram (DEP)** – Köpta eller hanterade iOS-enheter med DEP kan vara mål för en registreringsprofil. När användarna sätter på sina enheter för första gången laddar enheten ned DEP-profilen och registreras med DEP-profilen.

  - **Apple Configurator på en Mac** – Apple Configurator är ett Apple-program som körs på en Mac-dator. Du kan ansluta dina iOS-enheter till Mac-datorn med en USB-kabel för att installera en registreringsprofil på enheten. Om du inte kan återställa fabriksinställningarna på enheterna kan du registrera dem med hjälp av installationsassistentläget. Om du inte vill fabriksåterställa enheterna kan du använda Direktregistrering.

  - **Hanterare för enhetsregistrering** – Med Intunes enhetsregistreringshanterare (DEM) kan en chef eller administratör registrera många mobila enheter med ett enda användarkonto. Dessa enheter kan inte ha användartillhörighet (d.v.s. särskilda användare) och måste registreras genom att installera och logga in i företagsportalappen.

> [!div class="button"]
[< Bakåt](choose-how-to-enroll-devices3.md)
