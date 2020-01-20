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
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d8397dea1dca97122aac6716ee3d51295b913538
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885944"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices"></a>Konfigurera Intune-registrering av fullständigt hanterade Android Enterprise-enheter 

Fullständigt hanterade Android Enterprise-enheter är företagsägda enheter som är associerade med en enskild användare och som endast används för arbete och inte för personligt bruk. Administratörer kan hantera hela enheten och tillämpa principkontroller som inte är tillgängliga för arbetsprofiler, till exempel dessa:
- Tillåt endast appinstallation från hanterad Google Play.
- Blockera avinstallation av hanterade appar.
- Förhindra att användare återställer enheter till fabriksinställningar och så vidare.

Intune hjälper dig att distribuera appar och inställningar till Android Enterprise-enheter, däribland fullständigt hanterade Android Enterprise-enheter. Specifik information om Android Enterprise finns i [Krav för Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="technical-requirements"></a>Tekniska krav

Du måste ha en fristående Intune-klientorganisation för att hantera fullständigt hanterade Android Enterprise-enheter. Hantering av fullständigt hanterade enheter är inte tillgängligt i hybridläge (SCCM-anslutet) eller i den äldre hanteringskonsolen Silverlight.

Enheter måste uppfylla dessa krav för att kunna hanteras som fullständigt hanterade Android Enterprise-enheter:

- Android OS version 6.0 och senare.
- Enheter måste köra en version av Android som har anslutningsfunktioner för Google Mobile Services (GMS). Enheter måste ha GMS tillgängligt för att kunna ansluta till GMS.

Det finns ingen begränsning på enhetstillverkare/OEM om ovanstående krav är uppfyllda.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Konfigurera hantering av fullständigt hanterade Android Enterprise-enheter

För de här stegen om du vill konfigurera hanteringen av fullständigt hanterade Android Enterprise-enheter:

1. Förbered hantering av mobila enheter genom att [ange MDM-utfärdare som **Microsoft Intune**](../fundamentals/mdm-authority-set.md). Du anger det här objektet bara när du konfigurerar Intune för hantering av mobila enheter.
2. [Anslut ditt Intune-klientorganisationskonto till ditt Android Enterprise-konto](connect-intune-android-enterprise.md).
3. [Aktivera företagsägda användarenheter](#enable-corporate-owned-user-devices)
4. [Registrera fullständigt hanterade enheter](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Aktivera företagsägda användarenheter

1. Logga in på [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välj **Enheter** > **Android** > **Android-registrering**  > **Företagsägda fullständigt hanterade användarenheter**.
2. Välj **Ja** under **Låt användarna registrera företagsägda användarenheter** .

> [!NOTE]
> Om du har definierat en princip för villkorlig åtkomst för Azure AD som använder kontrollen *Kräv att enheten är markerad som kompatibel* och gäller för **alla molnappar**, **Android** och **webbläsare** måste du utesluta **Microsoft Intune**-molnappen från den här principen. Det beror på att Android-konfigureringsprocesser använder en Chrome-flik för att autentisera användarna under registreringen. Se [dokumentationen om villkorlig åtkomst till Azure AD](https://docs.microsoft.com/azure/active-directory/conditional-access/) för mer information.

När den här inställningen anges till **Ja** får du en token för programregistrering (en slumpmässig sträng) och en QR-kod för din Intune-klient. Den här enda registreringstoken är giltig för alla användare och förfaller inte. Beroende på enhetens Android OS-version kan du använda antingen token eller QR-koden för att registrera enheten.

## <a name="enroll-the-fully-managed-devices"></a>Registrera fullständigt hanterade enheter
Du kan nu [registrera dina fullständigt hanterade enheter](android-dedicated-devices-fully-managed-enroll.md).

## <a name="next-steps"></a>Nästa steg
- [Lägga till konfigurationsprinciper för fullständigt hanterade Android Enterprise-enheter](../configuration/device-restrictions-android-for-work.md#device-owner-only)
- [Konfigurera appkonfigurationsprinciper för fullständigt hanterade Android Enterprise-enheter](../apps/app-configuration-policies-use-android.md)

