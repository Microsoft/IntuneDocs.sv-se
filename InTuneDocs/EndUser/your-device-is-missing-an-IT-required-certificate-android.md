---
title: Din enhet saknar ett certifikat | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d6fcfac7c8bd469f5163ec9b4017ae8c3d486428
ms.openlocfilehash: 88770ba06718a767f8229e1b5aa4d543c87bc852

---

# <a name="your-android-device-is-missing-a-certificate-required-by-your-it-admin"></a>Android-enheten saknar ett certifikat som krävs av IT-administratören

Om din enhet inte har registrerats i Intune och den saknar ett certifikat som krävs av IT-administratören kan du inte logga in på företagsportalappen. Följande meddelande visas när du försöker logga in:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Det finns två steg som du behöver utföra för att lösa problemet och hämta certifikatet som krävs:

- Identifiera det saknade certifikatet i företags- eller skoldatorn.
- Hämta det saknade certifikatet via Internet på enheten.

## <a name="identify-the-missing-certificate-by-looking-on-a-company-or-school-pc"></a>Identifiera det saknade certifikatet i företags- eller skoldatorn

1. Öppna Internet Explorer på en dator. Kontakta IT-administratören om du inte har en dator som kan användas för detta ändamål. Se [företagsportalens webbplats](http://portal.manage.microsoft.com) för att hitta IT-administratörens kontaktuppgifter.

2. Öppna [företagsportalens webbplats](http://portal.manage.microsoft.com) och logga in med autentiseringsuppgifterna för ditt arbets- eller skolkonto.

3. Längst till höger i adressfältet i webbläsaren väljer du den symbol som ser ut som ett hänglås, se följande skärmbild.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    Om du inte ser hänglåssymbolen avbryter du och kontaktar IT-administratören. Låset innebär att du är inloggad på ett säkert sätt. Om du ser symbolen är det bara att fortsätta.

4. Klicka på **Visa certifikat**.

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. Välj fliken **Certifieringssökväg** i dialogrutan **Certifikat** och leta sedan reda på certifikatet du behöver hämta via Internet. Namnet på certifikatet du behöver finns på samma plats som certifikatet som är markerat på den föregående skärmbilden.

## <a name="download-and-install-the-missing-certificate-on-your-android-mobile-device"></a>Hämta och installera det saknade certifikatet på din Android-enhet

1. Använd en sökmotor, till exempel Bing eller Google, och sök efter namnet på det saknade certifikatet som du identifierade i föregående avsnitt. Certifikatet kan ha olika tillägg, till exempel .crt eller .pem.

2. Hämta rotcertifikatet från webbplatsen.

3. När certifikatet har hämtats drar du ned från enhetens övre kant för att öppna meddelandena. Tryck sedan på namnet på certifikatet i meddelandelistan.

4. I dialogrutan **Namnge certifikatet** som visas i följande skärmbild godkänner du standardcertifikatnamnet.

5. Kontrollera att **Autentiseringsuppgift** är inställt på **Används för VPN och appar** och tryck sedan på **OK**.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. Stäng företagsportalappen.

7. Öppna företagsportalappen igen. Du bör nu kunna logga in på företagsportalappen. Kontakta IT-administratören om du behöver hjälp.

Om du ser samma meddelande om att ett certifikat saknas som visades tidigare, och du har följt metoden, finns det troligtvis fortfarande ett annat certifikat som IT-administratören måste hjälpa dig att installera. Kontakta IT-administratören för att få hjälp med den kontaktinformation som finns på [företagsportalens webbplats](http://portal.manage.microsoft.com).



<!--HONumber=Jan17_HO1-->

