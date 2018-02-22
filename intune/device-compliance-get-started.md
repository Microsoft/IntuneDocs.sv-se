---
title: "Efterlevnadsprinciper för Intune-enheter"
titleSuffix: Azure portal
description: "Använd det här ämnet för att läsa mer om enhetsefterlevnad i Microsoft Intune”"
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6f4a9f70762c3d30a49a686bcf1cfa9de4851b6c
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2018
---
# <a name="get-started-with-intune-device-compliance-policies"></a>Komma igång med principer för Intune-enhetsefterlevnad

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="what-is-device-compliance-in-intune"></a>Vad är enhetsefterlevnad i Intune?

Efterlevnadsprinciper definierar de regler och inställningar som en Intune-enhet måste följa för att anses vara kompatibla med Intune.

Reglerna omfattar följande:

- Använd lösenord för att få åtkomst till enheter

- Kryptering

- Om enheten är jailbrokad eller rotad

- Lägsta tillåtna version av operativsystemet

- Högsta tillåtna version av operativsystemet

- Enheten måste ligga på eller under nivån för skydd mot mobilhot

Du kan också använda principer för enhetsefterlevnad för att övervaka enheters efterlevnadsstatus.

### <a name="device-compliance-requirements"></a>Krav på efterlevnad för enhet

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

När en enhet registreras i Intune sker även registreringen i Azure AD, vilket uppdaterar enhetens egenskaper med mer information i Azure AD. En viktig del av informationen är enhetens efterlevnadsstatus, vilket används av villkorlig åtkomstprinciper för att blockera eller tillåta åtkomst till e-post eller andra företagsresurser.

- Läs mer om [registreringsprocessen i Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-overview).

##  <a name="ways-to-use-device-compliance-policies"></a>Hantera efterlevnadsprinciper för enheter

### <a name="with-conditional-access"></a>Med villkorlig åtkomst
Du kan använda efterlevnadsprinciper med villkorlig åtkomst om du endast vill tillåta enheter som uppfyller en eller flera efterlevnadsprincipens regler för åtkomst till e-post och andra företagsresurser.

### <a name="without-conditional-access"></a>Utan villkorlig åtkomst
Du kan också använda principer för enhetsefterlevnad oberoende av villkorlig åtkomst. När du använder efterlevnadsprinciper separat utvärderas målenheterna varefter deras efterlevnadsstatus rapporteras. Du kan t.ex. få en rapport om hur många enheter som inte är krypterade eller vilka enheter som är upplåsta (jailbreakade) eller rotade. Men när du använder efterlevnadsprinciper separat tillämpas inga åtkomstbegränsningar på företagsresurser.

Du distribuerar efterlevnadsprinciper till användarna. När en efterlevnadsprincip distribueras till en användare så kontrolleras om användarens enheter uppfyller efterlevnadskraven. Information om hur lång tid det tar för mobila enheter att hämta en princip efter att den har distribuerats finns i [Troubleshooting device profiles in Microsoft Intune](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned) (Felsöka enhetsprofiler i Microsoft Intune).

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>Använda efterlevnadsprinciper för enheter i Intune kontra Azure-portalen

Observera de viktigaste skillnaderna som hjälper dig att övergå till det nya arbetsflödet med principefterlevnad i Azure Portal.

- Efterlevnadsprinciper skapas separat för varje plattform som stöds i Azure-portalen.
- I den klassiska Intune-administratörskonsolen är en efterlevnadsprincip gemensam för alla plattformar som stöds.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>Migrera enhetsefterlevnadsprinciper från den klassiska portalen för Intune till Azure Portal

Principer för enhetsefterlevnad som skapats i den [klassiska Intune-portalen](https://manage.microsoft.com) visas inte i nya [Intune Azure Portal](https://portal.azure.com). De kommer dock fortfarande att vara riktade till användarna och kunna hanteras via den klassiska Intune-portalen.

Om du vill dra nytta av de funktioner i Azure Portal som relaterar till den nya enhetsefterlevnaden, så måste du skapa nya principer för enhetsefterlevnad i Azure Portal. Om du tilldelar en användare en ny princip för enhetsefterlevnad i Azure Portal-portalen, och denna användare även har tilldelats en princip för enhetsefterlevnad från den klassiska Intune-portalen, så har principerna för enhetsefterlevnad från Azure Portal företräde framför dem från den klassiska Intune-konsolen.

##  <a name="next-steps"></a>Nästa steg

Skapa en princip för enhetsefterlevnad för följande plattformar:

- [Android](compliance-policy-create-android.md)
- [Android for Work](compliance-policy-create-android-for-work.md)
- [iOS](compliance-policy-create-ios.md)
- [macOS](compliance-policy-create-mac-os.md)
- [Windows](compliance-policy-create-windows.md)
