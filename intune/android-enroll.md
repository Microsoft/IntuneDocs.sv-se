---
title: Registrera Android-enheter i Intune
titleSuffix: Microsoft Intune
description: Läs hur du registrerar Android-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/31/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 363a7d0ef32aee0c21c6e5cecbd55cc3087f4613
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568680"
---
# <a name="enroll-android-devices"></a>Registrera Android-enheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du kan hantera följande Android-enheter som Intune-administratör:
- Android-enheter, inklusive Samsung Knox Standard-enheter.
- Android Enterprise-enheter, inklusive:
    - **Android Enterprise-arbetsprofilenheter**: Personliga enheter ges åtkomst till företagets data. Administratörer kan hantera arbetskonton, appar och data. Personliga data på enheten lagras separat från arbetsdata och administratörer har ingen kontroll över personliga inställningar eller data. 
    - **Dedikerade Android Enterprise-enheter**: Företagsägda enheter med ett enda användningsområde, till exempel digital signering, biljettutskrift eller lagerhantering. Administratörer låser användningen av enheten för en begränsad uppsättning appar och webblänkar. Användarna kan heller inte lägga till andra appar eller att vidta andra åtgärder på enheten.
    - **Fullständigt hanterade Android Enterprise-enheter**: Företagsägda enheter med enskilda användare används enbart för arbete och inte för personligt bruk. Administratörer kan hantera hela enheten och tillämpa principkontroller som inte är tillgängliga för arbetsprofiler. 

## <a name="prerequisite"></a>Krav

Förbered hantering av mobila enheter genom att ange MDM-utfärdare som **Microsoft Intune**. Fler anvisningar finns i [Ange MDM-utfärdare](mdm-authority-set.md). Du anger det här objektet bara när du konfigurerar Intune för hantering av mobila enheter.

## <a name="set-up-android-enrollment"></a>Konfigurera Android-registrering

Som standard tillåter Intune registrering av Android- och Samsung Knox Standard-enheter. När förutsättningarna är uppfyllda behöver administratörerna bara [berätta för användarna hur de registrerar sina enheter](/intune-user-help/enroll-your-device-in-intune-android).

När en användare har registrerat sig kan du börja hantera användarens enheter i Intune, inklusive [tilldela efterlevnadsprinciper](compliance-policy-create-android.md), [hantera appar](app-management.md) med mera.

Information om andra användaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](end-user-educate.md)
- [Använda en Android-enhet med Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Se [Ange begränsningar för enhetstyp](enrollment-restrictions-set.md) för att blockera Android-enheter eller endast blockera personligt ägda Android-enheter från registrering.

## <a name="set-up-android-enterprise-enrollment"></a>Konfigurera Android Enterprise-registrering

Android Enterprise erbjuder en uppsättning registreringsalternativ som ger användarna de mest aktuella och säkra funktionerna. Bland alternativen för Android Enterprise-registrering finns arbetsprofilenheter, fullständigt hanterade enheter och dedikerade enheter.

- [Konfigurera registrering av Android Enterprise-arbetsprofiler](android-work-profile-enroll.md)
- [Konfigurera registrering av dedikerade Android Enterprise-enheter](android-kiosk-enroll.md)
- [Konfigurera registrering av fullständigt hanterade Android Enterprise-registreringar](android-fully-managed-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Slutanvändarens upplevelse när en Samsung Knox-enhet registreras

Samsung Knox Standard-enheter har stöd för hantering av flera användare med Intune. Det innebär att användarna kan logga in och ut ur enheten med sina autentiseringsuppgifter för Azure AD. Enheten är centralt hanterad oavsett om den används eller inte. När användare loggar in får de tillgång till appar och eventuella principer tillämpas på dem. Alla appdata rensas när användaren loggar ut.

Det finns flera saker att tänka på vid registrering av Samsung Knox-enheter:
-   Även om inga principer kräver en PIN-kod, måste enheten ha en PIN-kod på minst fyra siffror för att kunna registreras. Om enheten inte har någon PIN-kod, uppmanas användaren att skapa en.
-   Det finns inga användaråtgärder för Workplace Join-certifikat (WPJ).
-   Användaren får information om tjänstregistreringen och om vad appen kan göra.
-   Användaren får information om Knox-registreringen och om vad Knox kan göra.
-   Om en krypteringsprincip tillämpas måste användarna ange ett avancerat lösenord på sex tecken som enhetens lösenord.
-   Det finns inga ytterligare användaruppmaningar att installera certifikat från en tjänst för åtkomst till företagsresurser.
- Vissa äldre Knox-enheter uppmanar användaren om ytterligare certifikat som används för åtkomst till företagsresurser.
- Om en Samsung Mini-enhet inte kan installera WPJ och får felet **Det gick inte att hitta certifikatet** eller **Det gick inte att registrera enheten**, installerar du de senaste uppdateringarna för inbyggd Samsung-programvara.

## <a name="next-steps"></a>Nästa steg

- [Konfigurera registrering av Android Enterprise-arbetsprofiler](android-work-profile-enroll.md)
- [Konfigurera registrering av dedikerade Android Enterprise-enheter](android-kiosk-enroll.md)
- [Konfigurera registrering av fullständigt hanterade Android Enterprise-registreringar](android-fully-managed-enroll.md)
