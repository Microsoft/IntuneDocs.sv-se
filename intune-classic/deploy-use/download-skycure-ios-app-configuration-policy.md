---
title: "Hämta konfigurationsprincip för Skycures iOS-app"
description: "Hämta den konfigurationsprincip för Skycures iOS-app som ska användas när Skycure iOS-app distribueras till slutanvändarna."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d211b876-4d3a-473c-999f-843c0a16cd22
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3159985bfbaec40899dd58766e214daa672ee6d4
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="download-skycure-ios-app-configuration-policy"></a>Hämta konfigurationsprincip för Skycures iOS-app

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

##<a name="before-you-begin"></a>Innan du börjar

Du måste logga in på Skycure Management Console för att kunna utföra nästa steg.

> [!TIP] 
> Om du använder Microsoft Internet Explorer 11 eller Edge kan du behöva öppna Skycure Management Console i privat läge.

## <a name="to-download-the-ios-app-configuration-policy"></a>Så här hämtar du konfigurationsprincipen för iOS-appen

1.  Gå till [Skycure Management Console](https://aad.skycure.com).

2.  Ange dina **autentiseringsuppgifter som Skycure-administratör** och klicka sedan på **Fortsätt**.

    ![Inloggning till Skycure Management Console](../media/mtp/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > Skycure-administratörens användarnamn är ett e-postkonto som måste vara ett giltigt användarkonto i Azure Active Directory, annars misslyckas inloggningen. Skycure använder Azure Active Directory för att autentisera sitt administratörsanvändarnamn med enkel inloggning (SSO).

3.  Gå till **Inställningar** &gt; **Integrering med enhetshantering** &gt; **Val av EMM-integrering**, välj **Microsoft Intune** och spara sedan ditt val.

2.  Klicka på länken **Integrering av installationsfiler** och spara den genererade \*ZIP-filen. ZIP-filen innehåller filen **skycure\_configuration.plist**, som används för att skapa iOS-appens konfigurationsprincip i den klassiska Intune-konsolen.

![Skycure integrering, installationsfiler](../media/mtp/skycure-ios-app-2.png)

## <a name="next-steps"></a>Nästa steg

[Lägga till Skycure-appar, Microsoft Authenticator-appen och iOS-konfigurationsprincipen](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)
