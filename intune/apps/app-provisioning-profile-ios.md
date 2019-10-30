---
title: Etableringsprofiler för iOS-appar i Microsoft Intune
titleSuffix: ''
description: Intune innehåller verktyg som proaktivt tilldelar en ny etableringsprofil till enheter som har appar som snart upphör att gälla.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/14/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c0b5f087494e8033cb9645d0a08edd4e1c481a2c
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584926"
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
2. I **Intune**-fönstret väljer du **Klientappar** > **Etableringsprofiler för iOS-app** > **Skapa profil**.
3. På sidan **Grundläggande** lägger du till följande värden:
    - **Namn** – Ange ett namn för den här etableringsprofilen.
    - **Beskrivning** – Om du vill kan du ange en beskrivning av principen.
    - **Ladda upp profilfil** – Välj ikonen **Öppna** och välj sedan en konfigurationsprofilfil för Apple Mobile (med tillägget `.mobileprovision`) som du laddar ned från [webbplatsen för Apple Developer](https://developer.apple.com/).

   **Förfallodatum** fylls i från ett värde i den fil för Apple Mobile-konfigurationsprofil som du lade till ovan.<br>

   <img alt="Create profile - Basics" src="~/apps/media/app-provisioning-profile-ios/app-provisioning-profile-ios-01.png">

4. Klicka på **Nästa: Omfångstaggar**.<br>
   På sidan **Omfångstaggar** kan du välja att konfigurera omfångstaggar för att fastställa vem som kan se etableringsprofilen för iOS-app i Intune. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar för distribuerad IT](../fundamentals/scope-tags.md).
5. Klicka på **Nästa: Tilldelningar**.<br>
   På sidan **Tilldelningar** kan du tilldela profilen till användare och enheter. Lägg märke till att du kan tilldela en profil till en enhet oavsett om enheten hanteras av Intune eller inte.
6. Klicka på **Nästa: Granska och skapa** för att granska de värden som du har angett för profilen.
7. När du är klar klickar du på **Skapa** för att skapa etableringsprofilen för iOS-app i Intune. 

## <a name="next-steps"></a>Nästa steg

Koppla profilen till nödvändiga iOS-enheter. Mer information finns i stegen i [Så här tilldelar du enhetsprofiler](../device-profile-assign.md).
