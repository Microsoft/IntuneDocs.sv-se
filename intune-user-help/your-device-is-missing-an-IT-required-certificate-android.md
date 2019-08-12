---
title: Din enhet saknar ett certifikat | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 16c6708fb730c459f41fec573a939bfb4fb5ddda
ms.sourcegitcommit: 549352bdea93cc2809e3e0010bfcc10bd44dc728
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68862141"
---
# <a name="install-missing-certificate-required-by-your-organization"></a>Installera certifikatet som saknas som krävs av din organisation  

Om enheten inte är registrerad i Intune och saknar ett nödvändigt certifikat, kan du inte logga in på Företagsportal-appen. Följande meddelande visas när du försöker logga in:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Det finns två alternativ du kan försöka hämta det certifikat som krävs och få enheten registrerat. 

- Aktivera webb läsar åtkomst i Företagsportal app.
- Identifiera det saknade certifikatet på en företags- eller skoldator. Sök sedan på Internet för att hämta certifikatet som saknas. 

Slutför stegen för att aktivera webb läsar åtkomst först. Om du fortfarande inte kan registrera enheten följer du anvisningarna för att leta upp certifikatet på Internet. 

## <a name="enable-browser-access"></a>Aktivera webb läsar åtkomst
Slutför de här stegen för att aktivera webb läsar åtkomst. När du har aktiverat åtkomst kommer Företagsportal att installera lämpligt certifikat och fortsätta registreringen.    

1. I Företagsportal-appen går du till det högra hörnet och väljer menyn.  
2. Välj **Inställningar**.  
3. Bredvid Aktivera **webb läsar** åtkomst **väljer**du aktivera.  
4. På skärmen enhets administratör väljer **du aktivera.** 

## <a name="identify-and-download-the-missing-certificate-through-web-search"></a>Identifiera och hämta certifikatet som saknas via Webbs ökning
Slutför de här stegen för att identifiera och installera certifikatet på enheten manuellt.  

1. Öppna Internet Explorer på en dator. Kontakta företagets support om du inte har en dator som kan användas för detta ändamål. Kontaktuppgifter till företagets support finns på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980).

2. Öppna [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980) och logga in med autentiseringsuppgifterna för ditt arbets- eller skolkonto.

3. Längst till höger i adressfältet i webbläsaren väljer du den symbol som ser ut som ett hänglås, se följande skärmbild.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    Om du inte ser hänglåssymbolen avbryter du och kontaktar företagets support. Låset innebär att du är inloggad på ett säkert sätt. Om du ser symbolen är det bara att fortsätta.

4. Klicka på **Visa certifikat**.

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. Välj fliken **Certifieringssökväg** och leta sedan reda på certifikatet du behöver hämta via Internet. Namnet på certifikatet du behöver finns på samma plats som certifikatet som är markerat på den föregående skärmbilden.

6. Använd en sökmotor, till exempel Bing eller Google, och sök efter namnet på det saknade certifikatet som du identifierade i föregående avsnitt. Certifikatet kan ha olika tillägg, till exempel .crt eller .pem.

7. Hämta rotcertifikatet från webbplatsen.

8. När certifikatet har hämtats drar du ned från enhetens övre kant för att öppna meddelandena. Tryck sedan på namnet på certifikatet i meddelandelistan.

4. I dialogrutan **Namnge certifikatet** som visas i följande skärmbild godkänner du standardcertifikatnamnet.

5. Kontrollera att **Autentiseringsuppgift** är inställt på **Används för VPN och appar** och tryck sedan på **OK**.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. Stäng företagsportalappen.

7. Öppna företagsportalappen igen. Du bör nu kunna logga in på företagsportalappen. Kontakta företagets support om du behöver hjälp.

Om du ser samma meddelande om att ett certifikat saknas som visades tidigare, och du har följt metoden, finns det troligtvis fortfarande ett annat certifikat som företagets support måste hjälpa dig att installera. Kontakta företagets support för att få hjälp med den kontaktinformation som finns på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980).

## <a name="next-steps"></a>Nästa steg  

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  
