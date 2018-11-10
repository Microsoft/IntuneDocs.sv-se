---
title: Ta bort en Android-enhet från Intune | Microsoft Docs
description: Beskriver hur du avregistrerar en Android-enhet från Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: d932005c955afed7f16e9766b559b77b2cd43182
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959493"
---
# <a name="unenroll-your-android-device-from-management"></a>Avregistrera din Android-enhet från hanteringen  

Ta bort en registrerad Android-enhet så att den inte längre hanteras av din organisation. Den här artikeln beskriver hur du tar bort enheten från företagsportalappen. När du har tagit bort enheten:  

* Enheten förlorar åtkomst till organisationens skyddade data och resurser.
* Enheten visas inte längre på Företagsportalen.
* Du kan inte installera appar från Företagsportalen.
* Eventuella inställningar som ändrades på enheten när du lade till den (t.ex. inaktivering av kameran eller krav på en viss lösenordslängd) gäller inte längre.  

1. Tryck på de tre lodräta punkterna i det övre högra hörnet på Företagsportalen. Åtgärdsmenyn öppnas.

   ![En bild av företagsportalappen för Android med åtgärdsmenyn öppnad i det övre högra hörnet. Det nya alternativet ”ta bort företagsportal” finns tillgängligt som det tredje alternativet under ”min profil” och ”inställningar” och ovanför ”användarvillkor”, ”hjälp och feedback” och ”om”.](./media/android_remove_cp_menu_action_after_1705.png)

2. Tryck på **Ta bort företagsportal**.  

3. Ett meddelande visas med information om vad som händer när du avregistrerar din enhet. Tryck på **OK** för att bekräfta att du vill ta bort enheten från Företagsportalen.

   ![En bild av dialogrutan som visas när du har valt det nya alternativet ”ta bort företagsportalen” i åtgärdsmenyn. Dialogrutan informerar användaren att ”genom att ta bort företagsportalen kommer enheten inte längre att hanteras av företagets support och åtkomst till företagsdata, företagsappar och företagets e-post kan tas bort." Användaren ombes sedan att bekräfta att de vill ta bort företagsportalappen genom att välja ”Ja”.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>Ta bort data som samlas in av företagsportalappen  

Så här tar du bort alla data som företagsportalappen för Android lagrar på din enhet:

-   Rensa appdata i Program -> Klicka på appen -> knappen ”Rensa data”
-   Ta bort mappen \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal

## <a name="uninstall-the-company-portal-app"></a>Avinstallera företagsportalappen  
Eftersom Företagsportalen är en enhetshanteringsapp går det inte att avinstallera den förrän du [avregistrerat din enhet från dess hantering](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management). När du har gjort det trycker du på och håller ned ikonen för företagsportalappen tills du ser **Avinstallera**. Tryck på **Avinstallera** för att ta bort appen från enheten.  

Du kan också trycka på **Inställningar** > **Appar** > **Företagsportal** > **Avinstallera**.  

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980)
