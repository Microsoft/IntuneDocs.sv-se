---
title: Distribuera appar | Microsoft Intune
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c95a776e79cf3e1c7009d6e27f8f50482434d298
ms.openlocfilehash: 46562ed3463c4a23a511eb5c7f28a0b11e84f421

---
# Distribuera appar i Microsoft Intune

Använd informationen i den här artikeln som hjälp för att planera användning av Microsoft Intune-appar.


## Distribuera en app
I den här proceduren ska du distribuera appen till valda enheter eller användare.

### Distribuera en app

1. Gå till [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) och klicka på **Appar** &gt; **Appar** så visas listan över appar som du hanterar.

2.  Välj den app som du vill distribuera och klicka sedan på **Hantera distribuering**.

3.  I dialogrutan *&lt;appnamn&gt;* väljer du först på sidan **Välj grupper** de användar- eller enhetsgrupper som du vill distribuera appen till.

4.  På sidan **Distributionsåtgärd** konfigurerar du följande:

    - **Godkännande** – Välj inställning för distributionen:
        - **Krävs** (obligatorisk installation)
        - **Tillgänglig** (användarna installerar från företagsportalen på begäran)
        - **Inte tillämpligt** (appen installeras inte och visas inte i företagsportalen)
        - **Avinstallera** (appen avinstalleras från målenheter).
    - **Tidsgräns** – Välj hur snart appen ska distribueras för obligatoriska installationer. Du kan välja bland fördefinierade värden eller välja **Anpassad** om du vill konfigurera en egen tidsgräns.

5. Om appen du distribuerar kan konfigureras med en hanteringsprincip för mobilappar visas sidan **Hantering av mobilappar**. På den här sidan väljer du den hanteringsprincip för mobilprogram som du vill koppla till den här appen.

    [Se vilka Microsoft-appar som är kompatibla med hanteringsprinciper för mobilappar.](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)

6. Om appen du distribuerar är kompatibel med Intune VPN-profiler visas sidan **VPN-profil**. På den här sidan kan du associera iOS-appar med en VPN-profil som du har distribuerat. VPN-anslutningen kommer att öppnas automatiskt när appen har startats. Om du vill göra en VPN-profil tillgänglig måste den ha profilinställningen **Per app-VPN** aktiverad.
 Information om hur du konfigurerar VPN-profiler, inklusive stöd för att associera profiler till appar, finns i [Hjälp användarna att ansluta till sitt arbete med hjälp av VPN-profiler med Microsoft Intune](vpn-connections-in-microsoft-intune.md).

## Exempel

I det här exemplet distribuerade du appen som **Tillgänglig** på en iOS-enhet.
Appen visas i företagsportalen på användarnas enheter och de kan installera appen därifrån. I den här skärmbilden har till exempel Bing for iOS-appen distribuerats med installationstypen **Extern länk**, med en anpassad ikon, och alternativet **Visa den här som en aktuell app och markera den i företagsportalen** har valts.
    ![Tillgänglig iOS-app](./media/available-install-on-iOS.png)

Om du har distribuerat appen som **Obligatorisk** till en iOS-enhet får användaren ett meddelande om att en app är redo att installera. I den här skärmbilden har till exempel Work Folders for iOS-appen distribuerats med installationstypen **Hanterad iOS-app från App Store**.
    ![Obligatorisk iOS-app](./media/iOS-Required-install.PNG)

## Nästa steg

När du har distribuerat en app vill du övervaka dess förlopp. Mer information finns i [Övervaka appar i Microsoft Intune](monitor-apps-in-microsoft-intune.md).



<!--HONumber=Jun16_HO4-->


