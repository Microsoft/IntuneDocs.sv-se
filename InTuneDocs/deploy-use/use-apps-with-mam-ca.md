---
title: "Använda appar med MAM CA | Microsoft Intune"
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
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 317d101c34854fdf4913adcf53bdef614599deb7


---
# <a name="what-to-expect-when-using-an-app-with-mam-ca"></a>Vad du kan förvänta dig när du använder en app med MAM CA
MAM CA verifierar det godkända programmets identitet med hjälp av en koordinatorapp som måste finnas på enheten:
*  På **iOS** fungerar **Azure Authenticator-appen** som en koordinatorapp.
* På **Android** fungerar **Intune-företagsportalappen** som en koordinatorapp. 

Slutanvändare som loggar in för första gången till en app som stöds av MAM CA, t.ex. OneDrive eller Outlook, uppmanas att installera koordinatorappen och registrera enheten med Azure AD. Registrering av enheter i Azure AD (tidigare kallat Workplace Join) skapar en post för enheten och ett certifikat mot vilket token utfärdas.  Detta är **inte** **MDM-registrering**. Inga hanteringsprofiler eller principer tillämpas och ingen inventering av appar på enheten utförs.  Processen att installera koordinatorappen och att registrera enheten sker endast den första gången en hanterad app används.

Här följer en lista över egenskaper som härleds direkt från enheten:

* alternativeSecurityIds (tumavtryck för certifikat och hash för offentlig nyckel för Azure Active Directory)
* deviceOSType
* deviceOSVersion
* visningsnamn

## <a name="to-remove-a-device-from-azure-ad-registration"></a>Så här tar du bort en enhet från Azure AD-registrering
Du kan ta bort enhetsregistreringen via Azure AD-administrationskonsolen, vilket normalt görs av IT-administratören.  Det kan också göras av slutanvändaren på själva enheten.

* **Azure AD-administrationskonsolen**: Ta bort enheten i Azure AD-administrationskonsolen **.
* **iOS-enhet**: Öppna Azure Authenticator-appen, svep åt vänster på kontot och välj Avregistrera.  
* **Android-enhet**: Avinstallera företagsportalappen eller ta bort kontot från **Systeminställningar**.



## <a name="mam-ca-with-conditional-access-based-on-device-compliance"></a>MAM CA med villkorlig åtkomst baserat på enhetens efterlevnad  

Du kan konfigurera [Villkorlig åtkomst baserat på enhetens efterlevnad](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (**Enhets-CA**) i [Intune-administratörskonsolen](https://manage.microsoft.com) eller [Azure AD Premium-hanteringskonsolen] (https://manage.windowsazure.com). Enhets-CA kräver att användare ansluter till Exchange Online via Intune-hanterade enheter som är kompatibla med Intunes policy för enhetsefterlevnad eller genom domänanslutna datorer.  Om en användare hör till en eller flera säkerhetsgrupper som hanteras av både MAM CA- och enhets-CA-principer så måste användaren uppfylla ett av dessa två krav:
* Appen som används för att komma åt tjänsten är en mobilapp som stöds av MAM CA och den enhet som appen körs på har **iOS Authenticator (för iOS-enheter)**, eller **Företagsportalappen (för Android-enheter)** installerad.
* Enheten som används för att komma åt tjänsten **hanteras av Intune och är kompatibel** med Intunes policy för enhetsefterlevnad, eller är en **domänansluten dator**.  Här följer några exempel för att illustrera detta:
  * Om en användare försöker ansluta från den **interna iOS e-postappen** måste de använda en **hanterad och kompatibel enhet** eftersom interna e-postappar inte stöds av MAM CA.
  * Om en användare försöker ansluta från en **Windows home PC** (Windows Home-dator) kommer **Device CA policy** (principen för enhets-CA) att gälla och kräva att användaren använder en domänansluten dator.




## <a name="next-steps"></a>Nästa steg
[Skapa en Exchange Online-princip för MAM-appar](mam-ca-for-exchange-online.md)

[Blockera appar som inte har modern autentisering](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Se även

[Skydda appdata med MAM-principer](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


