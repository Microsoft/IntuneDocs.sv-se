---
title: Registrera Windows-enheter med Windows AutoPilot-distributionsprogrammet
description: "Läs om hur du registrerar nya Windows 10-enheter med Windows AutoPilot-distributionsprogrammet."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: dae736aef57489880915c269cb30785371380a52
ms.sourcegitcommit: 53d272defd2ec061dfdfdae3668d1b676c8aa7c6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2018
---
# <a name="enroll-windows-devices-using-windows-autopilot-deployment-program"></a>Registrera Windows-enheter med Windows AutoPilot-distributionsprogrammet
Windows AutoPilot-distributionsprogrammet förenklar etableringen av enheter. Att skapa och underhålla anpassade operativsystemavbildningar är en process som tar tid. Det kan också ta tid att applicera de här anpassade operativsystemavbildningarna till nya enheter för att förbereda dem för användning innan du ger dem till dina slutanvändare. Med Microsoft Intune och AutoPilot kan du ge dina slutanvändare nya enheter utan att behöva skapa, underhålla och applicera anpassade operativsystemavbildningar på enheter med Microsoft Intune och AutoPilot. När du använder Intune för att hantera AutoPilot-enheter kan du hantera principer, profiler, appar, etc. på enheterna när de har registrerats. I [översikten över Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot) finns en översikt över fördelar, scenarier och förutsättningar.

## <a name="prerequisites"></a>Krav
- [Enheter måste vara registrerade för din organisation](https://docs.microsoft.com/en-us/windows/deployment/windows-autopilot/windows-10-autopilot#device-registration-and-oobe-customization)
- [Automatisk registrering i Windows aktiverad](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium-prenumeration](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="synchronize-devices"></a>Synkronisera enheter
Synkronisera dina registrerade enheter i Intune så du kan konfigurera dem.

1. Logga in på [Azure](https://portal.azure.com/).
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetsregistrering** under **Intune**.
4. Under **Windows-registrering** i avsnittet **Windows AutoPilot-distributionsprogram** väljer du **Enheter**.
5. Klicka på **Synkronisera** för att importera dina registrerade enheter. Ett meddelande visar att synkroniseringen pågår.
6. Uppdatera vyn för att se de nya enheterna. Processen kan ta några minuter att slutföra beroende på hur många enheter som synkroniseras.  

## <a name="create-an-autopilot-deployment-profile"></a>Skapa en AutoPilot-distributionsprofil
AutoPilot-distributionsprofiler används för att konfigurera AutoPilot-enheterna.
1. Logga in på [Azure](https://portal.azure.com/). 
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetsregistrering** under **Intune**.
4. Under **Windows-registrering** i avsnittet **Windows AutoPilot-distributionsprogram** väljer du **Distributionsprofiler**.
5. Klicka på **Skapa profil** och välj ett namn och en valfri beskrivning. 
6. Som **anslutningstyp** väljer du **Azure AD-ansluten**.
7. För **välkomstprogrammet (OOBE)** konfigurerar du följande alternativ och klickar på **OK**: 
   - **Sekretessinställningar**: Välj om du vill visa sekretessinställningar för andra. 
   - **Licensavtal för slutanvändare (EULA)**: Välj om du vill visa EULA för användarna.
   - **Användarkontotyp**: Välj om användarens kontotyp ska vara **Administratör** eller **Standard**.

     > [!Note]    
     > Den här inställningen gäller inte för konton för Global administratör eller företagsadministratör. Dessa konton kan inte vara standardanvändare eftersom de har åtkomst till alla administrativa funktioner i Microsoft Azure Active Directory.
8. Klicka på **Skapa** när du vill skapa profilen. AutoPilot-distributionsprofilen är nu tillgänglig för att tilldela till enheter.
     
> [!Note]    
> Följande inställningar konfigureras med alla AutoPilot-distributionsprofiler:
> - Registreringssidor för Skip Cortana, OneDrive och OEM
> - Konfigurera automatiskt för arbetet eller skolan
> - Logga in med företagets eller skolans varumärken    

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Aviseringar för otilldelade Windows AutoPilot-enheter <!-- 163236 -->
Du kan visa en avisering för otilldelade Windows AutoPilot-enheter om du vill se hur många enheter från AutoPilot-programmet som inte har tilldelade AutoPilot-distributionsprofiler. Använd informationen i aviseringen för att skapa profiler och tilldela dem till de otilldelade enheterna. När du klickar på aviseringen visas en fullständig lista över Windows AutoPilot-enheter och detaljerad information om dem. 
1. Logga in på [Azure](https://portal.azure.com/). 
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetsregistrering** under **Intune**.
4. Välj **Översikt** för att se aviseringen. Klicka på aviseringen om du vill se en lista över AutoPilot-enheter.  

## <a name="assign-an-autopilot-deployment-profile"></a>Tilldela en AutoPilot-distributionsprofil
När du har skapat AutoPilot-distributionsprofiler kan du tilldela dem till valda enheter.

1. Logga in på [Azure](https://portal.azure.com/). 
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetsregistrering** under **Intune**.
4. På bladet **Windows-registrering** i avsnittet **Windows AutoPilot-distributionsprogram** väljer du **Enheter**.
5. Välj de enheter som du vill tilldela distributionsprofilen till. Du kan filtrera i kolumnen **Status** och enkelt hitta enheter utan någon tilldelad profil. 
6. Klicka på **Tilldela profil**, välj AutoPilot-distributionsprofilen och klicka sedan på **Tilldela**. Ett meddelande visar att tilldelningen pågår.
7. Uppdatera vyn för att se att profilen har tilldelats till enheter. Processen kan ta några minuter att slutföra beroende på hur många enheter du har valt. 

> [!Note]
> Den nya profilen har tilldelats enheten. På enheter som redan har registrerats i Intune appliceras profilen efter att enheten har återställts och omregistrerats.

### <a name="assign-a-different-autopilot-deployment-profile"></a>Tilldela en annan AutoPilot-distributionsprofil
När du har tilldelat en AutoPilot-distributionsprofil till en enhet och vill tilldela en annan profil tilldelar du enheten den nya profilen.  

## <a name="edit-an-autopilot-deployment-profile"></a>Redigera en AutoPilot-distributionsprofil 
När du har skapat en AutoPilot-distributionsprofil kan du redigera vissa delar av den.   
1. Logga in på [Azure](https://portal.azure.com/). 
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetsregistrering** under **Intune**.
4. Under **Windows-registrering** i avsnittet **Windows AutoPilot-distributionsprogram** väljer du **Distributionsprofiler**. 
5. Välj den profil du vill redigera. 
6. Klicka på **Egenskaper** till vänster om du vill ändra distributionsprofilens namn eller beskrivning. Klicka på **Spara** när du har gjort ändringarna. 
7. Klicka på **Inställningar** när du vill göra ändringar i OOBE-inställningarna. Klicka på **Spara** när du har gjort ändringarna. 

> [!NOTE]
> Den uppdaterade profilen tilldelas till enheter. Den uppdaterade profilen tillämpas emellertid inte på enheter som redan har registrerats i Intune förrän enheten har återställts och omregistrerats. 

## <a name="using-autopilot-in-other-portals"></a>Använda AutoPilot i andra portaler
Om du inte är intresserad av hantering av mobila enheter har du möjlighet att använda AutoPilot i till exempel Microsoft Store för företag. Det går att använda andra portaler, men vi rekommenderar att du enbart hanterar dina AutoPilot-distributioner i Intune. Om du använder Intune med en annan portal kan inte Intune:
- Visa ändringar i profiler som har skapats i Intune men redigerats i en annan portal
- Synkronisera profiler som har skapats i en annan portal
- Visa ändringar i profiltilldelningar som har gjorts i en annan portal
- Synkronisera profiltilldelningar som har gjorts i en annan portal
- Visa ändringar i listan över enheter som har gjorts i en annan portal

## <a name="next-steps"></a>Nästa steg
Lär dig hur du hanterar enheterna när du har konfigurerat Windows AutoPilot för registrerade Windows 10-enheter. Mer information finns i [Vad är Microsoft Intune-enhetshantering?](https://docs.microsoft.com/intune/device-management)