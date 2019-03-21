---
title: Felsöka e-postprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Problem relaterade till e-postprofiler och hur du felsöker och löser dem.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 02eac7eaa42f6f9c97426e0536e48a4bc399ed08
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57461030"
---
# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Felsöka e-postprofiler i Microsoft Intune

Se några vanliga problem med e-postprofiler samt hur du felsöker och löser dem.

Om den här informationen inte är till någon hjälp, kan du även [få support för Microsoft Intune](get-support.md).

## <a name="unable-to-send-images-from--email-account"></a>Det går inte att skicka bilder från e-postkontot
Gäller för Intune i den klassiska Azure-portalen.

Användare med automatiskt konfigurerade e-postkonton kan inte skicka bilder från sina enheter. Detta kan hända om **Tillåt att e-post skickas från tredjepartsprogram** inte är aktiverat.

### <a name="intune-solution"></a>Intune-lösning

1. Öppna Microsoft Intune-administrationskonsolen och välj arbetsbelastningen **Princip** > **Konfigurationsprincip**.

2. Välj e-postprofilen och klicka på **Redigera**.

3. Välj **Tillåt att e-post skickas från tredjepartsprogram.**

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager integrerat med Intune

1. Öppna Configuration Manager-konsolen > **Tillgångar och efterlevnad**.

2. Expandera **Översikt** > **Kompatibilitetsinställningar** > **Åtkomst till företagsresurs** och välj **E-postprofiler**.

3. Högerklicka på e-postprofilen och öppna **Egenskaper**.

4. Välj **Tillåt att e-post skickas från tredjepartsprogram** på fliken **Synkroniseringsinställningar**.

## <a name="device-already-has-an-email-profile-installed"></a>Enheten har redan en e-postprofil installerad

Om användaren har installerat en e-postprofil före etableringen av en Intune-profil beror resultatet av e-postprofildistributionen i Intune på enhetsplattformen:

- **iOS**: Intune identifierar en befintlig, duplicerad e-postprofil baserat på värdnamn och e-postadress. Den duplicerade e-postprofilen som skapats av användaren blockerar distributionen av en profil som skapats av Intune-administratören. Det här är ett vanligt problem eftersom iOS-användare vanligtvis skapar en e-postprofil först och sedan registrerar sig. Företagsportalen meddelar användarna att de inte är kompatibla på grund av deras manuellt konfigurerade e-postprofil och uppmanar dem att ta bort profilen. Användarna bör ta bort e-postprofilen så att Intune-profilen kan distribueras. För att förhindra det här problemet ber du användarna att registrera sig så att Intune kan distribuera profilen. Installera sedan den användarskapade e-postprofilen.

- **Windows**: Intune identifierar en befintlig, duplicerad e-postprofil baserat på värdnamn och e-postadress. Intune skriver över den befintliga e-postprofilen som skapats av användaren.

- **Samsung KNOX Standard**: Intune identifierar ett duplicerat e-postkonto baserat på e-postadressen och skriver över det med Intune-profilen. Om användaren konfigurerar kontot skrivs det över igen av Intune-profilen. Detta kan orsaka förvirring för användaren vars kontokonfiguration skrivs över.

Samsung KNOX använder inte värdnamn för att identifiera profilen. Vi rekommenderar att du inte skapar flera e-postprofiler som ska distribueras till samma e-postadress på olika värdar, eftersom de kommer att skriva över varandra.

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>Fel 0x87D1FDE8 för KNOX Standard-enhet
**Problem**: När en e-postprofil för Exchange Active Sync har skapats och distribuerats för Samsung KNOX Standard till olika Android-enheter så rapporteras felet **0x87D1FDE8** eller **Reparationen misslyckades** på principfliken för enhetens egenskaper.

Granska konfigurationen av din EAS-profil för Samsung KNOX och källprincipen. Synkroniseringsalternativet för Samsung Note stöds inte längre och det alternativet bör inte väljas i din profil. Se till att enheterna har fått tillräckligt med tid (upp till 24 timmar) för att bearbeta principen.

## <a name="next-steps"></a>Nästa steg
Om den här informationen inte är till någon hjälp, kan du även [få support för Microsoft Intune](get-support.md).
