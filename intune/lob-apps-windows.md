---
title: "Så här lägger du till branschspecifika Windows-appar i Intune"
titlesuffix: Azure portal
description: "Läs om att lägga till verksamhetsspecifika Windows-appar till Intune.”"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c8ae15dc7b192cbfe3f0759e568b92783f24e1fe
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-add-windows-line-of-business-lob-apps-to-microsoft-intune"></a>Så här lägger du till branschspecifika Windows-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Steg 1 – Ange platsen för programinstallationsfilen

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Hantera appar** på **Intune**-bladet.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. I bladet **Lägg till app** väljer du **Branschspecifik app**.

## <a name="step-2---configure-the-app-package-file"></a>Steg 2 – Konfigurera appaketfilen

1. På bladet **Lägg till app** väljer du filen **Appaket**.
2. På bladet **Appaketfil** väljer du bläddringsknappen och väljer en Windows-installationsfil med filnamnstillägget **.msi**, **.appx** eller **.appxbundle**.
3. Välj **OK** när du är klar.


## <a name="step-3---configure-app-information"></a>Steg 3 – Konfigurera appinformation

1. På bladet **Lägg till app** väljer du filen **Appaket**.
2. På bladet **Appinformation** konfigurerar du följande information (vissa värden på det här bladet kanske har fyllts i automatiskt):
    - **Namn** – Ange namnet på appen så som det visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Beskrivning** – Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Kategori** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Om du kategoriserar apparna blir det enklare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Om du vill anger du webbadressen till en webbplats som innehåller information om appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretess-URL** – Om du vill anger du webbadressen till en webbplats som innehåller sekretessinformation för appen. Webbadressen visas för användarna på företagsportalen.
    - **Kommandoradsargument** – Om du vill anger du kommandoradsargument som du vill tillämpa på MSI-filen när den körs, t.ex. **/q**.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp** – Ladda upp en ikon som är associerad med appen. Ikonen visas tillsammans med appen när användarna söker på företagsportalen.
3. Välj **OK** när du är klar.

## <a name="step-4---finish-up"></a>Steg 4 – Slutför

1. På bladet **Lägg till app** kontrollerar du att appinformationen är korrekt konfigurerad.
2. Välj **Lägg till** för att överföra appen till Intune.

## <a name="next-steps"></a>Nästa steg

Appen som du har skapat visas i applistan. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).
