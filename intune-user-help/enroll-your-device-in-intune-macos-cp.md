---
title: Registrera din Mac med Intune-företagsportal | Microsoft Docs
description: Lär dig hur du registrerar din Mac i Intune med Företagsportal-appen.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: kakyker
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba285fc9de58b3fb739a16722e0e05e36e840e87
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74098122"
---
# <a name="enroll-your-macos-device-using-the-company-portal-app"></a>Registrera din macOS-enhet med hjälp av Företagsportal-appen  

Registrera din macOS-enhet i Intune-företagsportalappen för att få säker åtkomst till arbetets eller skolans e-post, filer och appar.

Organisationer kräver vanligt vis att du registrerar din enhet innan du kan komma åt patentskyddade data. När enheten har registrerats blir den *hanterad*. Din organisation kan tilldela principer och appar till enheten via en MDM-provider för hantering av mobilenheter, t.ex. Intune. För att få kontinuerlig tillgång till arbets- eller skolinformation på enheten måste du konfigurera den så att principinställningarna matchar organisationens.  

Den här artikeln beskriver hur du använder företagsportalappen för macOS för att registrera, konfigurera och underhålla enheten så att du uppfyller organisationens krav.  


## <a name="what-to-expect-from-the-company-portal-app"></a>Vad du kan förvänta dig av företagsportalappen

Under den första installationen kräver Företagsportal-appen att du loggar in och autentiserar dig själv med din organisation. Företagsportal sedan informerar dig om eventuella enhets inställningar som du behöver konfigurera för att uppfylla organisationens krav. Organisationer anger exempelvis ofta krav på lägsta eller högsta antal tecken i lösenordet som du måste uppfylla.    

När du har registrerat din enhet ser Företagsportal alltid till att enheten skyddas enligt organisationens krav. Om du till exempel installerar en app från en obetrodd källa, kan Företagsportal varna dig och kan begränsa åtkomsten till organisationens resurser. App Protection-principer som detta är vanliga. För att få åtkomst måste du förmodligen avinstallera den ej betrodda appen. 

Om organisationen inför ett nytt säkerhetskrav efter registreringen, t.ex. multifaktorautentisering, meddelar företagsportalen dig. Du får möjlighet att justera dina inställningar så att du kan fortsätta arbeta från enheten.  

Mer information om registrering finns i [Vad händer när jag installerar företagsportalappen och registrerar min enhet?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-macos-device-managed"></a>Få din macOS-enhet hanterad  
Använd följande steg för att registrera din macOS-enhet med din organisation. Din enhet måste köra macOS 10,12 eller senare.   

> [!NOTE]
> I den här processen kan du uppmanas att tillåta Företagsportal att använda konfidentiell information som lagras i din nyckel Ring. Dessa meddelanden är en del av Apples säkerhet. När du får frågan skriver du in lösen ordet för inloggnings nyckel och väljer **Tillåt alltid**. Om du trycker på **RETUR** eller **RETUR** på tangent bordet väljer du i stället **Tillåt**, vilket kan resultera i ytterligare prompter.  

### <a name="install-company-portal-app"></a>Installera företagsportalappen  
1. Gå till [registrera min Mac](https://go.microsoft.com/fwlink/?linkid=853070).  
2. Filen Företagsportal Installer. pkg laddas ned. Öppna installations programmet och Fortsätt genom stegen. 
3. Godkänn licens avtalet för program varan. 
4. Ange enhetens lösen ord eller det registrerade finger avtryck för att installera program varan.  
5. Öppna Företagsportal. 

> [!IMPORTANT]
> Microsoft AutoUpdate kan vara öppet för att uppdatera din Microsoft-programvara. När alla uppdateringar har installerats öppnar du appen Företagsportal. För bästa installations upplevelse installerar du de senaste versionerna av Microsoft AutoUpdate och Företagsportal.  


### <a name="enroll-your-mac"></a>Registrera din Mac  


1. Logga in på företagsportalen med ditt arbets- eller skolkonto.  
2. När appen öppnas väljer du **Starta**.  
3. Granska [vad din organisation kan och inte kan se](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) på den registrerade enheten. Välj sedan **Fortsätt**.  
4. På skärmen **Installera hanterings profil** väljer du **Hämta profil**.   

    ![Exempel skärm bild av skärmen Företagsportal installera hanterings profil och markera knappen Ladda ned profil.](./media/install-mgmt-profile-mac-1911.PNG)   
5. Enhetens system inställningar kommer att öppnas. Välj **Installera** och välj sedan **Installera** igen. Om du uppmanas till det anger du enhetens lösen ord.  

    ![Exempel skärm bild av macOS-Systeminställningar, installations prompt, markera knappen Installera.](./media/system-preference-install-1911.PNG)  
6. När profilen har installerats visas den i listan profiler under **hanterings profil.**  

   ![Exempel skärm bild av OS-inställningar för macOS, profil skärmen, som markerar den installerade hanterings profilen.](./media/system-preference-verify-1911.PNG)   
7. Återgå till Företagsportal.   
8. Din organisation kan kräva att du uppdaterar enhets inställningarna. När du är klar med att uppdatera inställningarna väljer du **kontrol lera inställningar**.  

    ![Exempel skärm bild av skärmen Företagsportal, uppdatera enhets inställningar och markera knappen kontrol lera inställningar.](./media/update-settings-mac-1911.PNG)  
9. När installationen är klar väljer du **klar**.  


 ## <a name="troubleshooting-and-feedback"></a>Fel sökning och feedback   

Om du stöter på problem under registreringen kan du gå till **hjälp** > **Skicka diagnostisk rapport** för att rapportera problemet till Microsoft Apps-utvecklare. Den här informationen används för att hjälpa till att förbättra appen. De använder också den här informationen för att hjälpa till att lösa problemet om IT-supporten når dem för att få hjälp.  

När du har rapporterat problemet till Microsoft kan du skicka information om din upplevelse till IT-supporten. Välj **e-postinformation**. Skriv vad du fick i e-postmeddelandets brödtext. Om du vill hitta din support persons e-postadress går du till Företagsportal app > **Kontakta**. Eller kontrol lera [företagsportal webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  
 

Dessutom skulle Microsoft Intune Företagsportals teamet älska att höra din feedback. Gå till **hjälp** > **Skicka feedback** för att dela med dig av dina tankar och idéer.  

## <a name="unverified-profiles"></a>Overifierade profiler  
När du visar de installerade MDM-profilerna för hantering av mobilenheter i **Systeminställningar** > **Profiler**, kan vissa profiler visas med statusen Inte verifierad. Så länge som hanteringsprofilen visar statusen Verifierad behöver du inte bry dig om detta.  

Hanteringsprofilen är vad som definierar MDM-kanalanslutningen. Så länge hanteringsprofilen är verifierad ärver alla andra profiler som levereras till datorn, via kanalen, hanteringsprofilens säkerhetsegenskaper.  

## <a name="updating-the-company-portal-app"></a>Uppdatera företagsportalappen

Företagsportalappen uppdateras på samma sätt som andra Office-appar, genom Microsoft AutoUpdate för macOS. Läs mer om [uppdatering av Microsoft-appar för macOS](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>Nästa steg  
Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  


