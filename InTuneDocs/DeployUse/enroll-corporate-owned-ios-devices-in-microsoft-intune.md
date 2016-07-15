---
title: "Registrera företagsägda iOS-enheter i Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ROBOTS: noindex,nofollow
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 48359b44bec9ac3e1c9510debc01d2cf8abf6d2b


---

# Registrera företagsägda iOS-enheter i Microsoft Intune
Microsoft Intune stöder registrering av företagsägda iOS-enheter med hjälp av Apples DEP (Device Enrollment Program) eller verktyget [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) på en Mac-dator.

Du kan registrera företagsregistrerade iOS-enheter på tre sätt:

-   **Registrering av installationsassistenten** – Fabriksåterställer enheten och förbereder den för installation av enhetens nya användare. Den här metoden kräver att administratören ansluter iOS-enheten via USB till en Mac-dator som kör Apple Configurator för att förkonfigurera registreringen. Enheterna levereras sedan till sina användare som kör processen med installationsassistenten, konfigurerar enheten med sina arbets- eller skolautentiseringsuppgifter och slutför registreringsprocessen. [Registrera iOS-enheter med Apple Configurator och installationsassistenten](ios-setup-assistant-enrollment-in-microsoft-intune.md)

-   **Direktregistrering** – Skapar en Apple Configurator-kompatibel fil som används vid förberedelse av enheten. Den registrerade enheten är inte fabriksåterställd, men har ingen anknytning till användaren. Den här metoden kräver att administratören ansluter iOS-enheten via USB till en Mac-dator som kör Apple Configurator för att registrera enheten. [Registrera iOS-enheter som använder direktregistrering i Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md)

-   **Device Enrollment Program (DEP)** – Distribuerar en registreringsprofil ”over-the-air” till enheter som har köpts via Apples enhetsregistreringsprogram. Enheten registreras i Intune när användaren kör installationsassistenten på enheten.  Enheter som har registrerats via DEP kan inte avregistreras av användarna. [Registrera iOS-enheter med Device Enrollment Program](ios-device-enrollment-program-in-microsoft-intune.md)




### Se även
[Dags att registrera enheter i Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


