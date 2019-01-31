---
title: Helskärmsinställningar för Windows- och Holographic-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera enheter med Windows 10 (och senare) samt Windows Holographic for Business med helskärmsläge för en app eller flera appar, anpassa startmenyn, lägg till appar, visa aktivitetsfältet och konfigurera en webbläsare i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: beb1c63e672c08963ba822e6cee2bf8a69456dac
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831351"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>Inställningar för enheter med Windows 10 (och senare) och Windows Holographic for Business som ska köras i dedikerat helskärmsläge med Intune

Använd Intune på Windows 10-enheter att köras som kioskenhet, som ibland kallas dedikerad enhet. En enhet i helskärmsläge kan köra en app eller många appar. Du kan visa och anpassa en startmeny, lägga till olika appar, inklusive Win32-appar, lägga till en viss startsida i en webbläsare och mycket mer. 

Den här funktionen gäller för enheter som kör:

- Windows 10 och senare
- Windows 10 Holographic for Business

Intune stöder en helskärmsprofil per enhet. Om du behöver flera helskärmsprofiler på en enskild enhet, kan du använda en [Anpassad OMA-URI](custom-settings-windows-10.md).

Intune använder ”konfigurationsprofiler” till att skapa och anpassa inställningarna efter din organisations behov. När du har lagt till funktionerna i en profil, skickar eller distribuerar du dessa inställningar till grupperna i din organisation.

Den här artikeln beskriver hur du skapar en enhetskonfigurationsprofil. En lista med alla inställningar och vad de gör finns i [Inställningar för helskärmsläge i Windows 10](kiosk-settings-windows.md) och [Inställningar för helskärmsläge i Windows Holographic for Business](kiosk-settings-holographic.md).

## <a name="create-the-profile"></a>Skapa profilen

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

   - **Namn**: Ange ett beskrivande namn på den nya profilen.
   - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
   - **Plattform**: Välj **Windows 10 och senare**
   - **Profiltyp**: Välj **Helskärmsläge**

4. I **Inställningar** väljer du ett **helskärmsläge**. **Helskärmsläge**: Identifierar den typ av kioskläge som stöds av principen. Alternativen är:

    - **Inte konfigurerat** (standard): Principen aktiverar inte helskärmsläge.
    - **En app, helskärmsläge**: Enhet körs som ett enda användarkonto och låser det till en enda Store-app. När användaren loggar in startar alltså en specifik app. Det här läget gör också att användaren inte kan öppna nya appar eller ändra appen som körs.
    - **Helskärmsläge för flera appar**: Enheten kör flera Store-appar, Win32-appar eller inkorgens Windows-appar med hjälp av ett ID för programanvändarmodell (AUMID). Det är bara de appar som du lägger till som är tillgängliga på enheten.

        Med en kiosk för flera appar, eller en enhet för ett bestämt ändamål, skapas en mer användarvänlig upplevelse för användarna eftersom de endast ser de appar de behöver. Appar som de inte behöver visas inte.

    En lista med alla inställningar och vad de gör finns i:
      - [Inställningar för helskärmsläge i Windows 10](kiosk-settings-windows.md)
      - [Inställningar för helskärmsläge i Windows Holographic for Business](kiosk-settings-holographic.md)

5. När du är klar väljer du **OK** > **Skapa** för att spara dina ändringar. 

Profilen skapas och visas i profillistan. Nu ska du [tilldela](device-profile-assign.md) profilen.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan skapa helskärmsprofiler för enheter som kör följande plattformar:
- [Android](device-restrictions-android.md#kiosk)
- [Android enterprise](device-restrictions-android-for-work.md#kiosk-settings)
- [Windows 10 och senare](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)
