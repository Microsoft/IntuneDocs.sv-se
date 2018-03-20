---
title: "Lägga till företagsportalappen för Windows 10 manuellt"
titleSuffix: Microsoft Intune
description: "Läs om hur du lägger till företagsportalappen för Windows 10 manuellt."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06ed9395d06e2d64edcedcaadfe819ad03f1d495
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="manually-add-the-windows-10-company-portal-app-using-microsoft-intune"></a>Lägg till företagsportalappen för Windows 10 manuellt med Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Slutanvändarna kan installera företagsportalappen från Microsoft Store för att hantera enheter och installera appar. Om företaget i stället kräver att du tilldelar företagsportalappen kan du tilldela företagsportalappen för Windows 10 manuellt direkt från Intune, även om du inte har integrerat Intune med Microsoft Store för företag.

 > [!NOTE]
 > Det här alternativet kräver att du tilldelar manuella uppdateringar varje gång som en appuppdatering släpps.

## <a name="configure-settings-to-show-offline-apps"></a>Konfigurera inställningar för att visa offlineappar
1. Gå till [Microsoft Store för företag](https://www.microsoft.com/business-store) och kontrollera att du är inloggad med ditt administratörskonto.
2. Välj fliken **Hantera** i fönstrets överkant.
3. Välj **Inställningar** i den vänstra kolumnen.
4. Ställ in **Visa offlineappar** i avsnittet om **shoppingupplevelsen** till **På**. Med det här alternativet visas licensierade offlineappar i Microsoft Store för företag.

## <a name="download-the-offline-company-portal-app"></a>Ladda ner företagsportalens offlineapp
1. Sök och markera appen **Företagsportal**.
2. Ange **Licenstyp** till **Offline**.
3. Klicka på **Hämta appen** för att hämta och lägga till offlineappen från företagsportalen i inventeringen.
4. Klicka på **Hantera** på appsidan **Företagsportal**.
5. Välj först **Windows 10 – Alla enheter** som **Plattform** och sedan lämplig **Minimiversion**, **Arkitektur** och Ladda ned värden för appmetadata**. 
6. Klicka på **Ladda ned** för att spara filen på din lokala dator.

    ![Bild av Windows 10 – Alla enheter och information om X86-arkitekturpaketet som ska laddas ned](./media/Win10CP-all-devices.png)

7. Hämta alla paket under Nödvändiga ramverk. Detta måste göras för x86-, x64- och ARM-arkitekturer – vilket ger totalt 12 paket.
8. Innan du laddar upp företagsportalappen till Intune, skapar du en mapp (t.ex. C:&#92;Företagsportal) med paketen strukturerade på följande sätt:
  - Placera företagsportalspaketet i C:\Company Portal. Skapa även en undermapp för beroenden på den här platsen.  

    ![Bild av beroendemappen sparad med APPXBUN-filen](./media/Win10CP-Dependencies-save.png)

  - Placera beroendepaketen i mappen *Beroenden*. 

     > [!NOTE]
     > Om beroendena inte placeras i rätt format kommer Intune inte känna igen och ladda upp dem under paketuppladdningen, vilket innebär att uppladdningen kommer att misslyckas och visa ett felmeddelande.

9. Återgå till Microsoft Intune i Azure-portalen.
10. Ladda upp företagsportalappen som en ny app. Tilldela den som en obligatorisk app för den önskade uppsättningen målanvändare.  

Mer information om hur Intune hanterar beroenden för universella appar finns i [Distribuera ett appxbundle med beroenden via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/).  

## <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Hur uppdaterar jag företagsportalen på mina användaress enheter om de redan har installerat de äldre apparna?
Om användarna redan har installerat företagsportalsapparna för Windows 8.1 eller Windows Phone 8.1 från Store, så borde de sedan uppdateras automatiskt till den nya versionen, utan att det krävs några åtgärder från dig eller användaren. Om uppdateringen inte genomförs, så be dina användare att kontrollera om de har aktiverat automatiska uppdateringar för Store-appar på sina enheter.   

## <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hur uppgraderar jag min separat inlästa företagsportalsapp för Windows 8.1 till företagsportalsappen för Windows 10?
Vår rekommenderade migreringssökväg är att ta bort tilldelningen för företagsportalappen för Windows 8.1 genom att ange tilldelningsåtgärden till ”Avinstallera”. När den här inställningen har gjorts kan du tilldela företagsportalappen för Windows 10 med hjälp av något av ovanstående alternativ.  

Om du behöver läsa in appen separat och tilldela företagsportalsappen för Windows 8.1 utan att signera den med Symantec-certifikatet, så slutförs uppgraderingen genom att följa stegen i avsnittet Tilldela direkt via Intune ovan.

Om du behöver läsa in appen separat och du har signerat och tilldelat företagsportalen för Windows 8.1 med Symantec-kodsigneringscertifikat ska du följa stegen i avsnittet nedan.  

## <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hur uppgraderar jag min signerade och separat inlästa företagsportalsapp för Windows Phone 8.1 eller Windows 8.1 till företagsportalsappen för Windows 10?
Vår rekommenderade migreringssökväg är att ta bort den befintliga tilldelningen av företagsportalsappen för Windows 8.1 Phone eller Windows 8.1 genom att ange tilldelningsåtgärden till Avinstallera. När den här inställningen har gjorts kan du tilldela företagsportalappen för Windows 10 på vanligt vis.  

I annat fall måste företagsportalappen för Windows 10 uppdateras på rätt sätt och signeras så att uppgraderingsvägen följs.  

Om företagsportalappen för Windows 10 signeras och tilldelas på det här sättet måste du upprepa proceduren för varje ny appuppdatering när den är tillgänglig i lagret. Appen uppdateras inte automatiskt när lagret uppdateras.  

Så här registrerar och tilldelar du appen:

1. Hämta signeringsskriptet för Microsoft Intune Windows 10-företagsportalappen på [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Det här skriptet kräver att Windows SDK för Windows 10 har installerats på värddatorn. Du kan hämta Windows-SDK:n för Windows 10 på [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Hämta Windows 10-företagsportalappen från Microsoft Store för företag så som beskrivs ovan.  
3. Kör skriptet med de indataparametrar som beskrivs i skripthuvudet, så att Windows 10-företagsportalsappen signeras (se utdrag nedan). Beroenden behöver inte överföras till skriptet. Detta krävs enbart om appen överförs till Intune-aministratörskonsolen.

|Parameter | Beskrivning|
| ------------- | ------------- |
|InputWin10AppxBundle |Sökvägen till platsen där appxbundle-källfilen finns |
|OutputWin10AppxBundle |Sökvägen för utdata för den signerade appxbundle-filen.  Win81Appx – Sökvägen till den plats där företagsportalsappen för Windows 8.1 eller Windows Phone 8.1 (. APPX) finns.|
|PfxFilePath |Sökvägen till filen för Symantec Enterprise Mobile Code Signing Certificate (.PFX). |
|PfxPassword| Lösenordet för Symantec Enterprise Mobile Code Signing Certificate. |
|PublisherId |Företagets publicerings-ID. Om det ej finns, används ämnes-fältet i Symantec-certifikatet med mobil kodsignering för företag.|
|SdkPath | Sökvägen till rotkatalogen på Windows SDK för Windows 10. Det här argumentet är valfritt och är som standard ${env:ProgramFiles(x86)}\Windows Kits\10|
Skriptets utdata är den signerade versioneb av företagsportalsappen för Windows 10. Du kan sedan tilldela den signerade versionen av appen som en LOB-app via Intune, som kommer att uppgraderas till de för tillfället tilldelade versionerna av den nya appen.  

## <a name="next-steps"></a>Nästa steg

- [Så här tilldelar du appar till grupper](apps-deploy.md)

