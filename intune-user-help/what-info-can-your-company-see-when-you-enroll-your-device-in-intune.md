---
title: "Vilken information kan företaget se när enheten registreras? | Microsoft Docs"
description: "En lista över vad IT-avdelningen kan se och inte kan se på den hanterade enheten."
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 11/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.openlocfilehash: 58fd9c985700e65ad5f97376382d348f009e2c29
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="what-information-can-my-company-see-when-i-enroll-my-device"></a>Vilken information kan företaget se när jag registrerar min enhet?

När du registrerar en enhet för hantering ger du företaget tillstånd att se viss information i syfte att skydda företagets information på enheten.

**Vad företaget aldrig kan se**

- Historik för samtal och surfning
- E-post och textmeddelanden
- Kontakter
- Kalender
-   Lösenord
- Bilder (inte heller de som ingår i appen Foton eller i Kamerabilder)

**Vad företaget alltid kan se**

- Enhetsmodell som Google Pixel
- Tillverkare, som t.ex. Microsoft
- Operativsystem, som t.ex. iOS
- Programnamn, som t.ex. Microsoft Word
- Enhetens ägare
- Enhetsnamn
- Serienummer

**Vad företaget kanske kan se**

-  Telefonnummer: Vid **företags**ägda enheter kan det fullständiga telefonnumret visas. För **personligt** ägda enheter är endast de sista fyra siffrorna i telefonnumret synliga för ditt företag. Du kan se **Typ av ägarskap** för varje enskild enhet genom att öppna sidan **Enhetsinformation** på enheten.
-  Plats: Företaget kan aldrig se var enheten finns, förutom om du har en iOS-enhet som övervakas och har försvunnit. [Hur vet jag?](https://go.microsoft.com/fwlink/?linkid=853816)
- Appinventering: om ditt företag använder skydd mot mobilhot, kommer de att kunna se mer information om apparna som är på din iOS-enhet. Läs mer om [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md).
- Nätverksinformation: en del information om nätverksanslutningar för Android-enheter kan vara tillgänglig för din företagssupport. Om ditt företag till exempel kräver att enheter ska finnas kvar i en viss byggnad, kan din enhet identifiera nätverket som den är ansluten till. 
