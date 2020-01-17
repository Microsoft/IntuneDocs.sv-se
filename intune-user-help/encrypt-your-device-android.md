---
title: Kryptera Android-enhet för Intune | Microsoft Docs
description: Steg för att aktivera Android-enhets kryptering vid behov av Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 2774a4f4c571b8a965c9ec47376a671df2dbf006
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856690"
---
# <a name="encrypting-your-android-device"></a>Kryptera din Android-enhet

Enhets kryptering skyddar dina filer och mappar från obehörig åtkomst om enheten tappas bort eller blir stulen. När du har aktiverat enhets kryptering kan endast personer med rätt lösen ord eller PIN-kod logga in på enheten. 

Innan du kan komma åt skol-eller arbets resurser kan din organisation kräva att du krypterar Android-enheten. Vissa nyare Android-enheter är krypterade som standard, färdiga.  

## <a name="turn-on-encryption"></a>Aktivera kryptering

Om Företagsportal eller Microsoft Intune-appen meddelar dig att du krypterar enheten utför du följande steg. 

> [!Note]
> Vissa Android-enheter från Huawei, vivo och OPPO kan inte krypteras. Läs mer [här](your-device-appears-encrypted-but-cp-says-otherwise-android.md).  

1. Ange ett lås för enhets skärmen.  
    a. Gå till **Inställningar** > **Låsskärm och säkerhet** > **Skärmlåstyp**.  
    b. Välj antingen **PIN**, **Password**eller **pattern**.  
    c. Konfigurera skärm låset genom att följa anvisningarna på skärmen.  

2. Gå tillbaka till **Lås skärmen och säkerhet** och välj **säker start**.
3. Välj **Kräv PIN-kod när enheten aktiverar** > **OK**.
4. Ange din PIN-kod för att bekräfta och kryptera enheten.
5. Öppna appen Företagsportal eller Microsoft Intune.
    * Användare av företagsportalen: Välj din enhet och tryck på **Kontrollera enhetsinställningar**. 
    * Microsoft Intune användare: du måste vänta tills sidan har uppdaterats, men när du gör det ska krypterings statusen ändras till kompatibel.  

Enheter som kör Android 4,4 och tidigare kanske inte har alternativet **säker start** . I så fall kan du utföra följande steg för att kryptera enheten.

1. Gå till **inställningar** > **säkerhets** > **kryptera enhet**. Etiketter på skärmen varierar mellan Android-enheter. Om du inte ser alternativet **kryptera enhet** , checka in:
    * **Lagring** > **lagrings kryptering**
    * **Lagrings** > **Lås skärmen och säkerhets** > **andra säkerhets inställningar** 

2. Följ anvisningarna på skärmen. Enheten kan starta om flera gånger under krypteringen.
3. Öppna appen Företagsportal eller Microsoft Intune.
    * Användare av företagsportalen: Välj din enhet och tryck på **Kontrollera enhetsinställningar**.  
    * Microsoft Intune användare: du måste vänta tills sidan har uppdaterats, men när du gör det ska krypterings statusen ändras till kompatibel.

## <a name="troubleshoot"></a>Felsöka  
**Problem**: du har redan krypterat enheten och

- Krypteringsknappen är inaktiverad.
- Du ser ett meddelande om att du fortfarande behöver kryptera enheten.
- Du får fel meddelanden när du försöker använda Företagsportal-eller Microsoft Intune-appen.

**Saker du kan prova**

- Kontrollera att enheten är laddad och inkopplad.  
- Kontrollera att du har ställt in en PIN-kod eller ett lösenord på enheten.  

Behöver du fortfarande hjälp? Kontakta företagets support (du hittar kontaktinformation på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980)) eller skriv till <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-teamet</a>.  
