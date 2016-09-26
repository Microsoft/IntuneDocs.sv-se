---
title: "Använda konfigurationsprinciper för iOS-mobilappar | Microsoft Intune"
description: "Använd konfigurationsprinciper för mobilappar i Intune om du vill definiera inställningar som kan krävas när användaren kör en iOS-app."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 360865bcd97230e264ee3439407e8dd3017d0055
ms.openlocfilehash: 1f239270c26a70b161e52c24e94ca5c2cae9ca3a


---

# Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune
Använd konfigurationsprinciper för mobilappar i Microsoft Intune om du vill definiera inställningar som kan krävas när användaren kör en app. En app kan till exempel kräva att användarna anger:

-   ett anpassat portnummer

-   språkinställningar

-   säkerhetsinställningar

-   anpassade inställningar, t.ex. en företagslogotyp.

Om användarna inte anger dessa inställningar på korrekt sätt kan det öka supportens arbetsbörda och ta längre tid att börja använda nya appar.

Med konfigurationsprinciper för mobilappar slipper du den här typen av problem eftersom du kan distribuera dessa inställningar till användarna i en princip innan de kör appen. Inställningarna distribueras sedan automatiskt utan att användarna behöver göra något.

Du distribuerar inte principerna direkt till användare och enheter. I stället associerar du principen med en app och distribuerar sedan appen. Principinställningarna används när appen söker efter dem (oftast första gången den körs.).

> [!TIP]
> Den här principen är för närvarande endast tillgänglig för enheter som kör iOS 8.0 och senare. Den stöder följande appinstallationstyper:
>
> -   **Hanterade iOS-appar från App Store**
> -   **App-paket för iOS**
>
> Mer information om appinstallationstyper finns i [Distribuera appar med Microsoft Intune](deploy-apps.md).

## Konfigurera en konfigurationsprincip för mobilappar

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Översikt** &gt; **Lägg till princip**.

2.  Expandera **iOS**i listan med principer, välj **Konfiguration av mobilapp**och välj sedan **Skapa princip**.

    > [!TIP]
    > Du kan bara konfigurera anpassade inställningar för den här principtypen. Rekommenderade inställningar är inte tillgängliga.

3.  Ange ett namn och en valfri beskrivning av konfigurationsprincipen för mobilappen under **Allmänt** på sidan **Skapa princip** .

4.  Skriv eller klistra in en XML-egenskapslista med de appkonfigurationsinställningar som du vill använda i rutan i avsnittet **Konfigurationsprincip för mobilapp** på sidan. Formatet på XML-egenskapslistan varierar beroende på vilken app du konfigurerar. Kontakta appleverantören för information om vilket format du ska använda.

    > [!TIP]
    > Mer information om XML-egenskapslistor finns i [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) i iOS Developer Library.

5.  Bekräfta att XML-egenskapslistan som du angav har ett giltigt format genom att klicka på **Validera** .

    > [!IMPORTANT]
    > När du klickar på **Validera** kontrollerar Intune att XML-egenskapslistan som du angett har rätt format. Intune kontrollerar inte om XML-egenskapslistan fungerar med den app som den är associerad med.

6.  När du är klar klickar du på **Spara princip**.

Den nya principen visas i noden **Konfigurationsprinciper** .

## Information om XML-filformatet

Intune har stöd för följande datatyper i en egenskapslista:
    
- &lt;heltal&gt;
- &lt;verklig&gt;
- &lt;sträng&gt;
- &lt;matris&gt;
- &lt;dict&gt;
- &lt;sant /&gt; eller &lt;falskt /&gt;
     
Mer information om datatyper finns i [About Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) i iOS Developer Library.

Dessutom stöder Intune följande typer av token i egenskapslistan:
- \{\{userprincipalname\}\} – (Exempel: **Johan@contoso.com**)
- \{\{mail\}\} – (Exempel: **Johan@contoso.com**)
- \{\{partialupn\}\} – (Exempel: **Johan**)
- \{\{accountid\}\} – (Exempel: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{deviceid\}\} – (Exempel: **b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{userid\}\} – (Exempel: **3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{username\}\} – (Exempel: **Johan Danielsson**)
- \{\{serialnumber\}\} - (Exempel: **F4KN99ZUG5V2**) för iOS-enheter
- \{\{serialnumberlast4digits\}\} - (Exempel: **G5V2**) för iOS-enheter
    
Tecknen \{\{ och \}\} används endast av tokentyper och får inte användas för andra ändamål.

## Associera en konfigurationsprincip för mobilappar med en app
När du har skapat en konfigurationsprincip för mobilappar måste du associera den med den iOS-app som du vill att inställningarna i konfigurationsprincipen ska gälla för.

Det gör du genom att följa stegen för att skapa en appdistribution i [Lägg till appar för mobila enheter i Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) och [Distribuera appar med Microsoft Intune](deploy-apps-in-microsoft-intune.md). När du kommer till sidan **Konfiguration av mobilapp** i guiden väljer du den princip som du vill associera med appen i listrutan **Appkonfigurationsprincip**.

Fortsätt sedan att distribuera och övervaka appdistributionen som vanligt.

När den distribuerade appen körs på en enhet körs den med de inställningar som du konfigurerade i konfigurationsprincipen för mobilappar.

> [!TIP]
> Om en eller flera konfigurationsprinciper för mobilappar är i konflikt med varandra tillämpas ingen av dem. Konflikten rapporteras på **instrumentpanelen** i Intune-administratörskonsolen.

## Exempelformat för XML-filen för en mobilappskonfiguration

När du skapar en konfigurationsfil för mobilappar kan du ange en eller flera av följande värden med hjälp av det här formatet:

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>

```



<!--HONumber=Sep16_HO3-->


