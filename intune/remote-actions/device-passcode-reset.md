---
title: Återställa enhetslösenord med Microsoft Intune – Azure | Microsoft Docs
description: Ta bort eller återställ lösenordet med åtgärden Ta bort lösenkod på enheter som du hanterar eller övervakar med Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd6e58efa096c006780c17d991a9ea5da26099d4
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415550"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Återställa eller ta bort ett enhetslösenord i Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Det här dokumentet beskriver återställning av lösenord på såväl enhets- som arbetsprofilnivå för Android Enterprise-enheter (tidigare kallat Android for Work eller AfW). Det är viktigt att notera denna skillnad eftersom detta kan medföra olika krav. En lösenordsåterställning på enhetsnivå återställer lösenordet för hela enheten. Återställning av lösenordet för en arbetsprofil återställer endast lösenordet för den användarens arbetsprofil på enheter med Android Enterprise.

## <a name="supported-platforms-for-device-level-passcode-reset"></a>Plattformar som stöder lösenordsåterställning på enhetsnivå

| Plattform | Stöds? |
| ---- | ---- |
| Android-enheter på version 6.x eller tidigare | Ja |
| Android Enterprise-enheter registrerade som enhetsägare | Ja |
| iOS-/iPadOS-enheter | Ja |
| iOS/iPadOS-enheter som registrerats med användarregistrering | Nej |
| Android-enheter som registrerats med en arbetsprofil | Nej |
| Android-enheter på version 7.0 eller senare | Nej |
| macOS | Nej |
| Windows | Nej |

För Android-enheter innebär detta i praktiken att lösenordsåterställning på enhetsnivå endast stöds på enheter med 6.x eller tidigare, eller Android Enterprise-enheter som körs i helskärmsläge. Detta beror på att Google inte längre stöder återställning av lösenord för Android 7-enheter från en app med enhetsadministratör vilket gäller för alla MDM-leverantörer.

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Plattformar som stöds lösenordsåterställning för Android Enterprise, arbetsprofil

| Plattform | Stöds? |
| ---- | ---- |
| Android Enterprise-enheter som registrerats med en arbetsprofil, version 8.0 och senare | Ja |
| Android Enterprise-enheter som registrerats med en arbetsprofil, version 7.x och tidigare | Nej |
| Android-enheter som kör version 7.x och tidigare | Nej |

Använd åtgärden återställ lösenord för att skapa ett nytt lösenord för arbetsprofilen. Den här åtgärden återställer lösenordet och skapar ett nytt, tillfälligt lösenord som endast gäller för arbetsprofilen. 

## <a name="reset-a-passcode"></a>Återställa ett lösenord


1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) med någon av följande roller: Global Azure Active Directory-administratör, Azure Active Directory Intune-tjänsteadministratör, supportoperatör eller rolladministratör.
2. Välj **Enheter** och sedan **Alla enheter**.
3. Välj en enhet från listan över enheter du hanterar och välj **...Mer**. Välj sedan fjärråtgärden **Ta bort lösenkod** för enheten.

## <a name="reset-android-work-profile-passcodes"></a>Återställa lösenord för Android-arbetsprofiler

Android Enterprise-arbetsprofilenheter som stöds får ett nytt lösenord för att låsa upp hanterade profiler, eller en kontrollfråga för hanterade profiler för slutanvändaren.

För Android Enterprise-enheter som kör version 8.x eller senare och som har registrerats med en arbetsprofil informeras slutanvändarna att de ska aktivera det återställa lösenordet när registreringen har slutförts. Meddelandet visas om ett lösenord för arbetsprofilen krävs och har ställts in. När de har angett lösenordet tas meddelandet bort.


## <a name="remove-iosipados-passcodes"></a>Ta bort iOS/iPadOS-lösenord

Lösenord tas bort från iOS/iPadOS-enheter istället för att återställas. Om en efterlevnadsprincip för lösenord har angetts uppmanar enheten användaren att ange ett nytt lösenord i inställningarna.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du nyss vidtog väljer du **Enhetsåtgärder** i **Enheter**.
