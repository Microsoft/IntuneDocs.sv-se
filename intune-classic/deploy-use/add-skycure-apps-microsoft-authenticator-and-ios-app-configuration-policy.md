---
title: Lägga till Skycure-appar, Microsoft Authenticator-appen och iOS-konfigurationsprincipen
description: Lägga till Skycure-program, Microsoft Authenticator-program och iOS-konfigurationsprincipen i den klassiska Intune-portalen.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018d26f4-4a75-4e27-bb04-54f54106cb2f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 45412855db4afd9dd03b2139a3720d1619d293e2
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="add-skycure-apps-microsoft-authenticator-app-and-ios-configuration-policy"></a>Lägga till Skycure-appar, Microsoft Authenticator-appen och iOS-konfigurationsprincipen

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Du måste använda Intune för att lägga till och distribuera Skycure-apparna, så att slutanvändarna får ett meddelande när ett hot har identifierats i deras mobila enheter och anvisningar för att åtgärda hoten.

Du måste dessutom ha [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) så att användarnas identiteter kontrolleras av Azure AD och iOS-appens konfigurationsprincip som visar att Skycure iOS-appen ska använda Intune och enkel inloggning (SSO) med Azure AD, så att användarna inte behöver ange användarnamn och lösenord varje gång de loggar in i Skycure-appen.

## <a name="before-you-begin"></a>Innan du börjar

-   Nedanstående steg måste slutföras i den [klassiska Intune-portalen](https://manage.microsoft.com/).

-   Använd samma Azure AD-konto som tidigare konfigurerades i Skycure Management Console, vilket ska vara samma konto som användes för att logga in på den klassiska Intune-portalen.

-   Skycure-integreringsfilen måste vara klar att använda. Detta är ZIP-filen som tidigare hämtades från Skycure Management Console. Den innehåller filen **skycure\_configuration.plist** med iOS-appens parametrar för konfigurationsprincipen.

-   Kontrollera att du vet hur man gör för att:

    -   [Lägga till en app i Intune](/intune-classic/deploy-use/add-apps).

    -   [Lägga till en konfigurationsprincip för iOS-appar i Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-add-the-skycure-app-for-android"></a>Så här lägger du till Skycure-appen för Android

1.  I den klassiska Intune-portalen väljer du **Program** &gt; **Lägg till program** för att starta Intunes programvaruutgivare. Klicka sedan på **Nästa**.

2.  På sidan **Programvaruinstallation** väljer du **Extern länk**. Klistra sedan in [URL för Skycures Android-app](https://play.google.com/store/apps/details?id=com.skycure.skycure) under **Ange URL**.

    ![Intune programvaruutgivare Ange URL](../media/mtp/skycure-add-apps-1.png)

3.  På sidan **Programvarubeskrivning** anger du **Utgivare**, **Namn** och **Beskrivning**. Välj alternativet **Visa den här som en aktuell app och markera den i företagsportalen**. Klicka sedan på **Nästa**.

    ![Intune programvaruutgivare Programvarubeskrivning](../media/mtp/skycure-add-apps-2.png)

4.  Klicka på **Överför** och sedan på **Stäng**.

## <a name="to-add-the-skycure-app-for-ios"></a>Så här lägger du till Skycures iOS-app

1.  I den klassiska Intune-portalen väljer du **Program** &gt; **Lägg till program** för att starta Intunes programvaruutgivare. Klicka sedan på **Nästa**.

2.  På sidan **Programvaruinstallation** väljer du **Hanterad iOS-app från App Store**. Klistra sedan in [URL för Skycures iOS-app](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) under **Ange URL**.

    ![Intune programvaruutgivare Hanterad iOS-app](../media/mtp/skycure-add-apps-3.png)

3.  På sidan **Programvarubeskrivning** anger du **Utgivare**, **Namn** och **Beskrivning**. Välj alternativet **Visa den här som en aktuell app och markera den i företagsportalen**. Klicka sedan på **Nästa**.

    ![Intune programvaruutgivare Alternativ](../media/mtp/skycure-add-apps-4.png)

4.  På sidan **Krav** väljer du alternativet **Alla** under **Typ av mobil enhet**. Klicka sedan på **Nästa**.

5.  Klicka på **Överför** och sedan på **Stäng**.

## <a name="to-add-the-microsoft-authenticator-app-for-ios"></a>Så här lägger du till Microsoft Authenticator-appen för iOS

1.  I den klassiska Intune-portalen väljer du **Program** &gt; **Lägg till program** för att starta Intunes programvaruutgivare. Klicka sedan på **Nästa**.

2.  På sidan **Programvaruinstallation** väljer du **Hanterad iOS-app från App Store**. Klistra sedan in [URL för Microsoft Authenticator-appen för iOS](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) under **Ange URL**.

    ![Intune programvaruutgivare Hanterad iOS-app 2](../media/mtp/skycure-add-apps-5.png)

3.  På sidan **Programvarubeskrivning** anger du **Utgivare**, **Namn** och **Beskrivning**. Välj alternativet **Visa den här som en aktuell app och markera den i företagsportalen**. Klicka sedan på **Nästa**.

    ![Intune programvaruutgivare Hanterad iOS-app 3](../media/mtp/skycure-add-apps-6.png)

4.  På sidan **Krav** väljer du alternativet **Alla** under **Typ av mobil enhet**. Klicka sedan på **Nästa**.

5.  Klicka på **Överför** och sedan på **Stäng**.

## <a name="to-add-the-skycure-ios-app-configuration-policy"></a>Så här lägger du till konfigurationsprincipen för Skycures iOS-app

1.  I den klassiska Intune-portalen väljer du **Princip** &gt; **Översikt &gt; Lägg till princip**.

2.  Expandera **iOS**i listan med principer, välj **Princip för mobilappkonfiguration (iOS 8.0 och senare)** och välj sedan **Skapa princip**.

    ![Konfigurationsprincip för iOS-app](../media/mtp/skycure-add-apps-7.png)

3.  Ange ett namn och en valfri beskrivning av konfigurationsprincipen för iOS-appen under **Allmänt** på sidan **Skapa princip** .

    a.  Öppna filen **skycure\_configuration.plist** med en textredigerare, t.ex. Anteckningar. Kopiera innehållet och klistra in det i **Konfigurationsprincip för mobilapp**, välj **Verifiera** och sedan **Spara princip**.

       ![Konfigurationsprincip 2 för iOS-app](../media/mtp/skycure-add-apps-8.png)

## <a name="next-steps"></a>Nästa steg

[Distribuera Skycure-appar, Microsoft Authenticator-appen och konfigurationsprincip för iOS-appen](/intune-classic/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)
