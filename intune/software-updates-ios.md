---
title: Konfigurera uppdateringsprinciper för programvara för iOS i Microsoft Intune
titlesuffix: ''
description: Konfigurera uppdateringsprinciper för iOS för att tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga uppdateringen.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: 58727a501d6a8ec14e964094eac9fcd6eb3868da
ms.sourcegitcommit: c3ae3c3dc46b62d9191813d25a196874ba4927be
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/28/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>Konfigurera uppdateringsprinciper för iOS i Microsoft Intune

Uppdateringsprinciper för programvara gör det möjligt att tvinga övervakade iOS-enheter som kör iOS 10.3 att automatiskt installera den senaste tillgängliga OS-uppdateringen. Den här funktionen är endast tillgänglig för övervakade enheter. Du kan konfigurera de dagar och tider då du inte vill att enheter ska installera uppdateringen. 

När enheten checkar in, ungefär var 8:e timme, försöker enheten att hämta och installera den senaste OS-uppdateringen om det finns en tillgänglig uppdatering och det inte är under en begränsad tidsperiod. Det krävs inga användaråtgärder för att uppdatera enheten. Principen skulle inte förhindra att en användare uppdaterar operativsystemet.

## <a name="configure-the-ios-update-policy"></a>Konfigurera iOS-uppdateringsprincipen
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Programuppdateringar** > **iOS-uppdateringsprinciper** i **Intune**-fönstret.
4. I principfönstret väljer du **Skapa** och anger sedan ett namn och en beskrivning för principen.
5. Välj **Inställningar** > **Konfigurera** och ange information om när iOS-enheter inte ska tvingas att installera den senaste uppdateringen. Du kan konfigurera veckodagar, tidszon, starttid och sluttid.
6. Spara konfigurationen genom att välja **OK**. Nu är du tillbaka i fönstret **Skapa uppdateringsprincip**. Skapa principen och spara inställningarna genom att välja **Skapa**.

Profilen skapas och visas i fönstret med listan över iOS-uppdateringsprinciper. Apple MDM ger inte möjlighet att genomdriva att enheten ska installera uppdateringen vid en viss tid eller ett visst datum. 

## <a name="change-the-restricted-times-for-the-policy"></a>Ändra begränsade tider för principen

1.  På bladet **Programuppdateringar** väljer du **iOS-uppdateringsprinciper**.
2.  Välj den iOS-uppdateringsprincip som du vill uppdatera.
3.  Välj **Egenskaper** och uppdatera informationen om begränsade tider.
4.  Välj veckodagar
5.  Tidszon som den här principen ska tillämpas i
6.  Start- och sluttid för svartlistade timmar

## <a name="assign-an-ios-update-policy-to-users"></a>Tilldela en iOS-uppdateringsprincip till användare

Om du vill tilldela en iOS-uppdateringsprincip till användare väljer du en princip som du har konfigurerat. Befintliga principer finns i fönstret **Programuppdateringar** > **iOS-uppdateringsprinciper**.

1. Välj den princip som du vill tilldela till användarna och välj **Tilldelningar**. Då öppnas ett fönster där du kan välja Azure Active Directory-säkerhetsgrupper och tilldela dem till principen.
2. Öppna fönstret som visar Azure AD-säkerhetsgrupperna genom att välja **Valda grupper**. Fastställ vem som har åtkomst till principen genom att tilldela grupper för att inkludera och exkludera.
3. Välj **Spara** om du vill distribuera principen till användarna.

Du har tillämpat principen på användare eller enheter. Uppdateringsefterlevnaden hos de enheter som används av de användare som principen är inriktad på kommer att utvärderas. Den här principen har även stöd för användarlösa enheter.

## <a name="monitor-ios-device-installation-failures"></a>Övervaka installationsfel för iOS-enhet
<!-- 1352223 -->
Rapporten **Installationsfel för iOS-enheter** är tillgänglig i fönstret **Programuppdateringar**. I rapporten kan du visa en lista över alla övervakade iOS-enheter som har varit mål för en iOS-uppdateringsprincip, som har försökt genomföra en uppdatering och som inte kunde uppdateras. Du kan se en status för varje enhet och se varför enheten inte har uppdaterats automatiskt. Felfria, uppdaterade enheter visas inte i listan. Vi definierar uppdaterad som den senaste uppdateringen som enheten har stöd för.

