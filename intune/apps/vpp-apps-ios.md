---
title: Hantera volyminköpta Apple-appar
titleSuffix: Microsoft Intune
description: Läs mer om synkronisering av volyminköpta appar från iOS och MacOs App Store i Microsoft Intune och hantering och spårning av deras användning.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff9a37a1dd815b6ec9d7522604796310e7f0b5ce
ms.sourcegitcommit: a7c35efb31c4efd816bd4aba29240013965aee92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2019
ms.locfileid: "73984112"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Så här hanterar du iOS- och MacOS-appar som har köpts via ett Apples volymköpsprogram med Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple låter dig köpa flera licenser för en app som du vill använda i företaget på iOS och MacOS-enheter. Om du köper flera exemplar så blir det lättare att effektivt hantera appar i ditt företag.

Microsoft Intune hjälper dig att hantera flera kopior av appar som du har köpt via det här programmet genom att:

- Rapportera licensinformation från App Store.
- Spåra antalet använda licenser.
- Hjälpa dig att inte installera fler exemplar av en app än du äger.

Det finns två metoder som du kan använda för att tilldela volyminköpta appar:

## <a name="device-licensing"></a>Enhetslicensiering

När du tilldelar en app till enheter används en applicens, och den förblir kopplad till den enhet som du tilldelade den till.

När du tilldelar volyminköpta appar till en enhet måste inte enhetens användare ange ett Apple-ID för att få åtkomst till butiken.

## <a name="user-licensing"></a>Användarlicensiering

När du tilldelar en app till en användare används en applicens för användaren och kopplas till denne. Appen kan köras på upp till 5 enheter som användaren äger (enhetsgränsen kontrolleras av Apple).

När du tilldelar användare en volyminköpt app måste varje användare ha ett giltigt och unikt Apple-ID för att få åtkomst till appbutiken.

Du kan dessutom synkronisera, hantera och tilldela böcker som du har köpt från Apples butik för volymköpsprogram (VPP) med Intune till iOS-enheter. Mer information finns i [Så här hanterar du e-böcker i iOS som du har köpt via ett volymköpsprogram](vpp-ebooks-ios.md).

## <a name="manage-volume-purchased-apps-for-ios-and-macos-devices"></a>Hantera volyminköpta appar för iOS- och MacOS-enheter

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps"></a>Stöder volyminköpta appar för Apples volymköpsprogram

Du kan köpa flera licenser för iOS- och MacOS-appar via [Apples volymköpsprogram för företag](https://www.apple.com/business/vpp/) eller [Apples volymköpsprogram för utbildning](https://volume.itunes.apple.com/us/store). Processen innebär bland annat att skapa ett Apple VPP-konto från Apples webbplats och ladda upp en Apple VPP-token till Intune.  Sedan kan du synkronisera volyminköpsinformationen med Intune och spåra din användning av appar som du köpt genom volyminköpsprogrammet.

### <a name="supports-business-to-business-volume-purchased-apps"></a>Har stöd för volyminköpta appar för samarbete mellan företag

Tredjepartsutvecklare kan dessutom distribuera appar privat till auktoriserade medlemmar i volyminköpsprogram för företag som anges i App Store Connect. Dessa medlemmar i volyminköpsprogram för företag kan logga in i appbutiken för volyminköpsprogram och köpa sina appar. Appar för volyminköpsprogram för företag som slutanvändaren köper synkroniseras med Intune-klienterna.

## <a name="before-you-start"></a>Innan du börjar
Innan du börjar måste du skaffa en VPP-token från Apple och ladda upp den till ditt Intune-konto. Du bör också känna till följande kriterier:

* Du kan associera flera 256 VPP-tokens med ditt Intune-konto.
* Om du tidigare har använt en VPP-token med en annan produkt måste du generera en ny som ska användas med Intune.
* Varje token är giltig i ett år.
* Som standard synkroniserar Intune med Apple VPP-tjänsten två gånger om dagen. Du kan starta en manuell synkronisering när som helst.
* Innan du börjar använda Apple VPP med Intune tar du bort alla befintliga VPP-användarkonton som skapats med andra MDM-leverantörer (hantering av mobila enheter). Av säkerhetsskäl synkroniserar Intune inte dessa användarkonton till Intune. Intune synkroniserar endast data från den Apple VPP-tjänst som skapades av Intune.
* Apples program för enhetsregistreringsprofil (DEP) automatiserar registrering för hantering av mobila enheter (MDM). Med hjälp av DEP kan du konfigurera företagsenheter utan att röra dem. Du kan registrera dig i DEP-programmet med hjälp av samma programagentkonto som du använde med Apples volymköpsprogram. Apples ID för distributionsprogram är unikt för program som anges på webbplatsen för [Apples distributionsprogram](https://deploy.apple.com) och kan inte användas för att logga in på Apple-tjänster som iTunes-butiken.
* När du tilldelar VPP-appar med hjälp av användarlicensieringsmodellen till användare eller enheter (med användartillhörighet), måste varje Intune-användare associeras med ett unikt Apple-ID eller en e-postadress när de accepterar Apples villkor på sin enhet.
* När du konfigurerar en enhet för en ny Intune-användare ser du till att konfigurera den med användarens unika Apple-ID eller e-postadress. Kombinationen av Intune-användare och Apple-ID eller e-postadress bildar ett unikt par och kan användas på upp till fem enheter.
* En VPP-token har endast stöd för användning på ett Intune-konto i taget. Återanvänd inte samma VPP-token för flera Intune-klienter.

>[!IMPORTANT]
>När du har importerat VPP-token i Intune ska du inte importera samma token till andra enhetshanteringslösningar. Om du gör det kan licenstilldelningen och användarposter gå förlorade.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Så här skaffar du och laddar upp en Apple VPP-token

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. I fönstret **Intune** väljer du **Klientappar** > **Apple VPP-token** under **Konfiguration**.
4. I fönstret med VPP-tokenlistan väljer du **Skapa**.
5. I fönstret **Skapa VPP-token** anger du följande information:
    - **VPP-tokenfil** – Om du inte redan gjort det, registrerar du dig för volymköpsprogram för företag eller programmet för utbildning. När du har registrerat dig laddar du ned Apple VPP-token för ditt konto och väljer det här.
    - **Apple-ID** – Ange Apple-ID för det konto som är associerat med inköpsprogrammet för volymen.
    - **Take control of token from another MDM** (Ta kontroll över token från en annan MDM) – Om du väljer **ja** för det här alternativet kan token omtilldelas till Intune från en annan MDM.
    - **Tokennamn** – Ett administrativt fält för att ange tokennamn.    
    - **Land/region** – Välj VPP-landskod/-regionkod.  Intune synkroniserar VPP-appar för alla språk från det angivna VPP-landet/-regionens App Store.
        > [!WARNING]  
        > När du byter land/region uppdateras apparnas metadata och butikens URL vid nästa synkronisering med Apple-tjänsten för appar som har skapats med denna token. Appen uppdateras inte om den inte finns i det nya landets/regionens butik.

    - **Typ av VPP-konto** – Välj mellan **Företag** eller **Utbildning**.
    - **Automatiska appuppdateringar** – Välj mellan **På** eller **Av** för att aktivera automatiska uppdateringar. När det är aktiverat identifierar Intune VPP-appuppdateringar i appbutiken och push-installerar dem automatiskt på enheten när den checkas in. Automatiska appuppdateringar för Apple VPP-appar uppdaterar endast de appar automatiskt som distribuerats med **krävd** installeringsavsikt. För appar som distribueras med **tillgänglig** installeringsavsikt genererar den automatiska uppdateringen ett statusmeddelande åt IT-administratören som informerar om att en ny version av appen är tillgänglig. Det här statusmeddelandet visas när du väljer appen, väljer Installationsstatus för enhet och kontrollerar statusinformationen. Dessutom ser användaren appen som inte installerad på Företagsportalen, även om en tidigare version av appen är installerad. I det här fallet kan användaren installera om appen genom att klicka på **Installera** på skärmen programinformation i företagsportalappen för att installera den nyare versionen av appen.

        > [!NOTE]
        > Automatiska appuppdateringar fungerar för både enhets- och användarlicensierade appar för iOS version 11.0 eller macOS 10.12 eller senare.

    - **Ge Microsoft behörighet att skicka information om både användare och enhet till Apple.** – Du måste välja **Jag accepterar** för att kunna fortsätta. Information om vilka data som Microsoft skickar till Apple finns i [Data som Intune skickar till Apple](~/protect/data-intune-sends-to-apple.md).

6. När du är klar väljer du **Skapa**.

Den token du önskar visas i fönstret med tokenlistan.

Du kan synkronisera data från Apple med Intune när som helst genom att välja **Synkronisera nu**.

## <a name="to-assign-a-volume-purchased-app"></a>Tilldela en volyminköpt app

1. I fönstret **Intune** väljer du **Klientappar** > **Appar** under **Hantera**.
2. I fönstret med applistan väljer du den app som du vill tilldela och väljer sedan **Tilldelningar**.
3. I fönstret ***Appnamn*** - **Tilldelningar** väljer du **Lägg till grupp** och i fönstret **Lägg till grupp** väljer du sedan en **Tilldelningstyp** och den Azure AD-användare eller de enhetsgrupper som du vill tilldela till appen.
5. Välj följande inställningar för varje grupp som du har valt:
    - **Typ** – Välj om appen ska vara **Tillgänglig** (slutanvändare kan installera appen från företagsportalen) eller **Obligatorisk** (slutanvändare får appen installerad automatiskt).
    - **Licenstyp** – Välj mellan **Användarlicensiering** eller **Enhetslicensiering**.
6. När du är klar väljer du **Spara**.


>[!NOTE]
>Tillgänglig distributionsavsikt stöds inte för enhetsgrupper – det är bara användargrupper som stöds. Listan över appar som visas är associerad med en token. Om du har en app som är associerad med flera VPP-token kan du se samma app visas flera gånger, en gång för varje token.

## <a name="end-user-prompts-for-vpp"></a>Slutanvändarprompt för VPP

Slutanvändaren får prompter för VPP-appinstallation i ett antal scenarier. Varje villkor förklaras i följande tabell:

| # | Scenario                                | Inbjudan till Apples VPP-program                              | Uppmaning vid appinstallation | Fråga efter Apple-ID |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – användarlicensierad                             | J                                                                                               | J                                           | J                                 |
| 2 | Corp – användarlicensierad (ej övervakad enhet)     | J                                                                                               | J                                           | J                                 |
| 3 | Corp – användarlicensierad (övervakad enhet)         | J                                                                                               | N                                           | J                                 |
| 4 | BYOD – enhetslicensierad                           | N                                                                                               | J                                           | N                                 |
| 5 | CORP – enhetslicensierad (ej övervakad enhet)                           | N                                                                                               | J                                           | N                                 |
| 6 | CORP – enhetslicensierad (övervakad enhet)                           | N                                                                                               | N                                           | N                                 |
| 7 | Helskärmsläge (övervakad enhet) – enhetslicensierad | N                                                                                               | N                                           | N                                 |
| 8 | Helskärmsläge (övervakad enheten) – användarlicensierad   | --- | ---                                          | ---                                |

> [!Note]  
> Vi rekommenderar inte att du tilldelar VPP-appar till enheter i helskärmsläge med VPP-användarlicensiering.

## <a name="revoking-app-licenses"></a>Återkalla applicenser

Du kan återkalla alla associerade iOS eller macOs VPP-applicenser (volyminköpsprogram) baserat på en viss enhet, användare eller app.  Men det finns vissa skillnader mellan iOS- och macOS-plattformarna. 

### <a name="revoking-app-licenses-on-ios"></a>Återkalla applicenser på iOS
Du kan meddela användare när en app inte längre är tilldelad till dem. Om du återkallar en applicens så avinstalleras inte den relaterade VPP-appen från enheten. Om du vill avinstallera en VPP-app och frigöra en applicens som är tilldelad till en användare eller enhet måste du ändra tilldelningsåtgärden till **Avinstallera**. När du tar bort en app som har tilldelats till en användare, frigör Intune användarens eller enhetens licens och avinstallerar appen från enheten. Du kan se antalet återkallade licenser vid noden **Licensierade appar** i arbetsbelastningen **App** i Intune. När en VPP-app har avinstallerats och applicensen har frigjorts kan du välja att tilldela applicensen till en annan användare eller enhet.


### <a name="revoking-app-licenses-on-macos"></a>Återkalla applicenser på macOS
Om du återkallar en applicens så avinstalleras inte den relaterade VPP-appen från enheten. När du återkallar en app som har tilldelats till en användare, frigör Intune användarens eller enhetens licens. MacOS-appen med återkallad licens fortsätter att vara användbar på enheten, men kan inte uppdateras förrän en licens har tilldelats till användaren eller enheten på nytt. Enligt Apple tas dessa appar bort efter en 30 dagar lång betänketid. Apple tillhandahåller dock inget sätt för Intune att ta bort appen med hjälp av tilldelningsåtgärden **Uninstall**. Men sedan kan du tilldela applicensen till en annan användare eller enhet.

>[!NOTE]
>Intune drar tillbaka användarlicensierade licenser för såväl iOS som macOS för VPP-appar när en anställd lämnar företaget och inte längre ingår i AAD-grupperna.

## <a name="deleting-vpp-tokens"></a>Ta bort VPP-token
<!-- 820879 -->  
Du kan ta bort en Apple-token för volyminköpsprogrammet (VPP) med hjälp av konsolen. Detta kan vara nödvändigt när du har dubblettinstanser av en VPP-token. Om du tar bort en token tas även alla associerade appar och tilldelningar bort. Men att ta bort en token innebär inte att applicenser frigörs eller att appar avinstalleras. 

>[!NOTE]
>Intune kan inte återkalla licenser för appar när en token har tagits bort. 

<!-- 820870 -->  
Om du vill återkalla en licens för alla VPP-appar för en specifik VPP-token, måste du först återkalla licenser för alla appar som är associerade med token och sedan ta bort token.

## <a name="renewing-app-licenses"></a>Förnya applicenser

Du kan förnya en Apple VPP-token genom att ladda ned en ny token från portalen för Apple Volume Purchase Program och sedan uppdatera befintlig token i Intune.

## <a name="deleting-a-vpp-app"></a>Ta bort en VPP-app

Du kan för närvarande inte ta bort en iOS VPP-app från Microsoft Intune.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Tilldela anpassade rollbehörigheter för VPP

Åtkomst till Apple VPP-token och VPP-appar kan kontrolleras oberoende av de behörigheter som tilldelats anpassade administratörsroller i Intune.

* För att låta en anpassad Intune-roll hantera Apple VPP-tokens under **Klientappar** > **Appar** ska du tilldela behörigheter till **mobilappar**.
* För att låta en anpassad Intune-roll hantera appar som har köpts med iOS VPP-tokens under **Klientappar** > **Appar** ska du tilldela behörigheter till **mobilappar**. 

## <a name="additional-information"></a>Ytterligare information

När en användare med en kvalificerande enhet försöker installera en volymköpsprogramapp på en enhet, ombeds användaren att gå med i Apples volymköpsprogram. Användaren måste gå med innan appinstallationen fortsätter. Inbjudan att gå med i Apples program för volyminköp kräver att användaren kan använda appen App Store på iOS- eller macOS-enheten. Om du har angett en princip för inaktivering av App Store-appen kommer den användarbaserade licensieringen för VPP-appar inte att fungera. Lösningen är att antingen tillåta App Store-appen genom att ta bort principen eller använda enhetsbaserad licensiering.

Apple tillhandahåller direkthjälp för att skapa och förnya VPP-token. Mer information finns i [Distribute content to your users with the Volume Purchase Program (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661) (Distribuera innehåll till användarna med volyminköpsprogrammet (VPP)) som en del av Apples dokumentation. 

Om **Assigned to external MDM** (Tilldelad till extern MDM) anges i Intune-portalen måste du (administratören) ta bort VPP-token från hantering av mobilenheter från tredje part innan VPP-token används i Intune.

## <a name="frequently-asked-questions"></a>Vanliga frågor och svar

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Hur lång tid tar det för portalen att uppdatera licensantalet när en app installeras eller tas bort från enheten?
Licensen bör vara uppdaterad inom några timmar efter installation eller avinstallation av en app. Observera att om slutanvändaren tar bort appen från enheten, är licensen fortfarande tilldelad till användaren eller enheten.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>Går det att överprenumerera på en app och i så fall när?
Ja. Intune-administratören kan överprenumerera på en app. Exempelvis om administratören köper 100 licenser för appen XYZ och sedan riktar appen till en grupp med 500 medlemmar. De första 100 medlemmarna (användare eller enheter) får den licens som tilldelats till dem, men resten av medlemmarna misslyckas vid licenstilldelningen.

### <a name="how-frequently-does-intune-sync-vpp-tokens-with-apple"></a>Hur ofta ska Intune synkronisera VPP-token med Apple?
Intune synkroniserar VPP-tokens och licenser två gånger om dagen med Apple. Intune-administratören kan starta en manuell synkronisering under **Klientappar** > **Apple VPP-token**.

## <a name="next-steps"></a>Nästa steg

Du hittar mer information i [Hur du övervakar appar](apps-monitor.md) som hjälper dig att övervaka apptilldelningar.
