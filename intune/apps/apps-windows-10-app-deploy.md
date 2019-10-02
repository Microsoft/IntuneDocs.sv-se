---
title: Windows 10-appdistribution med hjälp av Microsoft Intune
titleSuffix: ''
description: Läs mer om de scenarier för Windows 10-appdistribution som är tillgängliga med Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c853608f46bb01263ddd08193f729cdfb018fed9
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724977"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>Windows 10-appdistribution med hjälp av Microsoft Intune 

Microsoft Intune har för närvarande stöd för en mängd olika typer av appar och distributionsscenarier på Windows 10-enheter. När du har lagt till en app till Intune kan du tilldela appen till användare och enheter. Följande information innehåller mer detaljer om de Windows 10-scenarier som stöds. Dessutom innehåller följande information viktiga punkter att tänka på när du distribuerar appar till Windows. 

Verksamhetsspecifika appar (LOB) och Microsoft Store för företag-appar är de typer av appar som stöds på Windows 10-enheter. Filnamnstillägg för Windows-appar omfattar **.msi**, **.appx** och **.appxbundle**.  

> [!Note]
> De minsta nödvändiga Windows 10-uppdateringarna för att distribuera moderna appar är följande:
> - För Windows 10 1803, [23 maj 2018 – KB4100403 (OS-version 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403).
> - För Windows 10 1709 [21 juni 2018 – KB4284822 (OS-version 16299.522)](https://support.microsoft.com/help/4284822).
>
> Endast Windows 10 1803 och senare har stöd för installation av appar när det inte finns någon primär användare associerad.

## <a name="windows-10-line-of-business-apps"></a>Verksamhetsspecifika Windows 10-appar

Verksamhetsspecifika Windows 10-appar signeras och laddas upp till Intune-administratörskonsolen och kan innefatta både moderna appar, till exempel Universal Windows Platform-appar (UWP) och Windows-appaket (AppX), och Win 32-appar såsom enkla Microsoft Installer-paketfiler (MSI). Uppdateringar av verksamhetsspecifika appar måste laddas upp och distribueras manuellt varje gång av administratören. Uppdateringar som distribueras installeras automatiskt på slutanvändarenheter med appen installerad utan åtgärd från användaren. Användaren har ingen kontroll över uppdateringarna. 

## <a name="microsoft-store-for-business-apps"></a>Microsoft Store för företag-appar

Microsoft Store för företag-appar är moderna appar som har köpts från Microsoft Store för företag-adminportalen och sedan synkroniserats över till Microsoft Intune för hantering. Apparna kan antingen vara **onlinelicensierade** eller **offlinelicensierade**. Uppdateringar av Microsoft Store för företag-appar hanteras direkt av Microsoft Store utan att ytterligare åtgärd krävs av dig, administratören. Du kan även förhindra uppdateringar till specifika appar med hjälp av anpassad URI (Uniform Resource Identifier). Mer information finns på sidan om [Enterprise-apphantering – förhindra automatiska uppdateringar för appen](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates). På enheten kan slutanvändaren även inaktivera uppdateringar för alla Microsoft Store för företag-appar på enheten. 

### <a name="categorize-microsoft-store-for-business-apps"></a>Kategorisera appar i Microsoft Store för företag 
Använd följande steg för att kategorisera appar i Microsoft Store för företag: 

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Klientappar** > **Appar**>Välj en Microsoft Store för företag-app > **Appinformation** > **Kategori** . 
3. Välj en kategori i den nedrullningsbara menyn.

## <a name="installing-apps-on-windows-10-devices"></a>Installera appar på Windows 10-enheter
Beroende på apptypen kan appen installeras på en Windows 10-enhet på ett av två sätt:

- **Användarkontext**: När en app distribueras i användarkontext installeras den hanterade appen för den användaren på enheten när användaren loggar in på enheten. Observera att installationen av appen inte lyckas förrän användaren loggar in på enheten. 
  - Moderna verksamhetsspecifika appar och Microsoft Store för företag-appar (både online och offline) kan distribueras i användarkontext och stöder både avsikten Krävs och Tillgänglig.
  - Win32-appar som skapats som **användarläge** eller **dubbelläge** kan distribueras i användarkontext och stöder både **krävd** och **tillgänglig** avsikt. 
- **Enhetskontext**: När en app distribueras i enhetskontext installeras den hanterade appen direkt på enheten av Intune.
  - Endast moderna verksamhetsspecifika appar och offlinelicensierade appar i Microsoft Store för företag kan distribueras i enhetskontext och stöder endast avsikten Krävs.
  - Win32-appar som skapats som **datorläge** eller **dubbelläge** kan distribueras i användarkontext och stöder endast **krävd** avsikt.

> [!NOTE]
> För Win32-appar som skapats som **dubbelläge**-appar (admin) måste du välja om appen ska fungera som **användarläge** eller **datorläge** för alla tilldelningar som är associerade med denna instans. Distributionskontexten kan inte ändras per tilldelning.  

När en app distribueras i enhetskontext lyckas endast installationen när den riktas till en enhet som stöder enhetskontext. Dessutom stöder distribuering i enhetskontext dessutom följande villkor:
- Om en app distribueras i enhetskontext och riktas mot en användare kommer installationen att misslyckas med följande status och fel som visas i administratörskonsolen:
  - Status: Misslyckades.
  - Fel: Det går inte att rikta sig mot en användare med en kontextinstallation för enheter.
- Om en app distribueras i enhetskontext men riktas mot en enhet som inte stöder enhetskontext kommer installationen att misslyckas med följande status och fel i administratörskonsolen:
  - Status: Misslyckades.
  - Fel: Den här plattformen stöder inte kontextinstallationer för enheter. 

> [!Note]
> När en apptilldelning sparas med en specifik distribution går det inte att ändra kontexten för den tilldelningen förutom för moderna appar. I fallet med moderna appar går det att ändra kontexten från användarkontext till enhetskontext. 

I händelse av att det finns en konflikt i principer på en enskild användare/enhet används följande principprioriteringar för att avgöra den slutliga principen:
- En enhetskontextprincip är en högre prioritet än en användarkontextprincip. 
- En installationsprincip är en högre prioritet än en avinstallationsprincip.

Mer information om hur du tilldelar appar med hjälp av Microsoft Intune finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md) och [Inkludera och exkludera apptilldelningar i Microsoft Intune](apps-inc-exl-assignments.md). Mer information om apptyper i Intune finns i [Lägg till appar i Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Nästa steg

- Mer information om hur du tilldelar appar till grupper finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).
- Mer information om hur du övervakar apptilldelningar finns i [Hur du övervakar appar](apps-monitor.md).
