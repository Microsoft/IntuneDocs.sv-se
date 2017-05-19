---
title: "Använda appar med MAM CA"
description: "Förstå hur MAM CA kan hjälpa till med att styra vilka program som har åtkomst till O365-tjänster."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71dcf9bc-bfd1-4e06-b7ad-14b33a2288d0
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: ee407827c1c4eb7b113d29c301da0b9fa08fa86d
ms.lasthandoff: 04/19/2017


---
# <a name="what-to-expect-when-using-an-app-with-app-based-ca"></a>Vad som händer när du använder en app med appbaserad CA

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Appbaserad CA verifierar det godkända programmets identitet med hjälp av en koordinatorapp som måste finnas på enheten:
*  På **iOS** fungerar **Azure Authenticator-appen** som en koordinatorapp.
* På **Android** fungerar **Intune-företagsportalappen** som en koordinatorapp. 

Slutanvändare som loggar in för första gången i en app som stöds av appbaserad CA, t.ex. OneDrive eller Outlook, uppmanas att installera koordinatorappen och registrera enheten med Azure AD. Registrering av enheter i Azure AD (tidigare kallat Workplace Join) skapar en post för enheten och ett certifikat mot vilket token utfärdas.  Detta är **inte** **MDM-registrering**. Inga hanteringsprofiler eller principer tillämpas och ingen inventering av appar på enheten utförs.  Processen att installera koordinatorappen och att registrera enheten sker endast den första gången en hanterad app används.

Här följer en lista över egenskaper som härleds direkt från enheten:

* alternativeSecurityIds (tumavtryck för certifikat och hash för offentlig nyckel för Azure Active Directory)
* deviceOSType
* deviceOSVersion
* visningsnamn

> [!NOTE]
> På Android-enheter:
  * Företagsportalappen måste vara installerad på enheten, men användaren behöver inte logga in i appen.
  * Enhetsregistreringen måste göras via OneDrive- eller Outlook-appen.

## <a name="to-remove-a-device-from-azure-ad-registration"></a>Så här tar du bort en enhet från Azure AD-registrering
Du kan ta bort enhetsregistreringen via Azure AD-administrationskonsolen, vilket normalt görs av IT-administratören.  Det kan också göras av slutanvändaren på själva enheten.

* **Azure AD-administrationskonsolen**: Ta bort enheten i Azure AD-administrationskonsolen **.
* **iOS-enhet**: Öppna Azure Authenticator-appen, svep åt vänster på kontot och välj Avregistrera.  
* **Android-enhet**: Avinstallera företagsportalappen eller ta bort kontot från **Systeminställningar**.

## <a name="app-based-ca-with-device-based-ca"></a>Appbaserad CA med enhetsbaserad CA  

Du kan konfigurera [Villkorlig åtkomst baserat på enhetens efterlevnad](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (**Enhets-CA**) i [Intune-administratörskonsolen](https://manage.microsoft.com) eller [Azure AD Premium-hanteringskonsolen] (https://manage.windowsazure.com). Enhets-CA kräver att användare ansluter till Exchange Online via Intune-hanterade enheter som är kompatibla med Intunes policy för enhetsefterlevnad eller genom domänanslutna datorer.  Om en användare hör till en eller flera säkerhetsgrupper som hanteras av principer för både appbaserad CA och enhets-CA, måste användaren uppfylla ett av dessa två krav:
* Appen som används för att komma åt tjänsten är en mobilapp som stöds av 
* och **iOS Authenticator (för iOS-enheter)** eller **företagsportalappen (för Android-enheter)** måste vara installerat på den enhet som appen körs på.
* Enheten som används för att komma åt tjänsten **hanteras av Intune och är kompatibel** med Intunes policy för enhetsefterlevnad, eller är en **domänansluten dator**.  Här följer några exempel för att illustrera detta:
  * Om en användare försöker ansluta från den **interna iOS e-postappen** måste användarens enhet **vara hanterad och kompatibel** eftersom interna e-postappar inte stöds av appbaserad CA.
  * Om en användare försöker ansluta från en **Windows home PC** (Windows Home-dator) kommer **Device CA policy** (principen för enhets-CA) att gälla och kräva att användaren använder en domänansluten dator.

## <a name="next-steps"></a>Nästa steg
[Skapa en Exchange Online-princip för MAM-appar](mam-ca-for-exchange-online.md)

[Blockera appar som inte har modern autentisering](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Se även

[Skydda appdata med appskyddsprinciper](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

