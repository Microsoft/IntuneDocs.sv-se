---
title: "Registrera mobila enheter för utvärdering | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9755499575118feecf33780ee29a70525f95508e
ms.openlocfilehash: f26b64015f483eb5b6a6efbaa6fe6730dde7dac9


---

# Registrera mobila enheter för utvärdering och installera en app
Om du ska konfigurera hantering av mobila enheter med Intune måste du först ange utfärdaren för hantering av mobila enheter, aktivera hantering för enhetsplattformar och sedan registrera enheterna i företagsportalappen. Därefter kan du hämta det Microsoft Skype-program som du har publicerat.

## Förbereda-tjänsten för enhetshantering

1.  **Gör Intune till din utfärdare för hantering av mobila enheter**

    I [Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Admin** &gt; **Hantering av mobila enheter**. Välj **Uppgifter** > **Ange MDM-utfärdare** och välj sedan **Ja** i dialogrutan **MDM-utfärdare**.

2.  **Aktivera MDM för din enhetsplattform**

    Aktivera hantering av mobila enheter för den enhetsplattform som du vill hantera. Beroende på din plattform behövs olika krav:

    -   **iOS och Mac OS X**: Se [Konfigurera iOS- och Mac-hantering med Microsoft Intune](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune).

    -   **Android**: Med mobila Android-enheter kan användarna registrera sig med hjälp av företagsportalappen som finns i Google Play. Det krävs ingen ytterligare konfiguration i Intune.

    -   **Windows Phone**: Se [Konfigurera hantering av Windows Phone med Microsoft Intune](/Intune/Deploy-Use/set-up-windows-phone-management-with-microsoft-intune).

## Registrera testenheter

### iOS och Mac OS X
Installera appen **Microsoft Intune-företagsportal** från Microsoft Corporation som finns på App Store och logga in med den Intune-användarautentisering som lades till ovan. Visa **Registrerade enheter** för att lägga till din enhet.

### Android
Installera appen **Intune-företagsportal** från Microsoft Corporation som finns på [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) och logga in med den Intune-användarautentisering som lades till ovan.

### Windows Phone 8.1
Användarna installerar appen **Företagsportal** från Microsoft Corporation som finns i Windows Phone-butiken och loggar in med Intune-användarautentiseringsuppgifterna som lades till ovan.  Visa **Registrerade enheter** för att lägga till din enhet.

 ### Windows Phone 8.0
 Användare klickar på **Systeminställningar** &gt; **Företagsappar** och loggar in med de Intune-autentiseringsuppgifter som har lagts till ovan. Företagsportalappen distribueras till din telefon.

Om du tillfrågas om en **Serveradress**skriver du manage.microsoft.com.


## Installera appen som distribuerades tidigare
Öppna företagsportalen på den mobila enheten, välj **Appar**och installera sedan **Microsoft Skype**.

Mer information om hantering av mobila enheter med hjälp av Intune finns i [Dags att registrera enheter i Microsoft Intune](/Intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune).

### Nästa steg
Gratulerar! Du har precis slutfört steg 5 i genomgången av *Microsoft Intune-utvärderingen*.

>[!div class="step-by-step"]

>[&larr; **Skapa principer**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)     [**Alternativ och tillägg** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)  



<!--HONumber=Jun16_HO4-->


