---
title: Konfigurera Pradeo-integreringen med Intune
titleSuffix: Intune on Azure
description: Integrering av Pradeo-anslutningsapp med Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 82872ba6-80f8-4cc9-adf4-0ccd8ff26dd2
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbe996565291d2aaf280de0612480b879b3e5d29
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57398145"
---
# <a name="integrate-pradeo-with-intune"></a>Integrera Pradeo med Intune

Slutför följande steg för att integrera Pradeo Mobile Threat Defense-lösningen med Intune.

## <a name="before-you-begin"></a>Innan du börjar

> [!NOTE]
> Följande steg ska utföras i [Pradeo Security-konsolen](https://www.apps-security.com).

Kontrollera att du har följande innan du börjar integrera Pradeo med Intune:

-   Microsoft Intune-prenumeration

-   Azure Active Directory-administratörsautentiseringsuppgifter som beviljar följande behörigheter:

    -   Logga in och läsa användarprofil

    -   Gå till katalogen som den inloggade användaren

    -   Läs katalogdata

    -   Skicka enhetsinformation till Intune

-   Autentiseringsuppgifter som administratör för att få åtkomst till Pradeo Security-konsolen.

### <a name="pradeo-app-authorization"></a>Pradeo-appauktorisering

Processen för Pradeo-appauktorisering består av följande:

-   Tillåt att Pradeo-tjänsten förmedlar information om enhetens hälsostatus till Intune.

-   Pradeo synkroniserar med Azure AD-registreringsgruppmedlemskap för att fylla enhetens databas.

-   Tillåt att Pradeo-administratörskonsolen använder enkel inloggning för Azure AD.

-   Tillåt att Pradeo-appen loggar in med enkel inloggning för Azure AD.

## <a name="to-set-up-pradeo-integration"></a>Så konfigurerar du Pradeo-integrering

1.  Gå till [Pradeo Security-konsolen](https://www.apps-security.com) och logga in med dina autentiseringsuppgifter.

2.  Välj **Administration - Enterprise Mobility Management** (Administration – mobilitetshantering i företaget) på menyn.

3.  Välj **Intune-logotypen**.

4.  I fönstret **EMM (Enterprise mobility management) - Intune** (Mobilitetshantering i företaget) väljer du under **Step 1** (Steg 1) knappen **Pradeo Connector** (Pradeo-anslutningsapp). 

    ![Skärmbild av fönstret Pradeo EMM Intune](./media/pradeo_setup.png)

5. I Microsoft Intune-anslutningsfönstret anger du dina autentiseringsuppgifter för Intune.

5.  Pradeo-webbplatsen öppnas igen. Under **Step 2** (Steg 2) väljer du knappen **Pradeo Device Health** (Hälsotillstånd för Pradeo-enhet).

7. I fönstret Pradeo Intune Connector (Pradeo Intune-anslutningsapp) väljer du **Accept** (Acceptera). 

8. I fönstret för API-anslutningsapp för Pradeo-enhet väljer du **Accept** (Acceptera).

9. Pradeo-webbplatsen öppnas igen. Under **Step 3** (Steg 3) väljer du knappen **Connect to Microsoft** (Anslut till Microsoft). 

10. I Microsoft Intune-autentiseringsfönstret anger du dina autentiseringsuppgifter för Intune.

11. När meddelandet **Successful Integration** (Integrering klar) visas är integreringen slutförd.

## <a name="next-steps"></a>Nästa steg

-   [Konfigurera Pradeo-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)
