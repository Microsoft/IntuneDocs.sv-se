---
title: "Etableringsprofiler för iOS-appar i Microsoft Intune"
titlesuffix: 
description: "Intune ger dig verktyg för att proaktivt tilldela en ny etableringsprofil till enheter som har appar som snart går ut.”"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 87d97ddd4c70236193d4e6bb12ac6d68e4085903
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="use-ios-mobile-provisioning-profiles-in-intune-to-prevent-your-apps-from-expiring"></a>Använd etableringsprofiler för iOS-appar i Intune för att förhindra att dina appar upphör att gälla

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>Introduktion

Verksamhetsspecifika Apple iOS-appar som tilldelas till iPhone och iPad skapas med en inbyggd etableringsprofil och kod som signeras med ett certifikat. När appen körs bekräftar iOS appens integritet och tillämpar de principer som definieras av etableringsprofilen. Följande verifieringar görs:

- **Installationsfilens integritet** – iOS jämför appinformationen med företagets offentliga nyckel för signeringscertifikatet. Om de skiljer sig åt kan appinnehållet ha ändrats, och i så fall tillåts inte appen att köras.
- **Funktionstillämpning** – iOS försöker tillämpa appfunktioner från företagsetableringsprofilen (inte enskilda utvecklaretableringsprofiler) i appinstallationsfilen (.ipa).


Signeringscertifikatet du använder för att signera appar gäller normalt i tre år. Däremot upphör etableringsprofilen att gälla efter ett år. Så länge certifikatet är giltigt tillhandahåller Intune verktyg för att tilldela en ny etableringsprofil till enheter som har appar som snart upphör att gälla.
När certifikatet upphör att gälla måste du signera appen igen med ett nytt certifikat och bädda in en ny etableringsprofil med nyckeln för det nya certifikatet.


## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Så här skapar du en etableringsprofil för iOS-mobilappar

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning + hantering**.
3. Välj **Mobilappar** i **Intune**-fönstret.
1.  Välj **Hantera** > **Etableringsprofiler för iOS-app** i arbetsbelastningen **Mobilappar**.
2.  Välj **Skapa profil** i fönstret med profillistan.
3. Ange följande värden i fönstret **Skapa profil**:
    - **Namn** – Ange ett namn för den här etableringsprofilen.
    - **Beskrivning** – Om du vill kan du ange en beskrivning av principen.
    - **Ladda upp profilfil** – Välj **Importera** och välj sedan en Apple Mobile-konfigurationsprofilfil (med tillägget **.mobileprovision**) som du laddat ned från webbplatsen Apple Developer.
4. När du är klar väljer du **Skapa**.

## <a name="next-steps"></a>Nästa steg

Koppla profilen till nödvändiga iOS-enheter. Mer information finns i stegen i [Så här tilldelar du enhetsprofiler](device-profile-assign.md).
