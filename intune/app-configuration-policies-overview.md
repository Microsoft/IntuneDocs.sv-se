---
title: Appkonfigurationsprinciper för Microsoft Intune
titleSuffix: ''
description: Läs om hur du använder appkonfigurationsprinciper på en iOS- eller Android-enhet i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cda0453009855d96e7c13e170ba908479a0773ea
ms.sourcegitcommit: 513e805bbea8bf652c2901dfc5460e34946077df
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160528"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Appkonfigurationsprinciper för Microsoft Intune

Appkonfigurationsprinciper kan hjälpa dig att förhindra problem med konfiguration av appar eftersom du kan tilldela konfigurationsinställningar till en princip som tilldelas till slutanvändare innan de kör appen. Inställningarna anges sedan automatiskt när appen konfigureras på slutanvändarnas enheter, och slutanvändarna behöver då inte vidta några åtgärder. Konfigurationsinställningarna är unika för varje app. 

Du kan skapa och använda appkonfigurationsprinciper för att ge konfigurationsinställningar för både iOS-appar och Android-appar. Med dessa konfigurationsinställningar kan en app anpassas enligt [branschstandarden](https://www.appconfig.org/) för konfiguration och hantering av appar. Inställningarna för konfigurationsprincipen används när appen söker efter inställningarna, oftast första gången appen körs. 

Till exempel kan en appkonfigurationsinställning kräva att du anger några av de följande uppgifterna:

- Ett anpassat portnummer
- Språkinställningar
- Säkerhetsinställningar
- Anpassade inställningar, t.ex. en företagslogotyp

Om slutanvändarna skulle ange inställningarna i stället kan de göra detta felaktigt. Appkonfigurationsprinciper kan bidra till enhetlighet i ett företag och minska samtal till supporten från slutanvändare som försöker konfigurera inställningar på egen hand. Med hjälp av appkonfigurationsprinciper kan införandet av nya appar bli enklare och snabbare.

De tillgängliga konfigurationsparametrarna bestäms slutligen av appens utvecklare. Dokumentation från programleverantören bör granskas i syfte att kontrollera om en app stöder konfiguration och vilka konfigurationer som är tillgängliga. För vissa program fyller Intune i de tillgängliga konfigurationsinställningarna. 

> [!NOTE]
> I den hanterade Google Play Store markeras appar som stöder konfiguration därefter:
> 
> ![Skärmbild av en konfigurerad app](./media/app-configuration-policy-overview/configured-app.png)
>
> Du ser bara appar från [hanterad Google Play Store](https://play.google.com/work), inte [Google Play Store](https://play.google.com/store/apps), när du använder hanterade enheter som registreringstyp för Android-enheter. Hanterad Google Play Store, som även kallas Android for Work (AfW) och Android Enterprise, är de appar i arbetsprofilen som innehåller de appversioner som stöder appkonfiguration.

Du kan tilldela en appkonfigurationsprincip till en grupp med slutanvändare och enheter med hjälp av en kombination av [tilldelningar som inkluderar och exkluderar](apps-inc-exl-assignments.md). När du lägger till en appkonfigurationsprincip kan du ange tilldelningar för den. När du anger tilldelningar för principen kan du välja att inkludera och exkludera de [grupper](groups-add.md) av slutanvändare som principen gäller för. När du väljer att inkludera en eller flera grupper kan du välja att utse specifika grupper att inkludera eller välja inbyggda grupper. Inbyggda grupper innefattar **Alla användare**, **Alla enheter** samt **Alla användare + alla enheter**.

Du har två alternativ vad gäller användning av appkonfigurationsprinciper med Intune:
- **Hanterade enheter** – enheten hanteras av Intune som MDM-leverantör (hantering av mobila enheter). Appen måste vara utformad för att stödja appkonfigurationen.
- **Hanterade appar** – en app som har utvecklats för att integrera Intune App SDK. Detta kallas hantering av mobilprogram utan registrering ([MAM-WE](app-management.md#mobile-application-management-mam-basics)). Du kan även omsluta en app för att implementera och stödja Intune App SDK. Mer information om omslutning av en app finns i [Förbereda verksamhetsspecifika appar för appskyddsprinciper](apps-prepare-mobile-application-management.md).

    > [!NOTE]
    > Intune-hanterade appar checkar in med ett intervall på 30 minuter för status för Intune-appkonfigurationsprincip när de distribueras tillsammans med en Intune-appskyddsprincip. Om en Intune-appskyddsprincip inte är tilldelad till användaren är incheckningsintervallet för Intune-appkonfigurationsprincip angett till 720 minuter.

## <a name="apps-that-support-app-configuration"></a>Appar som stöder appkonfiguration

### <a name="managed-devices"></a>Hanterade enheter
Du kan använda appkonfigurationsprinciper för appar som stöder det. För att stödja appkonfiguration i Intune måste appar ha skrivits för att stödja användningen av appkonfigurationer enligt definitionen från [AppConfig-communityn](https://www.appconfig.org/members). Kontakta appleverantören om du vill ha mer information.

### <a name="managed-apps"></a>Hanterade appar
Du kan förbereda dina verksamhetsspecifika appar genom att antingen integrera [Intune App SDK](app-sdk.md) i appen eller genom att omsluta appen när den har utvecklats med hjälp av [Intune-verktyget för omslutning av appar](apps-prepare-mobile-application-management.md). Intune App SDK syftar till att minimera den mängd kodändringar i programmet som apputvecklare behöver göra. Mer information finns i [Översikt över Intune App SDK](app-sdk.md). En jämförelse mellan Intune App SDK och Intune-verktyget för omslutning av appar finns i [Förbereda verksamhetsspecifika appar för appskyddsprinciper](apps-prepare-mobile-application-management.md#feature-comparison).

Val av **Hanterade appar** som **Enhetsregistreringstyp** syftar specifikt på appar som konfigureras av Intune-konfigurationsprinciper på en enhet som inte är registrerad i enhetshantering, medan **Hanterade enheter** gäller för appar som distribueras via MDM-kanalen och därmed hanteras av Intune. Välj lämpligt alternativ baserat på dessa beskrivningar. 

![Enhetsregistreringstyp](./media/app-configuration-policy-overview/device-enrollment-type.png)

> [!NOTE]
> För appar med flera identiteter, till exempel Microsoft Outlook, kan användarinställningar beaktas. Prioriterad inkorg, till exempel, respekterar användarinställningen och ändrar inte konfigurationen. Andra parametrar gör det möjligt att kontrollera huruvida en användare kan ändra inställningen. Mer information finns i [Distribuera appkonfigurationsinställningar för Outlook för iOS och Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Verifiera den tillämpade appkonfigurationsprincipen

Du kan verifiera appkonfigurationsprincipen med följande tre metoder:

   1. Synligt på enheten. Har den avsedda appen det beteende som tillämpats i appkonfigurationsprincipen?
   2. Via diagnostikloggar (se avsnittet Diagnostikloggar nedan).
   3. I Intune-portalen. Avsnittet **Övervakare** i en princip kan ge relevant status:

      ![Första skärmbilden av enhetens installationsstatus](./media/app-configuration-policy-overview/device-install-status-1.png)

      ![Andra skärmbilden av enhetens installationsstatus](./media/app-configuration-policy-overview/device-install-status-2.png)

      Under **Intune** -> **enheter** -> **Alla enheter** på vänster sida av skärmen visar dessutom alternativet **Appkonfiguration** alla tilldelade principer och deras tillstånd:

      ![Skärmbild av appkonfiguration](./media/app-configuration-policy-overview/app-configuration.png)

## <a name="graph-api-support-for-app-configuration"></a>Graph API har stöd för appkonfiguration

Du kan använda Graph API för att utföra de här appkonfigurationsuppgifterna. Mer information finns i [Graph API-referens för MAM-riktad konfiguration](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="troubleshooting"></a>Felsökning

### <a name="using-logs-to-show-a-configuration-parameter"></a>Använda loggar för att visa en konfigurationsparameter
När loggarna visar en konfigurationsparameter som har bekräftats tillämpas men inte verkar fungera kan det finnas ett problem med konfigurationens implementering av apputvecklaren. Om du kontaktar apputvecklaren först eller läser deras kunskapsbas kan du undvika att behöva ringa Microsofts support. Om det är problem med hur konfigurationen hanteras i en app måste det åtgärdas i en framtida uppdaterad version av den appen.

## <a name="next-steps"></a>Nästa steg

### <a name="managed-devices"></a>Hanterade enheter

- Lär dig hur du använder appkonfiguration med iOS-enheter.  Se [Lägg till konfigurationsprinciper för hanterade iOS-mobilappar](app-configuration-policies-use-ios.md).
- Lär dig hur du använder appkonfiguration med Android-enheter.  Se [Lägg till konfigurationsprinciper för hanterade Android-enheter](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Hanterade appar

- Lär dig hur du använder appkonfiguration med hanterade appar. Se [Lägg till appkonfigurationsprinciper för hanterade appar utan enhetsregistrering](app-configuration-policies-managed-app.md).
