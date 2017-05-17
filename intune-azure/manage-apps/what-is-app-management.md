---
title: "Vad är apphantering | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Använd informationen i det här avsnittet för att lära dig grunderna om apphantering med Microsoft Intune"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 430329939c99fefcc2ace551545e079f874e83cb
ms.contentlocale: sv-se
ms.lasthandoff: 05/10/2017


---

# <a name="what-is-microsoft-intune-app-management"></a>Vad är apphantering i Microsoft Intune?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Som IT-administratör kommer du troligen att ha uppgiften att se till att slutanvändarna har åtkomst till de appar som de behöver för att utföra sitt arbete. Detta kan vara en utmaning eftersom:
- Det finns en mängd olika enhetsplattformar och apptyper.
- Du kan behöva hantera appar på företagets enheter liksom på användarnas egna enheter.
- Du behöver göra allt detta och ska samtidigt se till att nätverket och dina data förblir säkra. 

Dessutom kanske du vill tilldela och hantera appar på enheter som inte har registrerats med Intune.

Intune erbjuder en mängd funktioner som hjälper dig att få de appar som du behöver, på de enheter som du önskar.

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
|Installera genväg till en app på webben (webbklipp)|Ja|Ja|Ja|Ja|
|Verksamhetsspecifika appar|Ja|Ja|Nej|Nej|
|Appar från en butik|Ja|Ja|Ja|Ja|
|Uppdatera appar|Ja|Ja|Ja|Ja|

<sup>1</sup> Fundera på att använda [Windows Information Protection]../configure-devices/how-to-configure-windows-information-protection.md) för att skydda appar på enheter som kör Windows 10.

<sup>2</sup>Gäller endast enheter som hanteras med Intune.


## <a name="how-to-get-started"></a>Komma igång

Du hittar de flesta apprelaterade sakerna i arbetsbelastningen **Mobilappar** som du kommer åt enligt följande:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.

    ![Arbetsbelastningen mobilappar](./media/apps-workload.png)

### <a name="manage"></a>Hantera
- **Appar** – Det är här du lägger till, tilldelar och övervakar de flesta av dina appar. 
    - [Lägga till appar](add-apps.md)
    - [Tilldela appar](deploy-apps.md)
    - [Övervakning av appar](monitor-apps.md)
- **Konfigurationsprinciper för appar** – Konfigurationsprinciper för appar gör att du kan definiera inställningar som kan krävas när användaren kör en app. Mer information finns i:
    - [Konfigurationsprinciper för appar](app-configuration-policies.md)
- **Appskyddsprinciper** – Låter dig koppla inställningar till en app för att skydda företagets data som den använder. Du kan till exempel begränsa möjligheterna för en app att kommunicera med andra appar eller kräva att användaren anger en PIN-kod för att få åtkomst till en företagsapp.
    - [Appskyddsprinciper](app-protection-policies.md)
- **Appselektiv rensning** – Ta endast bort företagsdata från en användares enhet som du väljer.
    - [Appselektiv rensning](app-selective-wipe.md)
- **Etableringsprofiler för iOS** – iOS-appar innehåller en etableringsprofil och en kod som har signerats av ett certifikat. När certifikatet upphör att gälla kan du inte längre köra appen. Intune tillhandahåller verktyg för att tilldela en ny etableringsprofilprincip till enheter som har appar som snart upphör att gälla.
    - [iOS-appetableringsprofiler](ios-app-provisioning-profile.md)

### <a name="monitor"></a>Övervakare
- **Licensierade appar** – Visa, tilldela och övervaka volyminköpta appar från appbutiker.
    - [Volyminköpta appar från Windows Store för företag](wsfb-apps.md)
- **Identifierade appar** – Visar alla appar som har tilldelats av Intune och installerats på en enhet.
- **Appinstallationsstatus** – Visar status för en apptilldelning som du skapat.
- **Användarstatus för appskydd** – Visar status för en skyddsprincip hos en användare som du väljer.

Mer information finns i [Övervakning av appar](monitor-apps.md)

### <a name="setup"></a>Setup
<!--- **iOS VPP Tokens**
    - [iOS volume-purchased apps](ios-vpp-apps.md) --->
- **Windows Store för företag** – Installationsintegrering till Windows Store för företag. När du gjort detta kan du synkronisera inköpta program till Intune, tilldela dem och spåra användningen av licenser. 
    - [Volyminköpta appar från Windows Store för företag](wsfb-apps.md)
- **Anpassa företagsportalen.** – Anpassa företagsportalen enligt ert varumärke. 
    - [Företagsportalkonfiguration](company-portal-app.md)

