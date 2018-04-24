---
title: iOS-appar med appskyddsprinciper
titlesuffix: Microsoft Intune
description: Läs om vad som händer när iOS-appar har skyddsprinciper.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2804003a0f1acac56ecaae5e24dcf34b4eb0c256
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Vad som händer när din iOS-app hanteras av appskyddsprinciper

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Läs om användarupplevelsen för iOS-appar med appskyddsprinciper. Appskyddsprinciper används bara när appar används i en arbetskontext. Det kan till exempel vara när du använder en app med ett arbetskonto eller när du använder filer som är lagrade på företagets OneDrive-plats.
##  <a name="accessing-apps"></a>Komma åt appar

Om enheten **inte har registrerats i Intune** uppmanas användarna att starta om appen första gången de använder den.  En omstart krävs för att appskyddsprinciperna ska kunna tillämpas på appen. Följande skärmbild illustrerar detta med hjälp av Skype-appen:


![Skärmbild av iOS-enheten där användaren uppmanas att ange en PIN-kod](./media/ios-pin-prompt.png)

För enheter som **har registrerats för hantering i Intune** ser användaren ett meddelande som anger att appen nu hanteras:

![Skärmbild av iOS-enheten med ett meddelande som anger att appen hanteras av användarens företag och som uppmanar användaren att ange en PIN-kod](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>Använda appar med stöd för flera identiteter

Appskyddsprinciperna gäller endast om en användare försöker komma åt arbetsrelaterade data.  Beteendet kan se annorlunda ut om användaren använder appen för personligt bruk. 

För appar som stöder flera identiteter tillämpar Intune endast appskyddsprinciper när en användare försöker komma åt arbetsdata.  En användare kan till exempel uppmanas att ange en PIN-kod.  I **Outlook-appen** uppmanas användaren att ange en PIN-kod när han eller hon startar appen. I **OneDrive-appen** uppmanas användaren att ange en PIN-kod när han eller hon anger arbetskontot.  I Microsoft **Word**, **PowerPoint** och **Excel** uppmanas användaren att ange en PIN-kod när han eller hon öppnar företagets OneDrive-dokument.
##  <a name="managing-user-accounts-on-the-device"></a>Hantera användarkonton på enheten

Intune har endast stöd för distribution av appskyddsprinciper till ett användarkonto per enhet.

* Beroende på den app du använder kan den andra användaren eventuellt vara blockerad på enheten. I samtliga av dessa fall är det bara den första användaren som får appskyddsprinciperna som påverkas av principen.
  * **Microsoft Word**, **Excel** och **PowerPoint** blockerar inte åtkomst till ytterligare ett användarkonto. Användarkontot påverkas dock inte av appskyddsprinciperna.

  * För **OneDrive- och Outlook-appar** kan du bara använda ett arbetskonto.  Det går inte att lägga till flera arbetskonton i dessa appar.  Men du kan ta bort en användare från en enhet, och sedan lägga till en annan användare i enheten.

* En enhet kan ha flera befintliga användarkonton innan appskyddsprinciperna distribueras. I så fall hanteras det första kontot som appskyddsprinciperna distribueras till av Intunes appskyddsprinciper.


Läs följande exempelscenario om du vill veta hur Intune hanterar flera användarkonton.

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera appskyddsprinciper. **Företag X** distribuerar appskyddsprinciper **före** **Företag Y**. Det konto som är kopplat till **Företag X** får appskyddsprincipen, men inte kontot som är kopplat till Företag Y. Om du vill att användarkontot för Företag Y ska hanteras av appskyddsprinciperna måste Användare A ta bort användarkontot för Företag X.
### <a name="adding-a-second-account"></a>Lägga till ett andra konto

Om du använder en iOS-enhet kanske ett blockeringsmeddelande visas om du försöker lägga till ett andra arbetskonto på samma enhet.  Kontona visas och du kan välja det konto som du vill ta bort.

![Skärmbild av dialogrutan med blockeringsmeddelandet och alternativen Ja och Nej](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>Nästa steg
[Vad som händer när din Android-app hanteras av appskyddsprinciper](app-protection-enabled-apps-android.md)
### <a name="see-also"></a>Se även
[Skapa och distribuera appskyddsprinciper med Microsoft Intune](app-protection-policies.md)
