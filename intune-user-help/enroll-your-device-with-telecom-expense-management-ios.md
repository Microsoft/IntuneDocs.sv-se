---
title: Registrera iOS-enheten i kostnadshanteringsprogrammet för telekomtjänster med Intune
description: Lär dig hur du registrerar en iOS-enhet i kostnadsuppföljningen av telekommunikation.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6d8c6372-f2ce-4558-8886-1d7c1966699c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: ff51405ee48851b5a48c4d6142c33bc16ed6218e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-your-ios-device-in-telecom-expense-management"></a>Registrera iOS-enheten i kostnadshanteringsprogrammet för telekomtjänster

Din organisation kanske använder ett kostnadshanteringsprogram för telekomtjänster för att se till att samtal- och dataförbrukningen förblir inom rimliga gränser. När du har registrerat enheten visas ett meddelande som uppmanar dig att välja en lämplig kategori för enheten.

  ![En skärmbild av skärmen "Välja den bästa kategorin för en enhet" på en iOS-enhet. Den visar ett val mellan företagsregistrering och personlig registrering.](./media/ios-enroll-10-tem-select-best-category.png)

Välj ett lämpligt alternativ och du får en avisering om att installera programmet [ __Datalert__ ](https://itunes.apple.com/app/datalert/id771029268?mt=8) från App Store. Din organisation kan mäta dataanvändningen med programmet Datalert. Om din organisation har konfigurerat alternativet arbets- eller skolregistrering i Microsoft, måste du logga in med ditt arbets- eller skolkonto. Om detta inte har aktiverats måste du ange information som exempelvis ditt telefonnummer, samt verifiera din enhet med en kod för att kunna registrera till Datalert-tjänsten från appen.

  ![En skärmbild på välkomstskärmen i programmet Datalert, där du uppmanas att fortsätta till nästa steg samt en kort förklaring om hur Datalert låter dig få ut det mesta av din dataförbrukning.](./media/ios-enroll-11-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>Registrera till Datalert med ditt arbets- eller skolkonto hos Microsoft

> [!NOTE]
> Du måste ha appen [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) installerad och aktiv på din telefon för att kunna registrera på det här sättet.

1. Välj __Registrera med Microsoft-konto__.

   ![En bild av skärmen Inställningar i Datalert-appen, med ett fält för telefonnummer för att registrera en enhet på den övre delen av skärmen och ”Registrera med Microsoft-konto” längst ned, där du måste ha ett Microsoft Office 365-konto och en Intune-prenumeration.](./media/ios-enroll-11a-tem-datalert-enroll-msft-account.png)

2. Du får ett meddelande om att __”Datalert” vill öppna ”Authenticator”__. Välj __Öppna__.

   ![En bild av popup-frågan till användaren om att öppna autentiseringsappen på begäran av Datalert-appen.](./media/ios-enroll-11b-tem-datalert-open-authenticator.png)

3. Logga in med ditt __skol- eller arbetskonto i Microsoft__. Datalert-installationen körs en liten stund och bör sedan ha slutförts. Tryck på __Slutför__ när den är klar.

## <a name="enroll-into-datalert-using-your-phone-number"></a>Registrera till Datalert med ditt telefonnummer

1. Ange enhetens telefonnummer.

   ![En skärmbild på när programmet Datalert begär ett telefonnummer.](./media/ios-enroll-12-tem-datalert-phone-number.png)

2. Du får sedan en verifieringskod via SMS. Ange koden och tryck på __OK__.

   ![En skärmbild på när programmet verifieringskoden via SMS.](./media/ios-enroll-13-tem-datalert-sms.png)

3. När du har angett verifieringskoden är installationen av Datalert färdig. När du har tryckt på __Slutför__ kan du övervaka dina data från Datalert.

   ![En skärmbild av Datalerts övervakning av dagens dataförbrukning.](./media/ios-enroll-14-tem-datalert-monitoring-active.png)

När du har registrerat enheten, börjar du se din dataanvändning av i appen Datalert.

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
