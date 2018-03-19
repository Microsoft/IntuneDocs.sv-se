---
title: "Så här skapar du anpassade VPN-profiler med Microsoft Intune"
titleSuffix: 
description: "Använd anpassade konfigurationer för att skapa VPN-profiler i Intune."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ec9b959d086051985287a62f7d10fe8d4cbad7e9
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Så här skapar du anpassade VPN-profiler i Microsoft Intune

Du kan använda anpassade konfigurationsprinciper i Intune för att skapa VPN-profiler för följande plattformar:

* Android 4 och senare
* Registrerade enheter som kör Windows 8.1 och senare
* Windows Phone 8.1 och senare
* Registrerade enheter som kör Windows 10 desktop och senare 
* Windows 10 Mobil

Den här typen av princip kan vara praktisk när VPN-standardprinciperna i Intune inte har de inställningar som du vill använda.

## <a name="to-create-a-custom-configuration-policy"></a>Skapa en anpassad konfigurationsprincip:

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enhetskonfiguration**.
2. I fönstret **Enhetskonfiguration** under avsnittet **Hantera** väljer du **Profiler**.
5. I fönstret Profiler väljer du **Skapa profil**.
6. Ange **Namn** och **Beskrivning** för VPN-profilen i fönstret **Skapa profil**.
7. Välj den enhetsplattform på vilken du vill tillämpa VPN-inställningarna från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för anpassade enhetsinställningar:
    - **Android**
    - **Android for Work**
    - **iOS** (konfigureras med en fil som du har exporterat från Apple Configurator).
    - **macOS** (konfigureras med en fil som du har exporterat från Apple Configurator).
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**
6. I listrutan **Profil**typ väljer du **Anpassad**.
7. I fönstret **Anpassade OMA-URI-inställningar** väljer du för varje URI-inställning som du vill ange **Lägg till**, anger den begärda informationen och väljer sedan **OK**. Här är ett exempel:

   ![Dialogrutan för anpassad konfiguration av VPN-profil](./media/Intune_Add_VPN_URI.png)

4.  När du har angett alla URI-inställningar som du behöver väljer du **OK**, och klickar sedan på fönstret **Skapa profil** och väljer **Skapa**.

Profilen skapas och visas i fönstret med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).




