---
title: Använd en PIN-kod för att logga in på Windows 10-enheter med Microsoft Intune – Azure | Microsoft Docs
description: Använd Windows Hello för företag så att användarna kan logga in på enheter med hjälp av en PIN-kod, ett fingeravtryck med mera. Skapa en profil för identitetskyddskonfiguration i Intune för Windows 10-enheter med de här inställningarna och tilldela profilen till användargrupper och enhetsgrupper.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4f5d3a232cab25c60189132732a0ea3f347c74a
ms.sourcegitcommit: 107fef144013b01ed768ca8973373f9cb3f0f7dc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2020
ms.locfileid: "75683807"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>Använd Windows Hello för företag på Windows 10 på enheter med Microsoft Intune

Windows Hello för företag är en metod för att logga in till Windows-enheter genom att ersätta lösenord, smartkort och virtuella smartkort. Intune innehåller inbyggda inställningar så att administratörer kan konfigurera och använda Windows Hello för företag. Du kan till exempel använda dessa inställningar för att:

- Aktivera Windows Hello för företag för registrerade enheter och användare
- Ange enhetskrav för PIN-kod, inklusive en minsta eller längsta PIN-kodslängd
- Tillåta gester, till exempel ett fingeravtryck, som användare kan (eller inte kan använda) för att logga in på enheter

Den här funktionen gäller för enheter som kör:

- Windows 10 och senare
- Windows 10 Mobil
- Windows 10 Holographic for Business

Intune använder ”konfigurationsprofiler” till att skapa och anpassa inställningarna efter din organisations behov. När du har lagt till dessa funktioner i en profil, push-överför eller distribuerar du dessa inställningar till användare och enhetsgrupper i din organisation.

Den här artikeln beskriver hur du skapar en enhetskonfigurationsprofil. En lista över alla inställningar och vad de gör finns i [Enhetsinställningar för Windows 10 för att aktivera Windows Hello för företag](identity-protection-windows-settings.md).

## <a name="create-the-device-profile"></a>Skapa enhetsprofilen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.

3. Ange följande egenskaper:

   - **Namn**: Ange ett beskrivande namn på den nya profilen.
   - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
   - **Plattform**: Välj **Windows 10 och senare**. Windows Hello för företag stöds endast stöds på enheter som kör Windows 10 och senare.
   - **Profiltyp**: Välj **Identitetsskydd**.

4. Konfigurera följande alternativ i fönstret *Windows Hello för företag*:

   - **Konfigurera Windows Hello för företag**: Välj hur du vill konfigurera Windows Hello för företag:

     - **Inte konfigurerat** (standard): [Etablerar Windows Hello för företag](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) på enheten. När du tilldelar profiler för identitetsskydd till endast användare blir enhetskontext som standard **Inte konfigurerad**.

     - **Inaktiverad**: Välj det här alternativet om du inte vill använda Windows Hello för företag. Det här alternativet inaktiverar Windows Hello för företag för alla användare.

     - **Aktiverad**: Välj det här alternativet för att [etablera](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) och konfigurera Windows Hello för företag-inställningar i Intune. Ange vilka inställningar som du vill konfigurera. En lista över alla inställningar och vad de gör finns i [Enhetsinställningar för Windows 10 för att aktivera Windows Hello för företag](identity-protection-windows-settings.md).

   - **Använd säkerhetsnycklar för inloggning**: Aktivera säkerhetsnyckeln för Windows Hello som inloggningsinformation för alla datorer i klientorganisationen.

     - **Aktivera**
     - **Ej konfigurerat** (standard)

5. När du är klar väljer du **OK** > **Skapa** för att spara dina ändringar.

Profilen skapas och visas i profillistan. [Tilldela](../configuration/device-profile-assign.md) sedan den här profilen till användar- och enhetsgrupper som uppfyller dina behov.

> [!IMPORTANT]
> Om du vill tillåta att flera användare är etablerade på en enhet anger du att Windows Hello för företag-principen ska tillämpas på enheterna. Om principen endast ska tillämpas på användare kan bara en användare vara etablerad på en enhet.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/identity-protection-configure/disable-android-camera.png)

-->

## <a name="next-steps"></a>Nästa steg

- Se en lista med alla [inställningar och vad de gör](identity-protection-windows-settings.md).
- [Tilldela profilen](../configuration/device-profile-assign.md) och [övervaka dess status](../configuration/device-profile-monitor.md).
