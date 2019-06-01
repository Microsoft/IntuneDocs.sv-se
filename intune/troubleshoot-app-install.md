---
title: Felsöka appinstallationsproblem
titleSuffix: Microsoft Intune
description: Använd felsökningsfönstret i Microsoft Intune om du vill felsöka appinstallationsproblem.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/19/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe7ffa6ff024c719fc24209947b87b07ea2b6791
ms.sourcegitcommit: 063177c6c365fef3642edd7c455790958469aad9
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412687"
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
- Lagrade loggar krypteras för att skydda personligt identifierbar information som finns i loggarna.
- När du öppnar supportbegäranden om Win32-appfel bifogar du associerade felloggar genom att följa stegen ovan.

## <a name="app-installation-errors"></a>Appinstallationsfel

Följande felmeddelanden och beskrivningar ger information om både Android- och iOS-installationsfel. 

### <a name="android-errors"></a>Android-fel

|    Felmeddelande/kod    |    Beskrivning    |
|----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Det gick inte att installera appen. (0xC7D14FB5)    |    Det här felmeddelandet visas när Intune inte kan fastställa orsaken till Android-appens installationsfel. Ingen information angavs av Android om felet.       Det här felet returneras när APK-nedladdningen utfördes men det inte gick att installera appen. Det här felet beror normalt på att APK-filen är skadad och inte går att installera på enheten. En möjlig orsak kan vara att Google Play Protect blockerar installationen av appen av säkerhetsskäl. En annan möjlig orsak till felet är att enheten saknar stöd för appen. Appen kanske kräver API-version 21 eller senare medan enheten för närvarande har API-version 19.         Intune returnerar det här felet för både DA- och KNOX-enheter, och om det är problem med APK:t kommer installationen inte att lyckas även om användaren ser ett meddelande om att försöka igen. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet.        |
|    Appinstallationen avbröts eftersom installationsfilen (APK) togs bort efter nedladdningen men före installationen. (0xC7D14FBA)    |    APK-filen laddades ned, men innan användaren installerade appen så togs filen bort från enheten. Det här kan inträffa om det förflöt lång tid mellan nedladdningen och installationen. Användaren avbröt kanske den ursprungliga installationen, väntade en stund och sedan klickade på meddelandet om att försöka igen.         Det här felmeddelandet returneras bara för DA-scenarier. KNOX-scenarier kan utföras tyst. Vi visar ett meddelande om att försöka igen som användaren kan godkänna i stället för att avbryta. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet.    |
|    Appinstallationen avbröts eftersom processen startades om under installationen. (0xC7D14FBB)    |    Enheten startades om under APK-installationsprocessen, vilket gjorde att installationen avbröts.        Det här felmeddelandet returneras för både DA och KNOX-enheter. Intune visar ett meddelande som användaren kan klicka på för att försöka igen. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet.    |
|    Programmet hittades inte efter att installationen slutförts. (0x87D1041C)    |    Användaren har uttryckligen avinstallerat appen. Det här felet returneras inte från klienten. Det är ett fel som genererades när appen installerades tidigare, men sedan har användaren avinstallerat den. Det här felet ska bara inträffa för obligatoriska appar. Användare kan avinstallera appar som inte är obligatoriska. Det här felet kan endast inträffa i DA. KNOX blockerar avinstallation av hanterade appar.       Vid nästa synkronisering visas meddelandet om avinstallation för användaren igen.   Användaren kan ignorera meddelandet. Felet fortsätter att rapporteras tills användaren installerar appen.    |
|    Nedladdningen misslyckades på grund av ett okänt fel. (0xC7D14FB2)    |    Det här felet inträffar när nedladdningen misslyckas. Felet beror ofta på problem med Wi-Fi eller att anslutningen är långsam.       Det här felet returneras bara i DA-scenarier. I KNOX-scenarier uppmanas inte användaren att installera appar, det kan göras tyst. Intune visar ett meddelande som användaren kan klicka på för att försöka igen. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet.    |
|    Nedladdningen misslyckades på grund av ett okänt fel. Principen utförs igen nästa gång enheten synkroniseras. (0xC7D15078)    |    Det här felet inträffar när nedladdningen misslyckas. Felet beror ofta på problem med Wi-Fi eller att anslutningen är långsam.       Det här felet returneras bara i DA-scenarier. I KNOX-scenarier uppmanas inte användaren att installera appar, det kan göras tyst.    |
|    Slutanvändaren avbröt appinstallationen. (0xC7D14FB1)    |    Användaren har uttryckligen avinstallerat appen. Det här felet returneras när användaren avbryter installationen i Android-operativsystemet. Användaren tryckte på knappen Avbryt vid installationsprompten i operativsystemet eller stängde kommandotolken.        Det här felet returneras bara i DA-scenarier. I KNOX-scenarier uppmanas inte användaren att installera appar, det kan göras tyst. Intune visar ett meddelande som användaren kan klicka på för att försöka igen. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet.    |
|    Filnedladdningen stoppades oväntat. (0xC7D15015)    |    Operativsystemet stoppade nedladdningen innan den slutfördes. Det här felet kan inträffa när enheten har låg batterinivå eller om nedladdningen tar för lång tid.       Det här felet returneras bara i DA-scenarier. I KNOX-scenarier uppmanas inte användaren att installera appar, det kan göras tyst. Intune visar ett meddelande som användaren kan klicka på för att försöka igen. Om appen är en tillgänglig app kan användaren bortse från meddelandet. Om appen är obligatorisk går det dock inte att bortse från meddelandet.    |
|    Filnedladdningstjänsten stoppades oväntat. Principen utförs igen nästa gång enheten synkroniseras. (0xC7D1507C)    |    Operativsystemet stoppade nedladdningen innan den slutfördes. Det här felet kan inträffa när enheten har låg batterinivå eller om nedladdningen tar för lång tid.       Det här felet returneras bara i DA-scenarier. I KNOX-scenarier uppmanas inte användaren att installera appar, det kan göras tyst.    |

### <a name="ios-errors"></a>iOS-fel

| Felmeddelande/kod | Beskrivning/felsökningstips |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | Apple MDM-agenten returnerade att installationskommandot misslyckades. |
| (0x87D1313C) | Nätverksanslutningen bröts medan den uppdaterade webbadressen för nedladdningstjänsten skickades till enheten. Mer specifikt gick det inte att hitta någon server med det angivna värdnamnet. |
| iOS-enheten är upptagen för närvarande. (0x87D11388) | iOS-enheten var upptagen, vilket ledde till ett fel. |
| Appinstallationen misslyckades. (0x87D13B64) | Ett appinstallationsfel inträffade. Du behöver XCODE-loggar för att felsöka problemet. |
| Appen är hanterad men har upphört att gälla eller tagits bort av användaren. (0x87D13B66) | Användaren har uttryckligen avinstallerat appen. Appen kan ha upphört att gälla och inte gått att ladda ned, eller så matchar inte appidentifieringen svaret från enheten.   Det här felet kan också inträffa på grund av en bugg i plattformen iOS 9.2.2. |
| Appen är schemalagd för installation, men det krävs en inlösningskod för att slutföra transaktionen. (0x87D13B60) | Det här felet inträffar vanligen med betalda iOS Store-appar. |
| Programmet hittades inte efter att installationen slutfördes.   (0x87D1041C) | Appidentifieringsprocessen matchade inte svaret från enheten. |
| Användaren avvisade erbjudandet att installera appen. (0x87D13B62) | Användaren klickade på Avbryt under den inledande appinstallationen. |
| Användaren avvisade erbjudandet att uppdatera appen. (0x87D13B63) | Slutanvändaren klickade på Avbryt under uppdateringsprocessen. |
| Okänt fel (0x87D103E8) | Ett okänt fel inträffade under appinstallationen. Det här felet visas om inget annat fel kan identifieras. |
| Det går bara att installera VPP-appar på en delad iPad (-2016330861). | Apparna måste hämtas med Apples volymköpsprogram för installation på en delad iPad. |
| Det går inte att installera appar när App Store är inaktiverad (-2016330860).  | App Store måste vara aktiverad för att användaren ska kunna installera appen. |
| Det går inte att hitta VPP-licensen för appen (-2016330859).  | Prova att återkalla och omtilldela applicensen. |
| Det går inte att installera systemappar med din MDM-provider (-2016330858). | Det går inte att installera appar som förinstallerats av iOS-operativsystemet. |
| Det går inte att installera appar när enheten är i Borttappat läge (-2016330857). | All användning av enheten är blockerad i Borttappat läge.   Inaktivera Borttappat läge om du vill installera appar. |
| Det går inte att installera appar när enheten är i helskärmsläge (-2016330856). | Prova att lägga till enheten i en exkluderingsgrupp under konfigurationsprincipen för helskärmsläge för att installera appar. |
| Det går inte att installera 32-bitarsappar på enheten (-2016330852). | Enheten stöder inte installation av 32-bitarsappar. Prova att distribuera 64-bitarsversionen av appen. |
| Användaren måste logga in i App Store (-2016330855). | Användaren måste logga in i App Store innan appen kan installeras. |
| Okänt problem. Försök igen (-2016330854). | Appinstallationen misslyckades på grund av ett okänt problem.   Försök igen senare. |
| Appinstallationen misslyckades. Intune gör ett nytt försök nästa gång enheten synkroniseras (-2016330853). | Ett enhetsfel påträffades under appinstallationen. Synkronisera enheten och prova att installera appen igen. |

### <a name="other-installation-errors"></a>Andra installationsfel

|    Felmeddelande/kod    |    Beskrivning    |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    0x80073CFF,   0x80CF201C (klientfel)    |    Om du vill installera den här appen måste du ha ett system där separat inläsning tillåts. Kontrollera att app-paketet är signerat med en betrodd signatur och installerat på en domänansluten enhet där principen **AllowAllTrustedApps** är aktiverad, eller en enhet med en Windows-licens för separat inläsning med principen **AllowAllTrustedApps** aktiverad. Mer information finns i [Felsöka paketering, distribution och frågor för Windows Store-appar](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).     |
|    0x80073CF0    |    Paketet kunde inte öppnas. Möjliga orsaker:<ul><li> Paketet är inte signerat.</li><li> Utgivarens namn matchar inte signeringscertifikatets ämne.</li></ul> Mer information finns i **AppxPackagingOM**-händelseloggen. Mer information finns i [Felsöka paketering, distribution och frågor för Windows Store-appar](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x80073CF3    |    Paketet misslyckades med uppdaterings-, beroende- eller konfliktverifiering. Möjliga orsaker:<ul><li> Det inkommande paketet är i konflikt med ett installerat paket.</li><li> Det gick inte att hitta ett angivet paketberoende.</li><li> Paketet stöder inte korrekt processorarkitektur.</li></ul> Mer information finns i **AppXDeployment-Server**-händelseloggen. Mer information finns i [Felsöka paketering, distribution och frågor för Windows Store-appar](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x80073CFB    |    Det angivna paketet har redan installerats och en ominstallation av paketet är blockerad. Du kan råka ut för det här felet om du installerar ett paket som inte är identiskt med det paket som redan har installerats. Bekräftelse av den digitala signaturen ingår också i paketet. När ett paket har byggts om eller signerats på nytt så är det inte längre binärt identiskt med det tidigare installerade paketet. De två möjliga alternativ för att åtgärda det här felet är:<ul><li> Öka appens versionsnummer och bygg sedan om och signera paketet på nytt.</li><li> Ta bort det gamla paketet för varje användare i systemet innan du installerar det nya paketet.</li></ul> Mer information finns i [Felsöka paketering, distribution och frågor för Windows Store-appar](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x87D1041C    |    Programinstallationen lyckades men programmet identifieras inte. Appen har distribuerats av Intune och sedan avinstallerats. Orsaker till att appen avinstalleras är:<ul><li> Slutanvändaren avinstallerade appen.</li><li> Identitetsinformationen i paketet matchar inte vad enheten rapporterar för felaktiga appar.</li><li>Vid automatiskt uppdaterade MSI:er matchar produktversionen inte appinformationen när den har uppdaterats utanför Intune.</li></ul> Be användaren att installera om appen via företagsportalen. Observera att de appar som krävs ominstalleras automatiskt nästa gång enheten checkas in.    |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Felsöka appar från Microsoft Store

Informationen i avsnittet [Troubleshooting packaging, deployment, and query of Windows Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (Felsöka paketering, distribution och frågor för Windows Store-appar) hjälper dig att felsöka vanliga problem som kan uppstå när du installerar appar från Microsoft Store, oavsett om du gör det med Intune eller på annat sätt.

## <a name="next-steps"></a>Nästa steg

- Ytterligare information om felsökning av Intune information finns i [Använd felsökningsportalen för att hjälpa företagets användare](help-desk-operators.md). 
- Lär dig om kända problem i Microsoft Intune. Mer information finns i [Kända problem i Microsoft Intune](known-issues.md).
- Behöver du mer hjälp? Se [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).
