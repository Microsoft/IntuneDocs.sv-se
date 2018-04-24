---
title: Informera slutanvändare om Microsoft Intune | Microsoft Intune
description: Dela informationen med dina slutanvändare för en lyckad Intune-distribution.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/10/2017
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 48914533-f138-4dc0-8b93-4cea3ac61f7b
ms.reviewer: robstack
ms.suite: ems
ms.openlocfilehash: a8b5f44482a55a6bb9e9da9e2aa9a8fb67f0a713
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-educate-your-end-users-about-microsoft-intune"></a>Informera slutanvändare om Microsoft Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Med Microsoft Intune kan du ge personalen tillgång till mobila enheter samtidigt som företagets information skyddas. Det finns många åtgärder som du kan vidta för att säkerställa en lyckad distribution. Ett exempel är att utvärdera Intune med en [kostnadsfri utvärderingsversion](app-sdk.md).

Men ingen av dessa åtgärder ser till att användarna förstår varför att det är så viktigt att du hanterar deras enheter. Snarare upplever de att du inkräktar på deras integritet, särskilt om du distribuerar Intune som en [BYOD-lösning](/enterprise-mobility-security/solutions/byod-design-considerations-guide).

> [!Important]
> För att distributionen ska bli framgångsrik är det viktigt att du förstår slutanvändarnas oro och arbetar förebyggande med att informera dem om varför företaget behöver hantera enheterna.

Införandet handlar inte bara om att distribuera och få igång tekniken bland personalen utan även att få dem att inse att Intune ger dem en säker åtkomst. Användare kan känna sig hotade av företagsmobilitet om vi inte tydligt förklarar vad det är till för, och vad det kan användas till (och inte kan användas till).

## <a name="things-to-consider-about-your-end-users"></a>Saker att tänka på om användarna

__Vilken erfarenhet har användarna?__ Användarna kan ha många olika erfarenheter av olika tekniker. Det kan vara både positiva och negativa erfarenheter Det kan vara allt från bilder på barnen när de var små till den där gången när de tappade mobilen i vattnet och alla data som inte hade säkerhetskopierats gick förlorade. Dessa upplevelser påverkar hur användarna ser på teknik och på användningen av enheter hemma och på jobbet.

__Vad betyder företagsmobilitet för mig?__ Användare kanske inte inser vilken åtkomst du har (och inte har) till deras enheter och information. De är troligen oroliga för att IT-avdelningen och cheferna kan hålla koll på allt de gör. Detta kan vara särskilt oroande för ovana användare som kanske tror att allt de gör på sina enheter är privat. En erfarna användare kan vara oroliga för att andra spionerar på deras enheter på ett ”big brother”-liknande sätt, och kan sedan sprida denna oro bland medarbetarna.

__Vilka problem kan detta medföra för slutanvändarna?__ Det tar tid att installera appar, registrera enheter och följa reglerna. Att se till att företagets information är säker är högsta prioritet för alla Intune-distributioner, men att kräva ett orimligt lösenord på en privat enhet kan få användarna att ogilla hanteringen av deras enheter. Att skicka nödvändiga uppdateringar mitt under ett viktigt affärsmöte kan göra att användarna blir mindre produktiva, och det kan motverka syftet med att ha tillgång till mobila enheter.

## <a name="things-you-should-do"></a>Saker du bör göra

Distributionen blir smidigare om du dämpar oron. Vi har en lista över saker som kan göra det enklare för användare att acceptera enhetshanteringen.

* __Var rådig.__ I Intune-dokumentationen finns information som hjälper användarna att ta reda på hur de kan utföra uppgifter, till exempel registrera och felsöka sina enheter. Användarna länkas till vissa av dessa artiklar från företagsportalen. Länkarna är indelade i avsnitt om installation av företagsportalappen och Intune-registrering, uppgifter som användarna kan utföra på sina enheter samt felsökning. Den här dokumentationen finns i informationen om hur du [får saker gjorda med hanterade enheter](/intune-user-help/use-managed-devices-to-get-work-done).

* __Var tillgänglig.__ Användarna behöver få veta var de kan få hjälp med sina enheter. Se till att du inkluderar kontaktuppgifter till IT-administratören när du [anpassar företagsportalen](company-portal-customize.md) så att användarna kan få hjälp om det behövs.

* __Var personlig.__ Om du tillhandahåller instruktioner som inte gäller för din specifika distribution kan användarna uppleva att du inte har ägnat någon tanke på deras situation. Du kan använda den här [anpassningsbara mallen för slutanvändarregistrering i Intune för IT-administratörer](https://gallery.technet.microsoft.com/office/Intune-End-User-Enrollment-3a0c9b0c) för att skapa egna registreringsanvisningar för slutanvändare.

* __Hitta olika sätt att kommunicera.__ Användare har [olika sätt att lära sig saker](https://www.umassd.edu/dss/resources/facultystaff/howtoteachandaccommodate/howtoaccommodatedifferentlearningstyles/) och på samma sätt har de olika sätt att använda information. För användare som föredrar video framför dokumentation erbjuder vi [videor om hur du registrerar olika enhetstyper](https://channel9.msdn.com/Series/IntuneEnrollment) och annat på Channel 9. Dessa videor går att bädda in direkt på din egen [SharePoint-plats](https://support.office.com/article/Embed-a-video-from-Office-365-Video-59e19984-c34e-4be8-889b-f6fa93910581), eller så kan du ladda ned egna lokala kopior, antingen av videon eller bara ljudspåret.

* __Var informerad.__ Användarens upplevelse påverkar företagets produktivitet. Om du har bättre förståelse för deras upplevelse blir det enklare för dig att felsöka deras problem. Om du vet hur användarna får sina appar blir det mycket enklare för dig att diagnosticera vilka fel de upplever och det går snabbare att åtgärda deras problem.

* **Android**
  * [Använda en Android-enhet med Intune](/intune-user-help/using-your-android-device-with-intune)
  * [Så får dina Android-användare sina appar](end-user-apps-android.md)

* **iOS**
  * [Använda en iOS-enhet med Intune](/intune-user-help/using-your-ios-device-with-intune)
  * [Så får dina iOS-användare sina appar](end-user-apps-ios.md)

* **Windows**
  * [Använda en Windows-enhet med Intune](/intune-user-help/using-your-windows-device-with-intune)
  * [Så får dina Windows-användare sina appar](end-user-apps-windows.md)

* __Var tydlig.__ Var tydlig med att berätta för användarna vad du tänker hantera på deras enheter. Berätta vilka typer av data som du samlar in och varför du samlar in dem. Informera dem om hur du tänker använda alla data. [Microsoft anser att du har rätt till så mycket information som möjligt om hur vi hanterar din kundinformation i molnet](https://www.microsoft.com/trustcenter/about/transparency), och vi tror att den här filosofin kan göra att dina användare blir mer nöjda med Intune.

>[!Note]
> Transparens är nyckeln till en lyckad distribution.

Försök att kombinera förtroende med gedigna efterlevnadsprinciper. Se till att användarna vet att du *inte vill* titta på vissa typer av data, även om du *hade kunnat* göra det, och att du vet vilken skada det skulle medföra att inkräkta på deras integritet. Att utforma ett utlåtande tillsammans med den juridiska avdelningen och personalavdelningen kan vara till hjälp för anställda som är skeptiska.
