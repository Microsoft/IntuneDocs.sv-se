---
title: Så får dina Android-användare sina appar
description: Metoder för att göra Android-appar tillgängliga för slutanvändare
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 231b30e93a3e56811e1569c32cc1286e02320f0d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514412"
---
# <a name="how-your-android-users-get-their-apps"></a>Så får dina Android-användare sina appar

Den här artikeln hjälper dig att förstå hur och var dina Android-slutanvändare får de appar som du distribuerar via Microsoft Intune. Informationen kan variera för olika enhetstyper (Android-enheter eller Samsung Knox Standard-enheter).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Interna (ej Samsung Knox Standard) Android-enheter

| Typ av app | Verksamhetsspecifika appar | Play Store-appar  |
| ------------- |-------------| -----|
| Tillgängliga appar      | Användarna trycker på **Installera** i företagsportalen. Ett meddelande visas och användarna kan sedan trycka på det för att starta installationen. När installationen har slutförts försvinner meddelandet. | Användare trycker på appen i Företagsportal och kommer till en appsida i Play Store. Här startar de installationen.|
| Required apps      | Ett meddelande som inte kan stängas visas för användarna. I meddelandet står det att de måste installera en app. Användarna trycker på meddelandet för att starta installationen. När installationen har slutförts försvinner meddelandet.    | Ett meddelande som inte kan stängas visas för användarna. I meddelandet står det att de måste installera en app. När användarna trycker på meddelandet dirigeras de till en appsida i Play Store. Här startar de installationen. När installationen har slutförts försvinner meddelandet. |

Slutanvändarna måste tillåta installation från okända källor för att kunna installera [verksamhetsspecifika appar](../apps/lob-apps-android.md). Den här inställningen finns normalt på två olika platser:

* **Android 7.1.2 och tidigare**: **Inställningar** > **Säkerhet** > **Okända källor**
* **Android 8.0 och senare**: **Inställningar** > **Apps & notifications (Appar och aviseringar)**  > **Special app access (Särskild appåtkomst)**  > **Install unknown apps (Installera okända appar)**  > **Company Portal (Företagsportal)**  > **Allow from this source (Tillåt från den här källan)**

Om detta inträffar får slutanvändaren ett meddelande i företagsportalappen och vägleds direkt till rätt inställning. 

## <a name="samsung-knox-standard-android-devices"></a>Samsung Knox Standard Android-enheter

| Typ av app | Verksamhetsspecifika appar | Play Store-appar  |
| ------------- |-------------| -----|
| Tillgängliga appar      | Användarna trycker på **Installera** i företagsportalen. Appen installeras utan ytterligare åtgärder från användaren. | Användare trycker på appen i Företagsportal och kommer till en appsida i Play Store. Här startar de installationen.|
| Required apps      | Appen installeras utan ytterligare åtgärder från användaren.    | Ett meddelande som inte kan stängas visas för användarna. I meddelandet står det att de måste installera en app. När användarna trycker på meddelandet dirigeras de till en appsida i Play Store. Här startar de installationen. När installationen har slutförts försvinner meddelandet. |

Appar kan vara hanterade eller ohanterade (se nedan). Processen för att göra appar hanterade är densamma för alla typer av Android-enheter.

**Hanterade appar** – Dessa appar hanteras med principer. De har omslutits av Intune eller skapats med Intune App SDK. De här apparna kan hanteras av Intune och applikations-policys kan tillämpas på dem.

**Ohanterade appar** – Dessa appar hanteras med principer. De har inte omslutits av Intune eller inkluderar inte Intune App SDK. Programprincipen kan inte tillämpas på de här apparna.

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>Zebra-enheter med Zebra Mobility Extensions

Intune använder verktyget Zebra Mobility Extensions (MX) för att obevakat installera appar på Zebra-enheter som hanteras av enhetsadministratören. Med den här funktionen kan du distribuera och uppdatera appar på Zebra-enheter utan åtgärd av användaren. Om MX-versionen på din enhet är 4.2 eller äldre installeras inte appar obevakat. Mer information finns i [den fullständiga MX-funktionsmatrisen](http://techdocs.zebra.com/mx/compatibility/) på Zebras webbplats.

LOB-appar som distribuerats till Zebra-enheter måste installeras från en offentlig plats på enheten. .apk-appaketet kan vara tillgängligt för andra appar och tjänster som också har åtkomst till offentlig lagring på enheten. Den här åtkomsten är normalt ett litet fönster mellan att appen har laddats ned och installationen påbörjas. Det här fönstret kan möjliggöra en tidsattack. Till exempel kan ett .apk-paket ändras i det här fönstret. Intune minimerar hur mycket tid som .apk-filen finns i offentlig lagring och tillåter inte att osignerade appar installeras. Du kan minimera säkerhetsrisken genom att se till att .apk-filerna du laddar upp inte innehåller känslig information.

## <a name="see-also"></a>Se även

[Lägga till appar med Microsoft Intune](../apps/apps-add.md)

[Så får dina iOS/iPadOS-användare sina appar](end-user-apps-ios.md)

[Så får dina Windows-användare sina appar](end-user-apps-windows.md)
