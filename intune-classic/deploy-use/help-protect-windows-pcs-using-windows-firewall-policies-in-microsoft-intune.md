---
title: "Brandväggsprinciper för Windows-datorer | Microsoft Docs"
description: "Intune hjälper dig att skydda dina hanterade datorer med Intune-klienten på många olika sätt, till exempel att konfigurera inställningar för Windows-brandväggen."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d96fd3cf4d8963f1e79ef4ed27c1b826c8893b5f
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune"></a>Hjälp till att skydda Windows-datorer med principer för Windows-brandväggen i Microsoft Intune
Microsoft Intune hjälper dig att skydda dina hanterade Windows-datorer med Intune-klienten på många olika sätt. Ett sätt är att tillhandahålla principer som gör att du kan konfigurera inställningar för Windows-brandväggen på datorer.

Om du inte har installerat Intune-klienten på dina Windows-datorer än läser du [Installera Windows PC-klienten med Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Använd informationen i följande avsnitt för att konfigurera, distribuera och övervaka principer för Windows-brandväggen på Windows-datorer.

## <a name="use-intune-policies-to-manage-windows-firewall"></a>Använd Intune-principer för att hantera Windows-brandväggen
Med principen för Windows-brandväggen kan du skapa och distribuera inställningar som styr Windows-brandväggen på hanterade datorer. Du kan inte hantera anpassade undantag för Windows-brandväggen och de här inställningarna påverkar inte brandväggar från tredje part.

> [!NOTE]
> Om Microsoft Intune-principen och grupprincipen har konfigurerats för att hantera samma inställning på samma dator åsidosätter grupprincipen principinställningen för Microsoft Intune. Information om hur du undviker konflikter mellan Intune-principer och grupprinciper finns i [Åtgärda konflikter mellan grupprincipobjekt och Microsoft Intune-principer](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> Om du vill distribuera inställningar för Windows-brandväggen på datorer som kör Windows Vista, måste du först installera [Hotfix KB971800](http://support2.microsoft.com/kb/971800) på dessa datorer.

> [!IMPORTANT]
> Om du vill hantera Windows-brandväggen med hjälp av Intune ser du till att följande två tjänster är aktiverade på de datorer som du hanterar:
>
> -   Windows-brandvägg
> -   IPsec Policy Agent

## <a name="configure-a-windows-firewall-policy"></a>Konfigurera en princip för Windows-brandväggen

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Princip** &gt; **Lägg till princip**.

2.  Konfigurera och distribuera en princip för **Windows-brandväggens inställningar** . Du kan använda de rekommenderade inställningarna eller anpassa inställningarna. Om du behöver mer information om hur du skapar och distribuerar principer läser du [Vanliga hanteringsuppgifter för Windows-datorer med Microsoft Intune-datorklienten](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

    I följande avsnitt visas värdena som du kan konfigurera i principen och de standardvärden som används om du inte anpassar principen.

När du har distribuerat en princip för Windows-brandväggen kan du visas dess status på sidan **Alla principer** på arbetsytan **Principer** .

## <a name="specify-policy-settings-for-windows-firewall"></a>Ange principinställningar för Windows-brandväggen

### <a name="turn-on-windows-firewall"></a>Aktivera Windows-brandväggen

De här principinställningarna aktiverar Windows-brandväggen på hanterade datorer som är:
- Anslutna till en domän (till exempel på arbetsplatsen)
- Anslutna till ett privat (betrott) nätverk (till exempel ett hemnätverk)
- Anslutna till ett icke betrott offentligt nätverk (till exempel ett kafé)

Standardvärdet för var och en av de här inställningarna är **Ja**, vilket är det säkraste värdet.



### <a name="block-all-incoming-connections-including-those-in-the-list-of-allowed-programs"></a>Blockera alla inkommande anslutningar, även de som finns i listan över tillåtna program

De här principinställningarna konfigurerar Windows-brandväggen så att inkommande nätverkstrafik blockeras på hanterade datorer som är:
- Anslutna till en domän (till exempel på arbetsplatsen)
- Anslutna till ett privat (betrott) nätverk (till exempel ett hemnätverk)
- Anslutna till ett icke betrott offentligt nätverk (till exempel ett kafé)

Standardvärdet för var och en av de här inställningarna är **Ja**, vilket är det säkraste värdet.

> [!IMPORTANT]
> Om det finns hanterade datorer som kör Windows Vista utan något Service Pack i din miljö måste du antingen installera uppdateringen som är kopplad till [artikel 971800](http://go.microsoft.com/fwlink/?LinkId=188405) i Microsoft Knowledge Base eller inaktivera principinställningarna **Blockera alla inkommande anslutningar** i principer som distribueras till dessa datorer.

### <a name="notify-the-user-when-windows-firewall-blocks-a-new-program"></a>Meddela användaren när ett nytt program blockeras av Windows-brandväggen

De här principinställningarna avgör om Windows-brandväggen meddelar datoranvändare när den blockerar inkommande nätverkstrafik när de hanterade datorerna är:
- Anslutna till en domän (till exempel på arbetsplatsen)
- Anslutna till ett privat (betrott) nätverk (till exempel ett hemnätverk)
- Anslutna till ett icke betrott offentligt nätverk (till exempel ett kafé)

Standardvärdet för var och en av de här inställningarna är **Ja**.


### <a name="configure-predefined-exceptions"></a>Konfigurera fördefinierade undantag

Du kan konfigurera undantag som tillåter specifika typer av nätverkstrafik att passera genom brandväggen oavsett de värden som du konfigurerat tidigare. Ingen av de här inställningarna är konfigurerade som standard.

|Inställningsnamn|Information|
|------------------|--------------------|
|**BranchCache – innehållshämtning**<br>(Windows 7 eller senare)|Låter BranchCache-klienter använda HTTP vid hämtning av innehåll från andra BranchCache-klienter i distributionsläget och från värdhanterad cache i värdhanterat cacheläge. Inställningen använder HTTP.|
|**BranchCache – klient för värdhanterad cache**<br>(Windows 7 eller senare)|Låter BranchCache-klienter använda en värdbaserad cache. Inställningen använder HTTPS.|
|**BranchCache – server för värdhanterad cache**|Låter BranchCache-klienter använda en värdbaserad cache för att kommunicera med andra klienter. Inställningen använder HTTPS.|
|**BranchCache – peerupptäckt**<br>(Windows 7 eller senare)|Låter BranchCache-klienter använda WS-Discovery-protokollet (Web Services Dynamic Discovery) för att kontrollera tillgänglighet för innehåll på det lokala undernätet.|
|**BITS Peercaching**|Låter klienter använda Background Intelligent Transfer Service (BITS) för att hitta och dela filer som lagras i BITS-cacheminnet på klienter i samma undernät. Den här inställningen använder WSDAPI (Web Services on Devices) och RPC (Remote Procedure Call).|
|**Anslut till en nätverksprojektor**|Låter användare ansluta till projektorer över kabelanslutna eller trådlösa nätverk för att visa presentationer. Inställningen använder WSDAPI.|
|**Kärnnätverket**|Låter klienter använda IPv4 och IPv6 för att ansluta till nätverksresurserna.|
|**Distributed Transaction Coordinator**|Låter hanterade datorer koordinera transaktioner som uppdaterar transaktionsskyddade resurser, t.ex. databaser, meddelandeköer och filsystem.|
|**Fil- och skrivardelning**|Låter användare dela lokala filer och skrivare i nätverket med andra användare. Den här inställningen använder NetBIOS, LLMNR (Link Local Multicast Name Resolution), SMB-protokoll (Server Message Block) och RPC.|
|**Hemgrupp**<br>(Windows 7 eller senare)|Låter hanterade datorer delta i ett hemgruppsnätverk.|
|**Tjänsten iSCSI**|Låter hanterade datorer ansluta till iSCSI-servrar och -enheter.|
|**Nyckelhanteringstjänst**|Låter datorer räknas med i licenskontrollen i företagsmiljöer.|
|**Media Center Extenders**|Låter Media Center Extenders kommunicera med datorer som kör Windows Media Center. Den här inställningen använder SSDP (Simple Service Discovery Protocol) och qWave.|
|**Tjänsten Netlogon**|Konfigurerar en säkerhetskanal mellan domänklienter och en domänkontrollant som autentiserar användare och tjänster. Inställningen använder RPC.|
|**Nätverksidentifiering**|Låter datorer identifiera andra enheter och identifieras av andra enheter i nätverket. Inställningen använder nätverksprotokollen Function Discovery Host och Publication Services och SSDP, NetBIOS, LLMNR och UPnP™.|
|**Prestandaloggar och -varningar**|Låter tjänsten Prestandaloggar och -varningar fjärrhanteras. Inställningen använder RPC.|
|**Fjärradministration**|Tillåter fjärradministration av datorn.|
|**Fjärrhjälp**|Låter användare av hanterade datorer kunna begära fjärrhjälp från andra användare i nätverket. Den här inställningen använder SSDP-, PNRP- (Peer Name Resolution Protocol), Teredo- och UPnP-nätverksprotokoll.|
|**Fjärrskrivbord**|Låter datorn använda Fjärrskrivbord för att få åtkomst till andra datorer.|
|**Fjärrhantering av händelseloggen**|Låter klienthändelseloggar fjärrvisas och fjärrhanteras. Inställningen använder Named Pipes och RPC.|
|**Fjärrhantering av schemalagda aktiviteter**|Tillåter fjärrhantering av schemaläggningstjänsten. Inställningen använder RPC.|
|**Fjärrtjänsthantering**|Tillåter fjärrhantering av lokala tjänster på klienter. Inställningen använder Named Pipes och RPC.|
|**Fjärrvolymhantering**|Tillåter fjärrhantering av programvaru- och hårddiskvolym. Inställningen använder RPC.|
|**Routning och fjärråtkomst (RAS)**|Tillåter inkommande VPN- och RAS-anslutningar till datorer.|
|**Secure Socket Tunneling Protocol**|Tillåter inkommande VPN-anslutningar till hanterade datorer med SSTP (Secure Socket Tunneling Protocol). Inställningen använder HTTPS.|
|**SNMP Trap**|Låter hanterade datorer ta emot SNMP (Simple Network Management Protocol) Trap-tjänstens trafik.|
|**UPnP-ramverk**|Konfigurerar UPnP-ramverkstjänsten på datorer och låter dem identifiera och använda UPnP-enheter.|
|**Registreringstjänst för datornamn för Windows Collaboration**|Låter datorer hitta och kommunicera med andra datorer via SSDP och PNRP.|
|**Windows Media Player**|Låter användare ta emot strömmande medier över UDP (User Datagram Protocol).|
|**Nätverksdelningstjänsten för Windows Media Player**|Låter användare dela medier över ett nätverk. Inställningen använder SSDP-, qWave- och UPnP-nätverksprotokoll.|
|**Windows Media Player-tjänsten för nätverksdelning (Internet)**<br>(Windows 7 eller senare)|Låter användare dela hemmedier över Internet.|
|**Windows Mötesrum**|Låter användare samarbeta över ett nätverk för att dela dokument, program och skrivbord. Den här inställningen använder DFSR (Distributed File System Replication) och P2P.|
|**Windows Peer to Peer Collaboration Foundation**|Konfigurerar olika peer-to-peer-program och -tekniker så att de kan ansluta. Inställningen använder SSDP och PNRP.|
|**Windows Remote Management (kompatibilitet)**|Tillåter fjärrhantering av hanterade datorer med WS-Management, ett webbtjänstbaserat protokoll för fjärrhantering av operativsystem och enheter.|
|**Windows Remote Management**<br>(Windows 8 eller senare)|Tillåter fjärrhantering av hanterade datorer med WS-Management, ett webbtjänstbaserat protokoll för fjärrhantering av operativsystem och enheter.|
|**Windows Virtual PC**<br>(Windows 7 eller senare)|Låter virtuella datorer kommunicera med andra datorer.|
|**Trådlösa bärbara enheter**|Tillåter överföring av medier från en nätverksaktiverad kamera eller medieenhet till hanterade datorer med MTP (Media Transfer Protocol). Inställningen använder SSDP- och UPnP-nätverksprotokoll.|

### <a name="see-also"></a>Se även
[Principer för att skydda Windows-datorer](policies-to-protect-windows-pcs-in-microsoft-intune.md)

