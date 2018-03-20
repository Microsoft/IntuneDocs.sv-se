---
title: "Lägga till verksamhetsspecifika appar för Windows Phone i Microsoft Intune"
titlesuffix: 
description: "Läs om att lägga till verksamhetsspecifika appar för Windows Phone i Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8466a77929620ef9ef7c1559dae62990730d0acd
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-windows-phone-line-of-business-lob-apps-to-microsoft-intune"></a>Så här lägger du till branschspecifika Windows Phone-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Informationen i den här artikeln visar hur du lägger till verksamhetsspecifika appar för Windows Phone i Microsoft Intune. En verksamhetsspecifik app är en app som du lägger till i Intune från en appinstallationsfil. Dessa typer av appar är vanligen skrivna internt. Intune installerar den verksamhetsspecifika appen på användarens enhet. 

## <a name="step-1---specify-the-software-setup-file"></a>Steg 1 – Ange platsen för programinstallationsfilen

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Mobilappar** i **Intune**-fönstret.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. I fönstret **Lägg till app** väljer du **Verksamhetsspecifik app**.

## <a name="step-2---configure-the-app-package-file"></a>Steg 2 – Konfigurera appaketfilen

1. I fönstret **Lägg till app** väljer du filen **Appaket**.
2. I filfönstret **Appaket** väljer du knappen Bläddra. Välj sedan en Windows Phone-installationsfil med filnamnstillägget **.xap**.
3. Välj **OK** när du är klar.


## <a name="step-3---configure-app-information"></a>Steg 3 – Konfigurera appinformation

1. I fönstret **Lägg till app** väljer du filen **Appaket**.
2. I fönstret **Appinformation** konfigurerar du appinformationen. Beroende på vilken app du har valt kan det hända att några av värdena i det här fönstret har fyllts i automatiskt:
    - **Namn** – Ange namnet på appen så som det visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Beskrivning** – Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Ignorera appversion** – Ange **Ja** om appen uppdateras automatiskt av apputvecklaren.
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

1. I fönstret **Lägg till app** kontrollerar du att informationen är rätt konfigurerad.
2. Välj **Lägg till** för att överföra appen till Intune.

## <a name="next-steps"></a>Nästa steg

- Appen som du har skapat visas i applistan. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Mer information finns i [Så här övervakar du appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Mer information finns i [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md)
