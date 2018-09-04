---
title: Skydda en Android-enhet med kryptering | Microsoft Docs
description: Skydda din Android-enhet
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2017
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
ms.openlocfilehash: dfb70327737bcfe9e6bd2ded964a07a00f9d7610
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43148957"
---
# <a name="how-to-protect-your-android-device-using-encryption"></a>Skydda en Android-enhet med kryptering

När du krypterar en enhet omsluter du informationen på den i ett lager med skyddande kod som förhindrar att obehöriga personer får åtkomst till den. Organisationen kräver att du krypterar din Android-enhet för att skydda innan du kommer åt företagsfiler, -e-post eller -data som ett steg mot att se till att informationen är skyddad.

> [!Note]
> Vissa Android-enheter, inklusive vissa av Huawei och de som gjorts av Vivo och OPPO, kan inte krypteras. Läs mer [här](your-device-appears-encrypted-but-cp-says-otherwise-android.md).

Om du avregistrerar telefonen förblir den krypterad.

1.  Kontrollera att en PIN-kod eller ett lösenord för skärmlås har angetts för enheten.

2.  Under **Inställningar** väljer du **Säkerhet** > **Kryptera enhet**.
    (På vissa telefoner måste du välja **Lagring**  >  **Lagringskryptering** eller **Lagring**  > **Låsskärm och säkerhet** > **Andra säkerhetsinställningar** för att hitta krypteringsalternativet).

3.  Följ anvisningarna på skärmen. Enheten kan starta om flera gånger under krypteringen.

### <a name="what-to-do-if-you-have-issues"></a>Vad du gör om du har problem
**Problem**: Du har redan krypterat enheten och du ser något av följande:

- Krypteringsknappen är inaktiverad.
- Du ser ett meddelande om att du fortfarande behöver kryptera enheten.
- Fel uppstår när du försöker använda företagsportalappen.

**Saker du kan prova**

- Kontrollera att enheten är laddad och inkopplad.
- Kontrollera att du har ställt in en PIN-kod eller ett lösenord på enheten.
- Om du redan har ställt in en PIN-kod eller ett lösenord på enheten kan du prova följande steg, som företagets support kan kräva för att göra enheten säkrare. Menynamnen i de här stegen kan skilja sig något från de som visas på din enhet, beroende på vilken typ av Android-enhet du har.

    1. Gå till **Inställningar** > **Låsskärm och säkerhet** > **Skärmlås**. Bekräfta din aktuella PIN-kod eller ditt lösenord.

    2. På skärmen **Välj skärmlås** väljer du vilken typ av skärmlås du vill använda. 

    3. När du har valt skärmlås går du tillbaka till skärmen **Låsskärm och säkerhet** och väljer **Säker start**. 
    
    4. På skärmen **Säker start** trycker du på **Kräv PIN-kod för att starta enheten** och sedan på **Fortsätt**.

    5. Välj en PIN-kod (du kan ange samma som du angav tidigare) och tryck på **Bekräfta din PIN-kod**.

    6. Öppna företagsportalappen, välj din enhet och tryck på **Kontrollera efterlevnad**.

Behöver du fortfarande hjälp? Kontakta företagets support (du hittar kontaktinformation på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980)) eller skriv till <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-teamet</a>.
