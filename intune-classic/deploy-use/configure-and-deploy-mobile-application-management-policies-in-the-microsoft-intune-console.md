---
title: Konfigurera MAM-principer i Intune-konsolen
description: "Med hjälp av principer för hantering av mobilprogram i Microsoft Intune kan du ändra funktionen i appar som du distribuerar för att anpassa dem till företagets kompatibilitets- och säkerhetsprinciper."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 03/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 881180fec0fe4fca8b49106bcae6ea1ecd52c2eb
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/23/2018
---
# <a name="configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console"></a>Configure and deploy mobile application management policies in the Microsoft Intune console

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Med hjälp av hanteringsprinciper för mobilprogram (MAM) i Microsoft Intune kan du ändra funktionen i appar som du distribuerar för att anpassa dem till företagets kompatibilitets- och säkerhetsprinciper. Du kan till exempel begränsa åtgärder för att klippa ut, kopiera och klistra in inom en hanterad app eller konfigurera en app så att den öppnar alla länkar i en hanterad webbläsare.

Principerna för hantering av mobilprogram har stöd för:

-   Enheter som kör Android 4 och senare.

-   Enheter som kör iOS 8.0 och senare.

> [!TIP]
> Principer för hantering av mobilprogram stöder enheter som registrerats med Intune.
>
> Information om hur du skapar apphanteringsprinciper för enheter som inte hanteras av Intune finns i [Skydda appdata med hanteringsprinciper för mobila appar med Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

Till skillnad från andra Intune-principer kan du inte distribuera en princip för hantering av mobilprogram direkt. Du måste i stället associera principen med den app som du vill begränsa. Inställningarna du anger börjar gälla när appen har distribuerats och installerats på enheterna.

Om du vill tillämpa begränsningar i en app måste den innehålla Microsoft Intune App SDK. Det finns tre metoder för att hämta den här typen av app:

-   **Använda en principhanterad app**. En principhanterad app har en inbyggd App SDK. Om du vill lägga till den här typen av app måste ange du en länk till appen från en appbutik som iTunes eller Google Play. Ingen ytterligare bearbetning krävs för den här typen av app. Mer information finns i [listan med appar som du kan använda med Microsoft Intunes hanteringsprinciper för mobilprogram](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

-   **Använda en omsluten app**. En omsluten app är en app som du paketerar på nytt för att inkludera App SDK med hjälp av Microsoft Intunes programhanteringsverktyg. Det här verktyget används vanligtvis för att bearbeta företagsappar som har skapats internt. Du kan inte använda verktyget för att bearbeta appar som har hämtats från App Store. Mer information finns i [Förbereda iOS-appar för hantering av mobilprogram med Intunes programhanteringsverktyg](/intune/app-wrapper-prepare-ios) och [Förbereda Android-appar för hantering av mobilprogram med Intunes programhanteringsverktyg](/intune/app-wrapper-prepare-android).

- **Skriv egna app som införlivar Intune App SDK**. Med Intunes App SDK kan du införliva apphanteringsfunktioner i en app när du skriver den. Mer information finns i [Översikt över Intune App SDK](/intune/app-sdk).
/intune/apps-prepare-mobile-application-management Om du behöver hjälp med att välja mellan Intunes programhanteringsverktyg och Intune App SDK läser du [Förbereda appar för hantering av mobilprogram med Microsoft Intune](/intune/apps-prepare-mobile-application-management).

Vissa hanterade appar, t.ex. Outlook-appen för iOS och Android, stöder *flera identiteter*. Detta innebär att Intune tillämpar hanteringsinställningar endast för företagskonton eller data i appen.

Om du t.ex. använder Outlook-appen:

-   Om användaren konfigurerar ett e-postkonto för företag och ett privat, tillämpar Intune hanteringsinställningarna enbart på företagskontot och hanterar inte det privata kontot.

-   Om enheten har dragits tillbaka eller avregistrerats tas enbart företagets Outlook-data bort från enheten.

-   Företagskontot måste vara samma konto som användes för att registrera enheten med Intune.

> [!TIP]
> Om du använder Intune med Configuration Manager läser du [Kontrollera appar med principer för hantering av mobilprogram i Configuration Manager](https://technet.microsoft.com/library/mt131414.aspx).

## <a name="create-and-deploy-an-app-with-a-mobile-application-management-policy"></a>Skapa och distribuera en app med en princip för hantering av mobila program

-   **Steg 1:** Hämta en länk till en principhanterad app, skapa en omsluten app eller använd Intune App SDK för att skriva en MAM-aktiverad app.

-   **Steg 2:** Publicera appen i ditt molnlagringsutrymme.

-   **Steg 3:** Skapa en princip för hantering av mobila program.

-   **Steg 4:** Associera appen till en princip för hantering av mobila program och distribuera sedan appen.

-   **Steg 5:** Övervaka appdistributionen.

## <a name="step-1-get-the-link-to-a-policy-managed-app-create-a-wrapped-app-or-use-the-intune-app-sdk-to-write-a-mam-enabled-app"></a>Steg 1: Hämta en länk till en principhanterad app, skapa en omsluten app eller använd Intune App SDK för att skriva en MAM-aktiverad app

Gå till appbutiken och leta reda på och skriv ner webbadressen till den principhanterade app som du vill distribuera. Exempelvis är webbadressen till Microsoft Word för iPad-appen **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.


## <a name="step-2-publish-the-app-to-your-cloud-storage-space"></a>Steg 2: Publicera appen i ditt molnlagringsutrymme
När du publicerar en hanterad app varierar procedurerna beroende på om du publicerar en principhanterad app eller en app som bearbetats med Microsoft Intunes programhanteringsverktyg för iOS.

#### <a name="to-publish-a-policy-managed-app"></a>Så här publicerar du en principhanterad app

1.  När du är redo att överföra appen till molnlagringsutrymmet följer du anvisningarna i [Lägg till appar för mobila enheter i Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  För IOS-appar väljer du **Hanterade iOS-appar från App Store** under **Välj hur programvaran görs tillgänglig för enheter**.

    För Android-appar väljer du **Extern länk**.

3.  Under **Ange en URL**anger du webbadressen till den principhanterade app du antecknade tidigare.

När överföringen har slutförts visas **Ja** för **Apphanteringsprinciper** på sidan **Programvaruegenskaper** för den överförda appen.

När du har kontrollerat att appen överförts, fortsätter du till steg 3.

#### <a name="to-publish-an-app-that-was-processed-through-the-microsoft-intune-app-wrapping-tool"></a>Så här publicerar du en app som har bearbetats med Microsoft Intunes programhanteringsverktyg

1.  När du är redo att överföra appen till molnlagringsutrymmet följer du anvisningarna i [Lägg till appar för mobila enheter i Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  Välj **Installationsprogram för programvara** under **Välj hur programvaran görs tillgänglig för enheter**.

3.  Välj **Appaket för iOS (&#42;.ipa-fil)** under **Filtyp för installationsprogram för programvara**.

När överföringen har slutförts visas **Ja** för **Apphanteringsprinciper** på sidan **Programvaruegenskaper** för den överförda appen.

När du har kontrollerat att appen överförts, fortsätter du till steg 3.

## <a name="step-3-create-a-mobile-application-management-policy"></a>Steg 3: Skapa en princip för hantering av mobila program

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Översikt** &gt; **Lägg till princip**.

2.  Konfigurera och distribuera någon av följande principer för **Programvara** , beroende på vilken enhetstyp du vill konfigurera appar för:

    -   **Princip för hantering av mobila program (Android 4 och senare)**

    -   **Hanteringsprincip för mobilprogram (iOS 8.0 och senare)**

    Du kan använda rekommenderade inställningar eller anpassa inställningarna. Mer information finns i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Konfigurera följande inställningar efter behov. Alternativen kan variera beroende på enhetstypen som du konfigurerar principen för.

|Inställningsnamn|Information|
    |---------|--------------------|
    |**Namn**|Ange principens namn.|
    |**Beskrivning**|Du kan, om du vill, ange en beskrivning av principen.|
    |**Begränsa webbinnehåll till att bara visas i en företagshanterad webbläsare**|När den här inställningen är aktiverad öppnas alla länkar i appen i den hanterade webbläsaren. Du måste ha distribuerat den här appen till enheter för att det här alternativet ska fungera.|
    |**Förhindra Android-säkerhetskopieringar** eller **Förhindra iTunes- och iCloud-säkerhetskopieringar**|Den här inställningen inaktiverar all säkerhetskopiering från appen.|
    |**Tillåt att appen överför information till andra appar**|Den här inställningen vilka appar som den här appen kan skicka data till. Du kan välja att inte tillåta dataöverföring till någon app alls, att tillåta överföring till endast andra hanterade appar, eller att tillåta överföring till alla appar. <br /><br />Exempel: när du inte tillåter dataöverföring begränsar du dataöverföring till tjänster som SMS, att tilldela bilder till kontakter och att skicka information till Facebook eller Twitter.<br /><br />För att förhindra dokumentöverföring i iOS-enheter mellan hanterade och ohanterade appar, måste du också konfigurera och distribuera en säkerhetsprincip för mobila enheter som inaktiverar inställningen **Tillåt hanterade dokument i andra ohanterade appar**. Om du väljer att endast tillåta överföring till andra hanterade appar kommer Intune PDF och bildvisningsprogram (om de har distribuerats) att användas för att öppna de olika innehållstyperna.<br /><br />Om du anger det här alternativet till **Principhanterade appar** eller **Ingen** blockeras dessutom iOS 9-funktionen som gör att Spotlight-sökning kan söka efter data i appar.<br><br>Den här inställningen styr inte användningen av funktionen Öppna med på mobila enheter. Information om Öppna med finns i [Hantera dataöverföring mellan iOS-appar med Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).|
    |**Tillåt att appen hämtar data från andra appar**|Den här inställningen anger de appar som den här appen kan ta emot data från. Du kan välja att inte tillåta dataöverföring från någon app alls, att tillåta överföring endast från andra hanterade appar eller att tillåta överföring från alla appar.<br /><br />Om en användare kommer åt data från en app som inte hanteras av en hanteringsprincip för mobilprogram behandlas dessa data som företagsdata och skyddas av principen. Detta gäller iOS-appar som stöder flera identiteter (där Intune tillämpar hanteringsinställningar endast för företagskonton eller data i appen). Eller så gäller detta för en registrerad enhet som en hanteringsprincip för mobilprogram tillämpas på.|
    |**Förhindra ”Spara som”**|Den här inställningen inaktiverar användningen av alternativet **Spara som** för att spara data till personliga lagringsplatser i molnet (exempelvis OneDrive eller Dropbox) i alla appar som använder den här principen.|
    |**Begränsa klipp ut, kopiera och klistra in med andra appar**|Den här inställningen anger hur åtgärderna Klipp ut, Kopiera och Klistra in kan användas med appen. Välj mellan:<br /><br />**Blockerad**. Tillåt inte åtgärderna Klipp ut, Kopiera och Klistra in mellan principhanterade appar.<br /><br />**Principhanterade appar**. Tillåt åtgärderna Klipp ut, Kopiera och Klistra in endast mellan den här appen och andra hanterade appar.<br /><br />**Principhanterade appar med inklistring**. Tillåt att data som klipps ut eller kopieras från den här appen endast kan klistras in i andra hanterade appar. Tillåt att data som klipps ut eller kopieras från en annan app kan klistras in i den här appen.<br /><br />**Alla appar**. Använd inga begränsningar för åtgärderna Klipp ut, Kopiera och Klistra in till eller från den här appen.<br /><br />För att kopiera och klistra in data mellan hanterade appar måste båda apparna ha inställningar konfigurerade för antingen **Principhanterade appar** eller **Principhanterade appar med inklistring**.|
    |**Kräv enkel PIN-kod för åtkomst**|Den här inställningen kräver att användaren anger en PIN-kod för att använda appen. Användaren ombeds att ställa in den första gången de kör appen.|
    |**Antal försök innan PIN-koden återställs**|Ange antalet tillåtna PIN-inmatningsförsök innan användaren måste återställa PIN-koden.|
    |**Kräv företagets autentiseringsuppgifter för åtkomst**|Den här inställningen kräver att användarna anger företagets inloggningsinformation innan de kan använda appen.|
    |**Kräv enhetens efterlevnad med företagsprinciper för att få åtkomst**|Den här inställningen tillåter användning av appen endast om enheten inte är jailbreakad eller rotad.|
    |**Kontrollera åtkomstbehörigheterna på nytt efter (minuter)**|I fältet **Tidsgräns** anger du hur lång tid som ska gå innan åtkomstkraven för appen kontrolleras på nytt efter att den har öppnats.|
    |**Offline-respitperiod**|Ange hur lång tid som ska gå innan åtkomstkraven för appen kontrolleras på nytt om enheten är offline.|
    |**Kryptera appdata**|Den här inställningen anger att alla data som är associerade med appen krypteras. Detta innefattar data som lagras externt, till exempel på SD-kort.<br /><br />**Kryptering för iOS**<br /><br />För appar som är associerade med Intunes hanteringsprincip för mobilprogram krypteras data i viloläge med hjälp av den enhetskryptering som finns i operativsystemet. Detta aktiveras via enhetens PIN-princip som anges av IT-administratören. När en PIN-kod krävs krypteras data enligt inställningarna i hanteringsprincipen för mobilprogram. Enligt informationen i Apples dokumentation är [modulerna som används i iOS 140-2 FIPS 140-2-certifierade](http://support.apple.com/HT202739).<br /><br />**Kryptering för Android**<br /><br />För appar som är associerade med Intunes hanteringsprincip för mobilprogram tillhandahålls krypteringen av Microsoft. Data krypteras synkront under I/O-åtgärder.  Innehållet på enhetens lagring krypteras alltid. Krypteringsmetoden är endast FIPS 140-2-kompatibel för Samsung KNOX-enheter.|
    |**Blockera skärmdump** (endast Android-enheter)|Den här inställningen anger att skärmdumpsfunktionen i enheten är blockerad när någon använder den här appen.|

4. När du är klar väljer du **Spara princip**.

Den nya principen visas i noden **Konfigurationsprinciper** på arbetsytan **Principer** .

## <a name="step-4-associate-the-app-with-a-mobile-application-management-policy-and-then-deploy-the-app"></a>Steg 4: Associera appen till en hanteringsprincip för mobilprogram och distribuera sedan appen
Se till att du väljer hanteringsprincipen för mobilprogram på sidan **Hantering av mobilappar** i dialogrutan **Hantera distribuering** för att associera principen med appen.

Mer information finns i [Distribuera appar i Microsoft Intune](deploy-apps.md).

> [!IMPORTANT]
> Om enheten har avregistrerats från Intune tas inte principerna bort från apparna. Alla appar med tillämpade principer behåller principinställningarna när de avinstalleras och installeras om.

### <a name="what-to-do-when-an-app-is-already-deployed-on-devices"></a>Vad du gör om en app redan har distribuerats på enheter
Det kan finnas situationer då du distribuerar en app och en av målanvändarna eller målenheterna redan har en ohanterad version av appen installerad. Till exempel kan användaren ha installerat Microsoft Word från App Store.

I så fall måste du be användaren att manuellt avinstallera den ohanterade versionen så att det går att installera den hanterade version som du har konfigurerat.

För enheter som kör iOS 9 och senare ber Intune dock användaren om tillstånd att ta över hanteringen av den befintliga appen. Om användaren accepterar börjar appen hanteras av Intune och de hanteringsprinciper för mobilprogram som du har associerat med appen börjar tillämpas.

> [!TIP]
> Om enheten är i övervakat läge tar Intune över hanteringen av den befintliga appen utan att be om användarens tillstånd.

## <a name="step-5-monitor-the-app-deployment"></a>Steg 5: Övervaka appdistributionen
När du har skapat och distribuerat en app som är associerad med en princip för hantering av mobila program, kan du använda följande procedurer för att övervaka appen och lösa eventuella principkonflikter.

#### <a name="to-view-the-status-of-the-deployment"></a>Så här visar du status för distributionen

1.  Gå till [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) och välj **Grupper** &gt; **Översikt**.

2.  Utför något av följande steg:

    -   Välj **Alla användare** och dubbelklicka på den användare vars enhet du vill undersöka. På sidan **Användaregenskaper** väljer du **Enheter**. Dubbelklicka sedan på enheten som du vill undersöka.

    -   Välj **Alla enheter** &gt; **Alla mobila enheter**. På sidan **Egenskaper för enhetsgrupp** väljer du **Enheter**. Dubbelklicka sedan på enheten som du vill undersöka.

3.  På sidan **Egenskaper för mobil enhet** väljer du **Princip** för att se en lista över de principer för hantering av mobila program som har distribuerats till enheten.

4.  Välj den princip för hantering av mobila program vars status du vill visa. Du kan se information om principen längst ned i fönstret och expandera dess nod om du vill visa dess inställningar.

5.  Under kolumnen **Status** för var och en av principerna för hantering av mobila program visas **Överensstämmer**, **Överensstämmer (väntar)**eller **Fel**. Om den markerade principen har en eller flera inställningar i konflikt, visas **Fel** i det här fältet.

6.  När du har identifierat en konflikt kan du ändra motstridiga principinställningar till att använda samma inställning, eller så kan du distribuera endast en princip till appen och användaren.

### <a name="how-policy-conflicts-are-resolved"></a>Så här löser du principkonflikter
Om det finns en konflikt i principen för hantering av mobila program under den första distributionen till användare eller enhet, kommer det specifika konfliktvärdet tas bort från principen som distribueras till appen. Appen kommer att använda ett inbyggt konfliktvärde.

Om det finns en konflikt i principen för hantering av mobila program vid senare distributioner till app eller användare, kommer det specifika konfliktvärdet inte uppdateras i principen för hantering av mobila program som distribueras till appen. Appen kommer att använda det befintliga värdet för inställningen.

I de fall där enheten eller användaren får två motstridiga principer, gäller följande:

-   Om principen redan har distribuerats till enheten kommer befintliga principinställningar inte att skrivas över.

-   Om ingen princip har distribuerats till enheten och två motstridiga inställningar distribueras, används standardinställningen som är inbyggd i enheten.
