---
title: Konfigurera Google Chrome för Android-enheter med Intune
titleSuffix: Microsoft Intune
description: Använd Intunes konfigurationsprinciper med Google Chrome för Android-enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f667940cc238fe243b05c7ab6f1459f63f18faa
ms.sourcegitcommit: 2c8a41ee95a3fde150667a377770e51b621ead65
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73635476"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>Konfigurera Google Chrome för Android-enheter med Intune 

Du kan använda en konfigurationsprincip för Intune-appar med Google Chrome för Android-enheter. Inställningarna för appen kan tillämpas automatiskt. Du kan till exempel ange de bokmärken och webbadresser som du vill blockera eller tillåta.

## <a name="prerequisites"></a>Krav

- Användarens Android Enterprise-enhet måste vara registrerad i Intune. Mer information finns i [Konfigurera registrering av Android Enterprise-arbetsprofilenheter](~/enrollment/android-work-profile-enroll.md).
- Google Chrome läggs till som en hanterad Google Play-app. Läs om hanterade Google Play-konton i [Anslut ditt Intune-konto till ditt hanterade Google Play-konto](~/enrollment/connect-intune-android-enterprise.md) för mer information.

## <a name="add-the-google-chrome-app-to-intune"></a>Lägga till Google Chrome-appen i Intune

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. I fönstret **Intune** väljer du **Klientappar** > **Appar** > **Lägg till** och lägger sedan till appen **Hanterat Google Play-konto**.
3. Gå till Hanterat Google Play-konto, sök med **Google Chrome** och godkänn.

    ![Söka och godkänna Google Chrome](~/apps/media/apps-configure-chrome-android/search.png)

4. Tilldela Google Chrome till en användargrupp som en obligatorisk apptyp. Google Chrome distribueras automatiskt när enheten registreras i Intune.

Mer information om hur du lägger till en hanterad Google Play-app i Intune finns i [Hanterade Google Play Butik-appar](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps).

## <a name="add-app-configuration-for-managed-ae-devices"></a>Lägga till appkonfiguration för hanterade Android Enterprise-enheter

1. I fönstret [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) väljer du **Appkonfigurationsprinciper** > **Lägg till**.
2. Lägg till principnamnet, välj **Hanterade enheter** under Enhetsregistreringstyp och **Android** under Plattform.

    ![Lägga till en konfigurationsprincip för Google Chrome](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. Klicka på **Associerad app** och välj **Google Chrome**.

    ![Välj Google Chrome under Associerad app](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. Klicka på **Konfigurationsinställningar**, välj **Använd Configuration Designer** och klicka sedan på **Lägg till** för att välja konfigurationsnycklarna.

    ![Lägg till Använd Configuration Designer](~/apps/media/apps-configure-chrome-android/configuration.png)

    Nedan visas ett exempel på vanliga inställningar:
    - **Blockera åtkomst till en lista med URL:er**: `["*"]`
    - **Tillåt åtkomst till en lista med URL:er**: `["baidu.com", "yahoo.com", "chrome://*"]`
    - **Hanterade bokmärken**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Tillgänglighet för inkognitoläge**: `Incognito mode disabled`

    När konfigurationsinställningarna har lagts till med Configuration Designer, visas de i en tabell. 

    ![Vanliga inställningar](~/apps/media/apps-configure-chrome-android/common-settings.png)

    Inställningarna ovan skapar bokmärken och tillåter åtkomst till alla webbplatser, utom `baidu.com`, `yahoo.com` och `chrome://`.

5. Klicka på **OK** och **Lägg till** för att lägga till konfigurationsprincipen i Intune.
6. Tilldela den här konfigurationsprincipen till en användargrupp. Mer information finns i [Tilldela appar till grupper med Microsoft Intune](~/apps/apps-deploy.md). 

## <a name="verify-the-device-settings"></a>Verifiera enhetsinställningarna

När Android-enheten har registrerats med Android Enterprise, kommer den hanterade Google Chrome-appen med portföljikonen att distribueras automatiskt.
 
   <img alt="Managed Google Chrome with the portfolio icon" src="~/apps/media/apps-configure-chrome-android/chrome-icon.png" width="350">

Starta Google Chrome så ser du att inställningarna har tillämpats.

   Bokmärken:<br>
   <img alt="Bookmarks" src="~/apps/media/apps-configure-chrome-android/bookmarks.png" width="350">

   Blockerad URL:<br>
   <img alt="Blocked URL" src="~/apps/media/apps-configure-chrome-android/blocked-url.png" width="350">

   Tillåt URL:<br>
   <img alt="Allow URL" src="~/apps/media/apps-configure-chrome-android/allowed-url.png" width="350">

   Fliken Inkognito:<br>
   <img alt="Incognito tab" src="~/apps/media/apps-configure-chrome-android/incognito-tab.png" width="350">

## <a name="troubleshooting"></a>Felsökning

1. Kontrollera Intune-portalen för att övervaka principdistributionens status.

    ![Övervaka status för principdistributionen](~/apps/media/apps-configure-chrome-android/monitor-status.png)

2. Starta Google Chrome och gå till **chrome://policy**. Vi bekräftar om inställningarna har tillämpats.

    ![Bekräfta att inställningarna har tillämpats](~/apps/media/apps-configure-chrome-android/confirm.png)

## <a name="additional-information"></a>Ytterligare information

- [Lägga till konfigurationsprinciper för hanterade Android Enterprise-enheter](~/app-configuration-policies-use-android.md)
- [Chrome Enterprise-principlista](https://cloud.google.com/docs/chrome-enterprise/policies/)

## <a name="next-steps"></a>Nästa steg

- Mer information om fullständigt hanterade Android Enterprise-enheter finns i [Konfigurera Intune-registrering av fullständigt hanterade Android Enterprise-enheter](~/enrollment/android-fully-managed-enroll.md).
