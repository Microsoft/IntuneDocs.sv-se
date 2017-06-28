---
title: "Felsöka e-postprofiler"
description: "Problem relaterade till e-postprofiler och hur du felsöker och löser dem."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: f79ebec4dea17bd03b88d97aa1d7b30a58e35cdb
ms.contentlocale: sv-se
ms.lasthandoff: 06/08/2017


---

# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Felsöka e-postprofiler i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet innehåller information om problem relaterade till e-postprofiler och hur du felsöker och löser dem.

Om du inte lyckas lösa problemet med hjälp av den här informationen läser du [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md), som beskriver hur du kan få hjälp på fler sätt.


## <a name="unable-to-send-images-from--email-account"></a>Det går inte att skicka bilder från e-postkontot
Användare med automatiskt konfigurerade e-postkonton kan inte skicka bilder från sina enheter.
Detta inträffar när alternativet **Tillåt att e-post skickas från tredjepartsprogram** inte är aktiverat.

### <a name="intune-solution"></a>Intune-lösning

1.  Öppna Microsoft Intune-administrationskonsolen och välj arbetsbelastningen **Princip** &gt;**Konfigurationsprincip**.

2.  Välj e-postprofilen och klicka på **Redigera**.

3.  Välj **Tillåt att e-post skickas från tredjepartsprogram.**

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager integrerat med Intune

1.  Öppna Configuration Manager-konsolen &gt;**Tillgångar och efterlevnad**.

2.  Expandera **Översikt** -&gt; **Efterlevnadsinställningar** -&gt; **Åtkomst till företagsresurser** och välj **E-postprofiler**.

3.  Högerklicka på e-postprofilen och öppna **Egenskaper**.

4.  Välj **Tillåt att e-post skickas från tredjepartsprogram** på fliken **Synkroniseringsinställningar**.


## <a name="device-already-has-an-email-profile-installed"></a>Enheten har redan en e-postprofil installerad

Om användaren har installerat en e-postprofil före etablering av en profil av Intune, beror resultatet av e-postprofildistributionen i Intune på enhetsplattformen:

-**iOS**: Intune identifierar en befintlig, duplicerad e-postprofil baserat på värdnamn och e-postadress. Den duplicerade e-postprofilen som skapats av användaren blockerar distributionen av en profil som skapats av Intune-administratören. Det här är ett vanligt problem eftersom iOS-användare vanligtvis skapar en e-postprofil och sedan gör registreringen. Företagsportalen informerar användaren om att de inte uppfyller kraven på grund av den manuellt konfigurerade e-postprofilen, och användaren uppmanas att ta bort profilen. Användaren bör ta bort e-postprofilen så att Intune-profilen kan distribueras. För att förhindra det här problemet ber du användarna att göra registreringen före installation av en e-postprofil så att Intune kan distribuera profilen.

-**Windows**: Intune identifierar en befintlig, duplicerad e-postprofil baserat på värdnamn och e-postadress. Intune skriver över den befintliga e-postprofilen som skapats av användaren.

-**Samsung KNOX Standard**: Intune identifierar ett duplicerat e-postkonto baserat på e-postadressen och skriver över det med Intune-profilen. Om användaren konfigurerar det kontot skrivs det över igen av Intune-profilen. Observera att detta kan orsaka förvirring för användaren vars kontokonfiguration skrivs över.

Eftersom Samsung KNOX inte använder värdnamn för att identifiera profilen rekommenderar vi att du inte skapar flera e-postprofiler som ska distribueras till samma e-postadress på olika värdar, eftersom de kommer att skriva över varandra.

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>Fel 0x87D1FDE8 för KNOX Standard-enhet
**Problem**: När en Exchange Active Sync-e-postprofil har skapats och distribuerats för Samsung KNOX Standard för olika Android-enheter rapporteras felet **0x87D1FDE8** eller **Reparationen misslyckades** på fliken Egenskaper &gt; Princip på enheten.

Granska konfigurationen av din EAS-profil för Samsung KNOX och källprincipen. Synkroniseringsalternativet för Samsung Note stöds inte längre och det alternativet bör inte väljas i din profil. Se till att enheterna har fått tillräckligt med tid för att behandla principen, upp till 24 timmar.

## <a name="next-steps"></a>Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

