---
title: Vad är appskyddsprinciper?
titleSuffix: Microsoft Intune
description: Läs mer om hur Microsoft Intune appskyddsprinciper hjälper till att skydda företagets data och förhindra dataförluster.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 09/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 5acdcd0a8c2fcb906f0b40e2c1ab937559c7ae01
ms.sourcegitcommit: 445a54dc6826a549d770a9953549ae2191d391c2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/17/2018
ms.locfileid: "45727585"
---
# <a name="what-are-app-protection-policies"></a>Vad är appskyddsprinciper?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune appskyddsprinciper hjälper till att skydda företagets data och att förhindra dataförluster.

## <a name="how-you-can-protect-app-data"></a>Hur du kan skydda appdata
Dina anställda använder mobila enheter för både personliga och arbetsrelaterade uppgifter.  Samtidigt som du vill se till att de anställda kan vara produktiva vill du även förhindra dataförlust, både avsiktlig och oavsiktlig.  Dessutom vill du kunna skydda företagsdata som nås med enheter även i de fall då de inte hanteras av dig.

Du kan använda Intunes appskyddsprinciper för att skydda företagets data. Eftersom Intunes appskyddsprinciper kan användas **oberoende av en hanteringslösning för mobila enheter (MDM)** kan du använda dem för att skydda företagets data både om du registrerar eller inte registrerar enheter i en enhetshanteringslösning. Genom att implementera **principer på appnivå** kan du begränsa åtkomsten till företagsresurser och hålla data inom IT-avdelningens kontroll.

Appskyddsprinciper kan konfigureras för appar som körs på enheter som:

- **Är registrerade i Microsoft Intune:** Enheter i den här kategorin är vanligtvis företagsägda enheter.

- **Är registrerade i en hanteringslösning för mobila enheter (MDM) från tredje part:**   Enheter i den här kategorin är vanligtvis företagsägda enheter.

  > [!NOTE]
  > Principer för mobilapphantering ska inte användas med tredje parts mobilapphantering eller säkra containerlösningar.

- **Inte är registrerade i någon hanteringslösning för mobila enheter:**  Enheter i den här kategorin är vanligtvis personalägda enheter som inte hanteras eller som inte är registrerade i Intune eller andra MDM-lösningar.

> [!IMPORTANT]
> Du kan skapa hanteringsprinciper för mobila appar för Office-mobilappar som ansluter till Office 365-tjänster. Du kan även skydda åtkomsten till lokala Exchange-postlådor genom att skapa Intune-appskyddsprinciper för Outlook för iOS och Android där modern hybridautentisering är aktiverad. Innan du använder den här funktionen måste du se till att du uppfyller [kraven för Outlook för iOS och Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). Appskyddsprinciper stöds inte för andra appar som ansluter till lokala Exchange- eller SharePoint-tjänster.

**De främsta fördelarna med att använda appskyddsprinciper är:**

-   Skydda företagets data på appnivå.  Eftersom mobilapphantering inte kräver enhetshantering kan du skydda företagets data på både hanterade och ohanterade enheter. Eftersom hanteringen är uppbyggd kring användaridentiteten krävs ingen enhetshantering.

-   Slutanvändarens produktivitet påverkas inte och principerna tillämpas inte när appen används i en privat kontext.  Principerna tillämpas endast i arbetssammanhang, vilket ger dig möjlighet att skydda företagets data utan att röra personliga data.

Det finns ytterligare fördelar med att använda MDM med appskyddsprinciper. Företag kan använda appskyddsprinciper både med och utan MDM på samma gång. En medarbetare kan till exempel använda en telefon som utfärdats av företaget, samt en personlig surfplatta.  I det här fallet registreras företagets telefon i MDM och skyddas av appskyddsprinciper, och den personliga enheten skyddas endast av appskyddsprinciper.

- **MDM ser till att enheten är skyddad**.  Du kan till exempel behöva en PIN-kod för att få åtkomst till enheten, eller så kan du distribuera hanterade appar till enheten. Du kan också distribuera appar till enheter via MDM-lösningen, vilket ger dig större kontroll över apphanteringen.

- **Appskyddsprinciper säkerställer att det finns skydd på appnivå**. Du kan till exempel kräva en PIN-kod för att öppna en app i arbetssammanhang eller om data kan delas mellan appar, eller förhindra att företagets appdata sparas till en personlig lagringsplats.


### <a name="supported-platforms-for-app-protection-polices"></a>Plattformar som stöds för appskyddsprinciper
Plattformsstödet för Intune-appskyddsprinciper är synkroniserat med plattformsstödet för Office-program. Mer information finns i [Systemkrav för Office](https://products.office.com/en-US/office-system-requirements).

Windows-enheter stöds inte för tillfället. När du registrerar Windows 10-enheter med Intune kan du använda Windows Information Protection, som innehåller liknande funktioner. Mer information finns i avsnittet om hur du [skyddar dina företagsdata med hjälp av Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
##  <a name="how-app-protection-policies-protect-app-data"></a>Hur appskyddsprinciper skyddar appdata

####  <a name="apps-without-app-protection-policies"></a>Appar utan appskyddsprinciper

![Bild som visar hur data kan flyttas fritt mellan appar när inga appskyddsprinciper tillämpas](./media/apps-without-protection-policies.png)

När appar används utan begränsningar kan företagsrelaterade och personliga data blandas.  Företagsdata kan hamna på platser som personlig lagring eller överföras till appar som du inte har kontroll över, vilket leder till dataförlust. Pilarna i diagrammet visar hur data flyttas utan begränsningar mellan appar (företagsdata och personliga data) och till lagringsplatser.


### <a name="data-protection-with-app-protection-policies"></a>Dataskydd med appskyddsprinciper

![Bild som visar hur företagsdata skyddas när appskyddsprinciper tillämpas ](./media/apps-with-protection-policies.png)


Du kan använda appskyddsprinciper för att förhindra att företagets data sparas till enhetens lokala lagring och begränsa dataflyttningen till andra appar som inte skyddas av appskyddsprinciper. Principinställningar för appskydd inkluderar:
- Principer för dataflytt som **Förhindra spara som**, **Begränsa klipp ut, kopiera och klistra in**.
- Inställningar för åtkomstprinciper som **Kräv enkel PIN för åtkomst** eller **Blockera hanterade appar från att köras på jailbrokade eller rotade enheter**.

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mdm-solution"></a>Dataskydd med appskyddsprinciper på enheter som hanteras av en MDM-lösning

![Bild som visar hur appskyddsprinciper fungerar på BYOD-enheter](./media/app-protection-policies-with-mdm.png)

**För enheter som har registrerats i en MDM-lösning**-

Bilden ovan visar de skyddslager som MDM och appskyddsprinciper erbjuder tillsammans.

MDM-lösningen:

-   Registrerar enheten

-   Distribuerar appar till enheten

-   Tillhandahåller fortlöpande enhetskompatibilitet och hantering

**Appskyddsprinciper lägger till värde genom att:**

-   Hjälpa till att skydda företagsdata från att läcka till konsumentappar och tjänster

-   Använda begränsningar (Spara som, Urklipp, PIN-kod osv.) för klientappar

-   Rensa företagsdata från appar utan att ta bort dessa appar från enheten


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Dataskydd med appskyddsprinciper för enheter utan registrering

![Bild som visar hur appskyddsprinciper fungerar på hanterade enheter](./media/app-protection-policies-without-mdm.png)

Diagrammet ovan visar hur dataskyddsprinciper fungerar på appnivå utan MDM.

För BYOD-enheter som inte har registrerats i någon MDM-lösning kan appskyddsprinciper skydda företagets data på appnivå.
Det finns dock vissa begränsningar som du bör känna till, t.ex.:

-   Du kan inte distribuera appar till enheten.  Slutanvändaren måste hämta apparna från butiken.

-   Du kan inte etablera certifikatprofiler på enheterna.

-   Du kan inte etablera företagets Wi-Fi- och VPN-inställningar på enheterna.

## <a name="app-protection-global-policy"></a>Global princip för appskydd

Om en OneDrive-administratör går till **admin.office.com** och väljer **Enhetsåtkomst** kan de ha möjligheten att ange kontroller för **hantering av mobilprogram** för OneDrive- och SharePoint-klientappar. 

Inställningarna, som nås via OneDrive Admin-konsolen, konfigurerar en särskild Intune-appskyddsprincip som kallas **den Globala** principen. Den globala principen gäller för alla användare i din klient och kan inte styra riktad principtillämpning. 

När den har aktiverats skyddas OneDrive- och SharePoint-appar för iOS och Android med de valda inställningarna som standard. IT-personal kan ändra den här principen i Intune-konsolen när den har skapats och lägga till fler riktade appar och ändra alla principinställningar. 

Som standard kan det endast finnas en **Global** princip per klient. [Intune Graph API:er](intune-graph-apis.md) kan användas för att skapa extra globala principer per klient men detta rekommenderas inte. Vi rekommendera att du inte skapar extra globala principer då detta kan komplicera en eventuell felsökning av implementeringen av principen.

Medan den **Globala** principen gäller för alla användare i din klient kommer standardprinciper för appskydd med Intune att åsidosätta dessa inställningar.


## <a name="multi-identity"></a>Flera identiteter

Med appar som stöder flera identiteter kan du använda olika konton (arbetskonton och privata konton) för att få åtkomst till samma appar, där appskyddsprinciperna endast tillämpas när apparna används i arbetskontexten.

Om en användare t.ex. startar appen OneDrive med sitt arbetskonto kan hen inte flytta filerna till en personlig lagringsplats. Om användaren däremot använder OneDrive med ett personligt konto kan hen kopiera och flytta data från sin personliga OneDrive utan begränsningar.

- Mer information om appar som stöder [MAM och multiidentitet](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) med Intune.

##  <a name="next-steps"></a>Nästa steg

[Skapa och distribuera appskyddsprinciper med Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Se även
Appar från tredje part, till exempel Salesforce-mobilappen fungerar med Intune på specifika sätt för att skydda företagsdata. Läs mer om hur Salesforce-appen i synnerhet fungerar med Intune (inklusive MDM-appkonfigurationsinställningar) i [Salesforce-appen och Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
