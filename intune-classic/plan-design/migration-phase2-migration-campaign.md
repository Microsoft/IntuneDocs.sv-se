---
title: "Starta en kampanj för Intune-migrering | Microsoft Docs"
description: "Syftet med den här artikeln är att ge vägledning om hur du startar en migreringskampanj."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e98730105044d2147d9be37002fc20ec2de8eb0e
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="phase-2-migration-campaign"></a>Steg 2: Migreringskampanj

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Organisationer bör använda den migreringstyp som bäst passar deras behov och justera implementeringsmetoderna utifrån sina specifika krav. I den avslutande delen av den här guiden får du en introduktion till de verktyg du behöver för att få dina användares enheter registrerade i Intune.

## <a name="keys-to-a-successful-migration"></a>Nycklar till en lyckad migrering

Detta är de viktigaste sakerna att tänka på när du migrerar från en MDM-provider från tredje part till Intune:

-   Kommunikation är nyckeln till att minimera slutanvändarnas stilleståndstid och säkra deras tillfredsställelse.

-   Använd alltid specifika och konkreta migreringsinstruktioner.

-   Alla hanterade enheter måste avregistrerats från din befintliga MDM-provider innan de kan registreras i Intune.

-   Tillhandahåll vägledning från den befintliga MDM-providern till slutanvändarna om hur de ska avregistrera sina enheter.

-   Använd en fasad metod. Börja med en liten grupp pilotanvändare och lägg stegvis till flera användargrupper tills du uppnår fullskalig distribution.

-   Övervaka supportavdelningens belastning och registrera resultatet för varje cykel. Reservera tid i schemat så att du får tid att utvärdera framgångskriterierna för respektive grupp innan nästa migreras. Pilotdistributionen bör verifiera följande:

    -   Graden av lyckade och misslyckade registreringar ligger inom det förväntade.

    -   Användarproduktivitet:

        -   Företagsresurser, som VPN, Wi-Fi, e-post och certifikat, fungerar.

        -   Etablerade appar är tillgängliga.

    -   Datasäkerhet:

        -   Efterlevnadsrapportering

        -   Mobilappsskydd tillämpas

-   När du är nöjd med den första migreringsfasen så upprepar du migreringscykeln (vilken beskrivs nedan under Normal migreringscykel) för nästa fas.

-   Upprepa de fasade cyklerna tills alla användare har migrerats till Intune.

-   Se till att supportavdelningsteamet är redo att stödja slutanvändarna under hela migreringskampanjen. Kör en frivillig migrering tills du kan beräkna arbetsbelastningen för supportsamtal.

-   Ange inte tidsgränser för registreringen förrän den återstående populationen kan hanteras av supportavdelningen

> [!IMPORTANT] 
> Konfigurera inte både Intune och din befintliga MDM-lösning från tredje part när du vill tillämpa åtkomstkontroller på resurser som Exchange eller SharePoint Online. Dessutom bör enheterna bara vara registrerade i en lösning åt gången.

## <a name="next-steps"></a>Nästa steg

[Fas 2: Kommunikationsplan](/intune-classic/plan-design/migration-phase2-communication-plan)

