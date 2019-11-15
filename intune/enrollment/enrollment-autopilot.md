---
title: Registrera enheter med Windows Autopilot
titleSuffix: Microsoft Intune
description: Läs om hur du registrerar Windows 10-enheter med Windows Autopilot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 454d23038a593829ea8a14929dc435e9f9ddb457
ms.sourcegitcommit: 556b7ea2049014c9027f0e44affd3f301fab55fc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73709485"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Registrera Windows-enheter i Intune med hjälp av Windows Autopilot  
Det är enklare att registrera enheter i Intune med Windows Autopilot. Att skapa och underhålla anpassade operativsystemavbildningar är en process som tar tid. Det kan också ta tid att applicera de här anpassade operativsystemavbildningarna till nya enheter för att förbereda dem för användning innan du ger dem till dina slutanvändare. Med Microsoft Intune och Autopilot kan du ge dina slutanvändare nya enheter utan att behöva skapa, underhålla och installera anpassade operativsystemavbildningar på enheterna. Om du använder Intune för att hantera Autopilot-enheter kan du hantera principer, profiler, appar med mera när de har registrerats. I [översikten över Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot) finns en översikt över fördelar, scenarier och förutsättningar.

Det finns fyra typer av Autopilot-distributioner:
- [Självdistribuerande läge](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) för helskärmslägen, digital signering eller delade enheter
- Med [White Glove](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) kan partners eller IT-personal etablera en Windows 10-dator i förväg, så att den är helt konfigurerad och klar för verksamheten - Med [Autopilot för befintliga enheter](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) kan du enkelt distribuera den senaste versionen av Windows 10 till dina befintliga enheter
- [Användarläge](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) för traditionella användare. 


## <a name="prerequisites"></a>Krav
- [Intune-prenumeration](../fundamentals/licenses.md)
- [Automatisk registrering i Windows aktiverad](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium-prenumeration](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Hämta CSV-filen för import i Intune

Se avsnittet om PowerShell-cmdleten för information.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>Lägg till enheter

Du kan lägga till Windows Autopilot-enheter genom att importera en CSV-fil med deras information.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enhetsregistrering** > **Windows-registrering** > **Enheter** > **Importera**.

    ![Skärmbild av Windows Autopilot-enheter](./media/enrollment-autopilot/autopilot-import-device.png)

2. Under **Lägg till Windows Autopilot-enheter** bläddrar du till en CSV-fil som innehåller en lista med de enheter som du vill lägga till. CSV-filen bör innehålla serienummer, Windows-produkt-ID:n, maskinvaru-hasher, valfria grupptaggar och valfria tilldelade användare. Du kan ha upp till 500 rader i listan. Använd rubrik- och radformatet som visas nedan:

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![Skärmbild av Lägg till Windows Autopilot-enheter](./media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > När du använder CSV-uppladdning för att tilldela en användare måste du se till att du tilldelar giltiga UPN. Om du tilldelar ett ogiltigt UPN (felaktigt användarnamn) kanske enheten inte är tillgänglig förrän du tar bort den ogiltiga tilldelningen. Under CSV-uppladdning är en kontroll av giltigt domännamn den enda validering som utförs på kolumnen **Tilldelad användare**. Vi kan inte utföra en individuell UPN-verifiering för att se till att du tilldelar en befintlig eller korrekt användare.

3. Välj **Importera** för att börja importera enhetsinformationen. Det kan ta flera minuter att importera.

4. När importen är klar väljer du **Enhetsregistrering** > **Windows-registrering** > **Windows Autopilot** > **Enheter** > **Synkronisera**. Ett meddelande visar att synkroniseringen pågår. Processen kan ta några minuter att slutföra beroende på hur många enheter som synkroniseras.

5. Uppdatera vyn för att se de nya enheterna.

## <a name="create-an-autopilot-device-group"></a>Skapa en Autopilot-enhetsgrupp

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Grupper** > **Ny grupp**.
2. På bladet **Grupp**:
    1. Välj **Säkerhet** för **Grupptyp**.
    2. Ange ett **gruppnamn** och en **gruppbeskrivning**.
    3. För **Medlemstyp** väljer du antingen **Tilldelad** eller **Dynamisk enhet**.
3. Om du valde **Tilldelad** för **Medlemstyp** i föregående steg väljer du **Medlemmar** på bladet **Grupp** och lägger till Autopilot-enheter till gruppen.
    Autopilot-enheter som ännu inte har registrerats är enheter där namnet är samma som enhetens serienummer.
4. Om du väljer **Dynamiska enheter** för **Medlemstyp** ovan väljer du sedan **Dynamiska enhetsmedlemmar** på bladet **Grupp** och anger någon av följande koder i rutan **Avancerad regel**. Det är bara Autopilot-enheter som samlas in av de här reglerna, eftersom de avser attribut som endast finns i Autopilot-enheter. Skapandet av en grupp baserat på icke-Autopilot-attribut garanterar inte att enheter som ingår i gruppen faktiskt registreras till Autopilot.
    - Om du vill skapa en grupp som innehåller alla dina Autopilot-enheter anger du: `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Intunes grupptaggfält mappar till OrderID-attributet på Azure AD-enheter. Om du vill skapa en grupp som innehåller alla dina Autopilot-enheter med en viss grupptagg (Azure AD-enhetens OrderID) måste du ange: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Om du vill skapa en grupp som innehåller alla dina Autopilot-enheter med ett visst inköpsorder-ID anger du `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    När du har lagt till koden för **Avancerad regel** väljer du **Spara**.
5. Välj **Skapa**.  

## <a name="create-an-autopilot-deployment-profile"></a>Skapa en Autopilot-distributionsprofil
Autopilot-distributionsprofiler används för att konfigurera Autopilot-enheterna. Du kan skapa upp till 350 profiler per klientorganisation.
1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > **Skapa profil**.
2. På sidan **Grundinställningar** anger du ett **Namn** och en valfri **Beskrivning**.

    ![Skärmbild av sidan Grundinställningar](./media/enrollment-autopilot/create-profile-basics.png)

3. Om du vill att alla enheter i de tilldelade grupperna automatiskt ska omvandlas till Autopilot väljer du **Ja** för **Omvandla alla målenheter till Autopilot**. Enheter som ägs av företaget och som inte är Autopilot-enheter i tilldelade grupper registreras med Autopilot-distributionstjänsten. Personligt ägda enheter kommer inte att konverteras till autopilot. Det kan ta upp till 48 timmar för registreringen att bearbetas. När enheten har avregistrerats och återställts registreras den av Autopilot. När en enhet har registrerats på det här sättet tas inte enheten bort från Autopilot-distributionstjänsten om det här alternativet inaktiveras eller om profiltilldelningen tas bort. Du måste i stället [ta bort enheten direkt](enrollment-autopilot.md#delete-autopilot-devices).
4. Välj **Nästa**.
5. På sidan **Välkomstupplevelse (OOBE)** för **Distributionsläge** väljer du något av följande två alternativ:
    - **Användarstyrda**: Enheter med den här profilen är associerade med användaren som registrerar enheten. Autentiseringsuppgifter krävs för att registrera enheten.
    - **Självdistribution (förhandsversion)** : (kräver Windows 10, version 1809 eller senare) Enheter med den här profilen inte är associerade med användaren som registrerar enheten. Autentiseringsuppgifter krävs inte för att registrera enheten. När en enhet inte har någon användare associerad, gäller inte användarbaserade efterlevnadsprinciper. Om du använder ett självdistribuerande läge, tillämpas bara efterlevnadsprinciper som avser enheten.

    ![Skärmbild av OOBE-sidan](./media/enrollment-autopilot/create-profile-outofbox.png)

6. Välj **Azure AD-ansluten** i **Anslut till Azure AD som**.
7. Konfigurera följande alternativ:
    - **Licensavtal för slutanvändare (EULA)** : (Windows 10, version 1709 eller senare) Välj om du vill visa EULA för användarna.
    - **Sekretessinställningar**: Välj om du vill visa sekretessinställningar för användarna.
    >[!IMPORTANT]
    >Standardvärdet för inställningen av diagnostikdata varierar mellan olika versioner av Windows. För enheter som kör Windows 10, version 1903, är standardvärdet inställt på fullständig under välkomstupplevelsen. Mer information finns i [Windows-diagnostikdata](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data). <br>
    
    - **Dölj alternativ för att ändra konto (kräver Windows 10, version 1809 eller senare)** : Välj **Dölj** om du vill förhindra att alternativ för att ändra kontot visas på företagets sidor för inloggning och domänfel. Genom att dölja de här alternativen krävs att [företagsanpassning konfigureras i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Användarkontotyp**: Välj användarens kontotyp (**Administratör** eller **Standardanvändare**). Vi tillåter att användaren ansluter enheten som lokal administratör genom att lägga till dem i den lokala administratörsgruppen. Vi aktiverar inte användaren som standardadministratör på enheten.
    - **Tillåt White Glove OOBE** (kräver Windows 10, version 1903 eller senare. [Ytterligare fysiska krav](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)): Välj **Ja** för att tillåta assisterad support.
    - **Använd mall för enhetsnamn** (kräver Windows 10 version 1809 eller senare och Azure AD-anslutningstyp): Välj **Ja** för att skapa en mall som ska användas när du namnger en enhet under registreringen. Namn får innehålla högst 15 tecken, och får innehålla bokstäver, siffror och bindestreck. Namn kan inte bestå av enbart siffror. Använd [makrot %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) för att lägga till ett maskinvaruspecifikt serienummer. Du kan även använda [makrot %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) för att lägga till en slumpmässig sträng med siffror, där x motsvarar antalet siffror som ska läggas till. Du kan bara ange ett prefix för hybridenheter i en [domänanslutningsprofil](windows-autopilot-hybrid.md#create-and-assign-a-domain-join-profile). 
    - **Språk (Region)** \*: Välj et språk som du vill använda för enheten. Det här alternativet är endast tillgängligt om du har valt **Självdistribution** som **Distributionsläge**.
    - **Konfigurera tangentbord automatiskt**\*: Om ett **Språk (Region)** har valts väljer du **Ja** för att hoppa över sidan för val av tangentbord. Det här alternativet är endast tillgängligt om du har valt **Självdistribution** som **Distributionsläge**.
8. Välj **Nästa**.
9. På sidan **Omfångstaggar** lägger du eventuellt till omfångstaggar som du vill använda för den här profilen. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar för distribuerad IT](../fundamentals/scope-tags.md).
10. Välj **Nästa**.
11. På sidan **Tilldelningar** väljer du **Valda grupper** för **Tilldela till**.

    ![Skärmbild av sidan över tilldelningar](./media/enrollment-autopilot/create-profile-assignments.png)

12. Välj **Välj grupper att ta med** och välj de grupper som du vill ta med i den här profilen.
13. Om du vill undanta några grupper väljer du **Välj grupper att utesluta** och väljer de grupper som du vill undanta.
14. Välj **Nästa**.
15. På sidan **Granska och skapa** väljer du **Skapa** för att skapa profilen.

    ![Skärmbild av granskningssidan](./media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Intune söker regelbundet efter nya enheter i de tilldelade grupperna och påbörjar sedan processen med att tilldela profiler till dessa enheter. Det kan ta flera minuter att slutföra processen. Se till att processen har slutförs innan du distribuerar en enhet.  Du kan kontrollera detta under **Enhetsregistrering** > **Windows-registrering** > **Enheter**, där du bör se att profilstatusen ändras från ”Ej tilldelad” till ”Tilldelar” och slutligen ”Tilldelad”.

## <a name="edit-an-autopilot-deployment-profile"></a>Redigera en Autopilot-distributionsprofil
När du har skapat en Autopilot-distributionsprofil kan du redigera vissa delar av den.   

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enhetsregistrering**.
2. Under **Windows-registrering** i avsnittet **Windows Autopilot** väljer du **Distributionsprofiler**.
3. Välj den profil du vill redigera.
4. Klicka på **Egenskaper** till vänster om du vill ändra distributionsprofilens namn eller beskrivning. Klicka på **Spara** när du har gjort ändringarna.
5. Klicka på **Inställningar** när du vill göra ändringar i OOBE-inställningarna. Klicka på **Spara** när du har gjort ändringarna.

> [!NOTE]
> Ändringar i profilen tillämpas på enheter som är tilldelade till profilen. Den uppdaterade profilen tillämpas emellertid inte på enheter som redan har registrerats i Intune förrän enheten har återställts och omregistrerats.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Aviseringar för otilldelade Windows Autopilot-enheter  <!-- 163236 -->  

Aviseringar visar hur många Autopilot-programenheter som inte har Autopilot-distributionsprofiler. Använd informationen i aviseringen för att skapa profiler och tilldela dem till de otilldelade enheterna. När du klickar på aviseringen visas en fullständig lista över Windows Autopilot-enheter och detaljerad information om dem.

Om du vill visa aviseringar för otilldelade enheter väljer du **Enhetsregistrering** > **Översikt** > **Ej tilldelade enheter** i [Intune i Azure-portalen](https://aka.ms/intuneportal).  

## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Tilldela en användare till en specifik Autopilot-enhet

Du kan tilldela en användare till en specifik Autopilot-enhet. Den här tilldelningen gör att en användare fylls i på förhand från Azure Active Directory på den [företagsanpassade](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) inloggningssidan under Windows-installationen. Du kan även ange ett anpassat namn för hälsning. Windows-inloggningen fylls inte i i förväg och ändras inte. Endast licensierade Intune-användare kan tilldelas på detta sätt.

Krav: Azure Active Directory Företagsportal har konfigurerats och Windows 10, version 1809 eller senare.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enhetsregistrering** > **Windows-registrering** > **Enheter** > välj enheten > **Tilldela användare**.

    ![Skärmbild av Tilldela användare](./media/enrollment-autopilot/assign-user.png)

2. Välj en Azure-användare som är licensierad för att använda Intune och välj **Välj**.

    ![Skärmbild av Välj användare](./media/enrollment-autopilot/select-user.png)

3. I rutan **Användarvänligt namn** skriver du ett eget namn eller godkänner standarden. Den här strängen är det egna namn som visas när användaren loggar in under Windows-installationen.

    ![Skärmbild av eget namn](./media/enrollment-autopilot/friendly-name.png)

4. Välj **Ok**.

## <a name="autopilot-deployments-report"></a>Rapport om Autopilot-distributioner
Du kan se information om varje enhet som distribueras via Windows Autopilot.
Om du vill se rapporten går du till **Intune**. Under **Övervaka** väljer du **Autopilot-distributioner**.
Data är tillgängliga i 30 dagar efter distribution.


## <a name="delete-autopilot-devices"></a>Ta bort Autopilot-enheter

Du kan ta bort Windows Autopilot-enheter som inte har registrerats på Intune:

- Ta bort enheterna från Windows Autopilot på **Enhetsregistrering** > **Windows-registrering** > **Enheter**. Välj de enheter som du vill ta bort och välj sedan **Ta bort**. Det kan ta några minuter att ta bort en Windows Autopilot-enhet.

Om du vill ta bort en enhet helt från klienten fullständigt måste du ta bort Intune-enheten, Azure Active Directory-enheten och Windows Autopilot-enhetsposterna. Det kan du göra från Intune:

1. Om enheterna har registrerats i Intune måste du först [ta bort dem från Intune-bladet Alla enheter](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Ta bort enheterna på Azure Active Directory-enheter via **Enheter** > **Azure AD-enheter**.

3. Ta bort enheterna från Windows Autopilot på **Enhetsregistrering** > **Windows-registrering** > **Enheter**. Välj de enheter som du vill ta bort och välj sedan **Ta bort**. Det kan ta några minuter att ta bort en Windows Autopilot-enhet.

## <a name="using-autopilot-in-other-portals"></a>Använda Autopilot på andra portaler
Om du inte är intresserad av hantering av mobilenheter kan du använda Autopilot på andra portaler. Det går att använda andra portaler, men vi rekommenderar att du enbart hanterar dina Autopilot-distributioner i Intune. När du använder Intune med en annan portal kan inte Intune:  

- Visa ändringar i profiler som har skapats i Intune men redigerats i en annan portal
- Synkronisera profiler som har skapats i en annan portal
- Visa ändringar i profiltilldelningar som har gjorts i en annan portal
- Synkronisera profiltilldelningar som har gjorts i en annan portal
- Visa ändringar i listan över enheter som har gjorts i en annan portal

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot för befintliga enheter

Du kan gruppera Windows-enheter med ett korrelator-ID vid registrering med hjälp av [Autopilot för befintliga enheter](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) via Configuration Manager. Korrelator-ID:t är en parameter i Autopilot-konfigurationsfilen. [Azure Active Directory-enhetsattributet enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) matchas automatiskt med ”OfflineAutopilotprofile-\<korrelator-ID:t\>”. På så sätt kan godtyckliga dynamiska Azure AD-grupper skapas baserat på korrelator-ID med hjälp av attributet enrollmentprofileName.

>[!WARNING] 
> Eftersom korrelator-ID:t inte redan finns i Intune kan enheten rapportera valfritt korrelator-ID. Om du skapar ett korrelator-ID som matchar ett Autopilot- eller Apples DEP-profilnamn, läggs enheten till en dynamisk Azure Active Directory-enhetsgrupp som baseras på enrollmentProfileName-attributet. Så här undviker du konflikten:
> - Skapa alltid regler för dynamisk matchning mot *hela* enrollmentProfileName-värdet
> - Namnge aldrig Autopilot- eller Apple DEP-profiler med början ”OfflineAutopilotprofile-”.

## <a name="next-steps"></a>Nästa steg
Lär dig hur du hanterar enheterna när du har konfigurerat Windows Autopilot för registrerade Windows 10-enheter. Mer information finns i [Vad är Microsoft Intune-enhetshantering?](../remote-actions/device-management.md)
