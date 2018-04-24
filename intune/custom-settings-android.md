---
title: Lägga till anpassade inställningar för Android-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa en anpassad profil för Android-enheter om du vill skapa en WiFi-profil med en i förväg delad nyckel, skapa en VPN-profil per app eller tillåta/blockera appar för Samsung Knox Standard-enheter i Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0195e138b59fae019fa2bc02aadf211257a65cac
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="custom-settings-for-android-devices---intune"></a>Anpassade inställningar för Android-enheter – Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Anpassade profiler använder OMA-URI-inställningar (Open Mobile Alliance Uniform Resource Identifier) till att konfigurera olika funktioner på Android-enheter. De här inställningarna används vanligtvis av tillverkare av mobila enheter till att styra funktioner på enheten.

Med hjälp av en anpassad profil kan du konfigurera och tilldela följande Android-inställningar. De här inställningarna är inte inbyggda i Intune-principerna:

- [Skapa en Wi-Fi-profil med en i förväg delad nyckel](/intune/wi-fi-profile-shared-key)
- [Skapa en VPN-profil per app](/intune/android-pulse-secure-per-app-vpn)
- [Tillåta och blockera appar för Samsung Knox Standard-enheter](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> Det är bara inställningarna i listan som kan konfigureras med den här profiltypen. Android-enheter visar inte hela listan med OMA-URI-inställningar som du kan konfigurera. Om du vill se fler inställningar kan du rösta på detta på [Intunes UserVoice-webbplats](https://microsoftintune.uservoice.com/forums/291681-ideas).

## <a name="custom-profile-settings-for-android-devices"></a>Anpassade profilinställningar för Android-enheter

1. Logga in på [Azure Portal](https://portal.azure.com). 
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Skapa en anpassad profil med hjälp av Android-plattformen. Anvisningar finns i [Konfigurera anpassade enhetsinställningar i Microsoft Intune](custom-settings-configure.md).
4. I **Anpassade OMA-URI-inställningar** väljer du **Lägg till** och sedan **Lägg till rad**.
5. Ange följande egenskaper:

   - **Namn** – Ange ett unikt namn för OMA-URI-inställningen så att du lätt kan hitta den.
   - **Beskrivning** – Ange en beskrivning som ger en översikt över inställningen, samt annan viktig information.
   - **Datatyp** – Ange den datatyp som du använder för OMA-URI-inställningen. Välj mellan **Sträng**, **Sträng (XML)**, **Datum och tid**, **Heltal**, **Flyttal** och **Boolesk**.
   - **OMA-URI** – Ange önskad OMA-URI.
   - **Värde** – Ange det värde som du vill associera med den OMA-URI som du har angett.

6. Klicka på **OK** för att spara ändringarna. Fortsätt att lägga till fler inställningar efter behov.

## <a name="next-steps"></a>Nästa steg

När du slutför inställningarna skapas profilen och visas sedan i listan. Information om hur du tilldelar den här profilen till grupper finns i [Tilldela enhetsprofiler](device-profile-assign.md).
