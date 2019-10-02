---
title: Etableringsprofiler för iOS-appar i Microsoft Intune
titleSuffix: ''
description: Intune innehåller verktyg som proaktivt tilldelar en ny etableringsprofil till enheter som har appar som snart upphör att gälla.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 624c6cec2a887396cb6ef6508ab26a16d72f8f7c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725328"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Använd etableringsprofilerna för iOS-appar för att förhindra att dina appar upphör att gälla

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

## <a name="introduction"></a>Introduktion

Verksamhetsspecifika Apple iOS-appar som tilldelas till iPhone och iPad skapas med en inbyggd etableringsprofil och kod som signeras med ett certifikat. När appen körs bekräftar iOS appens integritet och tillämpar de principer som definieras av etableringsprofilen. Följande verifieringar görs:

- **Installationsfilens integritet** – iOS jämför appinformationen med företagets offentliga nyckel för signeringscertifikatet. Om de skiljer sig åt kan appinnehållet ha ändrats, och i så fall tillåts inte appen att köras.
- **Funktionstillämpning** – iOS försöker tillämpa appfunktioner från företagsetableringsprofilen (inte enskilda utvecklaretableringsprofiler) i appinstallationsfilen (.ipa).


Signeringscertifikatet du använder för att signera appar gäller normalt i tre år. Däremot upphör etableringsprofilen att gälla efter ett år. Så länge certifikatet är giltigt tillhandahåller Intune verktyg för att tilldela en ny etableringsprofil till enheter som har appar som snart upphör att gälla.
När certifikatet upphör att gälla måste du signera appen igen med ett nytt certifikat och bädda in en ny etableringsprofil med nyckeln för det nya certifikatet.

Som administratör kan du inkludera och undanta säkerhetsgrupper när du tilldelar etableringskonfiguration för iOS-appar. Du kan till exempel tilldela en iOS-app etableringskonfiguration för alla användare, men undanta en exekutiv grupp.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Så här skapar du en etableringsprofil för iOS-mobilappar

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Klientappar** i **Intune**-fönstret.
1. Välj **Hantera** > **Etableringsprofiler för iOS-app** i arbetsbelastningen **Klientappar**.
2. Välj **Skapa profil** i fönstret med profillistan.
3. Ange följande värden i fönstret **Skapa profil**:
    - **Namn** – Ange ett namn för den här etableringsprofilen.
    - **Beskrivning** – Om du vill kan du ange en beskrivning av principen.
    - **Ladda upp profilfil** – Välj ikonen **Öppna** och välj sedan en konfigurationsprofilfil för Apple Mobile (med tillägget `.mobileprovision`) som du laddar ned från [webbplatsen för Apple Developer](https://developer.apple.com/).
4. När du är klar väljer du **Skapa**.

## <a name="next-steps"></a>Nästa steg

Koppla profilen till nödvändiga iOS-enheter. Mer information finns i stegen i [Så här tilldelar du enhetsprofiler](../device-profile-assign.md).
