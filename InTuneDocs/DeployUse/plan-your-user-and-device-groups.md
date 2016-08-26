---
title: "Planera dina användar- och enhetsgrupper | Microsoft Intune"
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 82ab2dbfada6c0745195da149d5f0dc1948ceb92
ms.openlocfilehash: e89d8384532b994d810649fc07c698237e2f3cec


---

# Planera dina användar- och enhetsgrupper
Grupper i Intune ger stor flexibilitet vid hanteringen av enheter och användare. Du kan skapa grupper som passar organisationens behov enligt:

- geografisk plats
- avdelning
- maskinvaruegenskaper
- operativsystem
- om enheten är användarägd eller företagsägd


## Så här fungerar Intune-grupper


Standardvyn för noden Grupper i Intune-administrationskonsolen är:

![Skärmbild av standardvyn för noden Grupper i Intune-konsolen](/intune/media/Intune_Planning_Groups_Default_small.png)

Principer distribueras till grupper. Grupphierarkin är därför en av de viktigaste designaspekterna. Det är också viktigt att du vet att det inte går att ändra en grupps överordnade grupp när gruppen har skapas. Därför är gruppernas design ytterst viktig från det ögonblick då du börjar använda Intune-tjänsten. Här beskrivs några av de rekommenderade metoderna för att designa en grupphierarki baserat på din organisations behov.

## Regler för gruppmedlemskap

1. En grupp kan innehålla användare eller enheter, men inte båda.

    * **Enhetsgrupper:** Detta inkluderar både datorer och mobila enheter. Innan du kan lägga till en dator till en grupp måste den vara registrerad. Innan du kan lägga till en mobilenhet till en grupp måste din miljö konfigureras för mobila enheter och enheterna måste vara registrerade eller identifierade av Exchange ActiveSync.

    * **Användargrupp:** En grupp kan innehålla användare från säkerhetsgrupper, det vill säga grupper som ska synkroniseras från Active Directory. Om du inte använder Active Directory-synkronisering kan du skapa dessa grupper manuellt .

2. En enhet eller en användare kan tillhöra mer än en grupp.

3. En grupp kan innehålla och undanta medlemmar baserat på följande medlemskapsregler:

    * **Villkor för medlemskap:** Detta är dynamiska regler som Intune kör för att ta med eller undanta medlemmar. Dessa villkor använder **säkerhetsgrupper** och annan information som synkroniseras från din lokala Active Directory (AD). När säkerhetsgruppen eller data ändras, ändras gruppmedlemskapet när du synkroniserar med AD.

    * **Direkt medlemskap:** Det här är statiska regler som uttryckligen lägga till eller utelämna medlemmar. Medlemskapslistan är statisk.

4. Active Directory Domain Services (AD DS) krävs inte för att skapa användare eller enhetsgrupper som innehåller användare eller datorer, men i enheten som ska ta med mobila enheter måste din miljö konfigureras för mobila enheter.

    Dessutom måste enheterna identifieras och läggas till i Intune.

## Regler för grupprelationer

1. Alla grupper som du skapar måste ha en överordnad grupp och du kan inte ändra en grupps överordnade grupp när gruppen har skapats.

2. När du lägger till användare eller enheter i en underordnad grupp:

    * Underordnade grupper är alltid delar av den överordnade gruppen.

    * Nya medlemmar som du lägger till en underordnad gruppen läggs automatiskt till gruppens överordnad grupp.

    * Du kan inte lägga till en medlem i en underordnad grupp när medlemmen är inte del av den överordnade gruppen.

3. Medlemskap i en överordnad grupp definierar tillgängliga medlemskap för den underordnade gruppen.

4. När du tar bort en överordnad grupp tas alla underordnade grupper bort.

5. Du kan distribuera innehåll och principer till en överordnad grupp och utesluta distribution till underordnade grupper.

6. Du kan lägga till en specifik användare eller enhet till en underordnad grupp som inte är medlem i den överordnade gruppen. Om du gör det läggs den nya gruppmedlemmen till den överordnade gruppen.

    Du kan inte lägga till en medlem i en underordnad grupp när medlemmen är inte del av den överordnade gruppen.

7. Gruppmedlemskap är rekursivt. Exempel:

    * **Patrik** är endast medlem i en enda grupp: säkerhetsgruppen **Användare av bärbara datorer** .

    * Gruppen **Användare av bärbara datorer** är medlem i säkerhetsgruppen **Godkända användare** .

    * Du skapar en grupp i Intune som använder en dynamisk medlemskapsfråga som innehåller medlemmarna i gruppen **Godkända användare**. Resultatet är att din Intune-användargrupp innehåller **Erik**.

> [!TIP]
> När du skapar grupper bör du tänka på hur du ska tillämpa de olika principerna. Du kan t.ex. ha principer som är specifika för ett operativsystem för en enhet och principer som är specifika för olika roller i din organisation eller för organisationsenheter som du redan har definierat i Active Directory. Vissa tycker att det är praktiskt att ha enhetsgrupper som är specifika för iOS, Android och Windows och användargrupper som är specifika för olika organisationsroller.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your company. Then create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful naming your policies so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy you'll want to communicate it to your users, so after you create the more general groups and policies pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## Inbyggda grupper
Intune innehåller nio inbyggda grupper som du inte kan redigera eller ta bort: <!--maybe a screen shot would be best?-->

-   **Alla användare**
    -   Användare utan grupp
-   **Alla enheter**
    -   Alla datorer
    -   Alla mobila enheter
        -   Alla direkthanterade enheter
        -   Alla Exchange ActiveSync-hanterade enheter
    -   Alla enheter som ägs av företaget
    -   Enheter utan grupp

> [!NOTE]
> Låt ditt motto vara: *enkelhet*. Om din organisation inte har särskilda behov som de som beskrivs nedan bör du hålla allt så enkelt som möjligt och använda standardgruppstrukturen och standardgrupprinciperna så att tjänsten blir lättare att hantera på lång sikt. Underhållet blir enklare om du kan hantera dina användare på samma sätt med bara smärre skillnader beroende på grupp. På så sätt behöver du underhålla färre principer.


### Alla användare och enheter i din organisation
Definiera en överordnad grupp för alla användare och enheter i organisationen eftersom du förmodligen kommer att ha principer som gäller för alla. Du kan använda standardgrupperna **Alla användare** och **Alla enheter** i Intune. Undergrupper som ordnar enheter efter egenskaper, till exempel en grupp för BYOD-enheter (Bring Your Own Device) och en för företagsägda enheter (CO, Corporate Owned), kan dessa grupper vara underordnade grupper till de överordnade grupperna **Alla användare** och **Alla enheter**.

## Anpassa grupper för organisationen

### BYOD-enheter och företagsägda enheter
Om organisationen tillåter att anställda använder sina egna enheter på arbetet (BYOD), tillhandahåller företagsägda enheter (CO) eller en kombination av båda, rekommenderar vi att du tillämpar principer baserat på dessa två typer av enheter.

När det gäller BYOD-enheter eller en kombination bör du planera principer som inte överträder lokala sekretessbestämmelser. Skapa en överordnad grupp för alla användare som ska ta med sina egna enheter (BYOD). Den här gruppen kan sedan användas för att tillämpa principer som gäller för alla användare i kategorin.

![Skärmbild av hur du skapar en överordnad BYOD-grupp](/intune/media/Intune_Planning_Groups_BYOD_small.png)

På liknande sätt kan du skapa en grupp för CO-användarna i organisationen:

![Skärmbild av användargrupper för BYOD och CO på samma nivå](/intune/media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### Grupper för geografiska områden
Om organisationen behöver principer för vissa regioner kan du skapa grupper baserat på geografiskt område. Du kan basera dem på regionala grupper som du kanske redan har skapat i Active Directory (AD) och synkronisera dem till Azure AD. Du kan också skapa dem direkt i Azure AD.

Dessa skärmdumpar visar hur du skapar Intune-grupper baserat på grupper som synkroniserats från din lokala AD. Dessa exempel förutsätter att du har en AD-säkerhetsgrupp som heter **US Users Group**.

1. Börja med att ange den allmänna informationen.

![Skärmbild av området Redigera grupp](/intune/media/Intune_Planning_Groups_AD_General_small.png)

Under Kriterier för medlemskap väljer du **US Users Group**, som synkroniserats från AD, som säkerhetsgruppen som ska användas under Medlemskapsregler.

![Dialogrutan Redigera grupp](/intune/media/Intune_Planning_Groups_AD_Criteria_small.png)

Gå igenom informationen och skapa gruppen genom att välja **Slutför**.

![Dialogrutan Redigera grupp](/intune/media/Intune_Planning_Groups_AD_Summary_small.png)

I vårt exempel har vi också skapat en grupp för Mellanöstern och Asien, MEA.

> [!NOTE]
> Om gruppmedlemskapet inte har fyllts i baserat på medlemskap i säkerhetsgruppen kontrollerar du att dessa medlemmar har tilldelats Intune-licenser.

### Grupper för särskild maskinvara
Om organisationen kräver principer som tillämpas för specifika maskinvarutyper kan du skapa grupper utifrån det här kravet. Du kan basera dem på specifika grupper som du redan har skapat i din lokala AD och synkronisera dem till Azure AD. Du kan också skapa dem direkt i Azure AD. I det här exemplet använder vi **US Users Group** som överordnad grupp till gruppen **Laptop Users**.

![Dialogrutan Välj säkerhetsgrupp](/intune/media/Intune_Planning_Groups_Laptop_small.png)

Nu bör grupphierarkin se ut som nedan. Som du ser finns det nu medlemmar i Intune-gruppen **Laptop Users**. Alla principer som tillämpas på den här gruppen kommer nu att gälla användare av bärbara BYOD-datorer från regionen USA.

![Visning av gruppen Användare av bärbara datorer](/intune/media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### Grupper för specifika operativsystem
Om organisation kräver principer som tillämpas för specifika operativsystem, till exempel Android, iOS eller Windows, kan du skapa grupper utifrån det här kravet. Som i föregående exempel kan du basera dem på operativsystemspecifika grupper som du redan har skapat i din lokala AD och synkronisera dem till Azure AD. Du kan också skapa dem direkt i Azure AD.

Enligt samma metod som i föregående exempel kan vi skapa grupper baserat på användare <!--devices?--> som använder specifika operativsystemplattformar.

> [!NOTE]
> Om du har användare som använder flera mobila plattformar eller operativsystem och du inte har en automatiserad metod för att kategorisera användare som Android-användare, iOS-användare eller Windows-användare, bör du överväga att tillämpa principer på enhetsnivå, vilket ger bättre flexibilitet vid tillämpning av operativsystemspecifika principer.
>
> Du kan inte etablera grupper dynamiskt baserat på enhetens operativsystem. Det gör du med hjälp av AD- eller AAD-säkerhetsgrupper.

![Visning av gruppen Användare av bärbara datorer](/intune/media/Intune_Planning_Groups_OS_Hierachy_small.png)

När alla användargrupper har fyllts i baserat på dessa organisationskrav bör grupphierarkin se ut ungefär så här:

![Vy av grupphierarkin](/intune/media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

Den här hierarkin kan användas för att tillämpa organisationens principer på lämpligt sätt.

### Enhetsgrupper
Du kan också skapa liknande grupper för enheter som du ser nedan för BYOD-scenariot, och börja med en bred grupp som innehåller alla personalägda enheter:

![Dialogrutan Skapa grupp](/intune/media/Intune_Planning_Groups_Device_General_small.png)

Var noga med att välja **Alla enheter (datorer och mobila enheter)** så att gruppen omfattar alla BYOD-enheter:

![Sidan Ange villkor för medlemskap](/intune/media/Intune_Planning_Groups_Device_Criteria_small.png)

Gå igenom informationen och skapa BYOD-gruppen genom att välja **Slutför**.

![Dialogrutan Skapa grupp](/intune/media/Intune_Planning_Groups_Device_Summary_small.png)

Fortsätta att skapa enhetsgrupper tills du har en enhetshierarki liknande användargruppshierarkin. När du är klar bör gruppnoden i Intune-konsolen se ut ungefär så här:

![Vy av grupphierarkin i Intune](/intune/media/Intune_Groups_Hierarchy_Final_Small.png)

## Grupphierarkier och namngivningskonventioner
För att underlätta principhanteringen rekommenderar vi att du namnger varje princip efter dess syfte, plattform och omfång. Den här namngivningsstandarden bör följa den gruppstruktur som du skapade inför tillämpningen av dina principer.

För en Android-princip som tillämpas på alla företagsägda, mobila Android-enheter på regionsnivån USA kan du till exempel döpa principen till **CO_US_Mob_Android_General**.

![Skapa princip för Android](/intune/media/Intune_planning_policy_android_small.png)

Genom att namnge principerna på det här sättet kan du snabbt identifiera principer och deras avsedda användning och omfång i konsolens principnod, som du ser här:

![Principlista i Intune](/intune/media/Intune_planning_policy_view_small.png)

## Nästa steg
[Skapa grupper](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


