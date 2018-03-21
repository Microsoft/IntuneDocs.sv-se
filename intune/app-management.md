---
title: "Vad är apphantering i Microsoft Intune?"
titlesuffix: 
description: "Lär dig grunderna om apphantering med Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/09/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 737c2900b2cdd57cb4dfc8373d06111a52e772b2
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="what-is-microsoft-intune-app-management"></a>Vad är apphantering i Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Med Microsoft Intune kan du som är IT-administratör hantera de mobilappar som företagets personal använder. Den här funktionen är ett tillägg till hanteringen av enheter och att skydda data. Som en del av funktionen är en av dina prioriteringar att se till att dina slutanvändare har åtkomst till de appar som de behöver för att utföra sitt arbete. Detta kan vara en utmaning eftersom:
- Det finns en mängd olika enhetsplattformar och apptyper.
- Du kan behöva hantera appar på både företagets enheter samt på användarnas egna enheter.
- Du måste se till att ditt nätverk och dina data förblir säkra.

Dessutom kanske du vill tilldela och hantera appar på enheter som inte har registrerats med Intune.

Intune erbjuder en mängd funktioner som hjälper dig att få de appar som du behöver, på de enheter som du önskar. Följande tabell innehåller en sammanfattning av apphanteringsfunktionerna. Nedanför tabellen är en startpunkt till din ökade förståelse för Microsoft Intune i Azure-portalen.

## <a name="app-management-capabilities-by-platform"></a>Apphanteringsfunktioner efter plattform

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8.1|Windows 10|
|Lägga till och tilldela appar till enheter och användare|Ja|Ja|Ja|Ja|
|Tilldela appar till enheter som inte registrerats med Intune|Ja|Ja|Nej|Nej|
|Använda principer för appkonfigurering för att styra appars startfunktion|Nej|Ja|Nej|Nej|
|Använda principer för etablering av mobilappar för att förnya utgångna appar|Nej|Ja|Nej|Nej|
|Skydda företagets data i appar med appskyddsprinciper|Ja|Ja|Nej|Nej<sup>1</sup>|
|Ta bort endast företagsdata från en installerad app (Selektiv rensning)|Ja|Ja|Ja|Ja|
|Övervaka apptilldelningar|Ja|Ja|Ja|Ja|
|Tilldela och spåra volyminköpta appar från en appbutik|Nej|Nej|Nej|Ja|
|Obligatorisk installation av appar på enheter (Obligatoriskt)<sup>2</sup>|Ja|Ja|Ja|Ja|
|Valfri installation på enheter från Företagsportalen (Tillgänglig installation)|Ja|Ja|Ja|Ja|
|Installera genväg till en app på webben (webblänk)|Ja|Ja|Ja|Ja|
|Verksamhetsspecifika appar|Ja|Ja|Nej|Ja|
|Appar från en butik|Ja|Ja|Ja|Ja|
|Uppdatera appar|Ja|Ja|Ja|Ja|

<sup>1</sup> Överväg att använda [Windows informationsskydd](windows-information-protection-configure.md) för att skydda appar på enheter som kör Windows 10.

<sup>2</sup>Gäller endast enheter som hanteras med Intune.

## <a name="how-to-get-started"></a>Komma igång

Du hittar de flesta apprelaterade sakerna i arbetsbelastningen **Mobilappar** som du kommer åt enligt följande:

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Mobilappar** på **Intune**-bladet.

    ![Arbetsbelastningen mobilappar](./media/apps-workload.png)

Informationen nedan motsvarar alternativen på bladet **Mobilappar**.

### <a name="manage"></a>Hantera
- **Appar** – Välj det här alternativet för att lägga till, visa, tilldela och övervaka apparna personalen använder. Mer information finns i följande artiklar:
    - [Lägga till appar](apps-add.md)
    - [Tilldela appar](apps-deploy.md)
    - [Övervaka appar](apps-monitor.md)
- **Konfigurationsprinciper för appar** – Konfigurationsprinciper för appar gör att du kan definiera inställningar som kan krävas när användaren kör en app. Mer information finns i följande artiklar:
    - [Appkonfigurationsprinciper för Intune](app-configuration-policies-overview.md)
        - [Konfigurationsprinciper för iOS-appar](app-configuration-policies-use-ios.md)
        - [Konfigurationsprinciper för Android-appar](app-configuration-policies-use-android.md)
- **Appskyddsprinciper** – Med appskyddsprinciper kan du koppla inställningar till en app för att skydda företagets data som den använder. Du kan till exempel begränsa möjligheterna för en app att kommunicera med andra appar eller kräva att användaren anger en PIN-kod för att få åtkomst till en företagsapp. Mer information finns i följande artikel:
    - [Appskyddsprinciper](app-protection-policies.md)
- **Appselektiv rensning** – Ta endast bort företagsdata från en användares enhet som du väljer. Mer information finns i följande artikel:
    - [Appselektiv rensning](apps-selective-wipe.md)
- **Etableringsprofiler för iOS-app** – iOS-appar innehåller en etableringsprofil och en kod som har signerats av ett certifikat. När certifikatet upphör att gälla kan du inte längre köra appen. Intune tillhandahåller verktyg för att tilldela en ny etableringsprofilprincip till enheter som har appar som snart upphör att gälla. Mer information finns i följande artikel:
    - [iOS-appetableringsprofiler](app-provisioning-profile-ios.md)

Mer information finns i [Hantera appar](app-management.md).

### <a name="monitor"></a>Övervakare
- **Applicenser** – Visa, tilldela och övervaka volyminköpta appar från appbutiker. Mer information finns i följande artiklar:
    - [Volyminköpsprogram för iOS-appar (VPP)](vpp-apps-ios.md)
    - [Volyminköpta appar från Microsoft Store för företag](windows-store-for-business.md)
- **Identifierade appar** – Visar alla appar som har tilldelats av Intune och installerats på en enhet.
- **Appinstallationsstatus** – Visar status för en apptilldelning som du skapat.
- **Användarstatus för appskydd** – Visar status för en skyddsprincip hos en användare som du väljer.
- **Granskningsloggar** – Visar den apprelaterade Intune-aktivitet som gjorts av alla IT-administratörer.

Mer information finns i [Övervaka appar](apps-monitor.md).

### <a name="setup"></a>Setup
- **iOS VPP-token** – Tillämpa och visa dina licenser för iOS Volume Purchase Program (VPP).
    - [Volyminköpta iOS-appar](vpp-apps-ios.md)
- **Windows företagscertifikat** – Använd eller visa status för ett kodsigneringscertifikat som används för att distribuera branschspecifika appar till dina hanterade Windows-enheter.
- **Windows Symantec-certifikat** – Använd eller visa status för ett Symantec-kodsigneringscertifikat som behövs för att distribuera XAP- och WP8.x appx-filer till Windows 10 Mobile-enheter.
- **Microsoft Store för företag** – Installationsintegrering till Microsoft Store för företag. När du gjort detta kan du synkronisera inköpta program till Intune, tilldela dem och spåra användningen av licenser. Mer information finns i följande artikel:
    - [Volyminköpta appar från Microsoft Store för företag](windows-store-for-business.md)
- **Windows-nycklar för separat inläsning** – Du kan lägga till en Windows-nyckel för separat inläsning som kan användas för att installera en app direkt till enheter i stället för att publicera och hämta appen från Windows store. Mer information finns i följande artikel:
    - [Separat inläsning av en Windows-app](app-sideload-windows.md)
- **Anpassa företagsportalen.** – Anpassa företagsportalen enligt ert varumärke. Mer information finns i följande artikel:
    - [Företagsportalkonfiguration](company-portal-app.md)
- **Appkategorier** – Lägg till, fäst och ta bort appkategorinamn.
- **Android for Work** – Godkänn och synkronisera de appar som du har godkänt för ditt företag. Mer information finns i följande artikel:
    - [Android for Work-appar](apps-add-android-for-work.md)

### <a name="help-and-support"></a>Hjälp och support
- **Hjälp och support** – Felsök, begär support eller visa Intune-status. Mer information finns i följande artikel:
    - [Felsökning av problem](help-desk-operators.md)

## <a name="next-steps"></a>Nästa steg

- [Lägga till en app i Microsoft Intune](apps-add.md)
