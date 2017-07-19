---
title: "Så här använder du appkonfigurationsprinciper för iOS i Intune"
titleSuffix: Intune on Azure
description: "Lär dig hur du använder appkonfigurationsprinciper för att skicka konfigurationsdata till en iOS-app när den körs.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 112f60ff208c27825ddd0f4c812535b255894333
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-ios"></a>Så här använder du appkonfigurationsprinciper för iOS i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd appkonfigurationsprinciper i Microsoft Intune om du vill skicka inställningar som kan krävas när användarna kör en iOS-app. En app kan till exempel kräva att användarna anger:

-   ett anpassat portnummer

-   språkinställningar

-   säkerhetsinställningar

-   anpassade inställningar, t.ex. en företagslogotyp.

Om användarna inte anger dessa inställningar på korrekt sätt kan det öka supportens arbetsbörda och ta längre tid att börja använda nya appar.

Med appkonfigurationsprinciper slipper du den här typen av problem eftersom du kan tilldela dessa inställningar till användarna i en princip innan de kör appen. Inställningarna distribueras sedan automatiskt utan att användarna behöver göra något.

Du tilldelar inte principerna direkt till användare och enheter. I stället associerar du principen med en app och tilldelar sedan appen. Principinställningarna används när appen söker efter dem (oftast första gången den körs.).

> [!TIP]
> Den här principen är för närvarande endast tillgänglig för enheter som kör iOS 8.0 och senare. Den stöder följande appinstallationstyper:
>
> -   **Hanterade iOS-appar från App Store**
> -   **App-paket för iOS**
>
> Mer information om appinstallationstyper finns i [Så här lägger du till en app i Microsoft Intune](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Skapa en appkonfigurationsprincip

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.
1.  Välj **Hantera** > **Appkonfigurationsprinciper** i arbetsbelastningen **Mobile Apps**.

2.  I listan med principblad väljer du **Lägg till**.

3.  På bladet **Lägg till konfigurationsprincip** anger du ett namn och en valfri beskrivning för appkonfigurationsprincipen.
4.  Välj **Associerad app**. På bladet **Tillhörande app** väljer du den hanterade app som du vill tillämpa konfigurationen på.
5.  På bladet **Lägg till konfigurationsprincip** väljer du **Konfigurationsinställningar**. På bladet Konfigurationsinställningar väljer du sedan hur du vill ange de XML-värden som utgör konfigurationsprofilen från:
    - **Ange XML-data** – Ange eller klistra in en XML-egenskapslista som innehåller appkonfigurationsinställningarna som du vill använda. Formatet på XML-egenskapslistan varierar beroende på vilken app du konfigurerar. Kontakta appleverantören för information om vilket format du ska använda.
    Intune kontrollerar att den XML som du angett har ett giltigt format. Intune kontrollerar inte om XML-egenskapslistan fungerar med den app som den är associerad med.
    Mer information om XML-egenskapslistor finns i [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) i iOS Developer Library.
    - **Använd Configuration Designer** – Låter dig ange XML-nyckel och värdepar direkt i portalen.
8. När du är klar går du tillbaka till bladet **Lägg till konfigurationsprincip** och trycker på **Skapa**.

Principen kommer att skapas och visas på bladet med principlistan.

Fortsätt sedan med att [tilldela](apps-deploy.md) och [övervaka](apps-monitor.md) appen som vanligt.

När den tilldelade appen körs på en enhet, körs den med de inställningar som du konfigurerade i appkonfigurationsprincipen.

> [!TIP]
> Om en eller flera appkonfigurationsprinciper är i konflikt med varandra tillämpas ingen av dem.

## <a name="create-a-mam-targeted-configuration-policy"></a>Skapa en MAM-riktad konfigurationsprincip
Med hjälp av en MAM-riktad konfiguration kan en app att ta emot konfigurationsdata via Intune App SDK. Dataformat och eventuella varianter av dessa data måste definieras och kommuniceras till Intune-kunderna av ägaren/programutvecklaren. Intune-administratörerna kan rikta in och distribuera konfigurationsdata via Intune Azure-konsolen. MAM-riktade konfigurationsdata kan skickas med MAM-tjänsten till MAM-WE-aktiverade program. [Intune Managed Browser](https://docs.microsoft.com/intune/app-configuration-managed-browser) har t.ex. en lista för tillåtna/blockerade webbadresser. Programmets konfigurationsdata push-överförs med vår MAM-tjänst direkt till appen i stället för via MDM-kanalen. [MDM-appens konfigurationsprinciper](https://docs.microsoft.com/intune/app-configuration-policies-use-ios#create-an-app-configuration-policy) utgör den grundläggande lösningen, via MDM. Den viktigaste skillnaden med en MAM-riktad konfiguration är att den enhet som appen körs på inte behöver vara MDM-registrerad. MAM-riktad konfiguration är tillgänglig för iOS och Android. I iOS måste appen ha Intune App SDK för iOS (version 7.0.1) införlivad, och den måste vara delaktig i inställning av appkonfigurationen. Stegen för att skapa en MAM-riktad konfigurationsprincip är följande: 

1. Logga in på **Azure-portalen**.

2. Välj **Intune > Mobilappar – Appkonfigurationsprinciper**.

3. På bladet **Appkonfigurationsprinciper** väljer du **Lägg till**.

4. Ange ett **Namn** och en valfri **Beskrivning** för appens konfigurationsinställningar och välj **Inte registrerad med Intune**.

5. Välj **Välj obligatoriska appar** och välj sedan appar för de plattformar som du tänker använda på bladet **Riktade**. <br>
**Obs!** För LOB-appar väljer du **Fler appar**. Ange paket-ID för programmet.

6. Välj **OK** för att återgå till bladet **Lägg till appkonfiguration**.

7. Välj **Definiera konfiguration**. På bladet **Konfiguration** definierar du nyckel- och värdepar för att kunna tillhandahålla konfigurationer.

8. När du är klar väljer du **OK**.

9. På **bladet Lägg till appkonfiguration** väljer du **Skapa**.

Den nya konfigurationen skapas och visas på bladet Appkonfiguration.

Fortsätt sedan med att [tilldela](apps-deploy.md) och [övervaka](apps-monitor.md) appen som vanligt.

När den tilldelade appen (integrerad med Intune App SDK) körs på en enhet, körs den med de inställningar som du konfigurerade i den MAM-riktade konfigurationsprincipen. Den tilldelade appen måste ha implementerat den version som stöds av Intune APP SDK. Mer information om kraven vid apputveckling som använder MAM-riktade konfigurationsprinciper finns i [Integreringsguide för iOS Intune APP SDK](https://docs.microsoft.com/intune/app-sdk-ios).

Mer information om funktionerna i vår Graph API med avseende på MAM-riktade konfigurationsvärden, finns i [Graph API-referens för MAM-riktad konfiguration](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

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
