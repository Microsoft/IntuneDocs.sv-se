---
# required metadata

title: Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 05/05/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: karanda
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune
Många mobila plattformar har en *intern* e-postklient som levereras som en del av operativsystemet.  En del av dessa klienter kan konfigureras med e-postprofiler, enligt beskrivningen i det här avsnittet.

Om du behöver ytterligare skydd mot dataförlust (DLP) väljer du [Villkorlig åtkomst](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), som styr åtkomsten till användarens inkorg för alla e-postklienter, inklusive inbyggda e-postklienter.

Inställningar för e-postprofiler kan användas för att konfigurera åtkomstinställningar för e-post för specifika e-postklienter på mobila enheter.   De flesta mobila plattformar har en *intern* e-postklient som levereras som en del av operativsystemet.  På plattformar som stöds kan de interna e-postklienterna konfigureras av Microsoft Intune så att det blir möjligt för användarna att komma åt sin e-post för företaget på de personliga enheterna utan konfiguration.  

IT-administratörer eller användare kan också välja att installera alternativa e-postklienter, t.ex. Microsoft Outlook för Android eller iOS.  Dessa e-postklienter stöder inte e-postprofiler och kan inte konfigureras med hjälp av e-postprofiler i Microsoft Intune.  

Du kan använda e-postprofiler för att konfigurera den interna e-postklienten på följande enhetstyper:
-   Windows Phone 8 och senare
-   Windows 10 Desktop, Windows 10 Mobile, och senare
-   iOS 7.1 och senare
-   Samsung KNOX Standard (4.0 och senare)


Du kan konfigurera inställningar för synkronisering av till exempel hur många e-postmeddelanden som ska synkroniseras och, beroende på enhetstypen, vilka innehållstyper som ska synkroniseras.

## Skydda e-postprofiler
Du kan skydda e-postprofiler på något av två sätt:

### Certifikat
När du skapar en e-postprofil väljer du en certifikatprofil som du har skapat tidigare i Intune. Detta kallas identitetscertifikat och används för att autentisera mot en betrodd certifikatprofil (eller ett rotcertifikat) för att fastställa att användarens enhet får ansluta. Det betrodda certifikatet distribueras till datorn som verifierar e-postanslutningen, vanligtvis den interna e-postservern.

Mer information om hur du skapar och använder certifikatprofiler i Intune finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).

### Användarnamn och lösenord
Användaren autentiseras mot den interna e-postservern genom att ange sitt användarnamn och lösenord.

Lösenordet finns inte i e-postprofilen, användaren måste ange detta när de ansluter till sin e-post.

### Skapa en e-postprofil

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) klickar du på **Princip** &gt; **Lägg till princip**.

2.  Konfigurera en av följande principer:

    -   **E-postprofil för Samsung KNOX Standard (4.0 och senare)**

    -   **E-postprofil (iOS 7.1 och senare)**

    -   **E-postprofil (Windows Phone 8 och senare)**

    -   **E-postprofil (Windows 10 Desktop och Mobile och senare)**

    Du kan bara skapa och distribuera en princip för anpassad e-postprofil. Rekommenderade inställningar är inte tillgängliga.

3.  Använd följande tabell som hjälp för att konfigurera inställningar för e-postprofil:
    |Inställningsnamn|Mer information|
    |----------------|-----------------------------------------------------------------------------|
    |**Namn**|Unikt namn för e-postprofilen.|
    |**Beskrivning**|En beskrivning som hjälper dig att identifiera den här profilen.|
    |**Värd**|Värdnamnet för företagsservern som är värd för den interna e-posttjänsten.|
    |**Kontonamn**|Visningsnamnet för e-postkontot som kommer att visas på användarnas enheter.|
    |**Användarnamn**|Hur användarnamn för e-postkontot hämtas. Välj **Användarnamn** för en lokal Exchange-server eller välj **UPN (User Principal Name)** för Office 365.|
    |**E-postadress**|Hur e-postadressen för användaren på varje enhet genereras. Välj **Primär SMTP-adress** om du vill använda den primära SMTP-adressen för att logga in på Exchange eller använd **UPN (User Principal Name)** om du vill använda det fullständiga huvudnamnet som e-postadress.|
    |**Autentiseringsmetod** (Samsung KNOX och iOS)|Välj antingen **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som används av e-postprofilen.|
    |**Välj ett certifikat för klientautentisering (identitetscertifikat)** (Samsung KNOX och iOS)|Välj SCEP klientcertifikatet som du skapade tidigare som ska användas för att autentisera Exchange-anslutningen. Mer information om hur du använder certifikatprofiler i Intune finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).<br /><br />Det här alternativet visas endast när autentiseringsmetoden är **Certifikat**.|
    |**Använd S/MIME** (Samsung KNOX och iOS)|Skicka utgående e-post med S/MIME-kryptering.|
    |**Signeringscertifikat** (Samsung KNOX och iOS)|Välj signeringscertifikatet som ska användas för att signera utgående e-post.<br /><br />Det här alternativet visas bara om du väljer **Använd S/MIME**.|
    |**Antal dagars e-postmeddelande att synkronisera**|Hur många dagar för e-post som du vill synkronisera eller välj **Obegränsad** för att synkronisera alla tillgängliga e-postmeddelanden.|
    |**Synkroniseringsschema** (Samsung KNOX, Windows Phone 8 och senare, Windows 10)|Välj det schema som ska användas av enheterna som ska synkronisera data från Exchange-servern. Du kan även välja **Efter hand som meddelanden kommer** varvid data synkroniseras när de anländer eller **Manuell** där enhetens användare måste starta synkroniseringen.|
    |**Använd SSL**|Använda Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.<br /><br />För enheter som kör Samsung KNOX 4.0 eller senare kan du exportera Exchange-serverns SSL-certifikat och distribuera det som en Android-betrodd certifikatprofil i Intune. Intune stöder inte åtkomst till det här certifikatet om det är installerat på Exchange-servern på annat sätt.|
    |**Innehållstyp som ska synkroniseras**|Välj vilka typer av innehåll du vill synkronisera till enheterna.| 
    |**Tillåt att e-post skickas från tredjepartsprogram** (endast iOS)|Tillåt att tredjepartsprogram öppnar e-post i den interna e-postappen, t.ex. för att bifoga filer till e-post.|

    > [!IMPORTANT] Om du har distribuerat en e-postprofil och vill ändra värdena för **värd** eller **E-postadress** måste du ta bort den befintliga e-postprofilen och skapa en ny med nödvändiga värden.

4.  När du är klar klickar du på **Spara profilen**.

Ny princip som visas i noden **Konfigurationsprinciper** i arbetsytan **Principer** .

## Distribuera principen

1.  Välj den princip på arbetsytan **Princip** som du vill distribuera och klicka sedan på **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** :

    -   **Om du vill distribuera principen** - Markera en eller flera grupper som du vill distribuera principen till och klicka sedan på **Lägg till** &gt; **OK**.

    -   **Om du vill stänga dialogrutan utan att distribuera den** – Klicka på **Avbryt**.

En statssammanfattning och varningar på sidan **Översikt** på arbetsytan **Principer** identifierar problem med principer som kräver din uppmärksamhet. Dessutom visas en statussammanfattning på arbetsytan Instrumentpanel.

> [!NOTE] Om du vill ta bort en e-postprofil från en enhet, redigera distributionen och ta bort alla grupper där enheten är medlem.




<!--HONumber=Jun16_HO1-->


