---
title: "Välj hur du vill registrera mobila enheter | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 06/06/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
translationtype: Human Translation
ms.sourcegitcommit: f1dc713099c982d6e32c87b814dd3f55b1656eda
ms.openlocfilehash: 5668a4d8a6cce15446201926b03d71ede174a299


---

# Välj hur du vill registrera mobila enheter

Registrering av mobila enheter är den process som anger smarttelefoner, surfplattor och datorer som ska hanteras i Microsoft Intune. Som administratör måste du bestämma det bästa sättet att registrera enheter baserat på följande:

 -  Ägarskap (personligt kontra företagsägt)
 -  Användning (delad kontra personlig)
 -  Plattform (iOS, Android, Windows Phone, Windows-dator, Mac-dator) – Väljs efter registreringsmetod

Dina svar på följande frågor hjälper dig att avgöra den bästa registreringsmetoden för de enheter som du hanterar.

## **Tar de anställda med sina egna enheter eller tillhandahålls enheter av din organisation?**

  **Enheter som ägs av användare** används på arbetsplatsen enligt principen ”Bring your own device” (BYOD). Även dessa enheter kan registreras och få åtkomst till företagsresurser som e-post, appar, företagsdata och support. **Företagsägda enheter** (Company-owned devices, COD) tillhandahålls av organisationen och används av personalen. Uppfyller ofta ett särskilt behov i verksamheten.
  > [!div class="button"]
  [BYOD-registrering >](#byod-device-enrollment)   [COD-registrering >](#cod-device-enrollment)

### Registrering av BYOD-enheter

Registrering av BYOD-enheter kräver att användarna också installerar Intunes företagsportalapp på sina enheter. De kan sedan starta appen och registrera sig genom att ange autentiseringsuppgifterna för sina arbets- eller skolkonton. Under förutsättning att Intune hittar en licens kopplad till autentiseringsuppgifterna läggs enheten till på Intune-administrationskonsolen, tar emot principer från Intune och beviljas åtkomst till företagets resurser.

**Välj enhetstyp:**
> [!div class="button"]
[Android](..deploy-use/set-up-android-management-with-microsoft-intune) [iOS och Mac](..deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 Mobile och Windows Phone](..deploy-use/set-up-windows-phone-management-with-microsoft-intune) [Windows-datorer](..deploy-use/set-up-windows-device-management-with-microsoft-intune)


### Registrering av COD-enheter

Företagsägda enheter kan registreras för särskilda användare eller delas mellan flera användare.  **Delade enheter** har inte någon särskild användare och är vanligtvis inte konfigurerade för åtkomst till e-post. Exempel är till exempel kioskenheter eller aktivitetsbaserade enheter som användare lånar från en pool vid behov och sedan lämnar tillbaka. Vilka registreringsmetoder som rekommenderas beror på enheternas plattform. **Särskilda enheter** som har utfärdats till enskilda användare måste spåras som företagstillgångar samtidigt som användarna behöver få åtkomst till e-post och data som personliga enheter. Vilka registreringsmetoder som rekommenderas beror på enheternas plattform. [Nästa fråga …](Are your company-owned devices shared or do they have dedicated users?)

## **Är de företagsägda enheterna delade eller har de särskilda användare?**

> [!div class="button"]
[Delad >](#Shared-company-owned-devices)   [Dedikerad >](..deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)


### Delade företagsägda enheter

De här enheterna har inte någon särskild användare och är vanligtvis inte konfigurerade för åtkomst till e-post. Exempel är till exempel kioskenheter eller aktivitetsbaserade enheter som användare lånar från en pool vid behov och sedan lämnar tillbaka. Vilka registreringsmetoder som rekommenderas beror på enheternas plattform.

  - **Windows- och Android-enheter** – En *enhetsregistreringshanterare* är ett Intune-konto som kan användas för att registrera många delade enheter med företagsportalappen.
  > [!div class="button"]
  [Windows >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#shared-ios-device-enrollment)

### Registrering av delade iOS-enheter

Den bästa metoden för att registrera delade företagsägda iOS-enheter beror på hur du vanligen köper in och hanterar enheterna:

  - **Apples enhetsregistreringsprogram (DEP)** – Köpta eller hanterade iOS-enheter med DEP kan vara mål för en registreringsprofil. När användarna sätter på sina enheter för första gången hämtar enheten DEP-profilen och registreras med DEP-profilen
  - **Apple Configurator på en Mac (Mac)** – Apple Configurator är ett Apple-program som körs på en Mac-dator. Du kan ansluta dina iOS-enheter till Mac-datorn med en USB-kabel för att installera en registreringsprofil på enheten. Om du inte kan återställa fabriksinställningarna på enheterna kan du registrera dem med hjälp av installationsassistentläget. Om du inte vill fabriksåterställa enheterna kan du använda Direktregistrering.
  - **Inget av ovanstående** – Om du inte kan eller inte vill använda Apples DEP- eller Apple Configurator-registreringsmetoderna använder du enhetsregistreringshanteraren i Intune.

  **Välj:**
    > [!div class="button"]
     [DEP-registrering >](../deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Mac >](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Direktregistrering >](../deploy-use/ios-direct-enrollment-in-microsoft-intune)  

  > [!div class="button"]
    [DEM-registrering >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

**Enskilda användare** – Företagsägda enheter som har utfärdats till enskilda användare måste spåras som företagstillgångar samtidigt som användarna behöver få åtkomst till e-post och data som personliga enheter. Vilka registreringsmetoder som rekommenderas beror på enheternas plattform.

  - **Windows- och Android-enheter** – Genom att importera IMEI-numren (International Mobile Equipment Identity) för de företagsägda enheterna kan du tagga dem som företagsägda enheter i Intune. Användarna kan sedan registrera sina enheter som personliga enheter genom att installera företagsportalen för att få åtkomst till företagsresurser som e-post, appar och data.
  > [!div class="button"]
  [Tagga med IMEI >](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  - **iOS-enheter** – Delade iOS-enheter kan hanteras på tre sätt.  **Hur ska du registrera dina delade iOS-enheter?**

    - **Apples enhetsregistreringsprogram (DEP)** – Köpta eller hanterade iOS-enheter med DEP kan vara mål för en registreringsprofil. När användarna sätter på sina enheter för första gången hämtar enheten DEP-profilen och registreras enligt profilen.
    > [!div class="button"]
    [DEP-registrering](../deploy-use/ios-device-enrollment-program-in-microsoft-intune).

    - **Apple Configurator på en Mac** – Apple Configurator är ett Apple-program som körs på en Mac-dator. Du kan ansluta dina iOS-enheter till Mac-datorn med en USB-kabel för att installera en registreringsprofil på enheten. Om du inte kan återställa fabriksinställningarna på enheterna kan du registrera dem med hjälp av installationsassistentläget.

    Om du inte vill fabriksåterställa enheterna kan du använda Direktregistrering.
    Om du inte kan återställa fabriksinställningarna på enheterna kan du registrera dem med hjälp av installationsassistentläget.
    > [!div class="button"][iOS Setup Assistant enrollment](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [!div class="button"][iOS direct enrollment](../deploy-use/ios-direct-enrollment-in-microsoft-intune).

    - **Inget av ovanstående** – Om du inte kan eller inte vill använda Apples DEP- eller Apple Configurator-registreringsmetoder genom att importera IMEI-numren (Internationella Mobile Equipment Identity) för de företagsägda enheterna kan du tagga dem som företagsägda enheter i Intune. Användarna kan sedan registrera sina enheter som personliga enheter genom att installera företagsportalen för att få åtkomst till företagsresurser som e-post, appar och data.
    > [!div class="button"][Tag devices with IMEI numbers](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)



<!--HONumber=Jun16_HO5-->


