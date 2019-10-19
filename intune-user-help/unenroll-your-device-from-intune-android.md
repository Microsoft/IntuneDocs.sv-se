---
title: Ta bort en Android-enhet från Intune | Microsoft Docs
description: Ta bort en Android-enhet från Intune-företagsportalen
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
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb1538d484590a19eb7525a1451b5082ebab245d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506046"
---
# <a name="unenroll-your-android-device-from-management"></a>Avregistrera din Android-enhet från hanteringen  

Ta bort en registrerad Android-enhet så att den inte längre hanteras av din organisation. Den här artikeln beskriver hur du tar bort enheten från företagsportalappen. När du har tagit bort enheten:  

* Enheten förlorar åtkomst till organisationens skyddade data och resurser.
* Enheten visas inte längre på Företagsportalen.
* Du kan inte installera appar från Företagsportalen.
* Eventuella inställningar som ändrades på enheten när du lade till den (t.ex. inaktivering av kameran eller krav på en viss lösenordslängd) gäller inte längre.  

> [!NOTE]
> Det går inte att avregistrera eller ta bort företagsägda enheter från Microsoft Intune-appen. Enheten registrerades under den första installationen av enheten och måste registreras för att få åtkomst till din organisations resurser.  

1. Tryck på de tre lodräta punkterna i det övre högra hörnet på Företagsportalen. Åtgärdsmenyn öppnas.

   ![En skärmbild av företagsportalappen för Android med åtgärdsmenyn öppnad i det övre högra hörnet. Det nya alternativet ”ta bort företagsportal” finns tillgängligt som det tredje alternativet under ”min profil” och ”inställningar” och ovanför ”användarvillkor”, ”hjälp och feedback” och ”om”.](./media/android_remove_cp_menu_action_after_1705.png)

2. Tryck på **Ta bort företagsportal**.  

3. Ett meddelande visas med information om vad som händer när du avregistrerar din enhet. Tryck på **OK** för att bekräfta att du vill ta bort enheten från Företagsportalen.

   ![En skärmbild av bekräftelsen som visas när du har valt det nya alternativet ”ta bort företagsportalen” i åtgärdsmenyn.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="remove-data-collected-by-the-company-portal-app"></a>Ta bort data som samlas in av företagsportalappen  

Så här tar du bort alla data som företagsportalappen för Android lagrar på din enhet:

- Rensa appdata genom att trycka på **Program** > **[*appens namn*]**  > **Rensa data**.
- Ta bort följande mapp: \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal.

## <a name="uninstall-the-company-portal-app"></a>Avinstallera företagsportalappen

Företagsportalen är en app för enhetshantering. Den kan inte avinstalleras förrän du avregistrerat din enhet från dess hantering. När du har gjort det trycker du på och håller ned ikonen för företagsportalappen tills du ser **Avinstallera**. Tryck på **Avinstallera** för att ta bort appen från enheten.  

Du kan också trycka på **Inställningar** > **Appar** > **Företagsportal** > **Avinstallera**.  

### <a name="remove-the-company-portal-app-as-a-device-administrator"></a>Ta bort företagsportalappen som enhetsadministratör

Som en sista utväg kan du avinstallera appen från din enhet som enhetsadministratör.  

Om du har en enhet som ägs av företaget kanske din organisation kräver att företagsportalen alltid ska finnas på din enhet. Om du avinstallerar den kan du förlora åtkomst till skyddade företagsresurser, till exempel e-post, appar, Wi-Fi eller VPN, tills appen har installerats om. Mer information om hur du installerar, uppdaterar eller tar bort obligatoriska appar finns i [Lägga till appar i Microsoft Intune](/intune/apps/apps-add#apps-that-are-added-automatically-by-intune).

Så här inaktiverar du företagsportalen som enhetsadministratör. De faktiska namnen på varje inställning kan skilja sig åt beroende på Android-enhet.  

**Alternativ 1**:  

1. Välj **Inställningar** > **Säkerhet** > **Övriga säkerhetsinställningar** > **Enhetsadministratörer**.  
2. Avmarkera **Företagsportal**.  

**Alternativ 2**:

1. Välj **Inställningar** > **Låsskärm och säkerhet** > **Övriga säkerhetsinställningar** > **Enhetsadministratörsappar**.
2. Avmarkera **Företagsportal**.

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).
