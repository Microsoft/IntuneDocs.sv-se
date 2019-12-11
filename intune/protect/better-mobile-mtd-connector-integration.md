---
title: Konfigurera Better Mobile-integrering med Intune
titleSuffix: Intune on Azure
description: Integrera Better Mobile-anslutningsprogrammet med Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0528ec962165f358b35afce98f58c8b9b4efe93c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72810318"
---
# <a name="integrate-better-mobile-with-intune"></a>Integrera Better Mobile med Intune

Utför följande steg när du ska integrera Better Mobile Threat Defense-lösningen med Intune.

## <a name="before-you-begin"></a>Innan du börjar

Följande steg måste utföras i [Better Mobile-administratörskonsolen](https://aad.bmobi.net) och gör det möjligt att ansluta Better Mobile-tjänsten för både Intune-registrerade enheter (via enhetsefterlevnad) och oregistrerade enheter (via appskyddsprinciper).

Se till att du har följande innan du börjar integrera Better Mobile med Intune:

- Microsoft Intune-prenumeration

- Azure Active Directory-administratörsautentiseringsuppgifter som beviljar följande behörigheter:

  - Logga in och läsa användarprofil

  - Gå till katalogen som den inloggade användaren

  - Läs katalogdata

  - Skicka enhetsinformation till Intune

- Administratörsinloggning för åtkomst till administratörskonsolen för Better Mobile.

### <a name="better-mobile-app-authorization"></a>Behörighetskontroll av Better Mobile-appen

Det här är processen för behörighetskontroll av Better Mobile-appen:

- Tillåt att Better Mobile-tjänsten förmedlar information om enhetens hälsostatus till Intune.

- Better Mobile fyller enhetens databas genom att synkronisera med registreringsgruppmedlemskapet i Azure AD.

- Tillåt att Better Mobile-administratörskonsolen använder enkel inloggning för Azure AD.

- Tillåt att Better Mobile-appen loggar in med enkel inloggning för Azure AD.

## <a name="to-set-up-better-mobile-integration"></a>Konfigurera Better Mobile-integreringen

1. Öppna [administratörskonsolen för Better Mobile](https://aad.bmobi.net) och logga in med dina autentiseringsuppgifter.
2. Välj **Integrering** > **EMM/MDM** > **LÄGG TILL KONTO**.

     ![Bild av administratörskonsolen för Better Mobile](./media/better-mobile-mtd-connector-integration/better_mobile_console.png)
 
3. Välj **Intune**.
4. Bredvid **KONTONAMN** skriver du en beskrivning. 
5. I fönstret för **Microsoft-inloggning** anger du dina inloggningsuppgifter för Intune.
6. I fönstret **Begärda behörigheter** väljer du **Godkänn**.
7. Sök efter de Azure AD-säkerhetsgrupper du vill att Better Mobile ska synkronisera enheter med och välj dem i listan. Välj sedan **Fortsätt**.
8. Välj **Klar**.
9. Sidan **Lägg till konto** visas igen. Stäng sidan. 

## <a name="next-steps"></a>Nästa steg

- [Konfigurera Better Mobile-appar för registrerade enheter](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Konfigurera Better Mobile-appar för oregistrerade enheter](~/protect/mtd-add-apps-unenrolled-devices.md)
