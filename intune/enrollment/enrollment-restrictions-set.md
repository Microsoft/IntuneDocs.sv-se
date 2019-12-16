---
title: Ange registreringsbegränsningar i Microsoft Intune
titleSuffix: ''
description: Begränsa registrering per plattform och ange en gräns för enhetsregistrering i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78f79a734d0a7b4901b2248b20abd9d304926dd2
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955515"
---
# <a name="set-enrollment-restrictions"></a>Ange registreringsbegränsningar

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Som Intune-administratör kan du skapa och hantera registreringsbegränsningar som definierar vilka enheter som kan registreras för hantering med Intune, inklusive:
- Antalet enheter.
- Operativsystem och versioner.

Du kan skapa flera begränsningar och applicera dem på olika användargrupper. Du kan ange [prioriteringsordningen](#change-enrollment-restriction-priority) för dina olika begränsningar.

>[!NOTE]
>Begränsningar vid registrering ska inte betraktas som säkerhetsfunktioner. Komprometterade enheter kan ju utge sig för att vara en helt annan enhet. Det här är dock en bra barriär för att stänga ute användare utan skadliga avsikter.

Bland de specifika registreringsbegränsningarna som du kan skapa finns:

- Högsta tillåtna antal registrerade enheter.
- Enhetsplattformar som får registreras:
  - Android-enhetsadministratör
  - Android Enterprise-arbetsprofil
  - iOS
  - macOS
  - Windows
  - Windows Mobile
- Version av plattformsoperativsystem för iOS, Android-enhetsadministratör, Android Enterprise-arbetsprofil, Windows och Windows Mobile. (Endast Windows 10-versioner kan användas. Lämna tomt om Windows 8.1 tillåts.)
  - Lägsta version.
  - Högsta version.
- Begränsa [personligt ägda enheter](device-enrollment.md#bring-your-own-device) (endast för iOS, Android-enhetsadministratör, Android Enterprise-arbetsprofil, macOS, Windows och Windows Mobile).

## <a name="default-restrictions"></a>Standardbegränsningar

Standardbegränsningar tillhandahålls automatiskt för både begränsningar för enhetstyp och begränsningar för enhetsgränsregistrering. Du kan ändra alternativen för vad som är standard. Standardbegränsningarna gäller för alla användare och användarlösa registreringar. Du kan åsidosätta de här standardinställningarna genom att skapa nya begränsningar med högre prioritet.

## <a name="create-a-device-type-restriction"></a>Skapa en enhetstypsbegränsning

1. Logga in på [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **Enheter** > **Registreringsbegränsningar** > **Skapa begränsning** > **Begränsning av enhetstyp**.
2. På sidan **Grundinställningar** ger du begränsningen ett **Namn** och en valfri **Beskrivning**.
3. Välj **Nästa** för att gå till sidan **Plattforminställningar**.
4. Under **Plattform** väljer du **Tillåt** för de plattformar som du vill att begränsningen ska tillåta.
    ![Skärmpunkt för att välja plattformsinställningar](./media/enrollment-restrictions-set/choose-platform-settings.png)
5. Under **Versioner** väljer du de lägsta och högsta versioner som du vill att de tillåtna plattformarna ska stödja. Versionsbegränsningar gäller endast för enheter som har registrerats med företagsportalen.
     Versionsformat som stöds är:
    - Android-enhetsadministratör- och Android Enterprise-arbetsprofilen stöder major.minor.rev.build.
    - iOS stöder major.minor.rev. Operativsystemversionerna gäller inte för Apple-enheter som registreras med programmet för enhetsregistrering, Apple School Manager eller Apple Configurator-appen.
    - Windows stöder endast major.minor.build.rev för Windows 10.
    
    > [!IMPORTANT]
    > Plattformar för Android Enterprise (arbetsprofil) och Android-enhetsadministratör har följande beteende:
    > - Om båda plattformarna tillåts för samma grupp registreras användarna med en arbetsprofil om deras enhet stöder det. Annars registreras de som DA. 
    > - Om båda plattformarna tillåts för gruppen och raffineras för specifika och icke-överlappande versioner får användarna det registreringsflöde som definierats för deras OS-version. 
    > - Om båda plattformarna är tillåtna, men blockeras för samma versioner, kommer användare på enheter med de blockerade versionerna att dirigeras till registreringsflödet för Android-enhetsadministratör och sedan blockeras från registrering samt uppmanas att logga ut. 
    >
    > Observera att varken registrering med arbetsprofil eller enhetsadministratör fungerar såvida inte rätt förutsättningar har uppfyllts i Android-registrering. 
    
   > [!Note]
   > Windows 10 tillhandahåller inte rev-numret under registrering, så om du exempelvis anger 10.0.17134.100 och enheten är 10.0.17134.174 kommer den att blockeras under registreringen.

6. Under **Personligt ägda** väljer du **Tillåt** för de plattformar som du vill tillåta som personligt ägda enheter.
7. Välj **Nästa** för att gå till sidan **Tilldelningar**.
8. Välj **Välj grupper att inkludera** och använd sedan sökrutan för att hitta grupper som du vill ska ingå i begränsningen. Begränsningen gäller endast för grupper som den är tilldelad till. Om du inte tilldelar en begränsning till minst en grupp så påverkar den inte något. Välj sedan **Välj**. 
    ![Skärmpunkt för att välja plattformsinställningar](./media/enrollment-restrictions-set/select-groups.png)
9. Välj **Nästa** för att gå till sidan **Granska + skapa**.
10. Välj **Skapa** för att skapa begränsningen.
11. Den nya begränsningen skapas med prioritet precis ovanför standardvärdet. Du kan [ändra prioriteten](#change-enrollment-restriction-priority).


## <a name="create-a-device-limit-restriction"></a>Skapa en enhetsgränsbegränsning

1. Logga in på [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **Enheter** > **Registreringsbegränsningar** > **Skapa begränsning** > **Begränsning av enhetsgräns**.
2. På sidan **Grundinställningar** ger du begränsningen ett **Namn** och en valfri **Beskrivning**.
3. Välj **Nästa** för att gå till sidan **Enhetsgräns**.
4. För **Enhetsgräns**, ange det maximala antalet enheter som en användare kan registrera.
    ![Skärmpunkt för att välja enhetsgräns](./media/enrollment-restrictions-set/choose-device-limit.png)
5. Välj **Nästa** för att gå till sidan **Tilldelningar**.
6. Välj **Välj grupper att inkludera** och använd sedan sökrutan för att hitta grupper som du vill ska ingå i begränsningen. Begränsningen gäller endast för grupper som den är tilldelad till. Om du inte tilldelar en begränsning till minst en grupp så påverkar den inte något. Välj sedan **Välj**. 
    ![Skärmpunkt för att välja grupper](./media/enrollment-restrictions-set/select-groups-device-limit.png)
7. Välj **Nästa** för att gå till sidan **Granska + skapa**.
8. Välj **Skapa** för att skapa begränsningen.
9. Den nya begränsningen skapas med prioritet precis ovanför standardvärdet. Du kan [ändra prioriteten](#change-enrollment-restriction-priority).

Vid BYOD-registrering ser användarna information om att de har uppnått gränsen för antalet registrerade enheter. Till exempel i iOS:

![Avisering om enhetsbegränsning på iOS](./media/enrollment-restrictions-set/enrollment-restrictions-ios-set-limit-notification.png)

> [!IMPORTANT]
> Enhetsbegränsningar gäller inte för följande typer av Windows-registrering:
> - Samhanterade registreringar
> - GPO-registreringar
> - Azure Active Directory-anslutna registreringar
> - Massanslutna Azure Active Directory-registreringar
> - Autopilot-registreringar
> - Registreringar med enhetsregistreringshanteraren
>
> Enhetsbegränsningar tillämpas inte för dessa typer av registreringar eftersom de anses vara scenarier för delade enheter.
> Du kan ange fasta gränser för dessa typer av registreringar [i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal#configure-device-settings).


## <a name="change-enrollment-restrictions"></a>Ändra registreringsbegränsningar

Du kan ändra inställningarna för en begränsning för registrering genom att följa stegen nedan. Dessa begränsningar påverkar inte enheter som redan har registrerats. Enheter som registreras med [Intune PC-agenten](../fundamentals/manage-windows-pcs-with-microsoft-intune.md) kan inte blockeras med den här funktionen.

1. Logga in på [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **Enheter** > **Registreringsbegränsningar** > välj den begränsning som du vill ändra > **Egenskaper**.
2. Välj **Redigera** bredvid de inställningar som du vill ändra.
3. På sidan **Redigera** gör du dina önskade ändringar och fortsätter till sidan **Granska + spara** och väljer sedan **Save**.


## <a name="blocking-personal-android-devices"></a>Blockera personliga Android-enheter
- Om du blockerar registrering av personligt ägda Android-enhetsadministratörenheter kan du ändå registrera personligt ägda Android Enterprise-arbetsprofilenheter.
- Som standard är dina inställningar för Android Enterprise-arbetsprofilenheter samma som inställningarna för dina Android-enhetsadministratörenheter. När du har ändrat din arbetsprofil för Android Enterprise eller Android-enhetsadministratörsinställningar är detta inte längre fallet.
- Om du blockerar registrering av personligt ägda Android Enterprise-arbetsprofilenheter så kan endast företagsägda Android Enterprise-enheter att registreras som Android-arbetsprofil.

## <a name="blocking-personal-windows-devices"></a>Blockera personliga Windows-enheter
Om du blockerar personligt ägda Windows-enheter från registrering så kontrollerar Intune att varje ny begäran om Windows-registrering har godkänts som en företagsregistrering. Obehöriga registreringar kommer att blockeras.

Följande metoder räknas som auktoriserade som Windows-företagsregistrering:
- Den registrerande användaren använder ett [konto för enhetsregistreringshanteraren]( device-enrollment-manager-enroll.md).
- Enheten registreras via [Windows Autopilot](enrollment-autopilot.md).
- Enheten registreras med Windows Autopilot, men är inte det enda MDM-registreringsalternativet i Windows-inställningarna.
- Enhetens IMEI-nummer anges i **Enhetsregistrering** > **[ID:n för företagsenheter](corporate-identifiers-add.md)**. (Stöds inte för Windows Phone 8.1.)
- Enheten registreras via ett [bulketableringspaket](windows-bulk-enroll.md).
- Enheten registreras via GPO eller [automatisk registrering från SCCM för samhantering](https://docs.microsoft.com/sccm/comanage/quickstart-paths#bkmk_path1).
 
Följande registreringar är markerade som företagets av Intune. Men eftersom Intune-administratören inte har någon kontroll per enhet, kommer de att blockeras:
- [Automatisk MDM-registrering](windows-enroll.md#enable-windows-10-automatic-enrollment) med [Azure Active Directory-anslutning under Windows-installationen](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Automatisk MDM-registrering](windows-enroll.md#enable-windows-10-automatic-enrollment) med [Azure Active Directory-anslutning från Windows-inställningar](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
Följande personliga registreringsmetoder blockeras också:
- [Automatisk MDM-registrering](windows-enroll.md#enable-windows-10-automatic-enrollment) med [Lägg till arbetskonto från Windows-inställningar](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- Alternativet [MDM enrollment only]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) (Endast MDM-registrering) från Windows-inställningarna.

\* Dessa kommer inte att blockeras om de registrerats med Autopilot.


## <a name="blocking-personal-ios-devices"></a>Blockera personliga iOS-enheter
Intune klassificerar iOS-enheter som personligt ägda som standard. För att klassificeras som företagsägd måste iOS-enheten uppfylla något av följande villkor:
- Registrerad med ett serienummer eller IMEI.
- Registrerad med automatisk enhetsregistrering (tidigare Programmet för enhetsregistrering)


## <a name="change-enrollment-restriction-priority"></a>Ändra prioritet för registreringsbegränsning

Prioritet används när en användare befinner sig i flera grupper som tilldelas begränsningar. Användarna berörs endast av begränsningen med högst prioritet som är tilldelad till en grupp där de finns. Till exempel är Jens i grupp A tilldelad begränsningar med prioritet 5 och i grupp B tilldelad begränsningar med prioritet 2. Jens berörs då endast av begränsningar med prioritet 2.

När du skapar en begränsning läggs den till i listan precis ovanför den som är standard.

Enhetsregistrering inkluderar standardbegränsningar för både enhetstyp och för enhetsgränsbegränsningar. De här två begränsningarna gäller för alla användare om de inte åsidosätts av begränsningar med högre prioritet.

Du kan ändra prioriteten för begränsningar som inte är standard.

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster**, sök efter **Intune** och välj sedan **Intune**.
3. Välj **Enhetsregistrering** > **Registreringsbegränsningar**.
4. Hovra över begränsningen i prioritetslistan.
5. Använd de tre lodräta punkterna och dra prioriteten till önskad plats i listan.
