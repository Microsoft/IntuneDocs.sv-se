---
title: "Hämta den konfigurationsprincip för Skycures iOS-app som ska användas med Intune"
titlesuffix: Azure portal
description: "Hämta den konfigurationsprincip för Skycures iOS-app som ska användas med Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1bdc2ecf-32d0-4b6a-80b4-dbcdb9909010
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cbf26b44725f1fa08fbc6766f0560fe91d63d6ca
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/30/2017
---
# <a name="download-skycure-ios-app-configuration-policy"></a>Hämta konfigurationsprincip för Skycures iOS-app

## <a name="before-you-begin"></a>Innan du börjar

Du måste logga in på Skycure Management Console för att kunna utföra nästa steg.

> [!TIP] 
> Om du använder Microsoft Internet Explorer 11 eller Edge kan du behöva öppna Skycure Management Console i privat läge.

## <a name="to-download-the-ios-app-configuration-policy"></a>Så här hämtar du konfigurationsprincipen för iOS-appen

1.  Gå till [Skycure Management Console](https://aad.skycure.com).

2.  Ange dina **autentiseringsuppgifter som Skycure-administratör** och klicka sedan på **Fortsätt**.

    ![Inloggning till Skycure Management Console](./media/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > Skycure-administratörens användarnamn är ett e-postkonto som måste vara ett giltigt användarkonto i Azure Active Directory, annars misslyckas inloggningen. Skycure använder Azure Active Directory för att autentisera sitt administratörsanvändarnamn med enkel inloggning (SSO).

3.  Gå till **Inställningar** &gt; **Integrering med enhetshantering** &gt; **Val av EMM-integrering**, välj **Microsoft Intune** och spara sedan ditt val.

4.  Klicka på länken **Integrering av installationsfiler** och spara den genererade \*ZIP-filen. ZIP-filen innehåller filen **skycure\_configuration.plist**, som används för att skapa iOS-appens konfigurationsprincip i den klassiska Intune-portalen.

![Skycure integrering, installationsfiler](./media/skycure-ios-app-2.png)

## <a name="next-steps"></a>Nästa steg

[Lägga till och tilldela Skycure-appar, Microsoft Authenticator-appen och iOS-konfigurationsprincipen](mtd-apps-ios-app-configuration-policy-add-assign.md)
