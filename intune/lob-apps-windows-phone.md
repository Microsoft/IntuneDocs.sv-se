---
title: "Så här lägger du till branschspecifika Windows Phone-appar i Intune"
titlesuffix: Azure portal
description: "Läs om att lägga till verksamhetsspecifika Windows Phone-appar till Intune.\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 60776df3774d4f9ca7404ef04b1cc94536bcd164
ms.sourcegitcommit: 4b776d1a87c0707244f4ae0122de882e0eef6fa3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2017
---
# <a name="how-to-add-windows-phone-line-of-business-lob-apps-to-microsoft-intune"></a>Så här lägger du till branschspecifika Windows Phone-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Steg 1 – Ange platsen för programinstallationsfilen

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** + **Intune**.
3. Välj **Hantera appar** på **Intune**-bladet.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. I bladet **Lägg till app** väljer du **Branschspecifik app**.

## <a name="step-2---configure-the-app-package-file"></a>Steg 2 – Konfigurera appaketfilen

1. På bladet **Lägg till app** väljer du filen **Appaket**.
2. På bladet **Appaket** väljer du knappen Bläddra. Välj sedan en Windows Phone-installationsfil med filnamnstillägget **.xap**.
3. Välj **OK** när du är klar.


## <a name="step-3---configure-app-information"></a>Steg 3 – Konfigurera appinformation

1. På bladet **Lägg till app** väljer du filen **Appaket**.
2. På bladet **Appinformation** konfigurerar du appinformationen. Beroende på vilken app du har valt kan det hända att några av värdena i det här bladet har fyllts i automatiskt:
    - **Namn** – Ange namnet på appen så som det visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Beskrivning** – Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Kategori** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Om du använder kategorier blir det enklare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp** – Ladda upp en ikon som är associerad med appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
3. Välj **OK** när du är klar.

## <a name="step-4---finish-up"></a>Steg 4 – Slutför

1. På bladet **Lägg till app** kontrollerar du att informationen är korrekt konfigurerad.
2. Välj **Lägg till** för att överföra appen till Intune.

## <a name="next-steps"></a>Nästa steg

Appen som du har skapat visas i applistan. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Mer information finns i [Så här övervakar du appinformation och tilldelningar](apps-monitor.md).

Lär dig mer om kontexten för din app i Intune. Mer information finns i [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md)
