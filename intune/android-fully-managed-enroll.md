---
title: Konfigurera Intune-registrering för fullständigt hanterade Android-enheter
titlesuffix: Microsoft Intune
description: Läs hur du registrerar fullständigt hanterade Android-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: d457ca413f3069e8528dc6f4951f834e3f1dac6a
ms.sourcegitcommit: 2a1720184cec577684a64af85d0d731693d11d81
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/28/2019
ms.locfileid: "55146918"
---
# <a name="set-up-intune-enrollment-of-android-fully-managed-devices-preview"></a>Konfigurera Intune-registrering för fullständigt hanterade Android-enheter (förhandsversion)

Fullständigt hanterade Android-enheter är företagsägda enheter som är associerade med en enskild användare och som används endast för arbete och inte för personligt bruk. Administratörer kan hantera hela enheten och tillämpa principkontroller som inte är tillgängliga för arbetsprofiler, till exempel dessa:
- endast tillåta appinstallation från hanterad Google Play
- blockera avinstallation av hanterade appar
- förhindra att användare återställer enheter till fabriksinställningar och så vidare.

Intune hjälper dig att distribuera appar och inställningar till Android enterprise-enheter, inklusive fullständigt hanterade Android-enheter. Specifik information om Android enterprise finns i [Krav för Android enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="technical-requirements"></a>Tekniska krav

Du måste ha en fristående Intune-klient för att hantera fullständigt hanterade Android-enheter. Hantering med fullständigt hanterade enheter är inte tillgängligt i hybridläge (SCCM-anslutet) eller i den äldre hanteringskonsolen Silverlight.

Enheter måste uppfylla dessa krav för att kunna hanteras som en fullständigt hanterad Android-enhet:

- Android OS version 5.1 och senare.
- Enheter måste köra en version av Android som har anslutningsfunktioner för Google Mobile Services (GMS). Enheter måste ha GMS tillgängligt för att kunna ansluta till GMS.

Det finns ingen begränsning på enhetstillverkare/OEM om ovanstående krav är uppfyllda.

## <a name="set-up-android-fully-managed-device-management"></a>Konfigurera hantering av fullständigt hanterade Android-enheter

Du kan konfigurera hanteringen av fullständigt hanterade Android-enheter så här:

1. Förbered hantering av mobila enheter genom att [ange MDM-utfärdare som **Microsoft Intune**](mdm-authority-set.md). Du anger det här objektet bara när du konfigurerar Intune för hantering av mobila enheter.
2. [Anslut ditt Intune-klientkonto till ditt Android enterprise-konto](connect-intune-android-enterprise.md).
3. [Aktivera företagsägda användarenheter](#enable-corporate-owned-user-devices)
4. [Registrera fullständigt hanterade enheter](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Aktivera företagsägda användarenheter

1. Gå till [Intune-portalen](https://portal.azure.com) och välj **Enhetsregistrering** > **Android-registrering** > **Företagsägda, fullständigt hanterade användarenheter (förhandsversion)**.
2. Välj **Ja** under **Låt användarna registrera företagsägda användarenheter** .

När den här inställningen anges till **Ja** får du en token för programregistrering (en slumpmässig sträng) och en QR-kod för din Intune-klient. Den här enda registreringstoken är giltig för alla användare och förfaller inte. Beroende på enhetens Android OS-version kan du använda token eller QR-koden för att registrera kioskenheten.

## <a name="enroll-the-fully-managed-devices"></a>Registrera fullständigt hanterade enheter
Du kan nu [registrera dina fullständigt hanterade enheter](android-dedicated-devices-fully-managed-enroll.md).

## <a name="considerations-for-this-preview-feature"></a>Överväganden för den här förhandsversionen
Den här offentliga förhandsversionen innehåller en uppsättning grundläggande funktioner för den fullständigt hanterade Android-lösningen. Vi vill gärna höra om din upplevelse av funktionerna i förhandsversionen via någon av dina aktuella kommunikationskanaler till teamet (t.ex. [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853)).

Den här förhandsversionen har stöd för följande funktioner för fullständigt hanterade Android-enheter:
- enhetsregistrering med hjälp av NFC, inmatning av token, QR-kod och Zero Touch
- enhetskonfiguration för användargrupper
- appdistribution och konfiguration av användargrupper


Tänk på följande när du använder den här förhandsversionen:
- Funktioner i förhandsversioner bör inte användas i verksamhetskritiska eller produktionsmässig distribution. 
- Förhandsfunktioner implementeras i Microsoft Intune-produktionsstandarder. Men alla Intune-funktioner är inte tillgängliga för användning med fullständigt hanterade Android-användarenheter. Förhandsversionsfunktioner är tydligt märkta med ”(förhandsversion)” i Intune-konsolen. 
- För förhandsfunktionerna lämnas full support via de vanliga Intune-supportkanalerna.
- Det är inte möjligt att registrera fullständigt hanterade Android-enheter i förhandsversionen med hjälp av Samsung Knox Mobile Enrollment. 
- Användning av appen Intune-företagsportal stöds inte på fullständigt hanterade Android-enheter. 
- Intune-funktioner som Villkorlig åtkomst, appskyddsprinciper och certifikatdistribution stöds inte i förhandsversionen. 
- I förhandsversionen är det inte möjligt att ange enhetsgrupp som mål för en profil eller app. Endast användargrupper kan anges som mål. 
- Det finns inget förstklassigt användargränssnitt för att konfigurera e-post, Wi-Fi eller VPN. Använd appkonfigurationsprinciper för att konfigurera inställningar för program som stöds.

## <a name="next-steps"></a>Nästa steg
- [Lägga till konfiguration för fullständigt hanterade Android-enheter](device-restrictions-android-for-work.md#device-owner-only)
- [Konfigurera till appkonfigurationsprinciper för fullständigt hanterade Android-enheter](app-configuration-policies-use-android.md)

