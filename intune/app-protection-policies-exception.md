---
title: Undantag för dataöverföringsprinciper i appar
titleSuffix: Microsoft Intune
description: Skapa undantag för Intunes MAM-princip (Mobile Application Management) vid dataöverföring.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1910334093a416933912c9cdeedac85e36d66e92
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Så här skapar du undantag för Intunes MAM-princip (Mobile Application Management) vid dataöverföring

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Som administratör kan du skapa undantag för Intunes MAM-princip (Mobile Application Management) vid dataöverföring. Med ett undantag kan du uttryckligen välja vilka ohanterade appar som får överföra data till och från hanterade appar. De ohanterade appar som du lägger i undantagslistan måste vara betrodda av IT-avdelningen. 

>[!WARNING] 
> Du ansvarar för att göra ändringar i undantagsprincipen för dataöverföring. Tillägg till den här principen tillåter att ohanterade appar (som inte hanteras av Intune) får åtkomst till data som skyddas av hanterade appar. Den här åtkomsten till skyddade data kan resultera i datasäkerhetsläckor. Lägg endast till dataöverföringsundantag för appar som din organisation måste använda, men som saknar stöd för Intunes principer för programskydd. Dessutom bör du bara lägga till undantag för appar som du inte anser utgöra någon risk för dataläckor.

Den här funktionen tillämpas när du skapar en Intune-princip för programskydd med dataöverföringen inställd på **Endast hanterade appar**. Utöver de undantag du skapar är dataöverföringen ändå begränsad till appar som hanteras av Intune när dataöverföringsprincipen är inställd på **Endast hanterade appar**. Du kan skapa begränsningarna med protokoll (iOS) eller paket (Android).

Du kan konfigurera att den här funktionen möjliggör undantag till Intunes MAM-princip för programskydd för att **begränsa dataöverföringen**. Den här principen är bara nödvändig om du vill tillåta att data överförs till en app som inte stöds av Intune-principen för programskydd. Med den här principen kan program som hanteras av Intune, med dataöverföringsinställningen **Endast hanterade appar**, anropa ohanterade program baserat på URL-protokoll (iOS) eller paketnamn (Android). Intune lägger till viktiga ursprungliga program till standardlistan med undantag. 

## <a name="ios-data-transfer-exceptions"></a>Undantag vid iOS-dataöverföring
Du kan konfigurera dataöverföringsundantag för en princip med iOS som mål med hjälp av URL-protokoll. Om du vill lägga till ett undantag kan du läsa mer i dokumentationen från apputvecklaren om vilka URL-protokoll som stöds. Mer information om undantag vid iOS-dataöverföring finns i [Principinställningar för iOS-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-ios.md#data-transfer-exemptions).

## <a name="android-data-transfer-exceptions"></a>Undantag vid Android-dataöverföring
Du kan konfigurera dataöverföringsundantag för en princip med Android som mål med hjälp av appaketets namn. Paketnamnet för den app du vill lägga till ett undantag för finns på appsidan i **Google Play** Butik. Mer information om undantag vid Android-dataöverföring finns i [Principinställningar för Android-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> Du kan hitta paket-ID:et för en app genom att gå till appen i Google Play. Paket-ID finns i webbadressen på appens sida. Paket-ID för Microsoft Word-appen är till exempel **com.microsoft.office.word**.

### <a name="example"></a>Exempel
Genom att lägga till **Webex**-paketet som ett undantag till MAM-dataöverföringsprincipen, tillåts att Webex-länkar i ett hanterat e-postmeddelande i Outlook öppnas direkt i Webex-programmet. Dataöverföringen är fortfarande begränsad i andra ohanterade appar.

- **Webex**-exempel för iOS:   Om du vill göra ett undantag för **Webex**-appen så att den kan anropas av Intune-hanterade appar, måste du lägga till ett dataöverföringsundantag för följande sträng: <code>wbx</code>.

- **Webex**-exempel för Android:   Om du vill göra ett undantag för **Webex**-appen så att den kan anropas av Intune-hanterade appar, måste du lägga till ett dataöverföringsundantag för följande sträng: <code>com.cisco.webex.meetings</code>. 

## <a name="next-steps"></a>Nästa steg

- [Skapa och distribuera appskyddsprinciper](app-protection-policies.md)
- [Principinställningar för iOS-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Principinställningar för Android-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-android.md#data-transfer-exemptions)
