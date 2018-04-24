---
title: Ta bort Windows-enheten från Intune | Microsoft Docs
description: Beskriver hur du tar bort en Windows-enhet från Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/28/2018
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
ms.openlocfilehash: 9f9051fb393c82031d581f7fec731a3b148cbf2e
ms.sourcegitcommit: 7f46e9990797bdfa669ccba2077721f1bc70c07e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/04/2018
---
# <a name="remove-your-windows-device-from-intune"></a>Ta bort din Windows-enhet från Intune

Om enheten är registrerad i Intune, men du inte längre vill använda din Windows-enhet för att komma åt e-postmeddelanden, appar eller andra resurser på arbetet eller i skolan, måste du ta bort enheten från hanteringen. När du har tagit bort enheten från Intune kommer du inte längre ha åtkomst till dessa resurser. Mer information om vad som händer när du tar bort enheten finns i [Vad händer om du avregistrerar din enhet från Intune?](what-happens-if-you-unenroll-your-device-from-intune-windows.md).

## <a name="remove-your-windows-10-device"></a>Ta bort din Windows 10-enhet

1.  Från din applista trycker du på appen **Företagsportal** .

2.  Logga in med dina kontouppgifter för arbets- eller skolkontot.

3.  I **Mina Enheter**väljer du den enhet du vill avregistrera.

4.  Tryck på **Ta bort** &gt; **Ta bort**.

## <a name="remove-your-windows-81-computer"></a>Ta bort din Windows 8.1-dator

1.  Gå till **Datorinställningar** &gt; **Nätverk** &gt; **Arbetsplats**.

2.  Under **Anslut till arbetsplats** väljer du **Lämna**.

3.  Under **Turn on device management** (Aktivera enhetshantering) väljer du **Inaktivera**.

4.  I popup-fönstret som öppnas väljer du **Inaktivera**.

## <a name="remove-your-windows-phone-81-mobile-device"></a>Ta bort din mobila Windows Phone 8.1-enhet

1.  Gå till **Inställningar** &gt; **Arbetsplats**.

2.  Tryck på arbetsplatskontot som du vill avregistrera.

3.  Tryck på **Ta bort** längst ned på skärmen.

4.  Tryck på **Ta bort** i dialogrutan **Ta bort konto**.

## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Ta bort din personliga information när du tagit bort företagsportalen

Det finns två typer av data som företagsportalen lagrar på din Windows-enhet:

-   **Diagnostikloggar**: Standardappens aktivitetsdata som Microsoft samlar in, t.ex. hur länge appen var öppen eller om den kraschade, raderas automatiskt när du tar bort enheten från företagsportalen.
-   **Programcache**: Lagring av vissa stödfiler som krävs för appen ska fungera, t.ex. ikoner och inställningar.

Det finns vissa saker som du behöver göra för att den här informationen ska tas bort helt.

### <a name="uninstall-the-company-portal"></a>Avinstallera företagsportalen  

När du [avinstallerar företagsportalappen](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) tas vissa appdata som lagras på enheten bort.  

### <a name="reset-the-company-portal"></a>Återställa företagsportalen

Du kan återställa resten av företagsportalens appdata genom att återställa appen i Inställningar. Öppna **Inställningar** > **Appar och funktioner** > **Företagsportal** > **Avancerade alternativ** > **Återställ**.

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).