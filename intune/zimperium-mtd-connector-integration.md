---
title: Integrera Zimperium MTD med Microsoft Intune
titleSuffix: Microsoft Intune
description: Konfigurera Zimperium Mobile Threat Defense (MTD) med Microsoft Intune för att styra mobila enheters åtkomst till företagsresurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db7f008e67c0523a373da24dd0a04f3556d9dd4c
ms.sourcegitcommit: 119962948045079022aa48f968dde3e961d7cd0c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031387"
---
# <a name="integrate-zimperium-with-intune"></a>Integrera Zimperium med Intune

Slutför följande steg för att integrera Zimperium Mobile Threat Defense-lösningen med Intune.

## <a name="before-you-begin"></a>Innan du börjar

> [!NOTE]
> Följande steg ska utföras i  [Zimperiums MTD-konsol](https://www.zimperium.com/platform).

Kontrollera att du har följande prenumeration och autentiseringsuppgifter innan du börjar integrera Zimperium med Intune:

-   Microsoft Intune-prenumeration

-   Azure Active Directory-autentiseringsuppgifter för global administratör beviljar följande behörigheter:

    -   Logga in och läsa användarprofil

    -   Gå till katalogen som den inloggade användaren

    -   Läs katalogdata

    -   Skicka enhetsinformation till Intune

-   Autentiseringsuppgifter som administratör för att få åtkomst till Zimperium MTD-konsolen.

### <a name="zimperium-app-authorization"></a>Zimperium-appauktorisering

Processen för Zimperium-appauktorisering består av följande:

-   Ge behörighet för Zimperium-tjänsten att förmedla information om enhetens hälsotillstånd tillbaka till Intune. Du måste använda autentiseringsuppgifter för global administratör för att kunna bevilja dessa behörigheter. Att bevilja behörigheter är en engångsåtgärd. När behörigheterna har beviljats behövs inte autentiseringsuppgifterna för global administratör i den dagliga verksamheten.

-   Zimperium fyller enhetens databas genom att synkronisera med Azure Active Directory-registreringsgruppmedlemskap.

-   Tillåt att Zimperium-administratörskonsolen använder enkel inloggning för Azure AD.

-   Tillåt att Zimperium-appen loggar in med enkel inloggning för Azure AD.

Mer information om medgivande och Azure Active Directory-program finns i [Begär behörighet från en katalogadministratör](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin) i Azure Active Directory-artikeln *Behörighet och medgivande i Azure Active Directory v2.0-slutpunkten*.


## <a name="to-set-up-zimperium-integration"></a>Konfigurera Zimperium-integration

1.  Gå till [Zimperium MTD-konsolen](https://www.zimperium.com/platform) och logga in med dina autentiseringsuppgifter. Om du vill konfigurera Zimperium-integration, måste du logga in som en Azure Active Directory-användare med en global administratörsroll. Denna engångsåtgärd använder den globala administratörsbehörigheten till att bevilja behörighet i din organisation för Zimperium-appar som ska kommunicera med Intune. 

2.  Välj **Hantering** på den vänstra menyn.

3.  Välj fliken **MDM-inställningar**.

4.  Välj **Lägg till MDM** och välj sedan **Microsoft Intune** från listan **MDM-provider**.

5.  När du har angett Microsoft Intune som MDM-tjänst öppnas fönstret **Microsoft Intune-konfiguration**. Välj **Lägg till Azure Active Directory** för varje alternativ: **Zimperium zConsole**, **zIPS iOS- och Android-appar** för att ge Zimperium behörighet att kommunicera med Intune och Azure AD via enkel inloggning i Azure AD.

    > [!IMPORTANT]  
    > Du måste lägga till Zimperium zConsole, zIPS iOS- och Android-appar för att slutföra integreringsprocessen med Intune.

6.  Välj **Acceptera** för att ge Zimperium-appen tillstånd att kommunicera med Intune och Azure Active Directory.

7.  När du har lagt till **Zimperium zConsole** samt **zIPS iOS- och Android**-appar i Azure AD, lägger du till Azure AD-säkerhetsgrupper. Det gör att Zimperium kan synkronisera Azure AD-säkerhetsgruppen med sin tjänst.

8.  Välj **Slutför** för att spara konfigurationen och starta den första synkroniseringen för Azure AD-säkerhetsgruppen.

9.  Logga ut från Zimperium MTD-konsolen.

## <a name="next-steps"></a>Nästa steg

-   [Konfigurera Zimperium-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)
