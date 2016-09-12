---
title: "Använda grupper för att hantera användare och enheter | Microsoft Intune"
description: Skapa och hantera grupper med arbetsytan Grupper.
keywords: 
author: Nbigman
manager: angrobe
ms.date: 06/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb9b01ce-9b9b-4c2a-bf99-3879c0bdaba5
ms.reviewer: lpatha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e7c680c43b8c9120755ec3c652cf7ec1cbcc3472
ms.openlocfilehash: b13e2ff2f4822d71ef8cff9d835e32b99cb3e4ab


---
# Använda grupper för att hantera användare och enheter i Microsoft Intune

I det här avsnittet beskrivs hur man skapar grupper i Intune. Det innehåller även information om hur hanteringen av grupper kommer att ändras under de kommande månaderna. Mer information om den *aktuella* -metoden för grupphantering finns under [Skapa grupper för att hantera användare och enheter med Microsoft Intune](#Create-groups-to-manage-users-and-devices-with-Microsoft-Intune) i det här avsnittet.

## Meddelande om kommande förbättringar till administratörsupplevelsen för grupper

Efter att ha fått feedback om en enskild upplevelse för grupper och målgrupper i Enterprise Mobility + Security har vi gjort om Intune-grupper till Azure Active Directory-baserade säkerhetsgrupper. Det skapar en enhetlig grupphantering i Intune och Azure Active Directory (Azure AD). Det innebär att du undviker duplicerade grupper mellan tjänster och kan utöka med PowerShell och Graph. 

### Hur påverkar det här mig nu?
Den här ändringen påverkar dig inte nu, men vi kan berätta vad som är på gång:

-   Från september kommer nya konton som har etablerats efter den månatliga tjänsteuppdateringen att använda Azure AD-säkerhetsgrupper i stället för Intune-användargrupper.   
-   I oktober kommer nya konton som har etablerats efter den månatliga tjänsteuppdateringen att hantera både användargrupper och enhetsgrupper i Azure AD-portalen. Befintliga kunder påverkas inte
-   I november kommer Intune-produktteamet att börja migrera befintliga kunder till den nya upplevelsen med Azure AD-baserad grupphantering. Alla aktuella användargrupper och enhetsgrupper i Intune kommer att migreras till Azure AD-säkerhetsgrupper. Migreringen kommer att ske batchvis med start i november. Vi påbörjar inte migreringen förrän vi kan minimera dess inverkan på ditt dagliga arbete och kan utföra den utan att det påverkar slutanvändarna. Vi meddelar dig innan ditt konto migreras.


### Hur och när kommer jag att migrera till den nya upplevelsen?
Aktuella kunder kommer att migreras under en viss tidsperiod. Vi håller på att färdigställa schemat för migreringen och kommer att uppdatera det här avsnittet med mer information om ett par veckor. Du får ett meddelande innan du migreras. Om du har några frågor angående migreringen kan du kontakta vårt migreringsteam på [intunegrps@microsoft.com](intunegrps@microsoft.com).

### Vad händer med mina befintliga användargrupper och enhetsgrupper?
 De användargrupper och enhetsgrupper som du har skapat kommer att migreras till Azure AD-säkerhetsgrupper. Intune-standardgrupper, till exempel gruppen Alla användare, migreras endast om du använder dem i distributioner vid tidpunkten för migreringen. Migreringen kan vara mer komplex för vissa grupper och vi meddelar dig om ytterligare steg krävs.

### Vilka nya funktioner kommer att vara tillgängliga för mig?
Här är de nya funktionerna som introduceras:

-    Azure AD-säkerhetsgrupper stöds i Intune för alla typer av distributioner.
-    Azure AD-säkerhetsgrupper stöder gruppering av enheter tillsammans med användare.
-    Azure AD-säkerhetsgrupper kommer att ha stöd för dynamiska grupper med Intune-enhetsattribut. Till exempel kommer du att kunna gruppera enheter dynamiskt baserat på plattform, till exempel iOS. När en ny iOS-enhet registreras i din organisation läggs den därmed automatiskt till i den dynamiska iOS-enhetsgruppen.
-    Delade administratörsupplevelser för grupphantering i Azure AD och Intune.
- *Intune-tjänstadministratörsrollen* kommer att läggas till i Azure AD så att tjänstadministratörer i Intune kan utföra grupphanteringsuppgifter i Azure AD.




### Vilka Intune-funktioner kommer inte att vara tillgängliga?
Grupphanteringen kommer att vara bättre, men vissa Intune-funktioner kommer inte att vara tillgängliga efter migreringen.

#### Funktionen Hantering av grupper

-   Du kommer inte att kunna undanta medlemmar eller grupper när du skapar en ny grupp. Men med dynamiska grupper i Azure AD kan du använda attribut för att skapa avancerade regler för att undanta medlemmar baserat på kriterier.
-   Det kommer inte att finnas stöd för grupperna **Användare utan grupp** och **Enheter utan grupp**. Dessa grupper migreras inte.


#### Gruppberoende funktioner

-   Rollen Tjänstadministratör kommer inte att ha behörighet att **hantera grupper**.
-   Du kommer inte att kunna gruppera Exchange ActiveSync-enheter.  Gruppen **Alla Exchange ActiveSync-hanterade enheter** kommer att konverteras från en grupp till en rapport.
-  Pivotering med grupper i rapporter kommer inte att vara tillgängligt.
-  Anpassade meddelanderegler för specifika grupper kommer inte att vara tillgängligt.

### Vad kan jag göra för att förbereda mig för den här ändringen?
 Vi har rekommendationer som underlättar övergången:

- Ta bort alla oönskade eller onödiga Intune-grupper före migreringen.
- Utvärdera din användning av undantag i grupper och fundera på om du kan ändra dina grupper så att du inte behöver använda undantag.
-  Om det finns administratörer i organisationen som inte har behörighet att skapa grupper i Azure AD kan du be Azure AD-administratören att lägga till dem i rollen **Intune-tjänstadministratör** i Azure AD.


## Använda grupper för att hantera användare och enheter med Microsoft Intune

I det här avsnittet beskrivs hur du skapar Intune-grupper i Intune-administratörskonsolen.

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



<!--HONumber=Aug16_HO4-->


