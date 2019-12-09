---
title: Lägga till webbappar i Microsoft Intune
titleSuffix: ''
description: Läs mer om att lägga till webbappar (klient/serverprogram) i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68e2e768067a88b8ae58adeb38c17d90ac995a30
ms.sourcegitcommit: b752acefec077c719e169e665c955adb944e85c6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74781234"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Lägga till webbappar i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune stöder en mängd olika apptyper som bland annat webbappar. En webbapp är ett klientserverprogram. Servern tillhandahåller webbappen, som inkluderar användargränssnitt, innehåll och funktioner. Dessutom erbjuder moderna webbtjänstplattformar ofta säkerhet, belastningsutjämning och andra förmåner. En webbapp underhålls separat på webben. Du använder Microsoft Intune till att peka på den här apptypen. Du anger också vilka användargrupper som får åtkomst till den här appen. 

Innan du kan hantera och tilldela appar för dina användare, lägger du till appen i Intune. 

Intune skapar en genväg till webbappen på användarens enhet. På iOS-enheter läggs en genväg till webbappen till på startskärmen. På Android Device Admin-enheter läggs en genväg till webbappen till i Intunes företagsportalswidget, vilken användaren måste fästa manuellt. På Windows-enheter placeras en genväg till webbappen i Start-menyn.

> [!Note]
> En webbläsare måste vara installerad på användarens enhet för att det ska gå att starta webbappar. 

> [!Note]
> Information rörande Android Enterprise-enheter finns i [Webblänkar för hanterat Google Play-konto](apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="add-a-web-app-to-intune"></a>Lägg till en webbapp i Intune
Om du vill lägga till en app i Intune som en genväg till en app på webben gör du så här:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. Välj typen **Webblänk** i listrutan **Typ av app** i fönsterrutan **Lägg till app**.
4. Välj **Konfigurera**.
5. Lägg till följande information i fönstret **Appinformation**:
    - **Namn**:  Ange namnet på appen så som den ska visas i företagsportalen. 

        > [!NOTE]
        > Om du ändrar namnet på appen via Intune i Azure Portal när du har distribuerat och installerat den kan du inte längre använda appen som mål i dina kommandon.

    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Appens webbadress**: Ange webbadressen till den webbplats där den app som du vill tilldela finns.
    - **Kategori**: Du kan även välja en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Välj det här alternativet för att tydligt visa appsviten på företagsportalens huvudsida när användarna söker efter appar.
    - **Kräv en hanterad webbläsare för att öppna den här länken**: Välj det här alternativet om du vill tilldela en länk till användarna till en webbplats eller en webbapp som de kan öppna i en Intune-hanterad webbläsare. Den här webbläsaren måste installeras på enheterna.
    - **Logotyp**: Överför en ikon som ska kopplas till appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
6. Välj **OK**.
7. I fönstret **Lägg till app** väljer du **Lägg till**.

> [!Note]
> För närvarande associeras distribution av Intune-webappar till iOS-enheter med hanteringsprofilen och kan inte tas bort manuellt. Du kan ändra distributionstypen till **Avinstallera** i Intune-portalen, så att webbappen kan tas bort automatiskt. Om du tar bort distributionen innan du ändrar tilldelningsavsikt för appen till **Avinstallera**, kommer webbappen dock att förbli permanent på enheten tills enheten har avregistrerats från Intune.

Slutanvändarna kan starta webbappar direkt från Windows företagsportalapp genom att välja webbappen och sedan välja alternativet **Öppna i webbläsare**. Den publicerade webbadressen öppnas direkt i webbläsaren. 

## <a name="next-steps"></a>Nästa steg

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md). 
