---
title: Fjärradministrera enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se vilka roller krävs för att använda TeamViewer, hur du installerar TeamViewer-anslutningsprogrammet och stegvisa anvisningar för hur du fjärradministrerar enheter med Microsoft Intune i Azure Portal
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0372c9629e111c460b095d8c0236305866da42e3
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907210"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>Fjärradministrera Intune-enheter med TeamViewer

Enheter som hanteras av Intune kan fjärradministreras med hjälp av [TeamViewer](https://www.teamviewer.com). TeamViewer är ett tredjepartsprogram som du köper separat. Det här avsnittet visar hur du konfigurerar TeamViewer i Intune och fjärradministrerar en enhet. 

## <a name="prerequisites"></a>Krav

- Använd en enhet som stöds. Intune-hanterad Android-enhetsadministratör, arbetsprofil för Android-, Windows-, iOS- och macOS-enheter stöder fjärradministration. TeamViewer kanske inte stöder Windows Holographic (HoloLens), Windows Team (Surface Hub) eller Windows 10 S. Information om support finns i [TeamViewer](https://www.teamviewer.com).

> [!NOTE]
> Android-dedikerad och fullständigt hanterad stöds inte.

- Intune-administratören i Azure Portal måste ha följande [Intune-roller](../fundamentals/role-based-access-control.md):  

  - **Uppdatera fjärrhjälp**: Gör att administratörer kan ändra inställningarna för TeamViewer-anslutningsprogrammet
  - **Begär fjärrhjälp**: Gör att administratörer kan starta en ny fjärrhjälpssession för alla användare. Användare med den här rollen begränsas inte av någon Intune-roll inom ett omfång. Dessutom kan användare eller enhetsgrupper som tilldelats en Intune-roll i ett omfång också begära fjärrhjälp. 

- Ett [TeamViewer](https://www.teamviewer.com)-konto med autentiseringsuppgifter för inloggning. Endast vissa TeamViewer-licenser kan stödja integrering med Intune. Särskilda krav för TeamViewer beskrivs i [TeamViewer-integreringspartner: Microsoft Intune](https://www.teamviewer.com/integrations/microsoft-intune/).

Genom att använda TeamViewer tillåter du att TeamViewer för Intune-anslutningsprogrammet kan skapa TeamViewer-sessioner, läsa Active Directory-data och spara TeamViewer-kontots åtkomsttoken.

## <a name="configure-the-teamviewer-connector"></a>Konfigurera TeamViewer-anslutningen

För att kunna ge fjärrhjälp till enheter måste du först konfigurera Intune TeamViewer-anslutningsprogrammet med följande steg:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Administration av klientorganisation** > **Anslutning och token** > **TeamViewer-anslutningsprogram**.
3. Välj **Anslut** och acceptera sedan licensavtalet.
4. Välj **Logga in på TeamViewer och auktorisera**.
5. En webbsida öppnas med TeamViewer-webbplatsen. Ange dina autentiseringsuppgifter för TeamViewer-licensen och välj sedan **Logga in**.

## <a name="remotely-administer-a-device"></a>Fjärradministrera en enhet

När anslutningen har konfigurerats är du redo att fjärradministrera en enhet. Gör så här: 

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** och sedan **Alla enheter**.
3. I listan väljer du den enhet som du vill fjärradministrera > **...** > **Ny fjärrhjälpssession**.
4. När Intune ansluter till TeamViewer-tjänsten visas information enheten. Välj **Anslut** för att starta fjärrsessionen.

![Exempel på hur du fjärradministrerar en Android-enhet](./media/teamviewer-support/android-teamviewer.png)

När du startar en fjärrsession ser användarna en meddelandeflagga på ikonen för företagsportalappen på enheten. Ett meddelande visas också när appen öppnas. Användarna kan då godkänna begäran om fjärrhjälp.

> [!NOTE]
> Windows-enheter som registreras med hjälp av ”användarlösa” metoder, t. ex. DEM och WCD, visar inte TeamViewer-meddelandet i företagsportalappen. I dessa fall rekommenderar vi att TeamViewer-portalen används för att skapa sessionen.

I TeamViewer kan du utföra ett antal åtgärder på enheten, till exempel ta kontroll över enheten. Fullständig information om vad du kan göra finns i [vägledningen för TeamViewer](https://www.teamviewer.com/support/documents/).

Stäng TeamViewer-fönstret när du är klar.
