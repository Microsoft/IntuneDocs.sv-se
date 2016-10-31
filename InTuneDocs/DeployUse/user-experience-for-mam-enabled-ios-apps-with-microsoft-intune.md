---
title: iOS-appar med MAM-principer | Microsoft Intune
description: "Det här avsnittet beskriver vad som händer när din iOS-app hanteras av hanteringsprinciper för mobilappar (MAM)."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: 3f9d9c7cafcdac0db21e5ba35f713fe630c65b99


---

# Vad som händer när din iOS-app hanteras med MAM-principer
 Det här avsnittet beskriver användargränssnittet för appar med MAM-principer. MAM-principer för hantering av mobila program används bara om appar används i arbetskontexten, t.ex. åtkomst till appar med ditt arbetskonto eller åtkomst till filer som lagras på platsen för ditt företags OneDrive för företag.
##  Komma åt appar

Om enheten **inte har registrerats i Intune** uppmanas slutanvändarna att starta om appen första gången de använder den.  En omstart krävs för att MAM-principerna ska kunna tillämpas på appen. Följande skärmbild illustrerar detta med hjälp av Skype-appen:


![Skärmbild av iOS-enheten där användaren uppmanas att ange en PIN-kod](../media/appmanagement/iOS_AppPINPrompt.png)

För enheter som **har registrerats för hantering i Intune** ser slutanvändaren ett meddelande som anger att appen nu hanteras:

![Skärmbild av iOS-enheten med ett meddelande som anger att appen hanteras av användarens företag och som uppmanar användaren att ange en PIN-kod](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  Använda appar med stöd för flera identiteter

MAM-principer tillämpas bara i arbetskontexten när du använder appen, och appens beteende kan skilja sig beroende på kontexten: arbete eller personligt.  

För appar som stöder flera identiteter tillämpar Intune endast MAM-principerna när slutanvändaren använder appen i arbetskontexten.  Slutanvändaren uppmanas till exempel att ange en PIN-kod för att kunna komma åt arbetsdata.  För **Outlook-appen** uppmanas slutanvändaren att ange en PIN-kod när appen startas. För **OneDrive-appen** sker detta när slutanvändaren anger arbetskontot.  För Microsoft **Word**, **PowerPoint* och **Excel** sker detta när användaren kommer åt dokument som lagras på platsen för företagets OneDrive för företag.
##  Hantera användarkonton på enheten

Intune har endast stöd för distribution av MAM-principer till endast ett användarkonto per enhet.

* Beroende på den app du använder kan den andra användaren eventuellt vara blockerad på enheten. I samtliga fall påverkas dock endast den första användaren som hämtar MAM-principerna av principen.
  * **Microsoft Word**, **Excel** och **PowerPoint** blockerar inte ett andra användarkonto, men det andra användarkontot påverkas inte av MAM-principerna.  

  * För **OneDrive- och Outlook-appar** kan du bara använda ett arbetskonto.  Det går inte att lägga till flera arbetskonton i dessa appar.  Däremot kan du ta bort en användare och lägga till en annan användare på enheten.

* Om en enhet har flera befintliga användarkonton innan MAM-principerna distribueras kommer kontot som MAM-principerna distribueras till först att hanteras av Intune MAM-principer.


Läsa exemplet nedan för att få en bättre förståelse för hur flera användarkonton behandlas.

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera MAM-principer. **Företag X** distribuerar MAM-principer **före** **Företag Y**. Det konto som är kopplat till **Företag X** får MAM-principen, men inte kontot som är kopplat till Företag Y. Om du vill att användarkontot som är kopplat till Företag Y ska hanteras av MAM-principerna måste du ta bort användarkontot som är kopplat till Företag X.
### Lägga till ett andra konto

Om du använder en iOS-enhet kanske ett blockeringsmeddelande visas om du försöker lägga till ett andra arbetskonto på samma enhet.  Kontona visas och du kan välja det konto som du vill ta bort.

![Skärmbild av dialogrutan med blockeringsmeddelandet och alternativen Ja och Nej](../media/AppManagement/iOS_SwitchUser.PNG)
## Nästa steg
[Vad som händer när din Android-app hanteras med MAM-principer](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### Se även
[Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


