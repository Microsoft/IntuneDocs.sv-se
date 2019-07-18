---
title: Konfigurera Intune-registrering för fullständigt hanterade Android Enterprise-enheter
titleSuffix: Microsoft Intune
description: Lär dig hur du registrerar fullständigt hanterade Android Enterprise-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 54d9fa1016ff39fcf1e7da9c21391ce70f7acaac
ms.sourcegitcommit: e451295ca3ee3efc31bf9ee360e599b28ef643ea
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/12/2019
ms.locfileid: "67863087"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices-preview"></a>Konfigurera Intune-registrering av fullständigt hanterade Android Enterprise-enheter (förhandsversion)

Fullständigt hanterade Android Enterprise-enheter är företagsägda enheter som är associerade med en enskild användare och som endast används för arbete och inte för personligt bruk. Administratörer kan hantera hela enheten och tillämpa principkontroller som inte är tillgängliga för arbetsprofiler, till exempel dessa:
- Tillåt endast appinstallation från hanterad Google Play.
- Blockera avinstallation av hanterade appar.
- Förhindra att användare återställer enheter till fabriksinställningar och så vidare.

Intune hjälper dig att distribuera appar och inställningar till Android Enterprise-enheter, däribland fullständigt hanterade Android Enterprise-enheter. Specifik information om Android Enterprise finns i [Krav för Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="technical-requirements"></a>Tekniska krav

Du måste ha en fristående Intune-klientorganisation för att hantera fullständigt hanterade Android Enterprise-enheter. Hantering av fullständigt hanterade enheter är inte tillgängligt i hybridläge (Configuration Manager-anslutet) eller i den äldre Silverlight-hanteringskonsolen.

Enheter måste uppfylla dessa krav för att kunna hanteras som fullständigt hanterade Android Enterprise-enheter:

- Android OS version 5.1 och senare.
- Enheter måste köra en version av Android som har anslutningsfunktioner för Google Mobile Services (GMS). Enheter måste ha GMS tillgängligt för att kunna ansluta till GMS.

Det finns ingen begränsning på enhetstillverkare/OEM om ovanstående krav är uppfyllda.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Konfigurera hantering av fullständigt hanterade Android Enterprise-enheter

För de här stegen om du vill konfigurera hanteringen av fullständigt hanterade Android Enterprise-enheter:

1. Förbered hantering av mobila enheter genom att [ange MDM-utfärdare som **Microsoft Intune**](mdm-authority-set.md). Du anger det här objektet bara när du konfigurerar Intune för hantering av mobila enheter.
2. [Anslut ditt Intune-klientorganisationskonto till ditt Android Enterprise-konto](connect-intune-android-enterprise.md).
3. [Aktivera företagsägda användarenheter](#enable-corporate-owned-user-devices)
4. [Registrera fullständigt hanterade enheter](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Aktivera företagsägda användarenheter

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välj **Enhetsregistrering** > **Android-registrering** > **Företagsägda, fullständigt hanterade användarenheter (förhandsversion)** .
2. Välj **Ja** under **Låt användarna registrera företagsägda användarenheter** .

> [!NOTE]
> Om du har definierat en princip för villkorlig åtkomst för Azure AD som använder kontrollen *Kräv att enheten är markerad som kompatibel* och gäller för **alla molnappar**, **Android** och **webbläsare** måste du utesluta **Microsoft Intune**-molnappen från den här principen. Det beror på att Android-konfigureringsprocesser använder en Chrome-flik för att autentisera användarna under registreringen. Se [dokumentationen om villkorlig åtkomst till Azure AD](https://docs.microsoft.com/azure/active-directory/conditional-access/) för mer information.

När den här inställningen anges till **Ja** får du en token för programregistrering (en slumpmässig sträng) och en QR-kod för din Intune-klient. Den här enda registreringstoken är giltig för alla användare och förfaller inte. Beroende på enhetens Android OS-version kan du använda token eller QR-koden för att registrera kioskenheten.

## <a name="enroll-the-fully-managed-devices"></a>Registrera fullständigt hanterade enheter
Du kan nu [registrera dina fullständigt hanterade enheter](android-dedicated-devices-fully-managed-enroll.md).

## <a name="considerations-for-this-preview-feature"></a>Överväganden för den här förhandsversionen
Den här offentliga förhandsversionen innehåller en uppsättning grundläggande funktioner för den fullständigt hanterade Android Enterprise-lösningen. Vi vill gärna höra om din upplevelse av funktionerna i förhandsversionen via någon av dina aktuella kommunikationskanaler till teamet (t.ex. [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853)).

Den här förhandsversionen har stöd för följande funktioner för fullständigt hanterade Android Enterprise-enheter:
- enhetsregistrering med hjälp av NFC, inmatning av token, QR-kod och Zero Touch
- enhetskonfiguration för användargrupper
- appdistribution och konfiguration av användargrupper


Tänk på följande när du använder den här förhandsversionen:
- Funktioner i förhandsversioner bör inte användas i verksamhetskritiska eller produktionsmässig distribution. 
- Förhandsfunktioner implementeras i Microsoft Intune-produktionsstandarder. Dock är inte alla Intune-funktioner tillgängliga för användning med fullständigt hanterade Android Enterprise-användarenheter. Förhandsversionsfunktioner är tydligt märkta med ”(förhandsversion)” i Intune-konsolen. 
- För förhandsfunktionerna lämnas full support via de vanliga Intune-supportkanalerna.
- Det är inte möjligt att registrera fullständigt hanterade Android Enterprise-enheter i förhandsversionen med hjälp av Samsung Knox Mobile Enrollment. 
- Användning av appen Intune-företagsportal stöds inte på fullständigt hanterade Android Enterprise-enheter. 
- Intune-funktioner som Villkorlig åtkomst, appskyddsprinciper och certifikatdistribution stöds inte i förhandsversionen. 
- I förhandsversionen är det inte möjligt att ange enhetsgrupp som mål för en profil eller app. Endast användargrupper kan anges som mål. 
- Det finns inget förstklassigt användargränssnitt för att konfigurera e-post, Wi-Fi eller VPN. Använd appkonfigurationsprinciper för att konfigurera inställningar för program som stöds.

## <a name="next-steps"></a>Nästa steg
- [Lägga till konfigurationsprinciper för fullständigt hanterade Android Enterprise-enheter](device-restrictions-android-for-work.md#device-owner-only)
- [Konfigurera appkonfigurationsprinciper för fullständigt hanterade Android Enterprise-enheter](app-configuration-policies-use-android.md)

