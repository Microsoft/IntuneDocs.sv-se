---
title: "Inställningar för Intunes webbinnehållsfilter för iOS-enheter"
titlesuffix: Azure portal
description: "Läs om de inställningar du kan använda för att tillåta och blockera åtkomst till webbplatser från iOS-enheter.\""
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 7/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16aa0f3c-8977-4495-9fbe-ca30ad278c9e
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6a2c0fd5de8abcac6b6ac007bb1e393cdfbc116f
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="web-content-filter-settings-for-ios-devices"></a>Inställningar för webbinnehållsfilter för iOS-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd de här inställningarna om du vill konfigurera webbadresser som användarna av webbläsare på iOS-enheter får eller inte får besöka. Du kan konfigurera webbadresser på två sätt:

- **Konfigurera webbadresser** – Använd Apples inbyggda webbfilter som söker efter innehåll som är olämpligt för barn, som t.ex. svordomar eller sexuellt explicit språk. Den här funktionen utvärderar varje webbsida som är inläst och försöker identifiera och blockera olämpligt innehåll. Dessutom kan du konfigurera webbadresser som inte ska kontrolleras av filtret eller webbadresser som alltid ska blockeras, oavsett inställningarna i filtret.

- **Endast vissa webbplatser** (endast för Safari-webbläsaren) – Dessa webbadresser läggs till i Safari-webbläsarens bokmärken. Användaren är **endast** tillåten att besöka dessa webbplatse, inga andra platser kan nås. Använd bara det här alternativet om du vet den exakta listan över webbadresser som kan nås av användarna.
Om du inte anger några webbadresser får användarna inte åtkomst till några webbplatser förutom microsoft.com, microsoft.net och apple.com.



## <a name="get-started"></a>Kom igång

1. På bladet Enhetsfunktioner väljer du **Webbinnehållsfilter (endast övervakat)**.
2. På bladet **Webbinnehållsfilter** väljer du den **Filtertyp** som du vill konfigurera från:
    - **Inte konfigurerat** – Ingen filtrering utförs.
    - **Konfigurera webbadresser**
    - **Endast vissa webbplatser**
3. Därefter, beroende på vilken filtertyp du använder, följer du någon av anvisningarna nedan:


## <a name="configure-urls"></a>Konfigurera webbadresser

1. På bladet **Webbinnehållsfilter** väljer du någon av följande inställningar om det behövs:
    - **Tillåtna webbadresser** – På bladet **Tillåtna webbadresser** anger du de webbadresser som du vill tillåta (och kringgår Apple-webbfiltret). Tryck på returtangenten efter varje.
    - **Blockerade webbadresser** – På bladet **Blockerade webbadresser** anger du de webbadresser som du vill blockera (oavsett inställningarna i Apple-webbfiltret). Tryck på returtangenten efter varje.
2. Klicka på **OK**när du är klar.


## <a name="specific-websites-only"></a>Endast vissa webbplatser

1. På bladet **Webbinnehållsfilter** anger du följande för varje webbplats som du vill tillåta:
    - **Webbadress** – Ange webbadressen till den webbplats som du vill tillåta, till exempel **http://www.contoso.com**.
    - **Bokmärkessökväg** – Ange sökvägen där du vill lagra bokmärket, till exempel **/Contoso/Affärsappar**. Om du inte lägger till någon sökväg läggs bokmärket till i standardmappen för bokmärken på enheten.
    - **Rubrik** – Ange en beskrivande rubrik för bokmärket.
2. Klicka på **Lägg till** när du har angett informationen för varje webbplats.
3. Klicka på **OK**när du är klar.

>[!IMPORTANT] 
> Följande webbadresser tillåts automatiskt av Intune.
> - www.microsoft.com
> - www.microsoft.net
> - www.apple.com

## <a name="finish-up"></a>Slutför

Välj **OK** för att återgå till bladet **Skapa profil** och välj sedan **Skapa**.

## <a name="next-steps"></a>Nästa steg

Du kan nu tilldela enhetsprofilen till de grupper som du väljer. Mer information finns i [Hur du tilldelar enhetsprofiler](device-profile-assign.md).
