---
title: iOS-appar med appskyddsprinciper
titleSuffix: Intune on Azure
description: "Det här ämnet beskriver vad du kan förvänta dig när din iOS-app hanteras av appskyddsprinciper.”"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 912bc5230904f5798b2e0026dcf0dd1cecdb811c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Vad som händer när din iOS-app hanteras av appskyddsprinciper
[!INCLUDE[azure_portal](./includes/azure_portal.md)] Det här avsnittet beskriver användarupplevelsen för appar med appskyddsprinciper. Appskyddsprinciper används bara när appar används i arbetskontext, t.ex. åtkomst till appar med ditt arbetskonto eller åtkomst till filer som lagras på platsen för ditt företags OneDrive för företag.
##  <a name="accessing-apps"></a>Komma åt appar

Om enheten **inte har registrerats i Intune** uppmanas slutanvändarna att starta om appen första gången de använder den.  En omstart krävs för att appskyddsprinciperna ska kunna tillämpas på appen. Följande skärmbild illustrerar detta med hjälp av Skype-appen:


![Skärmbild av iOS-enheten där användaren uppmanas att ange en PIN-kod](./media/ios-pin-prompt.png)

För enheter som **har registrerats för hantering i Intune** ser slutanvändaren ett meddelande som anger att appen nu hanteras:

![Skärmbild av iOS-enheten med ett meddelande som anger att appen hanteras av användarens företag och som uppmanar användaren att ange en PIN-kod](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>Använda appar med stöd för flera identiteter

Appskyddsprinciper tillämpas bara i arbetskontexten när du använder appen, och appens beteende kan skilja sig beroende på kontexten: arbete eller personligt.  

För appar som stöder flera identiteter tillämpar Intune endast appskyddsprinciperna när slutanvändaren använder appen i arbetskontexten.  Slutanvändaren uppmanas till exempel att ange en PIN-kod för att kunna komma åt arbetsdata.  För **Outlook-appen** uppmanas slutanvändaren att ange en PIN-kod när appen startas. För **OneDrive-appen** sker detta när slutanvändaren anger arbetskontot.  För Microsoft **Word**, **PowerPoint* och **Excel** sker detta när slutanvändaren kommer åt dokument som lagras på platsen för företagets OneDrive för företag-plats.
##  <a name="managing-user-accounts-on-the-device"></a>Hantera användarkonton på enheten

Intune har endast stöd för distribution av appskyddsprinciper till ett användarkonto per enhet.

* Beroende på den app du använder kan den andra användaren eventuellt vara blockerad på enheten. I samtliga fall påverkas dock endast den första användaren som hämtar appskyddsprincipen.
  * **Microsoft Word**, **Excel** och **PowerPoint** blockerar inte ett andra användarkonto, men det andra användarkontot påverkas inte av appskyddsprinciperna.  

  * För **OneDrive- och Outlook-appar** kan du bara använda ett arbetskonto.  Det går inte att lägga till flera arbetskonton i dessa appar.  Däremot kan du ta bort en användare och lägga till en annan användare på enheten.

* Om en enhet har flera befintliga användarkonton innan appskyddsprinciperna distribueras kommer kontot som appskyddsprinciperna distribueras till först att hanteras av Intunes appskyddsprinciper.


Läsa exemplet nedan för att få en bättre förståelse för hur flera användarkonton behandlas.

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera appskyddsprinciper. **Företag X** distribuerar appskyddsprinciper **före** **Företag Y**. Det konto som är kopplat till **Företag X** får appskyddsprincipen, men inte kontot som är kopplat till Företag Y. Om du vill att användarkontot som är kopplat till Företag Y ska hanteras av appskyddsprinciperna måste du ta bort användarkontot som är kopplat till Företag X.
### <a name="adding-a-second-account"></a>Lägga till ett andra konto

Om du använder en iOS-enhet kanske ett blockeringsmeddelande visas om du försöker lägga till ett andra arbetskonto på samma enhet.  Kontona visas och du kan välja det konto som du vill ta bort.

![Skärmbild av dialogrutan med blockeringsmeddelandet och alternativen Ja och Nej](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>Nästa steg
[Vad som händer när din Android-app hanteras av appskyddsprinciper](app-protection-enabled-apps-android.md)
### <a name="see-also"></a>Se även
[Skapa och distribuera appskyddsprinciper med Microsoft Intune](app-protection-policies.md)
