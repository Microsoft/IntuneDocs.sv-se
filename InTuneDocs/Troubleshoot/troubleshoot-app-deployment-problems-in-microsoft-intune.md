---
title: "Felsöka problem med appdistributionen | Microsoft Intune"
description: "Det här avsnittet innehåller information om hur du löser problem med appdistributionen i Microsoft Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5256d4decfcd14de2d50a32a0906b6894639010
ms.openlocfilehash: 552514971a64b16f88a7d83a0f7d66a0c00b61b0


---

# Felsöka problem med appdistributionen i Microsoft Intune
Börja här om du har problem med att distribuera och hantera appar med Intune. Det här avsnittet innehåller några vanliga problem du kan stöta på samt lösningar på problemen.

## Vanliga felkoder för appdistribution

|Felkod|Möjligt problem|Föreslagen lösning|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (klientfel)|Om du vill installera den här appen måste du ha ett system där separat inläsning tillåts.|Kontrollera att app-paketet är signerat med en betrodd signatur och installerad på en domänansluten enhet där principen AllowAllTrustedApps är aktiverad, eller en enhet som har en Windows-licens för separat inläsning med principen AllowAllTrustedApps aktiverad (tillämpas när en  Windows RT-enhet registreras).|
|0x80073CF0|Paketet kunde inte öppnas.|Möjliga orsaker:<br /><br />-   Paketet är osignerat.<br />-   Utgivarens namn matchar inte signeringscertifikatets ämne.<br /><br />Mer information finns i AppxPackagingOM-händelseloggen.|
|0x80073CF3|Paketet klarade inte av uppdaterings-, beroende- eller konfliktverifiering|Möjliga orsaker:<br /><br />-   Det inkommande paketet är i konflikt med ett installerat paket.<br />-   Det gick inte att hitta ett angivet paketberoende.<br />-   Paketet stöder inte korrekt processorarkitektur.<br /><br />Mer information finns i AppXDeployment-Server-händelseloggen.|
|0x80073CFB|Det tillhandahållna paketet har redan installerats, och återinstallering av paketet är blockerad|Du kan råka ut för det här felet om du installerar ett paket som inte är identiskt till det paket som redan har installerats. Bekräftelse av den digitala signaturen ingår också i paketet. När ett paket har byggts om eller signerats på nytt så är det inte längre binärt identiskt med det tidigare installerade paketet. De två möjliga alternativ för att åtgärda det här felet är:<br /><br />-   Öka appens versionsnummer och bygg sedan om och signera paketet på nytt.<br />-   Ta bort det gamla paketet för varje användare i systemet innan du installerar det nya paketet.|
|0x87D1041C|Programinstallationen lyckades men programmet identifieras inte.|- Appen har distribuerats av Intune och sedan avinstallerats (troligtvis av slutanvändaren). Be användaren att installera om appen via företagsportalen. De appar som krävs ominstalleras automatiskt nästa gång enheten checkar in.|

### Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md)



<!--HONumber=Sep16_HO1-->


