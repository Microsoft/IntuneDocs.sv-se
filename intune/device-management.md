---
title: Hantera enheter med Intune
titleSuffix: Intune on Azure
description: "Läs hur du visar de enheter som du hanterar med Intune och utför olika åtgärder på dem.”"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0686b3ece3a929cb06a29f4e58046872b70ec926
ms.sourcegitcommit: b8987b8dfb009ea55678d7f640ac5f18a6ab167e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Vad är enhetshantering i Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som IT-administratör måste du se till att hanterade enheter tillhandahåller de resurser som slutanvändarna behöver för att utföra sitt arbete, samtidigt som du måste skydda dessa data så att de inte utsätts för risk.

Arbetsbelastningen **Enheter** ger dig insikter om de enheter du hanterar och låter dig utföra fjärråtgärder på dessa enheter. För att få åtkomst till arbetsbelastningen:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** i **Intune**.
4. Du kan visa information om enheter och utföra fjärrenhetsåtgärder på följande sätt:
    - **Översikt** – En ögonblicksbild av de registrerade enheter som du kan hantera.
    - **Alla enheter** – En lista över de registrerade enheter som du hanterar. Välj **Filter** eller **Kolumner** om du vill begränsa vilken information som visas. Välj en enhet om du vill [visa enhetsinventering](device-inventory.md).
    - **Azure AD-enheter** – En lista över de enheter som registrerats för eller anslutits till Azure Active Directory (AD). Läs mer om [Azure AD-enhetshantering](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
    - **Enhetsåtgärder** – En historik över de fjärråtgärder som utförts på enheter, inklusive åtgärden, dess status, vem som initierade åtgärden och när den utfördes.

    ![Övervaka enhetsåtgärder](./media/monitor-device-actions.png)

    - **TeamViewer** – Med tjänsten TeamViewer kan användare av Intune-hanterade Android-enheter få fjärrhjälp från IT-administratören. Läs mer om [TeamViewer](device-profile-android-teamviewer.md).

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

- Välj **Enhetsåtgärder** om du vill visa status för åtgärder som vidtas på enheter som du hanterar.
