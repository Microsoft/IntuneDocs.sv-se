---
title: Hämta en återställnings nyckel för en macOS-enhet från Intune-företagsportal webbplats
description: Visa återställnings nyckeln för en registrerad, hanterad macOS-enhet.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 1e7831712b4c07d015aa0f587ff6ba6183940897
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75855244"
---
# <a name="get-a-recovery-key-for-a-macos-device"></a>Hämta en återställnings nyckel för en macOS-enhet

Använd Företagsportal webbplats för att få en återställnings nyckel för din låsta macOS-enhet. Om du glömmer ditt enhets lösen ord kan du logga in på Företagsportal från en annan enhet för att hämta din nyckel.  

## <a name="get-recovery-key-from-company-portal-website"></a>Hämta återställnings nyckel från Företagsportal webbplats

Det här alternativet är tillgängligt för enheter som har krypterats av din organisation med hjälp av FileVault. Det är inte tillgängligt för enheter som du har krypterat personligen.

1. På valfri enhet loggar du in på [företagsportal webbplats](https://portal.manage.microsoft.com) och väljer **meny** knappen > **enheter**.  
2. Välj den krypterade macOS-enheten.  
3. Välj **Hämta återställningsnyckel**.  

    ![Skärm bild av Företagsportal webbplats, markera Hämta återställnings nyckel avsnitt.](./media/1907-recovery2-cpweb-intune.PNG)  

4. Återställnings nyckeln kommer att visas.

    ![Skärm bild av Företagsportal webbplats som visar återställnings nyckeln.](./media/1907-recovery-cpweb-intune.PNG)  

    Av säkerhets skäl försvinner nyckeln efter fem minuter. Om du vill se nyckeln igen väljer du **Hämta återställnings nyckel**.

Om en nyckel inte hittas men enheten är korrekt krypterad kontaktar du din organisations support person. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="get-recovery-key-from-company-portal-app-for-ios"></a>Hämta återställnings nyckel från Företagsportal app för iOS

Du kan hämta din personliga återställnings nyckel (FileVault Key) med hjälp av Företagsportal-appen för iOS. Enheten som har den personliga återställnings nyckeln måste registreras med Intune och krypteras med FileVault via Intune. Det här alternativet är inte tillgängligt för enheter som du själv har krypterat. 

Med hjälp av Företagsportal-appen kan du öppna Safari-webbvyn och hämta din personliga återställnings nyckel. 

1. Öppna appen Företagsportal.
2. Klicka på **Hämta återställnings nyckel**.

    ![Skärm bild av Företagsportal app för iOS, med återställnings nyckel](./media/get-recovery-key-cpweb-02.png)  

Företagsportal webbplats öppnas i Safari-webbvy och visar nyckeln. 

## <a name="it-pro-support"></a>Support för IT-proffs

Om du är en IT-support person och vill konfigurera och hantera FileVault-kryptering för macOS-enheter, se [Använd enhets kryptering med Intune](/intune/protect/encrypt-devices).

## <a name="next-steps"></a>Nästa steg

Ta reda på mer om vad du kan göra från Företagsportal webbplats. Se [använda Intune-företagsportal webbplats](using-the-intune-company-portal-website.md) för att få en lista över åtgärder.  

Behöver du fortfarande hjälp? Kontakta IT-supporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  
