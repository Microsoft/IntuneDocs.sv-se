---
title: Inställningar för delade Windows Holographic for Business-enheter – Microsoft Intune – Azure | Microsoft Docs
description: Lägg till och använd Windows Holographic for Business för att konfigurera enheter som är delade eller som används av flera användare i Microsoft Intune. Se en lista över inställningar för kontohantering och vad de gör på enheterna, inklusive Microsoft HoloLens.
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 428025e5e56450fd859f6bf2c9a990cbdca4f263
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835120"
---
# <a name="windows-holographic-for-business-settings-to-manage-shared-devices-using-intune"></a>Windows Holographic for Business-inställningar för hantering av delade enheter med Intune

Windows Holographic for Business-enheter, som Microsoft HoloLens, kan användas av flera användare. Enheter som har flera användare kallas delade enheter och är en del av MDM-lösningar (hantering av mobilenheter).

Med Microsoft Intune kan användare logga in på dessa delade enheter med ett gästkonto. När de använder enheten får de bara åtkomst till funktioner du tillåter.

Den här artikeln listar och beskriver de inställningar du använder i en Windows Holographic for Business-enhetskonfigurationsprofil. När profilen har skapats i Intune distribuerar och tilldelar du sedan profilen till enhetsgrupper i organisationen. Du kan även tilldela profilen till en enhetsgrupp med blandade enhetstyper och OS-versioner.

Mer information om den här funktionen i Intune finns i [Styra åtkomst, konton och energifunktioner på delade datorer eller enheter med flera användare](shared-user-device-settings.md). Mer information om Windows CSP finns i [AccountManagement CSP](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp).

## <a name="before-your-begin"></a>Innan du börjar

[Skapa profilen](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Inställningar för delade enheter med flera användare

> [!NOTE]
> Enheter som kör Windows Holographic for Business, inklusive Microsoft HoloLens, stöder bara inställningarna i **Kontohantering**. Om du konfigurerar några av de andra inställningarna som visas i Intune, till exempel **Läget för delad dator**, har det ingen inverkan på dessa enheter.

- **Kontohantering**: Ange **Aktivera** för att automatiskt ta bort lokala konton skapade av gäster och konton i AD och Azure AD. När en användare loggar ut enheten, eller när systemunderhåll körs, tas dessa konton bort. När alternativet är aktiverat anger du även följande:
  - **Borttagning av konto**: Välj när konton tas bort: **Vid tröskelvärdet för lagringsutrymme**, **Vid tröskelvärdet för lagringsutrymme och tröskelvärdet för inaktivitet** eller **Omedelbart efter utloggning**. Ange även:
    - **Starta borttagning (%)**: Ange ett procenttal (0–100) för diskutrymme. När det totala disk-/lagringsutrymmet sjunker under det värde du anger tas cachelagrade konton bort. Konton tas bort kontinuerligt för att frigöra diskutrymme. Konton som har varit inaktiva längst tas bort först.
    - **Avbryt borttagning (%)**: Ange ett procenttal (0–100) för diskutrymme. När det totala disk-/lagringsutrymmet uppfyller det värde du anger avbryts borttagningen.

  Ange **Inaktivera** för att behålla lokala konton, AD-konton och Azure AD-konton som har skapats av gäster.

  > [!NOTE]
  > Microsoft HoloLens-enheter stöder bara inställningarna i **Kontohantering**.

## <a name="next-steps"></a>Nästa steg

- [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
- Se inställningarna för [Windows 10 och senare](shared-user-device-settings-windows.md).
