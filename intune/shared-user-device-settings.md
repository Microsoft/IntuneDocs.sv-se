---
title: Inställningar i Microsoft Intune för delade enheter eller enheter med flera användare – Azure | Microsoft Docs
description: Lägg till och använd Windows 10 och Windows Holographic for Business-enheter som är delade eller som används av flera användare i Microsoft Intune. Se en lista över alla inställningar och vad de gör på enheterna, inklusive Microsoft HoloLens. Kontrollera gästkonton, hantera konton och ta bort inaktiva konton, tillåt eller förhindra att spara i lokal lagring, ange energi- och strömsparalternativ, välj när uppdateringar installeras och använd enheter i utbildningsmiljöer i en enhetskonfigurationsprofil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: cf35d2ab2a1e08591669ef21ed3c24a00076a1ae
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54204953"
---
# <a name="control-access-accounts-and-power-features-on-shared-pc-or-multi-user-devices-using-intune"></a>Kontrollera åtkomst, konton och energifunktioner på delade datorer eller enheter med flera användare med Intune

Enheter som har flera användare kallas delade enheter och är en vanlig del av MDM-lösningar (hantering av mobilenheter). Med Microsoft Intune kan du anpassa delade enheter som kör följande plattformar:

- Windows 10 Professional och senare
- Windows 10 Enterprise och senare
- Windows Holographic for Business, till exempel HoloLens

Till exempel har skolor enheter som normalt används av många elever. Med den här inställningen kan skolans Intune-administratör aktivera delad dator-funktionen för att tillåta en användare åt gången. Elever kan inte växla mellan olika inloggade konton på enheten. När eleven loggar ut väljer du även att ta bort alla användarspecifika inställningar.

Slutanvändare kan logga in på dessa delade enheter med ett gästkonto. När användare loggar in cachelagras autentiseringsuppgifterna. När slutanvändarna använder enheten får de bara åtkomst till funktioner du tillåter. Till exempel väljer du när enheten försätts i strömsparläge, om användarna kan se och spara filer lokalt, att aktivera eller inaktivera energisparfunktioner med mera. Du styr även om gästkontot tas bort när användaren loggar ut eller inaktiva konton tas bort när ett tröskelvärde nås.

Den här artikeln visar hur du skapar en konfigurationsprofil och innehåller länkar till tillgängliga inställningar med deras beskrivningar.

När profilen har skapats i Intune distribuerar och tilldelar du profilen till enhetsgrupper i organisationen. Du kan också tilldela den här profilen till enhetsgrupper med blandade enhetstyper och versioner av operativsystemet (OS).

## <a name="create-the-profile"></a>Skapa profilen

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

   - **Namn**: Ange ett beskrivande namn på den nya profilen.
   - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
   - **Plattform**: Välj **Windows 10 och senare**.
   - **Profiltyp**: Välj **Delad enhet för flera användare**.

4. Konfigurera inställningarna för [Windows 10 och senare](shared-user-device-settings-windows.md) eller [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).

5. Välj **OK** > **Skapa** för att spara ändringarna.

Din profil skapas och visas i listan men den gör ingenting än. Se till att [tilldela profilen](device-profile-assign.md) till enhetsgrupper i din organisation.

## <a name="next-steps"></a>Nästa steg

- Se alla inställningar för [Windows 10 och senare](shared-user-device-settings-windows.md) och [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).
- [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).