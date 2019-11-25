---
title: Skapa enhetsefterlevnadsprinciper i Microsoft Intune – Azure | Microsoft Docs
description: Skapa enhetsefterlevnadsprinciper, översikt över status och allvarlighetsgrader, använda statusen InGracePeriod, arbeta med villkorsstyrd åtkomst, hantera enheter utan en tilldelad princip, samt skillnader i efterlevnad i Azure-portalen och den klassiska portalen i Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
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
ms.openlocfilehash: c8452f9b56032864380ec703bfd444dc85ef129b
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188267"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Skapa en efterlevnadsprincip i Microsoft Intune

Enhetsefterlevnadsprinciper är en viktig funktion när du använder Intune för att skydda din organisations resurser. I Intune kan du skapa regler och inställningar som enheter måste uppfylla för att anses vara kompatibla, till exempel en lägsta operativsystemversion. Om enheten inte är kompatibel kan du blockera åtkomst till data och resurser med hjälp av [villkorlig åtkomst](conditional-access.md).

Du kan också vidta åtgärder vid inkompatibilitet genom att exempelvis skicka ett e-postmeddelande till användaren. En översikt över vad efterlevnadsprinciper gör och hur de används finns i avsnittet om att [komma igång med enhetsefterlevnad](device-compliance-get-started.md).

Den här artikeln:

- Visar kraven och stegen för att skapa en efterlevnadsprincip.
- Visar hur du tilldelar principen till dina användare och enhetsgrupper.
- Beskriver ytterligare funktioner, inklusive omfångstaggar för att ”filtrera” dina principer, samt vad du kan göra på enheter som inte är kompatibla.
- Visar en lista med incheckningstider för uppdateringscykeln när enheterna tar emot principuppdateringar.

## <a name="before-you-begin"></a>Innan du börjar

Om du vill använda enhetsefterlevnadsprinciper måste du:

- Använd följande prenumerationer:

  - Intune
  - Om du använder villkorlig åtkomst måste du ha Azure Active Directory (AD) Premium-utgåvan. I listan [Priser för Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) visas vad som finns i de olika utgåvorna. Intune-efterlevnad kräver inte Azure AD.

- Använd en plattform som stöds:

  - Android-enhetsadministratör
  - Android enterprise
  - iOS
  - macOS
  - Windows 10
  - Windows 8,1
  - Windows Phone 8.1

- Registrera enheter i Intune (krävs för att kunna se efterlevnadsstatusen)

- Registrera enheter för en användare, eller registrera utan någon primär användare. Enheter som har registrerats för flera användare stöds inte.

## <a name="create-the-policy"></a>Skapa principen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Efterlevnadsprinciper** > **Skapa princip**.

3. Ange följande egenskaper:

   - **Namn**: Ange ett beskrivande namn på principen. Namnge dina principer så att du enkelt kan identifiera dem senare. Till exempel är ett bra principnamn **Markera jailbrokade iOS-enheter som inkompatibla**.

   - **Beskrivning**: Ange en beskrivning av principen. Denna inställning är valfri, men rekommenderas.

   - **Plattform**: Välj plattform för dina enheter. Alternativen är:
     - **Android-enhetsadministratör**
     - **Android enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 och senare**
     - **Windows 10 och senare**

     För *Android Enterprise* måste du sedan välja en **Profiltyp**:
     - **Enhetsägare**
     - **Arbetsprofil**

   - **Inställningar**: I följande artiklar beskrivs inställningarna för varje plattform:
     - [Android-enhetsadministratör](compliance-policy-create-android.md)
     - [Android enterprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [macOS](compliance-policy-create-mac-os.md)
     - [Windows Phone 8.1, Windows 8.1 och senare](compliance-policy-create-windows-8-1.md)
     - [Windows 10 och senare](compliance-policy-create-windows.md)  

   - **Platser** *(Android-enhetsadministratör)* : I principen kan du framtvinga kompatibilitet baserat på enhetens plats. Välj från befintliga platser. Har du inga platser ännu? Du kan läsa mer i [Använda platser (nätverksstängsel) i Intune](use-network-locations.md).  

   - **Åtgärder för inkompatibilitet**: För enheter som inte uppfyller dina efterlevnadsprinciper kan du lägga till en sekvens av åtgärder som ska tillämpas automatiskt. Du kan ändra schemat när enheten har markerats som inkompatibel, till exempel efter en dag. Du kan också konfigurera en andra åtgärd som skickar ett e-postmeddelande till användaren när enheten inte är kompatibel.

     [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) innehåller mer information, inklusive anvisningar för hur du skapar ett e-postmeddelande till användarna.

     Anta till exempel att du använder funktionen Platser och lägger till en plats i en efterlevnadsprincip. Standardåtgärden för inkompatibilitet tillämpas när du väljer minst en plats. Om enheten inte är ansluten till de valda platserna utvärderas den omedelbart som inkompatibel. Du kan ge användarna en respitperiod, till exempel en dag.

   - **Omfång (taggar)** : Omfångstaggar är ett bra sätt att tilldela och filtrera principer till specifika grupper, till exempel Försäljning, Personal eller Alla amerikanska NC-anställda. När du har lagt till inställningarna kan du också lägga till en omfångstagg till efterlevnadsprinciperna. [Använd omfångstaggar för att filtrera principer](../fundamentals/scope-tags.md) är en bra resurs.

4. Välj **OK** > **Skapa** när du är klar för att spara dina ändringar. Principen skapas och visas i listan. Tilldela därefter principen till dina grupper.

## <a name="assign-the-policy"></a>Tilldela principen

När en princip har skapats är nästa steg att tilldela principen till dina grupper:

1. Välj den princip som du skapade. Befintliga principer finns i **Enheter** > **Efterlevnadsprinciper** > **Principer**.

2. Välj *princip* > **Tilldelningar**. Du kan inkludera eller exkludera säkerhetsgrupper i Azure Active Directory (AD).

3. Välj **Valda grupper** för att se dina Azure AD-säkerhetsgrupper. Välj de grupper som du vill att principen ska tillämpas på > Välj **Spara** för att distribuera principen.

De användare eller enheter som omfattas av din princip utvärderas för efterlevnad när de checkar in med Intune.

### <a name="evaluate-how-many-users-are-targeted"></a>Utvärdera hur många användare som omfattas

När du tilldelar principen kan du också **utvärdera** hur många användare som påverkas. Den här funktionen beräknar användare, den beräknar inte enheter.

1. Välj **Enheter** > **Efterlevnadsprinciper** > **Principer** i Intune.

2. Välj *princip* > **Tilldelningar** > **Utvärdera**. Ett meddelande visas med hur många användare som omfattas av principen.

Om knappen **Utvärdera** är nedtonad kontrollerar du att principen har tilldelats till en eller flera grupper.

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>Uppdatera cykeltider

Intune använder olika uppdateringscykler för att söka efter uppdateringar av efterlevnadsprinciper. Om enheten nyligen har registrerats körs incheckningarna oftare. [Princip-och profil uppdaterings cykler](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) visar de uppskattade uppdateringstiderna.

Användarna kan när de vill öppna företagsportalappen och synkronisera enheten för att söka efter principuppdateringar.

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

Anta exempelvis att en enhet har tre tilldelade efterlevnadsprinciper: en med statusen Okänd (allvarlighetsgrad = 1), en med statusen Kompatibel (allvarlighetsgrad = 3) och en med statusen InGracePeriod (allvarlighetsgrad = 4). Statusen InGracePeriod har högst allvarlighetsgrad. Därför har alla tre principerna efterlevnadsstatusen InGracePeriod.

## <a name="next-steps"></a>Nästa steg

[Övervaka dina principer](compliance-policy-monitor.md).
