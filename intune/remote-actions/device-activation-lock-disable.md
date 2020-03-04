---
title: Kringgå iOS/iPadOS-aktiveringslås med Intune
titleSuffix: Microsoft Intune
description: Läs om hur du använder Intune för att kringgå iOS/iPadOS-aktiveringslåset och få åtkomst till låsta enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af5bb1c95a15a5c52585278605e2f7a86307cb76
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782219"
---
# <a name="disable-activation-lock-on-supervised-iosipados-devices-with-intune"></a>Inaktivera aktiveringslåset på övervakade iOS/-enheter med Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune kan hjälpa dig att hantera iOS/iPadOS-aktiveringslåset, en funktion i appen Hitta min iPhone för enheter med iOS/iPadOS 8.0 och senare. Aktiveringslås aktiveras automatiskt när en användare öppnar appen Hitta min iPhone på en enhet. När den har aktiverats måste användarens Apple-ID och lösenord anges innan någon kan:

- Inaktivera Hitta Min iPhone
- Rensa enheten
- Återaktivera enheten

## <a name="how-activation-lock-affects-you"></a>Hur du påverkas av aktiveringslås

Även om aktiveringslås hjälper till att skydda iOS/iPadOS-enheter och förbättra chansen att få tillbaka en borttappad eller stulen enhet, så gör den här funktionen att du som IT-administratör står inför ett antal utmaningar. Exempel:

- En användare ställer in aktiveringslås på en enhet. Användaren lämnar sen företaget och lämnar tillbaks enheten. Utan användarens Apple-ID och lösenord går det inte att återaktivera enheten.
- Du behöver en rapport med alla enheter som har aktiveringslås aktiverat.
- Du vill omtilldela några enheter till en annan avdelning under en enhetsuppdatering i organisationen. Du kan bara omtilldela enheter som inte har aktiveringslås aktiverat.

I syfte att bidra till att lösa de här problemen, så introducerade Apple med iOS/iPadOS 7.1 funktionen Inaktivera aktiveringslås. Inaktivera aktiveringslås gör det möjligt att ta bort aktiveringslås från övervakade enheter utan att ha användarens Apple-ID och lösenord. Övervakade enheter kan generera en enhetsspecifik kod för att kringgå aktiveringslåset, vilken lagras på Apples aktiveringsserver.

>[!TIP]
>Övervakat läge för iOS/iPadOS-enheter gör att du kan använda Apple Configurator för att låsa en enhet och begränsa funktionerna till specifika företagsändamål. Övervakat läge används endast för företagsägda enheter.

Du kan läsa mer om aktiveringslåset på [Apples webbplats](https://support.apple.com/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>Hur Intune hjälper dig att hantera aktiveringslås
Intune kan begära status för aktiveringslåset för övervakade enheter som kör iOS/iPadOS 8.0 och senare. Enbart för övervakade enheter kan Intune hämta koden för att inaktivera aktiveringslåset och skicka den direkt till enheten. Om enheten har rensats kan du få åtkomst till den direkt genom att använda ett tomt användarnamn och koden som lösenord.

**Affärsfördelarna med att använda Intune för att hantera aktiveringslås är:**

- Användaren får säkerhetsfördelarna i Hitta Min iPhone-appen.
- Du kan låta användarna sköta sitt arbete och samtidigt vara säker på att du kan avaktivera eller låsa upp en enhet när den behöver återanvändas.

## <a name="before-you-start"></a>Innan du börjar
Innan du kan inaktivera aktiveringslåset på enheter måste du aktivera det genom att följa dessa anvisningar:

1. Konfigurera en Intune-begränsningsprofil för iOS/iPadOS med hjälp av informationen i [Så här konfigurerar du inställningar för enhetsbegränsning](/intune-azure/configure-devices/how-to-configure-device-restrictions).
2. I [inställningarna för enhetsbegränsningar för iOS/iPadOS](../configuration/device-restrictions-ios.md) under de **allmänna** inställningarna aktiverar du alternativet **Aktiveringslås**.
3. Spara profilen och [tilldela den](../configuration/device-profile-assign.md) till de enheter som du vill ska hantera Inaktivera aktiveringslås.


## <a name="how-to-use-disable-activation-lock"></a>Så här använder du Inaktivera aktiveringslås

>[!IMPORTANT]
>När du har inaktiverat aktiveringslåset på en enhet aktiveras ett nytt aktiveringslås automatiskt om appen Hitta min iPhone startas. Därför **bör du ha fysisk tillgång till enheten innan du följer den här proceduren**.

Intunes fjärråtgärd **Inaktivera aktiveringslås** tar bort aktiveringslåset från en iOS/iPadOS-enhet utan att kräva användarens Apple-ID och lösenord. När du har inaktiverat aktiveringslåset aktiverar enheten aktiveringslåset igen när appen Hitta Min iPhone startas. Inaktivera endast aktiveringslåset om du har fysisk åtkomst till enheten.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. På bladet **Intune** väljer du **Enheter**.
4. På bladet **Enheter** väljer du **Alla enheter**.
5. I listan över enheter som du hanterar väljer du fjärråtgärden **Inaktivera aktiveringslås** för enheten.
6. Gå till enhetens maskinvaruavsnitt och kopiera sedan värdet **Kod för att kringgå aktiveringslås** under **Villkorlig åtkomst**.

    >[!NOTE]
    >Kopiera koden för att kringgå innan du rensar enheten. Om du återställer enhetsinställningarna innan du har kopierat koden tas koden bort från Azure.

7. Gå till bladet **Översikt** för enheten och välj sedan **Rensa**.
8. När enheten har återställts uppmanas du att ange *Apple-ID* och *lösenord*. Lämna fältet *ID* tomt och ange sedan den **koden för att kringgå** för *lösenordet*. Detta tar bort kontot från enheten. 


## <a name="next-steps"></a>Nästa steg

Du kan kontrollera status för upplåsningsbegärandet på informationssidan för enheten i arbetsbelastningen **Hantera enheter**.
