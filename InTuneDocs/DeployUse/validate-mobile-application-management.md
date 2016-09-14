---
title:
- Verifiera din MAM-konfiguration | Microsoft Intune
description: "Detta avsnitt beskriver hur du kan testa och verifiera om din MAM-princip är korrekt konfigurerad och fungerar som förväntat."
keywords: 
author: karthikaraman
manager: angerobe
ms.date: 08/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41d82597-e13e-4c3e-9151-e71392236ca0
ms.reviewer: joglocke
translationtype: Human Translation
ms.sourcegitcommit: 52d9301f6297065f752cea1dd19024efb11f0730
ms.openlocfilehash: a92334871301523c33f7453038df3ae0fc1fd1a4


---

# Verifiera din konfiguration för hantering av mobilprogram

Det här avsnittet innehåller information om hur du felsöker problem när du har konfigurerat hantering av mobila program (MAM). Dessa anvisningar gäller MAM-principer i Azure Portal.

### Söka efter problem
Det är inte troligt att användarna rapporterar dessa fel eftersom MAM är ett verktyg för att skydda data. Om det finns ett problem med MAM-konfigurationen har användaren obegränsad åtkomst (vilket användaren även skulle ha utan MAM) och användaren är inte medveten om felet. Därför rekommenderar vi att du verifierar din MAM-konfiguration genom att testa MAM-principerna med en liten grupp användare som avsiktligt kan testa MAM-begränsningarna. 


### Vad som ska kontrolleras 

Om testningen visar att MAM-principen inte fungerar som förväntat rekommenderar vi att du kontrollerar följande:

- Är användarna licensierade för MAM?
- Är användarna licensierade för O365?
- Status för användarnas MAM-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**.

#### Användarens MAM-status
1. Välj **Hantering av mobilprogram i Intune** > **inställningar** > **apphantering** > **Alla inställningar** > **Apprapportering av användare** > **användare** i Azure Portal.

2. Välj en användare i listan (eller sök efter och välj en användare) och välj sedan **Välj användare**. Längst upp i kolumnen **Apprapportering** kan du se om användaren är licensierad för MAM. Nedanför det kan du se om användaren är licensierad för O365 och appstatus för alla användarens enheter.

![Appstatus för MAM](..\media\ts-mam-use-apps.png) 

### Vad bör jag göra
Åtgärder som kan vidtas baserat på användarens status:

- Om användaren inte är licensierad för MAM tilldelar du en Intune-licens till användaren enligt beskrivningen i [Hantera Intune-licenser](..\get-started\start-with-a-paid-subscription-to-microsoft-intune).
- Om användaren inte är licensierad för O365 skaffar du en licens för användaren.
- Om en användares app har status **Inte incheckad** kontrollerar du om MAM-principen för appen är korrekt konfigurerad.
- Se till att dessa villkor används för alla användare som du vill att MAM-principerna ska gälla för.

### Se även
[Förbered dig för att konfigurera hanteringsprinciper för mobila appar med Microsoft Intune](..\deploy-use\get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

[Skydda appdata med hanteringsprinciper för mobila appar med Microsoft Intune](..\deploy-use\protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)



<!--HONumber=Aug16_HO5-->


