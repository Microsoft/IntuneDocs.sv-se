---
title: "Felsöka problem med appdistributionen | Microsoft Docs"
description: "Det här avsnittet innehåller information om hur du löser problem med appdistributionen i Microsoft Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 239371198cbbc01b1345c72b3f887055acd44462
ms.lasthandoff: 12/10/2016


---

# <a name="troubleshoot-app-deployment-problems-in-microsoft-intune"></a>Felsöka problem med appdistributionen i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Börja här om du har problem med att distribuera och hantera appar med Intune. Det här avsnittet innehåller några vanliga problem du kan stöta på samt lösningar på problemen.

## <a name="common-app-deployment-error-codes"></a>Vanliga felkoder för appdistribution

|Felkod|Möjligt problem|Föreslagen lösning|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (klientfel)|Om du vill installera den här appen måste du ha ett system där separat inläsning tillåts.|Kontrollera att app-paketet är signerat med en betrodd signatur och installerad på en domänansluten enhet där principen AllowAllTrustedApps är aktiverad, eller en enhet som har en Windows-licens för separat inläsning med principen AllowAllTrustedApps aktiverad.|
|0x80073CF0|Paketet kunde inte öppnas.|Möjliga orsaker:<br /><br />-   Paketet är osignerat.<br />-   Utgivarens namn matchar inte signeringscertifikatets ämne.<br /><br />Mer information finns i AppxPackagingOM-händelseloggen.|
|0x80073CF3|Paketet klarade inte av uppdaterings-, beroende- eller konfliktverifiering|Möjliga orsaker:<br /><br />-   Det inkommande paketet är i konflikt med ett installerat paket.<br />-   Det gick inte att hitta ett angivet paketberoende.<br />-   Paketet stöder inte korrekt processorarkitektur.<br /><br />Mer information finns i AppXDeployment-Server-händelseloggen.|
|0x80073CFB|Det tillhandahållna paketet har redan installerats, och återinstallering av paketet är blockerad|Du kan råka ut för det här felet om du installerar ett paket som inte är identiskt till det paket som redan har installerats. Bekräftelse av den digitala signaturen ingår också i paketet. När ett paket har byggts om eller signerats på nytt så är det inte längre binärt identiskt med det tidigare installerade paketet. De två möjliga alternativ för att åtgärda det här felet är:<br /><br />-   Öka appens versionsnummer och bygg sedan om och signera paketet på nytt.<br />-   Ta bort det gamla paketet för varje användare i systemet innan du installerar det nya paketet.|
|0x87D1041C|Programinstallationen lyckades men programmet identifieras inte.|- Appen har distribuerats av Intune och sedan avinstallerats (troligtvis av slutanvändaren). Be användaren att installera om appen via företagsportalen. De appar som krävs ominstalleras automatiskt nästa gång enheten checkar in.|

## <a name="troubleshooting-apps-from-the-windows-store"></a>Felsöka appar från Windows Store

Informationen i avsnittet [Troubleshooting packaging, deployment, and query of Windows Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (Felsöka paketering, distribution och frågor för Windows Store-appar) hjälper dig att felsöka vanliga problem som kan uppstå när du installerar appar från Windows Store, oavsett om du gör det med Intune eller på annat sätt.

## <a name="troubleshooting-app-deployment-to-pcs-managed-by-the-intune-software-client"></a>Felsöka distribution av appar till datorer som hanteras av Intune-klientprogrammet
För att hjälpa dig att felsöka problem med att distribuera appar till datorer som hanteras av Intune-klientprogrammet kan du se följande två loggfiler:
- %ProgramFiles%\Microsoft\OnlineManagement\Logs folder
- %ProgramFiles%\Microsoft\OnlineManagement\Updates\ReportingEvents.log

Vidare, om du behöver öppna ett supportärende för Intune hjälper det att även skicka dessa loggar till Microsoft.


### <a name="next-steps"></a>Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md)

