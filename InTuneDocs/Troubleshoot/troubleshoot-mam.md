---
title:
- "Felsök hantering av mobilprogram | Microsoft Intune"
description: 
keywords: 
author: karaman
manager: angerobe
ms.date: 09/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: 9cfb3694b2fae919fd0554a6e21b497cdcf19c72
ms.openlocfilehash: f33e8de82ee07bb4571a5bfaff63af72f9086376


---

# Felsök hantering av mobilprogram

Börja här om du har problem med hantering av mobilprogram. Det här avsnittet innehåller några vanliga problem du kan stöta på samt lösningar på problemen.


**Problem:** MAM utan registreringsprincip från Azure-konsolen kan inte tillämpas på Skype för Business-app på iOS och Android-enheter.

Lösning: Skype för företag måste konfigureras för modern autentisering.  Följ instruktionerna i [Enable your tenant for modern authentication](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (Aktivera din klient för modern autentisering) för att konfigurera modern autentisering för Skype.

**Problem:** MAM utan registreringsprinciper kan inte tillämpas på någon (Office-app som stöds) [https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners] för någon användare.
 
Lösning: Kontrollera att användaren är licensierad för Intune.  

**Problem:** IT-administratör kan inte konfigurera MAM principer i Azure-portalen

Lösning: Följande roller har åtkomst till Azure-portalen:

- Global administratör, som du kan ställa in i [Office-portalen](http://portal.office.com/)
- Ägare, som du kan ställa in i [Azure-portalen](https://portal.azure.com/).
- Deltagare, som du kan ställa in i [Azure-portalen](https://portal.azure.com/).

Referera till [Förbered dig för att konfigurera hanteringsprinciper för mobila appar med Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) för hjälp med att ställa in dessa roller. 

**Problem:** Apprapporten visar inte användare vi nyligen riktade MAM-principen till.

Lösning: Om en MAM-princip nyligen riktats till en användare kan det kan ta upp till 24 timmar för att användaren ska visas i rapporter som en sådan användare. 

**Problem:** Principändringar/uppdateringar kan ta upp till 8 timmar innan de börjar gälla.  

Lösning: Slutanvändaren kan logga ut från appen och logga in igen för att tvinga synkronisering med tjänsten.  

**Problem:** MAM-principen tillämpas inte på Apple DEP-enheter

Lösning: Kontrollera att du använder Användartillhörighet med Apples program för enhetsregistrering (DEP). Användartillhörighet krävs för alla appar som kräver användarautentisering under DEP.
Referera till [Registrera företagsägda iOS-enheter i Enhetsregistreringsprogrammet](https://docs.microsoft.com/en-us/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) för mer information om DEP-registrering.


### Se även
- [Verifiera din konfiguration för hantering av mobilprogram](https://docs.microsoft.com/en-us/intune/deploy-use/validate-mobile-application-management)
- [Förbered dig för att konfigurera hanteringsprinciper för mobila appar med Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) 





<!--HONumber=Sep16_HO2-->


