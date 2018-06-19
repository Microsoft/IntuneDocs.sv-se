---
title: Ta bort en Android-enhet från Intune | Microsoft Docs
description: Beskriver hur du avregistrerar en Android-enhet från Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
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
ms.openlocfilehash: ec3c0a1c8ce4e04f4d23fb01e7c2525d8f2eed5b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31018370"
---
# <a name="how-to-remove-your-android-device-from-intune"></a>Så här tar du bort en Android-enhet från Intune

När du tar bort din Android-enhet från Intune kan enheten inte längre komma åt företagets resurser.  Mer information om vad som händer när du tar bort enheten från hanteringen finns i [Vad händer om du avregistrerar din enhet från Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md)

## <a name="removing-the-device-from-the-company-portal-app"></a>Ta bort enheten från företagsportalappen

Ta bort enheten från Intune och företagsportalappen genom att följa dessa steg:

1. Öppna **menyn Åtgärder** genom att trycka på de tre lodräta punkterna i det övre högra hörnet av företagsportalappen.

   ![En bild av företagsportalappen för Android med åtgärdsmenyn öppnad i det övre högra hörnet. Det nya alternativet ”ta bort företagsportal” finns tillgängligt som det tredje alternativet under ”min profil” och ”inställningar” och ovanför ”användarvillkor”, ”hjälp och feedback” och ”om”.](./media/android_remove_cp_menu_action_after_1705.png)

2. Tryck på **Ta bort företagsportal**.

3. Ett meddelande kommer att visas som frågar om du är säker på att du vill ta bort företagsportalen. Den innehåller information om vad som händer när du avregistrerar din enhet. När du har läst det här meddelandet trycker du på **OK** för att ta bort appen.

   ![En bild av dialogrutan som visas när du har valt det nya alternativet ”ta bort företagsportalen” i åtgärdsmenyn. Dialogrutan informerar användaren att ”genom att ta bort företagsportalen kommer enheten inte längre att hanteras av företagets support och åtkomst till företagsdata, företagsappar och företagets e-post kan tas bort." Användaren ombes sedan att bekräfta att de vill ta bort företagsportalappen genom att välja ”Ja”.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>Ta bort data som samlas in av företagsportalappen

Så här tar du bort alla data som företagsportalappen för Android lagrar på din enhet:

-   Rensa appdata i Program -> Klicka på appen -> knappen ”Rensa data”
-   Ta bort mappen \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
