---
title: Fel och statuskoder i Microsoft Intune – Azure | Microsoft Docs
description: Visa en lista över fel, statuskod, beskrivningar och lösningar vid användning av MDM-hanterade enheter, få åtkomst till företagets resurser, fel på iOS-enheter och OMA-svarsfel i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 40622ced-6029-4abf-873e-b51d2b51934c
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17a8ebfcad2bcf485771f26184377aeb2c4bf4e1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509802"
---
# <a name="common-error-codes-and-descriptions-in-microsoft-intune"></a>Vanliga felkoder och beskrivningar i Microsoft Intune

Den här artikeln innehåller vanliga fel, statuskoder, beskrivningar och möjliga lösningar vid åtkomst till organisationens resurser. Använd den här informationen för att felsöka åtkomstproblem vid användning av Microsoft Intune.

Om du behöver supporthjälp kan du läsa informationen om att [få support för Microsoft Intune](../get-support.md).

## <a name="status-codes-for-mdm-managed-windows-devices"></a>Statuskoder för MDM-hanterade Windows enheter

|Statuskod|Felmeddelande|Vad bör jag göra|
|---------------|-----------------|--------------|
|10 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Installation pågår||
|20 (APP_CI_ENFORCEMENT_IN_PROGRESS_WAITING_CONTENT)|Väntar på innehåll||
|30 (APP_CI_ENFORCEMENT_ERROR_RETRIEVING_CONTENT)|Hämtar innehåll|Möjlig orsak: Jobbstatus 30 visar att en användare misslyckades med att ladda ned en app.<br /><br />Troliga orsaker till detta kan vara:<br /><br />Enheten förlorade internetanslutning medan nedladdningen pågick.<br /><br />Certifikatet som utfärdades för enheten vid registreringen kan ha löpt ut.<br /><br />Lösningar:<br /><br />Starta företagsapparna från kontrollpanelen på enheten för att kontrollera att enhetens certifikat inte har löpt ut. Om det har det måste du omregistrera enheten.<br /><br />Kontrollera att enheten är ansluten till internet och försök att begära appen igen.|
|40 (APP_CI_ENFORCEMENT_IN_PROGRESS_CONTENT_DOWNLOADED)|Nedladdning av innehåll klart||
|50 (APP_CI_ENFORCEMENT_IN_PROGRESS_INSTALLING)|Installation pågår||
|60 (APP_CI_ENFORCEMENT_ERROR_INSTALLING)|Ett fel med installationen uppstod|Installationen av appen misslyckades efter nedladdning.<br /><br />Kodsigneringscertifikatet som appen undertecknades med finns inte på enheten.<br /><br />Programmet är beroende av ett ramverk som inte är installerat på enheten.<br /><br />Se till att kodsigneringscertifikatet som appen undertecknats med finns på enheten och kontrollera med administratören att ett sådant certifikat utfärdats för alla företagets registrerade Windows RT-enheter.<br /><br />Om installationsproblemet inte beror på ett saknat ramverk, måste administratören återpublicera programmet genom att paketera ramverket tillsammans med applikationspaketet.<br /><br />Det nedladdade applikationspaketet är inte giltigt, det kan ha skadats, eller är kanske inte kompatibelt med enhetens OS-version.|
|70 (APP_CI_ENFORCEMENT_SUCCEEDED)|Installationen lyckades||
|80 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Avinstallation pågår||
|90 (APP_CI_ENFORCEMENT_ERROR)|Avinstallationsfel inträffade.||
|100 (APP_CI_ENFORCEMENT_SUCCEEDED)|Avinstallationen lyckades||
|110 (APP_CI_ENFORCEMENT_ERROR)|Hash-matchningsfel i innehållet||
|120 (APP_CI_ENFORCEMENT_ERROR)|SLK / sidladdning är inte aktiverad||
|130 (APP_CI_ENFORCEMENT_ERROR)|Installation av MSADP misslyckades||
|Ingen status (APP_CI_ENFORCEMENT_UNKNOWN)|saknas|Statusen är för närvarande okänd.|

## <a name="company-resource-access-common-errors"></a>Åtkomst till företagets resurser

|Statuskod|Hexadecimal felkod|Felmeddelande|
|---------------|--------------------------|-----------------|
|-2016281101|0x87D1FDF3|MDM CRP-begäran hittades inte|
|-2016281102|0x87D1FDF2|Webbadressen för NDES hittades inte|
|-2016281103|0x87D1FDF1|MDM CRP-certifikatet hittades inte|
|-2016281104|0x87D1FDF0|MDM CI-certifikat hittades inte|
|-2016281105|0x87D1FDEF|Det gick inte att utvärdera regeln|
|-2016281106|0x87D1FDEE|Ej tillämplig på grund av förlorad konfliktlösning|
|-2016281107|0x87D1FDED|Inställningar som inte stöds har upptäckts i källan|
|-2016281108|0x87D1FDEC|Referensinställning hittades inte i CI|
|-2016281109|0x87D1FDEB|Konverteringen av datatyp misslyckades|
|-2016281110|0x87D1FDEA|Ogiltig parameter för CIM inställning|
|-2016281111|0x87D1FDE9|Ej tillämpad för denna enhet|
|-2016281112|0x87D1FDE8|Åtgärden misslyckades|
|-2016330905|0x87D13B67|Okänd appstatus|
|-2016330906|0x87D13B66|Appen hanteras, men har tagits bort av användaren|
|-2016330907|0x87D13B65|Enheten löser in inlösningskoden|
|-2016330908|0x87D13B64|Appinstallationen misslyckades.|
|-2016330909|0x87D13B63|Användaren avvisade erbjudandet att uppdatera appen|
|-2016330910|0x87D13B62|Användaren avvisade erbjudandet att installera appen|
|-2016330911|0x87D13B61|Användaren installerade appen innan en hanterad appinstalltion kunde genomföras|
|-2016330912|0x87D13B60|Appen är planerad för installation, men behöver en inlösenkod för att slutföra transaktionen|
|-2016341109|0x87D1138B|iOS-enheten har returnerat ett fel|
|-2016341110|0x87D1138A|iOS-enheten har avvisat kommandot på grund av felaktigt format|
|-2016341111|0x87D11389|iOS-enheten har returnerat en oväntad inaktiv status|
|-2016341112|0x87D11388|iOS-enheten är förnärvarande upptagen|

## <a name="errors-returned-by-ios-devices"></a>iOS-enheterna returnerade fel

### <a name="company-portal-errors"></a>Företagsportalfel

|Feltext i företagsportalen|HTTP-statuskod|Ytterligare felinformation|
|---|---|---|
|__Internt serverfel__ <br>Det verkar som att du inte kunde kontakta oss på grund av ett internt fel på vår server. Försök igen och kontakta IT-administratören om problemet kvarstår.|Fel 500|Det här felet beror sannolikt på problem i Intune-tjänsten. Problemet ska lösas hos Intune och beror förmodligen inte på något fel hos kunden.|
|__Tillfälligt otillgänglig__ <br>Det verkar som det gick inte att nå oss eftersom tjänsten för tillfället är otillgänglig. Försök igen och kontakta IT-administratören om problemet kvarstår.|Fel 503|Detta beror troligen på ett tillfälligt Intune-tjänstproblem, till exempel att underhåll utförs i tjänsten. Problemet ska lösas hos Intune och beror förmodligen inte på något fel hos kunden.|
|__Det gick inte att ansluta till servern__ <br>Det verkar som om du inte kan nå oss. Försök igen och kontakta IT-administratören om problemet kvarstår.|Inte associerad med någon HTTP-statuskod|Det går inte att upprätta någon säker anslutning till servern, förmodligen på grund av ett SSL-problem med de certifikat som används. Det här problemet kan bero på kundkonfigurationer som inte är kompatibla med Apples krav för App Transport Security (ATS).|
|__Något verkar ha gått fel__ <br>Företagsportalens klient kunde inte läsas in. Försök igen och kontakta IT-administratören om problemet kvarstår.|Fel 400|Fel med en HTTP-statuskod i 400-intervallet som inte har ett mer specifikt felmeddelande visar den här felkoden. Det här är ett klientfel i företagsportalappen för iOS.|
|__Det går inte att nå servern__ <br>Det verkar som om du inte kan nå oss. Försök igen och kontakta IT-administratören om problemet kvarstår.|Fel 500|Fel med en HTTP-statuskod i 500-intervallet som inte har ett mer specifikt felmeddelande visar den här felkoden. Det här är ett tjänstfel som uppstår i Intune-tjänsten.|

### <a name="service-errors"></a>Tjänstfel

|Statuskod|Hexadecimal felkod|Felmeddelande|
|---------------|--------------------------|-----------------|
|-2016299111|0x87D1B799|Internt fel|
|-2016299112|0x87D1B798|Internt fel|
|-2016300111|0x87D1B3B1|36001:(internt fel)|
|-2016300112|0x87D1B3B0|36000:Mobil enhet redan konfigurerad|
|-2016301110|0x87D1AFCA|35002:Flera teckensnitt i en enda nyttolast.|
|-2016301111|0x87D1AFC9|35001:Teckensnittsinstallation misslyckades|
|-2016301112|0x87D1AFC8|35000:Ogiltiga teckensnittsdata|
|-2016302109|0x87D1ABE3|34003:Ogiltigt Kerberos-huvudnamn|
|-2016302110|0x87D1ABE2|34002:Kerberos-huvudnamn fattas|
|-2016302111|0x87D1ABE1|34001:Ogiltigt matchningsmönster för URL|
|-2016302112|0x87D1ABE0|34000:matchningsmönstret har identiferat ogiltig app|
|-2016304112|0x87D1A410|32000:För många appar|
|-2016305111|0x87D1A029|31001:Det går inte att tillämpa inställningar|
|-2016305112|0x87D1A028|31000:Det går inte att tillämpa autentiseringsuppgift|
|-2016306111|0x87D19C41|30001:Tidsgränsen uppnåddes|
|-2016306112|0x87D19C40|30000:Autentisering misslyckades|
|-2016307109|0x87D1985B|29003:Felaktiga certifikatuppgifter|
|-2016307110|0x87D1985A|29002:|
|-2016307111|0x87D19859|29001:|
|-2016307112|0x87D19858|29000:Enheten är inte övervakad|
|-2016308110|0x87D19472|28002:Det går inte att ställa in bakgrund|
|-2016308111|0x87D19471|28001:Felaktig bakgrundsbild|
|-2016308112|0x87D19470|28000:Okänt objekt|
|-2016310111|0x87D18CA1|26001:Filnivåkryptering stöds inte|
|-2016310112|0x87D18CA0|26000:Blocknivåkryptering stöds inte|
|-2016311110|0x87D188BA|25002:Kan inte ta bort|
|-2016311111|0x87D188B9|25001:Kan inte installera|
|-2016311112|0x87D188B8|25000:Felaktig profil|
|-2016312109|0x87D184D3|24003:Felaktig slutprofil|
|-2016312110|0x87D184D2|24002:Felaktig identitetsinmatning|
|-2016312111|0x87D184D1|24001:Kan inte skriva under attributordlista|
|-2016312112|0x87D184D0|24000:Kan inte skapa attributordlista|
|-2016313110|0x87D180EA|23002:Ogiltigt servercertifikat|
|-2016313111|0x87D180E9|23001:Felkatigt serversvar|
|-2016313112|0x87D180E8|23000:Felaktig identitet|
|-2016314099|0x87D17D0D|22013:Felaktigt PKIOperation-svar|
|-2016314100|0x87D17D0C|22012:Kan inte spara CACertificate|
|-2016314101|0x87D17D0B|22011:Kan inte generera CSR|
|-2016314102|0x87D17D0A|22010:Kan inte spara tillfällig identitet|
|-2016314103|0x87D17D09|22009:Kan inte skapa tillfällig identitet|
|-2016314104|0x87D17D08|22008:Kan inte skapa identitet|
|-2016314105|0x87D17D07|22007:Ogiltigt undertecknat certifikat|
|-2016314106|0x87D17D06|22006:Otillräckligt CACaps|
|-2016314107|0x87D17D05|22005:Nätverksfel|
|-2016314108|0x87D17D04|22004:Certifieringskonfigurationen stöds ej|
|-2016314109|0x87D17D03|22003:Ogiltigt RAResponse|
|-2016314110|0x87D17D02|22002:Ogiltigt CAResponse|
|-2016314111|0x87D17D01|22001:Kan inte generera nyckelpar|
|-2016314112|0x87D17D00|22000:Ogiltig nyckelanvändning|
|-2016315105|0x87D1791F|21007:Kan inte verifiera konto|
|-2016315106|0x87D1791E|21006:Kan inte dekryptera certifikat|
|-2016315107|0x87D1791D|21005: Kontot är inte unikt (En e-postprofil finns redan på enheten)|
|-2016315108|0x87D1791C|21004:Kan inte skapa konto|
|-2016315109|0x87D1791B|21003:Inget värdnamn|
|-2016315110|0x87D1791A|21002:Kan inte uppfylla krypteringspolicyn från servern|
|-2016315111|0x87D17919|21001:Kan inte uppfylla policyn från servern|
|-2016315112|0x87D17918|21000:Kan inte hämta policyn från servern|
|-2016316110|0x87D17532|20002:Kontot inte unikt|
|-2016316111|0x87D17531|20001:Inget värdnamn|
|-2016316112|0x87D17530|20000:Kan inte skapa konto|
|-2016317110|0x87D1714A|19002:Kontot inte unikt|
|-2016317111|0x87D17149|19001:Inget värdnamn|
|-2016317112|0x87D17148|19000:Kan inte skapa konto|
|-2016318110|0x87D16D62|18002:Ogiltiga autentiseringsuppgifter|
|-2016318111|0x87D16D61|18001:Onåbar värd|
|-2016318112|0x87D16D60|18000:Okänt fel|
|-2016319110|0x87D1697A|17002:Kontot inte unikt|
|-2016319111|0x87D16979|17001:Inget värdnamn|
|-2016319112|0x87D16978|17000:Kan inte skapa konto|
|-2016320110|0x87D16592|16002:Kontot inte unikt|
|-2016320111|0x87D16591|16001:Inget värdnamn|
|-2016320112|0x87D16590|16000:Det går inte att skapa prenumeration|
|-2016321109|0x87D161AB|15003:Ogiltigt certifikat|
|-2016321110|0x87D161AA|15002:Kan inte låsa nätverkskonfiguration|
|-2016321111|0x87D161A9|15001:Kan inte ta bort VPN|
|-2016321112|0x87D161A8|15000:Kan inte installera VPN|
|-2016322110|0x87D15DC2|14002:Molnkonfiguration finns redan|
|-2016322111|0x87D15DC1|14001:Låst enhet|
|-2016322112|0x87D15DC0|14000:Ogiltigt fält|
|-2016323107|0x87D159DD|13005:Det går inte att ställa in proxy|
|-2016323108|0x87D159DC|13004:Det går inte att ställa in EAP|
|-2016323109|0x87D159DB|13003:Det går inte att skapa WiFi-konfiguration|
|-2016323110|0x87D159DA|13002:Lösenord krävs|
|-2016323111|0x87D159D9|13001:Användarnamn krävs|
|-2016323112|0x87D159D8|13000:Kan inte installera|
|-2016324070|0x87D1561A|12042:Okänd kod för nationella inställningar|
|-2016324071|0x87D15619|12041:Okänd språkkod|
|-2016324072|0x87D15618|12040:Inloggning till iTunes krävs|
|-2016324073|0x87D15617|12039:(oanvänd)|
|-2016324074|0x87D15616|12038:App inte hanterad|
|-2016324075|0x87D15615|12037:Ogiltig inlösningskod|
|-2016324076|0x87D15614|12036:Kan inte ta bort appen med nuvarande status|
|-2016324077|0x87D15613|12035:Appen kan inte köpas|
|-2016324078|0x87D15612|12034:URL är inte HTTPS|
|-2016324079|0x87D15611|12033:Ogiltigt manifest|
|-2016324080|0x87D15610|12032:För många appar i manifest|
|-2016324081|0x87D1560F|12031:Appinstallation inaktiverad|
|-2016324082|0x87D1560E|12030:Ogiltigt URL|
|-2016324083|0x87D1560D|12029:App inte hanterad|
|-2016324084|0x87D1560C|12028:Väntar inte på åtgärd|
|-2016324085|0x87D1560B|12027:Inte en app|
|-2016324086|0x87D1560A|12026:App redan i kö|
|-2016324087|0x87D15609|12025:App redan installerad|
|-2016324088|0x87D15608|12024:Kunde inte validera appmanifest|
|-2016324089|0x87D15607|12023:Kunde inte validera app-iD|
|-2016324090|0x87D15606|12022:Ogiltigt ämne|
|-2016324091|0x87D15605|12021:Ogiltig typbegäran|
|-2016324092|0x87D15604|12020:Ej auktoriserad av server|
|-2016324093|0x87D15603|12019:Det går inte att kopiera depositionshemlighet|
|-2016324094|0x87D15602|12018:Det går inte att kopiera data för depositionsnyckelhållare|
|-2016324095|0x87D15601|12017:Det går inte att skapa spärrade nyckeldatauppgifter|
|-2016324096|0x87D15600|12016:Saknad identitet|
|-2016324097|0x87D155FF|12015:Kan inte hämta push-token|
|-2016324098|0x87D155FE|12014:Etableringssprofil inte hanterad|
|-2016324099|0x87D155FD|12013:Profil inte hanterad|
|-2016324100|0x87D155FC|12012:MDM-ersättningsmatchningsfel|
|-2016324101|0x87D155FB|12011:Ogiltig MDM-konfiguration|
|-2016324102|0x87D155FA|12010:Internt inkonsekvensfel|
|-2016324103|0x87D155F9|12009:Ogiltig ersättningsprofil|
|-2016324104|0x87D155F8|12008:Felaktigt utformad begäran|
|-2016324105|0x87D155F7|12007:Inte tillåten|
|-2016324106|0x87D155F6|12006:Vägrad omdirigering|
|-2016324107|0x87D155F5|12005:Kan inte hitta certifikat|
|-2016324108|0x87D155F4|12004:Ogiltigt push-certifikat|
|-2016324109|0x87D155F3|12003:Felaktigt utmaningssvar|
|-2016324110|0x87D155F2|12002:Kan inte checka in|
|-2016324111|0x87D155F1|12001:Flera MDM-instanser|
|-2016324112|0x87D155F0|12000:Ogiltiga åtkomsträttigheter|
|-2016325111|0x87D15209|11001:Anpassad APN redan installerad|
|-2016325112|0x87D15208|11000:Kan inte installera APN|
|-2016326111|0x87D14E21|10001:Ogiltig undertecknare|
|-2016326112|0x87D14E20|10000:Kan inte installera standardvärden|
|-2016327106|0x87D14A3E|9006:Certifikatet är inte en identitet|
|-2016327107|0x87D14A3D|9005:Certifikat är felaktigt|
|-2016327108|0x87D14A3C|9004:Kan inte spara rotcertifikat|
|-2016327109|0x87D14A3B|9003:Kan inte spara WAPI-data|
|-2016327110|0x87D14A3A|9002:Kan inte spara certifikat|
|-2016327111|0x87D14A39|9001:För många certifikat i en inmatning|
|-2016327112|0x87D14A38|9000:Ogiltigt lösenord|
|-2016328112|0x87D14650|8000:Kan inte installera Web Clip|
|-2016329105|0x87D1426F|7007:SMTP-kontot är felkonfigurerat|
|-2016329106|0x87D1426E|7006:POP-kontot är felkonfigurerat|
|-2016329107|0x87D1426D|7005:IMAP-kontot är felkonfigurerat|
|-2016329108|0x87D1426C|7004:SMIME-certifikatet är felaktigt|
|-2016329109|0x87D1426B|7003:SMIME-certifikatet kan inte hittas|
|-2016329110|0x87D1426A|7002:Okänt fel uppstod under valideringen|
|-2016329111|0x87D14269|7001:Ogiltiga autentiseringsuppgifter|
|-2016329112|0x87D14268|7000:Värden är inte åtkomlig|
|-2016330110|0x87D13E82|6002:Det går inte att skapa fråga|
|-2016330111|0x87D13E81|6001:Tom sträng|
|-2016330112|0x87D13E80|6000:Nyckelringssystemfel|
|-2016331097|0x87D13AA7|5015:Det går inte att ställa in anståndsperiod|
|-2016331098|0x87D13AA6|5014:Det går inte att ställa in lösenordskod|
|-2016331099|0x87D13AA5|5013:Det går inte att rensa lösenordskod|
|-2016331100|0x87D13AA4|5012:(oanvänd)|
|-2016331101||5011:Fel lösenordskod|
|-2016331102||5010:Låst enhet|
|-2016331103|0x87D13AA4|5009:(oanvänd)|
|-2016331104|0x87D13AA0|5008:Lösenordskod för ny|
|-2016331105|0x87D13A9F|5007:Lösenordskod har gått ut|
|-2016331106|0x87D13AA3|5006:Lösenordskoden måste ha alfatecken|
|-2016331107|0x87D13A9D|5005:Lösenordskoden måste ha nummer|
|-2016331108|0x87D13A9C|5004:Lösenordskoden har konsekutiva tecken|
|-2016331109|0x87D13A9B|5003:Lösenordskoden har upprepade tecken|
|-2016331110|0x87D13A9A|5002:För få avancerade tecken|
|-2016331111|0x87D13A99|5001:För få unika avancerade tecken|
|-2016331112|0x87D13A98|5000:Lösenordskod för kort|
|-2016332093|0x87D136C3|4019:Flera App Lock-nyttolaster|
|-2016332094|0x87D136C2|4018:Flera nyttolaster för APN eller mobila enheter|
|-2016332095|0x87D136C1|4017:Flertal globala HTTPProxy-nyttolaster|
|-2016332096|0x87D136C0|4016:(Internt fel)|
|-2016332097|0x87D136BF|4015:Ersättningsprofilen innehåller inte en MDM-nyttolast|
|-2016332098|0x87D136BE|4014:Ingen enhetsidentitet tillgänglig|
|-2016332099|0x87D136BD|4013:Uppdatering misslyckades|
|-2016332100|0x87D136BC|4012:Profil är inte uppdateringsbar|
|-2016332101|0x87D136BB|4011:Slutprofilen är inte en konfigurerad profil|
|-2016332102|0x87D136BA|4010:Den uppdaterade profilen har inte samma identifiering|
|-2016332103|0x87D136B9|4009:Låst enhet|
|-2016332104|0x87D136B8|4008:Certifikatmatchningsfel|
|-2016332105|0x87D136B7|4007:Okänt filformat|
|-2016332106|0x87D136B6|4006:Profilens borttagningsdatum har passerats|
|-2016332107|0x87D136B5|4005:Lösenordskoden uppfyller inte kraven|
|-2016332108|0x87D136B4|4004:Användaren avbröt installationen|
|-2016332109|0x87D136B3|4003:Profilen är inte i kö för installation|
|-2016332110|0x87D136B2|4002:Duplikat UUID|
|-2016332111|0x87D136B1|4001:Installationsfel|
|-2016332112|0x87D136B0|4000:Det går inte att tolka profilen|
|-2016333111|0x87D132C9|3001:Inkonsekvent värdejämförelse (internt fel)|
|-2016333112|0x87D132C8|3000:Inkonsekvent begränsning (internt fel)|
|-2016334108|0x87D12EE4|2004:Fältvärdet stöds inte|
|-2016334109|0x87D12EE3|2003:Felaktig datauppgift i fältet|
|-2016334110|0x87D12EE2|2002:Obligatoriskt fält saknas|
|-2016334111|0x87D12EE1|2001:Nyttolastversionen stöds inte|
|-2016334112|0x87D12EE0|2000:Felaktigt utformad nyttolast|
|-2016335102|0x87D12B02|1010:Fältvärdet stöds inte|
|-2016335103|0x87D12B01|1009:Profilinstallationsfel|
|-2016335104|0x87D12B00|1008:Inga unika nyttolastidentifierare|
|-2016335105|0x87D12AFF|1007:Inga unika UUID:er|
|-2016335106|0x87D12AFE|1006:Kan inte dekryptera|
|-2016335107|0x87D12AFD|1005:Tom profil|
|-2016335108|0x87D12AFC|1004:Felaktig underskrift|
|-2016335109|0x87D12AFB|1003:Felaktig datauppgift i fältet|
|-2016335110|0x87D12AFA|1002:Obligatoriskt fält saknas|
|-2016335111|0x87D12AF9|1001:Profilversionen stöds inte|
|-2016335112|0x87D12AF8|1000:Felaktigt utformad profil|

## <a name="oma-response-codes"></a>OMA-svarskoder

|Statuskod|Hexadecimal felkod|Felmeddelande|
|---------------|--------------------------|-----------------|
|-2016344008|0x87D10838|(1404): Certifikatåtkomst nekades|
|-2016344009|0x87D10837|(1403): Certifikatet hittades inte|
|-2016344010|0x87D10836|DCMO(1402): Åtgärden misslyckades|
|-2016344011|0x87D10835|DCMO(1401): Användaren valde att inte acceptera åtgärden|
|-2016344012|0x87D10834|DCMO(1400): Klientfel|
|-2016344108|0x87D107D4|DCMO(1204): Enhetskapacitet är inaktiverat och användaren får inte återaktivera det|
|-2016344109|0x87D107D3|DCMO(1203): Enhetskapacitet är inaktiverat och användaren får inte återaktivera det|
|-2016344110|0x87D107D2|DCMO(1202): Enhetsåtgärden genomfördes men enhetskapaciteten är bortkopplad|
|-2016344111|0xF3FB4D95|DCMO(1201): Enhetsåtgärden genomfördes och enhetskapaciteten är ansluten|
|-2016344112|0x87D107D0|DCMO(1200): Åtgärden genomfördes|
|-2016345595|0x87D10205|Syncml(517): Svaret på ett atomiskt kommando var för stort för att få plats i ett enda meddelande.|
|-2016345596|0x87D10204|Syncml(516): Kommandot fanns i ett atomiskt element och den atomiska åtgärden misslyckades. Detta kommando kunde inte föras tillbaka ordentligt.|
|-2016345598|0x87D10202|Syncml(514): Kommandot SyncML slutfördes inte på grund av att åtgärden avbröts innan kommandot bearbetades.|
|-2016345599|0x87D10201|Syncml(513): Mottagaren stöder inte eller vägrar att stödja den angivna versionen av synkroniseringsprotokollet för SyncML som används i SyncML-meddelandet med begäran.|
|-2016345600|0x87D10200|Syncml(512): Ett programfel inträffade under synkroniseringen.|
|-2016345601|0x87D101FF|Syncml(511): Ett allvarligt fel inträffade på servern när begäran bearbetades.|
|-2016345602|0x87D101FE|Syncml(510): Ett fel inträffade under behandlingen av begäran. Felet beror på ett fel i mottagarens datalagring|
|-2016345603|0x87D101FD|Syncml(509): Reserverat för framtida användning.|
|-2016345604|0x87D101FC|Syncml(508): Ett fel inträffade som kräver en uppdatering av det aktuella synkroniseringstillståndet av klienten med servern.|
|-2016345605|0x87D101FB|Syncml(507): Felet orsakade att alla SyncML-kommandon inom den atomiska elementtypen misslyckades.|
|-2016345606|0x87D101FA|Syncml(506): Ett programfel uppstod när begäran bearbetades.|
|-2016345607|0x87D101F9|Syncml(505): Mottagaren stöder inte eller vägrar att stödja den angivna versionen av SyncML DTD som används i SyncML-meddelandet med begäran.|
|-2016345608|=0x87D101F8|Syncml(504): När mottagaren var gateway eller proxy togs ett svar inte emot i rätt tid från mottagaren ovanför som är angiven i URI:n (t.ex. HTTP, FTP eller LDAP) eller en annan tilläggsmottagare (t.ex. DNS) som krävdes för att få åtkomst vid försöket att slutföra begäran.|
|-2016345609|0x87D101F7|Syncml(503): Mottagaren kan inte hantera begäran på grund av en tillfällig överbelastning eller underhåll av mottagaren.|
|-2016345610|0x87D101F6|Syncml(502): När mottagaren var gateway eller proxy togs ett ogiltigt svar emot från mottagaren ovanför som användes vid ett försök att slutföra begäran.|
|-2016345611|0x87D101F5|Syncml(501): Mottagaren stöder inte kommandot som krävs för att slutföra begäran.|
|-2016345612|0x87D101F4|Syncml(500): Mottagaren stötte på ett oväntat tillstånd som förhindrade att begäran slutfördes|
|-2016345684|0x87D101AC|Syncml(428): Flytten misslyckades|
|-2016345685|0x87D101AB|Syncml(427): Den överordnade kan inte tas bort eftersom den innehåller underordnade.|
|-2016345686|0x87D101AA|Syncml(426): Delar av objekt accepteras inte.|
|-2016345687|0x87D101A9|Syncml(425): Det begärda kommandot misslyckades på grund av att avsändaren inte har rätt ACL-behörighet på mottagaren.|
|-2016345688|0x87D101A8|Syncml(424): Det segmenterade objektet togs emot men storleken för det mottagna objektet överensstämmer inte med storleken som angavs i det första segmentet.|
|-2016345689|0x87D101A7|Syncml(423): Det begärda kommandot misslyckades på grund av att objektet "Ej permanent borttagen" tidigare togs bort permanent på servern.|
|-2016345690|0x87D101A6|Syncml(422): Det begärda kommandot misslyckades på servern på grund av att CGI-skriptningen i LocURI var felaktigt formaterad.|
|-2016345691|0x87D101A5|Syncml(421): Det begärda kommandot misslyckades på servern på grund av att den angivna sökgrammatiken var okänd.|
|-2016345692|0x87D101A4|Syncml(420): Det finns inte tillräckligt med lagringsutrymme för återstående synkroniseringsdata på mottagaren.|
|-2016345693|0x87D101A3|Syncml(419): Klientbegäran skapade en konflikt som löstes genom att serverkommandot vann.|
|-2016345694|0x87D101A2|Syncml(418): Det begärda kommandot för att placera eller lägga till misslyckades på grund av att målet redan finns.|
|-2016345695|0x87D101A1|Syncml(417): Begäran misslyckades denna gång och avsändaren bör försöka senare.|
|-2016345696|0x87D101A0|Syncml(416): Begäran misslyckades på grund av att den angivna byte-storleken i begäran var för stor.|
|-2016345697|0x87D1019F|Syncml(415): Medietyp eller medieformat stöds inte.|
|-2016345698|0x87D1019E|Syncml(414): Det begärda kommandot misslyckades på grund av att mål-URI:n är längre än vad som är möjligt att bearbeta med mottagaren.|
|-2016345699|0x87D1019D|Syncml(413): Mottagaren vägrar att utföra det begärda kommandot eftersom det begärda objektet är större än vad mottagaren kan eller vill bearbeta.|
|-2016345700|0x87D1019C|Syncml(412): Det begärda kommandot misslyckades på mottagaren på grund av att det var ofullständigt eller felaktigt formaterat.|
|-2016345701|0x87D1019B|Syncml(411): Det begärda kommandot måste åtföljas av information om byte-storlek eller längd i metaelementtypen.|
|-2016345702|0x87D1019A|Syncml(410): Det begärda målet finns inte längre på mottagaren och ingen URI för vidarebefordran är känd.|
|-2016345703|0x87D10199|Syncml(409): Begäran misslyckades på grund av en uppdateringskonflikt mellan dataversioner på klienten och servern.|
|-2016345704|0x87D10198|Syncml(408): Ett förväntat meddelande togs inte emot inom den nödvändiga tidsperioden.|
|-2016345705|0x87D10197|Syncml(407): Det begärda kommandot misslyckades eftersom avsändaren måste ange korrekt autentisering.|
|-2016345706|0x87D10196|Syncml(406): Det begärda kommandot misslyckades på grund av att en valfri funktion i begäran inte stöds.|
|-2016345707|0x87D10195|Syncml(405): Det begärda kommandot är inte tillåtet på målet.|
|-2016345708|0x87D10194|Syncml(404): Det begärda målet hittades inte.|
|-2016345709|0x87D10193|Syncml(403): Det begärda målet misslyckades, men mottagaren förstod det begärda kommandot.|
|-2016345710|0x87D10192|Syncml(402): Det begärda kommandot misslyckades eftersom korrekt betalning krävs.|
|-2016345711|0x87D10191|Syncml(401): Det begärda kommandot misslyckades eftersom begäranden måste ange korrekt autentisering.|
|-2016345712|0x87D10190|Syncml(400): Det gick inte att utföra det begärda kommandot på grund av en felformaterad syntax i kommandot.|
|-2016345807|0x87D10131|Syncml(305): Åtkomst till det begärda målet måste ske genom den angivna proxy-URI:n.|
|-2016345808|0x87D10130|SyncML (304): Det begärda SyncML-kommandot utfördes inte på målet.|
|-2016345809|0x87D1012F|Syncml(303): Det begärda målet finns på en annan URI.|
|-2016345810|0x87D1012E|Syncml(302): Det begärda målet har tillfälligt flyttats till en annan URI.|
|-2016345811|0x87D1012D|Syncml(301): Det begärda målet har en ny URI.|
|-2016345812|0x87D1012C|Syncml(300): Det begärda målet är ett av flera alternativa begärda mål.|
|-2016345896|0x87D100D8|Syncml(216): Kommandot fanns i ett atomiskt element och den atomiska åtgärden misslyckades. Kommandot har återställts|
|-2016345897|0x87D100D7|Syncml(215): Kommandot utfördes inte på grund av en användaråtgärd och användaren godkände inte valet.|
|-2016345898|0x87D100D6|Syncml(214): Åtgärden avbröts. SyncML-kommandot slutfördes korrekt, men inga fler kommandon kommer att behandlas inom sessionen.|
|-2016345899|0x87D100D5|Syncml(213): Ett segmenterat objekt godkändes och buffrades.|
|-2016345900|0x87D100D4|Syncml(212): Autentisering accepterad. Ingen ytterligare autentisering behövs för återstoden av synkroniseringssession. Svarskoden kan bara användas som svar på en förfrågan som innehåller autentiseringsuppgifter.|
|-2016345901|0x87D100D3|Syncml(211): Objektet togs inte bort. Det begärda objektet hittades inte. Det kan ha tagits bort vid ett tidigare tillfälle.|
|-2016345902|0x87D100D2|Syncml(210): Ta bort utan att arkivera. Svaret visar att de begärda datauppgifterna har tagits bort utan att först arkiveras eftersom denna VALFRIA funktion saknade stöd i implementeringen.|
|-2016345903|0x87D100D1|Konflikt löst med dubblett. Svaret anger att en uppdateringskonflikt uppstått som sedan löstes genom att en dubblett av klientens data skapades i serverdatabasen. Svaret innehåller både mål- och käll-URI i dubletten i objektet för statusen. Vid tvåvägssynkronisering returneras dessutom ett tilläggskommando med definitionen av den duplicerade informationen.|
|-2016345904|0x87D100D0|Konflikt löst genom att klientkommandot " vann". Svaret anger att en uppdateringskonflikt uppstått som löstes genom att klientkommandot vann.|
|-2016345905|0x87D100CF|Konflikt löst med sammanfogning. Svaret anger att en konflikt skapades som löstes genom att klient- och serverinstanserna av data sammanfogades. Svaret innehåller både mål- och källwebbadresserna i objektet för statusen. Dessutom returneras ett ersättningskommando med den sammanfogade informationen.|
|-2016345906|0x87D100CE|Svaret anger att endast en del av kommandot utfördes. Om resten av kommandot kan utföras senare måste en ny lämplig statuskod för begäran om slutförande skapas vid slutförandet.|
|-2016345907|0x87D100CD|Källan bör uppdatera innehållet. Den som skickat frågan uppmanas att synkronisera innehållet för att få en uppdaterad version.|
|-2016345908|0x87D100CC|Begäran slutfördes men inga data returnerades. Svarskoden returneras även som svar på Get när målet saknar innehåll.|
|-2016345909|0x87D100CB|Inte auktoritativt svar. Begäran besvaras av en annan entitet än den avsedda. Svaret ska bara returneras när förfrågan skulle ha resulterat i en 200-svarskod från det auktoritativa målet.|
|-2016345910|0x87D100CA|Godkänd för behandling. Begäran om att antingen fjärrköra ett program eller varna en användare eller ett program, har utförts.|
|-2016345911|0x87D100C9|Det begärda objektet lades till.|
|-2016345912|0x87D100C8|SyncML-kommandot har utförts.|
|-2016346011|0x87D10065|Det angivna SyncML-kommandot genomförs, men har ännu inte slutförts.|

## <a name="next-steps"></a>Nästa steg

Kontakta Microsoft-supporten för att [få support för Microsoft Intune](../get-support.md).
