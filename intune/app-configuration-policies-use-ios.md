---
title: "Så här använder du appkonfigurationsprinciper för iOS i Intune"
titlesuffix: Azure portal
description: "Lär dig hur du använder appkonfigurationsprinciper för att skicka konfigurationsdata till en iOS-app när den körs.\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bc42f3cafa83b5f7ba053d03dbd066b725bb1fee
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-ios"></a>Så här använder du appkonfigurationsprinciper för iOS i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd appkonfigurationsprinciper i Microsoft Intune om du vill skicka de inställningar som krävs när användarna kör en iOS-app. En app kan till exempel kräva att användarna anger:

-   ett anpassat portnummer

-   språkinställningar

-   säkerhetsinställningar

-   anpassade inställningar, t.ex. en företagslogotyp.

Om användarna inte anger dessa inställningar på korrekt sätt kan det öka supportens arbetsbörda och ta längre tid att börja använda nya appar.

Med appkonfigurationsprinciper slipper du den här typen av problem eftersom du kan tilldela dessa inställningar till användarna i en princip innan de kör appen. Inställningarna distribueras sedan automatiskt utan att användarna behöver göra något. Appar måste ha skrivits för att stödja användning av appkonfigurationer. Kontakta appleverantören om du vill ha mer information.

Du tilldelar inte principerna direkt till användare och enheter. I stället associerar du principen med en app och tilldelar sedan appen. Principinställningarna används när appen söker efter dem (oftast första gången den körs).

> [!TIP]
> Den här principen är för närvarande endast tillgänglig för enheter som kör iOS 8.0 och senare. Den stöder följande appinstallationstyper:
>
> -   **Hanterade iOS-appar från App Store**
> -   **App-paket för iOS**
>
> Mer information om appinstallationstyper finns i [Så här lägger du till en app i Microsoft Intune](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Skapa en appkonfigurationsprincip
1.  Logga in på Azure-portalen.
2.  Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3.  Välj **Mobilappar** på **Intune**-bladet.
4.  Välj **Hantera** > **Appkonfigurationsprinciper** i arbetsbelastningen **Mobile Apps**.
5.  I listan med principblad väljer du **Lägg till**.
6.  På bladet **Lägg till konfigurationsprincip** anger du ett **Namn** och en valfri **Beskrivning** för appkonfigurationsprincipen.
7.  För **Registreringstyp för enhet** väljer du något av följande:
    - **Registrerad med Intune** – för appar som hanteras av Intune.
    - **Inte registrerad med Intune** – för appar som inte hanteras av Intune eller som hanteras av en annan lösning.
8.  Under **Plattform** väljer du **iOS** (endast för enheter som registrerats i Intune)
9.  Välj **Associerad app**. På bladet **Tillhörande app** väljer du den hanterade app som du vill tillämpa konfigurationen på.
10. På bladet **Lägg till konfigurationsprincip** väljer du **Konfigurationsinställningar**
11. På bladet **Konfigurationsinställningar** väljer du sedan hur du vill ange de XML-värden som utgör konfigurationsprofilen från:
    - **Ange XML-data** (endast för enheter som registrerats i Intune) – Ange eller klistra in en XML-egenskapslista som innehåller appkonfigurationsinställningarna som du vill använda. Formatet på XML-egenskapslistan varierar beroende på vilken app du konfigurerar. Kontakta appleverantören för information om vilket format du ska använda.
Intune kontrollerar att den XML som du angett har ett giltigt format. Intune kontrollerar inte om XML-egenskapslistan fungerar med den app som den är associerad med.
Mer information om XML-egenskapslistor finns i [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) i iOS Developer Library.
    - **Använd Configuration Designer** (oavsett om enheten är registrerad eller inte) – Låter dig ange XML-nyckel och värdepar direkt i portalen.
11. När du är klar går du tillbaka till bladet **Lägg till konfigurationsprincip** och trycker på **Skapa**.

Principen skapas och visas på bladet med principlistan.



>[!Note]
>Du kan använda [Intune App SDK](https://docs.microsoft.com/intune/app-sdk-ios) för att förbereda branschspecifika appar som ska hanteras av appskydd- och appkonfigurationsprinciper i Intune – oavsett om enheten har registrerats i Intune eller inte. Du kan till exempel använda en appkonfigurationsprincip för att konfigurera användning av tillåtna respektive blockerade URL:er i [Intune Managed Browser](app-configuration-managed-browser.md). Om en app är kompatibel med dessa principer kan du konfigurera dem med hjälp av en princip.


När den tilldelade appen körs på en enhet, körs den med de inställningar som du konfigurerade i appkonfigurationsprincipen.
Läs dokumentationen till den app som du konfigurerar för mer information om vad som händer om en eller flera appkonfigurationsprinciper hamnar i konflikt med varandra.

>[!Tip]
>Du kan även använda Graph API för att utföra dessa uppgifter. Mer information finns i [Graph API-referens för MAM-riktad konfiguration](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).


## <a name="information-about-the-xml-file-format"></a>Information om XML-filformatet

Intune har stöd för följande datatyper i en egenskapslista:

- &lt;heltal&gt;
- &lt;verklig&gt;
- &lt;sträng&gt;
- &lt;matris&gt;
- &lt;dict&gt;
- &lt;sant/&gt; eller &lt;falskt/&gt;

Mer information om datatyper finns i [About Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) i iOS Developer Library.

Dessutom stöder Intune följande typer av token i egenskapslistan:
- \{\{userprincipalname\}\} – (Exempel: **John@contoso.com**)
- \{\{mail\}\} – (Exempel: **John@contoso.com**)
- \{\{partialupn\}\} – (Exempel: **Johan**)
- \{\{accountid\}\} – (Exempel: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{deviceid\}\} – (Exempel: **b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{userid\}\} – (Exempel: **3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{username\}\} – (Exempel: **Johan Danielsson**)
- \{\{serialnumber\}\} – (Exempel: **F4KN99ZUG5V2**) för iOS-enheter
- \{\{serialnumberlast4digits\}\} – (Exempel: **G5V2**) för iOS-enheter

Tecknen \{\{ och \}\} används endast av tokentyper och får inte användas för andra ändamål.

## <a name="example-format-for-an-app-configuration-xml-file"></a>Exempelformat för en XML-fil för en appkonfiguration

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

## <a name="next-steps"></a>Nästa steg

Fortsätt sedan med att [tilldela](apps-deploy.md) och [övervaka](apps-monitor.md) appen som vanligt.