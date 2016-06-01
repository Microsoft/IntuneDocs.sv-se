---
# required metadata

title: Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune
Använd konfigurationsprinciper för mobilappar i Microsoft Intune om du vill definiera inställningar som kan krävas när användaren kör en app. En app kan till exempel kräva att användaren anger:

-   Ett anpassat portnummer när den körs

-   Språkinställningar

-   Säkerhetsinställningar

-   Anpassade inställningar, t.ex. en företagslogotyp

Om dessa inställningar inte anges korrekt av användaren kan det öka supportens arbetsbörda och försena anpassningen av nya appar.

Med konfigurationsprinciper för mobilappar slipper du den här typen av problem eftersom du kan distribuera dessa inställningar till användarna i en princip innan de kör appen. Inställningarna distribueras sedan automatiskt utan att användaren behöver göra något.

Du distribuerar inte principerna direkt till användare och enheter. I stället associerar du principen med en app och distribuerar sedan appen. Principinställningarna används när appen söker efter dem (oftast första gången den körs.).

> [!TIP]
> Den här principtypen är för närvarande bara tillgänglig för enheter som kör iOS 7.1 och senare och stöder följande typer av appinstallationer:
> 
> -   **Hanterade iOS-appar från App Store**
> -   **App-paket för iOS**
> 
> Mer information om appinstallationstyper finns i [Distribuera appar med Microsoft Intune](deploy-apps.md)..

## Konfigurera en konfigurationsprincip för mobilappar

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Översikt** &gt; **Lägg till princip**.

2.  Expandera **iOS** i listan med principer, klicka på **Konfiguration av mobilapp**och klicka sedan på **Skapa princip**.

    > [!TIP]
    > Du kan bara konfigurera anpassade inställningar för den här principtypen. Rekommenderade inställningar är inte tillgängliga.

3.  Ange ett namn och en valfri beskrivning av konfigurationsprincipen för mobilappen i ämnet **Allmänt** på sidan **Skapa princip** .

4.  Skriv eller klistra in en XML-egenskapslista med de appkonfigurationsinställningar som du vill använda i rutan i ämnet **Konfigurationsprincip för mobilapp** på sidan.

    > [!TIP]
    > Mer information om XML-egenskapslistor finns i [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) i iOS Developer Library.
    > 
    > Formatet på XML-egenskapslistan varierar beroende på vilken app du konfigurerar. Kontakta appleverantören för information om vilket format du ska använda.
    > 
    > Intune har stöd för följande datatyper i en egenskapslista:
    > 
    > &lt;heltal&gt;
    > &lt;verklig&gt;
    > &lt;sträng&gt;
    > &lt;matris&gt;
    > &lt;dict&gt;
    > &lt;sant /&gt; eller &lt;falskt /&gt;
    > 
    > Mer information om datatyper finns i [About Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) i iOS Developer Library.
    >
        > Dessutom stöder Intune följande typer av token i egenskapslistan:
    >    
    > \{\{userprincipalname\}\} – (Exempel: **Johan@contoso.com**)
    > \{\{mail\}\} – (Exempel: **Johan@contoso.com**)
    > \{\{partialupn\}\} – (Exempel: **Johan**)
    > \{\{accountid\}\} – (Exempel: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
    > \{\{deviceid\}\} – (Exempel: **b9841cd9-9843-405f-be28-b2265c59ef97**)
    > \{\{userid\}\} – (Exempel: **3ec2c00f-b125-4519-acf0-302ac3761822**)
    > \{\{username\}\} – (Exempel: **Johan Danielsson**)
    > \{\{serialnumber\}\} - (Exempel: **F4KN99ZUG5V2**) för iOS-enheter
    > \{\{serialnumberlast4digits\}\} - (Exempel: **G5V2**) för iOS-enheter
>
> Tecknen \{\{ och \}\} används endast av tokentyper och får inte användas för andra ändamål.




5.  Bekräfta att XML-egenskapslistan som du angav har giltigt format genom att klicka på **Validera** .

    > [!IMPORTANT]
    > När du klickar på **Validera** kontrollerar Intune att XML-egenskapslistan som du angett har rätt format. Den kontrollerar inte om XML-egenskapslistan fungerar med den app som den är associerad med.

6.  När du är klar klickar du på **Spara princip**.

Den nya principen visas i noden **Konfigurationsprinciper** .

## Associera en konfigurationsprincip för mobilappar med en app
När du har skapat en konfigurationsprincip för mobilappar måste du associera den med den iOS-app som du vill att inställningarna i konfigurationsprincipen ska gälla för.

Det gör du genom att följa stegen för att skapa en appdistribution i [Lägg till appar för mobila enheter i Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) och [Distribuera appar med Microsoft Intune](deploy-apps-in-microsoft-intune.md). När du kommer till sidan **Konfiguration av mobilapp** i guiden väljer du den princip som du vill associera med appen i listrutan **Appkonfigurationsprincip**.

Fortsätt sedan att distribuera och övervaka appdistributionen som vanligt.

När den distribuerade appen körs på en enhet körs den med de inställningar som du konfigurerade i konfigurationsprincipen för mobilappar.

> [!TIP]
> Om en eller flera konfigurationsprinciper för mobilappar är i konflikt med varandra tillämpas ingen av dem och konflikten rapporteras på **instrumentpanelen** i Intune-administrationskonsolen.

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




<!--HONumber=May16_HO1-->


