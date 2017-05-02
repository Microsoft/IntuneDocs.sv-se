---
title: "Felsöka villkorlig åtkomst| Microsoft Docs"
description: "Vad du kan göra om användarna inte lyckas komma åt resurser via villkorlig åtkomst i Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: cc14d6a44b3dcb6234cc77cb463098a9d2f4c5b8
ms.lasthandoff: 04/14/2017


---

# <a name="troubleshoot-conditional-access"></a>Felsöka villkorlig åtkomst

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Vanligtvis försöker en användare få åtkomst till e-post eller SharePoint och får då ett meddelande med en uppmaning om att registrera enheten. Meddelandet dirigerar användaren till företagsportalen.

I det här avsnittet beskrivs vad du kan göra om användarna inte kan få åtkomst till resurser via villkorlig åtkomst i Intune.


## <a name="the-basics-for-success-in-conditional-access"></a>Grunder i hur du får en lyckad villkorlig åtkomst

För att villkorlig åtkomst ska fungera måste följande villkor uppfyllas:

-    Enheten måste hanteras av Intune.
-    Enheten måste vara registrerad i Azure Active Directory. Normalt sker registreringen automatiskt vid Intune-registreringen.
-    Enheten måste vara kompatibel med dina Intune-efterlevnadsprinciper, för både enheten och enhetsanvändaren.  Om det inte finns några efterlevnadsprinciper räcker det med registrering i Intune.
-    Exchange ActiveSync måste vara aktiverat på enheten om användaren tar emot e-post via enhetens inbyggda e-postklient i stället för via Outlook.     Detta sker automatiskt för iOS-, Windows Phone- och Android/KNOX Standard-enheter.
-    Intune Exchange Connector måste vara korrekt konfigurerad. Mer information finns i [Felsöka Exchange Connector i Microsoft Intune](troubleshoot-exchange-connector.md).

Du kan se dessa villkor för varje enhet i Azure-hanteringsportalen och i inventeringsrapporten för enheten.

## <a name="enrollment-issues"></a>Registreringsproblem

 -  Enheten är inte registrerad. Problemet kan åtgärdas genom att registrera enheten.
 -  Användaren har registrerat enheten men anslutningen till arbetsplatsen misslyckades. Användaren bör uppdatera registreringen från företagsportalen.

## <a name="compliance-issues"></a>Efterlevnadsproblem

 -  Enheten uppfyller inte kraven för Intune-principen. Vanliga problem är krav på kryptering och lösenord. Användaren omdirigeras till företagsportalen där de kan konfigurera enheten så att den uppfyller kraven.
 -  Det kan ta en stund innan efterlevnadsinformationen har registrerats för enheten. Vänta några minuter och försök igen.
 -  För iOS-enheter:
     -   En befintlig e-postprofil som skapats av användaren blockerar distributionen av en profil som skapats av Intune-administratören. Det här är ett vanligt problem eftersom iOS-användare vanligtvis skapar en e-postprofil och sedan gör registreringen. Företagsportalen informerar användaren om att de inte uppfyller kraven på grund av den manuellt konfigurerade e-postprofilen, och användaren uppmanas att ta bort profilen. Användaren bör ta bort e-postprofilen så att Intune-profilen kan distribueras. För att förhindra det här problemet ber du användarna att göra registreringen utan att installera en e-postprofil så att Intune kan distribuera profilen.
     -     En iOS-enhet kan fastna i ett tillstånd där efterlevnaden kontrolleras, vilket hindrar användaren från att påbörja en ny incheckning. Detta kan åtgärdas genom att starta om företagsportalen så att kompatibilitetstillståndet motsvarar enhetstillståndet i Intune. När alla data har samlats in från en enhetssynkronisering går efterlevnadskontrollen snabbt (mindre än en halv sekund i genomsnitt).

        Orsaken till att enheter fastnar i det här tillståndet är vanligtvis att de har problem med att ansluta till tjänsten eller att synkroniseringen tar lång tid.  Om problemet kvarstår i olika nätverkskonfigurationer (mobilnät, Wi-Fi, VPN) efter att du har startat om enheterna och har verifierat att SSP är uppdaterad på enheten, kontaktar du Microsoft Support enligt beskrivningen i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

 - För Android-enheter:
     - Vissa Android-enheter kan verka vara krypterade, men företagsportalappen identifierar dessa enheter som inte krypterade. 
    
        -    Enheter i det här tillståndet kräver att användaren anger ett lösenord för säker start. Användaren ser ett meddelande om enheten från företagsportalappen som ber användaren att ange ett lösenord för att starta enheten. När du tryckt på enhetsmeddelandet och bekräftat den befintliga PIN-koden eller lösenordet väljer du alternativet att **kräva PIN-kod för att starta enheten** på skärmen för **säker start**. Tryck sedan på knappen **Kontrollera efterlevnad** för enheten från företagsportalappen. Enheten bör nu identifieras som krypterad.
    
        -     Vissa enhetstillverkare krypterar sina enheter med en standard-PIN-kod i stället för den hemliga PIN-koden som användaren anger. Intune identifierar kryptering med standard-PIN-koden som osäker eftersom den här metoden för kryptering kan utsätta data på enheten för risker i form av användare med tillgång till enheten som vill vålla skada. Om det här är ett problem kan du överväga att använda [appskyddsprinciper](https://docs.microsoft.com/intune/deploy-use/azure-portal-for-microsoft-intune-mam-policies).

## <a name="policy-issues"></a>Principfrågor

När du skapar en efterlevnadsprincip och länkar den till en e-postprincip måste båda principerna distribueras till samma användare. Därför bör du tänka dig för när du planerar vilka principer som ska distribueras till olika grupper. Användare med endast en tillämpad princip märker troligtvis att deras enheter inte uppfyller kraven.


## <a name="exchange-activesync-issues"></a>Problem med Exchange ActiveSync

### <a name="compliant-android-device-gets-quarantine-notice"></a>Karantänmeddelande visas i en kompatibel Android-enhet
- En Android-enhet som är registrerad och uppfyller efterlevnadskraven kan fortfarande få ett karantänmeddelande när de försöker komma åt företagsresurser. Innan användarna väljer länken **Börja** måste de se till att företagsportalen inte är öppen när de försöker komma åt resurserna. Användarna måste stänga företagsportalen, försöka att få åtkomst till resurserna på nytt och sedan välja länken **Börja**.

### <a name="retired-device-continues-to-have-access"></a>En pensionerad enheten har fortfarande åtkomst.
- När du använder Exchange Online kan en pensionerad enhet fortfarande ha åtkomst flera timmar efter att den tagits bort. Det beror på att Exchange cachelagrar åtkomsträttigheter i 6 timmar. Överväg andra sätt att skydda data på pensionerade enheter i det här scenariot.

### <a name="device-is-compliant-and-registered-with-aad-but-still-blocked"></a>Enheten är kompatibel och registrerad i AAD men är ändå blockerad
- Ibland är etableringen av Exchange ActiveSync ID (EASID) på AAD fördröjd. Begränsning är en vanlig orsak till detta problem. Vänta några minuter och försök igen.

### <a name="device-blocked"></a>Enheten är blockerad

En enhet kan blockeras från villkorlig åtkomst utan att du får ett aktiveringsmeddelande via e-post.

- Finns det en Exchange-standardregel som placerar enheter i karantän eller som blockerar dem? Om en standardregel blockerar enheter eller placerar dem i karantän får enheterna inte aktiveringsmeddelandet via e-post från Exchange Connector. Detta beteende är inbyggt.
- Är meddelandekontot korrekt konfigurerat enligt beskrivningen i avsnittet om grundläggande konfiguration?
- Finns enheten som en Exchange ActiveSync-enhet i Intune-administratörskonsolen? Om inte, är det troligt att enhetsidentifieringen misslyckas, förmodligen på grund av ett Exchange Connector-synkroniseringsproblem. Läs avsnittet Exchange ActiveSync-enheten identifieras inte från Exchange.
- Sök i Exchange Connector-loggarna efter någon SendEmail-aktivitet (SkickaEpost) och sök efter fel. Du kan exempelvis söka efter kommandot SendEmail from notification account to useremail (SkickaE-post från meddelandekontot till AnvEpost).
- Exchange Connector skickar aktiveringsmeddelandet innan enheten blockeras. Om enheten är offline kanske den inte kan ta emot aktiveringsmeddelandet. Kontrollera om enhetens e-postklient använder hämtningsmetoden Push i stället för Pull eftersom det kan göra att användaren inte får meddelandet. Byt till Pull och se om enheten får e-postmeddelandet.

## <a name="non-compliant-device-not-blocked"></a>En inkompatibel enhet blockeras inte

Om en enhet har åtkomst trots att den är inkompatibel vidtar du följande åtgärder.

- Granska dina mål- och undantagsgrupper. Om användare inte är i rätt målgrupp, eller är i en undantagsgrupp, blockeras de inte. Efterlevnad kontrolleras endast för enheter som har användare i en målgrupp.
- Kontrollera att enheten identifieras. Pekar Exchange Connector på en Exchange 2010-klientåtkomstserver när användaren har en Exchange 2013-servern? I så fall kan Intune inte känna till enhetens anslutning till Exchange om Exchange-standardregeln är Tillåt, även om användaren är i målgruppen.
- Kontrollera om enhetens finns/enhetens åtkomststatus i Exchange:
    - Använd denna PowerShell-cmdlet om du vill hämta en lista över alla mobila enheter för en postlåda: "Get-ActiveSyncDeviceStatistics -mailbox mbx'. Om enheten inte visas har den inte åtkomst till Exchange.
    - Om enheten visas använder du cmdleten Get-CASmailbox -identity:’upn’ | fl för att få detaljerad information om enhetens åtkomststatus och ange den informationen till Microsoft Support.

## <a name="before-you-open-a-support-ticket"></a>Innan du skapar ett supportärende
Om du inte kan lösa problemet med dessa felsökningsanvisningar kanske du ombeds skicka information till Microsoft Support, till exempel OWA-postlådeloggar eller Exchange Connector-loggar.

### <a name="collecting-owa-mailbox-logs"></a>Samla in OWA-postlådeloggar

1. Logga in via OWA och välja inställningsikonen (kugghjulet) bredvid ditt namn i det övre högra hörnet.
2. Välj **Alternativ**.
3. Välj **Telefon** (det kan stå **Mobila enheter**) i kolumnen till vänster.
4. Välj **Mobila enheter** på den översta menyn.
5. Välj en enhet i listan och sedan **Starta loggning**.
6. Välj **Ja** i popup-fönstret.
7. Utför den åtgärd som har orsakat problemet, så att du kan återskapa det.
8. Vänta 1 till 2 minuter och gå sedan tillbaka till telefonlistan i OWA. Kontrollera att din telefon är markerad i listan och välj **Hämta logg** på den översta menyn.
9. Nu får du ett e-postmeddelande med en bilaga från dig själv. När du skapar ett supportärende anger du innehållet i e-postmeddelandet till Microsoft Support.

### <a name="exchange-connector-logs"></a>Exchange Connector-loggar

#### <a name="general-log-information"></a>Allmän logginformation
Du kan se Exchange Connector-loggar med [Server Trace Viewer Tool](visningsverktyg för serverspårning) (https://msdn.microsoft.com/library/ms732023(v=vs.110).aspx'). Det här verktyget kräver att du hämtar Windows Server SDK.

>[!NOTE]
>Loggarna finns i C:\ProgramData\Microsoft\Windows Intune Exchange Connector\Logs. Loggarna finns i en serie med 30 loggfiler som börjar med *Connector0.log* och slutar med *Connector29.log*. När 10 MB data har samlats i en logg går loggningen vidare till nästa logg. När loggningen når Connector29 börjar den om med Connector0 igen och de tidigare loggfilerna skrivs över.

#### <a name="locating-sync-logs"></a>Hitta synkroniseringsloggar

-    Leta upp en fullständig synkronisering i loggarna genom att söka efter **fullständig synkronisering**. Början av en fullständig synkronisering markeras med följande text:

    'Handling command: Getting the mobile device list without a time filter (full sync) for <number> users` (Hanteringskommando: Hämtar listan med mobila enheter utan tidsfilter (fullständig synkronisering) för <number> användare)

    Slutet på loggen för en fullständig synkronisering ser ut så här:

    Getting the mobile device list without a time filter (full sync) for 4 users completed successfully. (Hämtningen av listan med mobila enheter utan tidsfilter (fullständig synkronisering) för 4 användare har slutförts.) Details: Inventory command result - Devices synced: 0 Commmand ID: commandIDGUID' Exchange health: 'Server health 'Name: 'PowerShellExchangeServer: <Name=mymailservername>' Status: Connected',' (Information: Resultat för inventeringskommando - Enheter som synkroniserats: 0 Kommando-ID: commandIDGUID' Exchange-hälsa: 'Serverhälsa 'Namn: 'PowerShellExchangeServer: <Namn=mitte-postservername>' Status: Ansluten',')

-    Leta reda på en snabbsynkronisering (deltasynkronisering) i loggarna genom att söka efter **quick sync (snabbsynkronisering)**.

##### <a name="exceptions-in-get-next-command"></a>Undantag i Get next command (Hämta nästa kommando)
Kontrollera om det finns undantag i **Get next command** (Hämta nästa kommando) i Exchange Connector-loggarna och skicka dessa till Microsoft Support.

#### <a name="verbose-logging"></a>Utförlig loggning

Så här aktiverar du utförlig loggning:

1.    Öppna konfigurationsfilen för Exchange Connector-spårning. Filen finns på: %ProgramData%\Microsoft\Windows Intune Exchange Connector\TracingConfiguration.xml.
2.    Leta reda på TraceSourceLine med följande nyckel: OnPremisesExchangeConnectorService
3.    Ändra värdet för **SourceLevel**-noden från **Warning ActivityTracing** (standardvärdet) till **Verbose ActivityTracing** (se nedan).

    <TraceSourceLine>
          <Key xsi:type="xsd:string">OnPremisesExchangeConnectorService</Key>
          <Value xsi:type="TraceSource">
            <SourceLevel>All</SourceLevel>
            <Listeners>
              <Listener>
                <ListenerType>CircularTraceListener</ListenerType>
                <SourceLevel>Verbose ActivityTracing</SourceLevel>
                <FileSizeQuotaInBytes>10000000</FileSizeQuotaInBytes>
                <FileName>Microsoft\Windows Intune Exchange Connector\Logs\Connector.svclog</FileName>
                <FileQuota>30</FileQuota>
              </Listener>
            </Listeners>
          </Value>
    </TraceSourceLine>



### <a name="next-steps"></a>Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

