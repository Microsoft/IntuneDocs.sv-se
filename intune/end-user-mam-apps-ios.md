---
title: iOS-appar med appskyddsprinciper
description: "Det här avsnittet beskriver vad som händer när din iOS-app hanteras av appskyddsprinciper."
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 02/15/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0a9d17f8066ddd16c06322cf9cc64457daff87f1
ms.sourcegitcommit: 6d69403266dbcb31c879432719798935c94917fa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/19/2018
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Vad som händer när din iOS-app hanteras av appskyddsprinciper

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

 Det här avsnittet beskriver användarupplevelsen för appar med appskyddsprinciper. Appskyddsprinciper tillämpas endast när appar används i arbetssammanhang, exempelvis när användaren har åtkomst till appar med ett arbetskonto eller har åtkomst till filer som lagras på en OneDrive för företag-plats.

##  <a name="access-apps"></a>Åtkomstappar

Om enheten **inte har registrerats i Intune** uppmanas användarna att starta om appen första gången de använder den. En omstart krävs för att appskyddsprinciperna ska kunna tillämpas på appen.

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

För enheter som **har registrerats för hantering i Intune** ser användaren ett meddelande som anger att appen nu hanteras.

##  <a name="use-apps-with-multi-identity-support"></a>Använda appar med stöd för flera identiteter

Med appar som stöder flera identiteter kan du använda olika konton (arbetskonton och privata konton) för att få åtkomst till samma appar, där appskyddsprinciperna endast tillämpas när apparna används i arbetskontexten.  

Användaren uppmanas till exempel att ange en PIN-kod för att kunna komma åt arbetsdata. För **Outlook-appen**, uppmanas användaren att ange en PIN-kod när hen startar appen. För **OneDrive-appen**, uppmanas användaren att ange en PIN-kod när hen skriver i arbetskontot.  För Microsoft **Word**, **PowerPoint** och **Excel**, uppmanas användaren att ange en PIN-kod när hen har åtkomst till dokument som lagras i företagets OneDrive för företag.

- Mer information om appar som stöder [appskydd och multiidentitet](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) med Intune.

Appskyddsprinciper tillämpas bara i arbetssammanhang. Därför kan appen fungerar på olika sätt beroende på om sammanhanget är arbete eller personligt.

##  <a name="manage-user-accounts-on-the-device"></a>Hantera användarkonton på enheten

Med program med stöd för flera identiteter är det möjligt för användare att lägga till flera konton.  Intune APP har endast stöd för ett hanterat konto.  Intune APP begränsar inte antalet ohanterade konton.

När ett hanterat konto finns i ett program:
*   Om en användare försöker lägga till ett andra hanterat konto uppmanas användaren att välja vilket av de hanterade kontona som ska användas.  Det andra kontot tas bort.
*   Om IT-administratören lägger till principer till ett andra befintligt konto uppmanas användaren att välja vilket av de hanterade kontona som ska användas.  Det andra kontot tas bort.

Läs följande exempel för att få en bättre förståelse för hur flera användarkonton behandlas.

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera appskyddsprinciper. **Företag X** distribuerar appskyddsprinciper **före** **Företag Y**. Det konto som är associerad med **Företag X** får appskyddsprincipen först. Om du vill att användarkontot som är kopplat till Företag Y ska hanteras av appskyddsprinciperna måste du ta bort användarkontot som är kopplat till Företag X och lägga till användarkontot som är associerat med Företag Y.

### <a name="add-a-second-account"></a>Lägg till ett andra konto

Om du använder en iOS-enhet kanske ett blockeringsmeddelande visas om du försöker lägga till ett andra arbetskonto på samma enhet. Kontona visas och sedan kan du välja det konto som du vill ta bort.

## <a name="next-steps"></a>Nästa steg
[Vad som händer när din Android-app hanteras av appskyddsprinciper](end-user-mam-apps-android.md)
