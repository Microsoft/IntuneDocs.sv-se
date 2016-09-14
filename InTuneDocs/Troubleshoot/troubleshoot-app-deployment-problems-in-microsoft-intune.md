---
title: "Felsöka problem med appdistributionen | Microsoft Intune"
description: "Det här avsnittet innehåller information om hur du löser problem med appdistributionen i Microsoft Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aa96cf3a1909e3ea2187a3beb0aede3228894504
ms.openlocfilehash: 9f4b91bd523c82665bcac54902b2e8cc9c72ef75


---

# Felsöka problem med appdistributionen i Microsoft Intune
Börja här om du har problem med att distribuera och hantera appar med Intune. Det här avsnittet innehåller några vanliga problem du kan stöta på samt lösningar på problemen.

## Vanliga appdistributionsproblem

### Kontakta IT-informationen saknas i företagsportalen

1.  I Intune-administrationskonsolen väljer du **Admin**&gt;**Företagsportal**

2.  Ange **Kontakta IT** -informationen.

### Om du inte kan se några specifika appar i listan

1.  Se till att du markerar listan över appar för den användare eller enhet för vilken appen har distribuerats.

2.  Kontrollera att enheten uppfyller kraven för appen.

### Om du får ett fel när en app laddas ned

1.  Kontrollera att det inte finns mer än en samtidig nedladdning per användare. Varje enskild användare kan bara ladda ned en app åt gången.

2.  Kontrollera att det inte sker för många samtidiga nedladdningar per konto. Vänta några minuter och försök sedan igen.

3.  Om du får ett internt iOS-meddelande om att det inte går att installera, att installationen har avbrutits eller att du måste göra ett nytt försök, så kan det bero på hög trafik. Vänta några minuter och försök sedan igen.

4.  Om iOS-förloppsindikatorn för appnedladdning visar på slutförd nedladdning men installationen misslyckas, kan det bero på att det är något fel på appfilerna som du tillhandahöll.


### Om appen fastnar i pågående läge under hämtning

1.  När du hämtar en app läggs först metadata till, följt av själva app-paketet. Efter det att metadata har hämtats visas information om att appen håller på att hämtas. Om du ser att dina appar är i "pågående"-tillstånd under en ovanligt lång tid bör du ta bort appen och sedan försöka ladda ned den igen.

2.  Se till att du inte hanterar distributionen av appen medan hämtningen fortfarande pågår.

### Om det inträffar ett fel när du installerar en iOS-app

1.  Kontrollera att din organisations brandvägg tillåter åtkomst till Apples etablerings- och certifieringswebbplatser.

2.  Mer information finns i Dokumentation för Apple-utvecklare.

### Om hanterade appar inte rapporterar installationsstatus

Före Microsoft Intune-tjänstuppdateringen i november 2014 hämtades inte installationsstatusen för hanterade appinstallationer. För enheter som installerade hanterade appar före den här tjänstuppdateringen uppdaterar du varje associerad appdistribution med relevant distributionsåtgärd (till exempel **Tillgänglig installation**). Varje enhet uppdaterar appen under den automatiska kontrollen av tillgängliga appar. Mer information finns i [Uppdatera appar med Microsoft Intune](/intune/deploy-use/update-apps-using-microsoft-intune).

## <a name="BKMK_SoftDistErrorCodes"></a>Felkoder för appdistribution
I följande tabell listas vanliga fel som kan inträffa under Intune-appdistributioner, de sannolika orsakerna och möjliga lösningar som hjälper dig att felsöka dem.

|Felkod|Möjligt problem|Föreslagen lösning|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (klientfel)|Om du vill installera den här appen måste du ha ett system där separat inläsning tillåts.|Kontrollera att app-paketet är signerat med en betrodd signatur och installerad på en domänansluten enhet där principen AllowAllTrustedApps är aktiverad, eller en enhet som har en Windows-licens för separat inläsning med principen AllowAllTrustedApps aktiverad (tillämpas när en  Windows RT-enhet registreras).|
|0x80073CF0|Paketet kunde inte öppnas.|Möjliga orsaker:<br /><br />-   Paketet är osignerat.<br />-   Utgivarens namn matchar inte signeringscertifikatets ämne.<br /><br />Mer information finns i AppxPackagingOM-händelseloggen.|
|0x80073CF3|Paketet klarade inte av uppdaterings-, beroende- eller konfliktverifiering|Möjliga orsaker:<br /><br />-   Det inkommande paketet är i konflikt med ett installerat paket.<br />-   Det gick inte att hitta ett angivet paketberoende.<br />-   Paketet stöder inte korrekt processorarkitektur.<br /><br />Mer information finns i AppXDeployment-Server-händelseloggen.|
|0x80073CFB|Det tillhandahållna paketet har redan installerats, och återinstallering av paketet är blockerad|Du kan råka ut för det här felet om du installerar ett paket som inte är identiskt till det paket som redan har installerats. Bekräftelse av den digitala signaturen ingår också i paketet. När ett paket har byggts om eller signerats på nytt så är det inte längre binärt identiskt med det tidigare installerade paketet. De två möjliga alternativ för att åtgärda det här felet är:<br /><br />-   Öka appens versionsnummer och bygg sedan om och signera paketet på nytt.<br />-   Ta bort det gamla paketet för varje användare i systemet innan du installerar det nya paketet.|
|0x87D1041C|Programinstallationen lyckades men programmet identifieras inte.|- Appen har distribuerats av Intune och sedan avinstallerats (troligtvis av slutanvändaren). Be användaren att installera om appen via företagsportalen. De appar som krävs ominstalleras automatiskt nästa gång enheten checkar in.|

### Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md)



<!--HONumber=Aug16_HO5-->


