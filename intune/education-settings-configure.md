---
title: "Konfigurera inställningar för Intune-utbildning för Windows 10"
titleSuffix: Azure portal
description: "Läs om hur du använder Intune för att konfigurera Windows 10-utbildningsinställningar för enheter som du hanterar.”"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 12e36761320557f6af9554d3b671fc133253c13c
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>Så här konfigurerar du utbildningsinställningar för Windows 10 i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med utbildningsprofiler kan du ange information som konfigurerar Windows Gör ett prov-app, inklusive kontoinformation och URL. När du konfigurerar detta öppnas Gör ett prov-appen med det prov som du anger och inga andra appar kan köras på enheten förrän provet har slutförts.

Mer information om appen Gör ett prov finns i avsnittet om hur du [gör prov i Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).

## <a name="create-a-device-profile-containing-education-profile-settings"></a>Skapa en enhetsprofil som innehåller inställningarna för utbildningsprofilen

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för enhetsbegränsningsprofilen.
5. I listrutan **Plattform** väljer du **Windows 10 och senare**.
6. Välj **Utbildningsprofil** i listrutan **Profiltyp**. 
7. Välj Inställningar > Konfigurera, klicka på bladet **Gör ett prov** och konfigurera följande:
    - **Kontoanvändarnamn** – Ange användarnamnet för det konto som används till Gör ett prov. Detta kan vara ett domänkonto, ett konto i Azure Active Directory (AAD) eller ett lokalt datorkonto.
    - **URL för begränsad provmiljö** – Ange URL:en till det prov som du vill att användarna ska göra. Mer information finns i dokumentationen för Gör ett prov.
    - **Skärmbild** – Ange om du vill kunna övervaka skärmaktiviteten medan användarna gör provet.
    - **Textförslag** – Tillåt eller blockera textförslag medan användarna gör ett prov.
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.

## <a name="next-steps"></a>Nästa steg

Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).



