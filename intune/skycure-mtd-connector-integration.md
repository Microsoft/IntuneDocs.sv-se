---
title: Konfigurera Skycure-integrering med Intune
titlesuffix: Azure portal
description: Konfigurera Skycure-integrering med Microsoft Intune.
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: beaf027334ce4929e4ca824b2b7e199cea22a832
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2018
---
# <a name="set-up-the-skycure-integration-with-intune"></a>Konfigurera Skycure-integrering med Intune

Du måste lägga till Skycure-appar i Azure AD för att kunna använda enkel inloggning.

## <a name="before-you-begin"></a>Innan du börjar

### <a name="azure-ad-account-used-to-integrate-intune-and-skycure"></a>Azure AD-kontot som används för att integrera Intune och Skycure

-   Kontrollera att Azure AD-kontot har konfigurerats korrekt i [Skycure Management Console](https://aad.skycure.com), innan du startar den grundläggande Skycure-installationsprocessen.

### <a name="full-integration-vs-read-only"></a>Fullständig integrering resp. Skrivskyddad

Skycure har stöd för två integreringslägen med Intune:

-   **Skrivskyddad integrering (grundinställning):** Inventerar endast enheter från Azure Active Directory och fyller i dem i Skycure-konsolen.
<br>
    -   Om rutorna **Rapportera hälsotillstånd och enhetsrisker till Intune** och **Rapportera även säkerhetsincidenter till Intune** inte är markerade i Skycure Management Console, är integreringen skrivskyddad och ändrar därför aldrig tillståndet för en enhet (kompatibel eller icke-kompatibel) i Intune.
<br></br>
-   **Fullständig integrering:** Tillåter att Skycure rapporterar information om enheternas risker och säkerhetsincidenter till Intune, vilket skapar en dubbelriktad kommunikation mellan båda molntjänsterna.

### <a name="how-the-skycure-apps-are-used-with-azure-ad-and-intune"></a>Hur används Skycure-apparna med Azure AD och Intune?

-   **iOS-app:** Slutanvändarna kan logga in på Azure AD med en iOS-app.

-   **Android-app:** Slutanvändarna kan logga in på Azure AD med en Android-app.

-   **Hanteringsapp:** Detta är Skycures Azure AD-app för flera innehavare som möjliggör kommunikation från tjänst till tjänst med Intune.

## <a name="to-set-up-the-read-only-integration-between-intune-and-skycure"></a>Så här konfigurerar du skrivskyddad integrering mellan Intune och Skycure

> [!IMPORTANT]
> Skycure-administratörens autentiseringsuppgifter är ett e-postmeddelande som måste tillhöra en giltig användare i Azure Active Directory, annars misslyckas inloggningen. Skycure använder Azure Active Directory till att autentisera sin administratör med enkel inloggning (SSO).

1.  Gå till [Skycure Management Console](https://aad.skycure.com).

2.  Ange dina **autentiseringsuppgifter som Skycure-administratör** och klicka sedan på **Fortsätt**.

3.  Gå till **Inställningar** och välj **Grundinställning** under **Intune-integrering**.

4.  På etiketten **iOS-app** klickar du på **Lägg till i Active Directory**.

    ![iOS-app i Skycure Management Console](./media/skycure-setup-1.png)

5.  När inloggningssidan öppnas anger du dina autentiseringsuppgifter för Intune och klickar sedan på **Acceptera**.

    ![iOS-app i Intune, inloggningsfråga](./media/skycure-setup-2.png)

6.  När appen har lagts till i Azure AD, ser du en indikation om att appen lades till i Azure AD i Skycure Management Console.

    ![iOS-app, slutförandeskärm](./media/skycure-setup-3.png)

> [!NOTE]
> Upprepa samma steg för **Skycure Android**- och **hanterings**apparna.

### <a name="add-an-azure-ad-security-group-into-skycure"></a>Lägga till en Azure AD-säkerhetsgrupp i Skycure

Du måste lägga till en Azure AD-säkerhetsgrupp som innehåller alla enheter som kör Skycure.

1.  Ange och välj alla säkerhetsgrupper med enheter som kör Skycure. Klicka sedan på **Tillämpa ändringar**.

    ![Konfigurera säkerhetsgrupp i Skycure Management Console](./media/skycure-setup-4.png)

Skycure synkroniserar de enheter som kör Mobile Threat Defense-tjänsten med Azure AD-säkerhetsgrupperna.

![Säkerhetsgruppens konfiguration slutfördes i Skycure Management Console](./media/skycure-setup-5.png)

## <a name="set-up-the-full-integration-between-intune-and-skycure"></a>Konfigurera fullständig integrering mellan Intune och Skycure

1.  Gå till [Skycure Management Console](https://aad.skycure.com).

2.  Ange dina **autentiseringsuppgifter som Skycure-administratör** och klicka sedan på **Fortsätt**.

3.  Gå till **Inställningar** och välj **Fullständig integrering** under **Intune-integrering**.

4.  Kontrollera följande inställningar:

    a.  Rapportera hälsotillstånd och enhetsrisk till Intune

    b.  Rapportera även säkerhetsincidenter till Intune

5.  Klicka på **Tillämpa ändringar**.

    ![Skycures fullständiga integrering slutfördes](./media/skycure-setup-6.png)

## <a name="next-steps"></a>Nästa steg

[Konfigurera Skycure-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)
