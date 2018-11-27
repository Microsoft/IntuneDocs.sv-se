---
title: Om registreringsprocessen för iOS-enheter
titlesuffix: Microsoft Intune
description: Lär dig hur hela registreringsprocessen går till med registrering av en iOS-enhet som exempel.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bdd8267701b20600d67e6927c8b55d7f9c11a34f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186774"
---
# <a name="understand-the-users-experience-enrolling-an-ios-device"></a>Beskrivning av hur en iOS-enhet registreras

Med Microsoft Intune kan du ge personalen tillgång till mobila enheter samtidigt som företagets information skyddas. Eftersom användarna kommer att interagera med Intune på sina enheter i stället för på administrationskonsolen, måste du se till att sätta dig in i registreringsprocessen. På så sätt kan du införliva vettiga efterlevnadsprinciper i processen och hjälpa dina användare på traven. Detta är särskilt viktigt eftersom användarna då kan se exakt vilken information som du som administratör kan se:

| IT-avdelningen kan inte se | IT-avdelningen kan se |
|---|---|
| Historik för samtal och surfning | Modell |
| Plats | Serienummer |
| Privat e-post | Operativsystemversion |
| Textmeddelanden | Appnamn |
| Kontakter | Ägare |
| Lösenord till dina personliga konton | Enhetsnamn |
| Kalender-händelser | Tillverkare (för enheter som inte tillverkats av Apple) |
| Bilder (inte heller de som ingår i appen Foton eller i Kamerabilder) | Telefonnummer (hela numret för arbetsenheter. För personliga enheter, enbart de sista fyra siffrorna.) |

## <a name="how-do-i-enroll-a-device"></a>Hur gör jag för att registrera en enhet?

För många slutanvändare är enhetsregistreringen första gången som de försöker få åtkomst till företagets resurser. [Sätt dig in i processen](end-user-educate.md) så blir det hela mindre krångligt.

1. Öppna **App Store** och sök efter **Intune-företagsportal**.
2. Ladda ner appen **Microsoft Intune-företagsportal**.
3. Öppna appen **Företagsportal**, ange testanvändarens e-postadress och lösenord och tryck sedan på **Logga in**.
4. Uppdatera det tillfälliga lösenordet till ett nytt lösenord.
5. Tryck på **Enhetsregistrering** på sidan **Konfiguration av företagsåtkomst**.
6. På sidan **Varför ska jag registrera enheten?** kan du läsa mer om vad en användare kan göra när denne har registrerat enheten. Tryck sedan på **Fortsätt**.
7. Läs igenom listan med de olika åtkomsträttigheter som en användare får efter registreringen. Tryck sedan på **Fortsätt**.
8. Läs igenom informationen om vad IT-administratörer kan och inte kan se på en enhet. Tryck sedan på **Fortsätt**.
9. På skärmen **Vad kommer härnäst** kan du läsa mer om vad som händer under registreringen. Tryck sedan på **Registrera**.
10. På sidan **Installera profil** trycker du på **Installera** och anger enhetens lösenord om du uppmanas göra detta.
11. Tryck på **Installera**.
12. Tryck på **Installera** igen för att bekräfta att du har läst varningen.
13. Tryck på **Förtroende** i popup-fönstret **Varning**.
14. När skärmen ändras och visar att installationen av profilen är klar trycker du på **Klar**.
15. Meddelandet ”Registrerar enheten” visas på skärmen. Därefter visas en bekräftelse som visar att enheten har registrerats. Ett popup-fönster visas och frågar om du vill öppna sidan i Företagsportalen. Tryck på **Öppna**.
16. Skärmen **Konfiguration av företagsåtkomst** visas på nytt. Om du inte har konfigurerat några testprinciper ska enheten vara fullständigt kompatibel med alla regler och föreskrifter. Om du använder testprinciper kan du trycka på **Enhetsefterlevnad** och se efter vad du kan göra för att skydda enheten.

## <a name="next-steps"></a>Nästa steg

[Kom igång med att lägga till appar](get-started-apps.md) – Hitta och lägg till appar på enheter så att dina anställda kan få arbete utfört.

## <a name="learn-more"></a>Läs mer

* [Registreringsalternativ för Intune](enrollment-options.md)
* [Aktivera Bring Your Own Device (ta med egen enhet) med Intune](byod-enable.md)
* [Informera slutanvändarna om registrering och enhetshantering](end-user-educate.md)
