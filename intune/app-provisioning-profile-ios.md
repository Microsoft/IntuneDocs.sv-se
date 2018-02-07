---
title: Appetableringsprofiler
titlesuffix: Azure portal
description: "Intune ger dig verktyg för att proaktivt tilldela en ny etableringsprofil till enheter som har appar som snart går ut.”"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 05/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 96ae009abe8d8351052ede4efca779add01dc335
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="use-ios-mobile-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Använd etableringsprofilen för iOS för att förhindra att dina appar upphör att gälla

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>Introduktion

Verksamhetsspecifika Apple iOS-appar som tilldelas till iPhone och iPad skapas med en inbyggd etableringsprofil och kod som signeras med ett certifikat. När appen körs bekräftar iOS appens integritet och tillämpar de principer som definieras av etableringsprofilen. Följande verifieringar görs:

- **Installationsfilens integritet** – iOS jämför appinformationen med företagets offentliga nyckel för signeringscertifikatet. Om de skiljer sig åt kan appinnehållet ha ändrats, och därmed tillåts inte appen att köras.
- **Funktionstillämpning** – iOS försöker tillämpa appfunktioner från företagsetableringsprofilen (inte enskilda utvecklaretableringsprofiler) i appinstallationsfilen (.ipa).


Signeringscertifikatet du använder för att signera appar gäller normalt i tre år. Däremot upphör etableringsprofilen att gälla efter ett år. Så länge certifikatet är giltigt tillhandahåller Intune verktyg för att tilldela en ny etableringsprofil till enheter som har appar som snart upphör att gälla.
När certifikatet upphör att gälla måste du signera appen igen med ett nytt certifikat och bädda in en ny etableringsprofil med nyckeln för det nya certifikatet.


## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Så här skapar du en etableringsprofil för iOS-mobilappar

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning +hantering** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.
1.  Välj **Hantera** > **Etableringsprofiler för iOS** i arbetsbelastningen **Mobilappar**.
2.  Välj **Skapa profil** på bladet med listan över profiler.
3. Ange följande värden på bladet **Skapa profil**:
    - **Namn** – Ange ett namn för den här etableringsprofilen.
    - **Beskrivning** – Om du vill kan du ange en beskrivning av principen.
    - **Ladda upp profilfil** – Välj **Importera** och välj sedan en Apple Mobile-konfigurationsprofilfil (med tillägget **.mobileprovision**) som du laddat ned från webbplatsen Apple Developer.
4. När du är klar väljer du **Skapa**.

## <a name="next-steps"></a>Nästa steg

Koppla profilen till nödvändiga iOS-enheter. Mer information finns i stegen i [Så här tilldelar du enhetsprofiler](device-profile-assign.md).
