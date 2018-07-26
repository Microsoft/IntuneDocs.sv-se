---
title: Per-app-anpassad VPN-profil för Android
titlesuffix: Microsoft Intune
description: Du kan skapa en VPN-profil per app för Android-enheter som hanteras av Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5d8357a63f80552ff4b6ebd6d1da2998e675dd00
ms.sourcegitcommit: 08e1b0d45c84eb9525a0a59f5540d41434da2814
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39146687"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Använd en anpassad Microsoft Intune-profil för att skapa en VPN-profil per app för Android-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Du kan skapa en VPN-profil per app för enheter som kör Android 5.0 och senare som hanteras av Intune. Börja med att skapa en VPN-profil som använder antingen Pulse Secure- eller Citrix-anslutningstypen. Skapa sedan en princip för anpassad konfiguration som associerar VPN-profilen med specifika appar.

När du har tilldelat principen till din Android-enhet eller till användargrupper måste användarna starta Pulse Secure- eller Citrix VPN-klienten. VPN-klienten tillåter då endast trafik från de angivna apparna att använda den öppna VPN-anslutningen.

> [!NOTE]
>
> Endast anslutningstyperna Pulse Secure och Citrix stöds för den här profilen.


## <a name="step-1-create-a-vpn-profile"></a>Steg 1: Skapa en VPN-profil


1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enhetskonfiguration**.
2. I fönstret **Enhetskonfiguration** under avsnittet **Hantera** väljer du **Profiler**.
2. Välj **Skapa profil** i fönstret med profillistan.
3. Ange **Namn** och en valfri **Beskrivning** för VPN-profilen i fönstret **Skapa profil**.
4. Välj **Android** i listrutan **Plattform**.
5. Välj **VPN** i listrutan **Profiltyp**.
3. Välj **Inställningar** > **Konfigurera** och konfigurera sedan VPN-profilen enligt inställningarna i [Så här konfigurerar du VPN-inställningar](vpn-settings-configure.md) och [Intunes VPN-inställningar för Android-enheter](vpn-settings-android.md).

Notera **anslutningens namn** , det vill säga det värde som du anger när du skapar VPN-profilen. Detta krävs i nästa steg. Till exempel **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Steg 2: Skapa en princip för anpassad konfigurering

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enhetskonfiguration**.
2. I fönstret **Enhetskonfiguration** under avsnittet **Hantera** väljer du **Profiler**.
3. Välj **Skapa profil** i profilfönstret.
4. Ange **Namn** och **Beskrivning** för den anpassade profilen i fönstret **Skapa profil**.
5. Välj **Android** i listrutan **Plattform**.
6. Välj **Anpassad** i listrutan **Profiltyp**.
7. Välj **Inställningar** > **Konfigurera**.
3. I fönstret **Anpassade OMA-URI-inställningar** väljer du **Lägg till**.
    - Ange ett namn på inställningen.
    - För **OMA-URI** anger du strängen: ***./Vendor/MSFT/VPN/Profile/* Namn**/PackageList, där *Namn* är det anslutningsnamn som du antecknade i steg 1. I detta exempel skulle strängen vara **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
    - Ange **Sträng** som **Datatyp**.
    - För **Värde** skapar du en semikolonavgränsad lista över paket som ska associeras med profilen. Om du exempelvis vill att Excel och webbläsaren Google Chrome ska använda VPN-anslutningen anger du **com.microsoft.office.excel;com.android.chrome**.

![Exempel på VPN-anpassad princip per app för Android](./media/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Ange applistan som svartlistad eller vitlistad (valfritt)
  Du kan ange en lista över appar som *inte* kan använda VPN-anslutning med hjälp av värdet **SVARTLISTAT**. Alla andra appar ansluter via VPN.
Du kan också använda värdet **VITLISTAT** för att ange en lista över appar som *kan* använda VPN-anslutning. Appar som inte finns med i listan kan inte ansluta via VPN.
  1.    I fönstret **Anpassade OMA-URI-inställningar** väljer du **Lägg till**.
  2.    Ange ett namn på inställningen.
  3.    För **OMA-URI** använder du följande sträng: ***./Vendor/MSFT/VPN/Profile/* Namn**/Läge, där *Namn* är den VPN-profil som du antecknade i steg 1. I vårt exempel skulle strängen vara **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  4.    Ange **Sträng** som **Datatyp**.
  5.    Ange **SVARTLISTAT** eller **VITLISTAT** som **Värde**.



## <a name="step-3-assign-both-policies"></a>Steg 3: Tilldela båda principerna

Följ instruktionerna i [Tilldela enhetsprofiler](device-profile-assign.md) för att tilldela båda profilerna till önskade användare eller enheter.
