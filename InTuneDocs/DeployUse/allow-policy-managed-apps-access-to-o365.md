---
title: "Appbaserad villkorlig åtkomst till 0365 | Microsoft Intune"
description: "Förstå hur MAM CA kan hjälpa till med att styra vilka program som har åtkomst till O365-tjänster."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 64eaba6918c4a5c7ccc39fb8ccfeae729a34ff4c
ms.openlocfilehash: a03faa57f9bf1ec6784f0b1ec2d41d3f4cd88a12


---

# Skapa en princip som endast tillåter att mobila appar som stöder Intunes MAM-principer får åtkomst till Office 365-tjänster
[Intunes hanteringsprinciper för mobilappar (MAM)](protect-apps-and-data-with-microsoft-intune.md) hjälper dig att skydda företagets data på enheter som är registrerade för hantering i Intune. Du kan även använda MAM-principer på **medarbetares enheter som inte har registrerats för hantering i Intune**.  Även om du inte hanterar enheten i det här fallet behöver du fortfarande se till att företagets data och resurser är skyddade. Men hjälp av villkorlig åtkomst för MAM (MAM CA) kan du skapa en princip som endast tillåter att mobila appar som stöder Intunes MAM-principer får åtkomst till O365-tjänster som Exchange Online.

Till exempel kan du genom att bara tillåta **Microsoft Outlook-appen** att få åtkomst till Exchange Online **blockera inbyggda e-postappar på iOS och Android**, som inte har dataskydd från Intune MAM-principer, från att hämta e-post från **Exchange Online**.

## Förutsättningar
**Innan** du kan konfigurera MAM CA-principer måste du ha en **Enterprise Mobility + Security- eller Azure Active Directory Premium-prenumeration**, och användarna måste ha licens för EMS eller Azure AD. Mer information finns på [sidan med priser för Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing) eller [sida med priser för Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/).


## Appar som stöds
**Exchange Online**
* Microsoft Outlook för Android och iOS

## Överlappar med andra metoder för villkorlig åtkomst och autentisering
### MAM CA med Azure Active Directory-certifikatbaserad autentisering

MAM CA kan inte användas med Azure Active Directory (Azure AD)-certifikatbaserad autentisering. Du kan endast ha en av dessa konfigurerade åt gången.
### MAM CA med villkorlig åtkomst baserat på enhetens efterlevnad  

Du kan konfigurera [Villkorlig åtkomst baserat på enhetens efterlevnad](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (**Enhets-CA**) i [Intune-administratörskonsolen](https://manage.microsoft.com) eller [Azure AD Premium-hanteringskonsolen] (https://manage.windowsazure.com). Enhets-CA kräver att användare ansluter till Exchange Online via Intune-hanterade enheter som är kompatibla med Intunes policy för enhetsefterlevnad eller genom domänanslutna datorer.  Om en användare hör till en eller flera säkerhetsgrupper som hanteras av både MAM CA- och enhets-CA-principer så måste användaren uppfylla ett av dessa två krav:
* Appen som används för att komma åt tjänsten är en mobilapp som stöds av MAM CA och den enhet som appen körs på har **iOS Authenticator (för iOS-enheter)**, eller **Företagsportalappen (för Android-enheter)** installerad.
* Enheten som används för att komma åt tjänsten **hanteras av Intune och är kompatibel** med Intunes policy för enhetsefterlevnad, eller är en **domänansluten dator**.  Här följer några exempel för att illustrera detta:
  * Om en användare försöker ansluta från den **interna iOS e-postappen** måste de använda en **hanterad och kompatibel enhet** eftersom interna e-postappar inte stöds av MAM CA.
  * Om en användare försöker ansluta från en **Windows home PC** (Windows Home-dator) kommer **Device CA policy** (principen för enhets-CA) att gälla och kräva att användaren använder en domänansluten dator.


## Vad du kan förvänta dig när du använder en app med MAM CA
MAM CA verifierar det godkända programmets identitet med hjälp av en koordinatorapp som måste finnas på enheten:
*  På **iOS** fungerar **Azure Authenticator-appen** som en koordinatorapp.
* På **Android** fungerar **Intune-företagsportalappen** som en koordinatorapp. 

Slutanvändare som loggar in för första gången till en app som stöds av MAM CA, t.ex. OneDrive eller Outlook, uppmanas att installera koordinatorappen och registrera enheten med Azure AD. Registrering av enheter i Azure AD (tidigare kallat Workplace Join) skapar en post för enheten och ett certifikat mot vilket token utfärdas.  Detta är **inte** **MDM-registrering**. Inga hanteringsprofiler eller principer tillämpas och ingen inventering av appar på enheten utförs.  Processen att installera koordinatorappen och att registrera enheten sker endast den första gången en hanterad app används.


## Nästa steg
[Skapa en Exchange Online-princip för MAM-appar](mam-ca-for-exchange-online.md)

[Blockera appar som inte har modern autentisering](block-apps-with-no-modern-authentication.md)

### Se även

[Skydda appdata med MAM-principer](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


