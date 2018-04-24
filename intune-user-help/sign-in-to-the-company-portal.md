---
title: Så här loggar du in i företagsportalappen | Microsoft Docs
description: Lär dig hur du loggar in på företagsportalappen på flera plattformar.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 84f8e70d8321ca27d689d13472b69007a1d6c186
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="how-do-i-sign-in-to-the-company-portal-app---user-story-1132123--"></a>Hur loggar jag in på företagsportalappen? <!--User Story 1132123-->

Du använder företagsportalappen för att komma åt företagets resurser, t.ex. e-post och affärsappar. Det finns två sätt att logga in på företagsportalen:

* Med din e-postadress och lösenord för arbetet
* Logga in från en annan enhet

Även om följande bilder är för iOS är processen praktiskt taget identisk för Android- och Windows-enheter.

## <a name="signing-in-with-your-email-address-and-password"></a>Med din e-postadress och lösenord

1. Öppna företagsportalappen på enheten och tryck på **Logga in**.

   ![Företagsportalens inloggningssida med en ikon för en person framför en grafisk representation av en webbplats. Nedanför finns texten ”Få åtkomst till företagets resurser och skydda dem” och knappen ”Logga in”. En länk längst ner leder till Microsofts information om sekretess och cookies.](/intune-user-help/media/cp_ios_aad_signin_after_1804_001.png)

   Har du inte företagsportalappen? Ta reda på hur du installerar och laddar ned den för [iOS](install-and-sign-in-to-the-intune-company-portal-app-ios.md) eller [Android](install-the-company-portal-app-android.md).

2. Ange ditt **Arbets- eller skolkonto** och tryck på **Nästa**.

   ![Användaren ombeds endast att ange sin e-postadress, i stället för sin e-post och lösenord på samma skärm.](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. Ange ditt lösenord och tryck på **Logga in**.

   ![Användaren uppmanas att ange lösenordet när e-postadressen har accepterats.](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. När företagsportalen har godkänt din inloggning loggas du in och får åtkomst till företagets resurser.   

   ![Efter att genomgått autentiseringsprocessen loggas företagsportalappen in, vilket visas med en förloppsindikator.](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="signing-in-with-certificate-based-authentication"></a>Logga in med certifikatbaserad autentisering

1.  Öppna företagsportalappen på din enhet.

2.  Ange ditt **arbets- eller skolkonto**.

3.  Tryck på länken **Logga in med ett certifikat**.

4.  Tryck på **Fortsätt** för att använda certifikatet.

## <a name="signing-in-from-another-device"></a>Logga in från en annan enhet

Om du inte använder ett lösenord för att logga in till företagets resurser kan du använda en annan enhet som ett sätt att bekräfta att du är rätt person med rätt åtkomstnivå. Om företaget använder smartkort för att få åtkomst till datorerna är det sannolikt att du behöver logga in med en annan enhet.

1. I stället för att ange din e-postadress väljer du länken **Logga in från en annan enhet** under textrutan för e-postadresser.

   ![Företagsportalens inloggningssida uppmanar användaren att ange en e-postadress.  Nedanför är knappen ”Nästa” och en länk till ”Logga in från en annan enhet”. Det finns också en länk till ”Kan du inte öppna ditt konto?” En länk längst ner leder till Microsofts information om sekretess och cookies.](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. Du får en unik engångskod som du kan använda för att logga in på företagsportalen.

   ![Instruktioner för att gå till sidan https://microsoft.com/devicelogin visas, med ett unikt lösenord från din arbetsdator. Därefter använder du koden för att logga in.](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. Öppna webbläsaren på din andra enhet och gå till [https://microsoft.com/devicelogin](https://microsoft.com/devicelogin) för att ange koden.

   ![En bild av användarens webbläsare på arbetsdatorn, i stället för företagsportalappen. Sidan ”Inloggning på enhet” visas och uppmanar användarna ange koden de fick i företagsportalsappen.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. När sidan **Device Login** (Enhetsinloggning) verifierar koden väljer du __Fortsätt__ för att låta företagsportalen logga in din andra enhet.

   ![Användaren har matat in sin unika kod i fältet och webbplatsen ”Inloggning på enhet” har begärt en bekräftelse på att Intunes företagsportal är rätt app för att få behörighet att logga in.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. Du kan stänga fönstret när koden har verifierats.

   ![En bekräftelsesida som anger att användaren har loggat in i företagsportalsappen på sin enhet visas nu, och den här sidan kan stängas.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. På din ursprungliga enhet börjar företagsportalappen att logga in.

   ![Efter att ha genomgått autentiseringsprocessen loggas företagsportalappen in, vilket visas med en förloppsindikator.](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
