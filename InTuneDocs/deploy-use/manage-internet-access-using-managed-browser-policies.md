---
title: "Hantera webbåtkomst med den hanterade webbläsaren | Microsoft Docs"
description: "Distribuera den hanterade webbläsaren för att begränsa surfning och överföring av webbdata till andra appar."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 90222b10832fd8251ad897348eeebed5b3d1e552
ms.openlocfilehash: 49ad005846265deb7d4b34b52a1c139e8f61372b
ms.contentlocale: sv-se
ms.lasthandoff: 05/11/2017


---

# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Den hanterade webbläsaren är ett webbläsningsprogram som med hjälp av Microsoft Intune kan distribueras i organisationen. En princip för hanterad webbläsare konfigurerar en lista över tillåtna eller blockerade webbplatser som begränsar vilka webbplatser användare av den hanterade webbläsaren kan besöka.

Eftersom den här appen har integrering med Intune SDK kan du också använda appskyddsprinciper för den. De här principerna kan omfatta att kontrollera användningen av klipp ut, kopiera och klistra in, hindra skärmdumpar och säkerställa att länkar till innehåll som användare väljer endast öppnas i andra hanterade appar. Mer information finns i avsnittet [Konfigurera och distribuera hanteringsprinciper för mobilprogram i konsolen för Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

>[!IMPORTANT]
>Managed Browser-appen hämtar och använder Intunes appskyddsprinciper enbart när en annan app på enheten har hämtat en appskyddsprincip.<br><br> Om användarna installerar den hanterade webbläsaren från App Store och Intune inte hanterar den, gäller dessutom följande:<br /><br />
>**iOS** – Den hanterade webbläsarappen kan användas som en grundläggande webbläsare, men vissa funktioner är inte tillgängliga och den kan inte komma åt data från andra Intune-hanterade appar.<br />
**Android** – Den hanterade webbläsarappen kan inte användas.<br /><br />
Om användaren själv installerar den hanterade webbläsaren på en iOS-enhet med en tidigare version än iOS 9 hanterar inga principer som du skapar webbläsaren. För att säkerställa att Intune hanterar webbläsaren måste användarna avinstallera appen innan du kan distribuera den till dem som en hanterad app. Om användarna själva installerar den hanterade webbläsaren i iOS 9 och senare uppmanas de att tillåta att den hanteras av principer.

Du kan skapa principer för hanterade webbläsare för följande enhetstyper:

-   Enheter som kör Android 4 och senare

-   Enheter som kör iOS 8.0 och senare

Intune Managed Browser stöder öppning av webbinnehåll från [Microsoft Intune-programpartner](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx).

## <a name="create-a-managed-browser-policy"></a>Skapa en princip för hanterad webbläsare

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Lägg till princip**.

2.  Konfigurera en av följande typer av **programvaru** princip:

    -   **Hanterad webbläsare (Android 4 och senare)**

    -   **Managed Browser (iOS 8.0 och senare)**

    Mer information om hur du skapar och distribuerar principer finns i avsnittet [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Använd följande för att konfigurera inställningarna för en princip för hanterad webbläsare:

    - **Namn**. Ange ett unikt namn för principen för den hanterade webbläsaren som hjälper dig att identifiera den i Intune-konsolen.
    - **Beskrivning**. Ange en lämplig beskrivning av principen och annan information som gör det enkelt att hitta den.
    - **Aktivera en lista över tillåtna eller blockerade webbplatser för att begränsa URL:er som den hanterade webbläsaren kan öppna**. Välj något av följande alternativ:
        - **Låt den hanterade webbläsaren endast öppna webbadresserna nedan**. Ange en lista över webbadresser som den hanterade webbläsaren kan öppna.
        - **Blockera den hanterade webbläsaren från att öppna webbadresserna nedan**. Ange en lista över webbadresser som den hanterade webbläsaren blockeras från att öppna.
**Obs!** Både tillåtna och blockerade URL:er kan inte ingå i samma princip för den hanterade webbläsaren.
Mer information om de URL-format som du kan ange finns i **URL-format för tillåtna och blockerade URL:er** i det här avsnittet.

4.  När du är klar väljer du **Spara princip**.

Den nya principen visas i noden **Konfigurationsprinciper** på arbetsytan **Principer** .

## <a name="create-a-deployment-for-the-managed-browser-app"></a>Skapa en distribution för den hanterade webbläsarappen
När du har skapat principen för den hanterade webbläsaren kan du skapa en programdistribution för den hanterade webbläsarappen och associera den med principen som du skapade.

> [!IMPORTANT]
> Principer för hanterade webbläsare distribueras inte på samma sätt som andra Intune-principer. Den här typen av princip måste associeras med programvarupaketet för den hanterade webbläsaren.

Distribuera appen och se till att du väljer principen för den hanterade webbläsaren på sidan **Mobile App Management** för att associera principen med appen.

Mer information om hur du distribuerar appar finns i [Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).

## <a name="security-and-privacy-for-the-managed-browser"></a>Säkerhet och sekretess för hanterade webbläsare

-   Webbplatser som har ett utgånget eller ej betrott certifikat kan inte öppnas på iOS-enheter.

-   Den hanterade webbläsaren använder inte inställningar som användare gör för den inbyggda webbläsaren på sina enheter. Det här beror på att den hanterade webbläsaren inte har tillgång till de här inställningarna.

-   Om du konfigurerar alternativet **Kräv enkel PIN-kod för åtkomst** eller **Kräv företagets autentiseringsuppgifter för åtkomst** i en hanteringsprincip för mobilprogram som är associerad med den hanterade webbläsaren och en användare väljer hjälplänken på autentiseringssidan kan användaren bläddra på alla webbplatser, oavsett om de har lagts till i en blockeringslista i principen för hanterade webbläsare.

-   Den hanterade webbläsaren kan endast blockera åtkomst till webbplatser när de öppnas direkt. Den kan inte blockera åtkomst när mellanliggande tjänster (till exempel en översättningstjänst) används för åtkomst till webbplatsen.

-   För att tillåta autentisering och säkerställa att Intune-dokumentationen kan nås är **&#42;.microsoft.com** undantaget från listan Tillåt eller blockera. Den tillåts alltid.

### <a name="turn-off-usage-data"></a>Stäng av användningsdata
Microsoft samlar automatiskt in anonymiserade data om prestanda och användning av den hanterade webbläsaren för att kunna förbättra Microsofts produkter och tjänster. Användare kan stänga av insamling av data med hjälp av inställningen **Användningsdata** på sina enheter. Du har ingen kontroll över insamlingen av dessa data.

## <a name="reference-information"></a>Referensinformation

### <a name="url-format-for-allowed-and-blocked-urls"></a>URL-format för tillåtna och blockerade URL:er
Använd följande information för att lära dig om tillåtna format och jokertecken som du kan använda när du anger URL:er i listorna för tillåtna och blockerade webbplatser:

-   Du kan använda jokertecknet (**&#42;**) enligt reglerna i följande lista med tillåtna mönster.

-   Kontrollera att du lägger till prefixet **http** eller **https** till alla URL:er när du lägger till dem i listan.

-   Du kan ange portnummer i adressen. Om du inte anger ett portnummer, används följande värden:

    -   Port 80 för http

    -   Port 443 för http

    Jokertecken i portnummer stöds inte. Till exempel stöds inte **http&colon;//www&period;contoso&period;com:*;** och **http&colon;//www&period;contoso&period;com: /*;**.

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

### <a name="how-conflicts-between-the-allow-and-block-list-are-resolved"></a>Hur konflikter löses mellan en lista över tillåtna och en lista över blockerade webbplatser
Om flera principer för hanterade webbläsare har distribuerats till en enhet och det finns en konflikt mellan inställningarna, utvärderas både läget (tillåt eller blockera) och URL-listorna för konflikter. Om en konflikt uppstår, gäller följande:

-   Om läget i varje princip är samma men URL-listorna skiljer sig tillämpas URL:erna inte på enheten.

-   Om läget i varje princip skiljer sig men URL-listorna är samma tillämpas URL:erna inte på enheten.

-   Om en enhet tar emot principer för hanterade webbläsare för första gången och det uppstår en konflikt mellan två principer, tillämpas URL:erna inte på enheten. Använd noden **Principkonflikter** under arbetsytan **Princip** om du vill visa konflikterna.

-   Om en enhet redan har tagit emot en princip för hanterad webbläsare och en andra princip används med motstridiga inställningar, förblir de ursprungliga inställningarna på enheten. Använd noden **Principkonflikter** under arbetsytan **Princip** om du vill visa konflikterna.

