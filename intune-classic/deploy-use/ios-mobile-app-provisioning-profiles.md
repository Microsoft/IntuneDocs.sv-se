---
title: Appetableringsprofiler
description: "Intune tillhandahåller verktyg för att distribuera en ny etableringsprofilprincip till enheter som har appar som snart upphör att gälla."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 86fbe736-7bdb-4f5e-ae21-13c91eb2462c
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fa78cdbe73f2cca1da011836cecacfdd47dc2291
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="use-ios-mobile-provisioning-profile-policies-to-prevent-your-apps-from-expiring"></a>Använd etableringsprofilprinciper för iOS för att förhindra att dina appar upphör att gälla

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Verksamhetsspecifika Apple iOS-appar som distribueras till iPhone och iPad skapas med en inbyggd etableringsprofil och kod som signeras med ett certifikat. När appen körs bekräftar iOS appens integritet och tillämpar de principer som definieras av etableringsprofilen. Följande verifieringar görs:

- **Installationsfilens integritet** – iOS jämför appinformationen med företagets offentliga nyckel för signeringscertifikatet. Om de skiljer sig åt kan appinnehållet ha ändrats, och därmed tillåts inte appen att köras.
- **Funktionstillämpning** – iOS försöker tillämpa appfunktioner från företagsetableringsprofilen (inte enskilda utvecklaretableringsprofiler) i appinstallationsfilen (.ipa).


Signeringscertifikatet du använder för att signera appar gäller normalt i tre år. Däremot upphör etableringsprofilen att gälla efter ett år. Så länge certifikatet är giltigt tillhandahåller Intune verktyg för att distribuera en ny etableringsprofilprincip till enheter som har appar som snart upphör att gälla.
När certifikatet upphör att gälla måste du signera appen igen med ett nytt certifikat och bädda in en ny etableringsprofil med nyckeln för det nya certifikatet.



## <a name="how-to-find-out-when-a-line-of-business-app-will-expire"></a>Så här tar du reda på när en verksamhetsspecifik app upphör att gälla

1. Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och välj **Appar** > **Appar**.
2. I kolumnen **Förfallodatum** i listan med appar kan du se appens förfallodatum. Du kan också välja inställningen **Har upphört att gälla/upphör snart att gälla** i listrutan **Filter** om du bara vill visa appar som du måste vidta åtgärder för.

## <a name="how-to-create-an-ios-mobile-provisioning-profile-policy"></a>Så här skapar du en etableringsprofilprincip för mobila enheter för iOS


1. I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) klickar du på **Princip** > **Översikt** > **Lägg till princip**.
2. Välj **iOS** > **Princip för mobiletableringsprofil** i dialogrutan **Skapa en ny princip** och välj sedan **Skapa princip**.
3. Konfigurera följande värden på sidan **Allmänt**:
    - **Namn** – Ange ett namn för den här etableringsprofilprincipen.
    - **Beskrivning** – Om du vill kan du ange en beskrivning av principen.
    - **Fil för konfigurationsprofil** – Klicka på **Importera** och välj sedan en Apple Mobile-konfigurationsprofilfil (med tillägget **.mobileprovision**) som du laddat ned från webbplatsen Apple Developer.
4. När du är klar väljer du **Spara princip**.
5. Distribuera sedan principen till önskade iOS-enheter. Mer information finns i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
