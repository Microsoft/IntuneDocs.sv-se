---
title: Vad är apphantering i Microsoft Intune?
titleSuffix: ''
description: Läs mer om klientappens hanteringsfunktioner per plattform i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34807edabf99a107c259fdfae5e43db18084fb67
ms.sourcegitcommit: 219bbbfb44eba70ac2b751970d8b4b778cd28416
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/04/2019
ms.locfileid: "59569070"
---
# <a name="what-is-microsoft-intune-app-management"></a>Vad är apphantering i Microsoft Intune?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Som IT-administratör kan du använda Microsoft Intune för att hantera klientappar som ditt företags personal använder. Den här funktionen är ett tillägg till hanteringen av enheter och att skydda data. En av en administratörs prioriteringar är att säkerställa att användarna har åtkomst till appar som de behöver för att utföra sitt arbete. Detta mål kan vara en utmaning eftersom:
- Det finns en mängd olika enhetsplattformar och apptyper.
- Du kan behöva hantera appar på både företagets enheter samt på användarnas personalenheter.
- Du måste se till att ditt nätverk och dina data förblir säkra.

Dessutom kanske du vill tilldela och hantera appar på enheter som inte har registrerats med Intune.

Intune erbjuder en mängd funktioner som hjälper dig att få de appar som du behöver, på de enheter som du önskar köra dem på. Följande tabell innehåller en sammanfattning av apphanteringsfunktionerna: 

## <a name="app-management-capabilities-by-platform"></a>Apphanteringsfunktioner efter plattform

|  | Android | iOS | macOS | Windows 10 | Windows Phone 8.1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| Lägga till och tilldela appar till enheter och användare | Ja | Ja | Ja | Ja | Ja |
| Tilldela appar till enheter som inte registrerats i Intune | Ja | Ja | Nej | Nej | Nej |
| Använda principer för appkonfigurering som styr apparnas startfunktion | Ja | Ja | Nej | Nej | Nej |
| Använda principer för etablering av mobilappar för att förnya utgångna appar | Nej | Ja | Nej | Nej | Nej |
| Skydda företagets data i appar med appskyddsprinciper | Ja | Ja | Nej | Nej1 | Nej |
| Ta bort endast företagsdata från installerade appar (selektiv rensning) | Ja | Ja | Nej | Ja | Ja |
| Övervaka apptilldelningar | Ja | Ja | Ja | Ja | Ja |
| Tilldela och spåra volyminköpta appar från en appbutik | Nej | Nej | Nej | Ja | Nej |
| Obligatorisk installation av appar på enheter (obligatoriskt)2 | Ja | Ja | Ja | Ja | Ja |
| Valfri installation på enheter från Företagsportalen (tillgänglig installation) | Ja | Ja | Ja | Ja | Ja |
| Installera genvägar till appar på webben (webblänk) | Ja | Ja | Ja | Ja | Ja |
| Verksamhetsspecifika appar | Ja | Ja | Ja | Ja | Nej |
| Appar från en butik | Ja | Ja | Nej | Ja | Ja |
| Uppdatera appar | Ja | Ja | Nej | Ja | Ja |

<sup>1</sup> Överväg att använda [Windows informationsskydd](windows-information-protection-configure.md) för att skydda appar på enheter som kör Windows 10.

<sup>2</sup> Gäller enheter som hanteras av Intune endast.

## <a name="get-started"></a>Kom igång

Du hittar den mesta app-relaterade informationen i arbetsbelastningen **Klientappar** som du kan komma åt genom att göra följande:

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**.  
    Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Microsoft Intune** väljer du **Klientappar**.

    ![Välj arbetsbelastningen ”Klientappar”](./media/apps-workload.png)

I följande fyra avsnitt beskrivs alternativ som är tillgängliga i fönstret **Klientappar**.

### <a name="manage"></a>Hantera
- **Appar**: Välj det här alternativet för att lägga till, visa, tilldela och övervaka apparna som personalen använder. Mer information finns i:
    - [Lägga till appar](apps-add.md).
    - [Tilldela appar](apps-deploy.md).
    - [Övervaka appar](apps-monitor.md).
- **Appkonfigurationsprinciper**: Välj det här alternativet om du vill ange inställningar som kan krävas när en användare kör en app. Mer information finns i:
    - [Appkonfigurationsprinciper för Intune](app-configuration-policies-overview.md).
        - [Konfigurationsprinciper för iOS-appar](app-configuration-policies-use-ios.md).
        - [Konfigurationsprinciper för Android-appar](app-configuration-policies-use-android.md).
- **Appskyddsprinciper**: Välj det här alternativet för att koppla inställningar till en app och skydda de data som företaget använder. Du kan till exempel begränsa möjligheterna för en app att kommunicera med andra appar eller du kan kräva att användaren anger en PIN-kod för att få åtkomst till en företagsapp. Mer information finns i:
    - [Appskyddsprinciper](app-protection-policies.md).
- **Selektiv radering av app**: Välj det här alternativet för att ta bort enbart företagsdata från en vald användares enhet. Mer information finns i:
    - [Appselektiv rensning](apps-selective-wipe.md).
- **Etableringsprofiler för iOS-app**: iOS-appar innehåller en etableringsprofil och en kod som har signerats av ett certifikat. När certifikatet upphör att gälla kan du inte längre köra appen. Intune tillhandahåller verktyg för att tilldela en ny etableringsprofilprincip till enheter som har appar som snart upphör att gälla. Mer information finns i:
    - [iOS-appetableringsprofiler](app-provisioning-profile-ios.md).

Mer information om det här avsnittet finns [Hantera appar](app-management.md).

### <a name="monitor"></a>Övervakare
- **Applicenser**: Visa, tilldela och övervaka volyminköpta appar från appbutiker. Mer information finns i:
    - [Volyminköpsprogram för iOS-appar (VPP)](vpp-apps-ios.md).
    - [Volyminköpta appar från Microsoft Store för företag](windows-store-for-business.md).
- **Identifierade appar**: Visa appar som har tilldelats av Intune eller installerats på en enhet. Mer information finns i [Visa enhetsinformation med Microsoft Intune](device-inventory.md).
- **Status för appinstallation**: Visa status för en apptilldelning som du har skapat. Mer information finns i [Övervaka appinformation och tilldelningar med Microsoft Intune](apps-monitor.md#device-and-user-status-graphs).
- **Appskyddsstatus**: Visa status för en appskyddsprincip hos en användare som du väljer.
- **Granskningsloggar**: Visa den Intune-apprelaterade aktiviteten för alla IT-administratörer.

Mer information om det här avsnittet finns [Övervaka appar](apps-monitor.md).

### <a name="set-up"></a>Konfigurera
- **iOS VPP-token**: Tillämpa och visa dina licenser för iOS volymköpsprogram (VPP). Mer information finns i:
    - [Volyminköpta iOS-appar](vpp-apps-ios.md)
- **Windows företagscertifikat**: Tillämpa eller visa status för ett kodsigneringscertifikat som används för att distribuera verksamhetsspecifika appar till dina hanterade Windows-enheter.
- **Windows Symantec-certifikat**: Tillämpa eller visa status för ett Symantec-kodsigneringscertifikat som behövs för att distribuera XAP- och WP8.x appx-filer till Windows 10 Mobile-enheter.
- **Microsoft Store för företag**: Konfigurera integration till Microsoft Store för företag. När du gjort detta kan du synkronisera inköpta program till Intune, tilldela dem och spåra användningen av licenser. Mer information finns i:
    - [Volyminköpta appar från Microsoft Store för företag](windows-store-for-business.md).
- **Windows-nycklar för separat inläsning**: Lägg till en Windows-nyckel för separat inläsning som kan användas för att installera en app direkt till enheter, i stället för att appen publiceras och hämtas från Windows Store. Mer information finns i:
    - [Separat inläsning av en Windows-app](app-sideload-windows.md).
- **Logotyp för företagsportal**: Anpassa företagsportalen efter ert varumärke. Mer information finns i:
    - [Företagsportalkonfiguration](company-portal-app.md).
- **Appkategorier**: Lägg till, fäst och ta bort appkategorinamn.
- **Android-arbetsprofil**: Godkänn och synkronisera de appar som du har godkänt för ditt företag. Mer information finns i:
    - [Android Work-profilappar](apps-add-android-for-work.md).

### <a name="help-and-support"></a>Hjälp och support
- **Hjälp och support**: Felsök, begär support eller visa Intunes status. Mer information finns i:
    - [Felsökning av problem](help-desk-operators.md).

## <a name="next-steps"></a>Nästa steg

- [Lägg till en app i Microsoft Intune](apps-add.md)
