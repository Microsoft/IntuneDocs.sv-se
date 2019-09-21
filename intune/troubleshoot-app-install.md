---
title: Felsöka appinstallationsproblem
titleSuffix: Microsoft Intune
description: Använd felsökningsfönstret i Microsoft Intune om du vill felsöka appinstallationsproblem.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/04/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 850c7a28c4df1638e9f635713695dcf2e914ffce
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166945"
---
# <a name="troubleshoot-app-installation-issues"></a>Felsöka appinstallationsproblem

På Microsoft Intune MDM-hanterade enheter kan ibland appinstallationer misslyckas. När dessa appinstallationer misslyckas, kan det vara en utmaning att förstå felorsaken eller felsöka problemet. Microsoft Intune tillhandahåller information om appinstallationsfel som tillåter supportansvariga och Intune-administratörer att visa information som underlättar användarnas begäran om hjälp. Felsökningsfönstret i Intune ger information om felet, inklusive information om hanterade appar på en användares enhet. Information om en apps livscykel från början till slut ges under varje enskild enhet i fönstret **Hanterade appar**. Du kan visa installationsrelaterad information, t.ex. när appen har skapats, ändrats, inriktats och levereras till en enhet. 

## <a name="app-troubleshooting-details"></a>Information om felsökning av appar

Intune tillhandahåller appfelsökningsinformation baserad på de appar som installerats på en viss användares enhet.

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Felsök** i fönstret **Intune**.
4. Klicka på **Välj användare** om du vill välja en användare att felsöka. Fönstret **Välj användare** visas.
5. Välj en användare genom att skriva namnet eller e-postadressen. Klicka på **Nästa** längst ner i fönstret. Felsökningsinformationen för användaren visas i fönstret **Felsökning**. 
6. Välj den enhet som du vill felsöka i listan **Enheter**.
    ![Felsökningsfönstret i Intune.](media/troubleshoot-app-install-01.png)
7. Välj **Hanterade appar** i det valda enhetsfönstret. En lista över hanterade appar visas.
    ![Information om en specifik enhet som hanteras av Intune.](media/troubleshoot-app-install-02.png)
8. Välj en app i listan där **Installationsstatus** indikerar ett fel.
    ![En vald app som visar information om installationsfel.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > Samma app kan tilldelas till flera grupper, men med olika avsedda åtgärder (avsikter) för appen. En löst avsikt för en app kan t.ex. visa **Exkluderad** om appen har exkluderats för en användare under apptilldelningen. Mer information finns i [Lösa konflikter mellan appavsikter](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Om ett installationsfel inträffar för en app som krävs kan varken du eller supporten synkronisera enheten och försöka installera appen igen.

Problemet indikeras i informationen om appinstallationsfel. Du kan använda den här informationen för att komma fram till vilket som är det bästa sättet att lösa problemet på. Läs mer om hur du felsöker problem med appinstallationen i [Appinstallationsfel](troubleshoot-app-install.md#app-installation-errors).

> [!Note]  
> Du kan också få åtkomst till **felsökningsfönstret** genom att gå till: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>Installation av riktad app för användar grupp når inte enhet
Följande åtgärder bör beaktas när du har problem med att installera appar:
- Om appen inte visas i Företagsportal, se till att appen distribueras med **tillgänglig** avsikt och att användaren får åtkomst till företagsportal med den enhets typ som stöds av appen.
- För Windows BYOD-enheter måste användaren lägga till ett arbets konto till enheten.
- Kontrol lera om användaren är över enhets gränsen för AAD:
  1. Navigera till [Azure Active Directory enhets inställningar](https://portal.azure.com/#blade/Microsoft_AAD_IAM/DevicesMenuBlade/DeviceSettings/menuId).
  2. Anteckna det värde som har angetts för **maximalt antal enheter per användare**.
  3. Navigera till [Azure Active Directory användare](https://portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/AllUsers).
  4. Välj den berörda användaren och klicka på **enheter**.
  5. Om användaren är över angiven gräns tar du bort eventuella inaktuella poster som inte längre behövs.
- För iOS DEP-enheter kontrollerar du att användaren är listad som **registrerad av användaren** i Intune-bladet översikt. Om det visar NA, distribuerar du en konfigurations princip för Intune-företagsportal. Mer information finns i [Konfigurera appen Företagsportal](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Felsökning av Win32-appinstallationen

Välj Win32-appen som distribuerats med Intune-hanteringstillägget. Du kan välja alternativet **Samla in loggar** om installationen av Win32-appen misslyckas. 

> [!IMPORTANT]
> Alternativet **Samla in loggar** är inte aktiverat om Win32-appen har installerats korrekt på enheten.<p>Innan du kan samla in logginformation för Win32-appen måste Intune-hanteringstillägget installeras på Windows-klienten. Intune-hanteringstillägget installeras när ett PowerShell-skript eller en Win32-app distribueras till en användare eller en enhetssäkerhetsgrupp. Mer information finns i avsnittet med [förhandskrav för Intune-hanteringstillägget](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Samla in loggfil

Om du vill samla in installationsloggarna för Win32-appen följer du stegen i avsnittet med [information om felsökning av appar](troubleshoot-app-install.md#app-troubleshooting-details). Fortsätt sedan med följande steg:

1. Klicka på alternativet **Samla in loggar** på bladet **Installationsinformation**.

    <image alt="Win32 app installation details - Collect log option" src="media/troubleshoot-app-install-04.png" width="500" />

2. Ange sökvägar med loggfilnamn för att börja samla in loggfiler och klicka på **OK**.
    
    > [!NOTE]
    > Logginsamlingen tar mindre än två timmar. Följande filtyper stöds: *.log, .txt, .dmp, .cab, .zip, .xml, .evtx och .evtl*. Högst 25 sökvägar är tillåtna.

3. När loggfilerna har samlats in kan du välja länken **loggar** för att ladda ned loggfilerna.

    <image alt="Win32 app log details - Download logs" src="media/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Ett meddelande visas som anger att loggarna för apparna har samlats in.

#### <a name="win32-log-collection-requirements"></a>Krav för Win32-logginsamling

Det finns särskilda krav som du måste följa för att samla in loggfiler:

- Du måste ange den fullständiga sökvägen. 
- Du kan ange miljövariabler för logginsamling, till exempel följande:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Endast exakta filnamnstillägg är tillåtna, till exempel:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- Du kan ladda upp loggfiler på högst 60 MB eller högst 25 filer, beroende på vilken gräns som nås först. 
- Du kan samla in Win32-appinstallationsloggar för appar som uppfyller apptilldelningsavsikten Krävs, Tillgänglig eller Avinstallera.
- Lagrade loggar krypteras för att skydda personlig identifierbar information som finns i loggarna.
- När du öppnar supportbegäranden om Win32-appfel bifogar du associerade felloggar genom att följa stegen ovan.

## <a name="app-installation-errors"></a>Appinstallationsfel

Följande felmeddelanden och beskrivningar ger information om både Android- och iOS-installationsfel. 

### <a name="android-errors"></a>Android-fel

Det här avsnittet beskrivs både enhets administratör (DA) och Samsung KNOX-registrering. Mer information finns i [Android-enhetens administratörs registrering](android-enroll-device-administrator.md) och [registrera Android-enheter automatiskt med hjälp av Samsung: s Knox mobila registrering](android-samsung-knox-mobile-enroll.md). 

| Felmeddelande/kod | Beskrivning |
|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Det gick inte att installera appen. (0xC7D14FB5) | Det här felmeddelandet visas när Intune inte kan fastställa orsaken till Android-appens installationsfel. Ingen information angavs av Android om felet. Det här felet returneras när APK-nedladdningen utfördes men det inte gick att installera appen. Det här felet beror normalt på att APK-filen är skadad och inte går att installera på enheten. En möjlig orsak kan vara att Google Play Protect blockerar installationen av appen av säkerhetsskäl. En annan möjlig orsak till felet är att enheten saknar stöd för appen. Appen kanske kräver API-version 21 eller senare medan enheten för närvarande har API-version 19. Intune returnerar det här felet för både DA- och KNOX-enheter, och om det är problem med APK:t kommer installationen inte att lyckas även om användaren ser ett meddelande om att försöka igen. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet. |
| Appinstallationen avbröts eftersom installationsfilen (APK) togs bort efter nedladdningen men före installationen. (0xC7D14FBA) | APK-filen laddades ned, men innan användaren installerade appen så togs filen bort från enheten. Det här kan inträffa om det förflöt lång tid mellan nedladdningen och installationen. Användaren avbröt kanske den ursprungliga installationen, väntade en stund och sedan klickade på meddelandet om att försöka igen. Det här felmeddelandet returneras bara för DA-scenarier. KNOX-scenarier kan utföras tyst. Vi visar ett meddelande om att försöka igen som användaren kan godkänna i stället för att avbryta. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet. |
| Appinstallationen avbröts eftersom processen startades om under installationen. (0xC7D14FBB) | Enheten startades om under APK-installationsprocessen, vilket gjorde att installationen avbröts. Det här felmeddelandet returneras för både DA och KNOX-enheter. Intune visar ett meddelande som användaren kan klicka på för att försöka igen. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet. |
| Programmet hittades inte efter att installationen slutfördes. (0x87D1041C) | Användaren har uttryckligen avinstallerat appen. Det här felet returneras inte från klienten. Det är ett fel som genererades när appen installerades tidigare, men sedan har användaren avinstallerat den. Det här felet ska bara inträffa för obligatoriska appar. Användare kan avinstallera appar som inte är obligatoriska. Det här felet kan endast inträffa i DA. KNOX blockerar avinstallation av hanterade appar. Vid nästa synkronisering visas meddelandet om avinstallation för användaren igen. Användaren kan ignorera meddelandet. Felet fortsätter att rapporteras tills användaren installerar appen. |
| Nedladdningen misslyckades på grund av ett okänt fel. (0xC7D14FB2) | Det här felet inträffar när nedladdningen misslyckas. Felet beror ofta på problem med Wi-Fi eller att anslutningen är långsam. Det här felet returneras bara i DA-scenarier. I KNOX-scenarier uppmanas inte användaren att installera appar, det kan göras tyst. Intune visar ett meddelande som användaren kan klicka på för att försöka igen. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet. |
| Nedladdningen misslyckades på grund av ett okänt fel. Principen utförs igen nästa gång enheten synkroniseras. (0xC7D15078) | Det här felet inträffar när nedladdningen misslyckas. Felet beror ofta på problem med Wi-Fi eller att anslutningen är långsam. Det här felet returneras bara i DA-scenarier. I KNOX-scenarier uppmanas inte användaren att installera appar, det kan göras tyst. |
| Slutanvändaren avbröt appinstallationen. (0xC7D14FB1) | Användaren har uttryckligen avinstallerat appen. Det här felet returneras när användaren avbryter installationen i Android-operativsystemet. Användaren tryckte på knappen Avbryt vid installationsprompten i operativsystemet eller stängde kommandotolken. Det här felet returneras bara i DA-scenarier. I KNOX-scenarier uppmanas inte användaren att installera appar, det kan göras tyst. Intune visar ett meddelande som användaren kan klicka på för att försöka igen. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet. Be användaren att inte avbryta installationen. |
| Filnedladdningen stoppades oväntat. (0xC7D15015) | Operativsystemet stoppade nedladdningen innan den slutfördes. Det här felet kan inträffa när enheten har låg batterinivå eller om nedladdningen tar för lång tid. Det här felet returneras bara i DA-scenarier. I KNOX-scenarier uppmanas inte användaren att installera appar, det kan göras tyst. Intune visar ett meddelande som användaren kan klicka på för att försöka igen. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet. Se till att enheten har en tillförlitlig nätverks anslutning.  |
| Filnedladdningstjänsten stoppades oväntat. Principen utförs igen nästa gång enheten synkroniseras. (0xC7D1507C) | Operativsystemet avslutade nedladdningen innan den slutfördes. Det här felet kan inträffa när enheten har låg batterinivå eller om nedladdningen tar för lång tid. Det här felet returneras bara i DA-scenarier. I KNOX-scenarier uppmanas inte användaren att installera appar, det kan göras tyst. Synkronisera enheten manuellt eller vänta i 24 timmar och kontrol lera statusen. |
| Det gick inte att avinstallera appen. (0xc7d14fb8) | Det här felet är ett allmänt avinstallations fel. Det gick inte att ange varför appen inte kunde avinstallera. Vissa administrativa appar kan inte avinstalleras helt. Kontrol lera att appen kan avinstalleras manuellt och samla in Företagsportal loggar om avinstallationen Miss lyckas. |
| APK-filen för app-installationen som används för uppgraderingen matchar inte signaturen för den aktuella appen på enheten. (0xc7d14fb7) | Android OS har en begränsning som kräver att signerings certifikatet för uppgraderings versionen är exakt samma som det certifikat som används för att signera den befintliga versionen. Om utvecklaren inte kan använda samma certifikat för att signera den nya versionen måste du avinstallera den befintliga appen och distribuera om den nya appen i stället för att uppgradera den befintliga appen. |
| Slutanvändaren avbröt appinstallationen. (0xc7d14fb9) | Utbilda användaren att acceptera den Intune-distribuerade appen och installera appen när du uppmanas till det. |
| Avinstallationen av appen avbröts eftersom processen startades om under installationen. (0xc7d14fbc) | Installations processen för appen avslutades av operativ systemet eller också startades enheten om. Försök att installera igen och samla in Företagsportal loggar om felet uppstår igen. |
| Det går inte att installera APK-filen för app-installation eftersom den inte har signerats. (0xc7d14fb6) | Som standard kräver Android OS att appar signeras. Se till att appen är signerad före distributionen. |

### <a name="ios-errors"></a>iOS-fel

| Felmeddelande/kod | Beskrivning/felsökningstips |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | Apple MDM-agenten returnerade att installationskommandot misslyckades. |
| (0x87D1313C) | Nätverksanslutningen bröts medan den uppdaterade webbadressen för nedladdningstjänsten skickades till enheten. Mer specifikt gick det inte att hitta någon server med det angivna värdnamnet. |
| iOS-enheten är upptagen för närvarande. (0x87D11388) | iOS-enheten var upptagen, vilket ledde till ett fel. Enheten var låst. Användaren måste låsa upp enheten för att installera appen. |
| Appinstallationen misslyckades. (0x87D13B64) | Ett appinstallationsfel inträffade. Du behöver iOS-konsolloggar för att felsöka problemet. |
| Appen är hanterad men har upphört att gälla eller tagits bort av användaren. (0x87D13B66) | Antingen avinstallerade användaren uttryckligen appen, eller så har appen upphört att gälla, men det gick inte att ladda ned appen, eller också matchar inte svaret från enheten. Det här felet kan också inträffa på grund av en bugg i plattformen iOS 9.2.2. |
| Appen är schemalagd för installation, men det krävs en inlösningskod för att slutföra transaktionen. (0x87D13B60) | Det här felet inträffar vanligen med betalda iOS Store-appar. |
| Programmet hittades inte efter att installationen slutfördes. (0x87D1041C) | Appidentifieringsprocessen matchade inte svaret från enheten. |
| Användaren avvisade erbjudandet att installera appen. (0x87D13B62) | Användaren klickade på Avbryt under den inledande appinstallationen. Be användaren att acceptera installations förfrågan nästa gången. |
| Användaren avvisade erbjudandet att uppdatera appen. (0x87D13B63) | Slutanvändaren klickade på Avbryt under uppdateringsprocessen. Distribuera efter behov eller utbilda användaren för att acceptera uppgraderings meddelandet. |
| Okänt fel (0x87D103E8) | Ett okänt fel inträffade under appinstallationen. Det här felet visas om inget annat fel kan identifieras. |
| Det går bara att installera VPP-appar på en delad iPad (-2016330861). | Apparna måste hämtas med Apples volymköpsprogram för installation på en delad iPad. |
| Det går inte att installera appar när App Store är inaktiverad (-2016330860). | App Store måste vara aktiverad för att användaren ska kunna installera appen. |
| Det går inte att hitta VPP-licensen för appen (-2016330859). | Prova att återkalla och omtilldela applicensen. |
| Det går inte att installera systemappar med din MDM-provider (-2016330858). | Det går inte att installera appar som förinstallerats av iOS-operativsystemet. |
| Det går inte att installera appar när enheten är i Borttappat läge (-2016330857). | All användning av enheten är blockerad i Borttappat läge. Inaktivera Borttappat läge om du vill installera appar. |
| Det går inte att installera appar när enheten är i helskärmsläge (-2016330856). | Prova att lägga till enheten i en exkluderingsgrupp under konfigurationsprincipen för helskärmsläge för att installera appar. |
| Det går inte att installera 32-bitarsappar på enheten (-2016330852). | Enheten stöder inte installation av 32-bitarsappar. Prova att distribuera 64-bitarsversionen av appen. |
| Användaren måste logga in i App Store (-2016330855). | Användaren måste logga in i App Store innan appen kan installeras. |
| Okänt problem. Försök igen (-2016330854). | Appinstallationen misslyckades på grund av ett okänt problem. Försök igen senare. |
| Appinstallationen misslyckades. Intune gör ett nytt försök nästa gång enheten synkroniseras (-2016330853). | Ett enhetsfel påträffades under appinstallationen. Synkronisera enheten och prova att installera appen igen. |
| Licens tilldelningen misslyckades med Apple-fel ' inga VPP-licenser kvar ' (0x87d13b7e) | Detta här beteendet är avsiktligt. Du löser detta genom att köpa ytterligare VPP-licenser eller frigöra licenser från användare som inte längre är riktade. |
| App install-fel 12024: okänd orsak. (0x87d13b6e) | Apple har inte gett oss tillräckligt med information för att avgöra varför installationen misslyckades. Det finns inget att rapportera. |
| Konfigurations principen för nödvändig app saknas, se till att principen är riktad mot samma grupper. (0x87d13b7f) | Appen kräver konfiguration av appen men ingen app-konfiguration har mål. Administratören bör se till att de grupper som appen är riktad till också har den obligatoriska app-konfigurationen som är riktad till grupperna. |
| Enhetens VPP-licensiering gäller endast för iOS 9.0 +-enheter. (0x87d13b69) | Uppgradera berörda iOS-enheter till iOS 9.0 +. |
| Programmet installeras på enheten men är ohanterat. (0x87d13b8f) | Det här felet inträffar bara för LOB-appar. Appen installerades utanför Intune. Du kan åtgärda det här felet genom att avinstallera appen från enheten. Nästa gången enheten synkroniserar ska enheten installera appen från Intune. |
| Användaren avböjde app Management (0x87d13b68) | Be användaren att ta emot program hantering. |
| Okänt fel. (0x87d1279d) | Det här felet uppstår för iOS Store-appar, men fel scenariot är okänt. |
| Den senaste versionen av appen kunde inte uppdateras från en tidigare version. (0x87D13B9D) | Det här fel meddelandet visas om appen är installerad och hanterad men med fel version på enheten. Den här situationen inkluderar när en enhet har tagit emot ett kommando för att uppdatera en app, men den nya versionen har ännu inte installerats och rapporter ATS igen. Det här felet rapporteras för den första incheckningen av en enhet när uppgraderingen har distribuerats, och kommer att ske tills enheten rapporterar att den nya versionen är installerad eller Miss lyckas på grund av ett annat fel.  |


### <a name="other-installation-errors"></a>Andra installationsfel

|  Felmeddelande/kod  |  Beskrivning  |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  0x80073CFF, 0x80CF201C (klientfel)  |  Om du vill installera den här appen måste du ha ett system där separat inläsning tillåts. Kontrollera att app-paketet är signerat med en betrodd signatur och installerat på en domänansluten enhet där principen **AllowAllTrustedApps** är aktiverad, eller en enhet med en Windows-licens för separat inläsning med principen **AllowAllTrustedApps** aktiverad. Mer information finns i [Felsöka paketering, distribution och frågor för Windows Store-appar](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).   |
|  0x80073CF0  |  Paketet kunde inte öppnas. Möjliga orsaker:<ul><li> Paketet är inte signerat.</li><li> Utgivarens namn matchar inte signeringscertifikatets ämne.</li></ul> Mer information finns i **AppxPackagingOM**-händelseloggen. Mer information finns i [Felsöka paketering, distribution och frågor för Windows Store-appar](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CF3  |  Paketet misslyckades med uppdaterings-, beroende- eller konfliktverifiering. Möjliga orsaker:<ul><li> Det inkommande paketet är i konflikt med ett installerat paket.</li><li> Det gick inte att hitta ett angivet paketberoende.</li><li> Paketet stöder inte korrekt processorarkitektur.</li></ul> Mer information finns i **AppXDeployment-Server**-händelseloggen. Mer information finns i [Felsöka paketering, distribution och frågor för Windows Store-appar](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CFB  |  Det angivna paketet har redan installerats och en ominstallation av paketet är blockerad. Du kan råka ut för det här felet om du installerar ett paket som inte är identiskt med det paket som redan har installerats. Bekräftelse av den digitala signaturen ingår också i paketet. När ett paket har byggts om eller signerats på nytt så är det inte längre binärt identiskt med det tidigare installerade paketet. De två möjliga alternativ för att åtgärda det här felet är:<ul><li> Öka appens versionsnummer och bygg sedan om och signera paketet på nytt.</li><li> Ta bort det gamla paketet för varje användare i systemet innan du installerar det nya paketet.</li></ul> Mer information finns i [Felsöka paketering, distribution och frågor för Windows Store-appar](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x87D1041C  |  Programinstallationen lyckades men programmet identifieras inte. Appen har distribuerats av Intune och sedan avinstallerats. Orsaker till att appen avinstalleras är:<ul><li> Slutanvändaren avinstallerade appen.</li><li> Identitetsinformationen i paketet matchar inte vad enheten rapporterar för felaktiga appar.</li><li>Vid automatiskt uppdaterade MSI:er matchar produktversionen inte appinformationen när den har uppdaterats utanför Intune.</li></ul> Be användaren att installera om appen via företagsportalen. Observera att de appar som krävs ominstalleras automatiskt nästa gång enheten checkas in.  |
|  0x8000FFFF  |  Ett oväntat fel inträffade under installationen. Mer information hittar du i installations loggarna.  |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Felsöka appar från Microsoft Store

Informationen i avsnittet [Troubleshooting packaging, deployment, and query of Windows Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (Felsöka paketering, distribution och frågor för Windows Store-appar) hjälper dig att felsöka vanliga problem som kan uppstå när du installerar appar från Microsoft Store, oavsett om du gör det med Intune eller på annat sätt.

## <a name="app-troubleshooting-resources"></a>Appfelsökningsresurser
- [Distribuera Visio och Project som en del av din Office Pro plus-distribution](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Vidta åtgärder för att säkerställa att MSfB-appar distribueras via Intune-installation på Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Felsöka distributioner av MSI-appar i Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Metod tips för program distribution till den klassiska Windows PC-agenten i Intune](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Nästa steg

- Ytterligare information om felsökning av Intune information finns i [Använd felsökningsportalen för att hjälpa företagets användare](help-desk-operators.md). 
- Lär dig om kända problem i Microsoft Intune. Mer information finns i [Intune kund framgångar](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- Behöver du mer hjälp? Se [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).
