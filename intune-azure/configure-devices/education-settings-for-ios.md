---
title: "Konfigurera inställningar för Intune-utbildning på iOS | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs mer om de inställningar som du kan använda för att konfigurera utbildningsinställningarna på iOS-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44c427f8-0f22-43c2-8c29-e0f9fa533b1f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f05e0018fb202ab5774e935c3f59855e4aa2e75
ms.openlocfilehash: e52fdf8c30a680d62071cd31e308dd0180e8b9dc


---

# <a name="how-to-configure-intune-education-settings-for-ios-devices-in-intune-azure-preview"></a>Så här konfigurerar du inställningar för Intune-utbildning på iOS-enheter i förhandsversionen av Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="create-a-device-profile-containing-ios-education-settings"></a>Skapa en enhetsprofil med utbildningsinställningar för iOS

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för versionsuppgraderingsprofilen.
5. Välj **iOS** i listrutan **Plattform**.
6. Välj **Utbildning** i listrutan **Profiltyp**.
7. På bladet **Utbildning** väljer du följande:
    - **Rotcertifikatfil för lärare**
    - **PKCS12-/PFX-profil för lärare**
    - **Rotcertifikatfil för student**
    - **Student PKCS12/PFX-profil**
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.



<!--HONumber=Feb17_HO1-->


