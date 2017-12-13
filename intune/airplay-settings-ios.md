---
title: "AirPlay-inställningar för iOS-enheter i Intune"
titlesuffix: Azure portal
description: "Lär dig hur du kan använda Intune för att ansluta iOS-enheter automatiskt till AirPlay-kompatibla enheter."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9a1472d86a0a25e35ef26be1c579ff491437676b
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2017
---
# <a name="intune-airplay-settings-for-ios-devices"></a>AirPlay-inställningar för iOS-enheter i Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd de här inställningarna för att ansluta iOS-enheter som du hanterar till AirPlay-kompatibla enheter (till exempel Apple TV) i nätverket.
Med den här funktionen kan du:

- **Konfigurera en lista med enheter och lösenord** – nu kan användarna ansluta automatiskt till AirPlay enheter som är inom räckhåll. Tilldela ett namn och lösenord för AirPlay enheter så att de inte behöver uppge detta när de ansluter.
- **Konfigurera tillåtna mål** – Konfigurera en lista med AirPlay-enheter (med enhets-ID). Användarna kommer bara att kunna se och ansluta till enheterna i listan (endast för övervakade enheter).

## <a name="get-started"></a>Kom igång

1. På bladet **Enhetsfunktioner** väljer du **AirPlay**.
2. På bladet **AirPlay** väljer du någon eller båda av följande åtgärder:

## <a name="configure-a-device-and-password-list"></a>Konfigurera en lista med enheter och lösenord

1. På bladet **Lösenord** anger du **Enhetsnamn** och **Lösenord** för en Airplay-enhet, till exempel **Contoso Apple TV**.
2. När du har angett information om enheten, klickar du på **Lägg till**. Enheten kommer att visas i listan **Enhetsnamn**.
3. Fortsätt lägga till enheter. Välj **OK** när du är klar.


## <a name="configure-allowed-destinations"></a>Konfigurera tillåtna mål

1. På bladet **Tillåtna mål (endast övervakade)** anger du **Enhets-ID** för en Airplay-enhet, till exempel 52:46:CD:51:83:4C.
2. När du har angett enhets-ID klickar du på **Lägg till**. Enhetens ID kommer att visas i listan **Enhets-ID**.
3. Fortsätt lägga till enheter. Välj **OK** när du är klar.

Du kan också importera enheter och lösenord, samt tillåtna mål från en fil med kommaavgränsade värden (.csv).


## <a name="next-steps"></a>Nästa steg

Du kan nu tilldela enhetsprofilen till de grupper som du väljer. Mer information finns i [Hur du tilldelar enhetsprofiler](device-profile-assign.md).

