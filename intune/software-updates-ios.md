---
title: "Konfigurera uppdateringsprinciper för iOS i Microsoft Intune"
titlesuffix: 
description: "Konfigurera uppdateringsprinciper för iOS för att tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga uppdateringen."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.openlocfilehash: 6ba354fb3b39544f09363651abfd9e1a5c0f6154
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>Konfigurera uppdateringsprinciper för iOS i Microsoft Intune
Uppdateringsprinciper för iOS gör det möjligt att tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga uppdateringen. Du kan konfigurera de dagar och tider då du inte vill att enheter ska installera uppdateringen.

## <a name="configure-the-ios-update-policy"></a>Konfigurera iOS-uppdateringsprincipen
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
2. Välj **Programuppdateringar** > **iOS-uppdateringsprinciper** i **Intune**-fönstret.
4. I principfönstret väljer du **Skapa** och anger sedan ett namn och en beskrivning för principen.
5. Välj **Inställningar** > **Konfigurera** och ange information om när iOS-enheter inte ska tvingas att installera den senaste uppdateringen.
6. Spara konfigurationen genom att välja **OK**. Nu är du tillbaka i fönstret **Skapa uppdateringsprincip**. Skapa principen och spara inställningarna genom att välja **Skapa**.

Profilen skapas och visas i fönstret med listan över iOS-uppdateringsprinciper.

## <a name="assign-an-ios-update-policy-to-users"></a>Tilldela en iOS-uppdateringsprincip till användare
Om du vill tilldela en iOS-uppdateringsprincip till användare väljer du en princip som du har konfigurerat. Befintliga principer finns i fönstret **Programuppdateringar** > **iOS-uppdateringsprinciper**.
1. Välj den princip som du vill tilldela till användarna och välj **Tilldelningar**. Då öppnas ett fönster där du kan välja Azure Active Directory-säkerhetsgrupper och tilldela dem till principen.
2. Öppna fönstret som visar Azure AD-säkerhetsgrupperna genom att välja **Valda grupper**.
3. Välj **Spara** om du vill distribuera principen till användarna.

Du har tillämpat principen på användarna. Uppdateringsefterlevnaden hos de enheter som används av de användare som principen är inriktad på kommer att utvärderas.

## <a name="change-the-restricted-days-for-the-policy"></a>Ändra begränsade dagar för principen
1. I fönstret **Programuppdateringar** väljer du **iOS-uppdateringsprinciper**.
2. Välj den iOS-uppdateringsprincip som du vill uppdatera.
3. Välj **Egenskaper** > **Inställningar** och uppdatera informationen om begränsade dagar.

## <a name="monitor-ios-devices-with-older-ios-versions"></a>Övervaka iOS-enheter med äldre iOS-versioner
<!-- 1352223 -->
Rapporten **Out-of-date iOS Devices** (Gamla iOS-enheter) är tillgänglig i fönstret **Programuppdateringar** > **iOS-uppdateringsprinciper**. I rapporten kan du visa en lista över alla övervakade iOS-enheter som har varit mål för en iOS-uppdateringsprincip och inte kunde uppdateras. Du kan se en status för varje enhet och se varför enheten inte har uppdaterats automatiskt.
