---
title: "Konfigurationsinställningar för delad Intune-enhet för iOS"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs om de Intune-inställningar du kan använda för att visa information på iOS-enhetens låsskärm."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 4/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 2bc107054f438d5ed72de87dec85900f871c0acc
ms.lasthandoff: 04/19/2017


---

# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Den delade enhetens konfigurationsinställningar för att visa meddelanden på iOS-enhetens låsskärm

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Med konfigurationsinställningarna för den delade enheten kan du ange valfri text som ska visas i inloggningsfönstret och på låsskärmen (t.ex. ett ”Upphittad enhet återlämnas till”-meddelande och resurstagginformation). 

>[!IMPORTANT]
> Den här funktionen stöds för övervakade enheter som kör iOS 9.3 och senare.

1. På bladet **Enhetsfunktioner** väljer du **Konfiguration för delad enhet (endast övervakat)**.
2. På bladet **Konfiguration för delad enhet (endast övervakat)**, konfigurerar du följande:
    - **Resurstagginformation** – Ange information om resurstaggen för enheten. Exempelvis: **Ägs av Contoso Corp**. Den information som du anger kommer att tillämpas på alla enheter som du tilldelar den här profilen till.
    - **Fotnot på låsskärmen** – Ange en kommentar som kan hjälpa dig att få tillbaka enheten om den tappas bort eller blir stulen. Exempelvis: **Ring ”telefonnummer” om du hittar denna**.
3. När du är klar väljer du **OK** tills du kommer tillbaka till bladet **Skapa profil**. Välj sedan **Skapa**. 

