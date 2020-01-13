---
title: iOS-appar med appskyddsprinciper
description: Det här avsnittet beskriver vad som händer när din iOS-app hanteras av appskyddsprinciper.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 165ce160339647e396b9cfc3a8374f21c77665f8
ms.sourcegitcommit: f9dc50642efa8656054ef67f9335b9b46b655f93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/02/2020
ms.locfileid: "75606629"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Vad som händer när din iOS-app hanteras av appskyddsprinciper

Intunes appskyddsprinciper tillämpas på appar som används för arbete eller skola. Det innebär att när dina anställda och studenter använder sina appar i ett personligt sammanhang, kan de se till att upplevelsen blir likadan. I arbets- eller skolsammanhang kan de däremot få meddelanden om att fatta kontobeslut, uppdatera inställningar eller kontakta dig för hjälp. Använd den här artikeln för att lära dig vad dina användare upplever när de försöker komma åt och använda Intune-skyddade appar.  

## <a name="access-apps"></a>Åtkomstappar

Om enheten **inte har registrerats i Intune** uppmanas användarna att starta om appen första gången de använder den. En omstart krävs för att appskyddsprinciperna ska kunna tillämpas på appen.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

För enheter som **har registrerats för hantering i Intune** ser användaren ett meddelande som anger att appen nu hanteras.

## <a name="use-apps-with-multi-identity-support"></a>Använda appar med stöd för flera identiteter

Appar som stöder flera identiteter gör att du kan använda olika arbetskonton och personliga konton för att komma åt samma appar. Appskyddsprinciper, som att ange en PIN-kod för enheten, aktiveras när användarna kommer åt dessa appar i ett arbets- eller skolsammanhang.   

Användarna kan uppleva inmatningen av PIN-koden på olika sätt i sina olika appar, beroende på hur du konfigurerar principerna.  Du kan till exempel konfigurera principerna så att:       
* Outlook-appen uppmanar användarna att ange en PIN-kod när de startar appen. 
* OneDrive uppmanar användarna att ange en PIN-kod när de loggar in på sitt arbetskonto.  
* Microsoft, PowerPoint och Excel uppmanar användarna att ange en PIN-kod när de använder dokument som lagrats i företagets OneDrive för företag.  

- Mer information om appar som stöder [appskydd och multiidentitet](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) med Intune.  

## <a name="manage-user-accounts-on-the-device"></a>Hantera användarkonton på enheten  

Intunes appskyddsprinciper begränsar användare till ett hanterat arbets- eller skolkonto per app. Appskyddsprinciperna begränsar inte antalet ohanterade konton som en användare kan lägga till.   

- Om en användare försöker lägga till ett andra hanterat konto uppmanas användaren att välja vilket av de hanterade kontona som ska användas. Om användaren lägger till ett andra konto tas det första kontot bort.
- Om du lägger till skyddsprinciper till en annan användares konton uppmanas användaren att välja vilket hanterat konto som ska användas. Det andra kontot tas bort. 

Vissa användare får inte möjlighet att växla eller välja mellan hanterade konton. Alternativet är inte tillgängligt på enheter som:
* Hanteras av Intune  
* Hanteras av lösningar för hantering av företagsmobilitet från tredje part och konfigureras med IntuneMAMUPN-inställningen 

Följande exempelscenario beskriver hur användarkonton med flera användare behandlas:  

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera appskyddsprinciper. **Företag X** distribuerar appskyddsprinciper **före** **Företag Y**. Det konto som är associerad med **Företag X** får appskyddsprincipen först. Om du vill att användarkontot som är kopplat till Företag Y ska hanteras av appskyddsprinciperna måste du ta bort användarkontot som är kopplat till Företag X och lägga till användarkontot som är associerat med Företag Y.  

## <a name="next-steps"></a>Nästa steg

[Vad som händer när din Android-app hanteras av appskyddsprinciper](end-user-mam-apps-android.md)
