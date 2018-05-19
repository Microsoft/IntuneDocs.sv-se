---
title: Ta bort din Windows-enhet från Intune
description: Beskriver hur du tar bort en Windows-enhet från Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 1dd64250c1996c6b13c62f80572282d639112ba6
ms.sourcegitcommit: 8ee543c864097dc195b6f440471dca713fc21ed2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/09/2018
---
# <a name="remove-your-windows-device-from-intune-management"></a>Ta bort en Windows-enhet från Intune-hanteringen

Ta bort en registrerad Windows-enhet från Intune när du inte längre vill eller behöver:  
* Använd din enhet på arbetet eller i skolan. 
* Komma åt arbetets eller skolans e-post, appar eller andra resurser.

När den har tagits bort, kommer du inte att kunna komma åt skolans eller arbetets resurser från enheten. Windows-enheter som kan tas bort från Intune är:  
* Windows 10-enheter 
* Windows 8.1-dator
* Mobila enheter för Windows 8.1
 
Mer information om vad som händer när du tar bort enheten från Intune-hanteringen finns i [Vad händer om du tar bort enheten från Intune](what-happens-if-you-unenroll-your-device-from-intune-windows.md).

## <a name="remove-your-windows-10-device"></a>Ta bort din Windows 10-enhet
Utför följande steg om du vill ta bort en Windows 10-enhet från Intune.

### <a name="via-the-company-portal-app"></a>Via företagsportalappen

1. Öppna företagsportalappen.
2. Logga in med dina kontouppgifter för arbets- eller skolkontot.
3. I **Mina Enheter** väljer du den enhet du vill ta bort.
4. I det övre högra hörnet på appen, väljer du ikonen **Se mer**.
5. Välj **Ta bort**. 
6. För att bekräfta borttagning av en enhet, välj **Ta bort enheten**.

### <a name="via-device-settings-app"></a>Via appen för enhetsinställning
1. Öppna inställningsappen. 
2. Gå till **Konton** > **Åtkomst till arbete eller skola**.
3. Välj det anslutna konto som du vill ta bort > **Koppla från**.
4. För att bekräfta borttagning av en enhet, välj **Ja**.

## <a name="remove-your-windows-81-computer"></a>Ta bort din Windows 8.1-dator
Utför följande steg om du vill ta bort en Windows 8.1-dator från Intune.

1.  Gå till **Datorinställningar** > **Nätverk** > **Arbetsplats**.
2.  Under **Anslut till arbetsplats** väljer du **Lämna**.
3.  Under **Turn on device management** (Aktivera enhetshantering) väljer du **Inaktivera**.
4.  I popup-fönstret som öppnas väljer du **Inaktivera**.

## <a name="remove-your-windows-81-mobile-device"></a>Ta bort din mobila enhet för Windows 8.1
Utför följande steg om du vill ta bort en mobil enhet för Windows 8.1 från Intune.

1.  Gå till **Inställningar** > **Arbetsplats**.
2.  Tryck på arbetsplatskontot som du vill avregistrera.
3.  Tryck på **Ta bort** längst ned på skärmen.
4.  Tryck på **Ta bort** i dialogrutan **Ta bort konto**.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Ta bort din personliga information när du tagit bort företagsportalen
Det finns två typer av data som företagsportalen lagrar på din Windows-enhet:

-   **Diagnostikloggar**: Standardappens aktivitetsdata som Microsoft samlar in raderas automatiskt när du tar bort enheten från företagsportalen. Aktivitetsdata för appen är till exempel data om hur länge appen var öppen eller om appen har kraschat.
-   **Cacheminne**: Stödfiler som krävs för att appen ska fungerar, till exempel ikoner och inställningar.

Det finns vissa saker som du behöver göra för att den här informationen ska tas bort helt.

1. Avinstallera företagsportalen. När du [avinstallerar företagsportalappen](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) tas vissa appdata som lagras på enheten bort.  

2. Återställ företagsportalen för att återställa lagrade appdata. Öppna appen **Inställningar** och markera > **Appar** > **Företagsportalen** > **Avancerade alternativ**  >  **Återställ**. 

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).