---
title: Kryptera Android-enhet för Intune | Microsoft Docs
description: Steg för att aktivera kryptering för Android-enhet om detta krävs av Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfc17c60412a1cfe90693216caa69ada3d2d2c9a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545245"
---
# <a name="encrypting-your-android-device"></a>Kryptera din Android-enhet

Enhetskryptering skyddar filer och mappar från obehörig åtkomst om enheten tappas bort eller blir stulen. När du har aktiverat kryptering för enheten kan kommer endast personer med rätt lösenord eller PIN-kod att kunna logga in på din enhet. 

Innan du kan komma åt resurser skolan eller arbetet, kräver din organisation att du krypterar Android-enheten. Vissa nyare Android-enheter krypteras som standard out-of the box.  

## <a name="turn-on-encryption"></a>Aktivera kryptering

Om Företagsportalen eller Microsoft Intune app uppmanas du att kryptera din enhet, utför du följande steg. 

> [!Note]
> Vissa Android-enheter från Huawei, Vivo och OPPO kan inte krypteras. Läs mer [här](your-device-appears-encrypted-but-cp-says-otherwise-android.md).  

1. Ange en skärmlås för enheten.  
    a. Gå till **Inställningar** > **Låsskärm och säkerhet** > **Skärmlåstyp**.  
    b. Välj antingen **PIN-kod**, **lösenord**, eller **mönstret**.  
    c. Följ instruktionerna på skärmen för att konfigurera ditt skärmlås.  

2. Gå tillbaka till **Låsskärm och säkerhet** och välj **säker Start**.
3. Välj **Kräv PIN-kod när du aktiverar enheten** > **OK**.
4. Ange din PIN-kod för att bekräfta och kryptera din enhet.
5. Öppna appen företagsportal eller Microsoft Intune.
    * Användare av företagsportalen: Välj din enhet och tryck på **Kontrollera enhetsinställningar**. 
    * Microsoft Intune-användare: du måste vänta tills sidan uppdateringar, men när det gör det, bör din kryptering statusen ändras till kompatibla.  

Enheter som kör Android 4.4 och tidigare kanske inte har den **säker Start** alternativet. I så fall utför följande steg för att kryptera din enhet.

1. Gå till **inställningar** > **Security** > **kryptera enheten**. På skärmen etiketter varierar mellan Android-enheter. Om du inte ser den **kryptera enheten** alternativet, checka in:
    * **Storage** > **lagringskryptering**
    * **Storage** > **Låsskärm och säkerhet** > **andra säkerhetsinställningar** 

2. Följ anvisningarna på skärmen. Enheten kan starta om flera gånger under krypteringen.
3. Öppna appen företagsportal eller Microsoft Intune.
    * Användare av företagsportalen: Välj din enhet och tryck på **Kontrollera enhetsinställningar**.  
    * Microsoft Intune-användare: du måste vänta tills sidan uppdateringar, men när det gör det, bör din kryptering statusen ändras till kompatibla.

## <a name="troubleshoot"></a>Felsöka  
**Problemet**: du har redan krypterat enheten och

- Krypteringsknappen är inaktiverad.
- Du ser ett meddelande om att du fortfarande behöver kryptera enheten.
- Fel uppstår när du försöker använda appen företagsportal eller Microsoft Intune.

**Saker du kan prova**

- Kontrollera att enheten är laddad och inkopplad.  
- Kontrollera att du har ställt in en PIN-kod eller ett lösenord på enheten.  

Behöver du fortfarande hjälp? Kontakta företagets support (du hittar kontaktinformation på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980)) eller skriv till <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-teamet</a>.  
