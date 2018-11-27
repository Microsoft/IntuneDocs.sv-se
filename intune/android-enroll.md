---
title: Registrera Android-enheter i Intune
titlesuffix: Microsoft Intune
description: Läs hur du registrerar Android-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2b2b3ba5443cd95cd81bdca6d386ab95a2c831eb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190123"
---
# <a name="enroll-android-devices"></a>Registrera Android-enheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du kan hantera följande Android-enheter som Intune-administratör:
- Android-enheter, inklusive Samsung Knox Standard-enheter.
- Android enterprise-enheter, inklusive [Android-arbetsprofilenheter](#enable-enrollment-of-android-for-work-devices) och Android-kioskenheter.

Enheter som kör Samsung Knox Standard har stöd för hantering av flera användare med Intune. Det innebär att användarna kan logga in och ut ur enheten med sina autentiseringsuppgifter för Azure AD. Enheten är centralt hanterad oavsett om den används eller inte. När användare loggar in får de tillgång till appar och eventuella principer tillämpas på dem. Alla appdata rensas när användaren loggar ut.

## <a name="prerequisite"></a>Krav

Förbered hantering av mobila enheter genom att ange MDM-utfärdare som **Microsoft Intune**. Fler anvisningar finns i [Ange MDM-utfärdare](mdm-authority-set.md). Du anger det här objektet bara när du konfigurerar Intune för hantering av mobila enheter.

## <a name="set-up-android-enrollment"></a>Konfigurera Android-registrering

Som standard tillåter Intune registrering av Android- och Samsung Knox Standard-enheter. När förutsättningarna är uppfyllda behöver administratörerna bara [berätta för användarna hur de registrerar sina enheter](/intune-user-help/enroll-your-device-in-intune-android).

När en användare har registrerat sig kan du börja hantera användarens enheter i Intune, inklusive [tilldela efterlevnadsprinciper](compliance-policy-create-android.md), [hantera appar](app-management.md) med mera.

Information om andra användaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](end-user-educate.md)
- [Använda en Android-enhet med Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Se [Ange begränsningar för enhetstyp](enrollment-restrictions-set.md) för att blockera Android-enheter eller endast blockera personligt ägda Android-enheter från registrering.

## <a name="set-up-android-enterprise-enrollment"></a>Konfigurera Android enterprise-registrering

Android enterprise är en uppsättning funktioner och tjänster för Android-enheter som avgränsar personliga appar och data från en arbetsprofil som innehåller arbetsappar och data. Android enterprise-enheter omfattar arbetsprofilenheter och kioskenheter. 

Om du vill konfigurera registrering för Android enterprise-enheter måste först [ansluta Android enterprise till Intune](connect-intune-android-enterprise.md). När du har slutfört det här steget kan du:

[Konfigurera Android-arbetsprofilregistreringar](android-work-profile-enroll.md)
[Konfigurera Android-kioskregistreringar](android-kiosk-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Slutanvändarens upplevelse när en Samsung Knox-enhet registreras
Det finns flera saker att tänka på vid registrering av Samsung Knox-enheter:
-   Även om inga principer kräver en PIN-kod, måste enheten ha en PIN-kod på minst fyra siffror för att kunna registreras. Om enheten inte har någon PIN-kod, uppmanas användaren att skapa en.
-   Det finns inga användaråtgärder för Workplace Join-certifikat (WPJ).
-   Användaren får information om tjänstregistreringen och om vad appen kan göra.
-   Användaren får information om Knox-registreringen och om vad Knox kan göra.
-   Om en krypteringsprincip tillämpas måste användarna ange ett avancerat lösenord på sex tecken som enhetens lösenord.
-   Det finns inga ytterligare användaruppmaningar att installera certifikat från en tjänst för åtkomst till företagsresurser.
- Vissa äldre Knox-enheter uppmanar användaren om ytterligare certifikat som används för åtkomst till företagsresurser.
- Om en Samsung Mini-enhet inte kan installera WPJ och får felet **Det gick inte att hitta certifikatet** eller **Det gick inte att registrera enheten**, installerar du de senaste uppdateringarna för inbyggd Samsung-programvara.
