---
title: "Lägg till inbyggda appar på mobila enheter med Intune"
titlesuffix: Azure portal
description: "Så här använder du Intune för att underlätta installation av inbyggda appar på mobila enheter."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 90bec6442084e46f499c57cf128e6ef57fe1ce9c
ms.sourcegitcommit: 0a5f424a8f683daa919b13b5c363173040d561c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-add-built-in-apps-to-microsoft-intune"></a>Så här lägger du till inbyggda appar i Microsoft Intune

Den **inbyggda** apptypen gör det enkelt att tilldela granskade och hanterade appar som till exempel Office 365-appar till iOS- och Android-enheter. Du kan tilldela specifika appar för den här apptypen, till exempel Excel, Power BI, SharePoint, Teams, OneDrive, Outlook, Skype med mera. När du lagt till en app visas apptypen antingen som **Inbyggd iOS-app** eller **Inbyggd Android-app**. Du kan välja vilken av dessa specifika appar du vill publicera till enhetsanvändare genom att använda den inbyggda apptypen.

 I tidigare versioner av Intune-konsolen tillhandahöll Intune flera hanterade Office 365-appar som standard, till exempel Outlook och OneDrive. Apptypen för dessa hanterade appar har taggats som ”Hanterad iOS Store-app” eller ”Hanterad Android-app”. Vi rekommenderar att du använder de inbyggda apptyperna i stället för ”Hanterad iOS Store” eller ”Hanterad Android-app” eftersom de inbyggda apptyperna ger ytterligare flexibilitet för att redigera och ta bort Office 365-appar.

>[!NOTE]
>Standard-Office 365-appar som taggats som ”Hanterad iOS Store” och ”Hanterad Android-app” tas bort från listan över appar när alla tilldelningar har tagits bort för den här appen.

## <a name="add-built-in-app"></a>Lägg till inbyggd app

Med följande steg kan du lägga till en inbyggd app till dina tillgängliga appar i Microsoft Intune.
1.  Logga in på Azure-portalen.
2.  Visa Microsoft Intune-bladet genom att välja **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3.  Välj **Mobilappar** på **Intune**-bladet.
4.  På bladet **Mobilappar** väljer du **Appar** i gruppen **Hantera**.
5.  Välj **Lägg till** för att lägga till en ny app.
6.  Välj **Inbyggd app** från listan **Apptyp** på bladet för att **Lägga till** appar.
7.  Klicka på **Välj app** för att välja de inbyggda appar du vill inkludera.
8.  Välj apparna du vill inkludera på bladet för inbyggda appar.
9.  På bladet **Lägg till app** klickar du på **Lägg till** för att inkludera apparna.


## <a name="configure-app-information"></a>Konfigurera appinformation

Du kan modifiera informationen om den inbyggda appen. Den här informationen hjälper dig att identifiera appen i Intune och hjälper även användarna att hitta appen i appen Företagsportal.
1.  På bladet **Mobilappar – Appar** väljer du den inbyggda app som du vill ändra. Ett blad för den inbyggda appen visas.
2.  Välj alternativet **Egenskaper** från gruppen **Hantera**.
3.  Välj alternativet **Konfigurera** för att ändra informationen om den inbyggda appen.
4.  Du kan ändra följande information på bladet **Appinformation**:
    -   **Namn** – Ange namnet på den inbyggda appen så som det visas på företagsportalen. Kontrollera att alla namn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    -   **Beskrivning** – Ange en beskrivning för appen. 
    -   **Utgivare** – Ange namnet på appens utgivare.
    -   **Kategori** – Valfritt, välj en eller fler av de inbyggda appkategorierna. Om du konfigurerar det här alternativet blir det lättare för användarna att hitta appen när de söker på företagsportalen.
    -   **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    -   **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    -   **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    -   **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    -   **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. Personalavdelningen.
    -   **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    -   **Ladda upp ikon** - Ladda upp en ikon som visas med appen när användare söker i företagsportalen.
3.  När du är klar klickar du på **OK** på bladet **Appinformation**.
4.  Klicka på **Spara** på bladet **Egenskaper**.

## <a name="next-steps"></a>Nästa steg

Nu kan du tilldela apparna till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).
