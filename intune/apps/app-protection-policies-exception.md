---
title: Undantag för dataöverföringsprinciper i appar
titleSuffix: Microsoft Intune
description: Skapa undantag till dataöverföringsprincipen Intune-appskydd (APP).
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77a4f0ea0ee076907d2a6cd14000c5cf319231e6
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513783"
---
# <a name="how-to-create-exceptions-to-the-intune-app-protection-policy-app-data-transfer-policy"></a>Skapa undantag till dataöverföringsprincipen Intune-appskydd (APP)

Som administratör kan du skapa undantag till dataöverföringsprincipen Intune-appskydd (APP). Med ett undantag kan du uttryckligen välja vilka ohanterade appar som får överföra data till och från hanterade appar. IT-avdelningen måste ange de ohanterade apparna som du lägger i undantagslistan som betrodda. 

>[!WARNING] 
> Du ansvarar för att göra ändringar i undantagsprincipen för dataöverföring. Tillägg till den här principen tillåter att ohanterade appar (som inte hanteras av Intune) får åtkomst till data som skyddas av hanterade appar. Den här åtkomsten till skyddade data kan resultera i datasäkerhetsläckor. Lägg endast till dataöverföringsundantag för appar som din organisation måste använda, men som saknar stöd för Intunes principer för programskydd. Dessutom bör du bara lägga till undantag för appar som du inte anser utgöra någon risk för dataläckor.

I en Intune-princip för programskydd betyder inställningen **Tillåt att appen överför data till andra appar** till **Principhanterade appar** att appen överför data enbart för appar som hanteras av Intune. Om du vill tillåta dataöverföring till specifika appar som inte har stöd för Intune APP kan du skapa undantag för den här principen med hjälp av **Välj appar att undanta**. Undantag tillåter program som hanteras av Intune att anropa ohanterade program baserat på URL-protokoll (iOS/iPadOS) eller paketnamn (Android). Intune lägger som standard till viktiga ursprungliga program till listan med undantag. 

> [!NOTE]
> Att ändra eller lägga till undantag för dataöverföringsprinciper påverkar inte andra appskyddsprinciper, som till exempel begränsningar för att klippa ut, kopiera och klistra in. 

## <a name="ios-data-transfer-exceptions"></a>Undantag vid iOS-dataöverföring
Du kan konfigurera dataöverföringsundantag för en princip med iOS/iPadOS som mål med hjälp av URL-protokoll. Om du vill lägga till ett undantag kan du läsa mer i dokumentationen från apputvecklaren om vilka URL-protokoll som stöds. Mer information om undantag vid iOS/iPadOS-dataöverföring finns i [Principinställningar för iOS/iPadOS-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-ios.md#data-transfer-exemptions).

> [!NOTE]
> Microsoft har inte en metod för att hitta URL-protokollet för att skapa appundantag för program från tredje part manuellt. 

## <a name="android-data-transfer-exceptions"></a>Undantag vid Android-dataöverföring
Du kan konfigurera dataöverföringsundantag för en princip med Android som mål med hjälp av appaketets namn. Paketnamnet för den app du vill lägga till ett undantag för finns på appsidan i **Google Play** Butik. Mer information om undantag vid Android-dataöverföring finns i [Principinställningar för Android-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> Du kan hitta paket-ID:et för en app genom att gå till appen i Google Play. Paket-ID finns i webbadressen på appens sida. Paket-ID för Microsoft Word-appen är till exempel **com.microsoft.office.word**.

### <a name="example"></a>Exempel
Genom att lägga till **Webex**-paketet som ett undantag till MAM-dataöverföringsprincipen, tillåts att Webex-länkar i ett hanterat e-postmeddelande i Outlook öppnas direkt i Webex-programmet. Dataöverföringen är fortfarande begränsad i andra ohanterade appar.

- **Webex**-exempel för iOS/iPadOS:   Om du vill göra ett undantag för **Webex**-appen så att den kan anropas av Intune-hanterade appar, måste du lägga till ett dataöverföringsundantag för följande sträng: <code>wbx</code>
    
- **Maps**-exempel för iOS/iPadOS:   Om du vill göra ett undantag för den inbyggda appen **Kartor** så att den kan anropas av Intune-hanterade appar, måste du lägga till ett dataöverföringsundantag för följande sträng: <code>maps</code>

- **Webex**-exempel för Android:   Om du vill göra ett undantag för **Webex**-appen så att den kan anropas av Intune-hanterade appar, måste du lägga till ett dataöverföringsundantag för följande sträng: <code>com.cisco.webex.meetings</code>
    
- **SMS**-exempel för Android:   Om du vill göra ett undantag för den inbyggda **SMS**-appen så att den kan anropas av Intune-hanterade appar via olika meddelandeappar och Android-enheter, måste du lägga till undantag för dataöverföring för följande strängar: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

- Exempel på **installationsprogram för Android-certifikat**: För att undanta den inbyggda appen för **certifikatinstallation** så att Outlook för Android kan installera ett S/MIME-certifikat (levereras som en e-postbilaga) i Android KeyStore måste du lägga till dataöverföringsundantaget för följande sträng: <code>com.android.certinstaller</code>. Mer information finns i [Känslighetsetiketter och skydd i Outlook för iOS/iPadOS och Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/sensitive-labeling-and-protection-outlook-for-ios-android).

## <a name="next-steps"></a>Nästa steg

- [Skapa och distribuera appskyddsprinciper](app-protection-policies.md)
- [Principinställningar för iOS/iPadOS-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Principinställningar för Android-appskydd – Undantag vid dataöverföring](app-protection-policy-settings-android.md#data-transfer-exemptions)
