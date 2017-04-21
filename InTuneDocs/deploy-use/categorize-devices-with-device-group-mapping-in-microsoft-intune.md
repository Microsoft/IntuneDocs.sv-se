---
title: Kategorisera enheter med gruppmappning av enheter | Microsoft Docs
description: "Använd mappning av enhetsgrupp i Microsoft Intune för att gruppera enheter i kategorier som du definierar för att göra det enklare att hantera dessa enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 57c739444c18d12a6d7ee8ca591f9a1dd72985d7
ms.lasthandoff: 04/14/2017

---

# <a name="categorize-devices-with-device-group-mapping-in-microsoft-intune"></a>Kategorisera enheter med gruppmappning av enheter i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Använd **mappning av enhetsgrupp** i Microsoft Intune för att automatiskt lägga till enheter i grupper baserat på kategorier som du definierar för att göra det enklare att hantera dessa enheter. 

Mappning av enhetsgrupp använder följande arbetsflöde:
1. Skapa kategorier som användare väljer från när de registrerar sina enheter
2. Du skapar grupper eller använder befintliga grupper för varje kategori som du vill använda. Beroende på vilken version av Intune som du använder ska dessa antingen vara Intune-grupper eller Azure Active Directory-säkerhetsgrupper.
2. Du konfigurerar regler som mappar den kategori som du valt åt enhetsgruppen du skapat.
3. När slutanvändare registrerar sina enheter måste de välja en kategori från de listan över kategorier som du har konfigurerat. Efter att de har valt läggs enheten automatiskt till i motsvarande grupp som du har skapat. Om en enhet redan har registrerats kommer användaren uppmanas att välja en kategori nästa gång de öppnar appen i företagsportalen.
4. Du kan sedan distribuera principer och appar för dessa grupper.

Du kan skapa vilken typ av enhetskategori som du vill, till exempel:
* Butiksenhet
* Demonstrationsenhet
* Försäljning
* Redovisning
* Manager

## <a name="important-information-about-a-change-in-group-management-for-intune"></a>Viktig information om en ändring i grupphantering för Intune

Baserat på er feedback håller vi nu på att implementera enhetlig gruppering och målanpassning med Enterprise Mobility + Security. Av den anledningen kommer vi snart att konvertera Intune-grupper till Azure Active Directory-baserade säkerhetsgrupper. Efter den här ändringen kommer du inte längre skapa grupper med Intune. Du kommer istället skapa dem i Azure-Portal. Den här ändringen genomförs gradvis och du kan läsa fullständig information om den här ändringen och dess tidslinje i [det här avsnittet](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

### <a name="which-procedure-in-this-topic-should-you-use-to-configure-device-group-mapping"></a>Vilken procedur i det här avsnittet bör du använda för att konfigurera mappning av enhetsgrupper?

På grund av den stegvisa implementeringen av Azure Active Directory-baserade säkerhetsgrupper, måste du öppna arbetsytan **Grupper** i [Intune-administrationskonsolen](https://manage.microsoft.com) för att identifiera vilken metod du ska använda:

-  Om du ser en länk till Azure Portal så använder du inte längre Intune-grupper. Följ proceduren [Så konfigurerar du mappning av enhetsgrupper för Azure Active Directory-grupper](/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-azure-active-directory-groups) nedan.
-  Om du inte ser en länk till Azure Portal så använder du fortfarande Intune-grupper. Följ proceduren [Så konfigurerar du mappning av enhetsgrupper för Intune-grupper](/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-intune-groups) nedan.

## <a name="how-to-configure-device-group-mapping-for-intune-groups"></a>Så konfigurerar du mappning av enhetsgrupper för Intune-grupper
1. Skapa en Intune-enhetsgrupp eller identifiera en befintlig grupp för varje enhetskategori som du vill använda. Mer information om hur du skapar grupper finns i [Använda grupper för att hantera användare och enheter med Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).
2. Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och välj **Admin**.
3. På arbetsytan **Administration** expanderar du **Hantering av mobila enheter** och väljer sedan **Mappning av enhetsgrupp**.
4. På sidan **Mappning av enhetsgrupp** kan du aktivera mappning av enhetsgrupp.
5. Välj **Lägg till** för att skapa en ny mappningsregel.
6. I dialogrutan **Lägg till en mappningsregel för enhetsgrupp** anger du namnet på den kategori du vill skapa och använder sedan listrutan för att välja den enhetssamling som du vill mappa denna kategori till. Välj **Lägg till** när du är klar.
7. När du har lagt till alla kategorier och grupper som önskas väljer du **Spara**.



## <a name="how-to-configure-device-group-mapping-for-azure-active-directory-groups"></a>Så konfigurerar du mappning av enhetsgrupper för Azure Active Directory-grupper

### <a name="step-1---create-device-categories-in-the-intune-administration-console"></a>Steg ett – Skapa enhetskategorier i Intune-administrationskonsolen
1. Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och välj **Admin**.
3. På arbetsytan **Administration** expanderar du **Hantering av mobila enheter** och väljer sedan **Enhetskategorier**.
4. På sidan **Enhetskategorier** visas en lista där du kan konfigurera enhetskategorier: 
- Du kan ange ett namn och sedan klicka på **Lägg till** för att lägga till det som en ny enhetskategori.
- Dessutom kan du välja en kategori och sedan **Ta bort** den.

Du kommer att använda enhetskategorinamnet när du skapar Azure Active Directory-säkerhetsgrupper i steg två.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Steg två – Skapa Azure Active Directory-säkerhetsgrupper

I det här steget kommer du att skapa dynamiska grupper i Azure Portal baserat på enhetskategori och enhetskategorinamn.

Se avsnittet [Using attributes to create advanced rules](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) (Använda attribut för att skapa avancerade regler) i Azure Active Directory-dokumentationen för att fortsätta.
Använd informationen i det här avsnittet för att skapa en enhetsgrupp med en avancerad regel med hjälp av **deviceCategory**-attributet.
Till exempel (**device.deviceCategory - eq** "<*enhetskategorinamnet som du fick från Intune-administrationskonsolen*>")


## <a name="after-you-configure-device-groups"></a>När du har konfigurerat enhetsgrupper

När användare registrerar sina enheter får de se en lista med de kategorier som du har konfigurerat. När användaren har valt en kategori och slutfört registreringen läggs enheten till i den Intune-enhetsgruppen eller Active Directory-säkerhetsgruppen som motsvarar den kategori som har valts.

### <a name="see-also"></a>Se även
[Använda grupper för att hantera användare och enheter med Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)

