---
title: Appskyddsprinciper för tillägg
titleSuffix: Microsoft Intune
description: Det här ämnet beskriver appskyddsprinciper (APP) för tillägg.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f38f22d7aaf03f278fad86061aa8198c8e37f31f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725497"
---
# <a name="protecting-application-extensions"></a>Skydda programtillägg

I den här artikeln beskrivs programskyddsprinciper för tillägg i Microsoft Intune.

## <a name="add-ins-for-outlook-app"></a>Tillägg för Outlook-appen

Med Outlook-tillägg kan du integrera populära appar med e-postklienten. Tillägg för Outlook är tillgängliga för Outlook på webben, Windows, Mac och Outlook för Android och iOS. Appskyddsprinciperna för Intune APP SDK och Intune har inte stöd för att hantera tillägg till Outlook, men det finns andra sätt för att användningen. Eftersom tillägg hanteras via Microsoft Exchange kan användarna dela data och meddelanden via Outlook och ohanterade tilläggsprogram, såvida inte tilläggen har inaktiverats för användarna av Exchange.

Om du vill förhindra slutanvändarna från att få åtkomst till och kunna installera Outlook-tillägg (vilket påverkar alla Outlook-klienter) gör du följande rolländringar i Exchange-administrationscentret:

- Om du vill förhindra användare från att installera Office Store-tillägg tar du bort rollen Min Marketplace från dem.
- Om du vill förhindra användare från att läsa in tillägg separat tar du bort rollen Mina anpassade appar från dem.
- Om du vill förhindra användare från att installera alla tillägg tar du bort båda rollerna, Mina anpassade appar och Min Marketplace, från dem.

Dessa anvisningar gäller för Office 365, Exchange 2016, Exchange 2013 via Outlook på webben, Windows, Mac och mobilt.

- Lär dig mer om [tillägg för Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Lär dig mer om [hur du anger administratörer och användare som kan installera och hantera tillägg för Outlook-appen](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).

## <a name="linkedin-account-connections-for-microsoft-apps"></a>LinkedIn-kontoanslutningar för Microsoft-appar

Med LinkedIn-kontoanslutningar kan användare visa offentlig LinkedIn-profilinformation i vissa Microsoft-appar. Som standard kan användarna välja att ansluta sina LinkedIn-konton och Microsoft-konton för arbete eller skola för att visa ytterligare LinkedIn-profilinformation. 

> [!NOTE]
> LinkedIn-integration är för närvarande inte tillgängligt för kunder inom USA:s förvaltning eller för organisationer med Exchange Online-postlådor som finns i Australien, Kanada, Kina, Frankrike, Tyskland, Indien, Sydkorea, Storbritannien, Japan och Sydafrika.

Appskyddsprinciperna för Intune SDK och Intune har inte stöd för att hantera LinkedIn-kontoanslutningar, men det finns andra sätt att hantera dem. Du kan inaktivera LinkedIn-kontoanslutningar för hela organisationen, eller aktivera LinkedIn-kontoanslutningar för valda användargrupper i organisationen. Dessa inställningar påverkar LinkedIn-anslutningar i Office 365-appar på alla plattformar (webb, mobil och skrivbord). Du kan:

- Aktivera eller inaktivera LinkedIn-kontoanslutningar för din klientorganisation på Azure Portal. 
- Aktivera eller inaktivera LinkedIn-kontoanslutningar för din organisations Office 2016-appar med hjälp av grupprinciper.

Om LinkedIn-integration har aktiverats för din klientorganisation kan användarna i din organisation välja mellan två alternativ när de ansluter sina LinkedIn-konton och Microsoft-konton för skola eller arbete: 

- De kan välja att dela data mellan båda kontona. Det innebär att de tillåter att deras LinkedIn-konto delar data med deras Microsoft-skolkonto eller -arbetskonto och att deras Microsoft-skolkonto eller -arbetskonto delar data med deras LinkedIn-konto. Data som delas med LinkedIn lämnar onlinetjänsterna. 
- De kan välja att bara dela data från deras LinkedIn-konto till deras Microsoft-arbetskonto eller -skolkonto

Om en användare godkänner att data delas mellan konton, som med Office-tillägg, används befintliga Microsoft Graph API:er för LinkedIn-integrationen. LinkedIn-integrationen använder endast en deluppsättning av de API:er som är tillgängliga för Office-tillägg och stöder olika undantag.


|Microsoft Graph-behörigheter  |Beskrivning  |
|---------|---------|
|Läsbehörighet för [personer](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#people-permissions)     |Tillåter att appen läser en graderad lista med personer som är relevanta för den inloggade användaren. Listan kan innehålla lokala kontakter, kontakter från sociala nätverk eller din organisations katalog, samt personer från den senaste kommunikationen (till exempel e-post eller Skype).         |
|Läsbehörighet för [kalendrar](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#calendars-permissions)     |Tillåter att appen läser händelser i användarkalendrar. Detta omfattar möten i den inloggade användarens kalendrar, liksom mötestider, mötesplatser och mötesdeltagare.         |
|Läsbehörighet för [användarprofiler](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#user-permissions)     |Tillåter att användare loggar in i appen och tillåter att appen läser profilen för inloggade användare. Appen ges också tillstånd att läsa grundläggande företagsinformation för inloggade användare.         |
|Subscriptions     |Det här omfånget är inte tillgängligt och används inte än. Det omfattar prenumerationer som tillhandahålls av användarens organisation för Microsoft-appar och Microsoft-tjänster, till exempel Office 365.         |
|Insights     |Det här omfånget är inte tillgängligt och används inte än. Det omfattar intressen som är associerade med den inloggade användarens konto baserat på deras användning av Microsoft-tjänster.         |

### <a name="learn-more"></a>Läs mer

- Läs mer om [LinkedIn-information och LinkedIn-funktioner i Microsoft-appar](https://go.microsoft.com/fwlink/?linkid=850740).
- Läs mer om utgåvor av LinkedIn-kontoanslutningar på [översiktssidan för Office 365](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc). 
- Läs mer om hur du [konfigurerar LinkedIn-kontoanslutningar](https://docs.microsoft.com/azure/active-directory/linkedin-integration).
- Mer information om data som delas mellan användarnas LinkedIn-konton och Microsoft-arbetskonton och -skolkonton finns i avsnittet om [LinkedIn i Microsoft-program på arbetsplatsen eller skolan](https://www.linkedin.com/help/linkedin/answer/84077).

