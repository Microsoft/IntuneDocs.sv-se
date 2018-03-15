---
title: "Använda fabriksåterställning eller ta bort företagsdata på enheter som använder Microsoft Intune"
titlesuffix: 
description: "Läs om hur du kan ta bort företagsdata på en enhet eller fabriksåterställa enheten."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 01/12/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 62404f6ffede7a7f3f7150da1fde289f2ba9e64f
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2018
---
# <a name="remove-devices-by-using-factory-reset-or-remove-company-data"></a>Ta bort enheter med hjälp av fabriksåterställning eller ta bort företagsdata

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Du kan ta bort enheter från Intune som inte längre behövs, som ska få ett nytt syfte eller som har försvunnit. Det kan du göra genom att utfärda ett kommando för att **ta bort företagsdata** eller **fabriksåterställa**. Användare kan dessutom utfärda ett fjärrkommando från Intune-företagsportalen på privatägda enheter som registrerats i Intune.

> [!NOTE]
> Innan du tar bort en användare från Azure Active Directory kan du utfärda ett kommando för **Fabriksåterställning** eller **Ta bort företagsdata** till alla enheter som är kopplade till den användaren. Om du tar bort användare med hanterade enheter från Azure Active Directory kan inte Intune längre utfärda fabriksåterställning eller borttagning av företagsdata till dessa enheter.

## <a name="factory-reset"></a>Fabriksåterställning

**Fabriksåterställning** återställer enheten till fabriksinställningarna och tar bort alla företags- och användarrelaterade data och inställningar. Enheten tas bort från Intune-hantering. En fabriksåterställning är praktisk om du vill återställa en enhet innan du ger den till en ny användare eller om enheten har tappats bort eller blivit stulen. Var försiktig med att välja fabriksåterställning. Det går inte att återställa data på enheten.

### <a name="to-factory-reset-a-device"></a>Fabriksåterställa en enhet

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Alla enheter** på bladet **Enheter**.
4. Välj namnet på den enhet som du vill fabriksåterställa.
5. På bladet som visar enhetens namn väljer du **Fabriksåterställning**.
6. Det finns ytterligare ett alternativ för att ”Behålla registreringstillståndet och användarkontot” för Windows 10 version 1709 eller senare. 
    
    |Behålls efter en fabriksåterställning|Behålls inte|
    | -------------|------------|
    |Användarkonton kopplade till enheten|Användarfiler|
    |Datortillstånd \(domänansluten, ansluten till Azure Active Directory)| Användarinstallerade appar \(store och Win32-appar)|
    |MDM-registrering|Enhetsinställningar som inte är standard|
    |Installerade OEM-appar \(store och Win32-appar)||
    |Användarprofil||
    |Användardata utanför användarprofilen||
    |Automatisk inloggning för användare|| 
    
         
7. Bekräfta fabriksåterställningen genom att klicka på **Ja**.

Om enheten är på och ansluten tar det mindre än 15 minuter att sprida fabriksåterställningen över alla enhetstyper.

## <a name="remove-company-data"></a>Ta bort företagsdata

Kommandot **Ta bort företagsdata** tar bort hanterade appdata (om tillämpligt), inställningar och e-postprofiler som har tilldelats med hjälp av Intune. Med borttagning av företagsdata lämnas användarens personliga data på enheten. Enheten tas bort från Intune-hantering. Följande tabell beskriver vilka data som tas bort och hur data som lämnas kvar på enheten påverkas när företagsdata tas bort.

### <a name="ios"></a>iOS

|Datatyp|iOS|
|-------------|-------|
|Företagsappar och associerade data som installerats av Intune|Apparna avinstalleras. Data som hör till företagsappar tas bort.<br /><br />Appdata från Microsoft-appar som använder mobilapphantering tas bort. Appen tas inte bort.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|
|Certifikatprofilinställningar|Certifikat tas bort och återkallas.|
|Hanteringsagenten|Hanteringsprofilen tas bort.|
|E-post|E-postprofiler som etablerats via Intune tas bort och cachelagrad e-post på enheten tas bort.|
|Outlook|E-postmeddelanden som tagits emot av Microsoft Outlook-appen för iOS tas bort.|
|Frånkoppling från Azure Active Directory (AD)|Azure AD-posten tas bort.|
|Kontakter | Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort.  Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte tas bort. <br /> <br />För närvarande stöds endast Outlook-appen.

### <a name="android"></a>Android

|Datatyp|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Webblänkar|Tas bort.|Tas bort.|
|Google Play-appar som inte hanteras|Appar och data förblir installerade.|Appar och data förblir installerade.|
|Verksamhetsspecifika appar som inte hanteras|Appar och data förblir installerade.|Apparna avinstalleras och data som är lokala för appen tas därmed bort. Inga data utanför appen (till exempel på ett SD-kort) tas bort.|
|Google Play-appar som hanteras|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara men tas inte bort.|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade, men tas inte bort.|
|Verksamhetsspecifika appar som hanteras|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara men tas inte bort.|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara men tas inte bort.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|Tas bort.|
|Certifikatprofilinställningar|Certifikat återkallas, men tas inte bort.|Certifikat tas bort och återkallas.|
|Hanteringsagenten|Behörigheten som enhetsadministratör återkallas.|Behörigheten som enhetsadministratör återkallas.|
|E-post|Ej tillämpligt (e-post profiler stöds inte av Android-enheter)|E-postprofiler som etablerats via Intune tas bort och cachelagrad e-post på enheten tas bort.|
|Outlook|E-post som tagits emot av Microsoft Outlook-appen för Android tas bort, men bara om Outlook skyddas av MAM-principer. I annat fall rensas inte Outlook vid avregistrering.|E-post som tagits emot av Microsoft Outlook-appen för Android tas bort, men bara om Outlook skyddas av MAM-principer. I annat fall rensas inte Outlook vid avregistrering.|
|Frånkoppling från Azure Active Directory (AD)|Azure AD-posten tas bort.|Azure AD-posten tas bort.|
|Kontakter | Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort.  Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte tas bort. <br /> <br />För närvarande stöds endast Outlook-appen.|Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort.  Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte tas bort. <br /> <br />För närvarande stöds endast Outlook-appen.

### <a name="android-for-work"></a>Android for Work

Borttagning av företagsdata på en Android for Work-enhet tar bort alla data, appar och inställningar i arbetsprofilen på den enheten. Detta drar tillbaka enheten från hantering med Intune. Fabriksåterställning stöds inte för Android for Work.


### <a name="macos"></a>macOS

|Datatyp|macOS|
|-------------|-------|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|
|Certifikatprofilinställningar|Certifikat som har distribuerats via MDM tas bort och återkallas.|
|Hanteringsagenten|Hanteringsprofilen tas bort.|
|Outlook|Om villkorlig åtkomst är aktiverad tas ingen e-post emot av enheten.|
|Frånkoppling från Azure Active Directory (AD)|Azure AD-posten tas bort.|

### <a name="windows"></a>Windows

|Datatyp|Windows 8.1 (MDM) och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Företagsappar och associerade data som installerats av Intune|Filer som skyddas av EFS får sin nyckel återkallad och användaren kommer inte att kunna öppna filerna.|Företagsappar tas inte bort.|Appar som ursrpungligen installerats via företagsportalen avinstalleras. Data som hör till företagsappar tas bort.|Apparna avinstalleras och nycklarna för separat inläsning tas bort.<br>För Windows 10 version 1703 (Creator Update) och senare tas inte Office 365 ProPlus-appar bort.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|Tas bort.|Stöds inte.|Tas bort.|
|Certifikatprofilinställningar|Certifikat tas bort och återkallas.|Certifikat tas bort och återkallas.|Stöds inte.|Certifikat tas bort och återkallas.|
|E-post|Tar bort e-post som är EFS-aktiverad (krypterande filsystem), vilket även omfattar e-post och bifogade filer i Mail-appen för Windows.|Stöds inte.|E-postprofiler som etablerats via Intune tas bort och cachelagrad e-post på enheten tas bort.|Tar bort e-post som är EFS-aktiverad (krypterande filsystem), vilket även omfattar e-post och bifogade filer i Mail-appen för Windows. Tar bort e-postkonton som etablerats av Intune.|
|Frånkoppling från Azure Active Directory (AD)|Nej.|Nej.|Azure AD-posten tas bort.|Inte tillämpligt. Windows 10 har inte stöd för att ta bort företagsdata för Azure Active Directory-anslutna enheter.|

### <a name="to-remove-company-data"></a>Ta bort företagsdata

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Alla enheter** på bladet **Enheter**.
4. Välj namnet på den enhet där du vill ta bort företagets data.
5. På bladet som visar enhetens namn väljer du **Ta bort företagsdata** och väljer sedan **Ja** för att bekräfta.

Om enheten är på och ansluten tar det mindre än 15 minuter att sprida kommandot för att ta bort företagsdata över alla enhetstyper.

## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Ta bort enheter från Azure Active Directory-portalen

Till följd av kommunikationsproblem eller enheter som saknas kan du behöva ta bort enheter från Azure Active Directory (AD). Borttagningskommandot tar inte bort någon enhet från hanteringen, men du kan använda **Ta bort** för att ta bort enhetsposter från Azure-portalen som du vet inte går att nå och som sannolikt inte kommer att kommunicera med Azure igen.

1.  Logga in på [Azure Active Directory i Azure-portalen](http://aka.ms/accessaad) med dina autentiseringsuppgifter som administratör. Du kan också logga in på [Office 365-portalen](https://portal.office.com) och sedan välja **Administrationscenter** &gt; **Azure AD** genom att använda länken till vänster på sidan.
3.  Skapa en Azure-prenumeration om du inte redan har en. Detta bör inte kräva ett kreditkort eller en betalning om du har ett konto som kostar pengar (välj prenumerationslänken **Registrera en kostnadsfri Azure Active Directory** ).
4.  Välj **Azure Active Directory** och välj sedan din organisation.
5.  Välj fliken **Användare** .
6.  Välj den användare vars enheter du vill ta bort.
7.  Välj **Enheter**.
8.  Ta bort enheter efter behov, till exempel de som inte längre används eller som har felaktiga definitioner.
