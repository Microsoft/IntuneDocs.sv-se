---
title: "Registrera Android-enheten i kostnadshanteringsprogrammet för telekomtjänster med Intune"
description: "Läs om hur du registrerar en Android-enhet i kostnadsuppföljning av telekommunikation."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 26aa3698-7e4d-453a-8852-ab75e72b6485
searchScope: User help
ROBOTS: 
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 4d8bf1304d0a7b1f007c85befa3565b519719dbd
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2017
---
# <a name="enroll-your-android-device-in-telecom-expense-management"></a>Registrera Android-enheten i kostnadshanteringsprogrammet

Din organisation kanske använder ett kostnadshanteringsprogram för telekomtjänster för att se till att samtal- och dataförbrukningen förblir inom rimliga gränser. När du har registrerat enheten visas ett meddelande som uppmanar dig att välja en lämplig kategori för enheten.

![En skärmbild av skärmen "Välja den bästa kategorin för en enhet" på en iOS-enhet. Den visar ett val mellan företagsregistrering och personlig registrering.](./media/and-enroll-11-tem-select-best-category.png)

Välj ett lämpligt alternativ och du får en avisering om att installera programmet [ __Datalert__ ](https://play.google.com/store/apps/details?id=fr.memobox.databox) från Google Play Store. Din organisation kan mäta dataanvändningen med programmet Datalert. Om din organisation har konfigurerat alternativet arbets- eller skolregistrering, måste du logga in med ditt arbets- eller skolkonto. Om detta inte har aktiverats måste du ange information som exempelvis ditt telefonnummer, samt verifiera din enhet med en kod för att kunna registrera till Datalert-tjänsten från appen.

Tryck på pilen __nästa__ längst upp till höger på skärmen för att fortsätta. Företagets support bör tala om ifall du ska logga in med ditt __arbets- eller skolkonto hos Microsoft__ eller använda ditt __telefonnummer__.

  ![En skärmbild på välkomstskärmen i programmet Datalert, där du uppmanas att fortsätta till nästa steg samt en kort förklaring om hur Datalert låter dig få ut det mesta av din dataförbrukning.](./media/and-enroll-12-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>Registrera till Datalert med ditt arbets- eller skolkonto hos Microsoft

1. Välj __Registrera med Microsoft-konto__.

  ![En bild av skärmen Inställningar i Datalert-appen, med ett fält för telefonnummer för att registrera en enhet på den övre delen av skärmen och ”Registrera med Microsoft-konto” längst ned, där du måste ha ett Microsoft Office 365-konto och en Intune-prenumeration.](./media/and-enroll-12a-tem-datalert-enroll-msft-account.png)

2. Välj ditt arbets- eller skolkonto bland tillgängliga konton. Om ditt konto inte finns med i listan kan du logga in med hjälp av knappen **Lägg till konto**.

  ![En skärmbild av fönstret ”Välj konto” som visar ett exempelkonto och knappen Lägg till konto.](./media/and-enroll-12b-tem-datalert-enroll-select-msft-account.png)

3. Datalert-installationen körs en liten stund och bör sedan ha slutförts. Tryck på __Slutför__ när den är klar.

## <a name="enroll-into-datalert-using-your-phone-number"></a>Registrera till Datalert med ditt telefonnummer

1. Ange enhetens telefonnummer.

  ![En skärmbild på när programmet Datalert begär ett telefonnummer.](./media/and-enroll-13-tem-datalert-phone-number.png)

2. Du får sedan en verifieringskod via SMS. Ange koden och tryck på __OK__.

  ![En skärmbild på när programmet verifieringskoden via SMS.](./media/and-enroll-14-tem-datalert-sms.png)

3. När du har angett verifieringskoden är installationen av Datalert färdig. När du har tryckt på __Slutför__ kan du övervaka dina data från Datalert.

  ![En skärmbild av Datalerts övervakning av dagens dataförbrukning.](./media/and-enroll-15-tem-datalert-monitoring-active.png)

När du har registrerat enheten, börjar du se din dataanvändning av i appen Datalert.

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
