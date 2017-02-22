---
title: "Enhetsefterlevnad | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Använd det här avsnittet om du vill veta mer om enhetsefterlevnad i Microsoft Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7693d49e2f0fa6e4aa40b6bb71433a7eaab8dd15
ms.openlocfilehash: a4254503e4e6b86079f862966dee2727934f1ee6


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>Vad är enhetsefterlevnad i Intune Azure-förhandsversionen?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

För att skydda företagets data måste du se till att de enheter som används för åtkomst till företagets appar och data följer särskilda regler. Dessa regler kan till exempel kräva att en PIN-kod används för att komma åt enheter samt kryptering av data som lagras på enheter. En uppsättning med sådana regler kallas för en **efterlevnadsprincip**.

##  <a name="how-should-i-use-a-device-compliance-policy"></a>Hur använder jag en efterlevnadsprincip för enheter?
Du kan använda efterlevnadsprinciper med villkorlig åtkomst om du endast vill tillåta enheter som uppfyller efterlevnadsprincipens regler för åtkomst till e-post och andra tjänster.

Du kan också använda efterlevnadsprinciper utan villkorlig åtkomst.
När du använder efterlevnadsprinciper separat utvärderas målenheterna varefter deras efterlevnadsstatus rapporteras. Du kan t.ex. få en rapport om hur många enheter som inte är krypterade eller vilka enheter som är upplåsta (jailbreakade) eller rotade. Men när du använder efterlevnadsprinciper separat tillämpas inga åtkomstbegränsningar på företagsresurser.

Du distribuerar efterlevnadsprinciper till användarna. När en efterlevnadsprincip distribueras till en användare så kontrolleras om användarens enheter uppfyller efterlevnadskraven. Information om hur lång tid det tar för mobila enheter att hämta en princip efter att den har distribuerats, finns i Hantera inställningar och funktioner på dina enheter.

##  <a name="concepts"></a>Begrepp
Nedan visas några termer och begrepp som är användbara för att förstå hur du kan använda efterlevnadsprinciper.

### <a name="compliance-requirements"></a>Efterlevnadskrav
Efterlevnadskrav är i stort sett regler som kräver en enhets PIN-kod eller kryptering, vilket du kan ange att det krävs eller inte krävs för en efterlevnadsprincip.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be non-compliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

##  <a name="differences-between-the-classic-intune-admin-console-and-intune-in-the-azure-portal"></a>Skillnader mellan den klassiska Intune-administratörskonsolen och Intune i Azure-portalen


Om du har använt den klassiska Intune-administratörskonsolen tidigare, bör du observera följande skillnader om du ska övergå till det nya efterlevnadsarbetsflödet i Azure-portalen:


-   Efterlevnadsprinciper skapas separat för varje plattform som stöds i Azure-portalen. I Intune-administratörskonsolen är en efterlevnadsprincip gemensam för alla plattformar som stöds.


<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="next-steps"></a>Nästa steg

[Kom igång med efterlevnadsprinciper](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->



<!--HONumber=Feb17_HO1-->


