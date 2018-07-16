---
title: Inställningar för helskärmsläge för Android i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera dina Android-kioskenheter som enheter för enstaka eller för flera appar.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9158893b3ae2c2f70b08682a61cbba4d55b43710
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909158"
---
# <a name="kiosk-settings-for-android-devices-in-intune"></a>Inställningar för helskärmsläge för Android-enheter i Intune

Du kan konfigurera en enhet i helskärmsläge för en eller flera appar genom att använda enhetskonfigurationsinställningar. När en enhet är i helskärmsläge begränsas användningen av enheten till appar eller webblänkar som definieras av begränsningsprofilen. 

## <a name="restrict-an-android-kiosk-device-to-a-single-app"></a>Begränsa en Android-kioskenhet till en enda app

Om **Helskärmsläge** = **kioskenhet för enstaka app** anges för en kioskenhets begränsningsprofil kan användarna bara komma åt en enda app. När en enhet som konfigurerats i det här läget startas så startar den specifika appen. Användarna förhindras att öppna nya appar eller ändra appen som körs.

1. Kontrollera att den app som du vill ska användas på kioskenheten har [distribuerats till enheten](apps-deploy.md) och att du har tilldelat appen till enhetsgruppen du har skapat för dina kioskenheter.
2. Gå till [Intune-portalen](https://portal.azure.com) och välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande fält på bladet **Skapa profil**:
     - **Namn**
     - **Plattform**: Android enterprise
     - **Profiltyp**: Endast enhetsägare > Enhetsbegränsningar
4. Välj **Inställningar** > **Helskärmsläge**.
5. För **Helskärmsläge** väljer du **Kioskenhet för enstaka app**.
6. Välj **Välj en hanterad app** och välj sedan den Managed Google Play-app som du vill ska vara den enda app som är tillgängliga för enheter som använder den här profilen.
7. Välj **OK** > **OK** > **OK** > **Skapa**.
8. Välj den profil som du precis har skapat > **Tilldelningar**.
9. Under **Tilldelat till** väljer du **Valda grupper**.
10. Välj **Välj grupper att ta** > välj den enhetsgrupp som du har skapat för dina kioskenheter > **Välj**.

## <a name="restrict-a-kiosk-device-to-a-set-of-apps-or-web-links"></a>Begränsa en kioskenhet till en uppsättning appar eller webblänkar

Om **Helskärmsläge** = **kioskenhet för flera appar** anges för en kioskenhets begränsningsprofil kan användarna bara komma åt det begränsade antalet appar som du konfigurerar. Du kan också definiera en uppsättning webblänkar som användarna kan besöka. När principen används ser användarna ikoner för tillåtna appar på startskärmen.

Följ dessa steg om du vill ange en Android-kioskenhet för flera appar:

1. [Importera och distribuera Managed Home Screen-appen från Managed Google Play](#import-and -deploy-the-managed-home-screen-app)
2. [Lägga till och tilldela appar som kan användas i helskärmsläge](#add-and-assign-apps-that-can-be-used-in-kiosk-mode)
3. (Valfritt) [Lägga till webblänkar som kan användas i helskärmsläge](#add-web-links-that-can-be-used-in-kiosk-mode)

### <a name="import-and-deply-the-managed-home-screen-app"></a>Importera och distribuera Managed Home Screen-appen

1. Gå till [sidan Managed Home Screen på Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) och logga in med samma konto som du använder för andra Managed Google Play-appar.
2. Välj **Godkänn**.
3. Gå till [Intune-portalen](https://portal.azure.com) och välj **Mobilappar** > **Managed Google Play** > **Synkronisera**.
4. Välj **Appar** > **Managed Home Screen** > **Tilldelningar** > **Lägg till grupp**.
5. Under **Tilldelningstyp** väljer du **Obligatorisk**.
6. Välj **Grupper som omfattas** > **Välj grupper att ta med** > välj den enhetsgrupp du har skapat för dina kioskenheter > **Välj** > **OK** > **OK** > **Spara**.

### <a name="add-and-assign-apps-that-can-be-used-in-kiosk-mode"></a>Lägga till och tilldela appar som kan användas i helskärmsläge

Följ dessa steg för varje app du vill ska vara tillgängliga på kioskenheterna:

1. [Lägg till appen i Intune](store-apps-android.md).
2. Välj **Mobilappar** > **Appar** > välj appen > **Tilldelningar** > **Lägg till grupp**.
3. Under **Tilldelningstyp** väljer du **Obligatorisk**.
4. Välj **Grupper som omfattas** > **Välj grupper att ta med** > välj den enhetsgrupp du har skapat för dina kioskenheter > **Välj** > **OK** > **OK** > **Spara**.

### <a name="add-web-links-that-can-be-used-in-kiosk-mode"></a>Lägga till webblänkar som kan användas i helskärmsläge

1. Gå till [Intune-portalen](https://portal.azure.com) och välj **Mobilappar** > **Appar** > **Lägg till**.
2. Under **Apptyp** väljer du **Webblänk**.
3. Välj **Konfigurera** och ange nödvändig information. Du behöver inte lägga en logotypbild eftersom den hämtas automatiskt från webbplatsens favicon.ico.
4. Välj **OK** > **Lägg till**.

Kontrollera att du har distribuerat en webbläsare till kioskenheterna via [Mobilappar](apps-add.md).

### <a name="create-a-multi-app-kiosk-profile"></a>Skapa en profil för kioskenhet för flera appar

1. Gå till [Intune-portalen](https://portal.azure.com) och välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande fält på bladet **Skapa profil**:
     - **Namn**: ange ett intuitivt namn
     - **Plattform**: Android enterprise
     - **Profiltyp**: Endast enhetsägare > Enhetsbegränsningar
4. Välj **Inställningar** > **Helskärmsläge**.
5. För **Helskärmsläge** väljer du **Flera appar för kioskenhet**.
6. Välj **Lägg till** och välj sedan de appar eller webblänkar som du vill ska vara tillgängliga för enheter som använder profilen.
7. Välj **OK** > **OK** > **OK** > **Skapa**.
8. Välj den profil som du precis har skapat > **Tilldelningar**.
9. Under **Tilldelat till** väljer du **Valda grupper**.
10. Välj **Välj grupper att ta** > välj den enhetsgrupp som du har skapat för dina kioskenheter > **Välj** > **Spara**.

## <a name="next-steps"></a>Nästa steg
[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
