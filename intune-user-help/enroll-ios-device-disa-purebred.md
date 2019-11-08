---
title: Registrera iOS-eller iPad-enhet med Intune-företagsportal-och DISA-purebred
description: Lär dig hur du registrerar en iOS-eller iPad-enhet och konfigurerar autentisering med härledd autentisering med DISA purebred.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c484b98466c1418016f4ebc6cc805e412d7891e
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415795"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-disa-purebred"></a>Konfigurera iOS-eller iPad-enhet med Företagsportal-och DISA-purebred  

Registrera din enhet med appen för Intune-företagsportal om du vill få säker mobil åtkomst till din organisations e-post, filer och appar. När enheten har registrerats blir den *hanterad*. Din organisation kan tilldela principer och appar till enheten via en MDM-provider för hantering av mobilenheter, t.ex. Intune.  

Under registreringen installerar du även en härledd autentiseringsuppgift på enheten. Din organisation kan kräva att du använder den härledda autentiseringsuppgiften som autentiseringsmetod vid åtkomst till resurser, eller för att signera och kryptera e-post. 

Du måste förmodligen konfigurera en härledd autentiseringsuppgift om du använder ett smartkort för att:

* Logga in på skolan eller Worker-appar, Wi-Fi och virtuella privata nätverk (VPN)
* Signera och kryptera skol-eller arbets-e-postmeddelanden med S/MIME-certifikat  

I den här artikeln kommer du att:  

   * Registrera en mobil iOS-eller iPad-enhet med Intune-företagsportal.  
   * Få en härledd autentiseringsuppgift från din organisations leverantör av härledda autentiseringsuppgifter, [Disa purebred](https://cyber.mil/pki-pke/purebred/).  

## <a name="what-are-derived-credentials"></a>Vad är härledda autentiseringsuppgifter?  
En härledd autentiseringsuppgift är ett certifikat som härleds från autentiseringsuppgifterna för smartkort och installeras på enheten. Den ger dig fjärråtkomst till arbets resurser och förhindrar obehöriga användare från att komma åt känslig information.  

Härledda autentiseringsuppgifter används för att: 
* Autentisera studenter och anställda som loggar in på skol-eller Worker-appar, Wi-Fi och VPN
* Signera och kryptera skol-eller arbets-e-postmeddelanden med S/MIME-certifikat

Härledda autentiseringsuppgifter är en implementering av riktlinjerna från National Institute of Standards and Technology (NIST) för härledda PIV-autentiseringsuppgifter (Personal Identity Verification) som en del av en Special Publication (SP) 800-157.  

## <a name="prerequisites"></a>Krav

 För att slutföra registreringen måste du ha:

* Ditt skol-eller Worker-smartkort
* Åtkomst till en dator eller kiosk där du kan logga in med smartkortet
* Din mobila enhet
* Intune-företagsportal-appen för iOS och iPad installerat på enheten   

Du måste också kontakta en purebred-agent eller en representant under installationen.      

## <a name="enroll-device"></a>Registrera enhet  
1. Öppna Företagsportal-appen för iOS/iPad på din mobila enhet och logga in med ditt arbets konto.  

2. Skriv ner skärm koden.  

    ![Exempel bild av Företagsportal app med meddelande och kod på skärmen.](./media/copy-code-intercede.png)  
3. Växla till den smartkort-aktiverade enheten och gå till https://microsoft.com/devicelogin. 
4. Ange den kod som du tidigare skrev ned.  

    ![Skärm bild av exempel på den Företagsportal webbplatsen "Ange kod".](./media/enter-code-intercede.png)   

5. Infoga smartkortet för att logga in.  
6. Gå tillbaka till Företagsportal-appen på din mobila enhet och följ anvisningarna på skärmen för att registrera enheten.  
7. När registreringen är klar meddelar Företagsportal dig att du ska konfigurera smartkortet. Tryck på meddelandet. Om du inte får ett meddelande kan du kontrol lera din e-post.   

    ![Exempel skärm bild av Företagsportal push-meddelande på enhetens start sida.](./media/action-required-in-app-intercede.png)  
8. På skärmen **Konfigurera mobilt smartkort-åtkomst** :  
    a. Tryck på länken till din organisations instruktioner. Om din organisation inte tillhandahåller ytterligare instruktioner kommer du att skickas till den här artikeln.  
    b. Öppna purebred-appen genom att klicka på **Öppna** .  

    ![Skärm bild av exemplet Företagsportal konfigurera åtkomst till mobil smartkort.](./media/smart-card-open-disa-purebred.png)  
9. När du uppmanas att tillåta Företagsportal att öppna purebred-appen väljer du **Öppna**.   

    ![Exempel skärm bild av Företagsportal-prompten för att öppna DISA purebred-appen.](./media/open-app-prompt-disa-purbred.png)  
10. När appen fungerar arbetar du med organisationens purebred-agent för att konfigurera och hämta konfigurations profilen för purebred för registrering.   
11. Gå till appen Inställningar > **allmänna** > **profiler & enhets hantering** > **Installera profil** och tryck på **Installera**.  
12. Ange ditt enhetslösenord.  
13. Installera profilen. Du kan behöva trycka på **Installera** mer än en gång för att starta installationen. 
14. Gå tillbaka till purebred-registrerings programmet. Följ purebred-agentens instruktioner för att fortsätta.  
 
15. När du har laddat ned konfigurations profilen går du till appen Inställningar > **allmänna** > **profiler & enhets hantering** > **Installera profil** och trycker på **Installera**.   
16.  Ange ditt enhetslösenord.
17. Installera profilen. Du kan behöva trycka på **Installera** mer än en gång för att starta installationen. 
18. När installationen är klar går du tillbaka till Företagsportal-appen.  
19.  Tryck på **Fortsätt**på skärmen **Konfigurera mobil åtkomst till mobil smartkort** .  

20. På skärmen **Importera certifikat** hämtar och importerar du de härledda autentiseringsuppgifter som du fick från Disa purebred.  

    a. Tryck på **Fortsätt**.   

    ![exempel skärm bild av skärmen Företagsportal ange import certifikat.](./media/import-certificate-disa-purebred.png)  
    b. Gå till iCloud-enheten **bläddra** > **platser** och tryck på **fler platser**.  

    ![exempel skärm bild av iCloud-enhet, bläddra meny för att markera fler platser.](./media/icloud-drive-more-locations.png)  
    c. Tryck på växeln för att aktivera **purebred nyckel kedja**.  

    ![Exempel skärm bild av iCloud-enhet, bläddra i vyn och markera att växeln purebred Key Chain är aktive rad.](./media/icloud-drive-enable-purebred-keychain.png)   

    d. Tryck på **purebred Credential-paket**.  

    ![exempel skärm bild av en iOS-skärm med ett alternativ paket för en valbar purebred.](./media/purebred-credential-package.png)  
    f. En lista över certifikat visas. Välj en och tryck sedan på **Importera nyckel**.  

    ![Exempel skärm bild av en lista över certifikat som kan väljas, med ett redan valt.](./media/import-purebred-keychain.png) 
21. Gå tillbaka till Företagsportal-appen och vänta tills Företagsportal har slutfört konfigurationen av enheten.   

## <a name="next-steps"></a>Nästa steg  
När registreringen är klar har du åtkomst till arbets resurser, till exempel e-post, Wi-Fi och alla appar som din organisation gör tillgängliga. Mer information om hur du hämtar, söker efter, installerar och avinstallerar appar i Företagsportal finns i:

* [Hantera appar från Företagsportal-webbplatsen](manage-apps-cpweb.md)  
* [Använda hanterade appar på enheten](use-managed-apps-on-your-device-ios.md)  

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).
