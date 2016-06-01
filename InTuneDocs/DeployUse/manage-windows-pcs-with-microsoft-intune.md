---
# required metadata

title: Hantera Windows-datorer med Intune | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Hantera Windows-datorer med Microsoft Intune
Förutom att registrera enheter kan du använda Intune för att hantera Windows-datorer med operativsystem som stöds med hjälp av Intune-klientprogramvaran för Windows. Maskin- och programvarukraven för att köra datorklienten är minimala – i princip stöds alla datorer som kan köra Windows 7 eller senare.  Klientprogramvaran är också lätt att installera både på domänanslutna datorer (i valfri domän) eller icke-domänanslutna datorer.

Intune hanterar Windows-datorer med hjälp av principer på liknande sätt som AD DS-grupprincipobjekt (Active Directory Domain Services) för Windows Server gör. Om du ska hantera domänanslutna Active Directory-datorer med Intune bör du [försäkra dig om att Intune-principerna inte står i konflikt med grupprincipobjekt](resolve-gpo-and-microsoft-intune-policy-conflicts.md) som används i din organisation.

> [!NOTE]
> Microsoft Intune som fristående tjänst erbjuder dessa funktioner för datorhantering. Enheter som kör Windows 8.1 kan hanteras med Intune-klienten eller registreras som mobila enheter. Informationen nedan gäller för datorer som kör Intune-klienten.

## Krav för datorhantering i Intune

**Maskinvara**:

|Följande är de minsta maskinvarukraven för att installera Intune-klienten:|Krav|
|---------------|--------------------|
|Mer information|Nätverk|
|Klienten kräver att datorn är ansluten till Internet.|Processor och minne|
|Se RAM- och processorkraven för datorns operativsystem.|Diskutrymme|

200 MB ledigt diskutrymme innan klientprogrammet har installerats.

|**Programvara**:|Nedan visas programvarukraven för att installera klienten:|
|---------------|--------------------|
|Krav|Mer information|
|Administrativ behörighet|Det konto som installerar klientprogrammet måste ha lokal administratörsbehörighet på datorn.<br /><br />Windows Installer 3.1<br /><br />Datorn måste minst ha Windows Installer 3.1.<br /><br />Så visar du versionen för Windows Installer på en dator:|
|-   Högerklicka på **%windir%\System32\msiexec.exe** och sedan på **Egenskaper**|Du kan hämta den senaste versionen av Windows Installer från [Windows Installer Redistributables](http://go.microsoft.com/fwlink/?LinkID=234258) på webbplatsen Microsoft Developer Network.|

## Ta bort klientprogram som inte är kompatibla
Innan du installerar Intune-klientprogramvaran måste du avinstallera Configuration Manager- eller System Management Server-klientprogramvara från datorn. Installera Intune-datorklienten

-   Det första steget när du ska hantera Windows-datorer med Intune är att installera klienten. Klientprogramvaran kan installeras när en dator har registrerats för hantering i Intune-tjänsten på något av följande sätt:

    Du kan [distribuera Microsoft Intune-klientprogramvaran manuellt](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software). I den här typen av distribution laddar administratören ned Intune-klientprogramvaran och installerar den manuellt på varje dator.

-   Om du vill ladda ned Intune-klientprogramvaran öppnar du Intune-administrationskonsolen och laddar ned paketet med klientprogramvaran från området Hämta klientprogramvara.

-   När klientprogramvaran har installerats installerar Intune automatiskt ytterligare programvara om det behövs för att hantera datorn. Du kan använda samma filer som du laddar ned för att manuellt installera Intune-klienten om du vill [distribuera klienten till domänanslutna datorer med hjälp av Active Directory-grupprincipobjekt](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy)

-   [Slutanvändare kan självregistrera sina datorer](install-the-windows-pc-client-with-microsoft-intune.md#how-users-can-self-enroll-their-computers) via företagsportalen i Intune.

## Varje registrerad dator länkas sedan automatiskt till det användarkonto som användes för att installera Intunes-klientprogramvaran.
Slutligen kan du även distribuera Intune-klientprogramvaran till datorer som en del av en [operativsystemdistribution](install-the-windows-pc-client-with-microsoft-intune.md#install-the-microsoft-intune-client-software-as-part-of-an-image)

Datorhantering med Intune-datorklienten

-   När Intune-klienten har installerats ger klientprogramvaran tillgång till flera datorhanteringsfunktioner, till exempel: [programhantering](deploy-apps-in-microsoft-intune.md), Endpoint Protection, maskin- och programvaruinventering, fjärrstyrning (via begäran om Fjärrhjälp), programuppdateringar och rapportering av efterlevnadsinställningar.

-   Flera datorhanteringsåtgärder som aktiveras av datorklienten hanteras med Intune-principer som till exempel kan användas för att:

-   Konfigurera [inställningarna för Windows-brandväggen](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) på hanterade datorer.

Konfigurera [inställningar för programuppdatering](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) för hanterade datorer för att söka efter, och ladda ned, nödvändiga programuppdateringar.

-   Skydda hanterade datorer mot potentiella hot och skadlig programvara genom [övervakning i realtid och Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)-hantering.

-   Förutom att vidta åtgärder med Intune-klientagenten lokalt på enskilda datorer kan du utföra andra [vanliga datorhanteringsåtgärder](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) med Intune-administratörskonsolen på Windows-datorer där klienten är installerad:

-   Visa maskin- och programvaruinventering för hanterade datorer

-   Starta om en dator via en fjärranslutning

-   Dra tillbaka en dator för att avinstallera klientprogramvaran och ta bort den från hantering i Intune

Länka användare till specifika hanterade datorer Svara på en begäran om Fjärrhjälp


<!--HONumber=May16_HO2-->


