---
title: "Lägg till appkonfigurationsprinciper för hanterade iOS-enheter"
titlesuffix: Microsoft Intune
description: "Lär dig hur du använder appkonfigurationsprinciper för att skicka konfigurationsdata till en iOS-app när den körs."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ee17ceae0af131f683341f2346f92ad5ef03ed16
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Lägg till appkonfigurationsprinciper för hanterade iOS-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd appkonfigurationsprinciper i Microsoft Intune för att skicka inställningar när användarna kör en iOS-app. Du tilldelar inte principerna direkt till användare och enheter. I stället associerar du principen med en app och tilldelar sedan appen. Principinställningarna används när appen söker efter dem, oftast första gången den körs.

Du kan tilldela en programkonfigurationsprincip till en grupp användare och enheter genom att använda en kombination av tilldelningar som inkluderar och exkluderar. När du lägger till en appkonfigurationsprincip kan du ange tilldelningar för den. När du anger tilldelningar för principen kan du välja att inkludera och exkludera grupper av användare som principen ska gälla för. När du väljer att inkludera en eller flera grupper kan du välja att utse specifika grupper att inkludera eller välja inbyggda grupper. Inbyggda grupper innefattar **Alla användare**, **Alla enheter** samt **Alla användare och alla enheter**. 

>[!NOTE]
>Intune tillhandahåller de i förväg skapade grupperna **Alla användare** och **Alla enheter** i konsolen med inbyggda optimeringar för att förenkla för dig. Vi rekommenderar starkt att du använder de här grupperna för att ange alla användare och alla enheter som mål i stället för grupperna för ”Alla användare” eller ”Alla enheter” som du själv har skapat.

När du har valt de grupper som ska inkluderas i programkonfigurationsprincipen kan du även välja de specifika grupper som du vill exkludera.

> [!TIP]
> Den här principen är för närvarande endast tillgänglig för enheter som kör iOS 8.0 och senare. Den stöder följande appinstallationstyper:
>
> -   **Hanterade iOS-appar från App Store**
> -   **App-paket för iOS**
>
> Mer information om appinstallationstyper finns i [Så här lägger du till en app i Microsoft Intune](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Skapa en appkonfigurationsprincip

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
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
7.  Välj **Tillhörande app**. I fönstret **Tillhörande app** väljer du den hanterade app som du vill tillämpa konfigurationen på och sedan **OK**.
8.  I fönstret **Lägg till konfigurationsprincip** väljer du **Konfigurationsinställningar**.
9. Välj **Format för konfigurationsinställningar**. Välj något av följande:
    - **[Använd Configuration Designer](#use-configuration-designer)**
    - **[Ange XML-data](#enter-xml-data)**
10. När du har lagt till XML-informationen väljer du **OK** och sedan väljer du **Lägg till** för att lägga till konfigurationsprincipen. Översiktsfönstret för konfigurationsprincipen visas.
11. Välj **Tilldelningar** för att visa alternativen för att inkludera och exkludera. 

    ![Skärmbild av fliken Inkludera för principtilldelningar](./media/app-config-policy01.png)
12. Välj **Alla användare** på fliken **Inkludera**.

    ![Skärmbild av principtilldelningar – listrutealternativet Alla användare](./media/app-config-policy02.png)
13. Välj fliken **Exkludera**. 
14. Klicka på **Välj grupper att utesluta** för att visa det relaterade fönstret.

    ![Skärmbild av principtilldelningar – bladet Välj grupper att undanta](./media/app-config-policy03.png)
15. Välj de grupper som du vill exkludera och klicka sedan på **Välj**.

    >[!NOTE]
    >Om någon annan grupp redan har inkluderats för en viss tilldelning när du lägger till en grupp så blir den förvald och kan inte ändras för andra tilldelningstyper för inkludering. Gruppen som har använts kan därför inte användas som en undantagen grupp.
16. Klicka på **Spara**.

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