---
title: Policyer för efterlevnad för enheter i Microsoft Intune – Azure | Microsoft Docs
description: Kom igång med att använda enhetsefterlevnadsprinciper, få en översikt över status och allvarlighetsgrader, använd statusen InGracePeriod, arbeta med villkorsstyrd åtkomst, hantera enheter utan en tilldelad princip och se skillnaderna i efterlevnad mellan Azure-portalen och den klassiska portalen i Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 967bf9937c71ff3ca7277f43fd969291eb5af6de
ms.sourcegitcommit: c2e62f1ebdf75599c8e544287123c602f0f15f2b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72749177"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>Ange regler för enheter som tillåter åtkomst till resurser i din organisation med Intune

Många MDM-lösningar för hantering av mobilenheter skyddar organisationens data genom att kräva att användare och enheter uppfyller vissa krav. I Intune kan kallas den här funktionen för ”efterlevnadsprinciper”. Efterlevnadsprinciperna definierar de regler och inställningar som användare och enheter måste följa för att vara kompatibla. I kombination med villkorlig åtkomst kan administratörer blockera användare och enheter som inte följer reglerna.

En Intune-administratör kan till exempel kräva att:

- Slutanvändarna ska använda ett lösenord för att få åtkomst till organisationens data på mobila enheter
- Att enheten inte är jailbrokad eller rotad
- En högsta eller lägsta operativsystemversion finns på enheten
- Att enheten ligger på eller under en hotnivå

Du kan också använda den här funktionen till att övervaka efterlevnadsstatus på enheter i din organisation.

> [!IMPORTANT]
> Intune följer enhetens incheckningsschema för alla efterlevnadsutvärderingar på enheten. [Princip-och profiluppdateringscykler](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) visar de uppskattade uppdateringstiderna.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

- When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

- 3 days after initial noncompliance state, a follow up reminder is sent to the user.

- 5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

- 7 days after initial noncompliance state, access to company resources is blocked. This requires that you have Conditional Access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement Conditional Access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>Enhetsefterlevnadsprinciper kan användas med Azure AD

Intune använder [villkorlig åtkomst](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) i Azure Active Directory (AD) (öppnar en annan dokumentwebbplats) för att tvinga fram efterlevnaden. När en enhet registreras i Intune startas även registreringen i Azure AD och enhetens information uppdateras i Azure AD. Enhetens efterlevnadsstatus är viktig information. Efterlevnadsstatusen används av villkorliga åtkomstprinciper för att blockera eller tillåta åtkomst till e-post eller andra organisationsresurser.

- [Vad är enhetshantering i Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/device-management-introduction) är en bra resurs som beskriver varför och hur enheter registreras i Azure AD.

- I [Villkorlig åtkomst](conditional-access.md) och [Vanliga sätt att använda villkorlig åtkomst på](conditional-access-intune-common-ways-use.md) beskrivs den här funktionen i relation till Intune.

## <a name="ways-to-use-device-compliance-policies"></a>Hantera efterlevnadsprinciper för enheter

### <a name="with-conditional-access"></a>Med villkorlig åtkomst

Du kan ge enheter som följer principreglerna åtkomst till e-post och andra organisationsresurser. Om enheterna inte följer principreglerna får de inte någon åtkomst till organisationsresurserna. Det är det som kallas villkorlig åtkomst.

### <a name="without-conditional-access"></a>Utan villkorlig åtkomst

Du kan även använda policyer för enhetsefterlevnad utan villkorlig åtkomst. När du använder efterlevnadsprinciper separat utvärderas målenheterna varefter deras efterlevnadsstatus rapporteras. Du kan t.ex. få en rapport om hur många enheter som inte är krypterade, eller vilka enheter som är jailbrokade eller rotade. När du använder efterlevnadsprinciper utan villkorlig åtkomst, tillämpas inga åtkomstbegränsningar på organisationens resurser.

## <a name="ways-to-deploy-device-compliance-policies"></a>Sätt att distribuera policyer för efterlevnad för enheter

Du kan distribuera policyer för efterlevnad till användare i användargrupper eller till enheter i enhetsgrupper. När en efterlevnadsprincip distribueras till en användare så kontrolleras om alla användarens enheter uppfyller efterlevnadskraven. På Windows 10 version 1803 och senare enheter, rekommenderar vi för att distribuera till enhetsgrupper *om* den primära användaren inte registrerat enheten. Användning av enhetsgrupper i det här scenariot hjälper till med kompabilitetsrapportering.

Intune innehåller också en uppsättning inbyggda efterlevnadsprincipinställningar. Följande inbyggda principer utvärderas på alla enheter som registrerats i Intune:

- **Markera enheter utan någon tilldelad policy för efterlevnad som**: Den här egenskapen har två värden:

  - **Kompatibel** (*standard*): säkerhetsfunktion av
  - **Ej kompatibel**: säkerhetsfunktion av

  Om en enhet inte har en policy för efterlevnad är den kompatibel som standard. Om du använder villkorlig åtkomst med kompatibla principer rekommenderar vi att du ändrar standardinställningen till **Inte kompatibel**. Om en användare inte är kompatibel eftersom ingen princip har tilldelats, visar [företagsportalsappen](../apps/company-portal-app.md) `No compliance policies have been assigned`.

- **Förbättrad identifiering av uppbrytning**: När den här inställningen är aktiverad kommer iOS-enheter checka in till Intune oftare. När du aktiverar den här egenskapen används enhetens platstjänster, vilket påverkar batterianvändningen. Användarens platsdata lagras inte av Intune.

  När du aktiverar den här inställningen kräver den följande av enheter:
  - Aktivera platstjänster på operativsystemsnivå.
  - Tillåt att företagsportalen använder platstjänster.
  - Utvärdera och rapportera status för upplåsning till Intune minst en gång var 72:a timme. Annars markeras enheten som ej kompatibel. Utvärderingen utlöses genom att företagsportalappen öppnas, eller att enheten fysiskt flyttas minst 500 meter. Om enheten inte flyttas 500 meter inom 72 timmar, måste användaren öppna företagsportalappen för utökad utvärdering av upplåsningen.

- **Giltighetsperiod för efterlevnadsstatus (dagar)** : Ange inom vilken tidsperiod enheterna ska rapportera status för alla mottagna efterlevnadsprinciper. Enheter som inte returnerar status inom den här tidsperioden behandlas som inkompatibla. Standardvärdet är 30 dagar.

Du kan använda dessa inbyggda principer till att övervaka inställningarna. Intune [uppdaterar eller söker efter uppdateringar](create-compliance-policy.md#refresh-cycle-times) med olika intervall, beroende på enhetsplattform. [Vanliga frågor, problem och lösningar med enhetsprinciper och profiler i Microsoft Intune](../configuration/device-profile-troubleshoot.md) är en bra resurs.

Efterlevnadsrapporter är ett bra sätt att kontrollera status för enheter. I [Övervaka efterlevnadsprinciper](compliance-policy-monitor.md) finns mer vägledning.

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>Inkompatibilitet och villkorlig åtkomst på olika plattformar

Följande tabell beskriver också hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst.

---------------------------

|**Principinställning**| **Plattform** |
| --- | ----|
| **Konfiguration av PIN-kod eller lösenord** | - **Android 4.0 och senare**: I karantän<br>- **Samsung Knox Standard 4.0 och senare**: I karantän<br>- **Android Enterprise**: I karantän  <br>  <br>- **iOS 8.0 och senare**: Åtgärdad<br>- **macOS 10.11 och senare**: Åtgärdad  <br>  <br>- **Windows 8.1 och senare**: Åtgärdad<br>- **Windows Phone 8.1 och senare**: Åtgärdad|
| **Enhetskryptering** | - **Android 4.0 och senare**: I karantän<br>- **Samsung Knox Standard 4.0 och senare**: I karantän<br>- **Android Enterprise**: I karantän<br><br>- **iOS 8.0 och senare**: Åtgärdad (genom angiven PIN-kod)<br>- **macOS 10.11 och senare**: Åtgärdad (genom angiven PIN-kod)<br><br>- **Windows 8.1 och senare**: Inte tillämpligt<br>- **Windows Phone 8.1 och senare**: Åtgärdad |
| **Jailbreakad eller rotad enhet** | - **Android 4.0 och senare**: I karantän (inte en inställning)<br>- **Samsung Knox Standard 4.0 och senare**: I karantän (inte en inställning)<br>- **Android Enterprise**: I karantän (inte en inställning)<br><br>- **iOS 8.0 och senare**: I karantän (inte en inställning)<br>- **macOS 10.11 och senare**: Inte tillämpligt<br><br>- **Windows 8.1 och senare**: Inte tillämpligt<br>- **Windows Phone 8.1 och senare**: Inte tillämpligt |
| **E-postprofil** | - **Android 4.0 och senare**: Inte tillämpligt<br>- **Samsung Knox Standard 4.0 och senare**: Inte tillämpligt<br>- **Android Enterprise**: Inte tillämpligt<br><br>- **iOS 8.0 och senare**: I karantän<br>- **macOS 10.11 och senare**: I karantän<br><br>- **Windows 8.1 och senare**: Inte tillämpligt<br>- **Windows Phone 8.1 och senare**: Inte tillämpligt |
| **Lägsta version av operativsystemet** | - **Android 4.0 och senare**: I karantän<br>- **Samsung Knox Standard 4.0 och senare**: I karantän<br>- **Android Enterprise**: I karantän<br><br>- **iOS 8.0 och senare**: I karantän<br>- **macOS 10.11 och senare**: I karantän<br><br>- **Windows 8.1 och senare**: I karantän<br>- **Windows Phone 8.1 och senare**: I karantän |
| **Högsta version av operativsystemet** | - **Android 4.0 och senare**: I karantän<br>- **Samsung Knox Standard 4.0 och senare**: I karantän<br>- **Android Enterprise**: I karantän<br><br>- **iOS 8.0 och senare**: I karantän<br>- **macOS 10.11 och senare**: I karantän<br><br>- **Windows 8.1 och senare**: I karantän<br>- **Windows Phone 8.1 och senare**: I karantän |
| **Attestering av hälsotillstånd i Windows** | - **Android 4.0 och senare**: Inte tillämpligt<br>- **Samsung Knox Standard 4.0 och senare**: Inte tillämpligt<br>- **Android Enterprise**: Inte tillämpligt<br><br>- **iOS 8.0 och senare**: Inte tillämpligt<br>- **macOS 10.11 och senare**: Inte tillämpligt<br><br>- **Windows 10 and Windows 10 Mobile**: I karantän<br>- **Windows 8.1 och senare**: I karantän<br>- **Windows Phone 8.1 och senare**: Inte tillämpligt |

---------------------------

**Åtgärdad**: Enhetens operativsystem tillämpar efterlevnad. Till exempel om användaren tvingas att ange en PIN-kod.

**I karantän**: Enhetens operativsystem tillämpar inte efterlevnad. Till exempel tvingar Android- och Android Enterprise-enheter inte användaren att kryptera enheten. När enheten inte uppfyller efterlevnadskraven utförs följande åtgärder:

- Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
- Företagsportalappen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="azure-classic-portal-vs-azure-portal"></a>Den klassiska Azure-portalen jämfört med Azure-portalen

De största skillnaderna när du använder policyer för efterlevnad i Azure Portal:

- Policyer för efterlevnad skapas separat för varje plattform som stöds i Azure Portal
- I den klassiska Azure-portalen är en policy för efterlevnad gemensam för alla plattformar som stöds

<!--- - In the Azure portal, you have the ability to specify actions and notifications that are initiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

- In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

Policyer för efterlevnad för enheter som skapas i den [klassiska portalen](https://manage.microsoft.com) visas inte i [Azure Portal](https://portal.azure.com). De gäller dock fortfarande användare och kan hanteras via den klassiska portalen.

Om du vill använda de funktioner i Azure Portal som är relaterade till policyer för enhetsefterlevnad måste du skapa nya policyer för enhetsefterlevnad i Azure Portal. Om du tilldelar en användare en ny policy för enhetsefterlevnad i Azure Portal och denna användare även har tilldelats en policy för enhetsefterlevnad från den klassiska portalen så har policyerna för enhetsefterlevnad från Azure Portal företräde framför dem från den klassiska portalen.

## <a name="next-steps"></a>Nästa steg

- [Skapa en princip](create-compliance-policy.md) och visa kraven.
- Se efterlevnadsinställningar för de olika enhetsplattformarna:

  - [Android](compliance-policy-create-android.md)
  - [Android enterprise](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows Holographic for Business](compliance-policy-create-windows.md#windows-holographic-for-business)
  - [Windows Phone 8.1](compliance-policy-create-windows-8-1.md)
  - [Windows 8.1 och senare](compliance-policy-create-windows-8-1.md)
  - [Windows 10 och senare](compliance-policy-create-windows.md)

- Information om principentiteter för Intune Data Warehouse finns i [Referens för principentiteter](../reports-ref-policy.md).
