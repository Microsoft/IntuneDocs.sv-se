---
title: Felsöka e-postprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Se vanliga problem och lösningar med e-postprofiler i Microsoft Intune, inklusive duplicerade e-postprofiler och fel på Samsung KNOX Standard Android-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a19830130f992a002b73402f5e13a8f062539917
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512678"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Vanliga problem och lösningar med e-postprofiler i Microsoft Intune

Se några vanliga problem med e-postprofiler samt hur du felsöker och löser dem.

## <a name="what-you-need-to-know"></a>Vad du behöver veta

- E-postprofiler distribueras för den användare som har registrerat enheten. För att konfigurera e-postprofilen använder Intune egenskaperna Azure Active Directory (AD) i användarens e-postprofil under registreringen. Det kan vara en lämplig resurs att [lägga till e-postinställningar till enheter](email-settings-configure.md).
- För Android Enterprise, distribuera Gmail eller Nine for Work med hjälp av Google Play Butik. [Lägg till hanterade Google Play-appar](../apps/apps-add-android-for-work.md) anger stegen.
- Microsoft Outlook för iOS/iPad och Android stöder inte e-postprofiler. Distribuera i stället en konfigurationsprincip för appar. Mer information finns i [Konfigurationsinställning för Outlook](../apps/app-configuration-policies-outlook.md).
- E-postprofiler som är riktade till enhetsgrupper (inte användargrupper) kan inte levereras till enheten. När enheten har en primär användare bör enhetsmålen fungera. Om e-postprofilen innehåller användarcertifikat, måste du vara säker på att rikta in användargrupper.
- Användare kan uppmanas att ange sitt lösenord för e-postprofilen upprepade gånger. I det här scenariot markerar du alla certifikat som refereras i e-postprofilen. Om något av certifikaten inte är riktat mot en användare, försöker Intune att distribuera e-postprofilen igen.

## <a name="device-already-has-an-email-profile-installed"></a>Enheten har redan en e-postprofil installerad

Om användare skapar en e-postprofil innan de registreras i Intune eller Office 365 MDM, kanske e-postprofilen som distribueras av Intune inte fungerar som förväntat:

- **iOS/iPadOS**: Intune identifierar en befintlig, duplicerad e-postprofil baserat på värdnamn och e-postadress. Den användarskapade e-postprofilen blockerar distributionen av den Intune-skapade profilen. Det här är ett vanligt problem eftersom iOS/iPadOS-användare vanligtvis skapar en e-postprofil först och sedan registrerar sig. Företagsportalappen visar att användaren inte är kompatibel och kan uppmana användaren att ta bort e-postprofilen.

  Användaren bör ta bort sin e-postprofil så att Intune-profilen kan distribueras. Förhindra det här problemet genom att be dina användare att registrera sig så att Intune kan distribuera e-postprofilen. Användarna kan därefter skapa sin e-postprofil.

- **Windows**: Intune identifierar en befintlig, duplicerad e-postprofil baserat på värdnamn och e-postadress. Intune skriver över den befintliga e-postprofilen som skapats av användaren.

- **Samsung KNOX Standard**: Intune identifierar ett duplicerat e-postkonto baserat på e-postadressen och skriver över det med Intune-profilen. Om användaren konfigurerar kontot skrivs det över igen av Intune-profilen. Detta kan orsaka förvirring för användaren vars kontokonfiguration skrivs över.

Samsung KNOX använder inte värdnamn för att identifiera profilen. Vi rekommenderar att du inte skapar flera e-postprofiler som ska distribueras till samma e-postadress på olika värdar, eftersom de kommer att skriva över varandra.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Fel 0x87D1FDE8 för KNOX Standard-enhet

**Problem**: När en e-postprofil för Exchange Active Sync har skapats och distribuerats för Samsung KNOX Standard till olika Android-enheter så visas felet **0x87D1FDE8** eller **Åtgärden misslyckades** på enhetens egenskaper > princip-flik.

Granska konfigurationen av din EAS-profil för Samsung KNOX och källprincipen. Synkroniseringsalternativet Samsung Note stöds inte längre och det alternativet bör inte väljas i din profil. Se till att enheterna har fått tillräckligt med tid (upp till 24 timmar) för att bearbeta principen.

## <a name="unable-to-send-images-from--email-account"></a>Det går inte att skicka bilder från e-postkontot

Användare med automatiskt konfigurerade e-postkonton kan inte skicka foton eller bilder från sina enheter. Detta kan hända om **Tillåt att e-post skickas från tredjepartsprogram** inte är aktiverat.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler**.
3. Välj din e-postprofil > **Egenskaper** > **Inställningar**.
4. Ange alternativet **Tillåt att e-post skickas från tredjepartsprogram**  till **Aktivera**.

## <a name="next-steps"></a>Nästa steg

Få [support från Microsoft](../fundamentals/get-support.md) eller använd [community-forumen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
