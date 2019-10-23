---
title: Dra tillbaka eller rensa enheter med hjälp av Microsoft Intune – Azure | Microsoft Docs
description: Dra tillbaka eller rensa en enhet på en enhet med Android, Android-arbetsprofil, iOS, macOS eller Windows med hjälp av Microsoft Intune. Även ta bort en enhet från Azure Active Directory.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbcc50d275a3d3e6a613640e96b363ce7608da81
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508565"
---
# <a name="remove-devices-by-using-wipe-retire-or-manually-unenrolling-the-device"></a>Ta bort enheter genom att rensa, dra tillbaka eller manuellt avregistrera enheten

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Med hjälp av åtgärden **Dra tillbaka** eller **Rensa** kan du ta bort enheter från Intune som inte längre behövs, har omkonfigurerats eller saknas. Användare kan dessutom utfärda ett fjärrkommando från Intune-företagsportalen till enheter som har registrerats i Intune.

> [!NOTE]
> Innan du tar bort en användare från Azure Active Directory (Azure AD) kan du använda åtgärderna **Rensa** eller **Dra tillbaka** för alla enheter som är kopplade till den användaren. Om du tar bort användare som har hanterade enheter från Azure AD kan inte Intune längre rensa eller dra tillbaka dessa enheter.

## <a name="wipe"></a>Rensning

Åtgärden **Rensa** återställer en enhet till standardinställningarna från fabriken. Användardata sparas om du markerar kryssrutan **Behåll registreringstillstånd och användarkonto**. Annars tas personliga data, appar och inställningar bort.

|Åtgärden Rensa|**Behåll registreringstillstånd och användarkonto**|Borttagen från Intune-hanteringen|Beskrivning|
|:-------------:|:------------:|:------------:|------------|
|**Rensning**| Inte markerad | Ja | Rensar alla användarkonton, data, MDM-principer och inställningar. Återställer operativsystemet till dess standardtillstånd och -inställningar.|
|**Rensning**| Markerad | Nej | Rensar alla MDM-principer. Behåller användarkonton och data. Återställer användarinställningar till standard. Återställer operativsystemet till dess standardtillstånd och -inställningar.|


> [!NOTE]
> Åtgärden rensa är inte tillgänglig för iOS-enheter som har registrerats med användarregistrering.

Alternativet **Behåll registreringstillstånd och användarkonto** är endast tillgängligt för Windows 10 version 1709 eller senare.

MDM-principer kommer att tillämpas igen nästa gång enheten ansluter till Intune.

En rensning är praktisk om du vill återställa en enhet innan du ger den till en ny användare eller om enheten har tappats bort eller blivit stulen. Var försiktig med att välja **Rensa**. Det går inte att återställa data på enheten.

### <a name="wiping-a-device"></a>Rensa en enhet

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Enheter** > **Alla enheter**.
4. Välj namnet på den enhet som du vill rensa.
5. I fönstret som visar enhetsnamnet väljer du **Rensa**.
6. För Windows 10 version 1709 eller senare kan du även välja alternativet **Behåll registreringstillstånd och användarkonto**. 
    
    |Behålls under en rensning |Behålls inte|
    | -------------|------------|
    |Användarkonton kopplade till enheten|Användarfiler|
    |Enhetstillstånd \(domänanslutning, Azure AD-anslutning)| Användarinstallerade appar \(store och Win32-appar)|
    |Registrering i hanteringsagent för mobila enheter (MDM)|Enhetsinställningar som inte är standard|
    |Installerade OEM-appar \(store och Win32-appar)||
    |Användarprofil||
    |Användardata utanför användarprofilen||
    |Automatisk inloggning för användare|| 
    
         
7. Bekräfta rensningen genom att välja **Ja**.

Om enheten är på och ansluten sprids åtgärden **Rensa** över alla enhetstyper på mindre än 15 minuter.

## <a name="retire"></a>Pensionera

Åtgärden **Dra tillbaka** tar bort hanterade appdata (om tillämpligt), inställningar och e-postprofiler som har tilldelats med hjälp av Intune. Enheten tas bort från Intune-hantering. Detta sker nästa gång enheten checkar in och tar emot fjärråtgärden **Dra tillbaka**. Enheten visas fortfarande i Intune tills enheten checkar in. Om du vill ta bort inaktuella enheter direkt använder du åtgärden [Ta bort åtgärd](devices-wipe.md#delete-devices-from-the-intune-portal) istället.

**Dra tillbaka** lämnar kvar användarens personliga data på enheten.  

Följande tabeller beskriver vilka data som tas bort och hur åtgärden **Dra tillbaka** påverkar data som lämnas kvar på enheten när företagsdata tas bort.

### <a name="ios"></a>iOS

|Datatyp|iOS|
|-------------|-------|
|Företagsappar och associerade data som installerats av Intune|**Appar som installerats med hjälp av Företagsportalen:** För appar som är fästa på hanteringsprofilen tas alla appdata och appar bort. Dessa appar innehåller appar som ursprungligen installerats från App Store och som senare har hanterats som företagsappar. <br /><br /> **Microsoft-appar som använder mobil apphantering och som installerades från App Store:** För appar som inte hanteras med hjälp av Företagsportalen kommer data från företagsappar som skyddas av MAM-kryptering (Mobile Application Management) i appens lokala lagring att tas bort. Data som skyddas med MAM-kryptering utanför appen förblir krypterade och oanvändbara, men tas inte bort. Personliga appdata och appar tas inte bort.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|
|Certifikatprofilinställningar|Certifikat tas bort och återkallas.|
|Hanteringsagenten|Hanteringsprofilen tas bort.|
|E-post|E-postprofiler som tillhandahålls via Intune tas bort. Cachelagrad e-post på enheten tas bort.|
|Frånkoppling från Azure AD|Azure AD-posten tas bort.|

### <a name="android"></a>Android

|Datatyp|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Webblänkar|Tas bort.|Tas bort.|
|Google Play-appar som inte hanteras|Appar och data förblir installerade. <br /> <br />Data från företagsappar som skyddas av MAM-kryptering (Mobile Application Management) i appens lokala lagring tas bort. Data som skyddas med MAM-kryptering utanför appen förblir krypterade och oanvändbara, men tas inte bort. |Appar och data förblir installerade. <br /> <br />Data från företagsappar som skyddas av MAM-kryptering (Mobile Application Management) i appens lokala lagring tas bort. Data som skyddas med MAM-kryptering utanför appen förblir krypterade och oanvändbara, men tas inte bort.|
|Verksamhetsspecifika appar som inte hanteras|Appar och data förblir installerade.|Apparna avinstalleras och data som är lokala för appen tas bort. Inga data utanför appen (till exempel på ett SD-kort) tas bort.|
|Google Play-appar som hanteras|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering (Hantering av mobila program) utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara, men tas inte bort.|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade, men tas inte bort.|
|Verksamhetsspecifika appar som hanteras|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara, men tas inte bort.|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara, men tas inte bort.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|Tas bort.|
|Certifikatprofilinställningar|Certifikat återkallas, men tas inte bort.|Certifikat tas bort och återkallas.|
|Hanteringsagenten|Behörigheten som enhetsadministratör återkallas.|Behörigheten som enhetsadministratör återkallas.|
|E-post|Ej tillämpligt (e-postprofiler stöds inte av Android-enheter)|E-postprofiler som tillhandahålls via Intune tas bort. Cachelagrad e-post på enheten tas bort.|
|Frånkoppling från Azure AD|Azure AD-posten tas bort.|Azure AD-posten tas bort.|

### <a name="android-work-profile"></a>Android-arbetsprofil

Om du tar bort företagsdata från en Android-arbetsprofilenhet raderas alla data, appar och inställningar i arbetsprofilen på den enheten. Enheten dras tillbaka från hantering med Intune. Rensning stöds inte för Android-arbetsprofiler.

### <a name="android-enterprise-kiosk-devices"></a>Android enterprise-kioskenheter

Du kan endast rensa kioskenheter. Du kan inte dra tillbaka Android-kioskenheter.


### <a name="macos"></a>macOS

|Datatyp|macOS|
|-------------|-------|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|
|Certifikatprofilinställningar|Certifikat som har distribuerats via MDM tas bort och återkallas.|
|Hanteringsagenten|Hanteringsprofilen tas bort.|
|Outlook|Om villkorlig åtkomst är aktiverad tar enheten inte emot ny e-post.|
|Frånkoppling från Azure AD|Azure AD-posten tas bort.|

### <a name="windows"></a>Windows

|Datatyp|Windows 8.1 (MDM) och Windows RT 8.1|Windows RT|Windows Phone 8.1 och Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Företagsappar och associerade data som installerats av Intune|Nycklar återkallas för filer som skyddas av EFS. Användaren kan inte öppna filerna.|Företagsappar tas inte bort.|Appar som ursrpungligen installerats via företagsportalen avinstalleras. Data som hör till företagsappar tas bort.|Apparna avinstalleras. Nycklar för separat inläsning tas bort.<br>För Windows 10 version 1703 (Creator Update) och senare tas inte Office 365 ProPlus-appar bort. Win32-appar som installerats via Intune-hanteringstillägget avinstalleras inte på oregistrerade enheter. Administratörer kan använda tilldelningsundantag för att inte erbjuda Win32-appar till BYOD-enheter.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|Tas bort.|Stöds inte.|Tas bort.|
|Certifikatprofilinställningar|Certifikat tas bort och återkallas.|Certifikat tas bort och återkallas.|Stöds inte.|Certifikat tas bort och återkallas.|
|E-post|Tar bort e-post som är EFS-aktiverad. Detta omfattar e-postmeddelanden och bilagor i e-postprogrammet för Windows.|Stöds inte.|E-postprofiler som tillhandahålls via Intune tas bort. Cachelagrad e-post på enheten tas bort.|Tar bort e-post som är EFS-aktiverad. Detta omfattar e-postmeddelanden och bilagor i e-postprogrammet för Windows. Tar bort e-postkonton som etablerats av Intune.|
|Frånkoppling från Azure AD|Nej.|Nej.|Azure AD-posten tas bort.|Azure AD-posten tas bort.|

> [!NOTE]
> För Windows 10-enheter som ansluter till Azure AD under den första installationen (OOBE) tar kommandot Dra tillbaka bort alla Azure AD-konton från enheten. Följ stegen i [Starta datorn i felsäkert läge](https://support.microsoft.com/en-us/help/12376/windows-10-start-your-pc-in-safe-mode) för att logga in som lokal administratör och återfå åtkomst till användarens lokala data. 

### <a name="retire"></a>Pensionera

1. Logga in på [Intune i Azure Portal](https://aka.ms/intuneportal).
2. Välj **Alla enheter** i fönstret **Enheter**.
3. Välj namnet på den enhet som du vill dra tillbaka.
4. I fönstret som visar enhetsnamnet väljer du **Dra tillbaka**. Välj **Ja** för att bekräfta.

Om enheten är på och ansluten sprids åtgärden **Dra tillbaka** över alla enhetstyper på mindre än 15 minuter.

## <a name="delete-devices-from-the-intune-portal"></a>Ta bort enheter från Intune-portalen

Om du vill ta bort enheter från Intune-portalen kan du ta bort dem från det specifika enhetsfönstret. Nästa gång enheten checkar in tas alla företagets data bort.

1. Logga in på [Intune i Azure Portal](https://aka.ms/intuneportal).
2. Välj **Enheter** > **Alla enheter** > Välj de enheter som du vill ta bort > **Ta bort**.

### <a name="automatically-delete-devices-with-cleanup-rules"></a>Ta bort enheter med rensningsregler automatiskt
Du kan konfigurera Intune så att enheter som är inaktiva, inaktuella eller som inte svarar tas bort automatiskt. Dessa rensningsregler övervakar kontinuerligt dina enheter så att enhetsposterna är uppdaterade. Enheter som tas bort på det här sättet tas bort från Intune-hanteringen.
1. Logga in på [Intune i Azure Portal](https://aka.ms/intuneportal).
2. Välj **Enheter** > **Regler för rensning av enhet** > **Ja**.
3. Ange ett nummer mellan 30 och 270 i rutan **Ta bort enheter som inte har checkats in på många dagar**.
4. Välj **Spara**.



## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Ta bort enheter från Azure Active Directory-portalen

Till följd av kommunikationsproblem eller enheter som saknas kan du behöva ta bort enheter från Azure AD. Du kan använda åtgärden **Ta bort** för att ta bort enhetsposter från Azure-portalen för enheter som du vet inte går att nå och som sannolikt inte kommer att kommunicera med Azure igen. Åtgärden **Ta bort** tar inte bort en enhet från hanteringen.

1. Logga in på [Azure Active Directory i Azure-portalen](https://aka.ms/accessaad) med dina autentiseringsuppgifter som administratör. Du kan också logga in på [Administrationscenter för Microsoft 365](https://admin.microsoft.com). På menyn väljer du **Administrationscenter** > **Azure AD**.
2. Skapa en Azure-prenumeration om du inte redan har en. Detta får inte kräva kreditkort eller betalning om du har ett betalt konto (välj prenumerationslänken **Registrera en kostnadsfri Azure Active Directory**).
3. Välj **Azure Active Directory** och välj sedan din organisation.
4. Välj fliken **Användare** .
5. Välj den användare som är kopplad till den enhet som du vill ta bort.
6. Välj **Enheter**.
7. Ta bort enheter efter behov. Du kan till exempel ta bort enheter som inte längre används eller som har felaktiga definitioner.

## <a name="retire-an-apple-dep-device-from-intune"></a>Dra tillbaka en Apple DEP-enhet från Intune

Följ dessa steg om du vill ta bort en Apples DEP-enhet från hantering av Intune fullständigt:

1. Logga in på [Intune i Azure Portal](https://aka.ms/intuneportal).
2. Välj **Enheter** > **Alla enheter** > välj enheten > **Dra tillbaka**.
![Skärmbild för dra tillbaka](./media/devices-wipe/retire.png)
3. Besök [deploy.apple.com](http://deploy.apple.com) och sök efter enheter med hjälp av serienummer.
4. I menyn **Tilldelad till** väljer du **Otilldelad**.

5. Välj **Tilldela om**.

    ![Skärmbild för Tilldela om Apple](./media/devices-wipe/apple-reassign.png)

## <a name="fresh-start"></a>Börja om på nytt

Gäller för Windows 10-enheter. Läs mer om [Börja om på nytt](device-fresh-start.md).

## <a name="next-steps"></a>Nästa steg

Läs [registreringsalternativen](../enrollment/enrollment-options.md) för information om hur du registrerar om en borttagen enhet.

