---
# required metadata

title: Välj hur du vill registrera mobila enheter | Microsoft Intune
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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: damionw
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Välj hur du vill registrera mobila enheter

Registrering av mobila enheter är den process som anger smarttelefoner, surfplattor och datorer som ska hanteras i Microsoft Intune. Som administratör måste du bestämma det bästa sättet att registrera enheter baserat på följande:

 -  Ägarskap (personligt kontra företagsägt)
 -  Användning (delad kontra personlig)
 -  Plattform (iOS, Android, Windows Phone, Windows-dator, Mac-dator)

Dina svar på följande frågor hjälper dig att avgöra den bästa registreringsmetoden för de enheter som du hanterar.

## Tar de anställda med sina egna enheter eller tillhandahålls enheter av din organisation?

  **Användarägda enheter** – BYOD-registrering (Bring your own device) – användare kan installera appen för Intunes företagsportal på sin enhet och sedan registrera sig, få åtkomst till företagsresurser som e-post, företagsappar, företagets data och support.  
  > [!div class = "button"]   [BYOD-registrering >](..deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)

  **Företagsägda enheter** – Företagsägda enheter (COD, Company-owned devices) kan registreras på en rad olika sätt beroende på organisationens behov och vilka typer av enheter som hanteras. Nästa fråga …

## Är de företagsägda enheterna delade eller har de enskilda användare?

**Delade företagsägda enheter** – Dessa enheter har inte en enskild användare och är vanligtvis inte konfigurerade för åtkomst till e-post. Exempel är till exempel kioskenheter eller aktivitetsbaserade enheter som användare hämtar från en pool vid behov och sedan lämnar tillbaka. Vilka registreringsmetoder som rekommenderas beror på enheternas plattform.

  - **Windows- och Android-enheter** – En *enhetsregistreringshanterare* är ett Intune-konto som kan användas för att registrera många delade enheter med företagsportalappen.
  > [!div class="button"]   [Enhetsregistreringshanterare >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **iOS-enheter** – Delade iOS-enheter kan hanteras på tre sätt.  **Hur ska du registrera dina delade iOS-enheter?**

    - **Apples enhetsregistreringsprogram (DEP)** – Köpta eller hanterade iOS-enheter med DEP kan vara mål för en registreringsprofil. När användarna sätter på sina enheter för första gången hämtar enheten DEP-profilen och registreras med DEP-profilen
    > [!div class="button"]     [DEP-registrering >](../deploy-use/ios-device-enrollment-program-in-microsoft-intune)

    - **Apple Configurator på en Mac** – Apple Configurator är ett Apple-program som körs på en Mac-dator. Du kan ansluta dina iOS-enheter till Mac-datorn med en USB-kabel för att installera en registreringsprofil på enheten. Om du inte kan återställa fabriksinställningarna på enheterna kan du registrera dem med hjälp av installationsassistentläget. Om du inte vill fabriksåterställa enheterna kan du använda Direktregistrering.

    > [!div class="button"]     [Installationsassistentläge >](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) eller [Direktregistrering >](../deploy-use/ios-direct-enrollment-in-microsoft-intune)

    - **Inget av ovanstående** – Om du inte kan eller inte vill använda Apples DEP- eller Apple Configurator-registreringsmetoderna använder du enhetsregistreringshanteraren i Intune.
    > [!div class="button"]     [DEP-registrering >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

**Enskilda användare** – Företagsägda enheter som har utfärdats till enskilda användare måste spåras som företagstillgångar samtidigt som användarna behöver få åtkomst till e-post och data som personliga enheter. Vilka registreringsmetoder som rekommenderas beror på enheternas plattform.

  - **Windows- och Android-enheter** – Genom att importera IMEI-numren (International Mobile Equipment Identity) för de företagsägda enheterna kan du tagga dem som företagsägda enheter i Intune. Användarna kan sedan registrera sina enheter som personliga enheter genom att installera företagsportalen för att få åtkomst till företagsresurser som e-post, appar och data.
  > [!div class="button"]   [Tagga med IMEI >](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  - **iOS-enheter** – Delade iOS-enheter kan hanteras på tre sätt.  **Hur ska du registrera dina delade iOS-enheter?**

    - **Apples enhetsregistreringsprogram (DEP)** – Köpta eller hanterade iOS-enheter med DEP kan vara mål för en registreringsprofil. När användarna sätter på sina enheter för första gången hämtar enheten DEP-profilen och registreras enligt profilen.
    > [!div class="button"]     [DEP-registrering](../deploy-use/ios-device-enrollment-program-in-microsoft-intune).

    - **Apple Configurator på en Mac** – Apple Configurator är ett Apple-program som körs på en Mac-dator. Du kan ansluta dina iOS-enheter till Mac-datorn med en USB-kabel för att installera en registreringsprofil på enheten. Om du inte kan återställa fabriksinställningarna på enheterna kan du registrera dem med hjälp av installationsassistentläget.

    Om du inte vill fabriksåterställa enheterna kan du använda Direktregistrering.
    Om du inte kan återställa fabriksinställningarna på enheterna kan du registrera dem med hjälp av installationsassistentläget.
    > [!div class="button"] [iOS-installationsassistentläge](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [!div class="button"][iOS-direktregistrering](../deploy-use/ios-direct-enrollment-in-microsoft-intune).

    - **Inget av ovanstående** – Om du inte kan eller inte vill använda Apples DEP- eller Apple Configurator-registreringsmetoder genom att importera IMEI-numren (Internationella Mobile Equipment Identity) för de företagsägda enheterna kan du tagga dem som företagsägda enheter i Intune. Användarna kan sedan registrera sina enheter som personliga enheter genom att installera företagsportalen för att få åtkomst till företagsresurser som e-post, appar och data. > [!div class="button"][Tagga enheter med IMEI-nummer](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)


<!--HONumber=Jun16_HO1-->


