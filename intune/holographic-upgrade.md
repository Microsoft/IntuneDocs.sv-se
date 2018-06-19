---
title: Uppgradera Windows Holographic till Windows Holographic for Business
titleSuffix: Microsoft Intune
description: Lär dig hur du uppgraderar enheter som kör Windows Holographic till Windows Holographic for Business
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 08763aa527f24ff7b357603be5e3bd4da5083b45
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31830441"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Uppgradera enheter som kör Windows Holographic till Windows Holographic for Business


Om du vill hantera enheter som kör Windows Holographic med Microsoft Intune måste du uppgradera enheterna från Windows Holographic till Windows Holographic for Business. Du kan skapa en profil för versionsuppgradering för att genomföra uppgraderingen. Du kan köpa Commercial Suite för att få licensen som krävs för uppgraderingen för Microsoft-HoloLens. Mer information finns i [Unlock Windows Holographic for Business features](https://docs.microsoft.com/en-us/hololens/hololens-upgrade-enterprise) (Lås upp funktioner i Windows Holographic for Business).

## <a name="to-set-up-an-edition-upgrade-device-configuration-profile"></a>Konfigurera en konfigurationsprofil för versionsuppgradering av enheter

1. Logga in på [Azure Portal](https://portal.azure.com) med ditt administratörskonto.


2.  Klicka på **Enhetskonfiguration**, **Profiler** och sedan **+ Skapa profil**.

    ![Skapa en profil](media/Holographic-create-profile.png)

3.  I fönstret **Skapa profil** anger du ett namn för profilen, väljer **Windows 10 och senare** för plattformen och väljer **Uppgradering av utgåva** för profiltypen. Klicka på **Konfigurera inställningar**.

5. I fönstret **Uppgradering av utgåva** på **Version att uppgradera till** väljer du **Windows 10 Holographic for Business**. På **Licensfil** bläddrar du till och väljer XML-licensfilen som du fått.

    ![Ange ett XML-filnamnet](media/Holographic-edition-upgrade.png)
 
5.  Klicka på **OK** och sedan på **Skapa** för att skapa profilen.


## <a name="deploy-the-edition-upgrade-policy"></a>Distribuera utgåveuppgraderingsprincipen

Därefter tilldelar du utgåveuppgraderingsprofilen till valda grupper eller enheter.

1. På profilen som du skapade i föregående steg klickar du på **Tilldelningar**.

2. I fönstret **Tilldelningar** väljer du användargrupperna och enheterna som du vill inkludera och exkludera med principen.

![Inkludera och exkludera grupper](media/Holographic-groups.PNG)

När dessa användare eller enheter registreras i Intune används utgåveuppgraderingsprofilen. 

## <a name="next-steps"></a>Nästa steg

Mer information om de här grupperna finns i [Kom igång med grupper](get-started-groups.md).


