---
# required metadata

title: Kategorisera enheter med mappning av enhetsgrupp i Microsoft Intune | Microsoft Intune
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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

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
2. Klicka på **Admin** i [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com).
3. I arbetsytan **Administration** expanderar du **Hantering av mobila enheter** och klickar sedan på **Mappning av enhetsgrupp**.
4. På sidan **Mappning av enhetsgrupp** kan du aktivera mappning av enhetsgrupp.
5. Klicka på **Lägg till** att skapa en ny mappningsregel.
6. I dialogrutan **Lägg till en mappningsregel för enhetsgrupp** anger du namnet på den kategori du vill skapa och använder sedan listrutan för att välja den enhetssamling som du vill mappa denna kategori till. Klicka på **Lägg till** när du är klar.
7. När du har lagt till alla kategorier och grupper som önskas klickar du på **Spara**.

Nu när användare registrerar sina enheter får de se en lista med de kategorier du har konfigurerat. När användaren har valt en kategori och slutfört registreringen läggs enheten till i den enhetsgrupp som motsvarar den kategori som har valts.

### Se även
[Använda grupper för att hantera användare och enheter med Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)

<!--HONumber=May16_HO1-->

