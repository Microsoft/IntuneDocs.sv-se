---
title: Distribuera appar | Microsoft Intune
description: "Ta hjälp av informationen i den här artikeln när du distribuerar appar med Microsoft Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0c6f795031ec23ffe6f332b3510eea43d5fbdbcd
ms.openlocfilehash: 4c9f5b111fbd95f9e1c928cfaaa0c7ebf61dad2a

---
# Distribuera appar i Microsoft Intune

Ta hjälp av informationen i den här artikeln när du distribuerar appar med Microsoft Intune.


## Distribuera en app
I den här proceduren ska du distribuera en app till valda grupper av enheter eller användare.

### Distribuera en app

1. Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och klicka på **Appar** &gt; **Appar** så visas listan över appar som du hanterar.

2.  Välj den app som du vill distribuera och klicka sedan på **Hantera distribution**.

3.  I dialogrutan *&lt;appnamn&gt;* väljer du på sidan **Välj grupper** de användar- eller enhetsgrupper som du vill distribuera appen till.

4.  På sidan **Distributionsåtgärd** konfigurerar du följande:

    - **Godkännande** – Välj inställning för distributionen:
        - **Krävs** (obligatorisk installation)
        - **Tillgänglig** (användarna installerar från företagsportalen på begäran)
        - **Inte tillämpligt** (appen installeras inte och visas inte i företagsportalen)
        - **Avinstallera** (appen avinstalleras från målenheter)
    - **Tidsgräns** – Välj hur snart appen ska distribueras för obligatoriska installationer. Du kan välja bland fördefinierade värden eller välja **Anpassad** om du vill konfigurera en egen tidsgräns.

5. Om appen du distribuerar kan konfigureras med en hanteringsprincip för mobilappar visas sidan **Hantering av mobilappar**. På den här sidan väljer du den hanteringsprincip för mobilprogram som du vill koppla till den här appen.

    [Se vilka Microsoft-appar som är kompatibla med hanteringsprinciper för mobilappar.](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)

6. Om appen du distribuerar är kompatibel med Intune VPN-profiler visas sidan **VPN-profil**. På den här sidan kan du associera iOS-appar med en VPN-profil som du har distribuerat. VPN-anslutningen öppnas automatiskt när appen startas. Om du vill göra en VPN-profil tillgänglig måste den ha profilinställningen **Per app-VPN** aktiverad.
 Information om hur du konfigurerar VPN-profiler, inklusive information om hur du associerar profiler med appar, finns i [VPN-anslutningar i Microsoft Intune](vpn-connections-in-microsoft-intune.md).

## Exempel

I det här exemplet distribuerade du appen som **Tillgänglig** på en iOS-enhet.
Appen visas på användarnas enheter i företagsportalen och användarna kan installera den därifrån.

I den här skärmbilden har till exempel Bing for iOS-appen distribuerats med installationstypen **Extern länk** med en anpassad ikon. Alternativet **Visa den här som en aktuell app och markera den i företagsportalen** har valts.  
![Tillgänglig iOS-app](./media/available-install-on-iOS.png)

Om du har distribuerat appen som **Obligatorisk** till en iOS-enhet får användaren ett meddelande om att en app är redo att installera. I den här skärmbilden har till exempel Work Folders for iOS-appen distribuerats med installationstypen **Hanterad iOS-app från App Store**.
![Obligatorisk iOS-app](./media/iOS-Required-install.PNG)

## Nästa steg

När du har distribuerat en app vill du övervaka dess förlopp. Mer information finns i [Övervaka appar i Microsoft Intune](monitor-apps-in-microsoft-intune.md).



<!--HONumber=Jul16_HO5-->


