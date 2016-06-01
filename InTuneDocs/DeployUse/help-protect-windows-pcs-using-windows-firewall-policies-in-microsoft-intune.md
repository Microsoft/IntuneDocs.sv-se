---
# required metadata

title: Brandväggsprinciper för Windows-datorer | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Hjälp till att skydda Windows-datorer med principer för Windows-brandväggen i Microsoft Intune
Microsoft Intune kan hjälpa dig att skydda dina hanterade Windows-datorer med Intune-klienten på många olika sätt, inklusive användningen av principer som gör att du kan konfigurera inställningar för Windows-brandväggen på datorer.

Om du inte har installerat Intune-klienten på dina Windows-datorer än läser du [Installera Windows PC-klienten med Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md)

Använd informationen i följande avsnitt för att konfigurera, distribuera och övervaka principer för Windows-brandväggen på Windows-datorer.

## Använd Intune-principer för att hantera Windows-brandväggen
Med principen för Windows-brandväggen kan du skapa och distribuera inställningar som styr Windows-brandväggen på hanterade datorer. Du kan inte hantera anpassade undantag för Windows-brandväggen och de här inställningarna påverkar inte brandväggar från tredje part.

> [!NOTE]
> Om Microsoft Intune-principen och grupprincipen har konfigurerats för att hantera samma inställning på samma dator åsidosätter grupprincipen principinställningen för Microsoft Intune. Information om hur du undviker konflikter mellan Intune-principer och grupprinciper finns i [Åtgärda konflikter mellan grupprincipobjekt och Microsoft Intune-principer](resolve-gpo-and-microsoft-intune-policy-conflicts.md)
>
> Om du vill distribuera Windows-brandväggen på datorer som kör Windows Vista, måste du först installera [Hotfix KB971800](http://support2.microsoft.com/kb/971800) på dessa datorer.

> Om du vill hantera Windows-brandväggen med hjälp av Intune måste du se till att följande två tjänster är aktiverade på de datorer som du tänker hantera:
>
> -   Windows-brandvägg
> -   IPsec Policy Agent

## Konfigurera en princip för Windows-brandväggen

1.  I [Microsoft Intune Administrationskonsol](https://manage.microsoft.com/) väljer du **Princip** &gt; **Lägg till princip**

2.  Konfigurera och distribuera en princip för **Windows-brandväggens inställningar** . Du kan använda rekommenderade inställningar eller anpassa inställningarna. Om du behöver mer information om hur du skapar och distribuerar principer läser du [Vanliga hanteringsuppgifter för Windows-datorer med Microsoft Intune-datorklienten](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)

    I följande avsnitt visas värdena som du kan konfigurera i principen och de standardvärden som används om du inte anpassar principen.

När du har distribuerat en princip för Windows-brandväggen kan du visas dess status på sidan **Alla principer** på arbetsytan **Principer** .

## Principinställningar för Windows-brandväggen

### Aktivera Windows-brandväggen

Dessa principinställningar aktiverar Windows-brandväggen på hanterade datorer som är anslutna till en domän (till exempel på arbetsplatsen), ett privat (betrott) nätverk (till exempel ett hemnätverk) eller ett ej betrott offentligt nätverk (till exempel ett kafé). Standardvärdet för var och en av de här inställningarna är **Ja**, vilket är det säkraste värdet. 



### Blockera alla inkommande anslutningar, även de som finns i listan över tillåtna program

Dessa principinställningar konfigurerar Windows-brandväggen att blockera inkommande nätverkstrafik när den hanterade datorn är ansluten till en domän (till exempel på arbetsplatsen), ett privat (betrott) nätverk (till exempel ett hemnätverk) eller ett ej betrott offentligt nätverk (till exempel ett kafé). Standardvärdet för var och en av de här inställningarna är **Ja**, vilket är det säkraste värdet. 

> Om det finns hanterade datorer som kör Windows Vista utan något Service Pack i din miljö måste du antingen installera uppdateringen som är kopplad till [artikel 971800](http://go.microsoft.com/fwlink/?LinkId=188405) i Microsoft Knowledge Base eller inaktivera principinställningarna **Blockera alla inkommande anslutningar** i principer som distribueras till dessa datorer.

### Meddela användaren när ett nytt program blockeras av Windows-brandväggen

Dessa principinställningar konfigurerar huruvida Windows-brandväggen aviserar datoranvändaren när den blockerar inkommande nätverkstrafik när den hanterade datorn är ansluten till en domän (till exempel på arbetsplatsen), ett privat (betrott) nätverk (till exempel ett hemnätverk) eller ett ej betrott offentligt nätverk (till exempel ett kafé). Standardvärdet för var och en av de här inställningarna är **Ja**


### Fördefinierade undantag

När du har konfigurerat de grundläggande värdena ovan kan du konfigurera undantag som gör att viss nätverkstrafik tillåts passera genom brandväggen oavsett de värden som konfigurerats ovan. Ingen av de här inställningarna är konfigurerade som standard.

|Inställningsnamn|Information|
|------------------|--------------------|
|**BranchCache – innehållshämtning**<br>(Windows 7 eller senare)|Låter BranchCache-klienter använda HTTP vid hämtning av innehåll från varandra i distributionsläget och från värdhanterad cache i värdhanterat cacheläge. Inställningen använder HTTP.|
|**BranchCache – klient för värdhanterad cache**<br>(Windows 7 eller senare)|Låter BranchCache-klienter använda en värdbaserad cache. Inställningen använder HTTPS.|
|**BranchCache – server för värdhanterad cache**|Låter BranchCache-klienter använda en värdbaserad cache för att kommunicera med andra klienter. Inställningen använder HTTPS.|
|**BranchCache – peerupptäckt**<br>(Windows 7 eller senare)|Denna principinställning anger om BranchCache-klienterna ska kunna använda WS Discovery-protokollet för att kontrollera tillgänglighet för innehåll på det lokala undernätet.|
|**BITS Peercaching**|Låter klienter använda Background Intelligent Transfer Service (BITS) för att hitta och dela filer som lagras i BITS-cacheminnet på klienter i samma undernät. Inställningen använder WSDAPI och RPC.|
|**Anslut till en nätverksprojektor**|Låter användare ansluta till projektorer över kabelanslutna eller trådlösa nätverk för att visa presentationer. Inställningen använder WSDAPI.|
|**Kärnnätverket**|Låter klienter använda IPv4 och IPv6 för att ansluta till nätverksresurserna.|
|**Distributed Transaction Coordinator**|Låter hanterade datorer koordinera transaktioner som uppdaterar transaktionsskyddade resurser, t.ex. databaser, meddelandeköer och filsystem.|
|**Fil- och skrivardelning**|Låter användare dela lokala filer och skrivare i nätverket med andra användare. Inställningen använder NetBIOS, LLMNR, SMB och RPC.|
|**Hemgrupp**<br>(Windows 7 eller senare)|Låter hanterade datorer delta i ett hemgruppsnätverk.|
|**Tjänsten iSCSI**|Låter hanterade datorer ansluta till iSCSI-servrar och -enheter.|
|**Nyckelhanteringstjänst**|Låter datorer räknas med i licenskontrollen i företagsmiljöer.|
|**Media Center Extenders**|Låter Media Center Extenders kommunicera med datorer som kör Windows Media Center. Inställningen använder SSDP och qWave.|
|**Tjänsten Netlogon**|Konfigurerar en säkerhetskanal mellan domänklienter och en domänkontrollant som autentiserar användare och tjänster. Inställningen använder RPC.|
|**Nätverksidentifiering**|Låter datorer identifiera andra enheter och identifieras av andra enheter i nätverket. Inställningen använder nätverksprotokollen Function Discovery Host och Publication Services och SSDP, NetBIOS, LLMNR och UPnP™.|
|**Prestandaloggar och -varningar**|Låter tjänsten Prestandaloggar och -varningar fjärrhanteras. Inställningen använder RPC.|
|**Fjärradministration**|Tillåter fjärradministration av datorn.|
|**Fjärrhjälp**|Låter användare av hanterade datorer kunna begära fjärrhjälp från andra användare i nätverket. Inställningen använder SSDP-, PNRP-, Teredo- och UPnP-nätverksprotokoll.|
|**Fjärrskrivbord**|Låter datorn använda Fjärrskrivbord för att få åtkomst till andra datorer.|
|**Fjärrhantering av händelseloggen**|Låter klienthändelseloggar fjärrvisas och fjärrhanteras. Inställningen använder Named Pipes och RPC.|
|**Fjärrhantering av schemalagda aktiviteter**|Tillåter fjärrhantering av schemaläggningstjänsten. Inställningen använder RPC.|
|**Fjärrtjänsthantering**|Tillåter fjärrhantering av lokala tjänster på klienter. Inställningen använder Named Pipes och RPC.|
|**Fjärrvolymhantering**|Tillåter fjärrhantering av programvaru- och hårddiskvolym. Inställningen använder RPC.|
|**Routning och fjärråtkomst (RAS)**|Tillåter inkommande VPN- och RAS-anslutningar till datorer.|
|**Secure Socket Tunneling Protocol**|Tillåter inkommande VPN-anslutningar till hanterade datorer med hjälp av Secure Socket Tunneling Protocol (SSTP). Inställningen använder HTTPS.|
|**SNMP Trap**|Låter hanterade datorer ta emot SNMP Trap-tjänstens trafik.|
|**UPnP-ramverk**|Konfigurerar UPnP-ramverkstjänsten på datorer och låter dem identifiera och använda UPnP-enheter.|
|**Registreringstjänst för datornamn för Windows Collaboration**|Låter datorer hitta och kommunicera med andra datorer via Peer Name Resolution Protocol. Inställningen använder SSDP och PNRP.|
|**Windows Media Player**|Låter användare ta emot strömmande medier över UDP.|
|**Nätverksdelningstjänsten för Windows Media Player**|Låter användare dela medier över ett nätverk. Inställningen använder SSDP-, qWave- och UPnP-nätverksprotokoll.|
|**Windows Media Player-tjänsten för nätverksdelning (Internet)**<br>(Windows 7 eller senare)|Låter användare dela hemmedier över Internet.|
|**Windows Mötesrum**|Låter användare samarbeta över ett nätverk för att dela dokument, program eller skrivbordet. Inställningen använder DFSR och P2P.|
|**Windows Peer to Peer Collaboration Foundation**|Konfigurerar olika peer-to-peer-program och -tekniker så att de kan ansluta. Inställningen använder SSDP och PNRP.|
|**Windows Remote Management (kompatibilitet)**|Tillåter klientfjärrhantering genom WS-Management, ett webbtjänstbaserat protokoll för fjärrhantering av operativsystem och enheter.|
|**Windows Remote Management**<br>(Windows 8 eller senare)|Tillåter klientfjärrhantering genom WS-Management, ett webbtjänstbaserat protokoll för fjärrhantering av operativsystem och enheter.|
|**Windows Virtual PC**<br>(Windows 7 eller senare)|Låter virtuella datorer kommunicera med andra datorer.|
|**Trådlösa bärbara enheter**|Tillåter överföring av medier från en nätverksaktiverad kamera eller medieenhet till hanterade datorer med Media Transfer Protocol (MTP). Inställningen använder SSDP- och UPnP-nätverksprotokoll.|

### Se även
[Principer för att skydda Windows-datorer](policies-to-protect-windows-pcs-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


