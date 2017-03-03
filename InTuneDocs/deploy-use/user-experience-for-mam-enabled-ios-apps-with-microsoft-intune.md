---
title: iOS-appar med MAM-principer | Microsoft Docs
description: "Det här avsnittet beskriver vad som händer när din iOS-app hanteras av hanteringsprinciper för mobilappar (MAM)."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b068da7685792757825a4bc0d555e28ee0168cb1
ms.openlocfilehash: f5a26d3d5ed060571892d91637dc12cae08f1a69
ms.lasthandoff: 12/16/2016


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-mam-policies"></a>Vad som händer när din iOS-app hanteras med MAM-principer

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

 Det här avsnittet beskriver användargränssnittet för appar med principer för mobil åtkomsthantering (MAM). MAM-principer tillämpas endast när appar används i arbetssammanhang: Till exempel när användaren har åtkomst till appar med ett arbetskonto eller har åtkomst till filer som lagras på ett företags OneDrive-affärsplats.

##  <a name="access-apps"></a>Åtkomstappar

Om enheten **inte har registrerats i Intune** uppmanas användarna att starta om appen första gången de använder den.  En omstart krävs för att MAM-principerna ska kunna tillämpas på appen. 

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

För enheter som **har registrerats för hantering i Intune** ser användaren ett meddelande som anger att appen nu hanteras:

![Skärmbild av iOS-enheten som visar meddelandet om att appen nu hanteras av användarens företag och som uppmanar användaren att ange en PIN-kod](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  <a name="use-apps-with-multi-identity-support"></a>Använda appar med stöd för flera identiteter

MAM-principer tillämpas bara i arbetssammanhang. Därför kan appen fungerar på olika sätt beroende på om sammanhanget är arbete eller personligt.

 Användaren uppmanas till exempel att ange en PIN-kod för att kunna komma åt arbetsdata. För **Outlook-appen**, uppmanas användaren att ange en PIN-kod när hen startar appen. För **OneDrive-appen**, uppmanas användaren att ange en PIN-kod när hen skriver i arbetskontot.  För Microsoft **Word**, **PowerPoint** och **Excel**, uppmanas användaren att ange en PIN-kod när hen har åtkomst till dokument som lagras i företagets OneDrive för företag.

##  <a name="manage-user-accounts-on-the-device"></a>Hantera användarkonton på enheten

Intune stöder distribution av MAM-principer till ett användarkonto per enhet endast.

* Beroende på den app du använder kan den andra användaren eventuellt vara blockerad på enheten. I samtliga fall påverkas dock endast den första användaren som hämtar MAM-principerna av principen.
  * **Microsoft Word**, **Excel** och **PowerPoint** blockerar inte ett andra användarkonto, men det andra användarkontot påverkas inte av MAM-principerna.  

  * För **OneDrive- och Outlook-appar** och **Outlook-appar** kan du bara använda ett arbetskonto. Du kan inte lägga till flera arbetskonton för dessa appar. Däremot kan du ta bort en användare och lägga till en annan användare på enheten.

* Om en enhet har flera befintliga användarkonton innan MAM-principerna distribueras kommer kontot som MAM-principerna distribueras till först att hanteras av Intune MAM-principer.


Läs följande exempel för att få en bättre förståelse för hur flera användarkonton behandlas.

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera MAM-principer. **Företag X** distribuerar MAM-principer **före** **Företag Y**. Det konto som är kopplat till **Företag X** får MAM-principen, men inte kontot som är kopplat till Företag Y. Om du vill att användarkontot som är kopplat till Företag Y ska hanteras av MAM-principerna måste du ta bort användarkontot som är kopplat till Företag X.

### <a name="add-a-second-account"></a>Lägg till ett andra konto

Om du använder en iOS-enhet kanske ett blockeringsmeddelande visas om du försöker lägga till ett andra arbetskonto på samma enhet. Kontona visas och sedan kan du välja det konto som du vill ta bort.

![Skärmbild av dialogrutan med blockeringsmeddelandet och alternativen Ja och Nej](../media/AppManagement/iOS_SwitchUser.PNG)
## <a name="next-steps"></a>Nästa steg
[Vad som händer när din Android-app hanteras med MAM-principer](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### <a name="see-also"></a>Se även
[Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

