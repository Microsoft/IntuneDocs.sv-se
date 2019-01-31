---
title: Policyer för efterlevnad för enheter i Microsoft Intune – Azure | Microsoft Docs
description: Krav för att använda policyer för efterlevnad för enheter, översikt över tillstånd och allvarlighetsgrader, använda statusen InGracePeriod, arbeta med villkorlig åtkomst, hantera enheter utan en tilldelad policy och skillnader i efterlevnad i Azure Portal och den klassiska portalen i Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 806df8077045a4ad81cb7e221bd053059461a2fd
ms.sourcegitcommit: 6f2f2fa70f4e47fa5ad2f3c536ba7116e1bd1d05
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/29/2019
ms.locfileid: "55199412"
---
# <a name="get-started-with-device-compliance-policies-in-intune"></a>Komma igång med policyer för efterlevnad för enheter i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Många MDM-lösningar för hantering av mobilenheter skyddar organisationens data genom att kräva att användare och enheter uppfyller vissa krav. I Intune kan kallas den här funktionen för ”efterlevnadsprinciper”. Efterlevnadsprinciperna definierar de regler och inställningar som användare och enheter måste följa för att vara kompatibla. I kombination med villkorlig åtkomst kan administratörer blockera användare och enheter som inte följer reglerna. En Intune-administratör kan till exempel kräva att:

- Slutanvändarna ska använda ett lösenord för att få åtkomst till organisationens data på mobila enheter

- Att enheten inte är jailbrokad eller rotad

- En högsta eller lägsta operativsystemversion finns på enheten

- Att enheten ligger på eller under en hotnivå

Du kan också använda enhetsefterlevnadsprinciper till att övervaka enheternas efterlevnadsstatus.

> [!IMPORTANT]
> Intune följer enhetens incheckningsschema för alla efterlevnadsutvärderingar på enheten. [Mer information om enhetens incheckningsschema](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="prerequisites"></a>Krav

Om du vill använda enhetsefterlevnadsprinciper måste du:

- Använd följande prenumerationer:

  - Intune
  - Azure Active Directory (AD) Premium

- Använd en plattform som stöds:

  - Android
  - iOS
  - macOS (förhandsversion)
  - Windows 8,1
  - Windows Phone 8.1
  - Windows 10

- Registrera enheter i Intune för att se efterlevnadsstatusen

- Registrera enheter för en användare, eller registrera utan någon primär användare. Enheter som har registrerats för flera användare stöds inte.

## <a name="how-device-compliance-policies-work-with-azure-ad"></a>Så här fungerar enhetsefterlevnadsprinciper med Azure AD

När en enhet registreras i Intune startas även registreringen i Azure AD, vilket uppdaterar enhetens egenskaper i Azure AD. Enhetens efterlevnadsstatus är viktig information. Enhetens efterlevnadsstatus används av villkorliga åtkomstprinciper för att blockera eller tillåta åtkomst till e-post eller andra företagsresurser.

Läs mer i [registreringsprocessen i Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

## <a name="refresh-cycle-times"></a>Uppdatera cykeltider

Vid efterlevnadskontrollen använder Intune samma uppdateringscykel som konfigurationsprofilerna. I allmänhet görs detta:

- iOS: var 6:e timme
- macOS: var 6:e timme
- Android: var 8:e timme
- Windows 10-datorer som har registrerats som enheter: var 8:e timme
- Windows Phone: var 8:e timme
- Windows 8.1: var 8:e timme

En efterlevnadskontroll utförs oftare omedelbart efter att en enhet har registrerats.

### <a name="assign-an-ingraceperiod-status"></a>Tilldela en InGracePeriod-status

Statusen InGracePeriod för en tilldelad policy för efterlevnad är ett värde. Värdet fastställs genom en kombinationen av en enhets respitperiod och en enhets faktiska status för den tilldelade policyn för efterlevnad.

Specifikt innebär det att om en enhet har statusen NonCompliant för en tilldelad efterlevnadsprincip och:

- enheten inte har någon tilldelad respitperiod, så är det tilldelade värdet för policyn för efterlevnad är NonCompliant
- enheten har en respitperiod som har löpt ut, så är det tilldelade värdet för policyn för efterlevnad är NonCompliant
- enheten har en respitperiod som ligger i framtiden, så är det tilldelade värdet för policyn för efterlevnad är InGracePeriod

Följande tabell innehåller en sammanfattning av de här punkterna:

|Faktisk efterlevnadsstatus|Värde för tilldelad respitperiod|Effektiv efterlevnadsstatus|
|---------|---------|---------|
|NonCompliant |Ingen tilldelad respitperiod |NonCompliant |
|NonCompliant |Gårdagens datum|NonCompliant|
|NonCompliant |Morgondagens datum|InGracePeriod|

Mer information om hur du övervakar enhetsefterlevnadsprinciper finns i [Övervaka efterlevnadsprinciper för Intune-enhet](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Tilldela en resulterande status för policy för efterlevnad

Om en enhet har flera policyer för efterlevnad och enheten har olika efterlevnadsstatus för två eller fler av de tilldelade policyerna för efterlevnad tilldelas en enda resulterande efterlevnadsstatus. Den här tilldelningen baseras på en konceptuell allvarlighetsgrad som tilldelas till varje efterlevnadsstatus. Varje efterlevnadsstatus har följande allvarlighetsgrad:

|Status  |Allvarlighetsgrad  |
|---------|---------|
|Okänt     |1|
|NotApplicable     |2|
|Kompatibel|3|
|InGracePeriod|4|
|NonCompliant|5|
|Fel|6|

När en enhet har flera policyer för efterlevnad tilldelas den högsta allvarlighetsgraden av alla policyer till den enheten.

Anta exempelvis att en enhet har tre tilldelade efterlevnadsprinciper: en med statusen Okänt (allvarlighetsgrad = 1), en med statusen Kompatibel (allvarlighetsgrad = 3) och en med statusen InGracePeriod (allvarlighetsgrad = 4). Statusen InGracePeriod har högst allvarlighetsgrad så alla tre policyer har efterlevnadsstatus InGracePeriod.

## <a name="ways-to-use-device-compliance-policies"></a>Hantera efterlevnadsprinciper för enheter

#### <a name="with-conditional-access"></a>Med villkorlig åtkomst
Du kan ge enheter som följer principreglerna åtkomst till e-post och andra företagsresurser. Om enheterna inte följer principreglerna får de inte åtkomst till företagsresurser. Det är det som kallas villkorlig åtkomst.

#### <a name="without-conditional-access"></a>Utan villkorlig åtkomst
Du kan även använda policyer för enhetsefterlevnad utan villkorlig åtkomst. När du använder efterlevnadsprinciper separat utvärderas målenheterna varefter deras efterlevnadsstatus rapporteras. Du kan t.ex. få en rapport om hur många enheter som inte är krypterade, eller vilka enheter som är jailbrokade eller rotade. När du använder efterlevnadsprinciper utan villkorlig åtkomst, tillämpas inga åtkomstbegränsningar på organisationens resurser.

## <a name="ways-to-deploy-device-compliance-policies"></a>Sätt att distribuera policyer för efterlevnad för enheter
Du kan distribuera policyer för efterlevnad till användare i användargrupper eller till enheter i enhetsgrupper. När en efterlevnadsprincip distribueras till en användare så kontrolleras om alla användarens enheter uppfyller efterlevnadskraven. På Windows 10 version 1803 och senare enheter, rekommenderar vi för att distribuera till enhetsgrupper *om* den primära användaren inte registrerat enheten. Användning av enhetsgrupper i det här scenariot hjälper till med kompabilitetsrapportering.

En uppsättning inbyggda inställningar för efterlevnadsprinciper (**Intune** > **Enhetsefterlevnad**) utvärderas på alla Intune-registrerade enheter. Dessa omfattar:

- **Markera enheter utan någon tilldelad policy för efterlevnad som**: Den här egenskapen har två värden:

  - **Följer standard**: säkerhetsfunktion av
  - **Följer inte standard** (standard): säkerhetsfunktion på

  Om en enhet inte har en policy för efterlevnad är den inte kompatibel. Som standard markeras enheter som **följer ej standard**. Om du använder villkorlig åtkomst rekommenderar vi att du ändrar inställningen till **Inte kompatibel**. Om en användare inte är kompatibel eftersom en princip inte har tilldelats, visar företagsportalen `No compliance policies have been assigned`.

- **Förbättrad identifiering av uppbrytning**: När den här inställningen är aktiverad kommer iOS-enheter checka in till Intune oftare. När du aktiverar den här egenskapen används enhetens platstjänster, vilket påverkar batterianvändningen. Användarnas platsdata lagras inte av Intune.

  När du aktiverar den här inställningen kräver den följande av enheter:
  - Aktivera platstjänster på operativsystemsnivån
  - Tillåter att företagsportalen använder platstjänsterna
  - Utvärdera och rapportera status för upplåsning till Intune minst en gång var 72:a timme. Annars markeras enheten som ej kompatibel. Utvärderingen utlöses antingen genom att företagsportalappen öppnas eller att enheten fysiskt flyttas 500 meter eller längre. Om enheten inte flyttas 500 meter inom 72 timmar, måste användaren öppna företagsportalappen för utökad utvärdering av upplåsningen.

- **Giltighetsperiod för efterlevnadsstatus (dagar)**: Ange inom vilken tidsperiod enheterna ska rapportera status för alla mottagna efterlevnadsprinciper. Enheter som inte returnerar status inom den här tidsperioden behandlas som inkompatibla. Standardvärdet är 30 dagar.

Alla enheter har en **inbyggd enhetsefterlevnadsprincip** (Azure-portalen > Enhetsefterlevnad > Principefterlevnad). Använd den här inbyggda principen för att övervaka de här inställningarna.

Information om hur lång tid det tar för mobila enheter att hämta en princip efter att den har distribuerats finns i [Troubleshooting device profiles](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned) (Felsöka enhetsprofiler).

Efterlevnadsrapporter är ett bra sätt att kontrollera status för enheter. Läs [Övervaka policyer för efterlevnad](compliance-policy-monitor.md) för mer vägledning.

### <a name="actions-for-noncompliance"></a>Åtgärder för inkompatibilitet
Du kan konfigurera en tidsordnad sekvens med åtgärder som tillämpas på enheter som inte uppfyller villkoren för policyer för efterlevnad. De här åtgärderna för inkompatibilitet kan automatiseras. Detta beskrivs i [Automate actions for noncompliance](actions-for-noncompliance.md) (Automatisera åtgärder för inkompatibilitet).

## <a name="azure-classic-portal-vs-azure-portal"></a>Den klassiska Azure-portalen jämfört med Azure-portalen

De största skillnaderna när du använder policyer för efterlevnad i Azure Portal:

- Policyer för efterlevnad skapas separat för varje plattform som stöds i Azure Portal
- I den klassiska Azure-portalen är en policy för efterlevnad gemensam för alla plattformar som stöds

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

## <a name="device-compliance-policies-in-the-classic-portal-and-azure-portal"></a>Policyer för efterlevnad för enheter i den klassiska portalen och Azure Portal

Policyer för efterlevnad för enheter som skapas i den [klassiska portalen](https://manage.microsoft.com) visas inte i [Azure Portal](https://portal.azure.com). De gäller dock fortfarande användare och kan hanteras via den klassiska portalen.

Om du vill använda de funktioner i Azure Portal som är relaterade till policyer för enhetsefterlevnad måste du skapa nya policyer för enhetsefterlevnad i Azure Portal. Om du tilldelar en användare en ny policy för enhetsefterlevnad i Azure Portal och denna användare även har tilldelats en policy för enhetsefterlevnad från den klassiska portalen så har policyerna för enhetsefterlevnad från Azure Portal företräde framför dem från den klassiska portalen.

## <a name="next-steps"></a>Nästa steg

- Skapa en princip för enhetsefterlevnad för följande plattformar:

  - [Android](compliance-policy-create-android.md)
  - [Android-arbetsprofil](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Information om principentiteter för Intune-informationslagret finns i [Referens för principentiteter](reports-ref-policy.md).
