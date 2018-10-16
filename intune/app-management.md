---
title: Vad är apphantering i Microsoft Intune?
titlesuffix: ''
description: Lär dig grunderna om apphantering med Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 99d217c2d1960a1ca163bf697bfbd28e5406b58f
ms.sourcegitcommit: f69f2663ebdd9c1def68423e8eadf30f86575f7e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2018
ms.locfileid: "49075854"
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
| Använda principer för appkonfigurering som styr apparnas startfunktion | Nej | Ja | Nej | Nej | Nej |
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
- **Konfigurationsprinciper**: Välj det här alternativet om du vill definiera inställningar som kan krävas när en användare kör en app. Mer information finns i:
    - [Appkonfigurationsprinciper för Intune](app-configuration-policies-overview.md).
        - [Konfigurationsprinciper för iOS-appar](app-configuration-policies-use-ios.md).
        - [Konfigurationsprinciper för Android-appar](app-configuration-policies-use-android.md).
- **Appskyddsprinciper**: Välj det här alternativet för att koppla inställningar till en app och skydda företagets data som den använder. Du kan till exempel begränsa möjligheterna för en app att kommunicera med andra appar eller du kan kräva att användaren anger en PIN-kod för att få åtkomst till en företagsapp. Mer information finns i:
    - [Appskyddsprinciper](app-protection-policies.md).
- **Selektiv rensning för app**: Välj det här alternativet för att endast ta bort företagsdata från en vald användares enhet. Mer information finns i:
    - [Appselektiv rensning](apps-selective-wipe.md).
- **Etableringsprofiler för iOS-app**: iOS-appar innehåller en etableringsprofil och en kod som har signerats av ett certifikat. När certifikatet upphör att gälla kan du inte längre köra appen. Intune tillhandahåller verktyg för att tilldela en ny etableringsprofilprincip till enheter som har appar som snart upphör att gälla. Mer information finns i:
    - [iOS-appetableringsprofiler](app-provisioning-profile-ios.md).

Mer information om det här avsnittet finns [Hantera appar](app-management.md).

### <a name="monitor"></a>Övervakare
- **Applicenser**: Visa, tilldela och övervaka volyminköpta appar från appbutiker. Mer information finns i:
    - [Volyminköpsprogram för iOS-appar (VPP)](vpp-apps-ios.md).
    - [Volyminköpta appar från Microsoft Store för företag](windows-store-for-business.md).
- **Identifierade appar**: Visa alla appar som har tilldelats av Intune och installerats på en enhet. Mer information finns i [Övervaka appinformation och tilldelningar med Microsoft Intune](apps-monitor.md#device-and-user-status-graphs).
- **Appinstallationsstatus**: Visa status för en apptilldelning som du skapat. Mer information finns i [Övervaka appinformation och tilldelningar med Microsoft Intune](apps-monitor.md#device-and-user-status-graphs).
- **Användarstatus för appskydd** : Visa status för en skyddsprincip hos en användare som du väljer.
- **Granskningsloggar**: Visa den Intune app-relaterade aktiviteten för alla IT-administratörer.

Mer information om det här avsnittet finns [Övervaka appar](apps-monitor.md).

### <a name="set-up"></a>Konfigurera
- **iOS VPP-token**: Tillämpa och visa dina licenser för iOS Volume Purchase Program (VPP). Mer information finns i:
    - [Volyminköpta iOS-appar](vpp-apps-ios.md)
- **Windows företagscertifikat**: Använd eller visa status för ett kodsigneringscertifikat som används för att distribuera branschspecifika appar till dina hanterade Windows-enheter.
- **Windows Symantec-certifikat**: Använd eller visa status för ett Symantec-kodsigneringscertifikat som behövs för att distribuera XAP- och WP8.x appx-filer till Windows 10 Mobile-enheter.
- **Microsoft Store för företag**: Installationsintegrering till Microsoft Store för företag. När du gjort detta kan du synkronisera inköpta program till Intune, tilldela dem och spåra användningen av licenser. Mer information finns i:
    - [Volyminköpta appar från Microsoft Store för företag](windows-store-for-business.md).
- **Windows-nycklar för separat inläsning**: Lägg till en Windows-nyckel för separat inläsning som kan användas för att installera en app direkt till enheter i stället för att publicera och hämta appen från Windows store. Mer information finns i:
    - [Separat inläsning av en Windows-app](app-sideload-windows.md).
- **Anpassa företagsportalen.**: Anpassa företagsportalen enligt ert varumärke. Mer information finns i:
    - [Företagsportalkonfiguration](company-portal-app.md).
- **Appkategorier**: Lägg till, fäst och ta bort appkategorinamn.
- **Android-arbetsprofil**: Godkänn och synkronisera de appar som du har godkänt för ditt företag. Mer information finns i:
    - [Android Work-profilappar](apps-add-android-for-work.md).

### <a name="help-and-support"></a>Hjälp och support
- **Hjälp och support**: Felsök, begär support eller visa Intune-status. Mer information finns i:
    - [Felsökning av problem](help-desk-operators.md).

## <a name="next-steps"></a>Nästa steg

- [Lägg till en app i Microsoft Intune](apps-add.md)
