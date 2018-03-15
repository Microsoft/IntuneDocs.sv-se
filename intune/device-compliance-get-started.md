---
title: Microsoft Intunes enhetsefterlevnadsprinciper
titleSuffix: 
description: "Läs mer om enhetsefterlevnad i Microsoft Intune"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9e3a7bdf3ddf6ad77a82ac6dc7075d696fbe6497
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2018
---
# <a name="get-started-with-microsoft-intune-device-compliance-policies"></a>Komma igång med enhetsefterlevnadsprinciper för Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intunes efterlevnadsprinciper definierar de regler och inställningar som en enhet måste följa för att anses vara kompatibel med Intune.

Reglerna omfattar följande:

- Använd lösenord för att få åtkomst till enheter

- Kryptering

- Om enheten är jailbrokad eller rotad

- Lägsta tillåtna version av operativsystemet

- Högsta tillåtna version av operativsystemet

- Enheten måste ligga på eller under nivån för skydd mot mobilhot

Du kan också använda principer för enhetsefterlevnad för att övervaka enheters efterlevnadsstatus.

## <a name="device-compliance-requirements"></a>Krav på efterlevnad för enhet

Efterlevnadskrav är i stort sett regler som kräver en enhets PIN-kod eller kryptering, vilket du kan ange att det krävs eller inte krävs för en efterlevnadsprincip.

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

##  <a name="pre-requisites"></a>Förutsättningar

Du måste ha följande prenumerationer för att använda efterlevnadsprinciper för enheter med Intune:

- Intune EMS

- Azure AD Premium

###  <a name="supported-platforms"></a>Plattformar som stöds:

-   Android

-   iOS

-   macOS (förhandsversion)

-   Windows 8,1

-   Windows Phone 8.1

-   Windows 10

> [!IMPORTANT]
> Enheter måste registreras i Intune för att kunna rapportera efterlevnadsstatus.

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>Så här fungerar efterlevnadsprinciper för Intune med Azure AD

När en enhet registreras i Intune sker även registreringen i Azure AD, vilket uppdaterar enhetens egenskaper med mer information i Azure AD. En viktig del av informationen är enhetens efterlevnadsstatus, vilket används av villkorliga åtkomstprinciper för att blockera eller tillåta åtkomst till e-post eller andra företagsresurser.

- Läs mer om [registreringsprocessen i Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction).

### <a name="assigning-a-resulting-device-configuration-profile-status"></a>Tilldela en resulterande profilstatus för enhetskonfiguration

Om en enhet har flera tilldelade konfigurationsprofiler och enheten har olika efterlevnadsstatus för två eller fler av de tilldelade konfigurationsprofilerna, måste en enda resulterande efterlevnadsstatus tilldelas. Den här tilldelningen baseras på en konceptuell allvarlighetsgrad som tilldelas till varje efterlevnadsstatus. Varje efterlevnadsstatus har följande allvarlighetsgrad:


|Status  |Allvarlighetsgrad  |
|---------|---------|
|Väntar     |1|
|Lyckades     |2|
|Misslyckades     |3|
|Fel     |4|

En resulterande status med två eller flera konfigurationsprofiler tilldelas sedan genom att välja den högsta allvarlighetsgraden för alla profiler som är tilldelade till en enhet.

Anta exempelvis att en enhet har tre tilldelade profiler: en med statusen Väntar (allvarlighetsgrad = 1), en med statusen Lyckades (allvarlighetsgrad = 2) och en med statusen Fel (allvarlighetsgrad = 4). Statusen Fel har högst allvarlighetsgrad, så den tilldelas som resulterande efterlevnadsstatus för alla tre profilerna.

### <a name="assigning-an-ingraceperiod-status-for-an-assigned-compliance-policy"></a>Tilldela statusen InGracePeriod för en tilldelad efterlevnadsprincip

Statusen InGracePeriod för en efterlevnadsprincip är ett värde som fastställs genom att överväga kombinationen av en enhets respitperiod och en enhets faktiska status för den tilldelade efterlevnadsprincipen. 

Specifikt innebär det att om en enhet har statusen NonCompliant för en tilldelad efterlevnadsprincip och:

- enheten inte har någon tilldelad respitperiod, så är det tilldelade värdet för efterlevnadsprincipen NonCompliant.
- enheten har en respitperiod som har löpt ut, så är det tilldelade värdet för efterlevnadsprincipen NonCompliant.
- enheten har en respitperiod som ligger i framtiden, så är det tilldelade värdet för efterlevnadsprincipen InGracePeriod.

Följande tabell innehåller en sammanfattning av föregående punkter:


|Faktisk efterlevnadsstatus|Värde för tilldelad respitperiod|Effektiv efterlevnadsstatus|
|---------|---------|---------|
|NonCompliant |Ingen tilldelad respitperiod |NonCompliant |
|NonCompliant |Gårdagens datum|NonCompliant|
|NonCompliant |Morgondagens datum|InGracePeriod|

Mer information om hur du övervakar enhetsefterlevnadsprinciper finns i [Övervaka efterlevnadsprinciper för Intune-enhet](compliance-policy-monitor.md).

### <a name="assigning-a-resulting-compliance-policy-status"></a>Tilldela en resulterande status för efterlevnadsprincip

Om en enhet har flera tilldelade efterlevnadsprinciper och enheten har olika efterlevnadsstatus för två eller fler av de tilldelade efterlevnadsprinciperna, måste en enda resulterande efterlevnadsstatus tilldelas. Den här tilldelningen baseras på en konceptuell allvarlighetsgrad som tilldelas till varje efterlevnadsstatus. Varje efterlevnadsstatus har följande allvarlighetsgrad: 

|Status  |Allvarlighetsgrad  |
|---------|---------|
|Okänt     |1|
|NotApplicable     |2|
|Kompatibel|3|
|InGracePeriod|4|
|NonCompliant|5|
|Fel|6|

En resulterande status med två eller flera efterlevnadsprinciper fastställs sedan genom att välja den högsta allvarlighetsgraden för alla principer som är tilldelade till en enhet.
 
Anta exempelvis att en enhet har tre tilldelade efterlevnadsprinciper: en med statusen Okänt (allvarlighetsgrad = 1), en med statusen Kompatibel (allvarlighetsgrad = 3) och en med statusen InGracePeriod (allvarlighetsgrad = 4). Statusen InGracePeriod har högst allvarlighetsgrad, så den tilldelas som resulterande efterlevnadsstatus för alla tre profilerna.  

##  <a name="ways-to-use-device-compliance-policies"></a>Hantera efterlevnadsprinciper för enheter

### <a name="with-conditional-access"></a>Med villkorlig åtkomst
Du kan använda efterlevnadsprinciper med villkorlig åtkomst om du endast vill tillåta enheter som uppfyller en eller flera efterlevnadsprincipens regler för åtkomst till e-post och andra företagsresurser.

### <a name="without-conditional-access"></a>Utan villkorlig åtkomst
Du kan också använda principer för enhetsefterlevnad oberoende av villkorlig åtkomst. När du använder efterlevnadsprinciper separat utvärderas målenheterna varefter deras efterlevnadsstatus rapporteras. Du kan t.ex. få en rapport om hur många enheter som inte är krypterade eller vilka enheter som är upplåsta (jailbreakade) eller rotade. Men när du använder efterlevnadsprinciper separat tillämpas inga åtkomstbegränsningar på företagsresurser.

Du distribuerar efterlevnadsprinciper till användarna. När en efterlevnadsprincip distribueras till en användare så kontrolleras om användarens enheter uppfyller efterlevnadskraven. Information om hur lång tid det tar för mobila enheter att hämta en princip efter att den har distribuerats finns i [Troubleshooting device profiles in Microsoft Intune](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned) (Felsöka enhetsprofiler i Microsoft Intune).

#### <a name="actions-for-non-compliance"></a>Åtgärder vid inkompatibilitet

Med åtgärder för inkompatibilitet kan du konfigurera en tidsordnad sekvens med åtgärder som tillämpas på enheter som inte uppfyller villkoren för efterlevnadsprinciperna. Mer information finns i [Automatisera åtgärder för inkompatibilitet](actions-for-noncompliance.md).

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>Använda efterlevnadsprinciper för enheter i Intune kontra Azure-portalen

Observera de viktigaste skillnaderna som hjälper dig att övergå till det nya arbetsflödet med principefterlevnad i Azure Portal.

- Efterlevnadsprinciper skapas separat för varje plattform som stöds i Azure-portalen.
- I den klassiska Intune-administratörskonsolen är en efterlevnadsprincip gemensam för alla plattformar som stöds.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>Migrera enhetsefterlevnadsprinciper från den klassiska portalen för Intune till Azure Portal

Principer för enhetsefterlevnad som har skapats i den [klassiska Intune-portalen](https://manage.microsoft.com) visas inte i nya [Intune Azure Portal](https://portal.azure.com). De kommer dock fortfarande att vara riktade till användarna och kunna hanteras via den klassiska Intune-portalen.

Om du vill dra nytta av de funktioner i Azure Portal som relaterar till den nya enhetsefterlevnaden måste du skapa nya principer för enhetsefterlevnad i Azure Portal. Om du tilldelar en användare en ny princip för enhetsefterlevnad i Azure Portal-portalen, och denna användare även har tilldelats en princip för enhetsefterlevnad från den klassiska Intune-portalen, så har principerna för enhetsefterlevnad från Azure Portal företräde framför dem från den klassiska Intune-konsolen.

##  <a name="next-steps"></a>Nästa steg

- Skapa en princip för enhetsefterlevnad för följande plattformar:

   - [Android](compliance-policy-create-android.md)
   - [Android for Work](compliance-policy-create-android-for-work.md)
   - [iOS](compliance-policy-create-ios.md)
   - [macOS](compliance-policy-create-mac-os.md)
   - [Windows](compliance-policy-create-windows.md)

- Information om principentiteter för Intune-informationslagret finns i [Referens för principentiteter](reports-ref-policy.md).
