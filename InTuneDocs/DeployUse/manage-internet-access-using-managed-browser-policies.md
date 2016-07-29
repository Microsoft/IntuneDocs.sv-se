---
title: "Hantera webbåtkomst med den hanterade webbläsaren | Microsoft Intune"
description: "Distribuera den hanterade webbläsaren för att begränsa surfning och överföring av webbdata till andra appar."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: maxles
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6716a3d1fb53dc3de0189f637d5664d0a2023d05
ms.openlocfilehash: 44f6ee1354f1fdfc7f8db7d5b844dc12c01e686c


---

# Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune
Den hanterade webbläsaren är ett webbläsningsprogram som med hjälp av Microsoft Intune kan distribueras i organisationen. En princip för hanterad webbläsare konfigurerar en lista över tillåtna eller blockerade webbplatser som begränsar vilka webbplatser användare av den hanterade webbläsaren kan besöka.

Eftersom den här appen är en hanterad app, kan även hanteringsprinciper för mobilprogram tillämpas på appen, till exempel hur användningen av klipp ut, kopiera och klistra in kontrolleras, hindra skärmdumpar och även säkerställa att länkar till innehåll som användare klickar på endast öppnas i andra hanterade appar. Mer information finns i avsnittet [Konfigurera och distribuera hanteringsprinciper för mobilprogram i konsolen för Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> [!IMPORTANT]
>Om användare installerar den hanterade webbläsaren från app store och de inte hanteras av Intune gäller följande: iOS – Den hanterade webbläsarappen kan användas som en vanlig webbläsare, men vissa funktioner är inte tillgängliga, och den kan inte komma åt data från andra Intune-hanterade appar.
Android – Den hanterade webbläsaren kan inte användas.
Om användaren själv installerar den hanterade webbläsaren på en iOS-enhet med en version som är mindre än iOS 9, hanteras den inte av de principer som du skapar. För att säkerställa att webbläsaren hanteras av Intune, måste användarna avinstallera appen innan du kan distribuera den till dem som en hanterad app. Om användarna själva installerar den hanterade webbläsaren i iOS 9 och senare uppmanas de att tillåta att den hanteras av principer.

Du kan skapa principer för hanterade webbläsare för följande enhetstyper:

-   Enheter som kör Android 4 och senare

-   Enheter som kör iOS 7.1 och senare

Intune Managed Browser stöder öppning av webbinnehåll från [Microsoft Intune-programpartner](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

## Skapa en princip för hanterad webbläsare

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) klickar du på **Princip** &gt; **Lägg till princip**.

2.  Konfigurera en av följande typer av **programvaru** princip:

    -   **Princip för hanterad webbläsare (Android 4 och senare)**

    -   **Princip för hanterad webbläsare (iOS 7.1 och senare)**

    Mer information om hur du skapar och distribuerar principer finns i avsnittet [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Använd följande tabell för att konfigurera inställningarna för en princip för hanterad webbläsare:

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för principen för den hanterade webbläsaren som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en lämplig beskrivning av principen och annan information som gör det enkelt att hitta den.|
    |**Aktivera en lista över tillåtna eller blockerade webbplatser för att begränsa URL:er som den hanterade webbläsaren kan öppna**|Välj något av följande alternativ:<br /><br />**Låt Managed Browser enbart öppna de URL:er som listas nedan ** – ange en lista över URL:er som kan öppnas i den hanterade webbläsaren.<br /><br />**Blockera Managed Browser från att öppna de URL:er som listas nedan ** – ange en lista över URL:er som inte kan öppnas och som blockeras i den hanterade webbläsaren. **Obs!** Både tillåtna och blockerade URL:er kan inte ingå i samma princip för den hanterade webbläsaren.<br />Mer information om de URL-format som du kan ange finns i **URL-format för tillåtna och blockerade URL:er** i det här avsnittet.|

4.  När du är klar klickar du på **Spara profilen**.

Ny princip som visas i noden **Konfigurationsprinciper** i arbetsytan **Principer** .

## Skapa en distribution för den hanterade webbläsarappen
När du har skapat principen för den hanterade webbläsaren kan du skapa en programdistribution för den hanterade webbläsarappen och associera det med principen som du skapade.

> [!IMPORTANT]
> Principer för hanterade webbläsare distribueras inte på samma sätt som andra Intune-principer. Den här typen av princip måste associeras med programvarupaketet för den hanterade webbläsaren.

Distribuera appen och se till att du väljer principen för den hanterade webbläsaren på sidan **Mobile App Management** för att associera principen med appen.

Mer information om hur du distribuerar appar finns i [Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).

## Säkerhet och sekretess för hanterade webbläsare

-   Webbplatser som har ett utgånget eller ej betrott certifikat kan inte öppnas på iOS-enheter.

-   Inställningar som användare gör för den inbyggda webbläsaren på sina enheter används inte av den hanterade webbläsaren. Det här beror på att den hanterade webbläsaren inte har tillgång till de här inställningarna.

-   Om du konfigurerar alternativen **Kräv enkel PIN-kod för åtkomst** eller **Kräv företagets autentiseringsuppgifter för åtkomst** i en hanteringsprincip för mobilprogram som är associerad med den hanterade webbläsaren och en användare klickar på hjälplänken på autentiseringssidan kan användaren bläddra i alla webbplatser, oavsett om de har lagts till i en blockeringslista i principen för hanterade webbläsare.

-   Den hanterade webbläsaren kan endast blockera åtkomst till webbplatser när de används direkt. Den kan inte blockera åtkomst när mellanliggande tjänster (till exempel en översättningstjänst) används för åtkomst till webbplatsen.

-   För att tillåta autentisering och säkerställa att Intune-dokumentationen kan nås är **&#42;.microsoft.com** undantaget från listan Tillåt eller blockera – den tillåts alltid.

### Stäng av användningsdata
Microsoft samlar automatiskt in anonyma data om prestanda och användningen av den hanterade webbläsaren för att förbättra sina produkter och tjänster. Användarna kan dock inaktivera datainsamlingen med hjälp av inställningen **Användningsdata** på deras enheter. Du har ingen kontroll över insamlingen av dessa data.

## Referensinformation

### URL-format för tillåtna och blockerade URL:er
Använd följande information för att lära dig om tillåtna format och jokertecken som du kan använda när du anger URL:er i listorna för tillåtna och blockerade webbplatser.

-   Du kan använda jokertecknet **&#42;** enligt reglerna i listan med tillåtna mönster nedan.

-   Kontrollera att du lägger till prefixet **http** eller **https** till alla URL:er när du lägger till dem i listan.

-   Du kan ange portnummer i adressen. Om du inte anger ett portnummer, används följande värden:

    -   Port 80 för http

    -   Port 443 för http

    Jokertecken i portnummer stöds inte, till exempel **http&colon;//www&period;contoso&period;com:*;** och **http&colon;//www&period;contoso&period;com: /*;**

-   Lär dig mer om de tillåtna mönster du kan använda när du anger URL:er med hjälp av följande tabell:

|URL|Information|Matchar|Matchar inte|
    |-------|---------------|-----------|------------------|
    |http://www.contoso.com|Matchar en enstaka sida|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
    |http://contoso.com|Matchar en enstaka sida|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
    |http://www.contoso.com/&#42;|Matchar alla URL:er som börjar med www.contoso.com|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
    |http://&#42;.contoso.com/&#42;|Matchar alla underordnade domäner under contoso.com|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos|contoso.host.com|
    |http://www.contoso.com/images|Matchar en enstaka mapp|www.contoso.com/images|www.contoso.com/images/dogs|
    |http://www.contoso.com:80|Matchar en enstaka sida, med ett portnummer|http://www.contoso.com:80||
    |https://www.contoso.com|Matchar en enstaka, säker sida|https://www.contoso.com|http://www.contoso.com|
    |http://www.contoso.com/images/&#42;|Matchar en enstaka mapp och alla undermappar|www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats|www.contoso.com/videos|

-   Följande är några exempel på indata som du inte kan ange:

    -   &#42;.com

    -   &#42;.contoso/&#42;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   IP-adresser

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com:&#42;

    -   http://www.contoso.com: /&#42;

### Hur konflikter löses mellan en lista över tillåtna och en lista över blockerade webbplatser
Om flera principer för hanterade webbläsare har distribuerats till en enhet och det finns en konflikt mellan inställningarna, utvärderas både läget (tillåt eller blockera) och URL-listorna för konflikter. Om en konflikt uppstår, gäller följande:

-   Om läget i varje princip är samma men URL-listorna skiljer sig tillämpas URL:erna inte på enheten.

-   Om läget i varje princip skiljer sig men URL-listorna är samma tillämpas URL:erna inte på enheten.

-   Om en enhet tar emot principer för hanterade webbläsare för första gången och det uppstår en konflikt mellan två principer, tillämpas URL:erna inte på enheten. Använd noden **Principkonflikter** under arbetsytan **Princip** om du vill visa konflikterna.

-   Om en enhet redan har tagit emot en princip för hanterad webbläsare och en andra princip används med motstridiga inställningar, förblir de ursprungliga inställningarna på enheten. Använd noden **Principkonflikter** under arbetsytan **Princip** om du vill visa konflikterna.



<!--HONumber=Jul16_HO4-->


