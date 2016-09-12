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
ms.assetid: 40262e47-1ab4-437d-8ca5-c89b5022f91f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: 6fc98df3df19e8858e60427f3b0bfd44c4f4b17d
ms.openlocfilehash: dbdd2649ed565efffe50916c1dd661aac2ed38d8


---
# Välj hur du vill registrera mobila enheter

Dina svar på dessa frågor hjälper dig att avgöra den bästa registreringsmetoden för de enheter som du hanterar.

## **Hur ska du hantera dedikerade företagsägda enheter?**

  > [!div class="button"]
[iOS DEP >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)   [iOS installationsassistent >](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Tagga med IMEI >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  Du kan registrera företagsägda enheter med särskilda användare på följande sätt:

  - **Apples enhetsregistreringsprogram (DEP)** – Köpta eller hanterade iOS-enheter med DEP kan vara mål för en registreringsprofil. När användarna sätter på sina enheter för första gången laddar enheten ned DEP-profilen och registreras i Intune.

  - **Apple Configurator på en Mac** – Apple Configurator är ett Apple-program som körs på en Mac-dator. Du kan ansluta dina iOS-enheter till Mac-datorn med en USB-kabel för att installera en registreringsprofil på enheten. Om du inte kan återställa fabriksinställningarna på enheterna kan du registrera dem med hjälp av installationsassistentläget.

  - **Tagga med IMEI-nummer** – Genom att importera IMEI-numren (International Mobile Equipment Identity) för de företagsägda enheterna kan du tagga dem som företagsägda enheter i Intune. Detta är det enda sättet på vilket du an identifiera dedikerade ("enanvändarläge") Windows- och Android-enheter (i ”enandvändarläge”) som företagsägda. iOS-enheter som inte har registreras med Apples enhetsregistreringsprogram eller Apple Configurator kan även taggas med IMEI-nummer. När du har fördeklarerat enheten så att den taggas som företagsenhet kan du distribuera enheterna till användarna. Användarna kan sedan registrera sina enheter som dedikerade enheter genom att installera företagsportalen så att du får åtkomst till företagsresurser som e-post, appar och data.

  > [!div class="button"]
  [< Bakåt](choose-how-to-enroll-devices3.md)



<!--HONumber=Aug16_HO4-->


