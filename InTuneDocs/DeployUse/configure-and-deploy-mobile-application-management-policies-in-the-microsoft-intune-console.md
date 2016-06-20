---
# required metadata

title: Konfigurera och distribuera principer för hantering av mobilprogram i Microsoft Intune-konsolen | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configure and deploy mobile application management policies in the Microsoft Intune console
Med hjälp av principer för hantering av mobilprogram i Microsoft Intune kan du ändra funktionen i appar som du distribuerar för att anpassa dem till företagets kompatibilitets- och säkerhetsprinciper. Du kan till exempel begränsa åtgärder för att klippa ut, kopiera och klistra in inom en hanterad app eller konfigurera en app så att den öppnar alla länkar i en hanterad webbläsare.

Principerna för hantering av mobilprogram har stöd för:

-   Enheter som kör Android 4 och senare.

-   Enheter som kör iOS 7 och senare.

> [!TIP]Principer för hantering av mobilappar har stöd för enheter som har registrerats med Intune.
>
> Information om hur du skapar apphanteringsprinciper för enheter som inte hanteras av Intune finns i [Skydda appdata med hanteringsprinciper för mobila appar med Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

Till skillnad från andra Intune-principer kan du inte distribuera en princip för hantering av mobilprogram direkt. Du måste i stället associera principen med den app som du vill begränsa. När appen har distribuerats och installerats på enheter, börjar de inställningar du anger gälla.

Om du vill tillämpa begränsningar i en app måste den innehålla Microsoft Intune App SDK. Det finns tre metoder för att hämta den här typen av app:

-   **Använda en principhanterad app** – Har inbyggt app-SDK. Om du vill lägga till den här typen av app måste ange du en länk till appen från en appbutik som iTunes eller Google Play. Ingen ytterligare bearbetning krävs för den här typen av app. Visa en lista över [appar som du kan använda med Microsoft Intunes hanteringsprinciper för mobilprogram](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

-   **Använda en ”omsluten” app** – Appar som paketeras på nytt för att inkludera app-SDK med hjälp av **Microsoft Intunes apphanteringsverktyg**. Det här verktyget används vanligtvis för att bearbeta företagsappar som har skapats internt. Det kan inte användas för att bearbeta appar som har hämtats från App Store. Mer information finns i [Förbereda iOS-appar för hantering av mobila program med Microsoft Intunes-appomslutningsverktyg](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) och [Förbereda Android-appar för hantering av mobila program med Microsoft Intunes-appomslutningsverktyg](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)

- **Skriv din egna app som inkorporerar Intune App SDK** – Intunes App SDK låter du inkludera app-hanteringsfunktioner i en app när du skriver den. Mer information finns i [Översikt över Intune App SDK](/develop/intune-app-sdk)

Om du behöver hjälp med att välja mellan Intunes apphanteringsverktyg och Intune App SDK läser du [Förbereda appar för hantering av mobilprogram med Microsoft Intune](/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)

Vissa hanterade appar, t.ex. Outlook-appen för iOS och Android, stöder **flera identiteter**. Detta innebär att Intune endast tillämpar hanteringsinställningar för företagskonton eller data i appen.

Om du t.ex. använder Outlook-appen:

-   Om användaren konfigurerar ett e-postkonto för företag och ett privat tillämpar Intune hanteringsinställningarna enbart på företagskontot och hanterar inte det privata kontot.

-   Om enheten har dragits tillbaka eller avregistrerats tas enbart företagets Outlook-data bort från enheten.

-   Det företagskonto som används måste vara samma konto som användes för att registrera enheten med Intune.

> [!TIP] Om du använder Intune med Configuration Manager läser du [Kontrollera appar med principer för hantering av mobilprogram i Configuration Manager](https://technet.microsoft.com/library/mt131414.aspx).

## Skapa och distribuera en app med en princip för hantering av mobila program

-   **Steg 1:** Hämta en länk till en principhanterad app, skapa en omsluten app eller använd Intune App SDK för att skriva en MAM-aktiverad app.

-   **Steg 2:** Publicera appen i ditt molnlagringsutrymme.

-   **Steg 3:** Skapa en princip för hantering av mobila program.

-   **Steg 4:** Distribuera appen, välj att associera appen med en princip för hantering av mobila program.

-   **Steg 5:** Övervaka appdistributionen.

## **Steg 1:** Hämta en länk till en principhanterad app, skapa en omsluten app eller använd Intune App SDK för att skriva en MAM-aktiverad app.

-   **Så här skaffar du en länk till en principhanterad app i en appbutik** – Från appbutiken letar du reda på och skriver ner webbadressen till den principhanterade app som du vill distribuera.

    Exempelvis är webbadressen till Microsoft Word för iPad-appen **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**


## **Steg 2:** Publicera appen i ditt molnlagringsutrymme
När du publicerar en hanterad app varierar procedurerna beroende på om du publicerar en principhanterad app eller en app som bearbetats med Microsoft Intune App Wrapping-verktyget för iOS.

#### Så här publicerar du en principhanterad app

1.  När du är redo att överföra appen till molnlagringsutrymmet följer du anvisningarna i [Lägg till appar för mobila enheter i Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  För IOS-appar väljer du **Hanterade iOS-appar från App Store**under **Välj hur programvaran görs tillgänglig för enheter**.

    För Android-appar väljer du **Extern länk**.

3.  Under **Ange en URL**anger du webbadressen till den principhanterade app du antecknade tidigare.

När överföringen har slutförts visas **Ja** för **Apphanteringsprinciper** på sidan **Programvaruegenskaper** för den överförda appen.

När du har kontrollerat att appen överförts, fortsätter du till steg 3.

#### Så här publicerar du en app som bearbetades med verktyget Microsoft Intune App Wrapping

1.  När du är redo att överföra appen till molnlagringsutrymmet följer du anvisningarna i [Lägg till appar för mobila enheter i Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  Välj **Installationsprogram för programvara**under **Välj hur programvaran görs tillgänglig för enheter**.

3.  Välj **Appaket för iOS (&#42;.ipa-fil)** under **Filtyp för installationsprogram för programvara**.

När överföringen har slutförts visas **Ja** för **Apphanteringsprinciper** på sidan **Programvaruegenskaper** för den överförda appen.

När du har kontrollerat att appen överförts, fortsätter du till steg 3.

## **Steg 3:** Skapa en princip för hantering av mobila program

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Översikt** &gt; **Lägg till princip**.

2.  Konfigurera och distribuera någon av följande principer för **Programvara** , beroende på vilken enhetstyp du vill konfigurera appar för:

    -   **Princip för hantering av mobila program (Android 4 och senare)**

    -   **Princip för hantering av mobila program (iOS 7 och senare)**

    Du kan använda rekommenderade inställningar eller anpassa inställningarna. Mer information finns i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Konfigurera följande inställningar efter behov. Alternativen kan variera beroende på enhetstypen som du konfigurerar principen för.

|Inställningsnamn|Information|
    |---------|--------------------|
    |**Namn**|Ange principens namn.|
    |**Beskrivning**|Du kan, om du vill, ange en beskrivning av principen.|
    |**Begränsa webbinnehåll till att bara visas i en företagshanterad webbläsare**|När den här inställningen är aktiverad öppnas alla länkar i appen i den hanterade webbläsaren. Du måste ha distribuerat den här appen till enheter för att det här alternativet ska fungera.|
    |**Förhindra Android-säkerhetskopieringar** eller **Förhindra iTunes- och iCloud-säkerhetskopieringar**|Inaktiverar all säkerhetskopiering från appen.|
    |**Tillåt att appen överför information till andra appar**|Anger de appar som den här appen kan skicka data till. Du kan välja att inte tillåta dataöverföring till någon app alls, att endast tillåta överföring till andra hanterade appar, eller att tillåta överföring till alla appar. Den här inställningen kontrollerar användningen av funktionen **Öppna med** på mobila enheter.<br /><br />Exempel: när du inte tillåter dataöverföring begränsar du dataöverföring till tjänster som SMS, att tilldela bilder till kontakter och att skicka information till Facebook eller Twitter.<br /><br />Om du vill förhindra dokumentöverföring mellan hanterade och ohanterade appar på iOS-enheter måste du även konfigurera och distribuera en säkerhetsprincip för mobila enheter som inaktiverar inställningen **Tillåt hanterade dokument i andra ohanterade appar** Om du väljer att endast tillåta överföring till andra hanterade appar kommer Intunes PDF- och bildvisningsprogram (om de har distribuerats) att används för att öppna innehållet i respektive typ.<br /><br />Om du anger det här alternativet till **Principhanterade appar** eller **Ingen** blockeras dessutom iOS 9-funktionen som gör att Spotlight-sökning kan söka efter data i appar.|
    |**Tillåt att appen hämtar data från andra appar**|Anger de appar som den här appen kan ta emot data från. Du kan välja att inte tillåta dataöverföring från någon app alls, att endast tillåta överföring från andra hanterade appar eller att tillåta överföring från alla appar<br /><br />För iOS-appar som stöder flera identiteter (där Intune endast tillämpar hanteringsinställningar på företagskonton eller data i appen), på en registrerad enhet som en princip för hantering av mobilprogram tillämpas på, behandlas data som företagsdata och skyddas av principen om en användare kommer åt data från en app som inte hanteras av en hanteringsprincip för mobilprogram.|
    |**Förhindra ”Spara som”**|Inaktiverar användningen av alternativet **Spara som** för att spara data till personliga lagringsplatser i molnet (exempelvis OneDrive eller Dropbox) i alla appar som använder den här principen.|
    |**Begränsa klipp ut, kopiera och klistra in med andra appar**|Anger hur klipp ut-, kopiera- och klistra in-åtgärder kan användas med appen. Välj mellan:<br /><br />**Blockerad** – Tillåt inte klipp ut-, kopiera- och klistra in-åtgärder mellan den här appen och andra appar.<br /><br />**Principhanterade appar** – Tillåt endast klipp ut-, kopiera- och klistra in-åtgärder mellan den här appen och andra hanterade appar.<br /><br />**Principhanterade appar med Klistra in i** – Tillåt att data som klipps ut eller kopieras från den här appen endast kan klistras in i andra hanterade appar. Tillåt att data som klipps ut eller kopieras från en annan app kan klistras in i den här appen.<br /><br />**Alla appar** – Inga begränsningar för klipp ut-, kopiera- och klistra in-åtgärder till eller från den här appen.<br /><br />För att kopiera och klistra in data mellan hanterade appar måste båda apparna ha inställningar konfigurerade för antingen **Principhanterade appar** eller **Principhanterade appar med Klistra in i** konfigurerade.|
    |**Kräv enkel PIN-kod för åtkomst**|Kräver att användaren anger en PIN-kod när de ska använda den här appen. Användaren ombeds att ställa in den första gången de kör appen.|
    |**Antal försök innan PIN-koden återställs**|Ange hur många försök med PIN-koden som kan göras innan användaren måste återställa PIN-koden.|
    |**Kräv företagets autentiseringsuppgifter för åtkomst**|Kräver att användaren måste ange företagets inloggningsinformationen innan de kan använda appen.|
    |**Kräv enhetens efterlevnad med företagsprinciper för att få åtkomst**|Tillåter endast användning av appen när enheten inte är jailbreakad eller rotad.|
    |**Kontrollera åtkomstbehörigheterna på nytt efter (minuter)**|I fältet **Tidsgräns** anger du hur lång tid som ska gå innan åtkomstkraven för appen kontrolleras på nytt efter att den har startats.|
    |**Offline-respitperiod**|Ange hur lång tid som ska gå innan åtkomstkraven för appen kontrolleras på nytt om enheten är offline.|
    |**Kryptera appdata**|Anger att alla data som är associerade med appen krypteras, inklusive data som lagras externt, till exempel SD-kort.<br /><br />**Kryptering för iOS**<br /><br />För appar som är associerade med en Intune-princip för hantering av mobila program krypteras data i viloläge med hjälp av den enhetskryptering som finns i operativsystemet. Detta är aktiverat via enhetens PIN-princip som måste anges av IT-administratören. När en PIN-kod krävs krypteras data enligt inställningarna i principen för hantering av mobila program. Enligt informationen i Apples dokumentation är de [moduler som används av iOS 7 FIPS 140-2-certifierade](http://support.apple.com/en-us/HT202739).<br /><br />**Kryptering för Android**<br /><br />För appar som är associerade med en Intune-princip för hantering av mobila program tillhandahålls krypteringen av Microsoft. Data krypteras synkront under I/O-åtgärder.  Innehållet på enhetens lagring krypteras alltid. Krypteringsmetoden är inte FIPS 140-2-certifierad.|
    |**Blockera skärmdump** (endast Android-enheter)|Anger att skärmdumpsfunktionen i enheten är blockerad när du använder den här appen.|

4.  När du är klar väljer du **Spara princip**.

Ny princip som visas i noden **Konfigurationsprinciper** i arbetsytan **Principer** .

## **Steg 4:** Associera appen till en princip för hantering av mobila program och distribuera sedan appen.
Distribuera appen och se till att du väljer principen för hantering av mobila program på sidan **Hantering av mobilappar** för att associera principen med appen.

Mer information finns i [Distribuera appar i Microsoft Intune](deploy-apps.md).

> [!IMPORTANT] För enheter som kör operativsystem tidigare än iOS 7.1 tas tillhörande principer inte bort när appen avinstalleras.
>
> Om enheten avregistreras från Intune tas principerna inte bort från apparna. Alla appar som hade tillämpade principer behåller principinställningarna även efter att appen avinstallerats och installerats om.

### Vad du gör om en app redan har distribuerats på enheter
Det kan finnas situationer då du distribuerar en app och en av de hanterade användarna eller enheterna redan har en ohanterad version av appen installerad, t.ex. om användaren har installerat Microsoft Word från appbutiken.

I så fall måste du be användaren att manuellt avinstallera den ohanterade versionen så att det går att installera den hanterade version som du har konfigurerat.

För enheter som kör iOS 9 och senare ber Intune dock användaren om tillstånd att ta över hanteringen av den befintliga appen. Om användaren accepterar börjar appen hanteras av Intune och de hanteringsprinciper för mobilprogram som du har associerat med appen börjar tillämpas.

> [!TIP] Om enheten är i övervakat läge tar Intune över hanteringen av den befintliga appen utan att be om användarens tillstånd.

## **Steg 5:** Övervaka appdistributionen.
När du har skapat och distribuerat en app som är associerad med en princip för hantering av mobila program, kan du använda följande procedurer för att övervaka appen och lösa eventuella principkonflikter.

#### Så här visar du status för distributionen

1.  Gå till [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) och välj **Grupper** &gt; **Översikt**.

2.  Utför något av följande steg:

    -   Välj **Alla användare** och dubbelklicka på den användare vars enhet du vill undersöka. På sidan **Användaregenskaper** väljer du **Enheter**. Dubbelklicka sedan på enheten som du vill undersöka.

    -   Välj **Alla enheter** &gt; **Alla mobila enheter**. På sidan **Egenskaper för enhetsgrupp** väljer du **Enheter**. Dubbelklicka sedan på enheten som du vill undersöka.

3.  På sidan **Egenskaper för mobil enhet** väljer du **Princip** för att se en lista över de principer för hantering av mobila program som har distribuerats till enheten.

4.  Välj den princip för hantering av mobila program vars status du vill visa. Du kan se information om principen längst ned i fönstret och expandera dess nod om du vill visa dess inställningar.

5.  Under kolumnen **Status** för var och en av principerna för hantering av mobila program visas **Överensstämmer**, **Överensstämmer (väntar)**eller **Fel** . Om den markerade principen har en eller flera inställningar i konflikt, visas **Fel** i det här fältet.

6.  När du har identifierat en konflikt kan du ändra motstridiga principinställningar till att använda samma inställning, eller endast distribuera en princip till appen och användaren.

### Så här löser du principkonflikter
Om det finns en konflikt i principen för hantering av mobila program under den första distributionen till användare eller enhet, kommer det specifika konfliktvärdet tas bort från principen som distribueras till appen och appen kommer att använda ett inbyggt konfliktvärde.

Om det finns en konflikt i principen för hantering av mobila program vid senare distributioner till app eller användare, kommer det specifika konfliktvärdet inte uppdateras i principen för hantering av mobila program som distribueras till appen, och appen kommer att använda det befintliga värdet för inställningen.

I de fall där enheten eller användaren får två motstridiga principer, gäller följande:

-   Om principen redan har distribuerats till enheten kommer befintliga principinställningar inte att skrivas över.

-   Om ingen princip har distribuerats till enheten och två motstridiga inställningar distribueras, används standardinställningen som är inbyggd i enheten.


<!--HONumber=Jun16_HO2-->


