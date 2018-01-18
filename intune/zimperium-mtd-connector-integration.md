---
title: Integrera Zimperium med Intune
titleSuffix: Intune on Azure
description: Integrera Intune med Zimperium
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 515f99f694a9125d60bb9210becc6722bfb9e24f
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/30/2017
---
# <a name="integrate-zimperium-with-intune"></a>Integrera Zimperium med Intune

Slutför följande steg för att integrera Zimperium Mobile Threat Defense-lösningen med Intune.

## <a name="before-you-begin"></a>Innan du börjar

> [!NOTE]
> Följande steg ska utföras i [Zimperium MTD-konsolen](https://staging2-console.zimperium.com).

Kontrollera att du har följande innan du börjar integrera Zimperium med Intune:

-   Microsoft Intune-prenumeration

-   Azure Active Directory-administratörsautentiseringsuppgifter som beviljar följande behörigheter:

    -   Logga in och läsa användarprofil

    -   Gå till katalogen som den inloggade användaren

    -   Läs katalogdata

    -   Skicka enhetsinformation till Intune

-   Autentiseringsuppgifter som administratör för att få åtkomst till Zimperium MTD-konsolen.

### <a name="zimperium-app-authorization"></a>Zimperium-appauktorisering

Processen för Zimperium-appauktorisering består av följande:

-   Tillåt att Zimperium-tjänsten förmedlar information om enhetens hälsostatus till Intune.

-   Zimperium fyller enhetens databas genom att synkronisera med Azure AD-registreringsgruppmedlemskap.

-   Tillåt att Zimperium-administratörskonsolen använder enkel inloggning för Azure AD.

-   Tillåt att Zimperium-appen loggar in med enkel inloggning för Azure AD.

## <a name="to-set-up-zimperium-integration"></a>Konfigurera Zimperium-integration

1.  Gå till [Zimperium MTD-konsolen](https://staging2-console.zimperium.com) och logga in med dina autentiseringsuppgifter.

2.  Välj **Hantering** på den vänstra menyn.

3.  Välj fliken **MDM-inställningar**.

4.  Välj **Lägg till MDM** och välj sedan **Microsoft Intune** från listan **MDM-provider**.

5.  När du har ställt in Microsoft Intune som MDM-tjänst öppnas fönstret **Microsoft Intune-konfiguration** där du väljer **Lägg till Azure Active Directory** för varje alternativ: **Zimperium zConsole**, **zIPS iOS och Android-appar** för att ge Zimperium behörighet att kommunicera med Intune och Azure AD via enkel inloggning för Azure AD.

    > [!IMPORTANT]
    > Du måste lägga till Zimperium zConsole, zIPS iOS och Android-appar för att slutföra integreringsprocessen med Intune.

6.  Välj **Acceptera** för att ge Zimperium-appen tillstånd att kommunicera med Intune och Azure Active Directory.

7.  När du har lagt till **Zimperium zConsole** och **zIPS iOS och Android**-appar i Azure AD lägger du till Azure AD-säkerhetsgrupper så att Zimperium kan synkronisera Azure AD-säkerhetsgruppen med sin tjänst.

8.  Välj **Slutför** för att spara konfigurationen och starta den första synkroniseringen för Azure AD-säkerhetsgruppen.

## <a name="next-steps"></a>Nästa steg

-   [Konfigurera Zimperium-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)
