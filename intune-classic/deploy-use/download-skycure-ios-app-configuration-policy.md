---
title: Hämta konfigurationsprincip för Skycures iOS-app
description: Hämta den konfigurationsprincip för Skycures iOS-app som ska användas när Skycure iOS-app distribueras till slutanvändarna.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d211b876-4d3a-473c-999f-843c0a16cd22
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2f3cf3b2b18eeadf6779b7a8e96d75e569e6e3be
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="download-skycure-ios-app-configuration-policy"></a>Hämta konfigurationsprincip för Skycures iOS-app

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>Innan du börjar

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

2.  Klicka på länken **Integrering av installationsfiler** och spara den genererade \*ZIP-filen. ZIP-filen innehåller filen **skycure\_configuration.plist**, som används för att skapa iOS-appens konfigurationsprincip i den klassiska Intune-portalen.

![Skycure integrering, installationsfiler](../media/mtp/skycure-ios-app-2.png)

## <a name="next-steps"></a>Nästa steg

[Lägga till Skycure-appar, Microsoft Authenticator-appen och iOS-konfigurationsprincipen](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)
