---
title: Anpassa låsskärmen på iOS-enheter med hjälp av Microsoft Intune – Azure | Microsoft Docs
titlesuffix: ''
description: Läs om de Microsoft Intune-inställningar du kan använda för att visa information på iOS-enhetens låsskärm med hjälp av inställningar för Konfiguration för delad enhet för iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f4d75d795421c761398f349c324b498fd21ca01
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203084"
---
# <a name="add-custom-messages-to-lock-screen-and-login-window-on-ios-devices-using-microsoft-intune"></a>Lägga till anpassade meddelanden på låsskärmen och i inloggningsfönstret på iOS-enheter med hjälp av Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Den här artikeln beskriver de Microsoft Intune-inställningar du kan använda för att visa information på iOS-enhetens låsskärm och inloggningsfönster. 

Använd de här inställningarna för att visa ett anpassat meddelande eller text i inloggningsfönstret och på låsskärmen. Du kan till exempel skriva ett meddelande av typen ”Upphittad enhet återlämnas till...” och resurstagginformation.

Inställningarna har stöd för övervakade enheter som kör iOS 9.3 och senare.

## <a name="create-the-profile"></a>Skapa profilen

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange ett **namn** och en **beskrivning** för profilen.
4. I **Plattform** väljer du **iOS**. I **Profiltyp** väljer du **Enhetsfunktioner**.
5. I **Inställningar** väljer du **Meddelande på låsskärm (endast övervakat)**. Konfigurera följande inställningar:

    - **Resurstagginformation**: Ange information om resurstaggen för enheten. Ange till exempel `123xyz`.

        Den text du anger visas i inloggningsfönstret och på låsskärmen på enheten.

    - **Fotnot på låsskärmen**: Ange en kommentar som kan hjälpa dig att få tillbaka enheten om den tappas bort eller blir stulen. Du kan ange valfri text i fältet. Ange något i stil med `If found, call Contoso at ...`.

    Enhetstoken kan också användas för att lägga till enhetsspecifik information i de här fälten. Ange till exempel `Serial Number: {{serialnumber}}` om du vill visa serienumret. På låsskärmen visas texten ungefär som `Serial Number 123456789ABC`. När du anger variabler ska du använda klammerparenteser `{{ }}`. [Token för appkonfiguration](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) innehåller en lista över variabler som kan användas. Du kan också använda `deviceName` eller andra enhetsspecifika värden.

6. När du är klar väljer du **OK** > **OK** > **Skapa**. Profilen visas i listan.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
