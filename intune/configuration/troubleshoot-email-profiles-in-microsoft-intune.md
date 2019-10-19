---
title: Felsöka e-postprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Se vanliga problem och lösningar med e-postprofiler i Microsoft Intune, inklusive duplicerade e-postprofiler och fel på Samsung KNOX Standard Android-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/17/2019
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
ms.openlocfilehash: 101f414955a3b60d22003f61678854fecc16910d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506578"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Vanliga problem och lösningar med e-postprofiler i Microsoft Intune

Se några vanliga problem med e-postprofiler samt hur du felsöker och löser dem.

## <a name="what-you-need-to-know"></a>Vad du behöver veta

- E-postprofiler distribueras för den användare som registrerat enheten. Om du vill konfigurera e-postprofilen använder Intune egenskaperna Azure Active Directory (AD) i e-postprofilen för användaren under registreringen. Det kan vara en lämplig resurs att [lägga till e-postinställningar till enheter](email-settings-configure.md) .
- Efter migrering från Configuration Manager hybrid till Intune fristående är e-postprofilen från Configuration Manager hybrid kvar på enheten i 7 dagar. Det här beteendet är förväntat. Kontakta [Intunes support](../fundamentals/get-support.md)om du behöver ta bort e-postprofilen tidigare.
- För Android Enterprise, distribuera Gmail eller nio för arbete med hjälp av den hanterade Google Play Butik. [Lägg till hanterade Google Play-appar](../apps/apps-add-android-for-work.md) listar stegen.
- Microsoft Outlook för iOS och Android stöder inte e-postprofiler. Distribuera i stället en konfigurations princip för appar. Mer information finns i [konfigurations inställningen för Outlook](../apps/app-configuration-policies-outlook.md).
- E-postprofiler som är riktade till enhets grupper (inte användar grupper) kan inte levereras till enheten. När enheten har en primär användare bör enhets målen fungera. Om e-postprofilen innehåller användar certifikat, måste du vara säker på att det är mål för användar grupper.
- Användare kan uppmanas att ange sitt lösen ord för e-postprofilen upprepade gånger. I det här scenariot markerar du alla certifikat som refereras i e-postprofilen. Om något av certifikaten inte är riktat mot en användare, försöker Intune att distribuera e-postprofilen.

## <a name="device-already-has-an-email-profile-installed"></a>Enheten har redan en e-postprofil installerad

Om användare skapar en e-postprofil innan de registreras i Intune eller Office 365 MDM, kanske e-postprofilen som distribueras av Intune inte fungerar som förväntat:

- **iOS**: Intune identifierar en befintlig, duplicerad e-postprofil baserat på värdnamn och e-postadress. Den användarskapade e-postprofilen blockerar distributionen av den Intune-skapade profilen. Det här är ett vanligt problem eftersom iOS-användare vanligtvis skapar en e-postprofil först och sedan registrerar sig. Företagsportalappen visar att användaren inte är kompatibel och kan uppmana användaren att ta bort e-postprofilen.

  Användaren bör ta bort sin e-postprofil så att Intune-profilen kan distribueras. Förhindra det här problemet genom att be dina användare att registrera sig så att Intune kan distribuera e-postprofilen. Användarna kan därefter skapa sin e-postprofil.

- **Windows**: Intune identifierar en befintlig, duplicerad e-postprofil baserat på värdnamn och e-postadress. Intune skriver över den befintliga e-postprofilen som skapats av användaren.

- **Samsung KNOX Standard**: Intune identifierar ett duplicerat e-postkonto baserat på e-postadressen och skriver över det med Intune-profilen. Om användaren konfigurerar kontot skrivs det över igen av Intune-profilen. Detta kan orsaka förvirring för användaren vars kontokonfiguration skrivs över.

Samsung KNOX använder inte värdnamn för att identifiera profilen. Vi rekommenderar att du inte skapar flera e-postprofiler som ska distribueras till samma e-postadress på olika värdar, eftersom de kommer att skriva över varandra.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Fel 0x87D1FDE8 för KNOX Standard-enhet

**Problem**: När en e-postprofil för Exchange Active Sync har skapats och distribuerats för Samsung KNOX Standard till olika Android-enheter så visas felet **0x87D1FDE8** eller **Åtgärden misslyckades** på enhetens egenskaper > princip-flik.

Granska konfigurationen av din EAS-profil för Samsung KNOX och källprincipen. Synkroniseringsalternativet Samsung Note stöds inte längre och det alternativet bör inte väljas i din profil. Se till att enheterna har fått tillräckligt med tid (upp till 24 timmar) för att bearbeta principen.

## <a name="unable-to-send-images-from--email-account"></a>Det går inte att skicka bilder från e-postkontot

Användare med automatiskt konfigurerade e-postkonton kan inte skicka foton eller bilder från sina enheter. Detta kan hända om **Tillåt att e-post skickas från tredjepartsprogram** inte är aktiverat.

### <a name="intune-solution"></a>Intune-lösning

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler**.
3. Välj din e-postprofil > **egenskaper**  > **Inställningar**.
4. Ange alternativet **Tillåt att e-post skickas från tredjepartsprogram** till **aktive**rad.

### <a name="configuration-manager-hybrid"></a>Configuration Manager-hybrid

1. Öppna Configuration Manager-konsolen > **Tillgångar och efterlevnad**.

2. Expandera **Översikt** > **Kompatibilitetsinställningar** > **Åtkomst till företagsresurs** och välj **E-postprofiler**.

3. Högerklicka på e-postprofilen och öppna **Egenskaper**.

4. Välj **Tillåt att e-post skickas från tredjepartsprogram** på fliken **Synkroniseringsinställningar**.

## <a name="next-steps"></a>Nästa steg

Få [support från Microsoft](../fundamentals/get-support.md) eller använd [community-forumen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
