---
title: Konfigurationsinställningar för delad Microsoft Intune-enhet för iOS
titlesuffix: ''
description: Läs om de Microsoft Intune-inställningar du kan använda för att visa information på iOS-enhetens låsskärm.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73c4f96e3057227bc601175c4e8f42802eb322bc
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Den delade enhetens konfigurationsinställningar för att visa meddelanden på iOS-enhetens låsskärm

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Den här artikeln beskriver de Microsoft Intune-inställningar du kan använda för att visa information på iOS-enhetens låsskärm.

Med konfigurationsinställningarna för den delade enheten kan du ange valfri text som ska visas i inloggningsfönstret och på låsskärmen. Du kan t.ex. skriva ett meddelande av typen ”Upphittad enhet återlämnas till” och resurstagginformation. 

>[!IMPORTANT]
> Den här funktionen stöds för övervakade enheter som kör iOS 9.3 och senare.

## <a name="create-shared-device-settings"></a>Skapa inställningar för delade enheter

1. Från [Intune i Azure Portal](https://portal.azure.com) går du till [**Enhetsfunktioner** i enhetens konfigurationsområde](device-features-configure.md). 
1. I fönstret **Enhetsfunktioner** väljer du **Konfiguration för delad enhet (endast övervakat)**.
2. I fönstret **Konfiguration för delad enhet (endast övervakat)** konfigurerar du följande inställningar:
    - **Resurstagginformation** – Ange information om resurstaggen för enheten. Exempelvis: **Ägs av Contoso Corp**. Den information som du anger tillämpas på alla enheter som du tilldelar den här profilen till.
    - **Fotnot på låsskärmen** – Ange en kommentar som kan hjälpa dig att få tillbaka enheten om den tappas bort eller blir stulen. Exempelvis: **Ring ”telefonnummer” om du hittar denna**.
3. När du är klar väljer du **OK** tills du kommer tillbaka till fönstret **Skapa profil**. Välj sedan **Skapa**. 


## <a name="next-steps"></a>Nästa steg

Du kan nu tilldela enhetsprofilen till de grupper som du väljer. Mer information finns i [Hur du tilldelar enhetsprofiler](device-profile-assign.md).
