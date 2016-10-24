---
title: Registrera mobila enheter och installera en app | Microsoft Intune
description: "Beskriver hur du registrerar mobila enheter och installerar en app på en enhet som registrerats i Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3306d772b074ddcfd1bfcf7178b32f9b371321e7
ms.openlocfilehash: f57728bb41b750f53b021bed532de18187e764a0


---

# Registrera mobila enheter och installera en app
Om du ska konfigurera hantering av mobila enheter med Intune måste du först ange utfärdaren för hantering av mobila enheter, aktivera hantering för enhetsplattformar och sedan registrera enheterna i företagsportalappen. Därefter kan du distribuera Microsoft Skype-programmet som du publicerade i steg 6.

## Aktivera enhetshantering och registrera enheter

1.  **Gör Intune till din utfärdare för hantering av mobila enheter** I [Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Admin** > **Hantering av mobila enheter** och väljer sedan **Ange utfärdare för Hantering av mobila enheter** under **Uppgifter**.  Klicka på **Ja** i dialogrutan Ange utfärdare för Hantering av mobila enheter.
    ![Administrationskonsolen. Ange MDM till Intune](./media/mdmAuthority.png)

2.  **Aktivera MDM för din enhetsplattform** Aktivera hantering av mobila enheter för den enhetsplattform som du vill hantera. Beroende på din plattform behövs olika krav:

    -   **iOS och Mac OS X**: Se [Konfigurera iOS- och Mac-hantering med Microsoft Intune](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).

    -   **Windows Phone**: Se [Konfigurera hantering av Windows Phone med Microsoft Intune](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune).

    -   **Android**: Med mobila Android-enheter kan användarna registrera sig med hjälp av företagsportalappen som finns i [Google Play](https://play.google.com/store/apps/details?id=com.skype.raider). Det krävs ingen ytterligare konfiguration i Intune.

3.  **Registrera enheter**

    -   **Android** – Installera appen **Intune-företagsportal** från Microsoft Corporation som finns i [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) och logga in med användarautentiseringen för Intune som lades till ovan.

    -   **iOS och Mac OS X** – Installera appen **Microsoft Intune-företagsportal** från Microsoft Corporation som finns i App Store och logga in med Intune-användarautentiseringsuppgifterna som lades till ovan. Visa **Registrerade enheter** för att lägga till din enhet.

    -   **Windows Phone 8.1** – Användarna installerar appen **Företagsportal** från Microsoft Corporation som finns i Windows Phone-butiken och loggar in med Intune-användarautentiseringsuppgifterna som lades till ovan.  Visa **Registrerade enheter** för att lägga till din enhet.

    -   **Windows Phone 8.0** – Användarna väljer **systeminställningar** &gt; **företagsappar**, och loggar in med de Intune-autentiseringsuppgifter som lades till ovan. Företagsportalappen distribueras till din telefon.

    Om du tillfrågas om en **Serveradress**skriver du manage.microsoft.com.

## Installera en app på en registrerad enhet
I [steg 6](start-with-a-paid-subscription-to-microsoft-intune-step-6.md) i den här snabbstartsguide publicerade du Skype-appen till din anpassade Intune-användargrupp. Nu ska du installera appen på en nyligen registrerad enhet.

Öppna Företagsportalen på den registrerade mobila enheten, välj **appar** och installera sedan **Microsoft Skype**.

Se [Krav för att registrera enheter i Microsoft Intune](/intune/deploy-use/prerequisites-for-enrollment) för att läsa mer om hantering av mobila enheter med hjälp av [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].


### Nästa steg
Gratulerar! Du har slutfört det sista steget i *snabbstartsguiden för Intune*. Nu när den första konfigurationen är klar kan du välja att aktivera ytterligare MDM-funktioner.

>[!div class="step-by-step"]

>[&larr; **Registrera enheter**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md) [**Åtgärder efter konfigurering** &rarr;](.\post-configuration-tasks.md)  



<!--HONumber=Oct16_HO3-->


