---
title: "Registrera mobila enheter för utvärdering | Microsoft Intune"
description: "Så här registrerar du mobila enheter och installerar en app när du registrerar dig för en kostnadsfri 30-dagars utvärderingsversion av Intune"
keywords: 
author: lindavr
manager: angrobe
ms.date: 08/09/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 581e880fa4308ec627f5b2c1242fb5b30b713743
ms.openlocfilehash: 7bd5f5d8f4931133a8ef1e697b2fec4cccd07b83


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

## Installera appen som distribuerades tidigare
Öppna företagsportalen på den mobila enheten, välj **Appar**och installera sedan **Microsoft Skype**.

Mer information om hantering av mobila enheter med hjälp av Intune finns i [Dags att registrera enheter i Microsoft Intune](/Intune/deploy-use/prerequisites-for-enrollment).

### Nästa steg
Gratulerar! Du har precis slutfört steg 5 i genomgången av *Microsoft Intune-utvärderingen*.

>[!div class="step-by-step"]

>[&larr; **Skapa principer**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)     [**Alternativ och tillägg** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)  



<!--HONumber=Oct16_HO2-->


