---
# required metadata

title: Skapa grupper för att organisera användare och enheter som prenumererar på utvärderingen | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7162cad3-5c14-43f3-a760-833ffd7786b1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Skapa grupper för att organisera användare och enheter som prenumererar på utvärderingen
Grupper i Intune ger stor flexibilitet för att hantera dina enheter och användare. Du kan konfigurera grupper efter organisationens behov (till exempel genom geografisk plats, avdelning eller maskinvaruegenskaper) och använda dem för att utföra olika administrativa uppgifter i skala, från att ange principer för en uppsättning användare till att distribuera program till en uppsättning enheter.

## Skapa en enhetsgrupp
Använd enhetsgrupper för att distribuera programvara och uppdateringar och konfigurera inställningsprinciper för Microsoft Intune Agent och Windows brandvägg. Du kan till exempel skapa gruppen ”Mina utvärderingsenheter” med följande steg:

1.  I [Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Översikt** &gt; **Skapa grupp**

2.  Skriv ”Mina utvärderingsenheter” som **Gruppnamn**, välj **Alla enheter**i den överordnade grupplistan och välj sedan **Nästa**.

3.  Välj **Alla enheter** på sidan **Definiera medlemsskapsvillkor** för att indikera att gruppen innehåller både mobila enheter och datorer.

4.  Välj **Nästa** på sidan **Ange direkt medlemskap**. Om du tidigare har skapat en grupp som inte innehåller alla enheter, och du vill lägga till specifika enheter till din nya grupp, kan du göra det här.

5.  På sidan **Sammanfattning** kan du granska de åtgärder som vidtas och sedan välja **Slutför**.

Du kan hitta de nyligen skapade grupperna i listan **Grupper** under **Alla enheter** på arbetsytan **Grupper**. Här kan du också redigera eller ta bort gruppen.

## Skapa en användargrupp
Använd användargrupper för att distribuera programvara och enhetsprinciper. Du kan till exempel skapa gruppen ”Mina utvärderingsanvändare” med följande steg:

1.  I [Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Översikt** &gt; **Skapa grupp**

2.  Skriv ”Mina utvärderingsanvändare” som **Gruppnamn**, välj **Alla användare**i den överordnade grupplistan och välj sedan **Nästa**.

3.  På sidan **Definiera medlemskapsvillkor** ställer du in **Starta gruppmedlemskap med** på **Alla användare i den överordnade gruppen**

4.  Välj **Bläddra**intill **Exkludera medlemmar från dessa säkerhetsgrupper** och välj sedan **Företagsadministratör**. Med detta undantag kan du hantera gruppen Mina utvärderingsanvändare utan att företagsadministratörskontot (även kallat innehavaradministratören) påverkas.

5.  Välj **Nästa** på sidan **Ange direkt medlemskap**. Du behöver inte göra något här eftersom du vill att gruppen Mina utvärderingsanvändare ska innehåller alla användare, med undantag för företagsadministratören.

6.  På sidan **Sammanfattning** kan du granska de åtgärder som vidtas och sedan välja **Slutför**.

Du hittar den nyligen skapade gruppen i listan **Grupper** under **Alla användare** på arbetsytan **Grupper**. Här kan du också redigera eller ta bort gruppen.

Mer information om hur du använder grupper finns i [Använda grupper för att hantera användare och enheter med Microsoft Intune](/Intune/Deploy-Use/use-groups-to-manage-users-and-devices-with-microsoft-intune)

### Nästa steg
Gratulerar! Du har precis slutfört steg 3 i genomgången av *Microsoft Intune-utvärderingen*.

>[!div class="step-by-step"]

>[&larr; **Lägg till användare**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md)     [**Skapa principer** &larr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)  


<!--HONumber=May16_HO2-->


