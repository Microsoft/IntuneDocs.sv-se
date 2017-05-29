---
title: "Felsöka klientinstallationen | Microsoft Docs"
description: "Felsök vanliga problem med klientinstallationen."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e46d292b-1d16-46db-a87f-d53eefa4d22a
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: a6724f4dcf9d1c6001ba1e87e87ae31ccc2ab0da
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="troubleshoot-client-setup-in-microsoft-intune"></a>Felsöka klientinstallationen i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Använd följande information för att felsöka vanliga problem med klientinstallationen. Om du inte lyckas lösa problemet med hjälp av den här informationen läser du [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md), som beskriver hur du kan få hjälp på fler sätt.

## <a name="client-installation-fails"></a>Klientinstallationen misslyckas

-   Om inga meddelanden om distributionen av klientprogramvaran för datorn visas i [Microsoft Intune Administrationskonsol](https://manage.microsoft.com/) kontrollerar du datorns Internetanslutning och proxykonfiguration och kontrollerar att datorn kan kommunicera med tjänstens webbadress, [https://manage.microsoft.com](https://manage.microsoft.com/). Pröva sedan att installera klientprogramvaran igen.

-   Du kan ange att ett e-postmeddelande ska skickas till valda mottagare om distributionen av klientprogramvaran misslyckas genom att konfigurera en aviseringsregel på arbetsytan **Admin** . Mer information finns i [Håll dig informerad med aviseringar från Microsoft Intune](/intune-classic/deploy-use/get-notified-by-alerts).

-   Den viktiga aviseringen **Distributionen av klientprogramvaran misslyckades** visas i Intune om det inte går att distribuera klientprogramvaran. Meddelandet visas på sidan **Systemöversikt** och **Aviseringar** i [Microsoft Intune Administrationskonsol](https://manage.microsoft.com/). Så här letar du efter aviseringar:

1.  Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) och välj **Aviseringar** &gt; **Översikt**.

2.  På sidan **Översikt över aviseringar** kan du granska följande information:

    -   De tre översta aviseringarna kan sorteras efter datum, kategori eller allvarlighetsgrad

    -   Det totala antalet aktiva aviseringar

3.  Klicka på **Alla aviseringar** så visas följande information på sidan **Aviseringar** . Viktiga aviseringar visas först:

    -   **Namn** – namnet på den aviseringstyp som skapade aviseringen.

    -   **Källa** – en länk till aviseringens källa.  Om tröskelvärdet för visning av aviseringstypen är inställt på **Alla**visar den här länken en enda berörd enhet.  Om tröskelvärdet för visning av aviseringstypen är inställt på ett värde visar den här länken en lista över alla enheter som påverkas av aviseringen.

    -   **Senast uppdaterad** – detta anger den tidpunkt då aviseringen senast ändrades. Om en avisering är stängd visas den tid då aviseringen stängdes.

    -   **Allvarlighetsgrad** – anger aviseringens allvarlighetsgrad

## <a name="computer-enrollment-package-doesnt-download"></a>Det går inte att ladda ned datorregistreringspaketet
**Problem:** Följande händer när du försöker registrera en dator:
-  Det går inte att hämta registreringspaketet
-  Hämtningsdialogrutan visas men tidsgränsen går ut

**Lösning:** I webbläsaren som du använder för nedladdningen kontrollerar du, för den tid då nedladdningen sker, att nedladdningar är aktiverat och att krypterade filer kan sparas på din lokala disk.

## <a name="client-installation-hangs-with-error-code-0x80040154"></a>Klientinstallationen låser sig med felkoden 0x80040154
**Problem:**

-  Klientinstallationen låser sig under registreringen

-  Det går inte att registrera enheten

-  Fel 0x80040154 i WindowsUpdate.log

Detta kan bero på att viktiga programuppdateringar saknas på datorn.

**Lösning:** Kontrollera att din princip för programuppdateringar aktiverar installationen av viktiga uppdateringar. Mer information finns i [Hålla Windows-datorer uppdaterade med programvaruuppdateringar i Microsoft Intune](/intune-classic/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)


## <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Principrelaterade Microsoft Intune-fel i policyplatform.log
För icke-MDM Windows-enheter kan principfel i filen policyplatform.log bero på att andra inställningar än standardinställningarna används i Windows User Account Control (UAC) på enheten. Andra inställningar än UAC-standardinställningarna kan påverka Microsoft Intune-klientinstallationer och principkörning.

### <a name="to-resolve-uac-issues"></a>Så här löser du problem i UAC

1.  Dra tillbaka datorn genom att följa anvisningarna i [Återkalla data och enheter från hantering i Microsoft Intune](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management).

2.  Vänta 20 minuter tills klientprogrammet har tagits bort.

    > [!NOTE]
    > Försök inte att ta bort klienten från Program och funktioner.

3.  Skriv **UAC** på startmenyn för att öppna inställningarna för User Account Control.

4.  Dra meddelandereglaget till standardinställningen.

## <a name="what-to-do-if-the-client-will-not-uninstall-from-the-microsoft-intune-administrator-console"></a>Vad du gör om klienten inte avinstalleras från Microsoft Intune-administratörskonsolen

### <a name="to-remove-the-client-software-by-using-the-microsoft-intune-command-line-tool"></a>Så här tar du bort klientprogramvaran med hjälp av kommandoradsverktyget för Microsoft Intune

1.  Öppna en kommandotolk i administratörsläge.

2.  Gå till mappen *%programfiles%\Microsoft\OnlineManagement\Common*

3.  Kör följande kommando ``ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune``

## <a name="client-installation-error-codes"></a>Felkoder för klientinstallationer
I följande tabell beskrivs felkoder som visas under **Aviseringar** om installationen av klientprogramvaran misslyckas. Den innehåller förslag på hur du kan lösa problemet som representeras av respektive felkod.

|Felkod|Möjligt problem|Föreslagen lösning|
|--------------|--------------------|------------------------|
|**0x80CF0437**|Klockan på klientdatorn är inte inställd på rätt tid.|Kontrollera att klockan och tidszonen på klientdatorn är inställda på rätt tid och tidszon.|
|**0x80240438**, **0x80CF0438**, **0x80CF401B**|Det går inte att ansluta till Intune-tjänsten. Kontrollera klientens proxyinställningar.|Kontrollera att proxykonfigurationen på klientdatorn stöds av Intune och att klientdatorn har Internetanslutning. Mer information om proxykonfigurationer som stöds finns i [Skydda Windows-datorer med Endpoint Protection för Microsoft Intune](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|
|**0x80CF402C**|Det går inte att ansluta till Intune-tjänsten. Kontrollera nätverksanslutningen.|Kontrollera att datorn är ansluten till nätverket. Kontrollera att nätverkskabeln är ansluten eller att det trådlösa nätverket är på.|
|**0x80240438, 0x80CF0438**|Proxyinställningarna i Internet Explorer och Lokalt system har inte konfigurerats.|Kontrollera klientens proxyinställningar och bekräfta att proxykonfigurationen på klientdatorn stöds av Intune och att klientdatorn har Internetanslutning. Mer information om proxykonfigurationer som stöds finns i [Skydda Windows-datorer med Endpoint Protection för Microsoft Intune](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|
|**0x80043001**|Registreringspaketet är inaktuellt.|Hämta och installera det aktuella klientprogramvarupaketet från arbetsytan **Admin** . Mer information finns i avsnittet [Installera Windows PC-klienten med Microsoft Intune](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune).|
|**0x80043004**|Prenumerationen finns inte eller är inaktiverad.|Kontrollera att ditt konto och din prenumeration på Intune fortfarande är aktiva. Om du vill visa inställningarna för ditt konto loggar du in på kontot i [administrationscenter för Office 365](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043002**|Kontot är i underhållsläge.|Du kan inte registrera nya klientdatorer när kontot är i underhållsläge. Om du vill visa inställningarna för ditt konto loggar du in på kontot i [administrationscenter för Office 365](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043003**|Kontot har tagits bort.|Kontrollera att ditt konto och din prenumeration på Intune fortfarande är aktiva. Logga in på ditt konto för att visa dina kontoinställningar.|
|**0x80043005**|Klientdatorn är inaktiverad.|Vänta några timmar, ta bort alla äldre versioner av klientprogramvaran på datorn och pröva sedan att installera klientprogramvaran igen. Mer information finns i **Vad du gör om klienten inte avinstalleras från Microsoft Intune-administratörskonsolen** ovan.|
|**0x80043006**|Det högsta antalet tillåtna platser för kontot har nåtts.|Din organisation måste köpa fler platser innan du kan registrera fler klientdatorer i tjänsten.|
|**0x80043007**|Det gick inte att hitta certifikatfilen i samma mapp som installationsprogrammet.|Extrahera alla filer innan du påbörjar installationen. Byt inte namn på eller flytta någon av de hämtade filerna: alla filer måste finnas i samma mapp annars misslyckas installationen. Mer information finns i [Installera Windows PC-klienten med Microsoft Intune](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune).|
|**0x8024D015**, **0x00240005**, **0x80070BC2**, **0x80070BC9**, **0x80CFD015**|Det går inte att installera programvaran eftersom klientdatorn väntar på att startas om.|Starta om datorn och pröva sedan att installera klientprogramvaran igen.|
|**0x80070032**|Ett eller flera installationskrav för klientprogramvaran kunde inte bekräftas på klientdatorn.|Kontrollera att alla nödvändiga uppdateringar är installerade på klientdatorn och pröva sedan att installera klientprogramvaran igen. Mer information om installationskraven för klientprogramvaran finns i [Krav på nätverksinfrastruktur för Microsoft Intune](/intune-classic/get-started/network-infrastructure-requirements-for-microsoft-intune).|
|**0x80043008**|Det gick inte att starta tjänsten Microsoft Online Management Updates.|Kontakta supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).|
|**0x80043009**|Klientdatorn har redan registrerats i tjänsten.|Du måste inaktivera klientdatorn innan du kan registrera den igen i tjänsten. Instruktioner finns i [Dra tillbaka enheter från Microsoft Intune-hanteringen](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management).|
|**0x8004300A**|(Steg 21) Felet uppstår när registreringspaketet distribueras till grupprincipobjektet som ska installeras i användaromfånget och inte datoromfånget. |Kontrollera att grupprincipobjektet har rätt inriktning via GPSI i datoromfånget. Inlägg om det här ämnet finns i [TechNet-forumet](https://social.technet.microsoft.com/Forums/en-US/bb9fa71c-c132-4954-abb0-70be8acbd925/failed-to-install-windows-intune?forum=microsoftintuneprod).|
|**0x8004300B**|Det går inte att köra installationspaketet för klientprogramvaran eftersom den version av Windows som körs på klienten inte stöds.|Intune stöder inte den version av Windows som körs på klientdatorn. En lista över operativsystem som stöds finns i [Krav på nätverksinfrastruktur för Microsoft Intune](/intune-classic/get-started/network-infrastructure-requirements-for-microsoft-intune).|
|**0xAB2**|Windows Installer kunde inte komma åt VBScript-körtiden för en anpassad åtgärd.|Det här felet beror på en anpassad åtgärd som baseras på DLL:er (Dynamic-Link Libraries). När du felsöker DLL-filen kan du behöva använda de verktyg som beskrivs i [Microsoft Support-artikeln KB198038: Användbara verktyg för paket- och distributionsproblem](http://go.microsoft.com/fwlink/?LinkID=234255).|
|**0x8004300f**|Programvaran kan inte installeras eftersom System Center Configuration Manager-klienten redan är installerad.|Ta bort Configuration Manager-klienten och pröva sedan att installera klientprogramvaran igen.|
|**0x80043010**|Programvaran kan inte installeras eftersom OMADM-klienten (Open Mobile Alliance Device Management) redan är installerad.|Ta bort OMADM-klienten och pröva sedan att installera klientprogramvaran igen.|
Om installationsproblemen kvarstår kontaktar du supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md). Ha loggen för registreringen av klientdatorn (finns i %*programfiles*%\Microsoft\OnlineManagement\Logs\Enrollment.log och %*användarprofil*%\AppData\Local\Microsoft\OnlineManagement\Logs\Enrollement.log) och Windows Update-loggen (%*windir*%\windowsupdate.log) till hands när du kontaktar supporten.

## <a name="what-to-do-if-endpoint-protection-is-not-uninstalled-when-you-uninstall-the-client"></a>Vad ska du göra om Endpoint Protection inte har avinstallerats när du avinstallerar klienten?

Ibland kan värdskyddsagenten (Endpoint Protection) finnas kvar efter att du har kört kommandona ovan. I så fall kan du köra kommandot från en upphöjd kommandotolk:

    ```
    "C:\Program Files\Managed Defender\Setup.exe" /x /q /s
    ```


### <a name="next-steps"></a>Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

