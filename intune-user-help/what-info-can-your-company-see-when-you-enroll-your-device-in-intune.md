---
title: Vilken information kan företaget se när enheten registreras?
description: Förklarar vad IT-avdelningen kan och inte kan se på den hanterade enheten.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.openlocfilehash: 63295d7e05889f5a8beb44e399f36a4fbe27544d
ms.sourcegitcommit: 76c7b315b83eb6cb5b996facf1d250fb3e22f1bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/08/2018
ms.locfileid: "51276123"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>Vilken information min organisation se när jag registrerar min enhet?

Organisationen kan inte se din personliga information när du registrerar en enhet med Microsoft Intune. När du registrerar en enhet ger du organisationen behörighet att visa vissa typer av information på din enhet, till exempel enhetsmodell och serienummer. Organisationen använder den här informationen för att skydda företagsdata på enheten.

**Vad din organisation aldrig kan se:**

- Historik för samtal och surfning
- E-post och textmeddelanden
- Kontakter
- Kalender
-   Lösenord
- Bilder (inte heller de som ingår i appen Foton eller i Kamerabilder)
- Filer

**Vad din organisation alltid kan se:**

- Enhetsmodell som Google Pixel
- Enhetstillverkare, t.ex. Microsoft
- Operativsystem och version, t.ex. iOS 12.0.1
- Appnamn såsom Microsoft Word: på personliga enheter kan organisationen bara se din hanterade appinventering. På företagsägda enheter kan organisationen se hela din appinventering.
- Enhetens ägare
- Enhetsnamn
- Enhetens serienummer
- IMEI

**Det här kan organisationen kanske se:**

-  Telefonnummer: Vid **företags**ägda enheter kan det fullständiga telefonnumret visas. För **personligt** ägda enheter är endast de sista fyra siffrorna i telefonnumret synliga för organisationen. Du kan se **Typ av ägarskap** för varje enskild enhet genom att öppna sidan **Enhetsinformation** på enheten.
- Lagringsutrymme för enheten: om du inte kan installera en obligatorisk app kan organisationen titta på din enhets lagringsutrymme för att ta reda på om det är för lågt.  
-  Plats: organisationen kan aldrig se var enheten finns, förutom om du har en iOS-enhet som övervakas och har försvunnit. [Hur vet jag?](https://go.microsoft.com/fwlink/?linkid=853816)
- Appinventering: om organisationen använder skydd mot mobilhot kommer de att kunna se mer information om apparna som är på din iOS-enhet. Läs mer om [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md).
- Nätverksinformation: en del information om nätverksanslutningar för Android-enheter kan vara tillgänglig för din organisationssupport. Om organisationen till exempel kräver att enheter ska finnas kvar i en viss byggnad kan din enhet identifiera det nätverk som den är ansluten till. 
