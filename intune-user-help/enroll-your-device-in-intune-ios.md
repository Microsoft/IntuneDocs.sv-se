---
title: Konfigurera iOS-enhetsåtkomst till företagsresurser | Microsoft Docs
description: Beskriver hur du hämtar en iOS-enhet som hanteras av Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
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
ms.openlocfilehash: bef0eb545f5f0ca0f85365a08e6bc5d726d6979e
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196864"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Konfigurera iOS-enhetsåtkomst till företagsresurser  

Registrera din iOS-enhet i Intune-företagsportalappen för att få säker åtkomst till organisationens e-post, filer och appar.

När enheten har registrerats blir den *hanterad*. Din organisation kan tilldela principer och appar till enheten via en MDM-provider för hantering av mobilenheter, t.ex. Intune.  

För att kunna komma åt arbets- eller skolinformation från din enhet måste du konfigurera enheten så att den matchar organisationens önskade inställningar. Den här artikeln beskriver hur du använder Företagsportalen för att registrera enheten och underhålla organisationens inställningskrav.  
</br>
> [!VIDEO https://www.youtube.com/embed/mJyv6YcHi7c?rel=0]

> [!NOTE]
> Om du försökte komma åt företagets e-post i e-postprogrammet och du fick ett meddelande om att enheten måste vara hanterad, är du på rätt plats. Följ anvisningarna nedan för att få åtkomst till din e-post och andra företagsresurser på iOS-enheten.  

## <a name="what-to-expect-from-the-company-portal-app"></a>Vad du kan förvänta dig av företagsportalappen  

### <a name="security"></a>Säkerhet  
Under installationen kräver appen att du autentiserar dig själv hos organisationen. Du informeras sedan om eventuella enhetsinställningar som du behöver uppdatera. Organisationer anger exempelvis ofta krav på lägsta eller högsta antal tecken i lösenordet som du måste uppfylla.

### <a name="protection"></a>Skydd  
När enheten har registrerats fortsätter företagsportalappen att se till att enheten är skyddad. Om du till exempel installerar en app från en ej betrodd källa kommer appen meddela dig och återkallar ibland åtkomst till företagets data. Den här typen av princip är vanlig i organisationer och kräver ofta att du avinstallerar den icke betrodda appen innan du kan få åtkomst igen.  

### <a name="setting-notifications"></a>Konfigurera meddelanden  
Om organisationen inför ett nytt säkerhetskrav efter registreringen, t.ex. multifaktorautentisering, meddelar företagsportalappen dig. Du får möjlighet att justera dina inställningar så att du kan fortsätta arbeta från enheten.  

Mer information om registrering finns i [Vad händer när jag installerar företagsportalappen och registrerar min enhet?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Registrera din iOS-enhet  

Gå till appbutiken för att ladda ned och installera [Intune-företagsportalappen ](install-and-sign-in-to-the-intune-company-portal-app-ios.md) på din enhet. Du måste även ha en Wi-Fi-anslutning och åtkomst till Safari under registreringen. 

En paus på mer än några minuter under registreringen göra att appen stängs eller att installationen avslutas. Om detta inträffar öppnar du företagsportalappen och försöker igen.  

1. Öppna företagsportalen och logga in med ditt arbets- eller skolkonto. 

    ![Exempel på skärmbild av appen Företagsportal, Logga in.](./media/ios-01-cp-enroll-1903.PNG)  

2. När du uppmanas att ta emot meddelanden från företagsportalappen trycker du på **Tillåt**. Företagsportalen använder meddelanden för att avisera dig, t.ex. om dina enhetsinställningar behöver uppdateras. 

    ![Exempel på skärmbild av startsidan för Företagsportal, skärmen ”Meddelanden”.](./media/ios-04-cp-enroll-1903.PNG)  

3. Välj **Börja** på skärmen **Konfigurera åtkomst**.  

     ![Exempel på skärmbild av Företagsportal, skärmen ”Konfigurera åtkomst”.](./media/ios-05-cp-enroll-1903.PNG)  

4. Gå igenom listan med enhetsinformation som din organisation kan och inte kan se. Tryck sedan på **Fortsätt**.  

5. Läs anvisningarna på skärmen **Vad händer nu?** När du är redo att ladda ned och installera hanteringsprofilen trycker du på **Fortsätt**.  

 > [!IMPORTANT]
> Nästa steg och vilka skärmar som visas varierar beroende på din iOS-version. Följ anvisningarna för din iOS-version. 

6. Safari öppnar webbplatsen för Företagsportal på enheten. När du uppmanas att ladda ned konfigurationsprofilen trycker du på **Tillåt**. Om du använder en enhet som kör:  
    * iOS 12.2 och senare: När nedladdningen har slutförts trycker du på **Klar**. Fortsätt till steg 7 i den här artikeln.
    * iOS 12.1 och tidigare: Du omdirigeras automatiskt till appen Inställningar. Gå vidare till steg 8 i den här artikeln.  
 
    Om du trycker på **Ignorera** av misstag, uppdaterar du sidan. Du uppmanas att öppna appen Företagsportal. Från appen kan du trycka på **Ladda ned igen**.

  > [!NOTE]
  > Du måste installera hanteringsprofilen enligt beskrivningen i nästa steg inom 8 minuter efter nedladdningen. Annars tas profilen bort och du måste börja om registreringen.  

7. iOS 12.2 och senare: När du uppmanas att öppna appen Företagsportal trycker du på **Öppna**. Skärmen **Installing Management Profile** (Installera hanteringsprofil) visar en lista över stegen för att installera profilen.

    ![Exempel på skärmbild av Företagsportal, skärmen Installing Management Profile (Installera hanteringsprofil).](./media/ios-1904-settings-icon.PNG)  

8. Gå till appen Inställningar och tryck på **Profile Downloaded** (Nedladdad profil).  

    Om alternativet **Profile Downloaded** (Nedladdad profil) inte visas går du till **Allmänt** > **Profiler**. Om du fortfarande inte ser profilen kan du behöva ladda ned den igen.  

    ![Exempel på skärmbild av appen Inställningar, inställningen Profile Downloaded (Nedladdad profil).](./media/ios-1904-settings-badge.PNG)  

9. Tryck på **Installera**.  
    
10. Ange ditt enhetslösenord. Tryck sedan på **Installera**.    

    ![Exempel på skärmbild av appen Inställningar, skärmen Installing Profile (Installera profil), med markören på knappen **Installera**.](./media/ios-1904-password-install.PNG)  


11. Nästa skärm är en standardsystemvarning för enhetshantering. Fortsätt med installationen genom att trycka på **Installera**. Om du uppmanas att lita på fjärrhantering trycker du på **Förtroende**.  

    ![Exempel på skärmbild av appen Inställningar, standardskärm för systemvarning om rotcertifikat och hantering av mobilenheter.](./media/ios-15-cp-enroll-1903.PNG)  

12. När installationen är klar trycker du på **Klar**. Kontrollera att profilen har installerats, gå till inställningarna för **Profiler och enhetshantering**. Du bör se profilen under **Hantering av mobilenheter**.   

    ![Exempel på skärmbild av appen Inställningar, inställningar för Profiler och enhetshantering, som visar hanteringsprofilen.](./media/ios-00-cp-enroll-1903.PNG)  

13. Gå tillbaka till appen Företagsportal. Företagsportalen börjar synkronisera och konfigurera din enhet. Du kan uppmanas att uppdatera ytterligare enhetsinställningar. I så fall trycker du på **Fortsätt**.  

    ![Exempel på skärmbild av appen Företagsportal, skärmen ”Konfigurera åtkomst”, med en gul triangel bredvid inställningskraven.](./media/ios-12-cp-enroll-1903.PNG)  

14. Du vet att installationen är klar när alla objekt i listan visas med en grön cirkel. Tap **Klar**.   
    
    ![Exempel på skärmbild av appen Företagsportal, ”Nu är du klar!” Skärmbild med endast gröna cirklar.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Om din organisation övervakar röst- och databegränsningar, eller ger dig en företagsägd enhet, kan du behöva utföra några ytterligare steg. Om du uppmanas att installera appen **Datalert** läser du avsnittet om hur du [registrerar din enhet i kostnadshanteringen för telekommunikation](enroll-your-device-with-telecom-expense-management-ios.md). Om din organisation är en del av Apples program för enhetsregistrering (DEP) tar du reda på [hur du registrerar din företagsägda enhet](enroll-your-device-dep-ios.md).  

## <a name="it-administrator-support"></a>IT-administratörssupport  
Om du är IT-administratör och stöter på problem när du registrerar enheter kan du läsa [Felsöka problem med registrering av iOS-enhet i Microsoft Intune](https://support.microsoft.com/en-us/help/4039809). Den här artikeln innehåller vanliga fel, deras orsaker och stegen för att lösa dem.  

## <a name="next-steps"></a>Nästa steg  
Hitta appar som hjälper dig i arbetet eller skolan. Lär dig [hur appar blir tillgängliga](use-managed-apps-on-your-device-ios.md) för dig via Företagsportalen.  

Behöver du fortfarande hjälp? Kontakta företagets support. Du hittar kontaktinformationen på [Företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  
