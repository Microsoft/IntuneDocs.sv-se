---
title: Undantag för dataöverföringsprinciper i appar
titleSuffix: Microsoft Intune
description: Skapa undantag för Intunes MAM-princip (Mobile Application Management) vid dataöverföring.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5f50ad61634363ea1bc1ab8af139033a114f8b86
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231499"
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Så här skapar du undantag för Intunes MAM-princip (Mobile Application Management) vid dataöverföring

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Som administratör kan du skapa undantag för Intunes MAM-princip (Mobile Application Management) vid dataöverföring. Med ett undantag kan du uttryckligen välja vilka ohanterade appar som får överföra data till och från hanterade appar. De ohanterade appar som du lägger i undantagslistan måste vara betrodda av IT-avdelningen. 

>[!WARNING] 
> Du ansvarar för att göra ändringar i undantagsprincipen för dataöverföring. Tillägg till den här principen tillåter att ohanterade appar (som inte hanteras av Intune) får åtkomst till data som skyddas av hanterade appar. Den här åtkomsten till skyddade data kan resultera i datasäkerhetsläckor. Lägg endast till dataöverföringsundantag för appar som din organisation måste använda, men som saknar stöd för Intunes principer för programskydd. Dessutom bör du bara lägga till undantag för appar som du inte anser utgöra någon risk för dataläckor.

I en Intune-princip för programskydd betyder inställningen **Tillåt att appen överför data till andra appar** till **Principhanterade appar** att appen överför data enbart för appar som hanteras av Intune. Om du vill tillåta dataöverföring till specifika appar som inte har stöd för Intune APP kan du skapa undantag för den här principen med hjälp av **Välj appar att undanta**. Undantag tillåter program som hanteras av Intune att anropa ohanterade program baserat på URL-protokoll (iOS) eller paketnamn (Android). Intune lägger som standard till viktiga ursprungliga program till listan med undantag. 

> [!NOTE]
> Att ändra eller lägga till undantag för dataöverföringsprinciper påverkar inte andra appskyddsprinciper, som till exempel begränsningar för att klippa ut, kopiera och klistra in. 

## <a name="ios-data-transfer-exceptions"></a>Undantag vid iOS-dataöverföring
Du kan konfigurera dataöverföringsundantag för en princip med iOS som mål med hjälp av URL-protokoll. Om du vill lägga till ett undantag kan du läsa mer i dokumentationen från apputvecklaren om vilka URL-protokoll som stöds. Mer information om undantag vid iOS-dataöverföring finns i [Principinställningar för iOS-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-ios.md#data-transfer-exemptions).

> [!NOTE]
> Microsoft har inte en metod för att hitta URL-protokollet för att skapa appundantag för program från tredje part manuellt. 

## <a name="android-data-transfer-exceptions"></a>Undantag vid Android-dataöverföring
Du kan konfigurera dataöverföringsundantag för en princip med Android som mål med hjälp av appaketets namn. Paketnamnet för den app du vill lägga till ett undantag för finns på appsidan i **Google Play** Butik. Mer information om undantag vid Android-dataöverföring finns i [Principinställningar för Android-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> Du kan hitta paket-ID:et för en app genom att gå till appen i Google Play. Paket-ID finns i webbadressen på appens sida. Paket-ID för Microsoft Word-appen är till exempel **com.microsoft.office.word**.

### <a name="example"></a>Exempel
Genom att lägga till **Webex**-paketet som ett undantag till MAM-dataöverföringsprincipen, tillåts att Webex-länkar i ett hanterat e-postmeddelande i Outlook öppnas direkt i Webex-programmet. Dataöverföringen är fortfarande begränsad i andra ohanterade appar.

- **Webex**-exempel för iOS: Om du vill göra ett undantag för **Webex**-appen så att den kan anropas av Intune-hanterade appar, måste du lägga till ett dataöverföringsundantag för följande sträng: <code>wbx</code>
    
 - **Maps**-exempel för iOS: Om du vill göra ett undantag för den ursprungliga **Maps**-appen så att den kan anropas av Intune-hanterade appar, måste du lägga till ett dataöverföringsundantag för följande sträng: <code>maps</code>

- **Webex**-exempel för Android: Om du vill göra ett undantag för **Webex**-appen så att den kan anropas av Intune-hanterade appar, måste du lägga till ett dataöverföringsundantag för följande sträng: <code>com.cisco.webex.meetings</code>
    
- **SMS**-exempel för Android: För att undanta den överordnade länkens interna **SMS**-app så att den kan anropas av Intune-hanterade appar via olika meddelandeappar och Android-enheter, måste du lägga till undantag för dataöverföring för följande strängar: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>Nästa steg

- [Skapa och distribuera appskyddsprinciper](app-protection-policies.md)
- [Principinställningar för iOS-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Principinställningar för Android-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-android.md#data-transfer-exemptions)
