---
title: Separat inläsning av appar för Windows och Windows Phone
titleSuffix: Microsoft Intune
description: Lär dig hur du signerar verksamhetsspecifika appar, så att du kan använda Intune för att distribuera dem.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 09/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7500000f8a34120e69c27ce01a6cfdb85f447abe
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414705"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Signera verksamhetsspecifika appar så att de kan distribueras till Windows-enheter med Intune

Som Intune-administratör kan du distribuera verksamhetsspecifika (LOB) universella appar till Windows 8.1 Desktop- eller Windows 10 Desktop- och Mobile-enheter, inklusive appen Företagsportal. Om du vill distribuera .appx-appar till Windows 8.1 Desktop- eller Windows 10 Desktop- och Mobile-enheter kan du använda kodsigneringscertifikat från en offentlig certifikatutfärdare som redan är betrodd av dina Windows-enheter, eller så kan du använda din egen certifikatutfärdare.

 > [!NOTE]
 > Windows 8.1 Desktop kräver en företagsprincip för att möjliggöra separat inläsning eller användningen av nycklar för separat inläsning (automatiskt aktiverade för domänanslutna enheter). Mer information finns i inlägget om [separat inläsning i Windows 8.1](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/).

## <a name="windows-10-sideloading"></a>Separat Windows 10-inläsning

I Windows 10 fungerar separat inläsning annorlunda än i tidigare versioner av Windows:

- Du kan låsa upp en enhet för separat inläsning med hjälp av en företagsprincip. Intune tillhandahåller en enhetskonfigurationsprincip som kallas "Installation av betrodd app". Inställningen <allow> är allt som krävs för enheter som redan litar på certifikatet som används för att signera appx-appen.

- Symantec Phone-certifikat och licensnycklar för separat inläsning krävs inte. Men om en lokal certifikatutfärdare inte är tillgänglig kan du behöva hämta ett kodsigneringscertifikat från en offentlig certifikatutfärdare. Mer information finns i [Introduktion till kodsignering](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing).

### <a name="code-sign-your-app"></a>Kodsignera appen

Det första steget är att kodsignera ditt appx-paket. Mer information finns i [Signera appaket med SignTool](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool).

### <a name="upload-your-app"></a>Ladda upp appen

Sedan måste du ladda upp den signerade appx-filen. Mer information finns i [Lägga till en verksamhetsspecifik Windows-app i Microsoft Intune](lob-apps-windows.md).

Om du distribuerar appen efter behov till användare eller enheter behöver du inte appen Intune-företagsportal. Men om du distribuerar appen som den är tillgänglig för användarna kan de använda appen Företagsportal från offentliga Microsoft Store, använda appen Företagsportal via det privata Microsoft Store för företag, eller så måste du signera och manuellt distribuera appen Intune-företagsportal.

### <a name="upload-the-code-signing-certificate"></a>Ladda upp kodsigneringscertifikatet

Om din Windows 10-enhet inte redan litar på certifikatutfärdaren måste du, efter att du har signerat ditt appx-paket och laddat upp det till Intune-tjänsten, ladda upp kodsigneringscertifikatet till Intune-portalen:

1. Klicka på Klientappar
2. Klicka på Windows företagscertifikat
3. Välj ”Välj en fil” under kodsigneringscertifikat
4. Välj din .cer-fil och klicka på ladda upp

Nu laddar automatiskt alla Windows 10 Desktop- och Mobile-enheter med en appx-distribution av Intune-tjänsten ned motsvarande företagscertifikat och appen tillåts att starta efter installation.

Intune distribuerar bara den senaste .cer-filen som har laddats upp. Om du flera appx-filer som skapats av olika utvecklare som inte är associerade med din organisation måste du be dem att tillhandahålla osignerade appx-filer för signering med ditt certifikat eller ge dem kodsigneringscertifikatet som används av din organisation.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Så här förnyar du Symantec-företagscertifikatet för kodsignering

Certifikatet som används till att distribuera Windows Phone 8.1-mobilappar upphörde den 28 februari 2019 och är inte längre tillgänglig för förnyelse från Symantec. Om du distribuerar till WIndows 10 Mobile kan du fortsätta använda Symantec Desktop Enterprise-kodsigneringscertifikat genom att följa [Windows 10-instruktionerna för separat inläsning](app-sideload-windows.md#windows-10-sideloading).

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Hur du installerar det uppdaterade certifikatet för verksamhetsspecifika (LOB) appar

Windows Phone 8.1

Intune-tjänsten kan inte längre distribuera LOB-appar för den här plattformen när det befintliga Symantec Mobile Enterprise-kodsigneringscertifikatet upphör. Det går fortfarande att använda separat inläsning för osignerade XAP-/APPX-filer genom att använda ett SD-kort eller genom att ladda ned filen till enheten. Mer information finns i inlägget om [hur du installerar XAP-filer på Windows Phone](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280).

Windows 8.1 Desktop/Windows 10 Desktop och Mobile

Om certifikatperioden har upphört kanske appx-filerna slutar att starta. Du bör skaffa en ny .cer-fil och följa instruktionerna för att kodsignera varje distribuerad appx-fil och ladda upp alla appx-filer och den uppdaterade .cer-filen på nytt till avsnittet för Windows Enterprise-certifikat i Intune-portalen

## <a name="manually-deploy-windows-10-company-portal-app"></a>Distribuera Windows 10-företagsportalsappen

Om du inte vill ge åtkomst till Microsoft Store kan du distribuera Windows 10 företagsportalappen manuellt direkt från Intune, även om du inte har integrerat Intune med Microsoft Store för företag. Alternativt, om du har integrerat, kan du distribuera appen Företagsportal med hjälp av [distribuera appar med Microsoft Store för företag](store-apps-windows.md).

 > [!NOTE]
 > Det här alternativet kräver att du distribuerar manuella uppdateringar varje gång som en appuppdatering släpps.

1. Logga in på kontot i [Microsoft Store för företag](https://www.microsoft.com/business-store) och hämta **offline-licensversionen** av appen Företagsportal.  
2. När du har införskaffat appen markerar du den på sidan **Inventering**.  
3. Välj **Windows 10 – alla enheter** som **plattform**, sedan lämplig **arkitektur** och ladda ned. Det behövs inte någon applicensfil för den här appen.
   ![Bild av Windows 10 X86-paketinformation för nedladdning](./media/app-sideload-windows/Win10CP-all-devices.png)
4. Hämta alla paket under Nödvändiga ramverk. Detta måste göras för x86-, x64- och ARM-arkitekturer – vilket ger totalt 9 paket så som visas nedan.

   ![Bild av beroendefiler att hämta ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. Innan du skickar företagsportalappen till Intune så skapa en mapp (t.ex. C:\Company Portal) med paketen strukturerade på följande sätt:
   1. Placera företagsportalspaketet i C:\Company Portal. Skapa även en undermapp för beroenden på den här platsen.  
      ![Bild av beroendemappen sparad med APPXBUN-filen](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. Placera de nio beroendepaketen i mappen Dependencies.  
      Om beroendena inte placeras i det här formatet kommer Intune inte att kunna känna igen och överföra dem under paketöverföringen, vilket innebär att överföringen kommer att misslyckas med följande fel.  
      ![Felmeddelande – Windows-appberoendet måste anges.](./media/app-sideload-windows/Win10CP-error-message.png)
6. Gå tillbaka till Intune och överför företagsportalsappen som en ny app. Distribuera den som en obligatorisk app för den önskade uppsättningen målanvändare.  

Mer information om hur Intune hanterar beroenden för universella appar finns i [Distribuera ett appxbundle med beroenden via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Hur uppdaterar jag företagsportalen på mina användaress enheter om de redan har installerat de äldre apparna?

Om användarna redan har installerat företagsportalsapparna för Windows 8.1 eller Windows Phone 8.1 från Store, så borde de sedan uppdateras automatiskt till den nya versionen, utan att det krävs några åtgärder från dig eller användaren. Om uppdateringen inte genomförs, så be dina användare att kontrollera om de har aktiverat automatiska uppdateringar för Store-appar på sina enheter.

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hur uppgraderar jag min separat inlästa företagsportalsapp för Windows 8.1 till företagsportalsappen för Windows 10?

Våra rekommenderade migreringssökväg är att ta bort distributionen för Windows 8.1-företagsportalappen genom att ange distributionsåtgärden till Avinstallera. När detta är gjort kan du distribuera företagsportalappen för Windows 10 distribueras med hjälp av något av ovanstående alternativ.  

Om du behöver läsa in appen separat och distribuera Windows 8.1-företagsportalsappen utan signera den med Symantec-certifikatet, så slutför uppgraderingen genom att följa stegen i avsnittet Distribuera direkt via Intune ovan.

Om du behöver läsa in appen separat och du har signerat och distribuerat företagsportalen för Windows 8.1 med Symantec-kodsigneringscertifikat, så följ stegen i avsnittet nedan.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hur uppgraderar jag min signerade och separat inlästa företagsportalsapp för Windows Phone 8.1 eller Windows 8.1 till företagsportalsappen för Windows 10?

Våra rekommenderade migreringssökväg är att ta bort den befintliga distributionen av företagsportalsappen för Windows 8.1 Phone eller Windows 8.1 genom att ange distributionsåtgärden till Avinstallera. När detta är gjort kan du distribuera företagsportalappen för Windows 10 distribueras normalt.  

I annat fall måste företagsportalappen för Windows 10 uppdateras på rätt sätt och signeras så att uppgraderingsvägen följs.  

Om Windows 10-företagsportalappen signeras och distribueras på det här sättet måste du upprepa proceduren för varje ny appuppdatering när den är tillgänglig i lagret. Appen uppdateras inte automatiskt när lagret uppdateras.  

Så här registrerar och distribuerar du appen:

1. Ladda ner signeringsskriptet för Microsoft Intune Windows 10-företagsportalappen på [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Det här skriptet kräver att Windows SDK för Windows 10 har installerats på värddatorn. Ladda ner Windows SDK för Windows 10 genom att gå till [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Hämta Windows 10-företagsportalappen från Microsoft Store för företag så som beskrivs ovan.  
3. Kör skriptet med de indataparametrar som beskrivs i skripthuvudet, så att Windows 10-företagsportalsappen signeras (se utdrag nedan). Beroenden behöver inte överföras till skriptet. Detta krävs enbart om appen överförs till Intune-aministratörskonsolen.

|       Parameter       |                                                                    Beskrivning                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             Sökvägen till platsen där appxbundle-källfilen finns.                                              |
| OutputWin10AppxBundle |                                                  Sökvägen för utdata för den signerade appxbundle-filen.                                                  |
|       Win81Appx       |                          Sökvägen till den plats där företagsportalsappen för Windows 8.1 eller Windows Phone 8.1 (. APPX) finns.                           |
|      PfxFilePath      |                                   Sökvägen till filen för Symantec Enterprise Mobile Code Signing Certificate (.PFX).                                    |
|      PfxPassword      |                                     Lösenordet för Symantec Enterprise Mobile Code Signing Certificate.                                      |
|      PublisherId      |      Företagets publicerings-ID. Om det ej finns, används ämnes-fältet i Symantec-certifikatet med mobil kodsignering för företag.       |
|        SdkPath        | Sökvägen till rotkatalogen på Windows SDK för Windows 10. Det här argumentet är valfritt och är som standard ${env:ProgramFiles(x86)}\Windows Kits\10 |

Skriptets utdata är den signerade versioneb av företagsportalsappen för Windows 10. Du kan sedan distribuera den signerade versionen av appen som en LOB-app via Intune, som kommer att uppgraderas till de för tillfället distribuerade versionerna av den nya appen.  
