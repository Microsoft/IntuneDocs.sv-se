---
title: Konfigurera Intune-registrering för Hybrid Active Directory-anslutna enheter med Windows Autopilot
titleSuffix: Microsoft Intune
description: Använd Windows Autopilot för att registrera Hybrid Active Directory-anslutna enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1a10d434fbdb5d827c7ecb89d1ae2f7e43c0f951
ms.sourcegitcommit: 1e6fee4032c50ab41a5166db39fbea80a731c541
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51654916"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-using-intune-and-windows-autopilot-preview"></a>Distribuera Hybrid Azure AD-anslutna enheter med Intune och Autopilot för Windows (förhandsversion)
Du kan använda Intune och Windows Autopilot för att konfigurera Hybrid Azure Active Directory-anslutna enheter. Du gör det genom att följa stegen nedan.

> [!NOTE]
> Den här funktionen kommer att lanseras till hela användarbasen under de närmaste dagarna. Därför kanske du inte kan följa stegen förrän funktionen har distribuerats till ditt konto.

## <a name="prerequisites"></a>Krav

- Konfigurera [Hybrid Azure Active Directory-ansluta enheter](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan).
    - Verifiera [registreringen med hjälp av cmdleten Get-MsolDevice]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration).

Enheter som ska registreras måste också:
- Köra Windows 10 med [uppdateringen för oktober 2018](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/).
- Ha åtkomst till Internet.
- Ha åtkomst till din Active Directory (VPN-anslutning stöds inte).
- Gå igenom välkomstupplevelsen (OOBE, Out-of-Box Experience).

## <a name="set-up-windows-10-automatic-enrollment"></a>Konfigurera automatisk registrering i Windows 10

1. Logga in på [Azure Portal](https://portal.azure.com) och välj **Azure Active Directory**.

   ![Skärmbild av Azure-portalen](./media/auto-enroll-azure-main.png)

2. Välj **Mobility (MDM och MAM)**.

   ![Skärmbild av Azure-portalen](./media/auto-enroll-mdm.png)

3. Välj **Microsoft Intune**.

   ![Skärmbild av Azure-portalen](./media/auto-enroll-intune.png)

4. Kontrollera att användarna som distribuerar Azure Active Directory-anslutna enheter med Intune och Windows är medlemmar i en grupp som ingår i ditt **MDM-användaromfång**.

   ![Skärmbild av Azure-portalen](./media/auto-enroll-scope.png)

5. Använd standardvärdena för följande URL:er:
    - **Webbadress till MDM-användarvillkor**
    - **Webbadress till MDM-identifiering**
    - **Webbadress till MDM-kompatibilitet**
6. Välj **Spara**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Öka gränsen för datorkontot i organisationsenheten

Intune Connector för Active Directory skapar Autopilot-registrerade datorer i den lokala Active Directory-domänen. Värddatorn för Intune Connector måste ha behörighet att skapa datorobjekt i domänen. 

I vissa domäner beviljas inte datorer behörighet att skapa datorer. Eller så kanske administratörer inte vill öka gränsen för hela domänens datorkonton. I dessa fall kan rättigheter delegeras till organisationsenheten där Azure AD-anslutna enheter skapas.

Organisationsenheten som beviljas behörighet att skapa datorer måste matcha:
- organisationsenheten som anges i domänanslutningsprofilen
- eller, om ingen profil valts, datorns domännamn för din domän.

1. Öppna **Active Directory – användare och datorer** (DSA.msc).

2. Högerklicka på den organisationsenhet som du ska använda för att skapa Hybrid Azure AD-anslutna datorer > **Delegera kontroll**.

    ![Skärmbild av Delegera kontroll](media/windows-autopilot-hybrid/delegate-control.png)

3. I guiden för **delegering av kontroll** väljer du **Nästa** > **Lägg till** > **Objekttyper**.

4. I dialogrutan **Objekttyper** markerar du **Datorer** och väljer sedan **OK**.

    ![Skärmbild av Delegera kontroll](media/windows-autopilot-hybrid/object-types-computers.png)

5. I dialogrutan **Välj användare, datorer eller grupper** går du till rutan för att **ange de objektnamn som du vill välja** och anger namnet på datorn där anslutningsappen är installerad.

    ![Skärmbild av Delegera kontroll](media/windows-autopilot-hybrid/enter-object-names.png)

6. Välj **Kontrollera namn** för att verifiera din inmatning och klicka sedan på **OK** > **Nästa**.

7. Välj **Skapa en anpassad aktivitet och delegera kontroll för den** > **Nästa**.

8. Välj **Endast följande objekt i mappen** och kontrollera sedan följande alternativ:
    - **Datorobjekt**
    - **Skapa markerade objekt i den här mappen**
    - **Ta bort markerade objekt i den här mappen**

    ![Skärmbild av Delegera kontroll](media/windows-autopilot-hybrid/only-following-objects.png)
    
9. Välj **Nästa**.

10. Under **Behörigheter** markerar du **Fullständig kontroll** (när du gör det markeras alla andra alternativ) > **Nästa** > **Slutför**.

    ![Skärmbild av Delegera kontroll](media/windows-autopilot-hybrid/full-control.png)

## <a name="install-the-intune-connector"></a>Installera Intune Connector

Intune Connector för Active Directory måste installeras på en dator som kör Windows Server 2016 och som har åtkomst till Internet och din Active Directory. Om du vill öka skalningen och tillgängligheten eller om du vill ha stöd för flera Active Directory-domäner kan du installera flera anslutningsprogram i din miljö. Vi rekommenderar att du installerar anslutningsappen på en server som inte kör några andra Intune-anslutningsappar.

1. Se till att du har ett språkpaket installerat och konfigurerat enligt beskrivningen i [Språkkrav för Intune Connector (förhandsversion)](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector).
2. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Intune Connector för Active Directory (förhandsversion)** > **Lägg till anslutningsapp**. 
3. Följ anvisningarna för att ladda ned anslutningsappen.
4. Öppna konfigurationsfilen för det nedladdade anslutningsprogrammet för att installera programmet (ODJConnectorBootstrapper.exe).
5. I slutet av installationen väljer du **Konfigurera**.
6. Välj **Logga in**.
7. Ange autentiseringsuppgifter för rollen Global administratör eller Intune-administratör.
8. Gå till **Enhetsregistrering** > **Windows-registrering** > **Intune Connector för Active Directory (förhandsversion)** och bekräfta att anslutningsstatusen är **Aktiv**.

### <a name="configure-web-proxy-settings"></a>Konfigurera webbproxyinställningar

Om du har en webbproxy i din nätverksmiljö följer du anvisningarna här så att Intune Connector för Active Directory fungerar korrekt: [Arbeta med befintliga lokala proxyservrar](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers).


## <a name="create-a-device-group"></a>Skapa en enhetsgrupp
1. I [Intune](https://aka.ms/intuneportal) väljer du **Grupper** > **Ny grupp**.
2. På bladet **Grupp**:
    1. Välj **Säkerhet** för **Grupptyp**.
    2. Ange ett **gruppnamn** och en **gruppbeskrivning**.
    3. Välj en **medlemskapstyp**.
3. Om du väljer **Dynamiska enheter** för **Medlemstyp** ovan väljer du sedan **Dynamiska enhetsmedlemmar** på bladet **Grupp** och anger någon av följande koder i rutan **Avancerad regel**.
    - Om du vill skapa en grupp som innehåller alla dina Autopilot-enheter anger du `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Om du vill skapa en grupp som innehåller alla dina Autopilot-enheter med ett visst beställnings-ID anger du `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Om du vill skapa en grupp som innehåller alla dina Autopilot-enheter med ett visst inköpsorder-ID anger du `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    När du har lagt till koden för **Avancerad regel** väljer du **Spara**.
5. Välj **Skapa**.  

## <a name="register-your-autopilot-devices"></a>Registrera dina Autopilot-enheter

Välj något av följande sätt för att registrera dina Autopilot-enheter:

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registrera Autopilot-enheter som redan har registrerats

1. Skapa en Autopilot-distributionsprofil med **Omvandla alla målenheter till Autopilot** inställt till **Ja**. 
2. Tilldela profilen till en grupp som innehåller de medlemmar som du vill registrera automatiskt med Autopilot.

Mer information finns i [Skapa en Autopilot-distributionsprofil](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registrera Autopilot-enheter som inte har registrerats

Om dina enheter inte har registrerats än kan du registrera dem själv. Mer information finns i [Lägg till enheter](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registrera enheter från en OEM-tillverkare

Om du köper nya enheter kan vissa OEM-tillverkare registrera enheterna åt dig. Mer information finns på [Windows Autopilot-sidan](http://aka.ms/WindowsAutopilot).

När Autopilot-enheter har registrerats (och innan de har registrerats i Intune) visas de på tre platser (med namn som motsvarar deras serienummer):
- Bladet Autopilot-enheter i Intune på Azure-portalen (**Enhetsregistrering** > **Windows-registrering** > **Enheter**).
- Bladet Azure AD-enheter i Intune på Azure-portalen (**Enheter** > **Azure AD-enheter**).
- Bladet Alla enheter i Azure Active Directory på Azure-portalen (**Enheter** > **Alla enheter**).

När Autopilot-enheter har registrerats visas de på fyra platser:
- Bladet Autopilot-enheter i Intune på Azure-portalen (**Enhetsregistrering** > **Windows-registrering** > **Enheter**).
- Bladet Azure AD-enheter i Intune på Azure-portalen (**Enheter** > **Azure AD-enheter**).
- Bladet Alla enheter i Azure Active Directory på Azure-portalen (**Enheter** > **Alla enheter**).
- Bladet Alla enheter i Intune på Azure-portalen (**Enheter** > **Alla enheter**).

När Autopilot-enheter har registrerats ändras deras enhetsnamn till värdnamnet för enheten. Som standard börjar det med ”DESKTOP-”.




## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Skapa och tilldela en Autopilot-distributionsprofil
Autopilot-distributionsprofiler används för att konfigurera Autopilot-enheterna.

1. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > **Skapa profil**.
2. Ange ett **namn** och en valfri **beskrivning**.
3. I **Distributionsläge** väljer du **Användarstyrd**.
4. I rutan **Anslut till Azure AD som** väljer du **Hybrid Azure AD-ansluten (förhandsversion)**.
5. Välj **Välkomstupplevelse (OOBE)**, konfigurera alternativen efter behov och välj sedan **Spara**.
6. Välj **Skapa** när du vill skapa profilen. 
7. På profilbladet väljer du **Tilldelningar**.
8. Välj **Välj grupper** > på bladet **Välj grupper** väljer du enhetsgruppen > **Välj**.

Det tar ungefär 15 minuter innan enhetsprofilens status ändras från **Inte tilldelad** till **Tilldelar** och slutligen till **Tilldelad**.

## <a name="turn-on-the-enrollment-status-page-optional"></a>Aktivera registreringsstatussidan (valfritt)

1. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Statussidan för registrering (förhandsversion)**.
2. På bladet **Statussidan för registrering**  väljer du **Standard** > **Inställningar**.
3. Välj **Ja** för **Show app and profile installation progress** (Visa installationsförlopp för appar och profiler).
4. Konfigurera de andra alternativen efter behov.
5. Välj **Spara**.

## <a name="create-and-assign-a-domain-join-profile"></a>Skapa och tilldela en profil för domänanslutning

1. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
2. Ange följande egenskaper:
   - **Namn**: Ange ett beskrivande namn på den nya profilen.
   - **Beskrivning:** Ange en beskrivning för profilen.
   - **Plattform**: Välj **Windows 10 och senare**.
   - **Profiltyp**: Välj **Domänanslutning (förhandsversion)**.
3. Välj **Inställningar** och ange ett **datornamnprefix**, ett **domännamn** och en **organisationsenhet** (valfritt). 
4. Välj **OK** > **Skapa**. Profilen skapas och visas i listan.
5. Om du vill tilldela profilen följer du anvisningarna under [Tilldela en enhetsprofil](device-profile-assign.md#assign-a-device-profile). 

## <a name="next-steps"></a>Nästa steg

När du har konfigurerat Windows Autopilot rekommenderar vi att du går vidare och lär dig hur du hanterar dessa enheter. Mer information finns i [Vad är Microsoft Intune-enhetshantering?](device-management.md)
