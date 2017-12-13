---
title: "Lägg till konfigurationsprinciper för hanterade iOS-mobilappar | Microsoft Docs"
titlesuffix: Azure portal
description: "Lär dig hur du använder appkonfigurationsprinciper för att skicka konfigurationsdata till en iOS-app när den körs."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a39b2d120a804d32b93b7a240af246327514b1b7
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/08/2017
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Lägg till appkonfigurationsprinciper för hanterade iOS-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd appkonfigurationsprinciper i Microsoft Intune för att skicka inställningar när användarna kör en iOS-app. Du tilldelar inte principerna direkt till användare och enheter. I stället associerar du principen med en app och tilldelar sedan appen. Principinställningarna används när appen söker efter dem, oftast första gången den körs.

> [!TIP]
> Den här principen är för närvarande endast tillgänglig för enheter som kör iOS 8.0 och senare. Den stöder följande appinstallationstyper:
>
> -   **Hanterade iOS-appar från App Store**
> -   **App-paket för iOS**
>
> Mer information om appinstallationstyper finns i [Så här lägger du till en app i Microsoft Intune](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Skapa en appkonfigurationsprincip

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** + **Intune**.
3. Välj arbetsbelastningen **mobilappar**.
4. Under gruppen **Hantera** väljer du **Appkonfigurationsprinciper** och väljer sedan **Lägg till**.
5. Ange följande information:
    - **Namn**<br>
      Namnet på den profil som visas i Azure Portal.
    - **Beskrivning**<br>
      Beskrivning av den profil som visas i Azure Portal.
    - **Enhetsregistreringstyp**<br>
      Välj **Hanterade enheter**.
6. Välj **iOS** för **Plattform**.
7.  Välj **Tillhörande app**. På bladet **Tillhörande app** väljer du den hanterade app som du vill tillämpa konfigurationen på.
8.  På bladet **Lägg till konfigurationsprincip** väljer du **Konfigurationsinställningar**.
9. Välj **Format för konfigurationsinställningar**. Välj något av följande:
    - **[Använd Configuration Designer](#Use-the-configuration-designer)**
    - **[Ange XML-data](#enter-xml-data)**
10. Välj **OK** och sedan **Lägg till**.

## <a name="use-configuration-designer"></a>Använda Configuration Designer

Du kan både använda Configuration Designer för appar på enheter som har registrerats eller enheter som inte har registrerats i Intune. Designern gör det möjligt att konfigurera specifika konfigurationsnycklar och värden. Du måste även ange datatyp för varje värde. Inställningarna skickas automatiskt till appar när de installeras.

### <a name="add-a-setting"></a>Lägg till en inställning

1. För varje nyckel och värde i konfigurationen anger du:
   - **Konfigurationsnyckel**<br>
     Nyckeln som identifierar den specifika konfigurationsinställningen.
   - **Värdetyp**<br>
     Konfigurationsvärdets datatyp. Möjliga typer är heltals-, verklig, sträng- eller booleskt värde.
   - **Konfigurationsvärde**<br>
     Värdet för konfigurationen.
2. Välj **OK** för att ange konfigurationsinställningar.

### <a name="delete-a-setting"></a>Ta bort en inställning

1. Välj de tre punkterna (**...**) bredvid inställningen.
2. Välj **Ta bort**.

Tecknen \{\{ och \}\} används endast av tokentyper och får inte användas för andra ändamål.

## <a name="enter-xml-data"></a>Ange XML-data

Du kan ange eller klistra in en XML-egenskapslista som innehåller appkonfigurationsinställningarna för enheter som registrerats i Intune. Formatet på XML-egenskapslistan varierar beroende på vilken app du konfigurerar. Kontakta appleverantören för information om vilket format du ska använda.

Intune verifierar XML-formatet. Intune kontrollerar dock inte om XML-egenskapslistan (PList) fungerar med målappen.

Läs mer om XML-egenskapslistor:

  -  Läs [Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).
  -  Hänvisa till [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Förstå XML-egenskapslistor) i iOS Developer Library.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Exempelformat för en XML-fil för en appkonfiguration

När du skapar en appkonfigurationsfil kan du ange ett eller flera av följande värden med hjälp av det här formatet:

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
### <a name="supported-xml-plist-data-types"></a>XML PList-datatyper som stöds

Intune har stöd för följande datatyper i en egenskapslista:

- &lt;heltal&gt;
- &lt;verklig&gt;
- &lt;sträng&gt;
- &lt;matris&gt;
- &lt;dict&gt;
- &lt;sant/&gt; eller &lt;falskt/&gt;

### <a name="tokens-used-in-the-property-list"></a>Token som används i egenskapslistan

Dessutom stöder Intune följande typer av token i egenskapslistan:
- \{\{userprincipalname\}\} – till exempel **John@contoso.com**
- \{\{mail\}\} – till exempel **John@contoso.com**
- \{\{partialupn\}\} – till exempel **John**
- \{\{accountid\}\} – till exempel **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\} – till exempel **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\} – till exempel **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} – till exempel **Johan Danielsson**
- \{\{serialnumber\}\} – till exempel **F4KN99ZUG5V2** (för iOS-enheter)
- \{\{serialnumberlast4digits\}\} – till exempel **G5V2** (för iOS-enheter)

## <a name="next-steps"></a>Nästa steg

Fortsätt sedan med att [tilldela](apps-deploy.md) och [övervaka](apps-monitor.md) appen som vanligt.