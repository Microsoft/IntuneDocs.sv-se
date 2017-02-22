---
title: "Inställning av begränsningar i Intune-enheter för Windows 10 | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs om de Intune-inställningar du kan använda för att styra inställningar och funktioner på Windows 10-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89f2d806-2e97-430c-a9a1-70688269627f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e6e0540acd5488077ae5217f8862e3bc5462ed71
ms.openlocfilehash: 422826ded029eb8f17856e47e98f5a09dc36bc08


---

# <a name="windows-10-and-later-device-restriction-settings-in-intune-azure-preview"></a>Inställning av enhetsbegränsningar för Windows 10 i Intune Azure-förhandsversionen

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Allmänt
-   **Skärmdump** – Låter användaren fånga enhetens skärm som en bild. (endast Windows 10 Mobile)
-   **Kopiera och klistra in (endast mobil)** – Tillåter funktionen att kopiera och klistra in mellan appar på enheten.
-   **Manuell avregistrering** – Tillåter att användaren manuellt tar bort sitt arbetsplatskonto från enheten.
-   **Manuell installation av rotcertifikat** -  
-   **Sändning av diagnostikdata** – Möjliga värden är:
    -       **Inga** Inga data skickas till Microsoft
    -       **Grundläggande** Begränsad information skickas till Microsoft
    -       **Utökade** Utökade diagnostikdata skickas till Microsoft
    -       **Fullständiga** Skickar samma data som i Utökade, plus ytterligare information om enhetens tillstånd
-   **Kamera** – Tillåt eller blockera användning av kameran på enheten.
-   **Flyttbara lagringsmedier** – Anger om externa lagringsenheter, till exempel ett SD-kort, kan användas med enheten.
-   **Geoplats** – Anger om enheten kan använda information om platstjänster.
-   **Internetdelning** – Tillåter användning av Internetanslutningsdelning på enheten.
-   **Telefonåterställning** – Styr om användaren kan göra en fabriksåterställning på enheten eller inte.
-   **USB-anslutning** – Styr om enheter har åtkomst till externa lagringsenheter via en USB-anslutning.
-   **Stöldskyddsläge** – Konfigurera om stöldskyddsläget i Windows ska vara aktiverat.
-   **Meddelanden från Åtgärdscenter** – Aktivera eller inaktivera meddelanden från Åtgärdscenter på enhetens låsskärm (endast Windows 10 Mobile).
-   **Cortana** – Aktivera eller inaktivera röstassistenten Cortana.
-   **Röstinspelning** – Tillåt eller blockera användning av enhetens röstinspelning.

## <a name="password"></a>Lösenord
-   **Lösenord krävs** – Slutanvändaren måste ange ett lösenord för att få åtkomst till enheten.
-   **Krav på lösenordstyp** – Anger om lösenordet måste vara enbart numeriskt, eller om det kan vara alfanumeriskt.
-   **Minsta längd på lösenord** – Gäller endast Windows 10 Mobile.
-   **Antal felaktiga inloggningar innan enheten rensas** – För enheter som kör Windows 10: Om BitLocker är aktiverat på enheten försätts den i återställningsläget för BitLocker när den gräns för antal misslyckade inloggningar som du har angett har uppnåtts. Om BitLocker inte är aktiverat på enheten tillämpas inte den här inställningen.
För enheter som kör Windows 10 Mobile: Om inloggningen misslyckas ett visst antal gånger (som du angett) rensas enheten.
-   **Maximalt antal minuter av inaktivitet innan skärmen låses** – Anger hur lång tid en enhet måste vara i viloläge innan skärmen låses.
-   **Lösenordets giltighetstid (dagar)** – Anger efter hur lång tid enhetens lösenord måste ändras.
-   **Förhindra återanvändning av tidigare lösenord** – Anger hur många tidigare använda lösenord enheten kommer ihåg.
-   **Kräv lösenord när enheten lämnar inaktivt läge** – Anger att användaren måste ange ett lösenord för att kunna låsa upp enheten (endast Windows 10 Mobile).
-   **Kryptering** – Aktivera kryptering på målenheter (endast Windows 10 Mobile).
## <a name="app-store"></a>Appbutik

-   **Appbutik (endast mobil)** – Aktivera eller blockera användning av appbutiken på Windows 10 Mobile-enheter.
## <a name="edge-browser"></a>Edge-webbläsare
-   **Microsoft Edge-webbläsare (endast mobil)** – Tillåt användning av Edge-webbläsaren på enheten.
-   **SmartScreen** – Aktiverar eller inaktiverar SmartScreen som blockerar bedrägliga webbplatser.
-   **Skicka Do Not Track-huvuden** – Konfigurerar Edge-webbläsaren så att Do Not Track-huvuden skickas till webbplatser som användarna besöker.
-   **Cookies** – Gör att webbläsaren sparar Internetcookies på enheten.
-   **JavaScript** – Tillåter att skript (exempelvis JavaScript) körs i Edge-webbläsaren.
-   **Popup-fönster** – Blockerar popup-fönster i webbläsaren.<br>(Gäller endast för Windows 10 Desktop.)
-   **Sökförslag** – Tillåter att din sökmotor föreslår webbplatser när du skriver sökfraser.
-   **Skicka intranätstrafik till Internet Explorer** – Användarna kan öppna intranätswebbplatser i Internet Explorer. <br>(Endast Windows 10 Desktop.)
-   **Autofyll** – Tillåter att användarna ändrar inställningarna för att komplettera automatiskt i webbläsaren.<br>(endast Windows 10 Desktop)
-   **Lösenordshanteraren** – Aktivera eller inaktivera lösenordshanteraren för Edge.
-   **Plats för webbplatslista för företagsläge** – Anger var du hittar listan med webbplatser som kan öppnas i företagsläge. Användare kan inte redigera den här listan.<br>(Endast Windows 10 Desktop.)
## <a name="cloud-and-storage"></a>Moln och lagring
-   **Microsoft-konto** – Låter användaren associera ett Microsoft-konto med enheten.
-   **Andra konton än Microsoft-konton** – Låter användaren lägga till e-postkonton på enheten som inte är associerade med något Microsoft-konto.
-   **Synkroniseringsinställningar för Microsoft-konto** – Tillåt att enhets- och appinställningar som har associerats med ett Microsoft-konto synkroniseras mellan enheter.
## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning
-   **Datanätverksväxling** – Tillåt växling mellan nätverk vid åtkomst till data.
-   **VPN över mobilt nätverk** – Styr om enheten har åtkomst till VPN-anslutningar när den är ansluten till ett mobilt nätverk.
-   **VPN-nätverksväxling över mobilt nätverk** – Styr om enheten har åtkomst till VPN-anslutningar när den är nätverksväxlas i ett mobilt nätverk.
-   **Bluetooth** – Styr om användaren kan aktivera och konfigurera Bluetooth på enheten.
-   **Bluetooth-identifiering** – Tillåter att enheten kan upptäckas av andra Bluetooth-aktiverade enheter.
-   **Bluetooth-annonsering** – Låter enheten ta emot annonser via Bluetooth.
-   **NFC** – Låter användaren aktivera och konfigurera närfältskommunikation på enheten.
-   **Trådlöst** – Låter användaren aktivera och konfigurera trådlösa funktioner på enheten (endast Windows 10 Mobile).
-   **Anslut automatiskt till trådlösa surfpunkter** – Tillåter att enheten ansluter automatiskt till kostnadsfria trådlösa surfpunkter och att den godkänner eventuella villkor för anslutningen automatiskt.
-   **Manuell trådlös konfiguration** – Styr om användarna kan konfigurera egna trådlösa anslutningar, eller om de endast kan använda anslutningar som konfigurerats med en trådlös profil (endast Windows 10 Mobile).
## <a name="defender"></a>Defender

-   **Övervakning i realtid** – Tillåter genomsökning i realtid efter skadlig programvara, spionprogram och annan oönskad programvara.
-   **Övervaka funktionssätt** – Tillåter att Defender söker efter kända mönster för misstänkt aktivitet på enheterna.
-   **NIS (Network Inspection System)** – NIS hjälper till att skydda enheter mot nätverksbaserade hot genom att använda signaturerna för kända säkerhetsrisker från Microsoft Endpoint Protection Center för att upptäcka och blockera skadlig trafik.
-   **Sök igenom alla nedladdningar** – Styr om Defender genomsöker alla filer som laddas ner från Internet.
-   **Sök igenom skripts som har lästs in via Microsoft-webbläsare** – Tillåter Defender-genomsökning av skript som används i Internet Explorer.
-   **Användaråtkomst till Defender** – Styr om Windows Defender-användargränssnittet är dolt för slutanvändarna.
Om den här inställningen ändras börjar den gälla nästa gång slutanvändarens dator startas om.
-   **Intervall för signaturuppdatering (i timmar)** – Ange med vilket intervall som Defender ska söka efter nya signaturfiler.
-   **Övervaka fil- och programaktivitet** – Tillåter att Defender övervakar fil- och programaktivitet på enheter.
-   **Dagar innan skadlig kod i karantän tas bort** – Tillåter att Defender fortsätter spåra åtgärdad skadlig kod det antal dagar som du anger, för att du ska kunna kontrollera tidigare berörda enheter manuellt. Om du ställer in antalet dagar till **0** finns skadlig kod kvar i karantänmappen och tas inte bort automatiskt.
-   **Gräns för processoranvändning under genomsökning** – Tillåter att du begränsar hur mycket processorkraft som genomsökningarna får använda (från **1** till **100**).
-   **Sök igenom arkivfiler** – Tillåter att Defender söker igenom arkiverade filer, till exempel ZIP- eller CAB-filer.
-   **Sök igenom inkommande e-postmeddelanden** – Tillåter att Defender söker igenom e-postmeddelanden när de tas emot på enheten.
-   **Sök igenom flyttbara enheter vid fullständig genomsökning** –Tillåter att Defender genomsöker flyttbara enheter, som t.ex. USB-minnen.
-   **Sök igenom mappade nätverksenheter vid fullständig genomsökning** – Tillåter att Defender genomsöker filer på mappade nätverksenheter.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.
-   **Sök igenom filer öppnade från nätverksmappar** – Tillåter att Defender genomsöker filer på delade nätverksenheter (till exempel de som nås från en UNC-sökväg).
Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.
-   **Molnskydd** – Tillåter eller förhindrar att Microsoft Active Protection Service tar emot information om aktiviteter mot skadlig kod från enheter som du hanterar. Den här informationen används för att förbättra tjänsten i framtiden.
-   **Tillfråga användarna innan exempel skickas** – Styr om filer som kan kräva ytterligare analys av Microsoft för att avgöra om de är skadliga ska skickas automatiskt till Microsoft.
-   **Tidpunkt för daglig snabbsökning** – Tillåter att du schemalägger en snabbgenomsökning som körs varje dag vid den tidpunkt som du väljer.
-   **Typ av systemgenomsökning som ska utföras** – Här kan du ange nivå för genomsökningen som ska utföras när du schemalägger en systemgenomsökning.
## <a name="defender-exclusions"></a>Defender-undantag

-   **Filer och mappar som ska undantas från genomsökningar och realtidsskydd** – Lägger till en eller flera filer och mappar, som t.ex. **C:\Path** eller **%ProgramFiles%\Path\filename.exe**, i undantagslistan. Dessa filer och mappar tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.
-   **Filnamnstillägg som ska undantas från genomsökningar och realtidsskydd** – Lägg till ett eller flera filnamnstillägg, som t.ex. **jpg** eller **txt**, i undantagslistan. Filer med dessa filnamnstillägg tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.
-   **Processer som ska undantas från genomsökningar och realtidsskydd** – Lägg till en eller flera processer av typen **.exe**, **.com** eller **.scr** i undantagslistan. De här processerna tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.



<!--HONumber=Feb17_HO1-->


