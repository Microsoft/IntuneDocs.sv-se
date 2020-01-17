---
title: Registrera iOS-eller iPad-enhet med Intune-företagsportal och åsidosätta
description: Lär dig hur du registrerar en iOS-eller iPad-enhet och konfigurerar autentisering av härledd autentisering med överta.
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
ms.collection: ''
ms.openlocfilehash: 2a2c3264b2894ad81a64e7aaa7d3697f069dbfbb
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856295"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-intercede"></a>Konfigurera iOS-eller iPad-enhet med Företagsportal och åsidosätta

Registrera din enhet med appen för Intune-företagsportal om du vill få säker mobil åtkomst till din organisations e-post, filer och appar.  När enheten har registrerats blir den *hanterad*. Din organisation kan tilldela principer och appar till enheten via en MDM-provider för hantering av mobilenheter, t.ex. Intune.  

Under registreringen installerar du även en härledd autentiseringsuppgift på enheten. Din organisation kan kräva att du använder den härledda autentiseringsuppgiften som autentiseringsmetod vid åtkomst till resurser, eller för att signera och kryptera e-post. 

Du måste förmodligen konfigurera en härledd autentiseringsuppgift om du använder ett smartkort för att:

* Logga in på skolan eller Worker-appar, Wi-Fi och virtuella privata nätverk (VPN)
* Signera och kryptera skol-eller arbets-e-postmeddelanden med S/MIME-certifikat  

I den här artikeln kommer du att:  

* Registrera en mobil iOS-eller iPad-enhet med Intune-företagsportal.  
* Få en härledd autentiseringsuppgift från din organisations leverantör av härledda autentiseringsuppgifter, och [Åsidosätt](https://www.intercede.com/).   


## <a name="what-are-derived-credentials"></a>Vad är härledda autentiseringsuppgifter?  
En härledd autentiseringsuppgift är ett certifikat som härleds från autentiseringsuppgifterna för smartkort och installeras på enheten. Den ger dig fjärråtkomst till arbets resurser och förhindrar obehöriga användare från att komma åt känslig information.  

Härledda autentiseringsuppgifter används för att: 
* Autentisera studenter och anställda som loggar in på skol-eller Worker-appar, Wi-Fi och VPN
* Signera och kryptera skol-eller arbets-e-postmeddelanden med S/MIME-certifikat  

Härledda autentiseringsuppgifter är en implementering av riktlinjerna från National Institute of Standards and Technology (NIST) för härledda PIV-autentiseringsuppgifter (Personal Identity Verification) som en del av en Special Publication (SP) 800-157.  

## <a name="prerequisites"></a>Krav

 För att slutföra registreringen måste du ha:

* Ditt skol-eller Worker-smartkort
* Åtkomst till en dator eller en självbetjänings kiosk där du kan logga in med smartkortet
* Din mobila enhet
* Intune-företagsportal-appen för iOS och iPad installerat på enheten


## <a name="enroll-device"></a>Registrera enhet  
1. Öppna Företagsportal-appen för iOS/iPad på din mobila enhet och logga in med ditt arbets konto.  
2. Skriv ner koden som visas på skärmen.  

    ![Exempel bild av Företagsportal app med meddelande och kod på skärmen.](./media/copy-code-intercede.png)  
1. Växla till den smartkort-aktiverade enheten och gå till https://microsoft.com/devicelogin. 

1. Ange den kod som du tidigare skrev ned.
 
2. Infoga smartkortet för att logga in.   

3. Gå tillbaka till Företagsportal-appen på din mobila enhet och följ anvisningarna på skärmen för att registrera enheten.  
4. När registreringen är klar meddelar Företagsportal dig att du ska konfigurera smartkortet. Tryck på meddelandet. Om du inte får ett meddelande kan du kontrol lera din e-post.   

    ![Exempel skärm bild av Företagsportal push-meddelande på enhetens start sida.](./media/action-required-in-app-intercede.png)  

5. På skärmen **Konfigurera mobilt smartkort-åtkomst** :  
    a. Tryck på länken till organisationens konfigurations instruktioner. Om din organisation inte tillhandahåller ytterligare instruktioner kommer du att skickas till den här artikeln.  
    b. Tryck på **börja**.  

    ![Skärm bild av exemplet Företagsportal konfigurera åtkomst till mobil smartkort.](./media/smart-card-info-intercede.png)  

6. Växla till din Smart Card-aktiverade enhet eller självbetjänings kiosk och öppna MyID-appen. Logga in med dina autentiseringsuppgifter för arbetet.  
7. Välj alternativet för att begära ditt ID. 
8. När du tillfrågas om vilken profil du vill använda väljer du alternativet att aktivera med en Mobile-autentiseringsuppgift. En QR-kod visas.  
9. Återgå till din mobila enhet. Tryck på **Fortsätt**på sidan företagsportal > **Hämta QR-kod** .  

    ![Exempel skärm bild av skärmen Företagsportal Hämta QR-kod.](./media/get-qr-code-intercede.png) 
 
10. Tryck på **Använd kamera** > **OK**.  

    ![Exempel skärm bild av en Företagsportal fråga som ber om behörighet att tillåta åtkomst till kameran.](./media/allow-cp-camera-access-intercede.png)  

11. Skanna avbildningen av QR-koden som finns på din Smart Cards-aktiverade enhet. 
12. Vänta tills Företagsportal har slutfört konfigurationen av enheten.  

## <a name="next-steps"></a>Nästa steg  
När registreringen är klar har du åtkomst till arbets resurser, till exempel e-post, Wi-Fi och alla appar som din organisation gör tillgängliga. Mer information om hur du hämtar, söker efter, installerar och avinstallerar appar i Företagsportal finns i:

* [Hantera appar från Företagsportal-webbplatsen](manage-apps-cpweb.md)  
* [Använda hanterade appar på enheten](use-managed-apps-on-your-device-ios.md)  

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).
