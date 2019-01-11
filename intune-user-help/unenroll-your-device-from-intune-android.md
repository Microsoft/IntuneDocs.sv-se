---
title: Ta bort en Android-enhet från Intune | Microsoft Docs
description: Ta bort en Android-enhet från Intune-företagsportalen
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2019
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
ms.openlocfilehash: 75b26e178badbaa7905199eb91490134d2b72ba9
ms.sourcegitcommit: 61ed365f7f8826451c41bcab5e19bef97b5a3c72
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/05/2019
ms.locfileid: "54057346"
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
Företagsportalen är en app för enhetshantering. Den kan inte avinstalleras förrän du [avregistrerat din enhet från dess hantering](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management). När du har gjort det trycker du på och håller ned ikonen för företagsportalappen tills du ser **Avinstallera**. Tryck på **Avinstallera** för att ta bort appen från enheten.  

Du kan också trycka på **Inställningar** > **Appar** > **Företagsportal** > **Avinstallera**.  

### <a name="remove-company-portal-app-as-device-administrator"></a>Ta bort företagsportalappen som enhetsadministratör  
Som en sista utväg kan du avinstallera appen från din enhet genom att ta bort den som enhetsadministratör.  

Om du har en enhet som ägs av företaget kanske din organisation kräver att företagsportalen alltid ska finnas på din enhet. Om du avinstallerar den kan du förlora åtkomst till skyddade företagsresurser, till exempel e-post, appar, Wi-Fi eller VPN, tills appen har installerats om. Mer information om hur du installerar, uppdaterar eller tar bort obligatoriska appar finns i [Lägga till appar i Microsoft Intune](https://docs.microsoft.com/intune/apps-add#apps-that-are-added-automatically-by-intune).  

Slutför stegen nedan för att inaktivera företagsportalen som enhetsadministratör. De faktiska namnen på varje inställning kan skilja sig åt beroende på Android-enhet.  

**Android-steg, alternativ 1**:  
1. Välj **Inställningar** > **Säkerhet** > **Övriga säkerhetsinställningar** > **Enhetsadministratörer**.  
2. Avmarkera **Företagsportal**.  

**Android-steg, alternativ 2**:  
1. Välj **Inställningar** > **Låsskärm och säkerhet** > **Övriga säkerhetsinställningar** > **Enhetsadministratörsappar**.  
2. Avmarkera **Företagsportal**.    

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980)
