---
title: Konfigurera iOS-enhetsåtkomst till företagsresurser | Microsoft Docs
description: Beskriver hur du hämtar en iOS-enhet som hanteras av Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/26/2019
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
ms.openlocfilehash: ee0f438d929abd6b5b90acbaeeddc41e3ce11f98
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490650"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Konfigurera iOS-enhetsåtkomst till företagsresurser  

Registrera din iOS-enhet i Intune-företagsportalappen för att få säker åtkomst till organisationens e-post, filer och appar.

Innan du kan få åtkomst till upphovsrättsskyddade data från en företagsenhet eller personlig enhet måste enheten vara hanterad. När enheten är hanterad tilldelar din organisation principer och appar till enheten via en MDM-provider för hantering av mobilenheter, som Intune. 

För att kunna komma åt arbets- eller skolinformation från din enhet måste du konfigurera enheten så att den matchar organisationens önskade inställningar. Den här artikeln beskriver hur du använder Företagsportalen registrerar du enheten och underhålla inställningen krav som din organisation. 

> [!NOTE]
> Om du försökte komma åt företagets e-post i e-postprogrammet och du fick ett meddelande om att enheten måste vara hanterad, är du på rätt plats. Följ anvisningarna nedan för att få åtkomst till din e-post och andra företagsresurser på iOS-enheten.  

## <a name="what-to-expect-from-the-company-portal-app"></a>Vad du kan förvänta dig av företagsportalappen  

### <a name="security"></a>Säkerhet  
Under installationen kräver appen att du autentiserar dig själv hos organisationen. Du informeras sedan om eventuella enhetsinställningar som du behöver uppdatera. Organisationer anger exempelvis ofta krav på lägsta eller högsta antal tecken i lösenordet som du måste uppfylla.     

### <a name="protection"></a>Skydd  
När enheten har registrerats fortsätter företagsportalappen att se till att enheten är skyddad. Om du till exempel installerar en app från en ej betrodd källa kommer appen meddela dig och återkallar ibland åtkomst till företagets data. En princip så här är vanligt i organisationer och kräver ofta att avinstallera appen ej betrodda innan du kan få åtkomst.  

### <a name="setting-notifications"></a>Konfigurera meddelanden  
Om organisationen inför ett nytt säkerhetskrav efter registreringen, t.ex. multifaktorautentisering, meddelar företagsportalappen dig. Du får möjlighet att justera dina inställningar så att du kan fortsätta arbeta från enheten.  

Mer information om registrering finns i [Vad händer när jag installerar företagsportalappen och registrerar min enhet?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Registrera din iOS-enhet   

> [!IMPORTANT]
> Skärmbilderna i det här avsnittet visar upplevelsen för enheter som kör iOS version 12.1 och tidigare. Om tillämpligt, innehåller instruktioner som är specifika för iOS-versionen 12.2 och senare. Om du märker att din upplevelse skiljer sig från skärmbilderna visas kan du läsa 12.2 anvisningarna.      

Gå till appbutiken för att ladda ned och installera den [företagsportalappen](install-and-sign-in-to-the-intune-company-portal-app-ios.md) till din enhet. Under registreringen måste du också en Wi-Fi-anslutning och åtkomst till Safari. 

Om du pausar under mer än ett par minuter under registreringen kan appen stänga eller avsluta installationen. Om detta inträffar kan du öppna företagsportalappen och försök igen.  

1. Öppna företagsportalen och logga in med ditt arbets- eller skolkonto. 

    ![Exemplet på skärmbilden av företagsportalappen, logga in.](./media/ios-01-cp-enroll-1903.PNG)  

2. När du uppmanas att ta emot meddelanden i Företagsportalen trycker du på **Tillåt.** Företagsportalen använder meddelanden för att varna dig om till exempel din Enhetsinställningar behöver uppdateras. 

    ![Exemplet på skärmbilden av Företagsportalens startsida, ”meddelanden” fråga.](./media/ios-04-cp-enroll-1903.PNG)  

3. På den **Ställ in åtkomst** väljer **börjar.**  

     ![Exemplet på skärmbilden av Företagsportalen, ”Ställ in åtkomst” skärmen.](./media/ios-05-cp-enroll-1903.PNG)  

4. Läs igenom listan med enhetsinformation som din organisation kan och inte kan se. [Mer information om det här avsnittet](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md) kan hittas den **mer** länk. När du är klar trycker du på **Fortsätt**.  

    ![Exemplet på skärmbilden av företagsportalappen, ”vad kan min organisation se”, med knappen Fortsätt.](./media/ios-06-cp-enroll-1903.PNG)  
 
5. Den **vad händer nu?** skärmen sammanfattar de återstående stegen. De här stegen kan vara olika beroende på din iOS-version. 
    * **iOS 12.2 och senare**: din upplevelse i stället kräver att du:  

        a. **Tillåt hämtning av hanteringsprofil**: webbläsaren öppnar Företagsportalen, och uppmanar dig att hämta. Nedladdningen sparas i inställningsappen.  

        b. **Öppna appen inställningar och installera profilen**: du behöver gå till appen inställningar och installera hanteringsprofilen.  

        c. **Gå tillbaka till företagsportalappen**: du behöver gå tillbaka till företagsportalappen att slutföra installationen.  

    När du är redo att laddas ned hanteringsprofilen, trycker du på **Fortsätt**.  

6. Safari öppnar Företagsportalen. När du uppmanas att ladda ner konfigurationsprofilen, trycker du på **Tillåt**.  
    * **iOS 12.2 och senare**: vänta för profilen som har hämtats i Safari och tryck på **klar**. Öppna sedan appen **Inställningar** på enheten.  

    > [!IMPORTANT]
    > Du måste gå till den **inställningar** appen och installera den här profilen inom 8 minuter för att hämta den. Om du inte profilen tas bort och du måste starta om registrering. 

7. I den **inställningar** app, tryck **installera ned profil** > **installera**. Om **installera ned profil** inte visas som ett alternativ, gå till **Allmänt** > **profiler**. Om du fortfarande inte ser profilen kan du behöva ladda ned den igen.  

    ![Exemplet på skärmbilden av appen inställningar, installera hämtade profilinställningen, med en röd symbol som indikerar en nyligen hämtade profilen.](./media/ios-10-cp-enroll-1903.PNG)  
    
8. Om du uppmanas, anger du lösenordet för din enhet. Tryck sedan på **installera**.      

9. Nästa skärm är en Systemvarning för standard för enhetshantering. Om du vill veta mer om vad din organisation kan se och inte kan se på din enhet kan du se den relevanta [Intune docs-artikel](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md). Om du vill fortsätta med installationen, trycker du på **installera**. Om du uppmanas att lita på fjärrhantering, trycker du på **förtroende**.  

    ![Exemplet på skärmbilden av appen inställningar, standardsystem varning skärmen för rotcertifikatet och hantering av mobila enheter.](./media/ios-15-cp-enroll-1903.PNG)  

10. När installationen är klar trycker du på **klar**. Kontrollera att profilen har installerats, gå till den **profiler och enhetshantering** inställningar. Du bör se den profil som visas under **hantering av mobilenheter**.   

    ![Exemplet på skärmbilden av inställningsappen, profiler och enhetshantering inställningar, som visar hanteringsprofilen.](./media/ios-00-cp-enroll-1903.PNG)  


11. Gå tillbaka till appen **Företagsportal**. Företagsportalen börjar synkronisera och konfigurera din enhet. Företagsportalen kan be dig uppdatera ytterligare inställningar för enheter. Om den gör det, trycker du på **Fortsätt**.

    ![Exemplet på skärmbilden av Företagsportalen, ”Ställ in åtkomst” fönster, där gul triangel bredvid inställningen krav.](./media/ios-12-cp-enroll-1903.PNG)  

12. Vet du att installationen är klar när alla objekt i listan visas en grön cirkel. Tap **Klar**.  
    
    ![Exemplet på skärmbilden av Företagsportalen, ”var allt klart”! Skärmbild som visar alla gröna cirklar.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Om din organisation övervakar röst- och begränsningar, eller får du en enhet som ägs av företaget, kanske du har några fler steg att slutföra. Om du uppmanas att installera den **Datalert** appen, se [genom att registrera enheten i kostnadsuppföljningen av telekommunikation](enroll-your-device-with-telecom-expense-management-ios.md). Om din organisation är en del av Apples DEP kan ta reda på [hur du registrerar enheten ägs av företaget](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Nästa steg  
Hitta appar som hjälper dig i arbetet eller skolan. Lär dig [hur appar blir tillgängliga](use-managed-apps-on-your-device-ios.md) till dig via Företagsportalen.  

Behöver du fortfarande hjälp? Kontakta företagets support. Du hittar kontaktinformationen på [Företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  
