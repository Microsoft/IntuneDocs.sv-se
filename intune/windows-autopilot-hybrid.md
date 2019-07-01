---
title: Registrering för Azure AD-anslutna hybridenheter – Windows Autopilot
titleSuffix: ''
description: Använd Windows Autopilot till att registrera Azure AD-anslutna hybridenheter i Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cb9d1f52ccb147dc9a412f3cb7b601e3b18f214a
ms.sourcegitcommit: a63b9eaa59867ab2b0a6aa415c19d9fff4fda874
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389325"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot"></a>Distribuera Azure AD-anslutna hybridenheter med hjälp av Intune och Windows Autopilot
Du kan använda Intune och Windows Autopilot för att konfigurera Azure Active Directory-anslutna hybridenheter. Du gör det genom att följa stegen i den här artikeln.

## <a name="prerequisites"></a>Krav

Konfigurera [Azure AD-anslutna hybridenheterna](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan). [Verifiera enhetsregistreringen]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration) med hjälp av cmdleten Get-MsolDevice.

Enheter som ska registreras måste också:
- Köra Windows 10, v1809 eller senare.
- Ha åtkomst till Internet.
- Ha åtkomst till din Active Directory (VPN-anslutning stöds inte i nuläget).
- Gå igenom välkomstupplevelsen (OOBE, Out-of-Box Experience).
- Kunna pinga domänkontrollanten på den domän som du försöker ansluta till.

## <a name="set-up-windows-10-automatic-enrollment"></a>Konfigurera automatisk registrering i Windows 10

1. Logga in på [Azure Portal](https://portal.azure.com) och välj **Azure Active Directory** i det vänstra fönstret.

   ![Azure Portal](./media/auto-enroll-azure-main.png)

1. Välj **Mobility (MDM och MAM)** .

   ![Azure Active Directory-fönstret](./media/auto-enroll-mdm.png)

1. Välj **Microsoft Intune**.

   ![Fönstret Mobility (MDM och MAM)](./media/auto-enroll-intune.png)

1. Kontrollera att användarna som distribuerar Azure AD-anslutna enheter med Intune och Windows är medlemmar i en grupp som ingår i ditt **MDM-användaromfång**.

   ![Fönstret Konfigurera i Mobility (MDM och MAM)](./media/auto-enroll-scope.png)

1. Använd värdena i rutorna **MDM-användarvillkor-URL**, **Webbadress till MDM-identifiering** och **MDM-kompatibilitets-URL** och välj sedan **Spara**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Öka gränsen för datorkontot i organisationsenheten

Intune Connector för Active Directory skapar Autopilot-registrerade datorer i den lokala Active Directory-domänen. Värddatorn för Intune Connector måste ha behörighet att skapa datorobjekt i domänen. 

I vissa domäner beviljas inte datorer behörighet att skapa datorer. Domäner har dessutom en inbyggd gräns (10 som standard) som gäller för alla användare och datorer som inte har delegerad behörighet att skapa datorobjekt. Därför måste behörigheter delegeras till datorer som är värdar för Intune Connector på organisationsenheten där de Azure AD-anslutna hybridenheterna skapas.

Organisationsenheten som beviljas behörighet att skapa datorer måste matcha:
- Organisationsenheten som anges i domänanslutningsprofilen.
- Om ingen profil valts, datorns domännamn för din domän.

1. Öppna **Active Directory – användare och datorer (DSA.msc)** .

1. Högerklicka på den organisationsenhet som du ska använda för att skapa Azure AD-anslutna hybriddatorer och välj sedan **Delegera kontroll**.

    ![Kommandot för delegering av kontroll](media/windows-autopilot-hybrid/delegate-control.png)

1. I guiden för **delegering av kontroll** väljer du **Nästa** > **Lägg till** > **Objekttyper**.

1. I fönstret **Objekttyper** markerar du kryssrutan **Datorer** och väljer sedan **OK**.

    ![Fönstret Objekttyper](media/windows-autopilot-hybrid/object-types-computers.png)

1. I dialogrutan **Välj användare, datorer eller grupper** går du till rutan för att **ange de objektnamn som du vill välja** och anger namnet på datorn där anslutningsappen är installerad.

    ![Fönstret Välj användare, datorer eller grupper](media/windows-autopilot-hybrid/enter-object-names.png)

1. Välj **Check Names** (Kontrollera namn) för att validera uppgiften och välj **OK**. Välj sedan **Next** (Nästa).

1. Välj **Skapa en anpassad aktivitet och delegera kontroll för den** > **Nästa**.

1. Markera kryssrutan **Endast följande objekt i mappen** och markera sedan kryssrutorna **Datorobjekt**, **Skapa valda objekt i den här mappen** och **Ta bort valda objekt i den här mappen**.

    ![Fönstret Objekttyp för Azure Active Directory](media/windows-autopilot-hybrid/only-following-objects.png)
    
1. Välj **Nästa**.

1. Under **Behörigheter** markerar du kryssrutan **Fullständig kontroll**.  
    Den här åtgärden markerar alla de andra alternativen.

    ![Fönstret Behörigheter](media/windows-autopilot-hybrid/full-control.png)

1. Välj **Nästa** och sedan **Slutför**.

## <a name="install-the-intune-connector"></a>Installera Intune Connector

Intune Connector för Active Directory måste installeras på en dator som kör Windows Server 2016 eller senare. Datorn måste också ha åtkomst till internet och din Active Directory. Om du vill öka skalningen och tillgängligheten eller om du vill ha stöd för flera Active Directory-domäner kan du installera flera anslutningsprogram i din miljö. Vi rekommenderar att du installerar anslutningsappen på en server som inte kör några andra Intune-anslutningsappar.

1. Se till att du har ett språkpaket installerat och konfigurerat enligt beskrivningen i [Språkkrav för Intune Connector (förhandsversion)](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector).
2. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Intune Connector för Active Directory (förhandsversion)**  > **Lägg till anslutningsapp**. 
3. Följ anvisningarna för att ladda ned Connector.
4. Öppna den nedladdade konfigurationsfilen för anslutningsappen, *ODJConnectorBootstrapper.exe*, för att installera Connector.
5. Välj **Konfigurera** i slutet av konfigurationen.
6. Välj **Logga in.**
7. Ange autentiseringsuppgifter för rollen Global administratör eller Intune-administratör.  
   Användarkontot måste ha en tilldelad Intune-licens.
8. Gå till **Enhetsregistrering** > **Windows-registrering** > **Intune Connector för Active Directory (förhandsversion)** och bekräfta sedan att anslutningsstatusen är **Aktiv**.

> [!NOTE]
> När du har loggat in på Connector kan det ta några minuter innan det visas i [Intune](https://aka.ms/intuneportal). Det visas bara om den kan kommunicera med Intune-tjänsten.

### <a name="turn-off-ie-enhanced-security-configuration"></a>Aktivera förbättrad säkerhetskonfiguration i IE
Som standard har Windows Server förbättrad säkerhetskonfiguration i Internet Explorer aktiverat. Om du inte kan logga in på Intune Connector för Active Directory ska du inaktivera Förbättrad säkerhetskonfiguration i IE för administratören. [Så här inaktiverar du Förbättrad säkerhetskonfiguration i Internet Explorer](https://blogs.technet.microsoft.com/chenley/2011/03/10/how-to-turn-off-internet-explorer-enhanced-security-configuration)

### <a name="configure-web-proxy-settings"></a>Konfigurera webbproxyinställningar

Om du har en webbproxy i nätverksmiljön kontrollerar du att Intune Connector för Active Directory fungerar korrekt, i [Arbeta med befintliga lokala proxyservrar](autopilot-hybrid-connector-proxy.md).


## <a name="create-a-device-group"></a>Skapa en enhetsgrupp
1. I [Intune](https://aka.ms/intuneportal) väljer du **Grupper** > **Ny grupp**.

1. I fönstret **Grupp** gör du följande:

    a. I **Grupptyp** väljer du **Säkerhet**.

    b. Ange ett **gruppnamn** och en **gruppbeskrivning**.

    c. Välj en **medlemskapstyp**.

1. Om du har valt **Dynamiska enheter** som medlemskapstyp väljer du **Dynamiska enhetsmedlemmar** i fönstret **Grupp** och gör sedan något av följande i **Avancerad regel**:
    - Om du vill skapa en grupp som innehåller alla dina Autopilot-enheter anger du `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`.
    - Intunes grupptaggfält mappar till OrderID-attributet på Azure AD-enheter. Om du vill skapa en grupp som innehåller alla dina Autopilot-enheter med en viss grupptagg (OrderID) måste du ange:  `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Om du vill skapa en grupp som innehåller alla dina Autopilot-enheter med ett visst beställnings-ID anger du `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`.
    
1. Välj **Spara**.

1. Välj **Skapa**.  

## <a name="register-your-autopilot-devices"></a>Registrera dina Autopilot-enheter

Välj något av följande sätt för att registrera dina Autopilot-enheter.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registrera Autopilot-enheter som redan har registrerats

1. Skapa en Autopilot-distributionsprofil med **Omvandla alla målenheter till Autopilot** inställt till **Ja**. 
2. Tilldela profilen till en grupp som innehåller de medlemmar som du vill registrera automatiskt med Autopilot.

Mer information finns i [Skapa en Autopilot-distributionsprofil](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registrera Autopilot-enheter som inte har registrerats

Om dina enheter inte har registrerats än kan du registrera dem själv. Mer information finns i [Lägg till enheter](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registrera enheter från en OEM-tillverkare

Om du köper nya enheter kan vissa OEM-tillverkare registrera enheterna åt dig. Mer information finns på [Windows Autopilot-sidan](http://aka.ms/WindowsAutopilot).

När Autopilot-enheter har *registrerats* (och innan de har registrerats i Intune) visas de på tre platser (med namn som motsvarar deras serienummer):
- Fönstret **Autopilot-enheter** i Intune i Azure Portal. Välj **Enhetsregistrering** > **Windows-registrering** > **Enheter**.
- Fönstret **Azure AD-enheter** i Intune i Azure Portal. Välj **Enheter** > **Azure AD-enheter**.
- Fönstret **Alla enheter i Azure Active Directory** i Azure Portal (**Enheter** > **Alla enheter**).

När Autopilot-enheterna har *registrerats* visas de på fyra platser:
- Fönstret **Autopilot-enheter** i Intune i Azure Portal. Välj **Enhetsregistrering** > **Windows-registrering** > **Enheter**.
- Fönstret **Azure AD-enheter** i Intune i Azure Portal. Välj **Enheter** > **Azure AD-enheter**.
- Fönstret **Alla enheter i Azure Active Directory** i Azure Portal. Välj **Enheter** > **Alla enheter**.
- Fönstret **Alla enheter** i Intune i Azure Portal. Välj **Enheter** > **Alla enheter**.

När Autopilot-enheterna har registrerats ändras deras enhetsnamn till värdnamnet för enheten. Som standard börjar värdnamnet med *DESKTOP-* .


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Skapa och tilldela en Autopilot-distributionsprofil
Autopilot-distributionsprofiler används för att konfigurera Autopilot-enheterna.

1. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > **Skapa profil**.
1. Skriv ett **namn** och (frivilligt) en **beskrivning**.
1. I **Distributionsläge** väljer du **Användarstyrd**.
1. I rutan **Anslut till Azure AD som** väljer du **Hybrid Azure AD-ansluten (förhandsversion)** .
1. Välj **Välkomstupplevelse (OOBE)** , konfigurera alternativen efter behov och välj sedan **Spara**.
1. Välj **Skapa** för att skapa profilen. 
1. I profilfönstret väljer du **Tilldelningar**.
1. Välj **Välj grupper**.
1. I fönstret **Välj grupper** väljer du enhetsgruppen och klickar sedan på **Välj**.

Det tar ungefär 15 minuter innan enhetsprofilens status ändras från *Inte tilldelad* till *Tilldelar* och slutligen till *Tilldelad*.

## <a name="optional-turn-on-the-enrollment-status-page"></a>(Valfritt) Aktivera registreringsstatussidan

1. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Statussidan för registrering**.
1. I fönstret **Statussidan för registrering** väljer du **Standard** > **Inställningar**.
1. I rutan **Show app and profile installation progress** (Visa installationsförlopp för appar och profiler) väljer du **Yes** (Ja).
1. Konfigurera de andra alternativen efter behov.
1. Välj **Spara**.

## <a name="create-and-assign-a-domain-join-profile"></a>Skapa och tilldela en profil för domänanslutning

1. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
1. Ange följande egenskaper:
   - **Namn**: Ange ett beskrivande namn på den nya profilen.
   - **Beskrivning**: Ange en beskrivning av profilen.
   - **Plattform**: Välj **Windows 10 och senare**.
   - **Profiltyp**: Välj **Domänanslutning (förhandsversion)** .
1. Välj **Inställningar** och ange sedan **Datornamnprefix**, **Domännamn** och (valfritt) **Organisationsenhet** i [DN-format](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name). 
1. Välj **OK** > **Skapa**.  
    Profilen skapas och visas i listan.
1. Om du vill tilldela profilen följer du anvisningarna under [Tilldela en enhetsprofil](device-profile-assign.md#assign-a-device-profile) och tilldelar profilen till samma grupp som används i det här steget [Skapa en enhetsgrupp](windows-autopilot-hybrid.md#create-a-device-group)
   - Distribuera flera profiler för domänanslutning
   
     a. Skapa en dynamisk grupp som innehåller alla dina Autopilot-enheter med en specifik Autopilot-distributionsprofil, ange (device.enrollmentProfileName –dvs. ”Autopilot-profilnamn”). 
     
     b. Ersätt ”Autopilot-profilnamn” med namnet på den profil som skapats under [Skapa och tilldela en Autopilot-distributionsprofil](windows-autopilot-hybrid.md#create-and-assign-an-autopilot-deployment-profile). 
     
     c. Skapa flera Autopilot-distributionsprofiler och tilldela den enheten till den profil som angetts i den här dynamiska gruppen.

> [!NOTE]
> Namngivningsfunktionerna för Windows Autopilot för Azure AD-hybridanslutning stöder inte variabler såsom %SERIAL%, och stöder endast prefix för datornamnet.

## <a name="next-steps"></a>Nästa steg

När du har konfigurerat Windows Autopilot rekommenderar vi att du går vidare och lär dig hur du hanterar dessa enheter. Mer information finns i [Vad är Microsoft Intune-enhetshantering?](device-management.md).
