---
title: "Efterlevnad för enhet"
titleSuffix: Intune Azure preview
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
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2aec7463b9a2b3bdaa78281fca0bbb39dcd3f884
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>Vad är enhetsefterlevnad i Intune Azure-förhandsversionen?

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Principerna för enhetsfterlevnad i Intune definierar de regler och inställningar som en enhet måste följa för att den ska anses vara kompatibel med principerna för villkorlig åtkomst för Intune och EMS. Du kan också använda principer för enhetsefterlevnad för att övervaka och åtgärda enheters efterlevnadsproblem. 

Reglerna omfattar följande:

- Använd lösenord för att få åtkomst till enheter
- Kryptering
- Om enheten är jailbrokad eller rotad
- Lägsta tillåtna version av operativsystemet
- Högsta tillåtna version av operativsystemet
- Enheten måste ligga på eller under nivån för skydd mot mobilhot

<!---##  Concepts
Following are some terms and concepts that are useful to understanding how to use compliance policies.

### Device compliance requirements
Compliance requirements are essentially rules like requiring a device PIN or encryption that you can specify as required or not required for a compliance policy.

### Actions for noncompliance

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

##  <a name="how-should-i-use-a-device-compliance-policy"></a>Hur använder jag en efterlevnadsprincip för enheter?

### <a name="using-ems-conditional-access"></a>Använda villkorlig EMS-åtkomst
Du kan använda efterlevnadsprinciper med villkorlig EMS-åtkomst om du endast vill tillåta enheter som uppfyller en eller flera efterlevnadsprincipens regler för åtkomst till e-post och andra företagsresurser.

### <a name="not-using-ems-conditional-access"></a>Inte använda villkorlig EMS-åtkomst
Du kan också använda principer för enhetsefterlevnad oberoende av villkorlig EMS-åtkomst.
När du använder efterlevnadsprinciper separat utvärderas målenheterna varefter deras efterlevnadsstatus rapporteras. Du kan t.ex. få en rapport om hur många enheter som inte är krypterade eller vilka enheter som är upplåsta (jailbreakade) eller rotade. Men när du använder efterlevnadsprinciper separat tillämpas inga åtkomstbegränsningar på företagsresurser.

Du distribuerar efterlevnadsprinciper till användarna. När en efterlevnadsprincip distribueras till en användare så kontrolleras om användarens enheter uppfyller efterlevnadskraven. Information om hur lång tid det tar för mobila enheter att hämta en princip efter att den har distribuerats, finns i Hantera inställningar och funktioner på dina enheter.

##  <a name="intune-classic-admin-console-vs-intune-azure-preview-portal"></a>Den klassiska Intune-administratörskonsolen och Intune Azure Preview-portalen

Om du har använt den klassiska Intune-administratörskonsolen bör du observera följande skillnader om du ska övergå till det nya efterlevnadsarbetsflödet i Azure Portal:

-   Efterlevnadsprinciper skapas separat för varje plattform som stöds i Azure-portalen. I Intune-administratörskonsolen är en efterlevnadsprincip gemensam för alla plattformar som stöds.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migration-from-intune-classic-console-to-intune-azure-preview-portal"></a>Migrering från den klassiska Intune-konsolen till Intune Azure Preview Portal

Principer för enhetsfterlevnad som skapats i den [klassiska Intune-konsolen](https://manage.microsoft.com) visas inte i nya [Intune Azure Portal](https://portal.azure.com). De kommer dock fortfarande att vara riktade till användarna och kunna hanteras via den klassiska Intune-konsolen.

Om du vill dra nytta av de funktioner i Intune Azure Portal som relaterar till den nya enhetsefterlevnaden, så måste du skapa nya principer för enhetsefterlevnad i Intune Azure Portal. Om du tilldelar en användare en ny princip för enhetsefterlevnad i Intune Azure Portal-portalen, och denna användare även har tilldelats en princip för enhetsefterlevnad från den klassiska Intune-portalen, så har principerna för enhetsefterlevnad från Intune Azure Portal företräde framför dem från den klassiska Intune-konsolen.

##  <a name="next-steps"></a>Nästa steg

[Komma igång med principer för enhetsefterlevnad](device-compliance-get-started.md)


<!---### See also

Conditional access--->

