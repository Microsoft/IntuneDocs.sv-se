---
title: "Fullständig eller selektiv rensning på enheter med Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Information om hur du gör en selektiv rensning av företagets data på en enhet eller gör en fullständig rensning för att återställa enheten till fabriksinställningarna."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 22e188e81f2bc278045bb0988642b1b68372d6af
ms.lasthandoff: 02/18/2017


---

# <a name="use-full-or-selective-wipe"></a>Använda fullständig eller selektiv rensning 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Du kan rensa appar och data från Intune-hanterade enheter som inte längre behövs, som ska få ett nytt syfte eller som har försvunnit. Du kan göra detta med funktionerna för fullständig och selektiv rensning i Intune. Användare kan dessutom utfärda ett fjärrensningskommando från Intune-företagsportalappen på privatägda enheter som registrerats i Intune.

  > [!NOTE]
  > Den här artikeln handlar enbart om hur du rensar enheter som hanteras av Intune MDM (hantering av mobilenheter). Du kan också använda [Azure-portalen](https://portal.azure.com) om du vill [rensa företagsdata från appar](https://docs.microsoft.com/intune/deploy-use/wipe-managed-company-app-data-with-microsoft-intune). Du kan också [dra tillbaka datorer som hanteras av Intune-klientprogrammet](https://docs.microsoft.com/intune/deploy-use/retire-a-windows-pc-with-microsoft-intune).

## <a name="full-wipe"></a>Fullständig rensning

**Fullständig rensning** återställer enheten till fabriksinställningarna och tar bort alla företags- och användarrelaterade data och inställningar. Enheten tas bort från Intune. En fullständig rensning är praktisk om du vill återställa en enhet innan du ger den till en ny användare eller om enheten har tappats bort eller blivit stulen.  **Var försiktig med att välja fullständig rensning. Det går inte att återställa data på enheten**.


> [!Warning]
> Windows 10 RTM-enheter (enheter med en tidigare version än Windows 10 version 1511) som har mindre än 4 GB RAM-minne kan bli otillgängliga om de rensas. Om du vill komma åt en Windows 10-enhet som inte svarar kan du starta enheten från en USB-enhet.


**Göra en fullständig rensning (fabriksåterställning) av en enhet**:

1.  På bladet **Enheter och grupper** väljer du **Alla enheter**.

2.  Välj namnet på den enhet som du vill rensa.

3.  På bladet som visar enhetens namn väljer du **Fabriksåterställning** och väljer sedan **Ja** för att bekräfta rensningen.

Om enheten är på och ansluten tar det mindre än 15 minuter att sprida rensningen över alla enhetstyper.

### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>Ta bort enheter i Azure Active Directory-portalen

1.  Bläddra till [http://aka.ms/accessaad](http://aka.ms/accessaad) eller välj **Admin** &gt; **Azure AD** från [https://portal.office.com](https://portal.office.com).

2.  Logga in med ditt organisations-ID med hjälp av länken till vänster på sidan.

3.  Skapa en Azure-prenumeration om du inte har någon. Detta bör inte kräva ett kreditkort eller en betalning om du har ett konto som kostar pengar (välj prenumerationslänken **Registrera en kostnadsfri Azure Active Directory** ).

4.  Välj **Active Directory** och välj sedan din organisation.

5.  Välj fliken **Användare** .

6.  Välj den användare vars enheter du vill ta bort.

7.  Välj **Enheter**.

8.  Ta bort enheter efter behov, till exempel de som inte längre används eller som har felaktiga definitioner.


## <a name="selective-wipe"></a>Selektiv rensning

En **selektiv rensning** tar bort företagsdata, inklusive eventuell mobil apphanteringsdata (MAM), inställningar och e-postprofiler från en enhet. Med en selektiv rensning lämnas användarens personliga data på enheten. Enheten tas bort från Intune. Följande tabell beskriver vilka data som tas bort och hur data som lämnas kvar på enheten påverkas vid en selektiv rensning. (Tabellerna är ordnade efter plattform.)

**iOS**

|Datatyp|iOS|
|-------------|-------|
|Företagsappar och associerade data som installerats av Intune|Apparna avinstalleras. Data som hör till företagsappar tas bort.<br /><br />Appdata från Microsoft-appar som använder mobilapphantering tas bort. Appen tas inte bort.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|
|Certifikatprofilinställningar|Certifikat tas bort och återkallas.|
|Hanteringsagenten|Hanteringsprofilen tas bort.|
|E-post|E-postprofiler som etablerats via Intune tas bort och cachelagrad e-post på enheten tas bort. Om Microsoft Exchange finns lokalt, tas e-postprofiler och cachelagrade e-postmeddelanden inte bort.|
|Outlook|E-postmeddelanden som tagits emot av Microsoft Outlook-appen för iOS tas bort.</br>Undantag: Om Exchange finns lokalt så tas inte e–post bort.|
|Frånkoppling från Azure Active Directory (AAD)|AAD-posten tas bort.|
|Kontakter | Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort.  Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. <br /> <br />För närvarande stöds endast Outlook-appen.

**Android**

|Datatyp|Android|Android Samsung KNOX Standard|
|-------------|-----------|------------------------|
|Webblänkar|Tas bort.|Tas bort.|
|Google Play-appar som inte hanteras|Appar och data förblir installerade.|Appar och data förblir installerade.|
|Branschspecifika appar som inte hanteras|Appar och data förblir installerade.|Apparna avinstalleras och data som är lokala för appen tas därmed bort. Inga data utanför appen (till exempel på ett SD-kort) tas bort.|
|Google Play-appar som hanteras|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara men tas inte bort.|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade, men tas inte bort.|
|Branschspecifika appar som hanteras|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara men tas inte bort.|Appdata tas bort. Appen tas inte bort. Data som skyddas med MAM-kryptering utanför appen (t.ex. ett SD-kort) förblir krypterade och oanvändbara men tas inte bort.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|Tas bort.|
|Certifikatprofilinställningar|Certifikat återkallas, men tas inte bort.|Certifikat tas bort och återkallas.|
|Hanteringsagenten|Behörigheten som enhetsadministratör återkallas.|Behörigheten som enhetsadministratör återkallas.|
|E-post|E-post som tagits emot av Microsoft Outlook-appen för Android tas bort.|E-postprofiler som etablerats via Intune tas bort och cachelagrad e-post på enheten tas bort.|
|Outlook|E-postmeddelanden som tagits emot av Microsoft Outlook-appen för iOS tas bort.</br>Undantag: Om Exchange finns lokalt så tas inte e–post bort.|E-postmeddelanden som tagits emot av Microsoft Outlook-appen för iOS tas bort.</br>Undantag: Om Exchange finns lokalt så tas inte e–post bort.|
|Frånkoppling från Azure Active Directory (AAD)|AAD-posten tas bort.|AAD-posten tas bort.|
|Kontakter | Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort.  Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. <br /> <br />För närvarande stöds endast Outlook-appen.|Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort.  Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. <br /> <br />För närvarande stöds endast Outlook-appen.

**Windows**

|Datatyp|Windows 8.1 (MDM) och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Företagsappar och associerade data som installerats av Intune|Filer som skyddas av EFS får sin nyckel återkallad och användaren kommer inte att kunna öppna filerna.|Företagsappar tas inte bort.|Appar som ursrpungligen installerats via företagsportalen avinstalleras. Data som hör till företagsappar tas bort.|Apparna avinstalleras och nycklarna för separat inläsning tas bort.|
|Inställningar|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|Konfigurationer som ställts in av Intune-principer tillämpas inte längre och användarna kan ändra inställningarna.|
|Profilinställningar för Wi-Fi och VPN|Tas bort.|Tas bort.|Stöds inte.|Tas bort.|
|Certifikatprofilinställningar|Certifikat tas bort och återkallas.|Certifikat tas bort och återkallas.|Stöds inte.|Certifikat tas bort och återkallas.|
|E-post|Tar bort e-post som är EFS-aktiverad (krypterande filsystem), vilket även omfattar e-post och bifogade filer i Mail-appen för Windows.|Stöds inte.|E-postprofiler som etablerats via Intune tas bort och cachelagrad e-post på enheten tas bort.|Tar bort e-post som är EFS-aktiverad (krypterande filsystem), vilket även omfattar e-post och bifogade filer i Mail-appen för Windows. Tar bort e-postkonton som etablerats av Intune.</br>**Undantag**: Om Microsoft Exchange finns lokalt så tas inte e-postkonton bort.|
|Frånkoppling från Azure Active Directory (AAD)|Nej.|Nej.|AAD-posten tas bort.|Inte tillämpligt. Windows 10 har inte stöd för selektiv rensning för Azure Active Directory-anslutna enheter.|

**Göra en selektiv rensning**:

1.  På bladet **Enheter och grupper** väljer du **Alla enheter**.

2.  Välj namnet på den enhet som du vill rensa.

3.  På bladet som visar enhetens namn väljer du **Ta bort föret...** (står för Ta bort företagsdata) och väljer sedan **Ja** för att bekräfta rensningen.

Om enheten är på och ansluten tar det mindre än 15 minuter att sprida rensningen över alla enhetstyper.

