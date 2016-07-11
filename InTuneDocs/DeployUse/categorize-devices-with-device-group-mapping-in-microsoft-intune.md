---
title: Kategorisera enheter med gruppmappning av enheter | Microsoft Intune
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: sumitp
ms.suite: ems
ms.sourcegitcommit: bb30b8e61a768b15e2f09993f4dceae8f4e1bd8a
ms.openlocfilehash: 55f811153bf37048a4fcdfc6da301a5f181700c3


---

# Kategorisera enheter med gruppmappning av enheter i Microsoft Intune
Använd **mappning av enhetsgrupp** i Microsoft Intune för att gruppera enheter i kategorier som du definierar för att göra det enklare att hantera dessa enheter. 

Mappning av enhetsgrupp använder följande arbetsflöde:
1. Du skapar Intune-enhetsgrupper för varje kategori som du vill använda.
2. Du konfigurerar regler för mappning av enhetsgrupp som mappar den kategori som du skapade.
3. När slutanvändare registrerar sina enheter måste de välja en kategori från de kategorier du har konfigurerat. Efter att de har valt kommer enheten att läggas till automatiskt i motsvarande enhetsgrupp som du har skapat.
4. Du kan sedan använda dessa enhetsgrupper när du distribuerar principer och appar.

Exempel på kategorier kan vara:
* Personligt
* Butiksenhet
* Demonstrationsenhet
* Försäljning
* Redovisning
* Manager

Du kan dock konfigurera vilka kategorier du vill.

## Konfigurera inställningar för mappning av enhetsgrupp
1. Skapa en Intune-enhetsgrupp för varje enhetskategori som du vill använda. Mer information om hur du skapar grupper finns i [Använda grupper för att hantera användare och enheter med Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).
2. Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och välj **Admin**.
3. På arbetsytan **Administration** expanderar du **Hantering av mobila enheter** och väljer sedan **Mappning av enhetsgrupp**.
4. På sidan **Mappning av enhetsgrupp** kan du aktivera mappning av enhetsgrupp.
5. Välj **Lägg till** för att skapa en ny mappningsregel.
6. I dialogrutan **Lägg till en mappningsregel för enhetsgrupp** anger du namnet på den kategori du vill skapa och använder sedan listrutan för att välja den enhetssamling som du vill mappa denna kategori till. Välj **Lägg till** när du är klar.
7. När du har lagt till alla kategorier och grupper som önskas väljer du **Spara**.

Nu när användare registrerar sina enheter får de se en lista med de kategorier du har konfigurerat. När användaren har valt en kategori och slutfört registreringen läggs enheten till i den enhetsgrupp som motsvarar den kategori som har valts.

### Se även
[Använda grupper för att hantera användare och enheter med Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)


<!--HONumber=Jun16_HO3-->


