---
title: "Lista över tillåtna och blockerade appar för KNOX"
description: "Anpassad profil för att skapa en lista över tillåtna och blockerade appar för KNOX."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2632da8ca8d149e1519aeac33a57571ae1a55a54
ms.sourcegitcommit: cf7f7e7c9e9cde5b030cf5fae26a5e8f4d269b0d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/14/2017
---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Använda anpassade principer för att tillåta och blockera appar för Samsung KNOX Standard-enheter

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I det här avsnittet anges hur du skapar en anpassad princip för Microsoft Intune som skapar något av följande:

- En lista över appar som blockeras från att köras på enheten. Appar i den här listan blockeras från att köras även om de redan är installerade när principen tillämpas.
- En lista över appar som enhetens användare tillåts att installera från Google Play Store. Endast de appar som du tar med i listan kan installeras. Inga andra appar kan installeras från butiken.

De här inställningarna kan endast användas av enheter som kör Samsung KNOX Standard.

## <a name="to-create-an-allowed-or-blocked-app-list"></a>Skapa en lista med tillåtna eller blockerade appar

1. Öppna [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/) och välj **Princip** &gt; **Konfigurationsprinciper** &gt; **Lägg till**.
2. Expandera **Android** i dialogrutan **Skapa en ny princip**, välj **Anpassad konfiguration** och välj sedan **Skapa princip**.
3. Ange ett namn och en beskrivning (valfritt) för principen och välj sedan **Lägg till** i avsnittet **OMA-URI-inställningar**.
4. I dialogrutan **Lägg till eller redigera OMA-URI-inställning** anger du följande: För en lista över appar som blockeras från att köras på enheten:
    
    - **Inställningsnamn.** Ange **PreventStartPackages**.
    - **Beskrivning av inställning.** Ange en valfri beskrivning (valfritt), till exempel ”lista över appar som har blockerats från att köras”.
    -   **Datatyp.** Välj **Sträng** i listrutan.
    -   **OMA-URI.** Ange **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
    -   **Värde.** Ange en lista över de appaketnamn som du vill blockera. Du kan använda **; : ,** eller **|** som avgränsare. (Exempel: paket1;paket2;)

    För en lista över appar som användare tillåts att installera från Google Play (alla andra appar exkluderas):

    - **Inställningsnamn.** Ange **AllowInstallPackages**.
    - **Beskrivning av inställning.** Ange en beskrivning (valfritt), till exempel ”lista över appar som användare kan installera från Google Play”.
    - **Datatyp.** Välj **Sträng** i listrutan.
    - **OMA-URI.** Ange **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
    - **Värde.** Ange en lista över de appaketnamn som du vill tillåta. Du kan använda **; : ,** eller **|** som avgränsare. (Exempel: paket1;paket2;)

4. Klicka på **OK** och sedan på **Spara princip**. 

>[!TIP]
> Du kan hitta paket-ID:et för en app genom att gå till appen i Google Play. Paket-ID finns i webbadressen på appens sida. Paket-ID för Microsoft Word-appen är till exempel **com.microsoft.office.word**.

Appinställningarna tillämpas nästa gång en målenhet checkar in.


## <a name="deploy-the-policy"></a>Distribuera principen

1.  Välj den princip på arbetsytan **Princip** som du vill distribuera och klicka sedan på **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** väljer du en eller flera grupper som du vill distribuera principen till. Klicka sedan på **Lägg till** &gt; **OK**.

 
När du väljer en distribuerad princip visas ytterligare information om distributionen i den nedre delen av principlistan.

### <a name="see-also"></a>Se även
[Inställningar för Android- och Samsung KNOX-principer i Microsoft Intune](android-policy-settings-in-microsoft-intune.md)
