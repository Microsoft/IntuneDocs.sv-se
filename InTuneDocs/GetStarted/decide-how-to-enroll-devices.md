---
title: "Välj hur du vill registrera mobila enheter | Microsoft Intune"
description: "Bestäm hur du ska registrera mobila enheter i Intune genom att besvara några enkla frågor"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: c671610b9c56d8b92d126d9902cce9c8c689ed63
ms.openlocfilehash: 9f1612ffd9ab85e38058edb09870297a44b37c16


---

# Välj hur du vill registrera mobila enheter

Registrering av mobila enheter är den process som anger smarttelefoner, surfplattor och datorer som ska hanteras i Microsoft Intune. Som administratör måste du bestämma det bästa sättet att registrera enheter baserat på följande:

 -  Ägarskap (personligt kontra företagsägt)
 -  Användning (delad kontra personlig)
 -  Plattform (iOS, Android, Windows Phone, Windows-dator, Mac-dator)

Dina svar på följande frågor hjälper dig att avgöra den bästa registreringsmetoden för de enheter som du hanterar.

## **Tar de anställda med sina egna enheter eller tillhandahålls enheter av din organisation?**

  - **Användarägda enheter** – BYOD-registrering (Bring your own device) – användare kan installera appen för Intunes företagsportal på sin enhet och sedan registrera sig, få åtkomst till företagsresurser som e-post, företagsappar, företagets data och support.  

  - **Företagsägda enheter** – Företagsägda enheter (COD, Company-owned devices) kan registreras på en rad olika sätt beroende på organisationens behov och vilka typer av enheter som hanteras.

> [!div class="button"]
[BYOD-registrering >](#what-byod-devices-can-your-users-enroll)   [COD-registrering >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

## **Vilka egna enheter kan användarna registrera?**

> [!div class="button"]
[Android](/intune/deploy-use/set-up-android-management-with-microsoft-intune) [iOS och Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 Mobile & Windows Phone](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) [Windows-datorer](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)

## **Är de företagsägda enheterna delade eller har de särskilda användare?**

- **Delade företagsägda enheter** – Dessa enheter har inte en enskild användare och är vanligtvis inte konfigurerade för åtkomst till e-post. Exempel är till exempel kioskenheter eller aktivitetsbaserade enheter som användare hämtar från en pool vid behov och sedan lämnar tillbaka. Vilka registreringsmetoder som rekommenderas beror på enheternas plattform.

- **Särskilda användare** – Företagsägda enheter som har utfärdats till enskilda användare måste spåras som företagstillgångar samtidigt som användarna behöver få åtkomst till e-post och data som personliga enheter. Vilka registreringsmetoder som rekommenderas beror på enheternas plattform.

> [!div class="button"]
[Delad >](#what-operating-system-are-your-shared-devices-running)   [Dedikerad >](#how-will-you-manage-dedicated-ios-devices)


## **Vilket operativsystem har dina delade enheter?**

  > [!div class="button"]
  [Windows >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#how-will-you-manage-shared-ios-devices)

## **Hur ska du hantera dina delade iOS-enheter?**

- **Apples enhetsregistreringsprogram (DEP)** – Köpta eller hanterade iOS-enheter med DEP kan vara mål för en registreringsprofil. När användarna sätter på sina enheter för första gången hämtar enheten DEP-profilen och registreras med DEP-profilen

- **Apple Configurator på en Mac** – Apple Configurator är ett Apple-program som körs på en Mac-dator. Du kan ansluta dina iOS-enheter till Mac-datorn med en USB-kabel för att installera en registreringsprofil på enheten. Om du inte kan återställa fabriksinställningarna på enheterna kan du registrera dem med hjälp av installationsassistentläget. Om du inte vill fabriksåterställa enheterna kan du använda Direktregistrering.

- **Hanterare för enhetsregistrering** – Med Intunes enhetsregistreringshanterare (DEM) kan en chef eller administratör registrera många mobila enheter med ett enda användarkonto. Dessa enheter kan inte ha användartillhörighet (d.v.s. särskilda användare) och måste registreras genom att installera och logga in i företagsportalappen.

  > [!div class="button"]
  [DEP-registrering av iOS >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Direktregistrering av iOS >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)  [DEM-registrering >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

## **Hur ska du hantera dina dedikerade iOS-enheter?**

Du kan registrera företagsägda enheter med särskilda användare på följande sätt:

- **Apples enhetsregistreringsprogram (DEP)** – Köpta eller hanterade iOS-enheter med DEP kan vara mål för en registreringsprofil. När användarna sätter på sina enheter för första gången laddar enheten ned DEP-profilen och registreras i Intune.

- **Apple Configurator på en Mac** – Apple Configurator är ett Apple-program som körs på en Mac-dator. Du kan ansluta dina iOS-enheter till Mac-datorn med en USB-kabel för att installera en registreringsprofil på enheten. Om du inte kan återställa fabriksinställningarna på enheterna kan du registrera dem med hjälp av installationsassistentläget.

- **Tagga med IMEI-nummer** – Genom att importera IMEI-numren (International Mobile Equipment Identity) för de företagsägda enheterna kan du tagga dem som företagsägda enheter i Intune. Användarna kan sedan registrera sina enheter som personliga enheter genom att installera företagsportalen för att få åtkomst till företagsresurser som e-post, appar och data.

  > [!div class="button"]
  [Tagga med IMEI >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers) [iOS DEP](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [iOS installationsassistent](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Tagga med IMEI](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)



<!--HONumber=Aug16_HO1-->


