---
title: Registrera enheter med Windows AutoPilot
titleSuffix: Microsoft Intune
description: Läs om hur du registrerar Windows 10-enheter med Windows AutoPilot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: a640e6d914da6fead7a64d5235c1cdeac164ac9e
ms.sourcegitcommit: 7c70c3e0fcae7c4fa8c9e108aafb1cebb366332d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/07/2018
ms.locfileid: "44096545"
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot"></a>Registrera Windows-enheter med hjälp av Windows AutoPilot
Windows AutoPilot förenklar etableringen av enheter. Att skapa och underhålla anpassade operativsystemavbildningar är en process som tar tid. Det kan också ta tid att applicera de här anpassade operativsystemavbildningarna till nya enheter för att förbereda dem för användning innan du ger dem till dina slutanvändare. Med Microsoft Intune och AutoPilot kan du ge dina slutanvändare nya enheter utan att behöva skapa, underhålla och applicera anpassade operativsystemavbildningar på enheter med Microsoft Intune och AutoPilot. Om du använder Intune för att hantera AutoPilot-enheter kan du hantera principer, profiler, appar med mera när de har registrerats. I [översikten över Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot) finns en översikt över fördelar, scenarier och förutsättningar.

## <a name="prerequisites"></a>Krav
- [Automatisk registrering i Windows aktiverad](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium-prenumeration](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="add-devices"></a>Lägg till enheter

Du kan lägga till Windows AutoPilot-enheter genom att importera en CSV-fil med deras information.

1. I [Intune på Microsoft Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Enheter** > **Importera**.

    ![Skärmbild av Windows AutoPilot-enheter](media/enrollment-autopilot/autopilot-import-device.png)

2. Under **Lägg till Windows Autopilot-enheter** bläddrar du till en CSV-fil som innehåller en lista med de enheter som du vill lägga till. Filen bör innehålla serienummer, Windows produkt-ID, maskinvaru-hasher och valfria beställningsnummer för enheterna.

    ![Skärmbild av Lägga till Windows AutoPilot-enheter](media/enrollment-autopilot/autopilot-import-device2.png)

3. Välj **Importera** för att börja importera enhetsinformationen. Det kan ta flera minuter att importera.

4. När importen är klar väljer du **Enhetsregistrering** > **Windows-registrering** > **Windows AutoPilot** > **Enheter** > **Synkronisera**. Ett meddelande visar att synkroniseringen pågår. Processen kan ta några minuter att slutföra beroende på hur många enheter som synkroniseras.

5. Uppdatera vyn för att se de nya enheterna.

## <a name="create-an-autopilot-device-group"></a>Skapa en AutoPilot-enhetsgrupp

1. I [Intune på Azure-portalen](https://aka.ms/intuneportal) väljer du **Grupper**.
2. På bladet **Grupp**:
    1. Välj **Säkerhet** för **Grupptyp**.
    2. Ange ett **gruppnamn** och en **gruppbeskrivning**.
    3. För **Medlemstyp** väljer du antingen **Tilldelad** eller **Dynamisk enhet**.
3. Om du väljer **Tilldelad** för **Medlemstyp** i föregående steg väljer du sedan **Medlemmar** på bladet **Grupp** och lägger till AutoPilot-enheter till gruppen.
    AutoPilot-enheter som ännu inte har registrerats är enheter där namnet är samma som enhetens serienummer.
4. Om du väljer **Dynamiska enheter** för **Medlemstyp** ovan väljer du sedan **Dynamiska enhetsmedlemmar** på bladet **Grupp** och anger någon av följande koder i rutan **Avancerad regel**.
    - Om du vill skapa en grupp som innehåller alla dina AutoPilot-enheter anger du `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Om du vill skapa en grupp som innehåller alla dina AutoPilot-enheter med ett visst beställnings-ID anger du `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Om du vill skapa en grupp som innehåller alla dina AutoPilot-enheter med ett visst inköpsorder-ID anger du `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    När du har lagt till koden för **Avancerad regel** väljer du **Spara**.
5. Välj **Skapa**.



## <a name="create-an-autopilot-deployment-profile"></a>Skapa en AutoPilot-distributionsprofil
AutoPilot-distributionsprofiler används för att konfigurera AutoPilot-enheterna.
1. I [Intune på Microsoft Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > **Skapa profil**.
2. Ange ett **namn** och en valfri **beskrivning**.
3. Välj något av följande två alternativ för **Distributionsläge**:
    - **Användarbaserat**: Enheter med den här profilen är associerade med användaren som registrerar enheten. Användarautentiseringsuppgifter krävs för att etablera enheten.
    - **Självdistribution (förhandsversion)**: (nyaste [Windows 10 Insider Preview-version](https://docs.microsoft.com/windows-insider/at-work-pro/) krävs) Enheter med den här profilen associeras inte med användaren som registrerar enheten. Användarautentiseringsuppgifter krävs inte för att etablera enheten.
4. Välj **Azure AD-ansluten** i **Anslut till Azure AD som**.
5. Välj **välkomstprogrammet (OOBE)**, konfigurera följande alternativ och välj **Spara**:
    - **Språk (Region)***: Välj språket du vill använda för enheten. Det här alternativet är endast tillgängligt om du har valt **Självdistribution** som **Distributionsläge**.
    - **Konfigurera tangentbord automatiskt***: Om ett **Språk (Region)** har valts väljer du **Ja** för att hoppa över sidan för val av tangentbord. Det här alternativet är endast tillgängligt om du har valt **Självdistribution** som **Distributionsläge**.
    - **Licensavtal för slutanvändare (EULA)**: (Windows 10, version 1709 eller senare) Välj om du vill visa EULA för användarna.
    - **Sekretessinställningar**: Välj om du vill visa sekretessinställningar för andra.
    - **Hide change acount options (Windows Insider only)** (Dölj alternativ för att ändra konto (endast Windows Insider)): Välj **Dölj** om du vill förhindra att alternativ för att ändra konto visas på företagets sidor för inloggning och domänfel. Genom att dölja de här alternativen krävs att [företagsanpassning konfigureras i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Användarkontotyp**: Välj om användarens kontotyp ska vara **Administratör** eller **Standard**.
    - **Apply computer name template (Windows Insider only)** (Använd mall för datornamn (endast Windows Insider)): Välj **Ja** för att skapa en mall som ska användas när du namnger en enhet under etableringen. Namn får innehålla högst 15 tecken, och får innehålla bokstäver, siffror och bindestreck. Namn kan inte bestå av enbart siffror. Använd [makrot %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) för att lägga till ett maskinvaruspecifikt serienummer. Du kan även använda [makrot %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) för att lägga till en slumpmässig sträng med siffror, där x motsvarar antalet siffror som ska läggas till. 

6. Välj **Skapa** när du vill skapa profilen. AutoPilot-distributionsprofilen är nu tillgänglig för att tilldela till enheter.

*Både **Språk (region)** och **Konfigurera tangentbord automatiskt** är endast tillgängliga om du har valt **Självdistribution (förhandsversion)** som **Distributionsläge** (senaste [Windows 10 Insider Preview-version](https://docs.microsoft.com/windows-insider/at-work-pro/) krävs).


## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Tilldela en AutoPilot-distributionsprofil till en enhetsgrupp

1. I [Intune på Microsoft Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > välj en profil.
2. Välj **Tilldelningar** på det specifika profilbladet. 
3. Välj **Välj grupper**, sedan väljer du de grupper som du vill tilldela appen på bladet **Välj grupper** och slutligen väljer du **Välj**.

## <a name="edit-an-autopilot-deployment-profile"></a>Redigera en AutoPilot-distributionsprofil
När du har skapat en AutoPilot-distributionsprofil kan du redigera vissa delar av den.   

1. I [Intune på Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsregistrering**.
2. Under **Windows-registrering** i avsnittet **Windows AutoPilot** väljer du **Distributionsprofiler**.
3. Välj den profil du vill redigera.
4. Klicka på **Egenskaper** till vänster om du vill ändra distributionsprofilens namn eller beskrivning. Klicka på **Spara** när du har gjort ändringarna.
5. Klicka på **Inställningar** när du vill göra ändringar i OOBE-inställningarna. Klicka på **Spara** när du har gjort ändringarna.

> [!NOTE]
> Ändringar i profilen tillämpas på enheter som är tilldelade till profilen. Den uppdaterade profilen tillämpas emellertid inte på enheter som redan har registrerats i Intune förrän enheten har återställts och omregistrerats.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Aviseringar för otilldelade Windows AutoPilot-enheter <!-- 163236 -->
Du kan visa en avisering för att se hur många enheter från AutoPilot-programmet som inte har tilldelade AutoPilot-distributionsprofiler. Använd informationen i aviseringen för att skapa profiler och tilldela dem till de otilldelade enheterna. När du klickar på aviseringen visas en fullständig lista över Windows AutoPilot-enheter och detaljerad information om dem.

Om du vill visa aviseringar för otilldelade enheter väljer du **Enhetsregistrering** > **Översikt** > **Ej tilldelade enheter** i [Intune i Azure-portalen](https://aka.ms/intuneportal).  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Tilldela en användare till en specifik Autopilot-enhet

Du kan tilldela en användare till en specifik Autopilot-enhet. Den här tilldelningen gör att en användare fylls i på förhand från Azure Active Directory på den [företagsanpassade](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) inloggningssidan under Windows-installationen. Du kan även ange ett anpassat namn för hälsning. Windows-logotypen fylls inte i på förhand och ändras inte. Endast licensierade Intune-användare kan tilldelas på detta sätt.

Krav: Azure Active Directory-företagsportal konfigurerad och senaste [Windows 10 Insider Preview-version](https://docs.microsoft.com/windows-insider/at-work-pro/).

1. I [Intune på Azure Portal](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Enheter** > väljer enheten > **Tilldela användare**.
    ![Skärmbild av Tilldela användare](media/enrollment-autopilot/assign-user.png)
2. Välj en Azure-användare som är licensierad för att använda Intune och välj **Välj**.
    ![Skärmbild av välj användare](media/enrollment-autopilot/select-user.png)
3. I rutan **Användarvänligt namn** skriver du ett eget namn eller godkänner standarden. Det här är det egna namn som visas när användaren loggar in under Windows-installationen.
    ![Skärmbild av eget namn](media/enrollment-autopilot/friendly-name.png)
4. Välj **Ok**.


## <a name="delete-autopilot-devices"></a>Ta bort AutoPilot-enheter

Du kan ta bort Windows AutoPilot-enheter som inte har registrerats.

1. Om enheterna har registrerats i Intune måste du först [ta bort dem från Azure Active Directory-portalen](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. I [Intune på Azure Portal](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Enheter**.

3. Under **Windows AutoPilot-enheter**, välj de enheter som du vill ta bort och välj sedan **Ta bort**.

4. Bekräfta borttagningen genom att välja **Ja**. Det kan ta några minuter att ta bort.

## <a name="using-autopilot-in-other-portals"></a>Använda AutoPilot i andra portaler
Om du inte är intresserad av hantering av mobila enheter kan du använda AutoPilot i till exempel Microsoft Store för företag. Det går att använda andra portaler, men vi rekommenderar att du enbart hanterar dina AutoPilot-distributioner i Intune. Om du använder Intune med en annan portal kan inte Intune:
- Visa ändringar i profiler som har skapats i Intune men redigerats i en annan portal
- Synkronisera profiler som har skapats i en annan portal
- Visa ändringar i profiltilldelningar som har gjorts i en annan portal
- Synkronisera profiltilldelningar som har gjorts i en annan portal
- Visa ändringar i listan över enheter som har gjorts i en annan portal

## <a name="next-steps"></a>Nästa steg
Lär dig hur du hanterar enheterna när du har konfigurerat Windows AutoPilot för registrerade Windows 10-enheter. Mer information finns i [Vad är Microsoft Intune-enhetshantering?](https://docs.microsoft.com/intune/device-management)
