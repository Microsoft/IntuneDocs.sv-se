---
title: "Ordna användare och enheter genom att skapa grupper | Microsoft Intune"
description: "Skapa användare och grupper för din Intune-prenumeration"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4f8db75ed17e70dae5d3507b6af33a835c1658e9
ms.openlocfilehash: 5195de40f35085c45ae63957da1a9058ed7d6493


---


# <a name="create-groups-to-organize-users-and-devices"></a>Skapa grupper för att organisera användare och enheter
Grupper i Intune ger stor flexibilitet att hantera enheter och användare. Du kan konfigurera grupper efter organisationens behov (till exempel genom geografisk plats, avdelning eller maskinvaruegenskaper) och använda dem för att utföra olika administrativa uppgifter, från att distribuera principer för en uppsättning användare till att distribuera program till en uppsättning enheter.

## <a name="group-management-moving-to-azure-ad"></a>Grupphantering flyttar till Azure AD

**Från och med november 2016**, kommer nya konton att hantera användare och enhetsgrupper i Azure Active Directory (AD)-portalen. I december 2016 kommer Intune-produktteamet att börja migrera befintliga kunder till den nya Azure AD-baserade grupphantering. Alla användargrupper och enhetsgrupper kommer att migreras till Azure AD-säkerhetsgrupper. Vi påbörjar inte migreringen förrän vi kan minimera dess inverkan på ditt dagliga arbete, och vi förväntar oss att kunna utföra den utan att det påverkar slutanvändarna. Vi kommer även att meddela dig innan vi migrerar dina konton.


>[!IMPORTANT]
>
>Om du öppnar arbetsytan Grupper i Intune-portalen och ser **Intune-användargrupper hanteras nu som grupper i Azure Active Directory** med en länk till Azure Active Directory-portal, använder du redan den *nya* metoden för Azure AD-säkerhetsgrupper för grupphantering i Intune. Information om hur du skapar grupper finns i [Hantera grupper i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-accessmanagement-manage-groups).
>
>Om du inte ser länken till Azure AD-portalen använder du fortfarande Intune-portalen för hantering av grupper.

## <a name="group-management-in-the-intune-portal"></a>Grupphantering i Intune-portalen

Både enhets- och användargrupper skapas på arbetsytan Grupper i Intune-administrationskonsolen.

![Arbetsytan Grupper i administrationskonsolen](./media/groups.png)


> [!TIP]
> Mer information om hur du använder grupper finns i [Använda grupper för att hantera användare och enheter med Microsoft Intune](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).


## <a name="create-a-device-group"></a>Skapa en enhetsgrupp
Använd enhetsgrupperna för att distribuera appar och uppdateringar, samt konfigurera andra funktioner. Du kan till exempel skapa gruppen ”Mina enheter” med följande steg:

1.  I [Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Grupper** > **Översikt** > **Skapa grupp**.

2.  Skriv ”Mina enheter” som **Gruppnamn**, välj **Alla enheter** i listan med överordnade grupper och klicka sedan på **Nästa**.

3.  Välj **Alla enheter** på sidan **Definiera medlemsskapsvillkor** för att indikera att gruppen innehåller både mobila enheter och datorer.

4.  Välj **Nästa** på sidan **Ange direkt medlemskap**. Om du tidigare skapade en grupp som inte innehöll alla enheter, och du vill lägga till specifika enheter till din nya grupp, kan du göra det här.

5.  På sidan **Sammanfattning** granskar du de åtgärder som kommer att vidtas och väljer sedan **Slutför**.

Du kan hitta de nyligen skapade grupperna i listan **Grupper** under **Alla enheter** på arbetsytan **Grupper**. Här kan du också redigera eller ta bort gruppen.

## <a name="create-a-user-group"></a>Skapa en användargrupp
Använd användargrupper för att distribuera programvara och enhetsprinciper. Du kan till exempel skapa gruppen ”Intune-användare” med följande steg:

1.  I [Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Grupper** > **Översikt** > **Skapa grupp**.

2.  Skriv ”Intune-användare” som **Gruppnamn**, välj **Alla användare** i listan med överordnade grupper och välj sedan **Nästa**.

3.  På sidan **Definiera medlemskapsvillkor** ställer du in **Starta gruppmedlemskap med** på **Alla användare i den överordnade gruppen**.

4.  Välj **Bläddra**intill **Exkludera medlemmar från dessa säkerhetsgrupper** och välj sedan **Företagsadministratör**. Med detta exkluderande kan du hantera gruppen Intune-användare utan att företagsadministratörskontot (även kallat innehavaradministratör) påverkas.

5.  Välj **Nästa** på sidan **Ange direkt medlemskap**. Du behöver inte göra något här eftersom du vill att gruppen Intune-användare ska innehålla alla användare, med undantag för företagsadministratören.

6.  På sidan **Sammanfattning** kan du granska de åtgärder som vidtas och sedan välja **Slutför**.

Du kan hitta de nyligen skapade grupperna i listan **Grupper** under **Alla användare** på arbetsytan **Grupper**. Här kan du också redigera eller ta bort gruppen.



### <a name="next-steps"></a>Nästa steg
Gratulerar! Du är klar med steg 5 i *snabbstartsguiden för Intune*.

>[!div class="step-by-step"]

>[&larr; **Hantera Intune-licenser**](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md) [**Skapa principer och appar** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  



<!--HONumber=Nov16_HO4-->


