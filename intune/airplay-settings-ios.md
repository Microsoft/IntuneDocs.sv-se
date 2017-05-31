---
title: "AirPlay-inställningar för iOS-enheter i Intune"
titleSuffix: Intune Azure preview
description: "Lär dig hur du kan använda Intune för att ansluta iOS-enheter automatiskt till AirPlay-kompatibla enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ad2f20603261ec0eac4156facd3fd23b2982f517
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="intune-airplay-settings-for-ios-devices"></a>AirPlay-inställningar för iOS-enheter i Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Använd de här inställningarna för att ansluta iOS-enheter som du hanterar till AirPlay-kompatibla enheter (till exempel Apple TV) i nätverket.
Med den här funktionen kan du:

- **Konfigurera en lista med enheter och lösenord** – Förse enheter med namn och lösenord för AirPlay-enheter så att de ansluts automatiskt när de befinner sig i området. Om du anger ett lösenord behöver inte användarna ange det när de ansluter.
- **Konfigurera tillåtna mål** – Konfigurera en lista med AirPlay-enheter (med enhets-ID). Användarna kommer bara att kunna se och ansluta till enheterna i listan (endast för övervakade enheter).

## <a name="get-started"></a>Kom igång

1. På bladet **Enhetsfunktioner** väljer du **AirPlay**.
2. På bladet **AirPlay** väljer du någon eller båda av följande åtgärder:

## <a name="configure-a-device-and-password-list"></a>Konfigurera en lista med enheter och lösenord

1. På bladet **Lösenord** anger du **Enhetsnamn** och **Lösenord** för en Airplay-enhet, till exempel **Contoso Apple TV**.
2. När du har angett information om enheten, klickar du på **Lägg till**. Enheten kommer att visas i listan **Enhetsnamn**.
3. Fortsätt lägga till enheter. Välj **OK** när du är klar.


## <a name="configure-allowed-destinations"></a>Konfigurera tillåtna mål

1. På bladet **Tillåtna mål (endast övervakade)* anger du **Enhets-ID** för en Airplay-enhet, till exempel 52:46:CD:51:83:4C.
2. När du har angett enhets-ID klickar du på **Lägg till**. ID:t visas i listan **Enhets-ID**.
3. Fortsätt lägga till enheter. Välj **OK** när du är klar.

Du kan också importera enheter och lösenord, samt tillåtna mål från en fil med kommaavgränsade värden (.csv).



