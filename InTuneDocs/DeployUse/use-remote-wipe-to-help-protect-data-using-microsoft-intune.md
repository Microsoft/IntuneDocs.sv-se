---
title: "Skydda data med hjälp av fjärrensning | Microsoft Intune"
description: "I Intune finns funktioner för selektiv och fullständig rensning så att du kan ta bort känsliga företagsdata och ta bort åtkomsten till många företagsresurser."
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8519e411-3d48-44eb-9b41-3e4fd6a93112
ms.reviewer: lancecra
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d44a6494bed0758b9768045bd204ea0eb481636
ms.openlocfilehash: 5900894ded0518f731ac76c3eac0332e5a3f6c4b


---

# <a name="help-protect-your-data-with-full-or-selective-wipe-using-microsoft-intune"></a>Skydda data med fullständig eller selektiv rensning med Microsoft Intune
Du kan rensa appar och data från Intune-hanterade enheter som inte längre behövs, som ska få ett nytt syfte eller som har försvunnit. Du kan göra detta med funktionerna för fullständig och selektiv rensning i Intune. Användare kan dessutom utfärda ett fjärrensningskommando från Intune-företagsportalappen på privatägda enheter som registrerats i Intune.

  > [!NOTE]
  > Den här artikeln handlar enbart om hur du rensar enheter som hanteras av Intune MDM (hantering av mobilenheter). Du kan också använda [Azure-portalen](https://portal.azure.com) om du vill [rensa företagsdata från appar](wipe-managed-company-app-data-with-microsoft-intune.md). Du kan också [dra tillbaka datorer som hanteras av Intune-klientprogrammet](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md).

## <a name="full-wipe"></a>Fullständig rensning

**Fullständig rensning** återställer enheten till fabriksinställningarna och tar bort alla företags- och användarrelaterade data och inställningar. Enheten tas bort från Intune. En fullständig rensning är praktisk om du vill återställa en enhet innan du ger den till en ny användare eller om enheten har tappats bort eller blivit stulen.  **Var försiktig med att välja fullständig rensning. Det går inte att återställa data på enheten**.


> [!Warning]
> Windows 10 RTM-enheter (enheter med en tidigare version än Windows 10 version 1511) som har mindre än 4 GB RAM-minne kan bli otillgängliga om de rensas. Om du vill komma åt en Windows 10-enhet som inte svarar kan du starta enheten från en USB-enhet.

### <a name="remotely-wipe-a-device-from-the-intune-administrator-console"></a>Fjärrensa en enhet från Intune-administrationskonsolen

1.  Välj vilka enheter som ska rensas. Du hittar dem antingen efter användare eller enhet.

    -   **Efter användare:**

        1.  Gå till [Intune-administratörskonsolen](https://manage.microsoft.com/) och välj **Grupper** &gt; **Alla användare**.

        2.  Välj namnet på den användare vars mobila enhet du vill rensa. Välj **Visa egenskaper**.

        3.  Öppna sidan **Egenskaper** för användaren, välj **Enheter** och välj sedan namnet på den mobila enhet som du vill rensa. Använd Ctrl + klicka om du vill markera flera enheter.

    -   **Efter enhet:**

        1.  Gå till [Intune-administratörskonsolen](https://manage.microsoft.com/) och välj **Grupper** &gt; **Alla mobila enheter**.

         ![Starta en tillbakadragnings- eller rensningsåtgärd](../media/dev-sa-wipe.png)

        2.  Välj **Enheter** och välj sedan namnet på den mobila enhet som du vill rensa. Använd Ctrl + klicka om du vill markera flera enheter.

2.  Välj **Ta ur bruk/rensa**.

3.  Ett bekräftelsemeddelande visas där du tillfrågas om du vill dra tillbaka enheten.

    -   Om du vill utföra en **selektiv rensning** som bara tar bort företagsappar och företagsdata väljer du **Ja**.

    -   Om du vill utföra en **fullständig rensning** som rensar alla appar och data och återställer enheten till fabriksinställningarna väljer du **Rensa enheten innan den tas ur bruk**. Den här åtgärden gäller för alla plattformar förutom Windows 8.1. **Du inte kan återställa data som tagits bort vid en fullständig rensning**.

Om enheten är på och ansluten tar det mindre än 15 minuter att sprida rensningen över alla enhetstyper.

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
|E-post|E-post som tagits emot av Microsoft Outlook-appen för Android tas bort.|E-postprofiler som etablerats via Intune tas bort och cachelagrad e-post på enheten tas bort. Om Microsoft Exchange finns lokalt, tas e-postprofiler och cachelagrade e-postmeddelanden inte bort.|
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

## <a name="wipe-encryption-file-system-efsenabled-content"></a>Rensa EFS-aktiverat innehåll (Encryption File System)
Selektiv radering av EFS-krypterat innehåll stöds av Windows 8.1 och Windows RT 8.1. Följande gäller för en selektiv radering av EFS-aktiverat innehåll:

-   Endast program och data som skyddas med krypterande filsystem (EFS) som använder samma Internetdomän som Intune-kontot raderas selektivt. Mer information finns i [Selektiv Windows-rensning för hantering av enhetsdata](http://technet.microsoft.com/library/dn486874.aspx).

-   Om några ändringar görs i domänen som är associerade med EFS, kan ändringarna ta upp till 48 timmer innan program och data som använder den nya domänen kan rensas selektivt.

-   Alla domäner som är registrerade i Intune rensas.

De data och program som för närvarande stöds av EFS-selektiv rensning är:

-   E--postprogrammet för Windows

-   Arbetsmappar

-   Filer och mappar som krypterats med EFS. Mer information finns i [Metodtips för krypterande filsystem (EFS)](http://support.microsoft.com/kb/223316).

-   Om organisationen upprätthåller sin identitet i Active Directory, måste verktyget Katalogsynkronisering (DirSync) användas för att synkronisera uppgifter i AAD för att selektiv rensning av EFS ska fungera korrekt.  Mer information om DirSync finns i [Directory Sync Scenario](http://technet.microsoft.com/library/dn441212.aspx) i dokumentationen för Azure Active Directory.

## <a name="monitor-retire-wipe-and-delete-actions"></a>Övervaka återställnings-, rensnings- och borttagningsåtgärder
Så här hämtar du en rapport över enheter som har dragits tillbaka, rensats eller tagits bort:

1.  Gå till [Intune-administratörskonsolen](https://manage.microsoft.com/) och välj **Rapporter** &gt; **Rapporter om enhetshistorik**.

2.  Ange ett start- och slutdatum för rapporten och välj sedan **Visa rapport**.

Den här rapporten visar även vem som utförde åtgärden.

### <a name="see-also"></a>Se även
[Dra tillbaka enheter](retire-devices-from-microsoft-intune-management.md)

[Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx) (Selektiv Windows-rensning för hantering av enhetsdata)



<!--HONumber=Nov16_HO2-->


