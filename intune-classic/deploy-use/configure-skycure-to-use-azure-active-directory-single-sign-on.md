---
title: "Konfigurera Skycure till att använda enkel inloggning med Azure Active Directory"
description: "Konfigurera Skycure till att använda enkel inloggning (SSO) med Azure Active Directory"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 34d5d359-5c7c-4225-a205-8ce890b6f890
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a26292f2247c4fa65e9aa2df047a9ef1fe98476a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="configure-skycure-to-use-azure-active-directory-single-sign-on-sso"></a>Konfigurera Skycure till att använda enkel inloggning (SSO) med Azure Active Directory

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Enkel inloggning med Azure AD används när du integrerar Intune med Skycure. Här är de främsta fördelarna:

-   **Administratörer** kan använda samma autentiseringsuppgifter utan att behöva skriva dem varje gång de loggar in och ut från Microsoft-portaler (Intune, Azure) och Skycure Management Console.

-   **Slutanvändare** kan använda samma autentiseringsuppgifter för Azure AD utan att behöva ange dem igen varje gång de loggar in och ut från Skycure-apparna.

Nedan visas stegen för att integrera Skycure med enkel inloggning (SSO) med Azure Active Directory.

## <a name="to-retrieve-the-azure-active-directory-tenant-id"></a>Så här hämtar du ett klient-ID för Azure Active Directory

Du måste hämta ett klient-ID för Azure AD.

1.  Gå till [Azure-portalen](https://portal.azure.com/) och logga in med dina autentiseringsuppgifter.

2.  I **instrumentpanelen** väljer du **Azure Active Directory**.

![Azure AD-instrumentpanel](../media/mtp/skycure-sso-1.png)

1.  Bladet **Azure Active Directory** öppnas. Välj **Egenskaper**.

![Bladet Azure AD-egenskaper](../media/mtp/skycure-sso-2.png)

1.  Klicka på **ikonen Kopiera** under **Katalog-ID för innehavare** på bladet **Egenskaper för Azure Active Directory**.

> Klistra in det kopierade katalog-ID-värdet i en textfil så att du kan använda det senare. Katalog-ID-värdet krävs senare i processen för Skycure- och Intune-integrering.

![Azure AD-instrumentpanel](../media/mtp/skycure-sso-3.png)

## <a name="allow-skycure-to-communicate-with-azure-active-directory"></a>Tillåt att Skycure kommunicerar med Azure Active Directory

1.  Skriv nedanstående URL i webbläsaren. I stället för **DIRECTORY_ID**, anger du det klient-ID för Azure Active Directory som du tidigare kopierade till textfilen.

        https://login.microsoftonline.com/<DIRECTORY_ID>/oauth2/authorize?client_id=28fd67fdb1794629a8b0dad420b697c7&prompt=admin_consent&redirect_uri=https%3A%2F%2Fmc.skycure.com%2Fapi%2Fexternal%2Fmdm%2Faad_app_consent%2Fmanagement_callback&response_type=code

2.  Du måste logga in med dina autentiseringsuppgifter för Azure Active Directory. Klicka på **Acceptera** för att fortsätta.

![Inloggningssida för Azure AD](../media/mtp/skycure-sso-4.png)

## <a name="create-an-azure-ad-security-group-for-skycure-optional"></a>Skapa en Azure AD-säkerhetsgrupp för Skycure (valfritt)

Du kanske vill skapa en särskild användargrupp som innehåller de användare som kör Skycure (dvs. Skycure-användare). Detta kan vara användbart när du analyserar Skycure-aktivitet via rapporter.

-   Lär dig mer om [hur du skapar en grupp och lägger till medlemmar i Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).

> [!NOTE] 
> Du kan också använda en befintlig Azure AD-säkerhetsgrupp.

## <a name="configure-the-azure-ad-account-to-integrate-intune-with-skycure"></a>Konfigurera Azure AD-kontot till att integrera Intune med Skycure

1.  Från [Skycure Management Console](https://aad.skycure.com/) anger du det klient-ID för Azure Active Directory som du sparade tidigare i textfilen.

![Skycure Management Console Azure AD fältet klient-ID](../media/mtp/skycure-sso-5.png)

> [!IMPORTANT] 
> Skycure kontrollerar om klient-ID:t för Azure AD finns genom att skicka en fråga till Azure AD. När Skycure hittar det kan administratören gå vidare till nästa steg, vilket är grundinställningen.

## <a name="next-steps"></a>Nästa steg

[Hämta konfigurationsprincip för Skycures iOS-app](/intune-classic/deploy-use/download-skycure-ios-app-configuration-policy)
