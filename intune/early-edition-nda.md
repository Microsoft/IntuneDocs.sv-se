---
title: Tidig utgåva – Microsoft Intune
titlesuffix: ''
description: Tidig utgåva av Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 8cd32a7ec99064a36d58a5a714406659d9d16675
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2019
ms.locfileid: "55072447"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Den tidiga utgåvan för Microsoft Intune – Januari 2019

> [!Note]
> Sekretessavtalsmeddelande: Följande ändringar är under utveckling för Intune. Den här informationen har mycket begränsad spridning, i enlighet med sekretessavtalet. Sprid inte den här informationen vidare på sociala medier eller offentliga webbplatser, till exempel Twitter, UserVoice, Reddit och så vidare. 

Den **tidiga utgåvan** innehåller en lista med funktioner, som delas i enlighet med sekretessavtalet, som ingår i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte den här informationen på Twitter, UserVoice eller på något annat sätt med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

<!-- 1901 start -->


### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Distribution av online-licensierade Microsoft Store för företag-appar <!-- 1672660  -->
Du kommer att kunna tilldela nödvändiga online-licensierade Microsoft Store för företag-appar i kontexten för enheten. Genom att distribuera en Microsoft Store för företag-app på detta sätt, kan appen installeras för alla användare på enheten. Detta gäller endast för Windows 10 RS4+ desktop-enheter. Alternativet att installera i kontexten för enheten finns på sidan Tilldelning av klientappar för MSFB Online-licensierade appar.


<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Appdistribution för Android Enterprise APP-WE <!-- 1171203 -->
För Android-enheter i ett distributionsscenario med en appskyddsprincip utan registrering (APP-WE) kommer du att kunna använda hanterade Google Play för att distribuera store-appar och LOB-appar till användare. Mer specifikt kan IT-avdelningen kan ge slutanvändarna en app-katalog och installationsupplevelse som inte längre kräver att slutanvändare minskar säkerhetspositionen för sina enheter genom att tillåta installationer från okända källor. Dessutom kan det här distributionsscenariot ge en förbättrad slutanvändarupplevelse.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK stöder 256-bitars krypteringsnycklar <!-- 1832174 -->
Intune App SDK för Android använder 256-bitars krypteringsnycklar när kryptering har aktiverats av appskyddsprinciperna. SDK fortsätter att stödja 128-bitars nycklar för kompatibilitet med innehåll och appar som använder äldre versioner av SDK.


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Uppdatering av Intune-principers autentiseringsmetod och installation av företagsportalappen  <!-- 1927359 -->
På enheter som redan har registrerats via Installationsassistenten med någon av Apples metoder för registrering av företagsenheter, stöder Intune inte längre företagsportalen om den installeras manuellt av slutanvändarna från App Store. Den här ändringen gäller endast när du autentiserar med Apple-installationsassistenten under registreringen. Den här ändringen påverkar också bara iOS-enheter som registrerats via:  
* Apple configurator
* Apple Business Manager
* Apple School Manager
* Apples program för enhetsregistrering (DEP)

Om användare installerar företagsportalappen från App store och sedan försöker att registrera enheterna genom den, får de ett felmeddelande. Dessa enheter kommer förväntas att bara använda företagsportalen när den har skickats automatiskt av Intune under registreringen. Profiler för registrering i Intune i Azure-portalen kommer att uppdateras så att du kan ange hur enheter ska autentiseras och om de får företagsportalappen. Om du vill att dina DEP-enhetsanvändare ska ha företagsportalen behöver du ange dina preferenser i en registreringsprofil. Dessutom kommer skärmen **Identifiera din enhet** i företagsportalappen snart att bli föråldrad.  
För att installera företagsportalen på redan registrerade DEP-enheter, måste du gå till Intune > Klientappar, och skicka den som en hanterad app med konfigurationsprinciper för appar. Information om hur du utför dessa steg kommer att ges i framtida dokument.


### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrativa mallar finns i offentlig förhandsversion och flyttas till deras egna konfigurationsprofil <!-- 3322847 -->
Administrativa mallar i Intune (**Enhetskonfiguration** > **Administrationsmallar**) är för tillfället i privat förhandsvisning. I denna uppdatering: De administrativa mallarna innehåller ungefär 300 inställningar som kan hanteras i Intune. De här inställningarna fanns tidigare endast i redigeraren.
Administrativa mallar finns i offentlig förhandsversion, administrativa mallar flyttar från **Enhetskonfiguration** > **Administrationsmallar** till **Enhetskonfiguration** > **Profiler** >**Skapa profil** > i **Plattform**, välj  **Windows 10 och senare**i **Profiltyp**, välj **Administrationsmallar**.
Rapportering är aktiverad och gäller för: Windows 10 och senare

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Mörkt läge i Intune macOS-företagsportalen <!-- 3300524 -->
Nu stöder Intune macOS-företagsportalen mörkt läge för macOS. När du aktiverar mörkt läge på en macOS 10.14 +-enhet kommer företagsportalen att justera dess utseende till färger som speglar detta läge.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>APP-inställningar (App Protection Policy) för webbdata <!-- 2662995 -->
Principinställningarna för webbinnehåll på både Android och iOS-enheter kommer att uppdateras så att de blir bättre på att hantera både http- och https-länkar liksom dataöverföring via universella iOS-länkar och Android App-länkar.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-token som används av en annan MDM <!-- 1488946 -->
Intune identifierar och visar information om en token för volyminköpt Apple-program (VPP) används av både Intune och en annan MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Tillbakadragna enheter i instrumentpanelen för enhetsefterlevnad <!-- 1981119 -->
I en kommande uppdatering tas tillbakadragna enheter bort från instrumentpanelen för enhetsefterlevnad. Detta ändrar dina efterlevnadsnummer.


## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).



