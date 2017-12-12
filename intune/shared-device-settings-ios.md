---
title: "Konfigurationsinställningar för delad Intune-enhet för iOS"
titlesuffix: Azure portal
description: "Läs om de Intune-inställningar du kan använda för att visa information på iOS-enhetens låsskärm.”"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1f9256594493aeebda9ab65e3df269ea7acaca5b
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2017
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Den delade enhetens konfigurationsinställningar för att visa meddelanden på iOS-enhetens låsskärm

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med konfigurationsinställningarna för den delade enheten kan du ange valfri text som ska visas i inloggningsfönstret och på låsskärmen. Du kan t.ex. skriva ett meddelande av typen ”Upphittad enhet återlämnas till” och resurstagginformation. 

>[!IMPORTANT]
> Den här funktionen stöds för övervakade enheter som kör iOS 9.3 och senare.

## <a name="create-shared-device-settings"></a>Skapa inställningar för delade enheter

1. På bladet **Enhetsfunktioner** väljer du **Konfiguration för delad enhet (endast övervakat)**.
2. På bladet **Konfiguration för delad enhet (endast övervakat)**, konfigurerar du följande inställningar:
    - **Resurstagginformation** – Ange information om resurstaggen för enheten. Exempelvis: **Ägs av Contoso Corp**. Den information som du anger tillämpas på alla enheter som du tilldelar den här profilen till.
    - **Fotnot på låsskärmen** – Ange en kommentar som kan hjälpa dig att få tillbaka enheten om den tappas bort eller blir stulen. Exempelvis: **Ring ”telefonnummer” om du hittar denna**.
3. När du är klar väljer du **OK** tills du kommer tillbaka till bladet **Skapa profil**. Välj sedan **Skapa**. 


## <a name="next-steps"></a>Nästa steg

Du kan nu tilldela enhetsprofilen till de grupper som du väljer. Mer information finns i [Hur du tilldelar enhetsprofiler](device-profile-assign.md).
