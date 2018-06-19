---
title: Konfigurera inställningar för Intune-utbildning för Windows 10
titleSuffix: Microsoft Intune
description: Läs om hur du använder Intune för att konfigurera Windows 10-utbildningsinställningar på enheter som du hanterar.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 413ad0bab32353fc6f5b401f9a7b910b6c5cb390
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31023316"
---
# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>Så här konfigurerar du utbildningsinställningar för Windows 10 i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Med utbildningsprofiler kan du ange information som konfigurerar Windows Gör ett prov-app, inklusive kontoinformation och URL. När du konfigurerar detta öppnas Gör ett prov-appen med det prov som du anger och inga andra appar kan köras på enheten förrän provet har slutförts.

Mer information om appen Gör ett prov finns i avsnittet om hur du [gör prov i Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).

## <a name="create-a-device-profile-containing-education-profile-settings"></a>Skapa en enhetsprofil som innehåller inställningarna för utbildningsprofilen

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enhetskonfiguration**.
2. I fönstret **Enhetskonfiguration** under avsnittet **Hantera** väljer du **Profiler**.
3. I fönstret Profiler väljer du **Skapa profil**.
4. I fönstret **Skapa profil** anger du ett **Namn** och en **Beskrivning** för enhetsbegränsningsprofilen.
5. I listrutan **Plattform** väljer du **Windows 10 och senare**.
6. Välj **Utbildningsprofil** i listrutan **Profiltyp**. 
7. Välj **Inställningar > Konfigurera**, klicka på fönstret **Gör ett prov** och konfigurera följande:
    - **Kontotyp** – Välj en kontotyp från listrutan.
    - **Kontoanvändarnamn** – Ange användarnamnet för det konto som används till Gör ett prov. Detta kan vara ett domänkonto, ett konto i Azure Active Directory (AAD) eller ett lokalt datorkonto.
    - **URL för begränsad provmiljö** – Ange URL:en till det prov som du vill att användarna ska göra. Mer information finns i dokumentationen för Gör ett prov.
    - **Skärmbild** – Ange om du vill kunna övervaka skärmaktiviteten medan användarna gör provet.
    - **Textförslag** – Tillåt eller blockera textförslag medan användarna gör ett prov.
8. När du är klar går du tillbaka till fönstret **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas i fönstret med profillistan.

## <a name="next-steps"></a>Nästa steg

Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).



