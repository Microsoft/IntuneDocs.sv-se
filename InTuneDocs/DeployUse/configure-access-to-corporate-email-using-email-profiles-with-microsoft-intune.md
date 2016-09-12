---
title: "Kom åt företagets e-post med hjälp av e-postprofiler | Microsoft Intune"
description: "Inställningar för e-postprofiler kan användas för att konfigurera åtkomstinställningar för e-post för specifika e-postklienter på mobila enheter."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d8a4fd4673560d6e2ffb4264ba8d8e56b0e5cb8d
ms.openlocfilehash: 59b8cc2ad33521fd4575e46d78129c168da757b3


---

# Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune
Många mobila plattformar har en intern e-postklient som levereras som en del av operativsystemet. En del av dessa klienter kan konfigureras med e-postprofiler, enligt beskrivningen i det här avsnittet.

Inställningar för e-postprofiler kan användas för att konfigurera åtkomstinställningar för e-post för specifika e-postklienter på mobila enheter. På plattformar som stöds kan de interna e-postklienterna konfigureras med Microsoft Intune så att användarna kan komma åt sin e-post för företaget på sina personliga enheter utan ytterligare inställningar.

Om du behöver vidta ytterligare åtgärder mot dataförlust (DLP) kan du använda [Villkorlig åtkomst](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), som styr åtkomsten till användarens inkorg för alla e-postklienter, inklusive inbyggda e-postklienter.

IT-administratörer eller användare kan också välja att installera alternativa e-postklienter, t.ex. Microsoft Outlook för Android eller iOS. Dessa e-postklienter stöder inte e-postprofiler och kan inte konfigureras med hjälp av e-postprofiler i Microsoft Intune.  

Du kan använda e-postprofiler för att konfigurera den interna e-postklienten på följande enhetstyper:
-   Windows Phone 8 och senare
-   Windows 10 (för datorer), Windows 10 Mobile, och senare
-   iOS 7.1 och senare
-   Samsung KNOX Standard (4.0 och senare)

Förutom att konfigurera ett e-postkonto på enheten kan du ställa in hur många e-postmeddelanden som ska synkroniseras och, beroende på enhetstypen, vilka innehållstyper som ska synkroniseras.
>[!NOTE]
>
>Om användaren har installerat en e-postprofil innan en profil skapas av Intune, beror resultatet av e-postprofildistributionen i Intune på enhetsplattformen:

[kommentar]: <> Passiv konstruktion är nödvändig i de följande tre styckena tills processen med dubblettidentifiering har klargjorts av PM.

>**iOS**: En befintlig duplicerad e-postprofil identifieras baserat på värdnamn och e-postadress. Den duplicerade e-postprofilen som skapats av användaren blockerar distributionen av en profil som skapats av Intune-administratören. Det här är ett vanligt problem eftersom iOS-användare vanligtvis skapar en e-postprofil och sedan gör registreringen. Företagsportalen meddelar användarna att de inte är kompatibla på grund av deras manuellt konfigurerade e-postprofil och uppmanar dem att ta bort profilen. Användarna bör ta bort e-postprofilen så att Intune-profilen kan konfigureras. För att förhindra det här problemet ber du användarna att göra registreringen före installation av en e-postprofil så att Intune kan konfigurera profilen.

>**Windows**: En befintlig duplicerad e-postprofil identifieras baserat på värdnamn och e-postadress. Intune skriver över den befintliga e-postprofilen som skapats av användaren.

>**Samsung KNOX**: En befintlig duplicerad e-postprofil identifieras baserat på e-postadressen, och den skrivs över med Intune-profilen. Om användaren konfigurerar det kontot skrivs det över igen av Intune-profilen. Observera att detta kan orsaka förvirring för användaren.

>Samsung KNOX använder inte värdnamn för att identifiera profilen. Därför rekommenderar vi att du inte skapar flera e-postprofiler för samma e-postadress på olika värdar, eftersom de kommer att skriva över varandra.


## Skydda e-postprofiler
Du kan skydda e-postprofiler på två sätt: antingen med ett certifikat eller med ett lösenord.

### Certifikat
När du skapar en e-postprofil väljer du en certifikatprofil som du har skapat tidigare i Intune. Detta kallas identitetscertifikat och används för att autentisera mot en betrodd certifikatprofil (eller ett rotcertifikat) för att fastställa att användarens enhet får ansluta. Det betrodda certifikatet distribueras till datorn som verifierar e-postanslutningen, vanligtvis den interna e-postservern.

Mer information om hur du skapar och använder certifikatprofiler i Intune finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).

### Användarnamn och lösenord
Användaren autentiseras mot den interna e-postservern genom att ange sitt användarnamn och lösenord.

Lösenordet finns inte i e-postprofilen. Användarna måste ange detta när de ansluter till sin e-post.

### Skapa en e-postprofil

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Lägg till princip**.

2.  Konfigurera en av följande principtyper:

    -   **E-postprofil för Samsung KNOX Standard (4.0 och senare)**

    -   **E-postprofil (iOS 7.1 och senare)**

    -   **E-postprofil (Windows Phone 8 och senare)**

    -   **E-postprofil (Windows 10 Desktop och Mobile och senare)**

    Du kan bara skapa och distribuera en princip för anpassad e-postprofil. Rekommenderade inställningar är inte tillgängliga.

3.  Ta hjälp av följande tabell när du konfigurerar inställningar för en e-postprofil:

|Inställningsnamn | Mer information|
| ----------- | --------------- |
    |**Namn**|Unikt namn för e-postprofilen.|
    |**Beskrivning**|En beskrivning som hjälper dig att identifiera den här profilen.|
    |**Värd**|Värdnamnet för företagsservern som är värd för den interna e-posttjänsten.|
    |**Kontonamn**|Visningsnamnet för e-postkontot som kommer att visas på användarnas enheter.|
    |**Användarnamn**|Hur användarnamn för e-postkontot hämtas. Välj **Användarnamn** för en lokal Exchange-server eller välj **UPN (User Principal Name)** för Office 365.|
    |**E-postadress**|Hur e-postadressen för användaren på varje enhet genereras. Välj **Primär SMTP-adress** om du vill använda den primära SMTP-adressen för att logga in på Exchange eller använd **UPN (User Principal Name)** om du vill använda det fullständiga huvudnamnet som e-postadress.|
    |**Autentiseringsmetod** (Samsung KNOX och iOS)|Välj antingen **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som används av e-postprofilen.|
    |**Välj ett certifikat för klientautentisering (identitetscertifikat)** (Samsung KNOX och iOS)|Välj SCEP klientcertifikatet som du skapade tidigare som ska användas för att autentisera Exchange-anslutningen. Mer information om hur du använder certifikatprofiler i Intune finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md). Det här alternativet visas endast när autentiseringsmetoden är **Certifikat**.|
    |**Använd S/MIME** (Samsung KNOX och iOS)|Skicka utgående e-post med S/MIME-kryptering.|
    |**Signeringscertifikat** (Samsung KNOX och iOS)|Välj signeringscertifikatet som ska användas för att signera utgående e-post. Det här alternativet visas bara om du väljer **Använd S/MIME**.|
    |**Antal dagars e-postmeddelande att synkronisera**|Ange hur många dagar e-post ska synkroniseras eller välj **Obegränsad** om du vill synkronisera alla tillgängliga e-postmeddelanden.|
    |**Synkroniseringsschema** (Samsung KNOX, Windows Phone 8 och senare, Windows 10)|Välj det schema som ska användas av enheterna som ska synkronisera data från Exchange-servern. Du kan även välja **Efter hand som meddelanden kommer** varvid data synkroniseras när de anländer eller **Manuell** där enhetens användare måste starta synkroniseringen.|
    |**Använd SSL**|Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern. För enheter som kör Samsung KNOX 4.0 eller senare kan du exportera Exchange-serverns SSL-certifikat och distribuera det som en Android-betrodd certifikatprofil i Intune. Intune stöder inte åtkomst till det här certifikatet om det installeras på Exchange-servern på annat sätt.|
    |**Innehållstyp som ska synkroniseras**|Välj vilka typer av innehåll du vill synkronisera till enheterna.|
    |**Tillåt att e-post skickas från tredjepartsprogram** (endast iOS)|Tillåt att användaren väljer den här profilen som standardkonto för att skicka e-post och att appar från andra leverantörer öppnar e-post i den interna e-postappen, till exempel för att bifoga filer i e-postmeddelanden.|
    > [!IMPORTANT]
    > If you have deployed an email profile and then wish to change the values for **host** or **Email address**, you must delete the existing email profile and create a new one with the required values.

4.  När du är klar klickar du på **Spara profilen**.

Ny princip som visas i noden **Konfigurationsprinciper** i arbetsytan **Principer** .

## Distribuera principen

1.  På arbetsytan **Princip** markerar du den princip som du vill distribuera och väljer sedan **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** :

    -   **Om du vill distribuera principen** – Välj en eller flera grupper som du vill distribuera principen till. Välj sedan **Lägg till** &gt; **OK**.

    -   **Om du vill stänga dialogrutan utan att distribuera den** – Välj **Avbryt**.

En statssammanfattning och varningar på sidan **Översikt** på arbetsytan **Principer** identifierar problem med principer som kräver din uppmärksamhet. Dessutom visas en statussammanfattning på arbetsytan Instrumentpanel.

> [!NOTE]
> Om du vill ta bort en e-postprofil från en enhet, redigera distributionen och ta bort alla grupper där enheten är medlem.



<!--HONumber=Aug16_HO3-->


