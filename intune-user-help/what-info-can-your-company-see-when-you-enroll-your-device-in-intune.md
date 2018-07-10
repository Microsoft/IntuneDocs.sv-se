---
title: Vilken information kan företaget se när enheten registreras?
description: Förklarar vad IT-avdelningen kan och inte kan se på den hanterade enheten.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/18/2018
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
ms.openlocfilehash: ad949cc9d20e0e46ab986b4646059af733018255
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232814"
---
# <a name="what-information-can-my-company-see-when-i-enroll-my-device"></a>Vilken information kan företaget se när jag registrerar min enhet?

Ditt företag inte kan se din personliga information när du registrerar en enhet med Microsoft Intune. När du registrerar en enhet ger du företaget behörighet att visa vissa typer av information på din enhet, till exempel enhetsmodell och serienummer. Företaget använder den här informationen för att skydda företagsdata på enheten.

**Det här kan företaget aldrig se:**

- Historik för samtal och surfning
- E-post och textmeddelanden
- Kontakter
- Kalender
-   Lösenord
- Bilder (inte heller de som ingår i appen Foton eller i Kamerabilder)

**Det här kan företaget alltid se:**

- Enhetsmodell som Google Pixel
- Tillverkare, som t.ex. Microsoft
- Operativsystem, som t.ex. iOS
- Programnamn, som t.ex. Microsoft Word
- Enhetens ägare
- Enhetsnamn
- Serienummer

**Det här kan företaget kanske se:**

-  Telefonnummer: Vid **företags**ägda enheter kan det fullständiga telefonnumret visas. För **personligt** ägda enheter är endast de sista fyra siffrorna i telefonnumret synliga för ditt företag. Du kan se **Typ av ägarskap** för varje enskild enhet genom att öppna sidan **Enhetsinformation** på enheten.
-  Plats: Företaget kan aldrig se var enheten finns, förutom om du har en iOS-enhet som övervakas och har försvunnit. [Hur vet jag?](https://go.microsoft.com/fwlink/?linkid=853816)
- Appinventering: om ditt företag använder skydd mot mobilhot, kommer de att kunna se mer information om apparna som är på din iOS-enhet. Läs mer om [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md).
- Nätverksinformation: en del information om nätverksanslutningar för Android-enheter kan vara tillgänglig för din företagssupport. Om ditt företag till exempel kräver att enheter ska finnas kvar i en viss byggnad, kan din enhet identifiera nätverket som den är ansluten till. 
