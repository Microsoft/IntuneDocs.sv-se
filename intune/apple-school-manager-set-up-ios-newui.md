---
title: Konfigurera registrering av Apple School Manager-programmet för iOS-enheter
titleSuffix: Microsoft Intune
description: Läs hur du konfigurerar Apple School Manager-programmets registrering av företagsägda iOS-enheter med Intune (nytt användargränssnitt).
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4c35a23e-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 58a1db63c3fef3b288c42d43ce7ffc5164d81845
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/03/2018
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>Aktivera registrering av iOS-enheter med Apple School Manager

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Tillfälliga skillnader i användargränssnittet
>
>Användargränssnitt för de funktioner som beskrivs i den här sidan håller på att uppdateras. De här uppdateringarna lanseras över alla användarkonton fram till och med den första veckan i maj.
>
>Om din sida för **Enhetsregistrering** ser ut som på bilden nedan, har du det uppdaterade användargränssnittet och kan använda den här hjälpsidan.
>
>![Nytt användargränssnitt](./media/appleenroll-newui.png)
>
>Om din sida för **Enhetsregistrering** ser ut som på bilden nedan, har ditt konto ännu uppdaterats till det nya användargränssnittet. Gå till [den här hjälpsidan](apple-school-manager-set-up-ios.md).
>
>![Gammalt användargränssnitt](./media/appleenroll-oldui.png)

Det här avsnittet hjälper dig att aktivera registrering av iOS-enheter som köpts via [Apple School Manager](https://school.apple.com/)-programmet. Med hjälp av Intune med Apple School Manager kan du registrera många iOS-enheter utan att ens behöva röra dem. När en student eller en lärare sätter på enheten körs installationsassistenten med de konfigurerade inställningarna och enheten registreras i hanteringen.

Om du vill aktivera Apple School Manager-registrering använder du både Intune-portalen och Apple School Manager-portalen. En lista med serienummer eller inköpsordernummer krävs så att du kan tilldela enheter till Intune för hantering. Du kan skapa DEP-registreringsprofiler som innehåller inställningar som verkställs på enheterna under registreringen.

Apple School Manager-registrering kan inte användas med [Apples program för enhetsregistrering](device-enrollment-program-enroll-ios.md) eller [enhetsregistreringshanteraren](device-enrollment-manager-enroll.md).

**Förutsättningar**
- [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)
- [MDM-utfärdare](mdm-authority-set.md)
- [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)
- Mappning mellan användare kräver [WS-Trust 1.3 användarnamn/kombinerad slutpunkt](https://technet.microsoft.com/library/adfs2-help-endpoints). [Läs mer](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
- Enheter som köpts från programmet [Apple School Management](http://school.apple.com)

## <a name="get-an-apple-token-and-assign-devices"></a>Skaffa en Apple-token och tilldela enheter

Innan du kan registrera företagsägda iOS-enheter med Apple School Manager behöver du en tokenfil (.p7m) från Apple. Med denna token kan Intune synkronisera information om enheter som är anslutna till Apple School Manager. Intune kan även utföra överföringar av registreringsprofilen till Apple och tilldela enheter till dessa profiler. I Apples portal kan du också tilldela de enhetsserienummer som ska hanteras.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-an-apple-token"></a>Steg 1. Ladda ned certifikatet för den offentliga Intune-nyckel som krävs för att skapa en Apple-token

1. I [Intune](https://aka.ms/intuneportal), väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > **Lägg till**.

   ![Hämta en registreringsprogramtoken.](./media/device-enrollment-program-enroll-ios/image01.png)

2. På bladet **Token för registreringsprogram** väljer du **Ladda ned din offentliga nyckel** för att ladda ned och spara krypteringsnyckelfilen (.pem) lokalt. .pem-filen används för att begära ett förtroendecertifikat från Apple School Manager-portalen.
     ![Registreringsprogramtokenbladet.](./media/device-enrollment-program-enroll-ios/image02.png)

### <a name="step-2-download-a-token-and-assign-devices"></a>Steg 2. Ladda ned en token och tilldela enheter
1. Välj **Skapa en token via Apple School Manager** och logga in på Apple School med ditt företags Apple-ID. Du kan använda detta Apple-ID när du behöver förnya din Apple School Manager-token.
2.  I [Apple School Manager-portalen](https://school.apple.com) går du till **MDM-servrar** och väljer sedan **Lägg till MDM-server** (längst upp till höger).
3.  Ange **MDM-serverns namn**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.
   ![Skärmbild av Apple School Manager-portalen med serienummeralternativet markerat](./media/asm-server-assignment.png)

4.  Välj **Ladda upp fil...**  i Apples portal, bläddra till .pem-filen och välj **Spara MDM-server** (längst ned till höger).
5.  Välj **Hämta token** och ladda ned servertokenfilen (.p7m) till datorn.
6. Gå till **Enhetstilldelningar** och **Välj enhet** med manuell inmatning av **Serienummer**, **Ordernummer** eller **Överför CSV-fil**.
     ![Skärmbild av Apple School Manager-portalen med serienummeralternativet markerat](./media/asm-device-assignment.png)
7.  Välj åtgärden **Tilldela till server** och välj den **MDM-server** som du skapade.
8. Ange alternativ för **Välj enheter** och ange sedan enhetsinformation.
9. Välj **Tilldela till server** och välj &lt;servernamnet&gt; som angetts för Microsoft Intune och sedan **OK**.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Steg 3. Spara det Apple-ID som användes för att skapa den här token

I Intune på Azure-portalen anger du ditt Apple-ID för framtida bruk.

![Skärmbild av någon som anger det Apple-ID som användes för att skapa registreringsprogramtoken och bläddrat till denna token.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Steg 4. Överför din token
I rutan **Apple-token**, bläddrar du till certifikatfilen (.pem), väljer **Öppna** och väljer sedan **Skapa**. Med pushcertifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter. Intune synkroniserar automatiskt dina Apple School Manager-enheter från Apple.

## <a name="create-an-apple-enrollment-profile"></a>Skapa en Apple-registreringsprofil
Nu när du har installerat din token, kan du skapa en registreringsprofil för Apple School-enheter. En enhetsregistreringsprofil definierar inställningarna som tillämpas på en grupp av enheter vid registreringen.

1. I [Intune](https://aka.ms/intuneportal), väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens**.
2. Välj en token, välj **Profiler** och välj sedan **Skapa profil**.
3. Under **Skapa profil**, anger du ett **Namn** och **Beskrivning** för profilen för administrationssyfte. Användarna kan inte se den här informationen. Du kan använda fältet **Namn** för att skapa en dynamisk grupp i Azure Active Directory. Använd profilnamnet för att definiera parametern enrollmentProfileName för att tilldela registreringsprofilen till enheter. Läs mer om [dynamiska Azure Active Directory-grupper](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).
    ![Profilnamn och beskrivning.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Ange om enheter med den här profilen måste registreras med eller utan en tilldelad användare under **Användartillhörighet**.
    - **Registrera med användartillhörighet** – välj det här alternativet för enheter som tillhör användare och som vill använda företagsportalen för tjänster som installation av appar. Det här alternativet låter också användare autentisera sina enheter med företagsportalen. Mappning mellan användare kräver [WS-Trust 1.3 användarnamn/kombinerad slutpunkt](https://technet.microsoft.com/library/adfs2-help-endpoints). [Läs mer](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).   Det delade iPad-läget i Apple School Manager innebär att användarna måste registrera sig utan användartillhörighet.

    - **Registrera utan användartillhörighet** – välj det här alternativet för enheter som inte är kopplade till en enda användare, till exempel en delad enhet. Använd det här för enheter som utför uppgifter utan att komma åt lokala användardata. Appar som företagsportalappen fungerar inte.

5. Om du väljer **Registrera med användartillhörighet**, får du alternativet att låta användare autentisera sig med Företagsportalen istället för Apple Installationsassistenten.

    ![Autentisera med Företagsportalen.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    >[!NOTE]
    >Multifaktorautentisering (MFA) fungerar inte vid registrering på Apple School Manager-enheter om du har profilegenskaperna inställda på **Använd med användartillhörighet** och du inte använder en Företagsportal. Efter registreringen fungerar MFA som förväntat på dessa enheter. Enheterna kan inte uppmana användare som behöver ändra sina lösenord när de loggar in första gången. Användare vars lösenord har upphört att gälla ombeds inte att återställa sina lösenord under registreringen. Användarna måste återställa lösenordet från en annan enhet.

6. Välj **Inställningar för enhetshantering** och välj om du vill att enheter som använder den här profilen ska övervakas.
    **Övervakade** enheter ger dig fler hanteringsalternativ och inaktiverar aktiveringslåset som standard. Microsoft rekommenderar att du använder DEP som mekanism för att aktivera övervakat läge, särskilt för organisationer som distribuerar större antal iOS-enheter.

    Användare meddelas att deras enheter är övervakade på två sätt:

   - Låsskärmen säger: ”Den här iPhone hanteras av Contoso.”
   - Skärmen **Inställningar** > **Allmänt** > **Om** säger: ”Den här iPhone är övervakad. Contoso can monitor your Internet traffic and locate this device." (Denna iPhone är övervakad. Contoso kan övervaka din Internettrafik och hitta denna enhet.)

     > [!NOTE]
     > En enhet som registrerats utan övervakning kan bara återställas genom att använda Apple Configurator. Om du återställer enheten på det här sättet, måste du ansluta en iOS-enhet till en Mac-dator med en USB-kabel. Läs mer om detta i [dokumentation för Apple Configurator](http://help.apple.com/configurator/mac/2.3).

7. Välj om du vill ha låst registrering för enheter som använder den här profilen. **Låst registrering** inaktiverar iOS-inställningarna som tillåter att hanteringsprofilen tas bort från **Inställningar**-menyn. När enhetsregistreringen är klar går det inte att ändra inställningen utan att göra en fabriksåterställning av enheten. Sådana enheter måste ha hanteringsläget **Övervakad** inställt på *Ja*. 

8. Om du vill låta flera användare logga in på registrerade iPad-enheter med hjälp av ett hanterat Apple-ID, väljer du **Ja** under **Delad iPad**. Det här kräver att lägena **Registrera utan användartillhörighet** och **Övervakat** är inställda på **Ja**.) Hanterade Apple-ID:n skapas i Apple School Manager-portalen. Mer information om [delad iPad](education-settings-configure-ios-shared.md). Du bör också granska [Apples krav för delad iPad](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56).

9. Välj om du vill att enheter som använder den här profilen ska kunna **Synkronisera med datorer**. Om du väljer **Tillåt Apple Configurator efter certifikat** måste du välja ett certifikat under **Apple Configurator-certifikat**.

10. Om du väljer **Tillåt Apple Configurator efter certifikat** i föregående steg, väljer du ett Apple Configurator-certifikat att importera.

11. Välj **OK**.

12. Välj **Inställningar för inställningsassistenten** för att konfigurera följande profilinställningar: ![Anpassning av inställningsassistenten.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    |                 Inställningen                  |                                                                                               Description                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>Avdelningsnamn</strong>     |                                                             Visas när användare trycker på <strong>Om konfiguration</strong> vid aktiveringen.                                                              |
    |    <strong>Avdelningens telefonnummer</strong>     |                                                          Visas när användaren klickar på knappen <strong>Behöver hjälp</strong> vid aktiveringen.                                                          |
    | <strong>Alternativ för installationsassistenten</strong> |                                                     Följande valfria inställningar kan ställas in senare i iOS <strong>Inställningar</strong>-menyn.                                                      |
    |        <strong>Lösenord</strong>         | Fråga efter lösenord under aktiveringen. Kräv alltid ett lösenord om inte enheten är skyddad eller åtkomstkontrolleras på något annat sätt (t.ex. helskärmsläge som begränsar enheten till en app). |
    |    <strong>Platstjänster</strong>    |                                                                 Om den här funktionen är aktiverad frågar installationsassistenten efter tjänsten under aktivering.                                                                  |
    |         <strong>Återställa</strong>         |                                                                Om den här funktionen är aktiverad frågar Installationsassistenten om iCloud-säkerhetskopiering vid aktivering.                                                                 |
    |   <strong>iCloud och Apple-ID</strong>   |                         Om det här alternativet är aktiverat, ber installationsassistenten användaren att logga in med ett Apple-ID och skärmen Appar och Data låter enheten återställas från iCloud-säkerhetskopiering.                         |
    |  <strong>Villkor</strong>   |                                                   Om det här alternativet är aktiverat, ber installationsassistenten användare att godkänna Apples villkor vid aktiveringen.                                                   |
    |        <strong>Touch ID</strong>         |                                                                 Om det här alternativet är aktiverat, frågar installationsassistenten efter den här tjänsten under aktivering.                                                                 |
    |        <strong>Apple Pay</strong>        |                                                                 Om det här alternativet är aktiverat, frågar installationsassistenten efter den här tjänsten under aktivering.                                                                 |
    |          <strong>Zoom</strong>           |                                                                 Om det här alternativet är aktiverat, frågar installationsassistenten efter den här tjänsten under aktivering.                                                                 |
    |          <strong>Siri</strong>           |                                                                 Om det här alternativet är aktiverat, frågar installationsassistenten efter den här tjänsten under aktivering.                                                                 |
    |     <strong>Diagnostikdata</strong>     |                                                                 Om det här alternativet är aktiverat, frågar installationsassistenten efter den här tjänsten under aktivering.                                                                 |


13. Välj **OK**.

14. Spara profilen genom att välja **Skapa**.

## <a name="connect-school-data-sync"></a>Ansluta School Data Sync
(Valfritt) Apple School Manager stöder synkronisering av klasslistdata till Azure Active Directory (AD) med hjälp av Microsoft SDS (School Data Sync). Du kan bara synkronisera en token med SDS. Om du ställer in en annan token med School Data Sync (SDS), kommer SDS att tas bort från den token som tidigare hade det. En ny anslutning ersätter den aktuella token. Utför följande steg om du vill använda SDS till att synkronisera skolans data.

1. I [Intune](https://aka.ms/intuneportal), väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens**.
2. Välj en Apple School Manager-token och välj sedan **School Data Sync**.
3. Under **School Data Sync**, väljer du **Tillåt**. Den här inställningen innebär att Intune kan ansluta till SDS i Office 365.
4. För att aktivera en anslutning mellan Apple School Manager och Azure AD väljer du **Ställ in Microsoft School Data Sync**. Lär dig mer om [hur du ställer in School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
5. Klicka på **Spara** > **OK**.

## <a name="sync-managed-devices"></a>Synkronisera hanterade enheter

Nu när Intune har tilldelats behörighet att hantera Apple School Manager-enheterna kan du synkronisera Intune med Apple-tjänsten och se dina hanterade enheter i Intune.

I [Intune](https://aka.ms/intuneportal), väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > välj en token i listan > **Enheter** > **Synkronisera**. ![Skärmbild där noden Registreringsprogramenheter har valts och länkvärde håller på att väljas.](./media/device-enrollment-program-enroll-ios/image06.png)

  För att följa Apples villkor för godkänd registreringsprogramtrafik tillämpar Intune följande begränsningar:
  - En fullständig synkronisering kan inte köras oftare än en gång var sjunde dag. Vid en fullständig synkronisering uppdateras Intune med alla Apple-serienummer som tilldelats till Intune. Om du försöker köra en fullständig synkronisering inom sju dagar efter den föregående fullständiga synkroniseringen uppdaterar Intune endast serienummer som inte redan visas i Intune.
  - Varje synkroniseringsbegäran har 15 minuter på sig att slutföras. Under den här tiden, eller tills begäran slutförts, är knappen **Synkronisera** inaktiverad.
  - Intune synkroniserar nya och borttagna enheter med Apple var 24:e timme.

>[!NOTE]
>Du kan också tilldela Apple School Manager-serienummer till profiler från bladet **Registreringsprogramenheter**.

## <a name="assign-a-profile-to-devices"></a>Tilldela en profil till enheter
Apple School Manager-enheter som hanteras av Intune måste tilldelas en registreringsprogramprofil innan de registreras.

1. I [Intune](https://aka.ms/intuneportal), väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > välj en token i listan.
2. Välj **Enheter** > välj enheter i listan > **Tilldela profil**.
3. Under **Tilldela profil**, väljer du en profil för enheterna och sedan **Tilldela**.

## <a name="distribute-devices-to-users"></a>Distribuera enheter till användare

Du har aktiverat hantering och synkronisering mellan Apple och Intune och har tilldelat en profil så att dina Apple School-enheter kan registreras. Du kan nu distribuera enheter till användare. När en Apple School Manager-enhet i iOS aktiveras kommer den att registreras för hantering av Intune. Om enheten har aktiverats och används kan profilen inte användas förrän enheten har fabriksåterställts.
