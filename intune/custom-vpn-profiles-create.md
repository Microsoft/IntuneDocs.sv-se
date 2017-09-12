---
title: "Så här skapar du anpassade VPN-profiler med Microsoft Intune"
titleSuffix: Azure portal
description: "Använd anpassade konfigurationer för att skapa VPN-profiler i Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ea86abedb49dea45af18caacbe25572d06ce984f
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Så här skapar du anpassade VPN-profiler i Microsoft Intune

## <a name="create-a-custom-configuration"></a>Skapa en anpassad konfiguration
Du kan använda anpassade konfigurationsprinciper i Intune för att skapa VPN-profiler för:

* Enheter som kör Android 4 och senare
* Registrerade enheter som kör Windows 8.1 och senare
* Enheter som kör Windows Phone 8.1 och senare
* Registrerade enheter som kör Windows 10 desktop och senare 
* Enheter som kör Windows 10 Mobile

Den här typen av princip kan vara praktisk när VPN-standardprinciperna i Intune inte innehåller de inställningar som du vill använda.

## <a name="to-create-a-custom-configuration-policy"></a>Skapa en anpassad konfigurationsprincip:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
4. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
5. Välj **Skapa profil** på profilbladet.
6. Ange **Namn** och **Beskrivning** för VPN-profilen på bladet **Skapa profil**.
7. Välj den enhetsplattform på vilken du vill tillämpa VPN-inställningarna från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för anpassade enhetsinställningar:
    - **Android**
    - **iOS** (konfigureras med en fil som du har exporterat från Apple Configurator).
    - **macOS** (konfigureras med en fil som du har exporterat från Apple Configurator).
    - **Windows Phone 8.1**
    - **Windows 10 och senare**
6. I listrutan **Profil**typ väljer du **Anpassad**.
7. På bladet **Anpassade OMA-URI-inställningar** väljer du för varje URI-inställning som du vill ange **Lägg till**, anger den begärda informationen och väljer sedan **OK**. Här är ett exempel:

   ![Dialogrutan för anpassad konfiguration av VPN-profil](./media/Intune_Add_VPN_URI.png)

4.  När du har angett alla URI-inställningar som du behöver väljer du **OK**, och klickar sedan på bladet **Skapa profil** och väljer **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).




