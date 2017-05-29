---
title: iOS-appar med appskyddsprinciper | Microsoft Docs
description: "Det här avsnittet beskriver vad som händer när din iOS-app hanteras av appskyddsprinciper."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 92a91fab353c78c751ae5eb25c9853df5cbcfe53
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Vad som händer när din iOS-app hanteras av appskyddsprinciper

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

 Det här avsnittet beskriver användarupplevelsen för appar med appskyddsprinciper. Appskyddsprinciper tillämpas endast när appar används i arbetssammanhang, exempelvis när användaren har åtkomst till appar med ett arbetskonto eller har åtkomst till filer som lagras på en OneDrive för företag-plats.

##  <a name="access-apps"></a>Åtkomstappar

Om enheten **inte har registrerats i Intune** uppmanas användarna att starta om appen första gången de använder den. En omstart krävs för att appskyddsprinciperna ska kunna tillämpas på appen. 

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

För enheter som **har registrerats för hantering i Intune** ser användaren ett meddelande som anger att appen nu hanteras.

##  <a name="use-apps-with-multi-identity-support"></a>Använda appar med stöd för flera identiteter

Med appar som stöder flera identiteter kan du använda olika konton (arbetskonton och privata konton) för att få åtkomst till samma appar, där appskyddsprinciperna endast tillämpas när apparna används i arbetskontexten.  

Användaren uppmanas till exempel att ange en PIN-kod för att kunna komma åt arbetsdata. För **Outlook-appen**, uppmanas användaren att ange en PIN-kod när hen startar appen. För **OneDrive-appen**, uppmanas användaren att ange en PIN-kod när hen skriver i arbetskontot.  För Microsoft **Word**, **PowerPoint** och **Excel**, uppmanas användaren att ange en PIN-kod när hen har åtkomst till dokument som lagras i företagets OneDrive för företag.

- Mer information om appar som stöder [MAM och multiidentitet](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) med Intune.

Appskyddsprinciper tillämpas bara i arbetssammanhang. Därför kan appen fungerar på olika sätt beroende på om sammanhanget är arbete eller personligt.

##  <a name="manage-user-accounts-on-the-device"></a>Hantera användarkonton på enheten

Intune stöder distribution av appskyddsprinciper till ett användarkonto per enhet endast.

* Beroende på den app du använder kan den andra användaren eventuellt vara blockerad på enheten. I samtliga fall påverkas dock endast den första användaren som hämtar appskyddsprincipen.
  * **Microsoft Word**, **Excel** och **PowerPoint** blockerar inte ett andra användarkonto, men det andra användarkontot påverkas inte av appskyddsprinciperna.  

  * För **OneDrive- och Outlook-appar** och **Outlook-appar** kan du bara använda ett arbetskonto. Du kan inte lägga till flera arbetskonton för dessa appar. Däremot kan du ta bort en användare och lägga till en annan användare på enheten.

* Om en enhet har flera befintliga användarkonton innan appskyddsprinciperna distribueras kommer kontot som appskyddsprinciperna distribueras till först att hanteras av Intunes appskyddsprinciper.


Läs följande exempel för att få en bättre förståelse för hur flera användarkonton behandlas.

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera appskyddsprinciper. **Företag X** distribuerar appskyddsprinciper **före** **Företag Y**. Det konto som är kopplat till **Företag X** får appskyddsprincipen, men inte kontot som är kopplat till Företag Y. Om du vill att användarkontot som är kopplat till Företag Y ska hanteras av appskyddsprinciperna måste du ta bort användarkontot som är kopplat till Företag X.

### <a name="add-a-second-account"></a>Lägg till ett andra konto

Om du använder en iOS-enhet kanske ett blockeringsmeddelande visas om du försöker lägga till ett andra arbetskonto på samma enhet. Kontona visas och sedan kan du välja det konto som du vill ta bort.

## <a name="next-steps"></a>Nästa steg
[Vad som händer när din Android-app hanteras av appskyddsprinciper](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### <a name="see-also"></a>Se även
[Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

