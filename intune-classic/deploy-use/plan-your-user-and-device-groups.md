---
title: Planera dina användar- och enhetsgrupper
description: Planera grupper för att uppfylla organisationens behov.
keywords: ''
author: sanchusa
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lpatha
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 679399f306f3837a010cc01799c7567c1e5b5b39
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025322"
---
# <a name="plan-your-user-and-device-groups"></a>Planera dina användar- och enhetsgrupper

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Grupper i Intune ger stor flexibilitet när du hanterar dina enheter och användare. Du kan skapa grupper som passar organisationens behov enligt:

- geografisk plats
- avdelning
- maskinvaruegenskaper
- operativsystem
- om enheten är användarägd eller företagsägd


## <a name="how-intune-groups-work"></a>Så här fungerar Intune-grupper


Det här är standardvyn för noden **Grupper** i Intune-administrationskonsolen:

![Skärmbild av standardvyn för noden Grupper i Intune-konsolen](../media/Intune_Planning_Groups_Default_small.png)

Principer distribueras till grupper. Grupphierarkin är därför en av de viktigaste designaspekterna. Det är viktigt att känna till att du inte kan ändra en grupps överordnade grupp efter att gruppen har skapats. Hur du utformar dina grupper är av yttersta vikt från det ögonblick då du börjar använda Intune-tjänsten. Här beskrivs några av de rekommenderade metoderna för att designa en grupphierarki baserat på din organisations behov.

## <a name="group-membership-rules"></a>Regler för gruppmedlemskap

- En grupp kan innehålla användare eller enheter, men inte båda.

    * **Enhetsgrupper**. Detta innefattar datorer och mobila enheter. Innan du kan lägga till en dator till en grupp måste den vara registrerad. Innan du kan lägga till en mobilenhet till en grupp måste din miljö konfigureras för mobila enheter och enheterna måste vara registrerade eller identifierade i Exchange ActiveSync.

    * **Användargrupper**. En grupp kan ha användare från säkerhetsgrupper. Säkerhetsgrupper synkroniserar med din instans av Active Directory. Om du inte använder synkronisering med Active Directory kan du skapa dessa grupper manuellt .

- En enhet eller en användare kan tillhöra mer än en grupp.

- En grupp kan innehålla och undanta medlemmar baserat på följande medlemskapsregler:

    * **Villkor för medlemskap**. Detta är dynamiska regler som används i Intune för att ta med eller undanta medlemmar. Dessa villkor använder säkerhetsgrupper och annan information som är synkroniserad med din lokala instans av Active Directory. När säkerhetsgruppen eller data ändras, ändras gruppmedlemskapet när du synkroniserar med Active Directory.

    * **Direkt medlemskap**. Det här är statiska regler som uttryckligen lägga till eller utelämna medlemmar. Medlemskapslistan är statisk.

-   Active Directory Domain Services (AD DS) krävs inte när du skapar användargrupper eller enhetsgrupper som innefattar användare eller datorer. Men för att kunna ta med mobila enheter i enhetsgrupper måste miljön vara konfigurerad för att stödja mobila enheter.

    Dessutom måste enheterna identifieras och läggas till i Intune.

## <a name="group-relationship-rules"></a>Regler för grupprelationer

- Varje grupp du skapar måste ha en överordnad grupp. Du kan inte ändra en grupps överordnade grupp efter att gruppen har skapats.

- När du lägger till användare eller enheter i en underordnad grupp:

    * Den underordnade gruppen är alltid en del av den överordnade gruppen.

    * Nya medlemmar som du lägger till en underordnad gruppen läggs automatiskt till gruppens överordnad grupp.

    * Du kan inte lägga till en medlem i en underordnad grupp när medlemmen är inte del av den överordnade gruppen.

- Medlemskap i en överordnad grupp definierar tillgängliga medlemskap för den underordnade gruppen.

- När du tar bort en överordnad grupp tas alla underordnade grupper bort.

- Du kan distribuera innehåll och principer till en överordnad grupp, men utesluta distribution till underordnade grupper.

- Du kan lägga till en specifik användare eller enhet i en underordnad grupp, om användaren eller enheten inte redan är medlem i den överordnade gruppen. Om du gör det läggs den nya medlemmen i den underordnade gruppen till i den överordnade gruppen.

    Däremot kan du inte lägga till en medlem i en underordnad grupp om medlemmen är undantagen från den överordnade gruppen.

- Gruppmedlemskap är rekursivt. Exempel:

    * **Patrik** är endast medlem i en enda grupp: säkerhetsgruppen **Användare av bärbara datorer** .

    * Gruppen **Användare av bärbara datorer** är medlem i säkerhetsgruppen **Godkända användare** .

    * Du skapar en grupp i Intune som använder en dynamisk medlemskapsfråga som innehåller medlemmarna i gruppen **Godkända användare**. Resultatet är att din Intune-användargrupp innehåller **Erik**.

> [!TIP]
> När du skapar grupper bör du tänka på hur du ska tillämpa de olika principerna. Du kan t.ex. ha principer som är specifika för ett operativsystem för en enhet och principer som är specifika för olika roller eller organisationsenheter som du redan har definierat i Active Directory-tjänsten. En del administratörer väljer att skapa enhetsgrupper som är specifika för iOS, Android och Windows. Det här är något som görs utöver att skapa användargrupper för varje roll i organisationen.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your organization. Then, you create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful when you name your policies, so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy, you'll want to communicate it to your users. After you create the more general groups and policies, pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## <a name="built-in-groups"></a>Inbyggda grupper
I Intune finns nio inbyggda grupper som du inte kan redigera eller ta bort: <!--maybe a screen shot would be best?-->

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
> Låt ditt motto vara: *enkelhet*. Om din organisation inte har särskilda behov (som de som beskrivs i följande avsnitt) bör du hålla allt så enkelt som möjligt och använda standardgruppstrukturen och standardgrupprinciperna. Det gör att tjänsten blir lättare att hantera på lång sikt. Underhållet blir enklare när du kan hantera användarna på ett enhetligt sätt. Och du får du färre principer att underhålla med liten differentiering per grupp.


### <a name="all-users-and-devices-in-your-organization"></a>Alla användare och enheter i din organisation
Definiera en överordnad grupp för alla användare och enheter i din organisation. Du har troligtvis principer som gäller för alla. Du kan använda standardgrupperna **Alla användare** och **Alla enheter** i Intune. Undergrupper som ordnar enheter efter egenskaper, till exempel en grupp för BYOD-enheter (Bring Your Own Device) och en för företagsägda enheter (CO, Corporate Owned), kan vara underordnade grupper till de överordnade grupperna **Alla användare** och **Alla enheter**.

## <a name="customize-groups-for-your-organization"></a>Anpassa grupper för organisationen

### <a name="byod-and-corporate-owned-devices"></a>BYOD-enheter och företagsägda enheter
Om organisationen tillåter att anställda använder egna enheter på arbetet (BYOD), tillhandahåller företagsägda enheter eller använder både och, rekommenderar vi att du tillämpar separata principer för dessa enhetskategorier.

När det gäller BYOD-enheter eller en kombination bör du planera principer som inte överträder lokala sekretessbestämmelser. Skapa en överordnad grupp för alla användare som ska ta med sina egna enheter (BYOD). Du kan använda den här gruppen för att tillämpa principer som gäller för alla användare i den här kategorin.

![Skapa en överordnad BYOD-grupp](../media/Intune_Planning_Groups_BYOD_small.png)

På liknande sätt kan du skapa en grupp för de som använder företagsägda enheter i organisationen:

![Användargrupper för BYOD-enheter och företagsägda enheter på samma nivå](../media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### <a name="groups-for-geographic-regions"></a>Grupper för geografiska områden
Om organisationen behöver principer för vissa regioner kan du skapa grupper baserat på geografiskt område. Du kan basera dem på regionala grupper som du kanske redan har skapat i din instans av Active Directory och synkronisera dem med Azure Active Directory-tjänsten. Du kan också skapa regionala grupper direkt i Azure Active Directory.

Följande skärmbilder visar hur du skapar Intune-grupper baserat på de grupper som du synkroniserar med din lokala instans av Active Directory. Dessa exempel förutsätter att du har en Active Directory-säkerhetsgrupp som heter **US Users Group** (grupp för USA-användare).

Börja med att ange allmän information.

![Skärmbild av området Redigera grupp](../media/Intune_Planning_Groups_AD_General_small.png)

Under **Kriterier för medlemskap** väljer du **US Users Group** (grupp för USA-användare), som är synkroniserat med Active Directory, som den säkerhetsgrupp som ska användas under medlemskapsregler.

![Skärmbild av dialogrutan Redigera grupp](../media/Intune_Planning_Groups_AD_Criteria_small.png)

Granska posterna och välj sedan **Slutför** för att skapa gruppen.

![Skärmbild av dialogrutan Redigera grupp](../media/Intune_Planning_Groups_AD_Summary_small.png)

I vårt exempel har vi också skapat en grupp som heter **MEA** för Mellanöstern och Asien.

> [!NOTE]
> Om gruppmedlemskapet inte har fyllts i baserat på medlemskap i säkerhetsgruppen kontrollerar du att gruppmedlemmarna har tilldelats Intune-licenser.

### <a name="groups-for-specific-hardware"></a>Grupper för särskild maskinvara
Om organisationen kräver principer som tillämpas för specifika maskinvarutyper kan du skapa grupper utifrån det här kravet. Du kan basera principerna på regionala grupper som du redan har skapat i din lokala instans av Active Directory och sedan synkronisera dem med Azure Active Directory. Du kan också skapa grupper direkt i Azure Active Directory. I det här exemplet använder vi **US Users Group** (grupp för USA-användare) som överordnad grupp till gruppen **Laptop Users** (Användare av bärbara datorer).

![Dialogrutan Välj säkerhetsgrupp](../media/Intune_Planning_Groups_Laptop_small.png)

Nu bör hierarkin för din grupp se ut ungefär som på nästa skärmbild. Som du ser finns det nu medlemmar i Intune-gruppen **Laptop Users** (användare av bärbara datorer). Alla principer som tillämpas på den här gruppen gäller för användare av bärbara BYOD-datorer från regionen USA.

![Visning av gruppen Användare av bärbara datorer](../media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### <a name="groups-for-specific-operating-systems"></a>Grupper för specifika operativsystem
Om din organisation kräver principer för specifika operativsystem, till exempel Android, iOS eller Windows, kan du skapa grupper utifrån det här kravet. Som i tidigare exempel kan du basera dem på grupper för specifika operativsystem som du redan har skapat i din lokala instans av Active Directory och synkronisera dem med Azure Active Directory. Du kan också skapa dem direkt i din instans av Azure Active Directory.

Genom att använda samma metod som från tidigare exempel kan du skapa grupper baserat på användare <!--devices?--> som använder specifika operativsystem.

> [!NOTE]
> Om du har användare som använder flera mobila plattformar eller operativsystem och du inte har en automatiserad metod för att kategorisera användare som Android-användare, iOS-användare eller Windows-användare, bör du överväga att tillämpa principer på enhetsnivå. Det ger dig bättre flexibilitet vid tillämpning av operativsystemspecifika principer.
>
> Du kan inte etablera grupper dynamiskt baserat på enhetens operativsystem. I stället gör du detta med hjälp av Active Directory-säkerhetsgrupper eller Azure Active Directory-säkerhetsgrupper.

![Gruppen Användare av bärbara datorer](../media/Intune_Planning_Groups_OS_Hierachy_small.png)

När alla användargrupper har fyllts i baserat på organisationens krav bör grupphierarkin se ut ungefär så här:

![Grupphierarkivy](../media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

Du kan använda den här hierarkin för att tillämpa organisationens principer.

### <a name="device-groups"></a>Enhetsgrupper
Du kan också skapa liknande grupper för enheter som du ser nedan för BYOD-scenariot, och börja med en bred grupp som innehåller alla personalägda enheter.

![Dialogrutan Skapa grupp](../media/Intune_Planning_Groups_Device_General_small.png)

Var noga med att välja **Alla enheter (datorer och mobila enheter)** så att gruppen omfattar alla BYOD-enheter:

![Sidan Ange villkor för medlemskap](../media/Intune_Planning_Groups_Device_Criteria_small.png)

Granska posterna och välj sedan **Slutför** för att skapa BYOD-gruppen.

![Dialogrutan Skapa grupp](../media/Intune_Planning_Groups_Device_Summary_small.png)

Fortsätt att skapa enhetsgrupper tills du har en enhetshierarki som liknar användargruppshierarkin. Gruppnoden i Intune-konsolen kommer att se ut ungefär så här:

![Vy av grupphierarkin i Intune](../media/Intune_Groups_Hierarchy_Final_Small.png)

## <a name="group-hierarchies-and-naming-conventions"></a>Grupphierarkier och namngivningskonventioner
För att underlätta principhanteringen rekommenderar vi att du namnger varje princip efter dess syfte, plattform och omfång. Använd en namngivningsstandard som följer den gruppstruktur som du skapade inför tillämpningen av dina principer.

För en Android-princip som tillämpas på alla företagsägda, mobila Android-enheter på regionsnivån USA kan du till exempel döpa principen till **CO_US_Mob_Android_General**.

![Skapa princip för Android](../media/Intune_planning_policy_android_small.png)

När du namnger principerna på det här sättet kan du snabbt identifiera principer och deras avsedda användning och omfång i noden **Principer**, som du ser här:

![Principlista i Intune](../media/Intune_planning_policy_view_small.png)

## <a name="next-steps"></a>Nästa steg
[Skapa grupper](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)
