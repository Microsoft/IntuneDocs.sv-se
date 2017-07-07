---
title: "Lägga till Windows Store-appar i Intune"
titleSuffix: Intune on Azure
description: "Läs hur man lägger till Windows Store-appar i Intune.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7ad1156076f0ec34d5ac110e32a19a8332c8f863
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-add-windows-store-apps-to-microsoft-intune"></a>Så här lägger du till Windows Store-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Hantera appar** på **Intune**-bladet.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. Välj **Appinformation** på bladet **Lägg till app**.
7. Konfigurera följande information på bladet **Redigera app**. När du är klar klickar du på **Lägg till**. Beroende på vilken app du har valt kan det hända att några av värdena i det här bladet har fyllts i automatiskt:
    - **Appnamn** – Ange namnet på appen så som det ska visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Appbeskrivning** – Ange en beskrivning för appen. Detta visas för användare i företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **App Store-URL** – Ange App Store-URL:en för den app som du vill skapa.
    - **Minsta operativsystem** – Välj den minsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Kategori (valfritt)** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användare i företagsportalen.
    - **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användare i företagsportalen.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Ladda upp ikon** – Överför en ikon som ska kopplas till appen. Den här ikonen visas med appen när användare söker i företagsportalen.
8. När du är klar väljer du **Spara** på bladet **Lägg till app**.

Den app som du har skapat visas i listan över appar där du kan välja att tilldela den till olika grupper. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

## <a name="manually-assign-windows-10-company-portal-app"></a>Tilldela företagsportalsappen för Windows 10 manuellt
Slutanvändarna kan installera företagsportalappen från Windows Store för att hantera enheter och installera appar. Om företaget i stället kräver att du tilldelar företagsportalappen kan du tilldela företagsportalappen för Windows 10 manuellt direkt från Intune, även om du inte har integrerat Intune med Windows Store för företag.

 > [!NOTE]
 > Det här alternativet kräver att du tilldelar manuella uppdateringar varje gång som en appuppdatering släpps.

1. Logga in på kontot i [Windows Store för företag](https://www.microsoft.com/business-store) och hämta **offline-licensversionen** av företagsportalsappen.  
2. När du har införskaffat appen markerar du den på sidan **Inventering**.  
3. Välj **Windows 10 – alla enheter** som **plattform**, sedan lämplig **arkitektur** och ladda ned. Det behövs inte någon applicensfil för den här appen.
![Bild av Windows 10 – alla enheter och information om Architecture X86-paketet för hämtning](./media/Win10CP-all-devices.png)
4. Hämta alla paket under Nödvändiga ramverk. Detta måste göras för x86-, x64- och ARM-arkitekturer – vilket ger totalt 9 paket så som visas nedan.

![Bild av beroendefiler att hämta ](./media/Win10CP-dependent-files.png)
5. Innan du skickar företagsportalappen till Intune så skapa en mapp (t.ex. C:\Company Portal) med paketen strukturerade på följande sätt:
  1. Placera företagsportalspaketet i C:\Company Portal. Skapa även en undermapp för beroenden på den här platsen.  
  ![Bild av beroendemappen sparad med APPXBUN-filen](./media/Win10CP-Dependencies-save.png)
  2. Placera de nio beroendepaketen i mappen Dependencies.  
  Om beroendena inte placeras i det här formatet kommer Intune inte att kunna känna igen och överföra dem under paketöverföringen, vilket innebär att överföringen kommer att misslyckas med följande fel.  
  ![Det gick inte att hitta Windows-appberoendet för den här programinstallationen i programmappen. Du kan fortsätta att skapa och tilldela det här programmet, men det kan inte köras förrän de saknade Windows-appberoendena har tillhandahållits.](./media/Win10CP-error-message.png)
6. Gå tillbaka till Intune och överför företagsportalsappen som en ny app. Tilldela den som en obligatorisk app för den önskade uppsättningen målanvändare.  

Mer information om hur Intune hanterar beroenden för universella appar finns i [Distribuera ett appxbundle med beroenden via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Hur uppdaterar jag företagsportalen på mina användaress enheter om de redan har installerat de äldre apparna?
Om användarna redan har installerat företagsportalsapparna för Windows 8.1 eller Windows Phone 8.1 från Store, så borde de sedan uppdateras automatiskt till den nya versionen, utan att det krävs några åtgärder från dig eller användaren. Om uppdateringen inte genomförs, så be dina användare att kontrollera om de har aktiverat automatiska uppdateringar för Store-appar på sina enheter.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hur uppgraderar jag min separat inlästa företagsportalsapp för Windows 8.1 till företagsportalsappen för Windows 10?
Vår rekommenderade migreringssökväg är att ta bort tilldelningen för företagsportalappen för Windows 8.1 genom att ange tilldelningsåtgärden till Avinstallera. När detta är gjort kan du tilldela företagsportalappen för Windows 10 med hjälp av något av ovanstående alternativ.  

Om du behöver läsa in appen separat och tilldela företagsportalsappen för Windows 8.1 utan att signera den med Symantec-certifikatet, så slutförs uppgraderingen genom att följa stegen i avsnittet Tilldela direkt via Intune ovan.

Om du behöver läsa in appen separat och du har signerat och tilldelat företagsportalen för Windows 8.1 med Symantec-kodsigneringscertifikat ska du följa stegen i avsnittet nedan.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hur uppgraderar jag min signerade och separat inlästa företagsportalsapp för Windows Phone 8.1 eller Windows 8.1 till företagsportalsappen för Windows 10?
Vår rekommenderade migreringssökväg är att ta bort den befintliga tilldelningen av företagsportalsappen för Windows 8.1 Phone eller Windows 8.1 genom att ange tilldelningsåtgärden till Avinstallera. När detta är gjort kan du tilldela företagsportalappen för Windows 10 normalt.  

I annat fall måste företagsportalappen för Windows 10 uppdateras på rätt sätt och signeras så att uppgraderingsvägen följs.  

Om företagsportalappen för Windows 10 signeras och tilldelas på det här sättet måste du upprepa proceduren för varje ny appuppdatering när den är tillgänglig i lagret. Appen uppdateras inte automatiskt när lagret uppdateras.  

Så här registrerar och tilldelar du appen:

1. Hämta signeringsskriptet för Microsoft Intune Windows 10-företagsportalappen på [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Det här skriptet kräver att Windows SDK för Windows 10 har installerats på värddatorn. Du kan hämta Windows-SDK:n för Windows 10 på [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Hämta Windows 10-företagsportalsappen från Windows Store för företag så som beskrivs ovan.  
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
