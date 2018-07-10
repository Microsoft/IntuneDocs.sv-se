---
title: Ta bort företagsdata på enheter med hjälp av Microsoft Intune – Azure | Microsoft Docs
description: Ta bort företagsdata på en enhet eller utföra en fabriksåterställning på en Android-, Android for work-, iOS-, macOS- eller Windows-enhet med hjälp av Microsoft Intune. Även ta bort en enhet från Azure Active Directory.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5b5eadc4ee23a89624cde9f1246f64aafce0b06c
ms.sourcegitcommit: 3284586d9260a66ce99029b7808e4807f8780d20
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37091735"
---
# <a name="remove-devices-by-using-factory-reset-removing-company-data-or-manually-unenrolling-the-device"></a>Ta bort enheter genom att använda fabriksåterställning, ta bort företagsdata eller manuellt avregistrera enheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Med hjälp av åtgärden **Ta bort företagsdata** eller **Fabriksåterställning** kan du ta bort enheter från Intune som inte längre behövs, har omkonfigurerats eller saknas. Användare kan dessutom utfärda ett fjärrkommando från Intune-företagsportalen till privatägda enheter som har registrerats i Intune.

> [!NOTE]
> Innan du tar bort en användare från Azure Active Directory (Azure AD) kan du använda åtgärderna **Fabriksåterställning** eller **Ta bort företagsdata** för alla enheter som är kopplade till den användaren. Om du tar bort användare som har hanterade enheter från Azure AD kan inte Intune längre utfärda fabriksåterställning eller borttagning av företagsdata för dessa enheter.

## <a name="factory-reset"></a>Fabriksåterställning

Åtgärden **Fabriksåterställning** återställer en enhet till standardinställningarna från fabriken. Informationen sparas eller rensas beroende på om du väljer kryssrutan **Behåll registreringstillstånd och användarkonto** eller inte.

|Åtgärden Fabriksåterställning|**Behåll registreringstillstånd och användarkonto**|Borttagen från Intune-hanteringen|Description|
|:-------------:|:------------:|:------------:|------------|
|**Fabriksåterställning**| Inte markerad | Ja | Rensar alla användarkonton, data, MDM-principer och inställningar. Återställer operativsystemet till dess standardtillstånd och -inställningar.|
|**Fabriksåterställning**| Markerad | Nej | Rensar alla MDM-principer. Behåller användarkonton och data. Återställer användarinställningar till standard. Återställer operativsystemet till dess standardtillstånd och -inställningar.|

Alternativet **Behåll registreringstillstånd och användarkonto** är endast tillgängligt för Windows 10 version 1709 eller senare.

MDM-principer kommer att tillämpas igen nästa gång enheten ansluter till Intune.

En fabriksåterställning är praktisk om du vill återställa en enhet innan du ger den till en ny användare eller om enheten har tappats bort eller blivit stulen. Var försiktig med att välja **Fabriksåterställning**. Det går inte att återställa data på enheten.

### <a name="factory-reset-a-device"></a>Fabriksåterställa en enhet

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enheter** > **Alla enheter**.
4. Välj namnet på den enhet som du vill fabriksåterställa.
5. I fönstret som visar enhetsnamnet väljer du **Fabriksåterställning**.
6. För Windows 10 version 1709 eller senare kan du även välja alternativet **Behåll registreringstillstånd och användarkonto**. 
    
    |Behålls under en fabriksåterställning|Behålls inte|
    | -------------|------------|
    |Användarkonton kopplade till enheten|Användarfiler|
    |Enhetstillstånd \(domänanslutning, Azure AD-anslutning)| Användarinstallerade appar \(store och Win32-appar)|
    |Registrering i hanteringsagent för mobila enheter (MDM)|Enhetsinställningar som inte är standard|
    |Installerade OEM-appar \(store och Win32-appar)||
    |Användarprofil||
    |Användardata utanför användarprofilen||
    |Automatisk inloggning för användare|| 
    
         
7. Bekräfta fabriksåterställningen genom att välja **Ja**.

Om enheten är på och ansluten sprids åtgärden **Fabriksåterställning** över alla enhetstyper på mindre än 15 minuter.

## <a name="remove-company-data"></a>Ta bort företagsdata

Åtgärden **Ta bort företagsdata** tar bort hanterade appdata (om tillämpligt), inställningar och e-postprofiler som har tilldelats med hjälp av Intune. Enheten tas bort från Intune-hantering. Detta sker nästa gång enheten checkar in och tar emot fjärråtgärden **Ta bort företagets data**.

Åtgärden **Ta bort företagsdata** behåller användarens personliga data på enheten.  

Följande tabell beskriver vilka data som tas bort och hur åtgärden **Ta bort företagsdata** påverkar data som lämnas kvar på enheten när företagsdata tas bort.

### <a name="ios"></a>iOS

|Datatyp|iOS|
|-------------|-------|
|Företagsappar och associerade data som installerats av Intune|Apparna avinstalleras. Data som hör till företagsappar tas bort.<br /><br />Appdata från Microsoft-appar som använder mobilapphantering tas bort. Appen tas inte bort.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|
|Certifikatprofilinställningar|Certifikat tas bort och återkallas.|
|Hanteringsagenten|Hanteringsprofilen tas bort.|
|E-post|E-postprofiler som tillhandahålls via Intune tas bort. Cachelagrad e-post på enheten tas bort.|
|Outlook|E-postmeddelanden som tagits emot av Microsoft Outlook-appen för iOS tas bort. För detta krävs att Outlook-mobilappen först distribueras som en obligatorisk app till iOS-användare.|
|Frånkoppling från Azure AD|Azure AD-posten tas bort.|
|Kontakter |Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte tas bort. <br /> <br />För närvarande stöds endast Outlook-appen.

### <a name="android"></a>Android

|Datatyp|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Webblänkar|Tas bort.|Tas bort.|
|Google Play-appar som inte hanteras|Appar och data förblir installerade.|Appar och data förblir installerade.|
|Verksamhetsspecifika appar som inte hanteras|Appar och data förblir installerade.|Apparna avinstalleras och data som är lokala för appen tas bort. Inga data utanför appen (till exempel på ett SD-kort) tas bort.|
|Google Play-appar som hanteras|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering (Hantering av mobila program) utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara, men tas inte bort.|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade, men tas inte bort.|
|Verksamhetsspecifika appar som hanteras|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara, men tas inte bort.|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara, men tas inte bort.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|Tas bort.|
|Certifikatprofilinställningar|Certifikat återkallas, men tas inte bort.|Certifikat tas bort och återkallas.|
|Hanteringsagenten|Behörigheten som enhetsadministratör återkallas.|Behörigheten som enhetsadministratör återkallas.|
|E-post|Ej tillämpligt (e-postprofiler stöds inte av Android-enheter)|E-postprofiler som tillhandahålls via Intune tas bort. Cachelagrad e-post på enheten tas bort.|
|Outlook|E-post som tagits emot av Outlook-appen för Android tas bort, men bara om Outlook skyddas av MAM-principer. Annars rensas inte Outlook när enheten avregistreras.|E-post som tagits emot av Outlook-appen för Android tas bort, men bara om Outlook skyddas av MAM-principer. Annars rensas inte Outlook när enheten avregistreras.|
|Frånkoppling från Azure AD|Azure AD-posten tas bort.|Azure AD-posten tas bort.|
|Kontakter |Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte tas bort. <br /> <br />För närvarande stöds endast Outlook-appen.|Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte tas bort. <br /> <br />För närvarande stöds endast Outlook-appen.

### <a name="android-for-work"></a>Android for Work

Borttagning av företagsdata på en Android for Work-enhet tar bort alla data, appar och inställningar i arbetsprofilen på den enheten. Enheten dras tillbaka från hantering med Intune. Fabriksåterställning stöds inte för Android for Work.


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
|Företagsappar och associerade data som installerats av Intune|Nycklar återkallas för filer som skyddas av EFS. Användaren kan inte öppna filerna.|Företagsappar tas inte bort.|Appar som ursrpungligen installerats via företagsportalen avinstalleras. Data som hör till företagsappar tas bort.|Apparna avinstalleras. Nycklar för separat inläsning tas bort.<br>För Windows 10 version 1703 (Creator Update) och senare tas inte Office 365 ProPlus-appar bort.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre. Användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|Tas bort.|Stöds inte.|Tas bort.|
|Certifikatprofilinställningar|Certifikat tas bort och återkallas.|Certifikat tas bort och återkallas.|Stöds inte.|Certifikat tas bort och återkallas.|
|E-post|Tar bort e-post som är EFS-aktiverad. Detta omfattar e-postmeddelanden och bilagor i e-postprogrammet för Windows.|Stöds inte.|E-postprofiler som tillhandahålls via Intune tas bort. Cachelagrad e-post på enheten tas bort.|Tar bort e-post som är EFS-aktiverad. Detta omfattar e-postmeddelanden och bilagor i e-postprogrammet för Windows. Tar bort e-postkonton som etablerats av Intune.|
|Frånkoppling från Azure AD|Nej.|Nej.|Azure AD-posten tas bort.|Inte tillämpligt. Du kan inte ta bort företagsdata för Azure AD-anslutna enheter i Windows 10.|

### <a name="remove-company-data"></a>Ta bort företagsdata

1. Logga in på [Intune i Azure Portal](https://aka.ms/intuneportal).
2. Välj **Alla enheter** i fönstret **Enheter**.
3. Välj namnet på den enhet där du vill ta bort företagsdata.
4. I fönstret som visar enhetsnamnet väljer du **Ta bort företagsdata**. Välj **Ja** för att bekräfta.

Om enheten är på och ansluten sprids åtgärden **Ta bort företagsdata** över alla enhetstyper på mindre än 15 minuter.

## <a name="delete-devices-from-the-intune-portal"></a>Ta bort enheter från Intune-portalen

Om du vill ta bort enheter från Intune-portalen kan du ta bort dem från det specifika enhetsfönstret. Nästa gång enheten checkar in tas alla företagets data bort.

1. Logga in på [Intune i Azure Portal](https://aka.ms/intuneportal).
2. Välj **Enheter** > **Alla enheter** > Välj de enheter som du vill ta bort > **Ta bort**.

## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Ta bort enheter från Azure Active Directory-portalen

Till följd av kommunikationsproblem eller enheter som saknas kan du behöva ta bort enheter från Azure AD. Du kan använda åtgärden **Ta bort** för att ta bort enhetsposter från Azure-portalen för enheter som du vet inte går att nå och som sannolikt inte kommer att kommunicera med Azure igen. Åtgärden **Ta bort** tar inte bort en enhet från hanteringen.

1.  Logga in på [Azure Active Directory i Azure-portalen](http://aka.ms/accessaad) med dina autentiseringsuppgifter som administratör. Du kan också logga in på [Office 365-portalen](https://portal.office.com). På menyn väljer du **Administrationscenter** > **Azure AD**.
2.  Skapa en Azure-prenumeration om du inte redan har en. Detta får inte kräva kreditkort eller betalning om du har ett betalt konto (välj prenumerationslänken **Registrera en kostnadsfri Azure Active Directory**).
3.  Välj **Azure Active Directory** och välj sedan din organisation.
4.  Välj fliken **Användare** .
5. Välj den användare som är kopplad till den enhet som du vill ta bort.
6.  Välj **Enheter**.
7.  Ta bort enheter efter behov. Du kan till exempel ta bort enheter som inte längre används eller som har felaktiga definitioner.
