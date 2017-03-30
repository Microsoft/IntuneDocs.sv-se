---
title: Distribuera Skycure-appar, Microsoft Authenticator-appen och iOS-konfigurationsprincipen | Microsoft Docs
description: Distribuera Skycure-appar, Microsoft Authenticator-appen och iOS-konfigurationsprincipen i den klassiska Intune-konsolen.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45826fbc-6df5-41b2-8e80-d1353f904b43
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 86fd9d7212277f9524eb4d7f225df2c7beda1313
ms.openlocfilehash: 9f09a070ec120064bdd64bfb05a39ec9e484606c
ms.lasthandoff: 03/21/2017


---

# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>Distribuera Skycure-appar, Microsoft Authenticator-appen och konfigurationsprincipen för iOS-appen

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>Innan du börjar

-   Nedanstående steg måste slutföras i den [klassiska Intune-konsolen](https://manage.microsoft.com/).

-   Använd samma Azure AD-konto som tidigare konfigurerades i Skycure Management Console, vilket ska vara samma konto som används för att logga in på den klassiska Intune-konsolen.

-   Kontrollera att du vet hur man gör för att:

    -   [Distribuera en app med Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).

    -   [Distribuera en konfigurationsprincip för iOS-appar](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-deploy-skycure-apps-microsoft-authenticator-app-and-the-ios-app-configuration-policy"></a>Så här distribuerar du Skycure-appar, Microsoft Authenticator-appen och konfigurationsprincipen för iOS-appen

1.  I den klassiska Intune-konsolen väljer du **Appar** &gt; **Appar** för att se listan med appar som du kan hantera.

2.  Välj följande appar:

    a.  Microsoft Authenticator

    b.  Skycure-app för Android

    c.  Skycure-app för iOS

       ![Den klassiska Intune-konsolen med alla appar som kan distribueras](../media/mtp/skycure-deploy-app-1.png)

3.  Välj **Hantera distributioner**, välj Azure AD-säkerhetsgruppen som har Skycure-användare och klicka sedan på **Nästa**.

4.  På sidan **Distributionsåtgärd** väljer du alternativet **Nödvändig installation** från listrutan **Godkännande** och klickar sedan på **Nästa**.

    ![Den klassiska Intune-konsolen Distributionsåtgärd](../media/mtp/skycure-deploy-app-2.png)

5.  På sidan **VPN-profil** väljer du alternativet **Ingen** från listrutan **VPN-princip**. Klicka sedan på **Nästa**.

6.  På sidan **Mobilappkonfiguration** väljer du iOS-appens konfigurationsprincip som tidigare skapades från listrutan **Princip för appkonfiguration** och klicka sedan på **Slutför**.

    ![Den klassiska Intune-konsolen Mobilappkonfiguration](../media/mtp/skycure-deploy-app-3.png)

## <a name="next-steps"></a>Nästa steg

[Konfigurera Skycure-integrering med Intune](https://docs.microsoft.com/intune/deploy-use/setup-the-skycure-integration-with-Intune)

