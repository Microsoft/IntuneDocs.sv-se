---
title: Hantera enheter med Microsoft Intune
titleSuffix: ''
description: Granska de enheter som du hanterar med Intune och utför olika åtgärder för dem.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 436eeb306bf4ba343ae4d88a824aeed2077a3426
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="what-is-microsoft-intune-device-management"></a>Vad är enhetshantering i Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som IT-administratör måste du se till att hanterade enheter tillhandahåller de resurser som slutanvändarna behöver för att utföra sitt arbete, samtidigt som du måste skydda dessa data så att de inte utsätts för risk.

Arbetsbelastningen **Enheter** ger dig insikter om de enheter du hanterar och låter dig utföra fjärråtgärder på dessa enheter. För att få åtkomst till arbetsbelastningen:

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enheter** i **Intune**.
4. Du kan visa information om enheter och utföra fjärrenhetsåtgärder på följande sätt:
    - **Översikt** – En ögonblicksbild av de registrerade enheter som du kan hantera.
    - **Alla enheter** – En lista över de registrerade enheter som du hanterar. Välj **Filter** eller **Kolumner** om du vill begränsa vilken information som visas. Välj en enhet om du vill [visa enhetsinventering](device-inventory.md).
    - **Azure AD-enheter** – En lista över de enheter som registrerats för eller anslutits till Azure Active Directory (AD). Läs mer om [Azure AD-enhetshantering](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
    - **Enhetsåtgärder** – En historik över de fjärråtgärder som utförts på enheter, inklusive åtgärden, dess status, vem som initierade åtgärden och när den utfördes.

        ![Skärmbild som visar när enhetsåtgärder övervakas](./media/monitor-device-actions.png)

    - **Granskningsloggar** – Med granskningsloggar får du en post med de aktiviteter som genererar en ändring i Microsoft Intune. Läs mer om [Granskningsloggar](monitor-audit-logs.md).
    - **TeamViewer-anslutningsprogram** – Med TeamViewer-tjänsten kan användare av Intune-hanterade Android-enheter få fjärrhjälp från sin IT-administratör. Läs mer om [TeamViewer](device-profile-android-teamviewer.md).
    - **Hjälp och support** – Felsök, begär support eller visa Intune-status.  
    
## <a name="available-device-actions"></a>Tillgängliga enhetsåtgärder
Vilka åtgärder som är tillgängliga beror på enhetsplattformen och enhetens konfiguration.

- [Visa enhetsinventeringen](device-inventory.md)
- Utför åtgärder för fjärransluten enhet:
    - [Ta bort företagsdata](devices-wipe.md#remove-company-data)
    - [Fabriksåterställning](devices-wipe.md#factory-reset)
    - [Fjärrlåsning](device-remote-lock.md)
    - [Återställ lösenord](device-passcode-reset.md)
    - [Kringgå aktiveringslås](device-activation-lock-bypass.md) (Endast iOS)
    - [Börja om på nytt](device-fresh-start.md) (Endast Windows)
    - [Borttappat läge](device-lost-mode.md) (Endast iOS)
    - [Hitta enhet](device-locate.md) (Endast iOS)
    - [Starta om](device-restart.md) (Endast Windows)
    - [Återställning av Windows 10-PIN](device-windows-pin-reset.md)
    - [Fjärrstyrning för Android](device-profile-android-teamviewer.md)
    - [Synkronisera enhet](device-sync.md)


## <a name="next-steps"></a>Nästa steg

- Välj **Enhetsåtgärder** för att se status för de åtgärder som vidtas på enheter som du hanterar.
