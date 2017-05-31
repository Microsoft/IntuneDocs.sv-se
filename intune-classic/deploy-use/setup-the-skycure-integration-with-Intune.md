---
title: Konfigurera Skycure-integrering med Intune | Microsoft Docs
description: Konfigurera Skycure-integrering med Microsoft Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93722f66-7641-4a3f-b1fb-3a0a58a36675
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8c862b085f654102f2d461ee5571aba1ab470ea5
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="set-up-the-skycure-integration-with-intune"></a>Konfigurera Skycure-integrering med Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Du måste lägga till Skycure-appar i Azure AD för att kunna använda enkel inloggning.

## <a name="before-you-begin"></a>Innan du börjar

### <a name="azure-ad-account-used-to-integrate-intune-and-skycure"></a>Azure AD-kontot som används för att integrera Intune och Skycure

-   Kontrollera att Azure AD-kontot har konfigurerats korrekt i [Skycure Management Console](https://aad.skycure.com), innan du startar den grundläggande Skycure-installationsprocessen.

### <a name="full-integration-vs-read-only"></a>Fullständig integrering resp. Skrivskyddad

Skycure har stöd för två integreringslägen med Intune:

-   **Skrivskyddad integrering (grundinställning):** Inventerar endast enheter från Azure Active Directory och fyller i dem i Skycure-konsolen.
<br>
    -   Om rutorna **Rapportera hälsotillstånd och enhetsrisker till Intune** och **Rapportera även säkerhetsincidenter till Intune** inte är markerade i Skycure Management Console, är integreringen skrivskyddad och ändrar därför aldrig enhetstillståndet (kompatibla eller icke-kompatibla) i Intune.
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

    ![iOS-app i Skycure Management Console](../media/mtp/skycure-setup-1.png)

5.  När inloggningssidan öppnas anger du dina autentiseringsuppgifter för Intune och klickar sedan på **Acceptera**.

    ![iOS-app i Intune, inloggningsfråga](../media/mtp/skycure-setup-2.png)

6.  När appen har lagts till i Azure AD, ser du en indikation om att appen lades till i Azure AD i Skycure Management Console.

    ![iOS-app, slutförandeskärm](../media/mtp/skycure-setup-3.png)

> [!NOTE]
> Upprepa samma steg för **Skycure Android**- och **hanterings**apparna.

### <a name="add-an-azure-ad-security-group-into-skycure"></a>Lägga till en Azure AD-säkerhetsgrupp i Skycure

Du måste lägga till en Azure AD-säkerhetsgrupp som innehåller alla enheter som kör Skycure.

1.  Ange och välj alla säkerhetsgrupper med enheter som kör Skycure. Klicka sedan på **Tillämpa ändringar**.

    ![Konfigurera säkerhetsgrupp i Skycure Management Console](../media/mtp/skycure-setup-4.png)

Skycure synkroniserar de enheter som kör Mobile Threat Defense-tjänsten med Azure AD-säkerhetsgrupperna.

![Säkerhetsgruppens konfiguration slutfördes i Skycure Management Console](../media/mtp/skycure-setup-5.png)

## <a name="set-up-the-full-integration-between-intune-and-skycure"></a>Konfigurera fullständig integrering mellan Intune och Skycure

1.  Gå till [Skycure Management Console](https://aad.skycure.com).

2.  Ange dina **autentiseringsuppgifter som Skycure-administratör** och klicka sedan på **Fortsätt**.

3.  Gå till **Inställningar** och välj **Fullständig integrering** under **Intune-integrering**.

4.  Kontrollera följande inställningar:

    a.  Rapportera hälsotillstånd och enhetsrisk till Intune

    b.  Rapportera även säkerhetsincidenter till Intune

5.  Klicka på **Tillämpa ändringar**.

    ![Skycures fullständiga integrering slutfördes](../media/mtp/skycure-setup-6.png)

## <a name="next-steps"></a>Nästa steg

[Aktivera Skycure Mobile Threat Defense i Intune](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

