---
title: "Inställningar för Mac OS X-principer | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 8c1f4f209c5ec704290882b8f6f71e0b1b01d21c
ms.openlocfilehash: bbbb666fdc34a82d247d760d156d48c5ac72374c


---

# Inställningar för Mac OS X-konfigurationsprinciper i Microsoft Intune

## Generella inställningar för konfigurationsprinciper

Använd Microsoft Intunes **allmänna konfigurationsprincip** för Mac OS X om du vill konfigurera inställningar för:

-   **Enhetssäkerhet** – Välj i en lista med fördefinierade inställningar som du kan använda för att styra många av enhetens egenskaper och funktioner.

-   **Kompatibla och inkompatibla appar** – Ange en lista över appar i företaget som är kompatibla eller inkompatibla. Inkompatibilitetsrapporter för appar kan användas för att visa om de appar du har angett i listan är kompatibla med appar som användare har installerat (men det går inte att blockera installationen av programmet).

Om den inställning som du söker efter inte visas i listan kan du skapa den med hjälp av en anpassad Mac OS X-princip med vilken du kan importera inställningar som du har skapat med hjälp av Apple Configurator-verktyget. Mer information finns i **Anpassade principinställningar** senare i det här avsnittet.

### Inställningar för lösenord

|Inställningsnamn|Information|
|----------------|---------------|
|**Kräv ett lösenord för att låsa upp enheter**|Anger om användaren måste använda ett lösenord för att komma åt Mac-datorn. **Viktigt!** Till skillnad från iOS-enheter uppmanas användare på Mac OS X-enheter inte genast att uppdatera sitt lösenord för att följa den här inställningen.|
|**Lösenordstyp krävs**|Anger om lösenordet som används kan vara endast numeriskt eller om det måste vara **Alfanumeriskt** (innehålla bokstäver och siffror). **Viktigt!** Den här inställningen stöds endast i Mac OS X version 10.10.3 och senare.|
|**Antal avancerade tecken som krävs i lösenord**|Anger det antal avancerade tecken som krävs i lösenordet (från **0** - **4**).<br /><br />Ett avancerat tecken är en symbol som "**?**"|
|**Minsta längd på lösenord**|Anger minimilängden för lösenordet (mellan **4** och **14** tecken).|
|**Tillåt enkla lösenord**|Låter användarna skapa enkla lösenord som "**0000**" eller "**1234**".|
|**Antal minuters inaktivitet innan lösenord krävs**|Anger hur länge datorn måste vara inaktiv innan ett lösenord krävs för att låsa upp den.|
|**Lösenordets giltighetstid (i dagar)**|Anger efter hur många dagar användaren måste byta lösenord (från **1** - **255** dagar).|
|**Kom ihåg tidigare lösenord**|Den här inställningen används för att förhindra att användaren använder ett lösenord som har använts tidigare. När den här inställningen används kan du även konfigurera **Förhindra återanvändning av tidigare lösenord** om du vill ange ett antal tidigare lösenord som inte får återanvändas (från **1** - **24**).|
|**Minuter av inaktivitet innan skärmsläckaren aktiveras**|Anger hur länge datorn måste vara inaktiv innan skärmsläckaren aktiveras.|

### Inställningar för kompatibla och icke-kompatibla appar
I listan **Kompatibla &amp; inkompatibla appar för Mac OS X** aktiverar du **Hanterade inställningar för enheter** och skapar sedan en lista över kompatibla eller inkompatibla appar med hjälp av följande information:

> [!NOTE]
> En enda princip kan bara innehålla en lista över kompatibla eller en lista över inkompatibel appar. Du kan inte ange båda i samma princip.
> 
> Intune gör det möjligt att rapportera enheter med inkompatibla appar. Den blockerar inte installation eller tar bort inkompatibla appar.

|Inställningsnamn|Information|
|----------------|---------------|
|**Rapportera inkompatibilitet när användare installerar apparna i listan**|Visar listan med de Mac OS X-appar som användare inte tillåts att installera. Om användarna installerar någon av de här apparna rapporteras de i **Rapporter om ej kompatibla appar**.|
|**Rapportera inkompatibilitet när användare installerar appar som inte är listade**|Visar listan med de Mac OS X-appar som användare tillåts att installera. Om användarna installerar några andra appar rapporteras de i **Rapporter om ej kompatibla appar**.|
|**Lägg till**|Lägger till en app i den markerade listan. Ange ett namn, eventuellt appens utgivare och paket-id för appen. **Tips!** Hitta paket-ID:t för en app på en Mac-dator där appen är installerad:<ol><li>Öppna mappen där appen har installerats (till exempel **/Appar**)</li><li>Välj paketet *&lt;Appnamn&gt;***.app** och välj **Visa paketinnehåll**</li><li>Öppna filen **Info.plist** </li><li>Kontrollera värdet som är associerat med nyckeln **CFBundleIdentifier**</li></ol>Formatet för paket-ID är **com.contoso.appname**|
|**Importera appar**|Importerar en lista med appar som du har angett i en fil med kommaseparerade värden. Använd format, appnamn, utgivare och appaket-ID i filen.|
|**Redigera**|Du kan redigera namn, utgivare och appaket-ID för den valda appen.|
|**Ta bort**|Tar bort den markerade appen från listan.|
> [!TIP]
> Mer information om Intune-rapporter finns i [Förstå Microsoft Intune-aktiviteter med hjälp av rapporter](understand-microsoft-intune-operations-by-using-reports.md).

> [!IMPORTANT]
> När en Mac OS X-enhet är i viloläge kan inte principer och profiler levereras eller inventeras. Därför kan det hända att Intune-konsolen tillfälligt visar statusen **Principinställningar med fel** tills enheten väcks ur viloläge nästa gång.

### Övervaka kompatibla och icke-kompatibla appar
Använd **Rapporter om ej kompatibla appar** för att visa kompatibiliteten för angivna appar.

#### Köra rapport

1.  Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och klicka på **Rapporter** &gt; **Rapporter om ej kompatibla appar**.

2.  Välj de enhetsgrupper du vill kontrollera, om du vill söka efter kompatibla eller icke kompatibla appar och klicka sedan på **Visa rapport**.

## Anpassade principinställningar för Mac OS X i Microsoft Intune
Använd Microsoft Intunes **Mac OS X anpassade konfigurationspolicy** för att distribuera inställningar till Mac OS X-enheter som du skapat med hjälp av [Apple konfigureringsverktyg](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12). Med detta verktyg kan du skapa många inställningar som styr driften av dessa enheter och exportera dem till en konfigurationsprofil. Du kan sedan importera denna konfigurationsprofil till en anpassad princip för Mac OS X i Intune och distribuera inställningarna för användare och enheter i organisationen.

Den här funktionen är avsedd för att distribuera Mac OS X-inställningar som inte kan konfigureras med den allmänna konfigurationsprincipen för Mac OS X i Intune.

### Krav
Innan du börjar, måste du har installerat Apple Configurator och skapat en konfigurationsfil som innehåller de inställningar som du vill distribuera till användare eller enheter. Du kan hämta hem och lära dig om Apple Configurator från [Mac App-butiken](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)

> [!NOTE]
> Intune rapporterar inte uppfyllande av individuella inställningar i en anpassad princip för Mac OS X. Dock rapporteras uppfyllande av principen som helhet.

### Allmänna inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för en anpassad princip för Mac OS X som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en beskrivning som ger en översikt över den anpassade principen för Mac OS X och annan relevant information som hjälper dig att hitta den.|


### Anpassade inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Anpassat konfigurationsprofilsnamn (visas för användare)**|Ange ett namn för principen som den kommer att visas på enheten och i principrapporter för Intune.|
    |**Konfigurationsprofilsfil**|Klicka på **Importera**, bläddra sedan till den konfigurationsprofilen som du skapat med hjälp av Apple Configurator. **Tips!** Se **Så här skapar du en fil för konfigurationsprofil** i det här avsnittet för hjälp med hur du skapar konfigurationsprofilen.|
    |**Information om konfigurationsprofilen**|Visar XML-koden för den konfigurationsprofil du har importerat.|



### Skapa en konfigurationsprofilfil
Du kan skapa filen för konfigurationsprofil som används av den anpassade principen på två sätt:

-   Exportera filen (med tillägget **.mobileconfig**) från Apple-konfigureringsverktyget.

-   Redigera filen själv med lämpligt schema från [Nyckelreferens för Apple-konfigurationsprofil](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).


> [!IMPORTANT]
> När en Mac OS X-enhet är i viloläge kan inte principer och profiler levereras eller inventeras. Därför kan det hända att Intune-konsolen tillfälligt visar statusen **Principinställningar med fel** tills enheten väcks ur viloläge nästa gång.

### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jul16_HO2-->


