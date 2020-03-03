---
title: Lägga till företagsportalappen för Windows 10 manuellt
titleSuffix: Microsoft Intune
description: Lär dig hur personalen manuellt kan lägga till företagsportalappen för Windows 10 i sina datorer från Microsoft Store.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c2083d6f259b62b2856e08fec5ebcb696cbc0df
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576444"
---
# <a name="add-the-windows-10-company-portal-app-by-using-microsoft-intune"></a>Lägga till appen Företagsportal för Windows 10 med Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Användarna kan själva installera appen Företagsportal från Microsoft Store för att hantera enheter och installera appar. Om företaget kräver att du i stället tilldelar dem appen Företagsportal kan du tilldela Företagsportal för Windows 10 direkt från Intune. Det kan du göra även om du inte har integrerat Intune med Microsoft Store för företag.

 > [!IMPORTANT]
 > Om du laddar ned appen Företagsportal kräver alternativet som beskrivs i den här artikeln att du tilldelar manuella uppdateringar varje gång det släpps en appuppdatering. Om du vill distribuera appen Företagsportal för Windows 10 Autopilot-enheter kan du läsa [Lägga till appen Företagsportal för Windows 10 Autopilot-enheter](~/apps/store-apps-company-portal-autopilot.md).

## <a name="configure-settings-to-show-offline-apps"></a>Konfigurera inställningar för att visa offlineappar
1. Logga in på [Microsoft Store för företag](https://www.microsoft.com/business-store) med ditt administratörskonto.
2. Välj fliken **Hantera** i fönstrets överkant.
3. Välj **Inställningar** i rutan till vänster.
4. Ställ in **Visa offlineappar** i avsnittet om **shoppingupplevelsen** till **På**.  
    Offlinelicensierade appar visas.

## <a name="download-the-offline-company-portal-app"></a>Ladda ner företagsportalens offlineapp
1. Sök och välj appen **Företagsportal**.
2. Ange **Licenstyp** till **Offline**.
3. Välj **Hämta appen** för att hämta och lägga till offlineappen Företagsportal i inventeringen.
4. Välj **Hantera** på appsidan **Företagsportal**.
5. Välj **Windows 10 – Alla enheter** för **Plattform** och sedan lämpliga värden för **Minimiversion**, **Arkitektur** och **Ladda ned värden för appmetadata**. 
6. Välj **Ladda ned** under **paketinformation** för att spara filen på din lokala dator.

    ![Windows 10-enheter, där arkitekturen är lika med X86, har valts](./media/app-sideload-windows/Win10CP-all-devices.png)

7. Hämta alla paket under Nödvändiga ramverk genom att välja **Ladda ned**.  

    Den här åtgärden måste slutföras för x86-, x64- och ARM-arkitekturer:<br> 
    *Det finns 9 nödvändiga ramverkspaket när du väljer 1507 som lägsta version av operativsystemet, 12 paket när du väljer 1511 och 15 paket när du väljer 1607.*

8. Ladda upp appen Företagsportal som en ny app i Microsoft Intune i Azure Portal. Du lägger till programmet genom att välja Branschspecifik app som **Apptyp** i fönstret **Välj apptyp**. Välj sedan appaketfilen (tillägget .Appxbundle).

9. Under **Välj beroende appfiler** väljer du alla beroenden som du laddade ner i steg 7 genom att använda shift+klick. Kontrollera att kolumnen **Tillagda** visar **Ja** för alla arkitekturer som du behöver.

     > [!NOTE]
     > Om beroendena inte läggs till kanske appen inte installeras på de angivna enhetstyperna.

10. Klicka på **Ok**, ange önskad **Appinformation** och klicka på **Add**.

11. Tilldela företagsportalen som en obligatorisk app till dina valda användargrupper eller enhetsgrupper.  

Mer information om hur Intune hanterar beroenden för universella appar finns i [Distribuera ett appxbundle med beroenden via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/).  

## <a name="frequently-asked-questions"></a>Vanliga frågor och svar 
### <a name="how-do-i-update-the-company-portal-app-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Hur gör jag för att uppdatera appen Företagsportal på mina användares enheter om de redan har installerat de äldre apparna?
Om användarna redan har installerat Företagsportal för Windows 8.1 eller Windows Phone 8.1 från Microsoft Store, så borde de uppdateras automatiskt till den nya versionen utan att det krävs några åtgärder från dig eller användaren. Om uppdateringen inte genomförs, så be dina användare att kontrollera att de har aktiverat automatiska uppdateringar för Store-appar på sina enheter.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hur uppgraderar jag min separat inlästa företagsportalsapp för Windows 8.1 till företagsportalsappen för Windows 10?
Vår rekommenderade migreringssökväg är att ta bort tilldelningen för appen Företagsportal för Windows 8.1 genom att ange tilldelningsåtgärden till **Avinstallera**. När du har valt den här inställningen kan du tilldela appen Företagsportal för Windows 10 med alla de alternativ som vi nämnt tidigare.  

Om du behöver läsa in appen separat och om du tilldelade appen Företagsportal för Windows 8.1 utan att signera den med Symantec-certifikatet, slutför du uppgraderingen genom att följa stegen i de tidigare avsnitten i den här artikeln.

Om du behöver läsa in appen separat och du har signerat och tilldelat företagsportalappen för Windows 8.1 med Symantec-kodsigneringscertifikat följer du stegen i nästa avsnitt.

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hur uppgraderar jag min signerade och separat inlästa företagsportalsapp för Windows Phone 8.1 eller Windows 8.1 till företagsportalsappen för Windows 10?
Vår rekommenderade migreringssökväg är att ta bort den befintliga tilldelningen av appen Företagsportal för Windows Phone 8.1 eller Windows 8.1 genom att ange tilldelningsåtgärden till **Avinstallera**. När du har valt den här inställningen kan du tilldela appen Företagsportal för Windows 10 som vanligt.  

I annat fall måste appen Företagsportal för Windows 10 uppdateras på rätt sätt och signeras så att uppgraderingsvägen följs.  

Om du signerar och tilldelar appen Företagsportal för Windows 10 på det här sättet måste du upprepa proceduren för varje ny appuppdatering när den är tillgänglig i Store. Appen uppdateras inte automatiskt när Microsoft Store uppdateras.  

Så här registrerar och tilldelar du appen:

1. Ladda ner [signeringsskriptet för Microsoft Intune Windows 10-företagsportalappen](https://aka.ms/win10cpscript).  
    Det här skriptet kräver att Windows SDK för Windows 10 har installerats på värddatorn. [Ladda ned Windows SDK för Windows 10](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Ladda ned appen Företagsportal för Windows 10 från Microsoft Store för företag enligt tidigare beskrivning.  
3. Signera appen Företagsportal för Windows 10 genom att köra skriptet med de indataparametrar som beskrivs i skripthuvudet, enligt tabellen nedan.  
    Beroenden behöver inte överföras till skriptet. De krävs endast om appen ska laddas upp till administratörskonsolen för Intune.

| Parameter |  Beskrivning  |
|---|---|
| InputWin10AppxBundle  |  Sökvägen till appxbundle-källfilen. |
| OutputWin10AppxBundle | Sökvägen för utdata för den signerade appxbundle-filen. 
| Win81Appx  | Sökvägen till .APPX-filen för Företagsportal för Windows 8.1 eller Windows Phone 8.1. |
| PfxFilePath  |  Sökvägen till .PFX-filen för Symantec Enterprise Mobile Code Signing Certificate.  |
| PfxPassword  | Lösenordet för Symantec Enterprise Mobile Code Signing Certificate. |
| PublisherId | Företagets publicerings-ID. Om detta saknas, används ämnesfältet i Symantec-certifikatet med mobil kodsignering för företag. |
| SdkPath | Sökvägen till rotkatalogen på Windows SDK för Windows 10. Det här argumentet är valfritt och är som standard ${env:ProgramFiles(x86)}\Windows Kits\10.  |

När skriptet har körts skapas den signerade versionen av appen Företagsportal för Windows 10. Du kan sedan tilldela den signerade versionen av appen som en LOB-app (Line of Business) via Intune, som uppgraderar till de tilldelade versionerna till den här nya appen.  

## <a name="next-steps"></a>Nästa steg

- [Tilldela appar till grupper](apps-deploy.md)

