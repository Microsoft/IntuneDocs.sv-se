---
# required metadata

title: Vanliga frågor | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a8126cca-9ec4-454b-a20b-dc1bb6797327

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Vanliga frågor om Microsoft Intune
Den här artikeln besvarar några vanliga frågor om Intune. Om du inte hittar svar på din fråga här kan du [berätta det för oss](https://microsoftintune.uservoice.com/)

## Allmänna frågor

-   **Hur vet jag när Intune-tjänsten har uppdaterats?**

    Logga in på ditt konto på manage.microsoft.com. Välj **Visa tjänstens status** i administrationsöversikten. Platsen för klientorganisationen och underhållsschemat visas där. Läs mer om tjänsteuppdateringar i artikeln [Nyheter](/intune/deploy-use/whats-new-in-microsoft-intune).

-   **Ändras namnet i Intune eller Configuration Manager om en användare byter namn på en enhet i appen Företagsportal?**

    Nej, namnändringen gäller bara för den användaren.

-   **Finns det någon fjärrhjälpsfunktion för mobila enheter i Intune?**

    Nej, tyvärr. Appar från tredje part som [Bomgar](http://www.bomgar.com/) och [TeamViewer](https://www.teamviewer.com/) kan vara användbara.

## Konton

-   **Kan jag lägga till Office 365 i utvärderingen med samma klientorganisation om jag börjar utvärdera Intune och skapar en ny klientorganisation för utvärderingsversionen?**

    Ja. Logga bara in med en global administratör från din befintliga klientorganisation eller prenumeration på Intune, till exempel *globaladmin@&lt;company&gt;.onmicrosoft.com*

-   **Är det svårt att byta till ett annat företags tjänst om jag tilldelar Intune en MDM-utfärdare under en utvärderingsprenumeration och sedan ändrar mig angående Intune?**

    Även om det är svårt att tro att du inte skulle fastna för Intune, så påverkar inte valet av MDM-utfärdare möjligheten att byta till en annan tjänst. Det handlar framför allt om att välja Intune eller Intune med System Center Configuration Manager.

-   **Kan jag använda mitt befintliga domännamn för Office 365 för mitt kommande Intune-konto?**

    Ja, om du loggar in med det organisations-ID som är kopplat till din befintliga Office 365-klientorganisation och verifierade domän när du antingen skapar din utvärderingsversion av Intune eller aktiverar dina licenser.

    Intune använder sedan samma domän, användare osv. i ditt Office 365-konto. Tänk på att varje Office 365-användare måste aktiveras som Intune-användare med en Intune-licens. Detta görs av den globala administratören som hanterar klientorganisationen.

## Registrering

-   **Var kan mina användare lära sig hur de registrerar sina enheter?**

    Du kan använda eller anpassa information från [registreringsanvisningarna för slutanvändare i Intune för IT-administratörer](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a)

-   **Hur felsöker jag en registrering av en enhet?**

    Anvisningar för hur du kan felsöka vanliga problem med registreringen finns i [Felsöka enhetsregistrering i Intune](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune)

-   **Hur samlar jag in registreringsloggar om en användare har problem med registreringen?**

    Följ [dessa anvisningar](http://www.microsoft.com/en-us/download/46391)

## Hantering av mobila enheter

-   **Allmänt om MDM**

    -   **Kan Intune identifiera om en enhet är jailbrokad?**

        Ja, för vissa operativsystem. Information om hur du hanterar jailbrokade enheter finns i [Skapa en princip för enhetsefterlevnad](/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune.md)

    -   **Kan jag välja vilka företagsdata jag vill ta bort från enheten?**

        Ja. Information om selektiv rensning finns i [Skydda dina data med fjärrensning, fjärrlåsning eller lösenordsåterställning](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune.md)

    -   **Går det att blockera vissa webbplatser i webbläsaren på en mobil enhet via Intune?**

        Inte i plattformarnas interna webbläsare. Du kan dock tillåta eller blockera webbadresser när du har distribuerat den Intune-hanterade webbläsaren på iOS- och Android-enheter. Mer information finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper](/intune/Deploy-Use/Manage-Internet-access-using-managed-browser-policies-with-Microsoft-Intune.md)

    -   **Kan vi hindra en användare från att avinstallera en app?**

        I allmänhet inte. På en övervakad iOS-enhet kan du dock förhindra att användare avinstallerar en app som har distribuerats med Apple Configurator. 

    -   **Går det att hantera mobildataanvändning?**

        Inte direkt, men du kan se till att Wi-Fi är den prioriterade metoden för att ansluta genom att skicka Wi-Fi-profiler till enheter. Anvisningar finns i [Hjälp användarna att ansluta till företagsnätverk med hjälp av Wi-Fi-profiler](/intune/Deploy-Use/wi-fi-connections-in-microsoft-intune.md). På vissa plattformar (till exempel iOS och Android KNOX) kan du även styra inställningar som röst- och dataroaming.

    -   **Går det att förhindra att en användare avregistrerar en enhet? Vad händer om det är en enhet som ägs av företaget?**

        Nej. I allmänhet inte. Du kan dock förhindra avregistrering av användare på Windows Phone 8.1 via anpassade inställningar för Windows Phone. I iOS-enheter som hanteras och registreras i Apples Device Enrollment Program (DEP) går det även att förhindra att användare avregistrerar en enhet.

    -   **Kan jag byta en MDM-utfärdare som jag har valt?**

        Du kan i vissa fall byta MDM-utfärdare. Om du behöver göra det kontaktar du supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](/intune/Troubleshoot/How-to-get-support-for-Microsoft-Intune.md). I tabellen nedan beskrivs vilka ändringar som är möjliga. Ändringar av MDM-utfärdare kräver ny registrering av enheter.

        **Till:** Intune!**Till:** O365|**Till:** Configuration Manager med Intune|
        
        **Från:** Intune| |Ja&#42;|Ja|



-   ****Från:** O365||Ja&#42;||Ja|**

    -   ****Från:** Configuration Manager med Intune|Ja|Ja| |**

        &#42;MDM-utfärdare för O365 och Intune kan samexistera, så du behöver inte registrera mobila enheter på nytt. Windows Kan jag läsa in en app från Windows Store separat?

    -   **Offentligt tillgängliga appar kan inte läsas in separat.**

        Även om du kan hämta XAP-filen kan du inte överföra den till Intune eftersom det är en offentlig XAP-fil som är krypterad och signerad med utvecklarens kodsigneringscertifikat. Du kan bara läsa in appar som du utvecklar och signerar med ditt eget kodsigneringscertifikat separat.

    -   **Måste slutanvändaren ha ett Microsoft-konto för att distribuera Windows Phone Store-appar via företagsportalen?**

        Ja, slutanvändaren kan inte hämta appar utan ett Microsoft-konto. Undantaget är privata LOB-appar som läses in separat och som kan distribueras till en enhet utan ett Microsoft-konto.

        **Måste jag ha ett Microsoft-konto på Windows Phone 8.1 för att den ska kunna hanteras av Intune?**
        Nej. Men det krävs för att installera de flesta appar från den offentliga butiken. Varför kräver Windows Phone ett Symantec-certifikat för hanteringen? Windows Phone styr hur du installerar appar. Alla användare med ett Microsoftkonto kan installera appar från Store, företag kan installera eller sidladda sina internt utvecklade företagsappar (LOB) med hjälp av en särskild process som beskrivs i dokumentationen för Windows Phone.

        När du installerar LOB-appar, litar Windows Phones endast på en speciell typ av certifiering som utfärdats av Symantec. Du kan inte använda någon annan kommersiellt eller privat genererad certifiering. Detta krav gäller för alla mobila enhetshanteringslösningar, inte bara Intune. Symantec-certifikatet skapar en programregistreringstoken (AET). AET kan installeras på en enhet när enheten registreras för hantering av mobila enheter, eller installeras out-of-band från en säker webbplats eller ett e-postmeddelande. Administratörer måste signera varje LOB-app med Symantec-certifikatet med hjälp av de verktyg som finns i [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=268439). När användarna försöker installera LOB-appar kontrollerar operativsystemet i Windows Phone signaturen i AET gentemot signaturen i appen.

        -   Om signaturerna matchar kan installationen fortsätta.

        -   Installationen misslyckas om AET inte kan verifieras.

        -   Det finns flera orsaker till att AET inte kan verifieras:

        AET installerades aldrig på enheten

    **AET har upphört att gälla**
  AET skapades inte med samma Symantec-certifikat som användes för att signera appen Windows Phone kräver inte att AET finns vid MDM-registreringen, men före versionen som släpptes i november 2014, krävde Intune AET och en signerad ssp.xap eftersom det inte fanns någon möjlighet att installera AET och ssp.xap utom under registreringen.

      > Hur skapas AET för Intune-användare?

    **När administratörer överför .pfx-filen för sina Symantec-certifikat, skapar Intune automatiskt AET och distribuerar den till registrerade Windows Phone-enheter.**
       Det är inte nödvändigt för Intune-administratörer att använda AET-generatorn i Windows Phone SDK.

       -   Intune stöder inte att skapa AET manuellt och distribuera den out-of-band. Vilka ändringar har minskat behovet av ett Symantec-certifikat?

        -   I november 2014-versionen har Intune gjort ändringar för att tillåta scenarier där företag inte har något Symantec-certifikat. Företagsportalen för Windows Phone 8.1 är tillgänglig för installation från Store, så den behöver inte signeras med ett Symantec-certifikat eller verifieras mot en AET. I stället verifieras appen som en del av publiceringsprocessen i Store.

        Windows Phone 8.1-enheter kan registreras med eller utan en AET i telefonen. Om det finns en tillgänglig AET installeras den första gången enheten synkroniserar med Intune.

        **Om det inte finns någon AET kan enheten fortfarande hanteras av Intune och användarna kan installera företagsportalen från Store, samt använda de flesta funktioner i företagsportalen utan ett Symantec-certifikat för att signera appar.**
        Det finns inte några ändringar i Symantecs krav för Windows Phone 8-enheter.

        -   Windows Phone 8-enheter måste ha signerade ssp.xap och AET under registreringen, annars går de inte att registrera.

        -   Vilka funktioner stöds om en Windows Phone 8.1-enhet registreras, men det inte finns något Symantec-certifikat?

        -   Om en Windows Phone 8.1-enhet registreras, men det inte finns något Symantec-certifikat kan du:

        -   Skapa principer och push-installera dem på enheten

        -   Konfigurera kontaktinformation för IT-avdelningen som ska visas i företagsportalen

        Skapa djuplänkar till Store och distribuera dem till företagsportalen

        > [!IMPORTANT]
        > Skapa länkar till webbsidor och distribuera dem till företagsportalen Skapa villkor som måste godkännas av användarna innan de kan använda företagsportalen

        **Det enda du  inte kan utföra utan ett Symantec-certifikat är att distribuera LOB-appar.**
        Programvaruutgivaren för Intune kontrollerar inte att appar har signerats när du överför dem.. Om du distribuerar osignerade appar kommer användarna inte att kunna installera dem. Vad kan användarna göra om de har företagsportalen, men det inte finns något Symantec-certifikat?

        Windows Phone 8.1-enheter registreras inte förrän användarna installerar företagsportalen från Store.

        -   Om enheten inte har registrerats uppmanas användarna att registrera den. När användarna pekar på promptfrågan i företagsportalen kommer de direkt till **Inställningar / Arbetsyta** där de kan registrera sina enheter.

        -   Även om användarna inte registrerar enheten kan de utföra följande åtgärder när företagsportalen installerats från Store:

        -   Godkänna eller avvisa de villkor som konfigurerats av administratören.

        -   Om användarna inte godkänner villkoren stängs företagsportalen.

        -   Visa kontaktinformation för IT-avdelningen

        Visa alla registrerade enheter, inklusive iOS-, Android- och Windows-enheter Använda djuplänkar till appar i Store Använda webblänkar för att öppna webbsidor När enheten är registrerad kan användarna visa den i listan **Mina enheter** .

        När enheten har registrerats följer den alla distribuerade Intune-principer.

        **Enheter måste registreras för att kunna hämta AET och installera LOB-appar. En oregistrerad enhet som försöker installera en LOB-app kommer att skickas vidare till registreringen.**
        Det enda som användarna inte kan göra om företaget saknar ett Symantec-certifikat, är att installera LOB-appar som distribuerats av administratören. Vårt företag har redan ett certifikat och har registrerat Windows Phone 8.1-enheter.

        **Måste jag göra något annat nu när företagsportalen finns i Store?**
        Aktuell ssp.xap från Download Center fungerar fortfarande på Windows Phone 8.1-enheter.

        -   Du kan fortsätta att dirigera användare till att registrera och hämta företagsportalen under installationen.

        -   Vilka fördelar och nackdelar får användare som hämtar företagsportalen från Store?

        -   Fördelar:

        -   Användarna får djuplänkar och webblänkar, även om Windows Phone 8.1-enheten inte registrerats

        När Microsoft uppdaterar företagsportalen uppdateras Store-appen automatiskt utan att du behöver hämta, signera och omdistribuera ssp.xap

        -   Dokumentationen för Windows Phone 8.1-, iOS-, Android- och Windows-användare är samstämmig: ”Gå till Store och installera företagsportalen.”

        -   Användarna ser appen när den installeras och får registreringsanvisningar när den öppnas

        Nackdelar:

        -   Användarna ser en kryssruta för att installera en ”**företagshubb**”, men de dirigeras inte till företagsportalen i enhetens applista

        -   Användarna behöver inte acceptera anpassade villkor förrän de öppnar företagsportalen

        -   Du kan fortsätta dirigera användare att registrera sig och installera ssp.xap vid registreringen under följande omständigheter:

        **Om företaget blockerar åtkomsten till Store från Windows Phone-enheter, måste användarna få ssp.xap installerat under registreringen.**

        -   Om användarna inte har konfigurerat något Microsoft-konto på sin Windows Phone-enhet, kan de inte installera företagsportalen från Store.

        -   Om den befintliga dokumentationen för Windows Phone-registreringen säger att de ska gå till Inställningar, Arbetsyta först, kan det ta ett tag att uppdatera dokumenten och dirigera användarna till Store.

        -   Vad är skillnaden mellan ssp.xap i Download Center och appen i Store?

        **Företagsportalen i Store behöver inte vara signerat av ett Symantec-certifikat som måste vara installerat**
        Företagsportalen i Store visar villkoren för användaren, men det gör inte ssp.xap i Download Center Företagsportalen i Store är en .appx i stället för en .xap

        -   Kan jag hämta företagsportalens fil och push-installera den hos användarna i stället för att skicka dem till Store?

        -   Ja.

        -   Företagsportalappen kan laddas ner för följande operativsystem från Download Center:

        **Windows Phone 8.1: [http://go.microsoft.com/fwlink/?LinkId=615799](http://go.microsoft.com/fwlink/?LinkId=615799)**
        Windows Phone 8.0 : [http://go.microsoft.com/fwlink/?LinkId=268440](http://go.microsoft.com/fwlink/?LinkId=268440) Windows 8.1: [http://go.microsoft.com/fwlink/?LinkId=615800](http://go.microsoft.com/fwlink/?LinkId=615800) Kan företag fortfarande använda supportverktyget för Windows Intune-testhantering för Windows Phone om de inte har något Symantec-certifikat och ändå låta användarna installera företagsportalen från Store?

        Ja.

        > [!IMPORTANT]
        > Om du behöver göra ett POC (Proof Of Concept) som innefattar installationen av LOB-appar, fungerar testhanteringsverktyget med Store-versionen av företagsportalen. Även om AET från Symantec-certifikatet inte längre krävs för att registrera Windows Phone 8.1-enheter, kan företag testa appinstallationen med djuplänkar till appar i Store.

        **Supportverktyget för Windows Intune-testhanteringen för Windows Phone är endast avsett för utvärderingsprenumerationer på Intune.**
        Använd bara testhanteringsverktyget vid testning. Enheter som har registrerats med AET från testhanteringsverktyget måste avregistreras och omregistreras om Symantec-certifikatet för testhanteringsverktyget inte längre är tillgängligt, eller om företaget erhåller ett eget Symantec-certifikat för signering av appar. Kan företag börja utan Symantec-certifikat och lägga till ett senare, även efter att Windows Phone 8.1-enheter har registrerats? Ja. Även om Windows Phone 8.1-enheter redan har registrerats kan du få ett certifikat från Symantec, signera ssp.xap samt överföra den och pfx-filen.


-   **Intune skapar sedan AET.**

    -   **Windows Phone 8.1-enheter får AET nästa gång de synkroniseras, efter upp till åtta timmar.**

        Låt det gå minst åtta timmar innan du distribuerar branschspecifika appar efter överföring av xap och pfx.

-   **Android**

    -   **Hur lång tid tar det att kryptera en Android-enhet?**

        Det beror i första hand på hastigheten på enhetens processor och den totala mängden använt minne. Det är inte en funktion som ingår i Intune. iOS

    -   **Måste enheten ha ett Apple-ID för att installationen ska kunna fortsätta vid distribution av iOS-appar med Intune om appens IPA- och Manifest-fil har överförts?**

        Nej. När Intune tillhandahåller bitarna (IPA-filen har överförts till Intune) läses apparna in separat och du behöver inget Apple-ID.

    -   **Går det att aktivera installationen av appar på iOS utan att tillåta åtkomst till Apple Store?**

        Nej, men du kan aktivera App Store och använda tillåtna eller blockerade appar på iOS för att hålla koll på vad användarna gör.

    -   **LOB-appar som läses in separat behöver inte ha åtkomst till Apple App Store.**

        Måste slutanvändaren ha ett iTunes-konto för att distribuera Apple Store-appar via företagsportalen? Ja, slutanvändaren kan inte hämta appar utan ett iTunes-konto.

## Kan jag blockera App Store?

-   **Ja, det kan du. Men det blockerar alla appinstallationer och uppdateringar från App Store, inte bara de som initierats av slutanvändaren.**

    Det innebär att alla offentliga appar från App Store som du distribuerar från Intune också misslyckas.

-   **Appdistribution**

    Hur lägger jag till en rekommenderad app? I Intune kallas dessa ”aktuella appar” och dokumenteras i [Distribuera appar i Microsoft Intune](/Intune/Deploy-Use/deploy-apps-in-microsoft-intune.md).

## Kan jag få ytterligare molnlagring för appar som jag vill distribuera?

-   **Ja.**

    Du kan läsa om detta i [Distribuera appar](/Intune/Deploy-Use/deploy-apps.md), i avsnittet *Krav för molnlagring* Säkerhet Kan BitLocker tillämpas av Intune?

-   **Med OMA-DM-agenten i Windows 8.1/RT kan du läsa (hämta) krypteringsstatusen.**

    Du kan inte ange den. Detta gäller för Intune och för andra tjänster för hantering av mobila enheter. Kan jag rensa hela enheten om en användare flera gånger i följd misslyckas med att logga in om jag har krypterat en Windows 8-surfplatta med BitLocker?

## Det finns inget alternativ för fullständig rensning på Windows 8.1/RT-enheter för tjänster för hantering av mobila enheter, inklusive Intune.

-   **Med Intune kan du ta göra en selektiv rensning på dessa enheter.**

    Mer information om rensning/selektiv rensning i Intune finns i [Skydda data och appar med Microsoft Intune](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md) Företagsportal

## Kan jag anpassa företagsportalen?

-   **Ja.**

    Öppna administratörskonsolen i Intune och välj **Admin&gt;Företagsportal** för dessa inställningar. Microsoft Intune med Configuration Manager

-   **Var hanterar jag mina enheter när jag använder Configuration Manager med Intune?**

    Hantera alla dina enheter från Configuration Manager-konsolen även om enheter som har Intune-agenten installerad visas i Intune-konsolen. Mobila enheter visas inte i Intune-konsolen.

-   **Kan jag göra en selektiv rensning på enheter?**

    Om du använder System Center 2012 R2 Configuration Manager eller senare med Intune kan du göra en selektiv rensning som tar bort företagsdata. Mer information finns i [Skydda data och appar med Microsoft Intune](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md)



<!--HONumber=May16_HO2-->


