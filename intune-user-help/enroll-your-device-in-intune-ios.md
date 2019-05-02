---
title: Konfigurera iOS-enhetsåtkomst till företagsresurser | Microsoft Docs
description: Beskriver hur du hämtar en iOS-enhet som hanteras av Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/05/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d0c7ac239a67a51ba7165771206883f3c46f5f55
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292432"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Konfigurera iOS-enhetsåtkomst till företagsresurser  

Registrera din iOS-enhet i Intune-företagsportalappen för att få säker åtkomst till organisationens e-post, filer och appar.

När enheten har registrerats blir *hanteras*. Din organisation kan tilldela principer och appar till enheten via en mobil enhet management (MDM)-provider, t.ex Intune.  

För att kunna komma åt arbets- eller skolinformation från din enhet måste du konfigurera enheten så att den matchar organisationens önskade inställningar. Den här artikeln beskriver hur du använder Företagsportalen registrerar du enheten och underhålla inställningen krav som din organisation. 

> [!NOTE]
> Om du försökte komma åt företagets e-post i e-postprogrammet och du fick ett meddelande om att enheten måste vara hanterad, är du på rätt plats. Följ anvisningarna nedan för att få åtkomst till din e-post och andra företagsresurser på iOS-enheten.  

## <a name="what-to-expect-from-the-company-portal-app"></a>Vad du kan förvänta dig av företagsportalappen  

### <a name="security"></a>Säkerhet  
Under installationen kräver appen att du autentiserar dig själv hos organisationen. Du informeras sedan om eventuella enhetsinställningar som du behöver uppdatera. Organisationer anger exempelvis ofta krav på lägsta eller högsta antal tecken i lösenordet som du måste uppfylla.     

### <a name="protection"></a>Skydd  
När enheten har registrerats fortsätter företagsportalappen att se till att enheten är skyddad. Om du till exempel installerar en app från en ej betrodd källa kommer appen meddela dig och återkallar ibland åtkomst till företagets data. Den här typen av princip är vanligt i organisationer och kräver ofta att avinstallera appen ej betrodda innan du kan få åtkomst.  

### <a name="setting-notifications"></a>Konfigurera meddelanden  
Om organisationen inför ett nytt säkerhetskrav efter registreringen, t.ex. multifaktorautentisering, meddelar företagsportalappen dig. Du får möjlighet att justera dina inställningar så att du kan fortsätta arbeta från enheten.  

Mer information om registrering finns i [Vad händer när jag installerar företagsportalappen och registrerar min enhet?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Registrera din iOS-enhet  

Gå till appbutiken för att ladda ned och installera den [företagsportalappen](install-and-sign-in-to-the-intune-company-portal-app-ios.md) på din enhet. Du måste också att upprätthålla en Wi-Fi-anslutning och har åtkomst till Safari under registreringen. 

Pausar under mer än ett par minuter under registreringen kan det leda till att appen att Stäng eller avsluta installationen. Om detta inträffar kan du öppna företagsportalappen och försök igen.  

1. Öppna företagsportalen och logga in med ditt arbets- eller skolkonto. 

    ![Exemplet på skärmbilden av företagsportalappen, logga in.](./media/ios-01-cp-enroll-1903.PNG)  

2. När du uppmanas att ta emot meddelanden i Företagsportalen trycker du på **Tillåt.** Företagsportalen använder meddelanden för att varna dig om till exempel din Enhetsinställningar behöver uppdateras. 

    ![Exemplet på skärmbilden av Företagsportalens startsida, ”meddelanden” fråga.](./media/ios-04-cp-enroll-1903.PNG)  

3. På den **Ställ in åtkomst** väljer **börjar.**  

     ![Exemplet på skärmbilden av Företagsportalen, ”Ställ in åtkomst” skärmen.](./media/ios-05-cp-enroll-1903.PNG)  

4. Läs igenom listan med enhetsinformation som din organisation kan och inte kan se. Tryck sedan på **Fortsätt**.  

5. Läs igenom anvisningarna på den **vad händer nu?** skärmen. När du är klar trycker du på om du vill ladda ned och installera hanteringsprofilen **Fortsätt**.  

 > [!IMPORTANT]
> Dessa nästa steg och skärmar varierar beroende på din iOS-version. Följ anvisningarna för din iOS-version. 

6. Safari öppnas webbplatsen företagsportal på enheten. När du uppmanas att ladda ner konfigurationsprofilen, trycker du på **Tillåt**. Om du är på en enhet som kör:  
    * iOS 12.2 och senare: När hämtningen är slutförd, trycker du på **klar.** Fortsätt till steg 7 i den här artikeln.
    * iOS 12.1 och tidigare: du omdirigeras automatiskt till appen inställningar. Gå vidare till steg 8 i den här artikeln.  
 
    Om du av misstag trycker **Ignorera**, uppdatera sidan. Du uppmanas att öppna appen företagsportal. Från appen, kan du trycka på **hämta igen**.

  > [!NOTE]
  > Du måste installera hanteringsprofilen enligt beskrivningen i nästa steg inom 8 minuter för att hämta den. Om du inte profilen tas bort och du måste starta om registrering.  

7. iOS 12.2 och senare: när du uppmanas att öppna Företagsportalen trycker du på **öppna**. Den **installera Hanteringsprofil** skärmen visar en lista över stegen för att installera profilen.

    ![Exemplet på skärmbilden av Företagsportalen, installera Hanteringsprofil skärmen.](./media/ios-1904-settings-icon.PNG)  

8. Gå till appen inställningar och trycka **profil ned**.  

    Om **profil ned** inte visas som ett alternativ, gå till **Allmänt** > **profiler**. Om du fortfarande inte ser profilen kan du behöva ladda ned den igen.  

    ![Exemplet på skärmbilden appen inställningar, profil ned inställningen.](./media/ios-1904-settings-badge.PNG)  

9. Tryck på **Installera**.  
    
10. Ändra enhetens lösenord Tryck sedan på **installera**.    

    ![Exemplet på skärmbilden av appen inställningar, installera profil kan du med en markör på den ** installera ** för.](./media/ios-1904-password-install.PNG)  


11. Nästa skärm är en Systemvarning för standard för enhetshantering. Om du vill fortsätta med installationen, trycker du på **installera**. Om du uppmanas att lita på fjärrhantering, trycker du på **förtroende**.  

    ![Exemplet på skärmbilden av appen inställningar, standardsystem varning skärmen för rotcertifikatet och hantering av mobila enheter.](./media/ios-15-cp-enroll-1903.PNG)  

12. När installationen är klar trycker du på **klar**. Kontrollera att profilen har installerats, gå till den **profiler och enhetshantering** inställningar. Du bör se den profil som visas under **hantering av mobilenheter**.   

    ![Exemplet på skärmbilden av inställningsappen, profiler och enhetshantering inställningar, som visar hanteringsprofilen.](./media/ios-00-cp-enroll-1903.PNG)  

13. Gå tillbaka till appen Företagsportal. Företagsportalen börjar synkronisera och konfigurera din enhet. Företagsportalen kan be dig uppdatera ytterligare inställningar för enheter. Om den gör det, trycker du på **Fortsätt**.  

    ![Exemplet på skärmbilden av Företagsportalen, ”Ställ in åtkomst” fönster, där gul triangel bredvid inställningen krav.](./media/ios-12-cp-enroll-1903.PNG)  

14. Vet du att installationen är klar när alla objekt i listan visas en grön cirkel. Tap **Klar**.   
    
    ![Exemplet på skärmbilden av Företagsportalen, ”var allt klart”! Skärmbild som visar alla gröna cirklar.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Om din organisation övervakar röst- och begränsningar, eller får du en enhet som ägs av företaget, kanske du har några fler steg att slutföra. Om du uppmanas att installera den **Datalert** appen, se [genom att registrera enheten i kostnadsuppföljningen av telekommunikation](enroll-your-device-with-telecom-expense-management-ios.md). Om din organisation är en del av Apples DEP kan ta reda på [hur du registrerar enheten ägs av företaget](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Nästa steg  
Hitta appar som hjälper dig i arbetet eller skolan. Lär dig [hur appar blir tillgängliga](use-managed-apps-on-your-device-ios.md) till dig via Företagsportalen.  

Behöver du fortfarande hjälp? Kontakta företagets support. Du hittar kontaktinformationen på [Företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  
