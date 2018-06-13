---
title: Fjärradministrera enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se vilka roller krävs för att använda TeamViewer, hur du installerar TeamViewer-anslutningsprogrammet och stegvisa anvisningar för hur du fjärradministrerar enheter med Microsoft Intune i Azure Portal
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 60d9398b80a30adee194470ac4e5c6c1efc0bd4c
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744643"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>Fjärradministrera Intune-enheter med TeamViewer

Enheter som hanteras av Intune kan fjärradministreras med hjälp av [TeamViewer](https://www.teamviewer.com). TeamViewer är ett tredjepartsprogram som du köper separat. Det här avsnittet visar hur du konfigurerar TeamViewer i Intune och fjärradministrerar en enhet. 

## <a name="prerequisites"></a>Krav

- Använd en enhet som stöds. Intune-hanterade Android-, Windows-, iOS- och macOS-enheter stöder fjärradministration. TeamViewer kanske inte stöder Windows Holographic (HoloLens), Windows Team (Surface Hub) eller Windows 10 S. Information om support finns i [TeamViewer](https://www.teamviewer.com).

- Intune-administratören i Azure Portal måste ha följande [Intune-roller](role-based-access-control.md):  

    - **Uppdatera fjärrhjälp**: Gör att administratörer kan ändra inställningarna för TeamViewer-anslutningsprogrammet
    - **Begär fjärrhjälp**: Gör att administratörer kan starta en ny fjärrhjälpsession för alla användare. Användare med den här rollen begränsas inte av någon Intune-roll inom ett omfång. Dessutom kan användare eller enhetsgrupper som tilldelats en Intune-roll i ett omfång också begära fjärrhjälp. 

- Ett [TeamViewer](https://www.teamviewer.com)-konto med autentiseringsuppgifter för inloggning

Genom att använda TeamViewer tillåter du att TeamViewer för Intune-anslutningsprogrammet kan skapa TeamViewer-sessioner, läsa Active Directory-data och spara TeamViewer-kontots åtkomsttoken.

## <a name="configure-the-teamviewer-connector"></a>Konfigurera TeamViewer-anslutningen

För att kunna ge fjärrhjälp till enheter måste du först konfigurera Intune TeamViewer-anslutningsprogrammet med följande steg:

1. I [Azure Portal](https://portal.azure.com) väljer du **Alla tjänster** och söker efter **Microsoft Intune**.
2. I **Microsoft Intune** väljer du **Enheter** och sedan **TeamViewer Connector**.
3. Välj **Anslut** och acceptera sedan licensavtalet.
4. Välj **Logga in på TeamViewer och auktorisera**.
5. En webbsida öppnas med TeamViewer-webbplatsen. Ange dina autentiseringsuppgifter för TeamViewer-licensen och välj sedan **Logga in**.

## <a name="remotely-administer-a-device"></a>Fjärradministrera en enhet

När anslutningen har konfigurerats är du redo att fjärradministrera en enhet. Gör så här: 

1. I [Azure Portal](https://portal.azure.com) väljer du **Alla tjänster** och söker efter **Microsoft Intune**.
2. I **Microsoft Intune** väljer du **Enheter** och sedan **Alla enheter**.
3. Välj den enhet som du vill fjärradministrera i listan. I egenskaperna för enheten väljer du **Ny fjärrhjälpssession**.
4. När Intune ansluter till TeamViewer-tjänsten visas information enheten. Välj **Anslut** för att starta fjärrsessionen.

![Exempel på hur du fjärradministrerar en Android-enhet](./media/android-teamviewer.png)

När du startar en fjärrsession visas en meddelandeflagga på ikonen för företagsportalappen på slutanvändarens enhet. Ett meddelande visas också när appen öppnas. Användaren kan sedan acceptera begäran om fjärrhjälp.

I TeamViewer kan du utföra ett antal åtgärder på enheten, till exempel ta kontroll över enheten. Fullständig information om vad du kan göra finns i [vägledningen för TeamViewer](https://www.teamviewer.com/support/documents/).

Stäng TeamViewer-fönstret när du är klar.