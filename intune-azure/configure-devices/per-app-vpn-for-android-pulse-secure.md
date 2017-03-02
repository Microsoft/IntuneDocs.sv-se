---
title: "VPN-profil per app för Android – Pulse Secure | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Skapa en VPN-profil per app för Android-enheter som hanteras av Intune."
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
ms.openlocfilehash: aeed271699656addce8f2bd8cde2a69ab8ede8f9
ms.lasthandoff: 02/16/2017


---

# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Använd en anpassad Microsoft Intune-profil för att skapa en VPN-profil per app för Android-enheter

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Du kan skapa en VPN-profil per app för enheter som kör Android 5.0 och senare som hanteras av Intune. Börja med att skapa en VPN-profil som använder anslutningstypen Pulse Secure. Skapa sedan en princip för anpassad konfiguration som associerar VPN-profilen med specifika appar.

När du har distribuerat principen till din Android-enhet eller användargrupper ska användarna starta PulseSecure VPN. PulseSecure kommer sedan att endast att ge trafik från de angivna apparna tillåtelse att använda den öppna VPN-anslutningen.

> [!NOTE]
>
> Endast anslutningstypen Pulse Secure stöds för den här profilen.


## <a name="step-1-create-a-vpn-profile"></a>Steg 1: Skapa en VPN-profil


1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
2. Välj **Skapa profil** från bladet med lista över profiler.
3. Ange **Namn** och en valfri **Beskrivning** för VPN-profilen på bladet **Skapa profil**.
4. Välj **Android** i listrutan **Plattform**.
5. Välj **VPN** i listrutan **Profiltyp**.
3. Välj **Inställningar** > **Konfigurera** och konfigurera sedan VPN-profilen enligt inställningarna i [Så här konfigurerar du VPN-inställningar](how-to-configure-vpn-settings.md) och [Intunes VPN-inställningar för Android-enheter](vpn-for-android.md).

Anteckna VPN-profilnamnet som ska användas i nästa steg. Till exempel **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Steg 2: Skapa en princip för anpassad konfigurering

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. Ange **Namn** och **Beskrivning** för den anpassade profilen på bladet **Skapa profil**.
5. Välj **Android** i listrutan **Plattform**.
6. Välj **Anpassad** i listrutan **Profiltyp**.
7. Välj **Inställningar** > **Konfigurera**.
3. På bladet **Anpassade OMA-URI-inställningar** väljer du **Lägg till**.
    - Ange ett namn på inställningen.
    - Ange **Sträng** för **Datatyp**.
    - För **OMA-URI** anger du strängen: **./Vendor/MSFT/VPN/Profile/*Namn*/PackageList**, där *Namn* är det VPN-profilnamn som du antecknade i steg 1. I detta exempel skulle strängen vara **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
    - För **Värde** skapar du en semikolonavgränsad lista över paket som ska associeras med profilen. Om du exempelvis vill att Excel och webbläsaren Google Chrome ska använda VPN-anslutningen anger du **com.microsoft.office.excel;com.android.chrome**.

![Exempel på VPN-anpassad princip per app för Android](./media/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Ange applistan som svartlistad eller vitlistad (valfritt)
  Du kan ange en lista över appar som *inte* kan använda VPN-anslutning med hjälp av värdet **SVARTLISTAT**. Alla andra appar ansluter via VPN.
Du kan också använda värdet **VITLISTAT** för att ange en lista över appar som *kan* använda VPN-anslutning. Appar som inte finns med i listan kan inte ansluta via VPN.
  1.    På bladet **Anpassade OMA-URI-inställningar** väljer du **Lägg till**.
  2.    Ange ett namn på inställningen.
  3.    Ange **Sträng** som **Datatyp**.
  4.    För **OMA-URI** använder du följande sträng: **./Vendor/MSFT/VPN/Profile/*Namn*/Läge**, där *Namn* är den VPN-profil som du antecknade i steg 1. I vårt exempel skulle strängen vara **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  5.    Ange **SVARTLISTAT** eller **VITLISTAT** som **Värde**.



## <a name="step-3-assign-both-policies"></a>Steg 3: Tilldela båda principerna

Följ instruktionerna i [Tilldela enhetsprofiler](how-to-assign-device-profiles.md) för att tilldela båda profilerna till önskade användare eller enheter.

