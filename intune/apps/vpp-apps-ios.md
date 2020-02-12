---
title: Hantera volyminköpta Apple-appar
titleSuffix: Microsoft Intune
description: Läs mer om synkronisering av volyminköpta appar från iOS och MacOs App Store i Microsoft Intune och hantering och spårning av deras användning.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/17/2019
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
ms.openlocfilehash: d965ac35719d809ab922d28f76dec1754e9a4c6b
ms.sourcegitcommit: 9b29478f815e10c46c8030abe0146d601ce0e28c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051634"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Så här hanterar du iOS- och MacOS-appar som har köpts via ett Apples volymköpsprogram med Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple låter dig köpa flera licenser för en app som du vill använda i din organisation på iOS-och macOS-enheter med hjälp av [Apple Business Manager](https://business.apple.com/) eller [Apple School Manager](https://school.apple.com/). Sedan kan du synkronisera volyminköpsinformationen med Intune och spåra din användning av appar som du köpt genom volyminköpsprogrammet. Genom att köpa app-licenser kan du effektivt hantera appar i företaget och behålla ägarskapet och kontrollen över de appar du köpt. 

Microsoft Intune hjälper dig att hantera appar som du har köpt via det här programmet genom att:

- Synkronisera platstokens som du laddar ned från Apple Business Manager.
- Spåra hur många licenser som är tillgängliga och har använts för köpta appar.
- Hjälper dig att installera det antal som motsvarar det antal licenser som du äger.

Du kan dessutom synkronisera, hantera och tilldela böcker som du har köpt från Apple Business Manager med Intune till iOS-enheter. Mer information finns i [Så här hanterar du e-böcker i iOS som du har köpt via ett volymköpsprogram](vpp-ebooks-ios.md).

## <a name="what-are-location-tokens"></a>Vad är en platstoken?
En platstoken kallas även VPP-token. Den här typen av token används för att tilldela och hantera licenser som köpts med hjälp av Apple Business Manager. Innehållshanterare kan köpa och associera licenser med de platstoken som de har behörighet till i Apple Business Manager. Dessa platstoken laddas sedan ned från Apple Business Manager och laddas upp i Microsoft Intune. Microsoft Intune stöder överföring av flera platstoken per klient. Varje token är giltig i ett år.

## <a name="how-are-purchased-apps-licensed"></a>Hur licensieras köpta appar?
Grupper kan tilldelas köpta appar med två typer av licenser som Apple erbjuder för iOS- och macOS-enheter.

|   | Enhetslicensiering | Användarlicensiering |
|-----|------------------|----------------|
| **App Store-inloggning** | Krävs inte. | Varje slutanvändare måste använda ett unikt Apple-ID när hen uppmanas att logga in till App Store. |
| **Enhetskonfigurationen blockerar åtkomst till App Store** | Appar kan installeras och uppdateras med hjälp av företagsportalen. | Inbjudan att ansluta till Apple VPP kräver åtkomst till App Store. Om du har angett en princip för att inaktivera App Store, så fungerar inte användarlicensieringen för VPP-appar. |
| **Automatisk appuppdatering** | Enligt Intune-administratörens konfiguration av Apple VPP tokeninställningarna, där appens **tilldelningstyp** **måste anges**. <br> <br> Om **tilldelningstypen** är **tillgänglig för registrerade enheter**, så kan tillgängliga appuppdateringar installeras från företagsportalen. | Enligt slutanvändarens konfiguration i de personliga App Store-inställningarna. Detta kan inte hanteras av Intune-administratören. |
| **Användarregistrering** | Stöds inte. | Stöds med hanterade Apple-ID:n. |
| **Böcker** | Stöds inte. | Stöds. |
| **Licenser som används** | 1 licens per enhet. Licensen associeras med enheten. | 1 licens för upp till 5 enheter med samma personliga Apple-ID. Licensen associeras med användaren. <br> <br> En slutanvändare som är associerad med ett personligt Apple-ID och ett hanterat Apple-ID i Intune förbrukar 2 applicenser.|
| **Licensmigrering** | Appar kan migrera tyst från användare till enhetslicenser. | Appar kan inte migreras från enheten till användarlicenser. |

> [!NOTE]  
> Företagsportalen visar inte enhetslicensierade appar för användarregistrerade enheter, eftersom endast användarlicensierade appar kan installeras på användarregistreringsenheter.

## <a name="what-app-types-are-supported"></a>Vilka disktyper stöds?
Du kan köpa och distribuera offentliga appar och privata appar med hjälp av Apple Business Manager.
- **Store-appar:** Med hjälp av Apple Business Manager kan innehållshanterare köpa både kostnadsfria och betalda appar som är tillgängliga i App Store.
- **Anpassade appar:** Med hjälp av Apple Business Manager kan innehållshanterare också köpa anpassade och privat tillgängliga appar till din organisation. Dessa appar skräddarsys efter organisationens speciella behov av utvecklare som du arbetar med direkt. Läs mer om [hur man distribuerar anpassade appar](https://developer.apple.com/business/custom-apps/).

## <a name="prerequisites"></a>Krav
- Ett [Apple Business Manager](https://business.apple.com/)- eller [Apple School Manager](https://school.apple.com/)-konto för din organisation. 
- Köpta applicenser som tilldelats till en eller flera platstoken. 
- Nedladdade platstoken. 

> [!IMPORTANT]
> - En platstoken kan endast användas med en enhetshanteringslösning i taget. Innan du börjar använda inköpta appar med Intune måste du återkalla och ta bort alla befintliga platskonton som används med andra MDM-leverantörer (hantering av mobilenheter). 
> - En platstoken har endast stöd för användning i en Intune-klient i taget. Återanvänd inte samma token för flera Intune-klienter.
> - Intune synkroniserar som standard platstoken med Apple två gånger om dagen. Du kan starta en manuell synkronisering från Intune när som helst.
> - När du har importerat platstoken till Intune, så importera inte samma token till någon annan enhetshanteringslösning. Om du gör det kan licenstilldelningen och användarposter gå förlorade.

## <a name="migrate-from-volume-purchase-program-vpp-to-apps-and-books"></a>Migrera från volymköpsprogram (VPP) till appar och böcker
Om din organisation ännu inte har migrerat till Apple Business Manager eller Apple School Manager, så läs [Apples vägledning om hur man migrerar till appar och böcker](https://support.apple.com/HT208257) innan du fortsätter med att hantera inköpta appar i Intune.

> [!IMPORTANT]
> - Migrera bara en VPP-inköpare per plats för bästa migrering. Om varje inköpare migreras till en unik plats, så flyttas alla licenser, tilldelade som otilldelade, till appar och böcker.
> - Ta inte bort den befintliga gamla VPP-token i Intune eller appar och tilldelningar som är associerade med en befintlig äldre VPP-token i Intune. Dessa åtgärder kräver att alla apptilldelningar återskapas i Intune.

Migrera befintligt inköpt VPP-innehåll och token till appar och böcker i Apple Business Manager eller Apple School Manager enligt följande:

1. Bjud in VPP-inköpare att ansluta till din organisation och dirigera varje användare till att välja en unik plats. 
2. Se till att alla VPP-inköpare i din organisation har slutfört steg 1 innan du fortsätter.
3. Kontrollera att alla inköpta appar och licenser har migrerats till appar och böcker i Apple Business Manager eller Apple School Manager.
4. Ladda ned en ny platstoken genom att gå till **Apple Business (eller School) Manager** > **Inställningar** > **Appar och böcker** > **Mina servertoken**.
5. Uppdatera platstoken i administrationscentret för Microsoft Endpoint Manager genom att gå till **Klientadministration** > **Anslutningar och token** > **Apple VPP-token** och synkronisera token.

## <a name="upload-an-apple-vpp-or-location-token"></a>Överför en Apple VPP-token eller platstoken

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Välj **Administration av klientorganisation** > **Anslutningsappar och token** > **Apple VPP-token**.
4. I fönstret med VPP-tokenlistan väljer du **Skapa**.
5. I fönstret **Skapa VPP-token** anger du följande information:
    - **VPP-tokenfil** – Om du inte redan har gjort det kan du registrera dig för Apple Business Manager eller Apple School Manager. När du har registrerat dig laddar du ned Apple VPP-token för ditt konto och väljer det här.
    - **Apple-ID** – Ange det hanterade Apple-ID:t för det konto som är associerat med den överförda token.
    - **Ta kontroll över token från en annan MDM** – Om du ställer in det här alternativet på **Ja** så tillåts token att återtilldelas till Intune från en annan MDM-lösning.
    - **Tokennamn** – Ett administrativt fält för att ange tokennamn.    
    - **Land/region** – Välj VPP-landskod/-regionkod.  Intune synkroniserar VPP-appar för alla språk från det angivna VPP-landet/-regionens App Store.
        > [!WARNING]  
        > När du byter land/region uppdateras appmetadata och App Store-URL vid nästa synkronisering med Apple-tjänsten för appar som har skapats med denna token. Appen uppdateras inte om den inte finns i det nya landets/regionens butik.

    - **Typ av VPP-konto** – Välj mellan **Företag** eller **Utbildning**.
    - **Automatiska appuppdateringar** – Välj mellan **På** eller **Av** för att aktivera automatiska uppdateringar. När det är aktiverat identifierar Intune VPP-appuppdateringar i appbutiken och push-installerar dem automatiskt på enheten när den checkas in. 
        
        > [!NOTE] 
        > Automatiska appuppdateringar för Apple VPP-appar uppdaterar endast de appar automatiskt som distribuerats med **krävd** installeringsavsikt. För appar som distribueras med **tillgänglig** installeringsavsikt genererar den automatiska uppdateringen ett statusmeddelande åt IT-administratören som informerar om att en ny version av appen är tillgänglig. Det här statusmeddelandet visas när du väljer appen, väljer Installationsstatus för enhet och kontrollerar statusinformationen.  

    - **Ge Microsoft behörighet att skicka information om både användare och enhet till Apple.** – Du måste välja **Jag accepterar** för att kunna fortsätta. Information om vilka data som Microsoft skickar till Apple finns i [Data som Intune skickar till Apple](~/protect/data-intune-sends-to-apple.md).

6. När du är klar väljer du **Skapa**. Den token du önskar visas i fönstret med tokenlistan.

## <a name="synchronize-a-vpp-token"></a>Synkronisera en VPP-token
Du kan synkronisera appnamn, metadata och licensinformation för dina köpta appar i Intune genom att välja **Synkronisera** för en vald token.

## <a name="assign-a-volume-purchased-app"></a>Tilldela en volyminköpt app

1. Välj **Appar** > **Alla appar**.
2. I fönstret med applistan väljer du den app som du vill tilldela och väljer sedan **Tilldelningar**.
3. I fönstret **Appnamn** - **Tilldelningar** väljer du **Lägg till grupp** och i fönstret **Lägg till grupp** väljer du sedan en **Tilldelningstyp** och den Azure AD-användare eller de enhetsgrupper som du vill tilldela till appen.
5. Välj följande inställningar för varje grupp som du har valt:
    - **Typ** – Välj om appen ska vara **Tillgänglig** (slutanvändare kan installera appen från företagsportalen) eller **Obligatorisk** (slutanvändare får appen installerad automatiskt).
    - **Licenstyp** – Välj mellan **Användarlicensiering** eller **Enhetslicensiering**.
6. När du är klar väljer du **Spara**.


>[!NOTE]
>Tillgänglig distributionsavsikt stöds inte för enhetsgrupper – det är bara användargrupper som stöds. Listan över appar som visas är associerad med en token. Om du har en app som är associerad med flera VPP-token kan du se samma app visas flera gånger, en gång för varje token.

> [!NOTE]  
> Intune (eller någon annan MDM) installerar egentligen inte VPP-appar. I stället ansluter Intune till ditt VPP-konto och talar om för Apple vilka applicenser som ska tilldelas till de olika enheterna. Därifrån sköts den faktiska installationen mellan Apple och enheten.
> 
> [Apple MDM-protokollreferens, sidan 135](https://developer.apple.com/business/documentation/MDM-Protocol-Reference.pdf)

## <a name="end-user-prompts-for-vpp"></a>Slutanvändarprompt för VPP

Slutanvändaren får prompter för VPP-appinstallation i ett antal scenarier. Varje villkor förklaras i följande tabell:

| # | Scenario                                | Inbjudan till Apples VPP-program                              | Uppmaning vid appinstallation | Fråga efter Apple-ID |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – licensierad användare (inte en enhet för användarregistrering)                             | J                                                                                               | J                                           | J                                 |
| 2 | Corp – användarlicensierad (ej övervakad enhet)     | J                                                                                               | J                                           | J                                 |
| 3 | Corp – användarlicensierad (övervakad enhet)         | J                                                                                               | N                                           | J                                 |
| 4 | BYOD – enhetslicensierad                           | N                                                                                               | J                                           | N                                 |
| 5 | CORP – enhetslicensierad (ej övervakad enhet)                           | N                                                                                               | J                                           | N                                 |
| 6 | CORP – enhetslicensierad (övervakad enhet)                           | N                                                                                               | N                                           | N                                 |
| 7 | Helskärmsläge (övervakad enhet) – enhetslicensierad | N                                                                                               | N                                           | N                                 |
| 8 | Helskärmsläge (övervakad enheten) – användarlicensierad   | --- | ---                                          | ---                                |

> [!Note]  
> Att tilldela enheter i helskärmsläge VPP-appar med användarlicensiering är inte något som vi rekommenderar.

## <a name="revoking-app-licenses"></a>Återkalla applicenser

Du kan återkalla alla associerade iOS eller macOs VPP-applicenser (volyminköpsprogram) baserat på en viss enhet, användare eller app.  Men det finns vissa skillnader mellan iOS- och macOS-plattformarna. 

|   | iOS | macOS |
|-----|------------------|----------------|
| **Ta bort apptilldelning** | När du tar bort en app som har tilldelats till en användare, frigör Intune användarens eller enhetens licens och avinstallerar appen från enheten. | När du tar bort en app som en användare har tilldelats, så frigör Intune användarens eller enhetens licens. Appen avinstalleras inte från enheten. |
| **Återkalla applicens** | När du återkallar en applicens återtas applicensen från användaren eller enheten. Du måste ändra tilldelningen till **Avinstallera** om du vill ta bort appen från enheten. | När du återkallar en applicens återtas applicensen från användaren eller enheten. MacOS-appen med återkallad licens fortsätter att vara användbar på enheten, men kan inte uppdateras förrän en licens har tilldelats till användaren eller enheten på nytt. Enligt Apple tas dessa appar bort efter en 30 dagar lång betänketid. Apple tillhandahåller dock inget sätt för Intune att ta bort appen med hjälp av tilldelningsåtgärden Avinstallera.

>[!NOTE]
> - Intune återtar applicenser när en anställd lämnar företaget och inte längre ingår i AAD-grupperna.
> - När du tilldelar en inköpt app med **Avinstallera** så både återtar Intune licensen och avinstallerar appen.
> - Applicenser återtas inte när en enhet tas bort från Intune-hanteringen. 

## <a name="deleting-vpp-tokens"></a>Ta bort VPP-token
<!-- 820879 -->  
Du kan ta bort en Apple-token för volyminköpsprogrammet (VPP) med hjälp av konsolen. Detta kan vara nödvändigt när du har dubblettinstanser av en VPP-token. Om du tar bort en token tas även alla associerade appar och tilldelningar bort. Men att ta bort en token innebär inte att applicenser frigörs eller att appar avinstalleras. 

>[!NOTE]
>Intune kan inte återkalla licenser för appar när en token har tagits bort. 

<!-- 820870 -->  
Om du vill återkalla en licens för alla VPP-appar för en specifik VPP-token, måste du först återkalla licenser för alla appar som är associerade med token och sedan ta bort token.

## <a name="renewing-app-licenses"></a>Förnya applicenser

Du kan förnya en Apple VPP-token genom att ladda ned en ny token från Apple Business Manager eller Apple School Manager och sedan uppdatera befintlig token i Intune.

## <a name="deleting-a-vpp-app"></a>Ta bort en VPP-app

Du kan för närvarande inte ta bort en iOS VPP-app från Microsoft Intune.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Tilldela anpassade rollbehörigheter för VPP

Åtkomst till Apple VPP-token och VPP-appar kan kontrolleras oberoende av de behörigheter som tilldelats anpassade administratörsroller i Intune.

* Om du vill låta en anpassad Intune-roll hantera Apple VPP-token, så måste du tilldela behörigheter för **Hanterade appar** under **Appar** > **Apple VPP-token**.
* Om du vill låta en anpassad Intune-roll hantera appar som har köpts med iOS VPP-token, så måste du tilldela behörigheter för **Mobilappar** under **Appar** > **Alla appar**. 

## <a name="additional-information"></a>Ytterligare information

Apple tillhandahåller direkthjälp för att skapa och förnya VPP-token. Mer information finns i [Distribute content to your users with the Volume Purchase Program (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661) (Distribuera innehåll till användarna med volyminköpsprogrammet (VPP)) som en del av Apples dokumentation. 

Om **Assigned to external MDM** (Tilldelad till extern MDM) anges i Intune-portalen måste du (administratören) ta bort VPP-token från hantering av mobilenheter från tredje part innan VPP-token används i Intune.

## <a name="frequently-asked-questions"></a>Vanliga frågor och svar

### <a name="how-many-tokens-can-i-upload"></a>Hur många token kan jag överföra?
Du kan överföra upp till 3 000 tokens i Intune.

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Hur lång tid tar det för portalen att uppdatera licensantalet när en app installeras eller tas bort från enheten?
Licensen bör vara uppdaterad inom några timmar efter installation eller avinstallation av en app. Observera att om slutanvändaren tar bort appen från enheten, är licensen fortfarande tilldelad till användaren eller enheten.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>Går det att överprenumerera på en app och i så fall när?
Ja. Intune-administratören kan överprenumerera på en app. Exempelvis om administratören köper 100 licenser för appen XYZ och sedan riktar appen till en grupp med 500 medlemmar. De första 100 medlemmarna (användare eller enheter) får den licens som tilldelats till dem, men resten av medlemmarna misslyckas vid licenstilldelningen.


## <a name="next-steps"></a>Nästa steg

Du hittar mer information i [Hur du övervakar appar](apps-monitor.md) som hjälper dig att övervaka apptilldelningar.

Information om hur du felsöker apprelaterade problem finns i [Felsöka appar](~/apps/troubleshoot-app-install.md).
