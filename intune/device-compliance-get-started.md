---
title: Policyer för efterlevnad för enheter i Microsoft Intune – Azure | Microsoft Docs
description: Krav för att använda policyer för efterlevnad för enheter, översikt över tillstånd och allvarlighetsgrader, använda statusen InGracePeriod, arbeta med villkorlig åtkomst, hantera enheter utan en tilldelad policy och skillnader i efterlevnad i Azure Portal och den klassiska portalen i Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 151a445bf7c5c17f8ff1b5ee403df8744f2d8ba6
ms.sourcegitcommit: ab08dd841f16ae11f958c43b6262a9f6a0cabdd4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49102063"
---
# <a name="get-started-with-device-compliance-policies-in-intune"></a>Komma igång med policyer för efterlevnad för enheter i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ett efterlevnadskrav är i princip samma sak som en regel, t. ex. att kräva en PIN-kod för en enhet eller att kräva kryptering. Policyer för efterlevnad definierar de regler och inställningar som en enhet måste följa för att anses vara kompatibel. Bland dessa regler finns:

- Använd lösenord för att få åtkomst till enheter

- Kryptering

- Om enheten är jailbrokad eller rotad

- Lägsta tillåtna version av operativsystemet

- Högsta tillåtna version av operativsystemet

- Kräv att enheten måste ligga på eller under nivån för skydd mot mobilhot

Du kan också använda principer för enhetsefterlevnad för att övervaka enheters efterlevnadsstatus.

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
Följande krävs för att använda policyer för efterlevnad för enheter:

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

- Enheter måste registreras i Intune för att kunna rapportera efterlevnadsstatus

- Enheter som registrerats till en användare eller enheter utan primär användare stöds. Flera användarkontexter stöds inte.

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>Så här fungerar efterlevnadsprinciper för Intune med Azure AD

När en enhet registreras i Intune startas även registreringen i Azure AD, vilket uppdaterar enhetens egenskaper i Azure AD. Enhetens efterlevnadsstatus är viktig information. Enhetens efterlevnadsstatus används av villkorliga åtkomstprinciper för att blockera eller tillåta åtkomst till e-post eller andra företagsresurser.

Läs mer i [registreringsprocessen i Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

### <a name="assign-a-resulting-device-configuration-profile-status"></a>Tilldela en resulterande profilstatus för enhetskonfiguration

Om en enhet har flera konfigurationsprofiler och enheten har olika efterlevnadsstatus för två eller fler av de tilldelade konfigurationsprofilerna tilldelas en enda resulterande efterlevnadsstatus. Den här tilldelningen baseras på en konceptuell allvarlighetsgrad som tilldelas till varje efterlevnadsstatus. Varje efterlevnadsstatus har följande allvarlighetsgrad:

|Status  |Allvarlighetsgrad  |
|---------|---------|
|Väntar     |1|
|Lyckades     |2|
|Misslyckades     |3|
|Fel     |4|

När en enhet har flera konfigurationsprofiler tilldelas den högsta allvarlighetsgraden till alla profiler som är tilldelade till den enheten.

Anta exempelvis att en enhet har tre tilldelade profiler: en med statusen Väntar (allvarlighetsgrad = 1), en med statusen Lyckades (allvarlighetsgrad = 2) och en med statusen Fel (allvarlighetsgrad = 4). Statusen Fel har högst allvarlighetsgrad så alla tre profilerna har efterlevnadsstatusen Fel.

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
Du kan även använda policyer för enhetsefterlevnad utan villkorlig åtkomst. När du använder efterlevnadsprinciper separat utvärderas målenheterna varefter deras efterlevnadsstatus rapporteras. Du kan t.ex. få en rapport om hur många enheter som inte är krypterade eller vilka enheter som är upplåsta (jailbreakade) eller rotade. När du använder policyer för efterlevnad utan villkorlig åtkomst tillämpas inga åtkomstbegränsningar på företagsresurser.

## <a name="ways-to-deploy-device-compliance-policies"></a>Sätt att distribuera policyer för efterlevnad för enheter
Du kan distribuera policyer för efterlevnad till användare i användargrupper eller till enheter i enhetsgrupper. När en efterlevnadsprincip distribueras till en användare så kontrolleras om alla användarens enheter uppfyller efterlevnadskraven.

**Standardinställningar för policyer för efterlevnad** (Azure Portal > Enhetsefterlevnad) innefattar:

- **Markera enheter som saknar en policy för efterlevnad som**: Den här egenskapen har två värden:

  - **Följer standard**: säkerhetsfunktion av
  - **Följer inte standard** (standard): säkerhetsfunktion på

  Om en enhet inte har en policy för efterlevnad är den inte kompatibel. Som standard markeras enheter som **Kompatibel**. Om du använder villkorlig åtkomst rekommenderar vi att du ändrar inställningen till **Inte kompatibel**. Om en användare inte följer standard eftersom en princip inte är tilldelad visar företagsportalen `No compliance policies have been assigned`.

- **Förbättrad identifiering av uppbrytning**: När den här inställningen är aktiverad gör den så att iOS-enheter checkar in med Intune oftare. När du aktiverar den här egenskapen används enhetens platstjänster, vilket påverkar batterianvändningen. Användarnas platsdata lagras inte av Intune.

  När du aktiverar den här inställningen kräver den följande av enheter:
  - Aktivera platstjänster på operativsystemsnivån
  - Tillåter att företagsportalen använder platstjänsterna
  - Utvärdera och rapportera status för upplåsning till Intune minst en gång var 72:a timme. Annars markeras enheten som ej kompatibel. Utvärderingen utlöses antingen genom att företagsportalappen öppnas eller att enheten fysiskt flyttas 500 meter eller längre.

- **Giltighetstid för efterlevnadsstatus (dagar)**: Ange inom vilken tidsperiod enheterna rapporterar status för alla mottagna policyer för efterlevnad. Enheter som inte returnerar status inom den här tidsperioden behandlas som inkompatibla. Standardvärdet är 30 dagar.

Alla enheter har en **standardpolicy för enhetsefterlevnad** (Azure Portal > Enhetsefterlevnad > Policy för efterlevnad). Använd den här standardprincipen för att övervaka de här inställningarna.

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
