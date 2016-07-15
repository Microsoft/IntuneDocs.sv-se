---
title: "Använda grupper för att hantera användare och enheter | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb9b01ce-9b9b-4c2a-bf99-3879c0bdaba5
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cc64e51499908d08823429871cda91dfb0078b1e
ms.openlocfilehash: a1f6dfc7629481403c40a1ce927b588f67e5fa74


---

# Använda grupper för att hantera användare och enheter med Microsoft Intune

Du skapar och hanterar grupper med hjälp av arbetsytan **Grupper** i Microsoft Intune-administrationskonsolen. Översiktssidan **Grupper** innehåller statusöversikter som hjälper dig att identifiera och prioritera problem som kräver din uppmärksamhet:

-   Aviseringar
-   Programuppdateringar
-   Slutpunktsskydd
-   Princip
-   Programvaruhantering

Dessutom visas din grupphierarki med statussammanfattningar som hjälper dig att identifiera och lösa problem för medlemmar i en vald grupp.


> [!TIP]
> När du skapar grupper bör du överväga hur du ska tillämpa de olika principerna. Du kan t.ex. ha principer som är specifika för ett operativsystem för en enhet och principer som är specifika för olika roller i din organisation eller för organisationsenheter som du redan har definierat i Active Directory. Vissa tycker att det är praktiskt att ha enhetsgrupper som är specifika för iOS, Android och Windows och användargrupper som är specifika för olika organisationsroller.
>
> Du vill förmodligen skapa en standardprincip som gäller för alla grupper och enheter och som fastställer de grundläggande kompatibilitetskraven för ditt företag. Sedan kan du skapa mer specifika principer för de bredaste användar- och enhetskategorierna, t.ex. e-postprinciper för vart och ett av enhetsoperativsystemen.
>
> Var noga med att ge dina principer namn som gör det lätt att identifiera dem längre fram. Ett exempel på ett bra beskrivande principnamn är **WP e-postprincip för hela företaget**.
>
> Varje gång som du skapar en begränsande princip vill du sannolikt informera användarna om den. Så när du har skapat de mer allmänna grupperna och principerna bör du vara noga med hur du skapar mindre grupper, så att du minskar risken för onödig information.


## Skapa en enhetsgrupp

1.  I Intune-administratörskonsolen klickar du på **Grupper** &gt; **Översikt** &gt; **Skapa grupp**.

2.  Ange ett namn och en valfri beskrivning för gruppen och välj en enhetsgrupp som den överordnade gruppen. Välj **Nästa**.

3.  På sidan **Definierar medlemskapskriterier** markerar du typen av enheter som gruppen kommer att innehålla. Fler alternativ för att konfigurera gruppen beror på vilken typ av enheter som du väljer:

    -   **Dator:** Ange om du vill lägga till alla medlemmar i den överordnade gruppen, ange de organisationsenheter som du vill ta med eller undanta och de domäner som du vill ta med eller undanta. Organisationsenheten och domäninformationen om en dator hämtas från förteckningen.

    -   **Mobil:** Ange om du bara vill ta med mobila enheter som hanteras av Intune, de som hanteras av Exchange ActiveSync eller båda.

    -   **Alla enheter:** Det här alternativet innehåller alla enheter utan undantag baserat på kriterier.

4.  På sidan **Definiera direkt medlemskap** tas med eller utesluts enskilda enheter som du anger genom att klicka på **Bläddra**. Om du använder alternativet för att välja enheter som inte ingår i den överordnade gruppen du angav läggs enheterna automatiskt till den överordnade gruppen.


5.  Granska de åtgärder som kommer att vidtas på sidan **Sammanfattning**. Välj **Slutför**.

Du hittar grupperna som skapats i listan **Grupper** under den överordnade gruppen på arbetsytan **Grupper**. Här kan du också redigera eller ta bort gruppen.

## Skapa en användargrupp

1.  I Intune-administratörskonsolen klickar du på **Grupper** &gt; **Översikt** &gt; **Skapa grupp**.

2.  Ange ett namn och en valfri beskrivning för gruppen och välj en användargrupp som den överordnade gruppen. Välj **Nästa**.

3.  På sidan **Definiera medlemskapskriterier** kan du ange om alla medlemmar i den överordnade gruppen ska inkluderas eller om du vill börja med en tom grupp.  Du kan sedan ta med eller utesluta medlemmar baserat på **Säkerhetsgrupper** med användare som du konfigurerar manuellt i [administrationscenter för Office 365](http://go.microsoft.com/fwlink/?LinkId=698854) eller som synkroniseras från din lokala Active Directory. Om medlemskap i en säkerhetsgrupp ändras kan även medlemskap i användargrupperna som är baserade på säkerhetsgruppen ändras.

    > [!IMPORTANT]
    > Om din grupp innehåller medlemmar från specifika säkerhetsbehörigheter eller manager-grupper, och du även exkluderar medlemmar från specifika grupper, tas medlemmarna du ursprungligen inkluderade för närvarande bort. Om du vill skapa en grupp som både har inkluderade medlemmar och exkluderade medlemmar, rekommenderar vi att du först skapar en överordnad grupp med inkluderade medlemmar och sedan skapar en underordnad grupp där du anger exkluderade medlemmar. Du kan sedan använda den underordnade gruppen för Intune-principer, profiler och app-distribution.

    > [!NOTE]
    > Du kan skapa en grupp baserad på den hanterare som användarna rapporterar till i Azure-hanteringsportal. Gruppen ska vara dynamisk, ändras då anställda läggs till eller tas bort från denna hanterares team i Azure Active Directory. Stegen som du följer för att skapa en Azure-grupp baserat på en hanterare beskrivs i [Använda attribut för att skapa avancerade regler](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/) i avsnittet **Konfigurera en grupp som en ”Manager”-grupp**.


4.  På sidan **Definiera direkt medlemskap** tas med eller utesluts enskilda användare som du anger genom att klicka på **Bläddra**. Om du använder alternativet för att välja användare som inte ingår i den överordnade gruppen du angav läggs enheterna automatiskt till den överordnade gruppen. Längst ned i dialogrutan **Välj medlemmar** hittar du alternativet för att lägga till en användare manuellt. Detta är praktiskt om du vill lägga till en användare som ännu inte har en registrerad enhet.


5.  Granska de åtgärder som kommer att vidtas på sidan **Sammanfattning**. Välj **Slutför**.

Du hittar grupperna som skapats i listan **Grupper** under den överordnade gruppen på arbetsytan **Grupper**. Här kan du också redigera eller ta bort gruppen.

> [!TIP]
> Säkerhetsgrupper är en utmärkt resurs när du ska fylla användargrupper. Eftersom dina säkerhetsgrupper definierar vem som har åtkomst till vilka resurser så kan de lätt överföras till Intune-användargrupper. Säkerhetsgrupper som synkroniseras från Active Directory till Azure Active Directory, eller som skapas direkt i Azure Active Directory via administrationscenter för Office 365 eller Azure-administrationsportalen, kan alla användas för att skapa användargrupper i Intune.

## Anpassa vyer till administratörsroller
Med filtrerade gruppvyer kan du anpassa vyn som administratörer kan se baserat på deras roll och begränsa vilka grupper som varje IT-administratör kan hantera. Detta kan vara användbart när:

-   IT-administratörer bara ska kunna distribuera objekt till särskilda användare och enheter.

-   Du vill endast visa relevanta grupper för varje IT-administratör.

Du kan konfigurera filtrerade gruppvyer för administratörer i Intune-administrationskonsolen. Mer information finns i [Vad du behöver veta innan du startar Microsoft Intune](/intune/get-started/what-to-know-before-you-start-microsoft-intune).

När du har konfigurerat filtrerade gruppvyer för en tjänstadministratör kan administratören:

-   Visa och välja de grupper som du angav när du distribuerade programvaran eller principerna eller använde rapporter

-   Inte ta emot information om status på följande sidor i administrationskonsolen:

    -   **Systemöversikt**

    -   **Översikt över grupper**

    -   **Endpoint Protection-översikt**

    -   **Översikt över aviseringar**

    -   **Översikt över programvara**

    -   **Uppgifter**

### Konfigurera filtrerade gruppvyer

1.  I Intune-administrationskonsolen väljer du **Admin** &gt; **Administratörshantering** &gt; **Tjänstadministratörer**.

2.  Välj den tjänstadministratör för vilken du vill filtrera grupper och klicka på **Hantera grupper**.

3.  I dialogrutan **Markera de grupper som visas för den här tjänstadministratören** lägger du till de grupper som den valda tjänstadministratör kommer att kunna få åtkomst till och klickar sedan på **OK**.

När du har konfigurerat de filtrerade gruppvyerna kommer IT-administratörerna att kunna visa och välj de grupper som du valt.

## Hantera grupper
När du har skapat dina grupper fortsätter du att hantera dem enligt organisationens behov.

Du kan ändra gruppers namn och beskrivning och vilka som ingår i gruppen.

Du kan ta bort en grupp som inte längre tjänar organisationens behov. Om du tar bort en grupp så innebär det inte att du tar bort de användare som tillhör gruppen.

## Nästa steg

### Kontrollera din design
När du har skapat dina grupper och principer kontrollerar du de praktiska effekterna av din design genom att kontrollera **Avsett värde** och **Status**.

1. Välj vilken enhet du vill från en enhetsgrupp och bläddra igenom informationskategorierna överst på skärmen.
2. Välj **Princip** . Du ser något som liknar denna skärmbild från en Android-enhets principinställningar.

![Exempel på iOS-inställningsprincip](../media/Intune-Device-Policy-v.2.jpg)

Varje princip har ett **Avsett värde** och en **Status**. Det avsedda värdet är vad du hade för avsikt att uppnå när du tilldelade principen. Statusen är vad du i själva verket har uppnått när samtliga principer som gäller för enheten och de begränsningar och krav som gäller för maskinvara och operativsystem bedöms tillsammans.  På skärmbilden ser du två tydliga exempel:

-   **Tillåt enkla lösenord** har getts värdet **Ja**, vilket kan ses i kolumnen **Avsett värde** , men dess **Status** är **Saknas**. Detta beror på det faktum att enkla lösenord inte stöds för Android-enheter.

-   På samma sätt tillämpas inte det utökade principobjektet, **E-postinställningar för iOS-enheter**, på den här enheten eftersom det är en Android-enhet.

> [!NOTE]
> Kom ihåg att om två principer med olika begränsningsnivåer tillämpas på samma enhet eller användare, så tillämpas i praktiken den mer restriktiva principen.



<!--HONumber=Jun16_HO4-->


