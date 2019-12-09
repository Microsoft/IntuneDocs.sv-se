---
title: Administratörsregistrering för Android-enhet i Microsoft Intune
titleSuffix: ''
description: Registrera Android-enheter i Intune med hjälp av enhetsadministratörsregistrering.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 678eb92bb6f5f23756092cd5d9cc1a645e1e8db3
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74562360"
---
# <a name="android-device-administrator-enrollment"></a>Administratörsregistrering för Android-enhet

Enhetsadministratören för Andriod (kallas ibland för "äldre" Android-hantering och lanseras med Android 2.2) är ett sätt att hantera Android-enheter. Det finns dock en bättre hanteringsfunktion med [Android Enterprise](https://www.android.com/enterprise/management/) (lanseras med Android 5.0). För att kunna flytta till en modern, mer omfattande och säkrare enhetshantering,minskar Google stödet för enhetsadministration i nya versioner av Android.

För att undvika försämrad funktion avråder vi därför från att registrera nya enheter med enhetsadministratörsprocessen som beskrivs nedan.

Av samma skäl rekommenderar vi också att du migrerar enheter från enhetsadministratörshantering om enheterna ska uppdateras till Android 10. 

Mer information om Intune-support för stöd för Android-enhetsadministratörer finns i [området Meddelanden](../fundamentals/whats-new.md#decreasing-support-for-android-device-administrator).

Fortsätt till nästa avsnitt om du fortfarande vill att användarna ska registrera sina Android-enheter med enhetsadministratörshantering.  


> [!Note]  
> Android 10 och högre stöds inte i hybridhantering av mobila enheter (hybrid-MDM, Intune som hanteras med System Center Configuration Manager-konsolen) eftersom hybrid-MDM tas ur drift den 1 september 2019. Om du fortfarande använder hybrid-MDM bör du migrera till fristående Intune så snart som möjligt. Kontakta supporten om du behöver hjälp med att migrera. Mer information finns i [Flytt från hybridhantering av mobilenheter till Intune i Azure](https://aka.ms/hybrid_notification).

Mer information om Googles Android Enterprise-funktioner finns i följande artiklar:
- [Googles vägledning för migrering från enhetsadministratör till Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Googles dokumentation om planen för att ta enhetsadministratörs-API:et ur drift](https://developers.google.com/android/work/device-admin-deprecation)


## <a name="set-up-device-administrator-enrollment"></a>Ställ in administratörsregistrering

1. Förbered hantering av mobila enheter genom att ange MDM-utfärdare som **Microsoft Intune**. Fler anvisningar finns i [Ange MDM-utfärdare](../fundamentals/mdm-authority-set.md). Du anger det här objektet bara när du konfigurerar Intune för hantering av mobila enheter.
2. Logga in på [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välj > **Enheter** > **Android** > **Android-registrering** > **Personliga och företagsägda enheter med enhetsadministratörsbehörigheter** > **Hantera enheter med enhetsadministratören**.
3. [Berätta för dina användare hur de registrerar sina enheter](/intune-user-help/enroll-your-device-in-intune-android).  

När en användare har registrerat sig kan du börja hantera användarens enheter i Intune, inklusive [tilldela efterlevnadsprinciper](../protect/compliance-policy-create-android.md), [hantera appar](../apps/app-management.md) med mera.

Information om andra användaraktiviteter finns i de här artiklarna:
- [Resurser om slutanvändarupplevelsen med Microsoft Intune](../fundamentals/end-user-educate.md)
- [Använda en Android-enhet med Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)


## <a name="block-device-administrator-enrollment"></a>Blockera administratörsregistrering
Se [Ange begränsningar för enhetstyp](enrollment-restrictions-set.md) för att blockera Android-enheter eller endast blockera personligt ägda Android-enheter från registrering.



## <a name="next-steps"></a>Nästa steg
- [Efterlevnadsprinciper för enheter](../protect/compliance-policy-create-android.md)
- [Hantera appar](../apps/app-management.md)
