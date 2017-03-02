---
title: "Intune-princip för att tillåta/blockera appar för Samsung KNOX | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Skapa en anpassad profil för att tillåta och blockera appar för Samsung KNOX Standard-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: f5267d2e06f1cd7ec471fd1782bfd965843d1c7e
ms.lasthandoff: 02/16/2017



---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices-in-microsoft-intune"></a>Använd anpassade principer för att tillåta och blockera appar för Samsung KNOX Standard-enheter i Microsoft Intune
[!INCLUDE[azure_preview](../includes/azure_preview.md)] I det här avsnittet anges hur du skapar en anpassad princip för Microsoft Intune som skapar något av följande:

- En lista över appar som blockeras från att köras på enheten. Appar i den här listan blockeras från att köras även om de redan är installerade när principen tillämpas.
- En lista över appar som enhetens användare tillåts att installera från Google Play Store. Endast de appar som du tar med i listan kan installeras. Inga andra appar kan installeras från butiken.

De här inställningarna kan endast användas av enheter som kör Samsung KNOX Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Skapa en lista med tillåtna eller blockerade appar

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
2. Välj **Skapa profil** från bladet med lista över profiler.
3. Ange **Namn** och en valfri **Beskrivning** för denna enhetsprofil på bladet **Skapa profil**.
2. Välj en **Plattformstyp** för **Android** och profiltypen **Anpassad**.
3. Klicka på **Inställningar**.
3. På bladet **Anpassade OMA-URI-inställningar** väljer du **Lägg till**.
4. I dialogrutan **Lägg till eller redigera OMA-URI-inställning** anger du följande:

### <a name="for-a-list-of-apps-that-are-blocked-from-running-on-the-device"></a>För en lista över appar som blockeras från att köras på enheten:

- **Namn** – Ange **PreventStartPackages**.
- **Beskrivning** – Ange en valfri beskrivning, till exempel ”lista över appar som har blockerats från att köras.”
-     **Datatyp** – Välj **Sträng** i listrutan.
-     **OMA-URI** – Ange **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
-     **Värde** – Ange en lista över de appaketnamn som du vill tillåta. Du kan använda **; : ,** eller **|** som avgränsare. (Exempel: paket1;paket2;)

### <a name="for-a-list-of-apps-that-users-are-allowed-to-install-from-the-google-play-store-while-excluding-all-other-apps"></a>För en lista över appar som användare tillåts att installera från Google Play (alla andra appar exkluderas):
- **Namn** – Ange **AllowInstallPackages**.
- **Beskrivning** – Ange en beskrivning (valfritt), till exempel ”lista över appar som användare kan installera från Google Play.”
- **Datatyp** – Välj **Sträng** i listrutan.
- **OMA-URI** – Ange **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
- **Värde** – Ange en lista över de appaketnamn som du vill tillåta. Du kan använda **; : ,** eller **|** som avgränsare. (Exempel: paket1;paket2;)

4. Klicka på **OK** och klicka sedan på bladet **Skapa profil** och välj **Skapa**.

>[!TIP]
> Du kan hitta paket-ID:et för en app genom att gå till appen i Google Play. Paket-ID finns i webbadressen på appens sida. Paket-ID för Microsoft Word-appen är till exempel **com.microsoft.office.word**.

Appinställningarna tillämpas nästa gång en målenhet checkar in.


<!---## Assign the custom profile--->
