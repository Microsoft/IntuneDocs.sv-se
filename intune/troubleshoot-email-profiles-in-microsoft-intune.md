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
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2246e3f6faa853f620327558a7faf4dc9d6a6e85
ms.sourcegitcommit: 43ba5a05b2e1dc1997126d3574884f65cde449c7
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67197512"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Vanliga problem och lösningar med e-postprofiler i Microsoft Intune

Se några vanliga problem med e-postprofiler samt hur du felsöker och löser dem.

## <a name="what-you-need-to-know"></a>Vad du behöver veta

- E-postprofiler distribueras för den användare som registrerat enheten. Om du vill konfigurera e-postprofilen använder Intune i Azure Active Directory (AD)-egenskaper i e-postprofil för användaren under registreringen. [Lägg till e-postinställningar på enheter](email-settings-configure.md) kan vara en bra resurs.
- När du har migrerat från Configuration Manager-hybrid till fristående Intune kvar e-postprofilen från Configuration Manager-hybrid på enheten under 7 dagar. Det här beteendet är förväntat. Om du behöver en e-postprofil som har tagits bort tidigare kan du kontakta [Intunes support](get-support.md).
- För Android-företag, distribuera Gmail- eller nio för arbete med hjälp av den hanterade Google Play Store. [Lägg till hanterad Google Play appar](apps-add-android-for-work.md) innehåller stegen.
- Microsoft Outlook för iOS och Android stöder inte e-postprofiler. I stället distribuera en princip för appkonfiguration. Mer information finns i [Outlook konfigurationsinställning](app-configuration-policies-outlook.md).
- E-postprofiler som är riktade till enhetsgrupper (inte användargrupper) kan inte levereras till enheten. När enheten har en primär användare kan ska sedan riktar in sig på enheten fungera. Om e-postprofilen innehåller certifikat, måste du målgrupper.
- Användare kan uppmanas att ange sitt lösenord för e-postprofilen upprepade gånger. Kontrollera alla certifikat som refereras till i e-postprofilen i det här scenariot. Om något av certifikaten inte är riktat mot en användare försöker Intune om du vill distribuera e-postprofilen.

## <a name="device-already-has-an-email-profile-installed"></a>Enheten har redan en e-postprofil installerad

Om användare skapar en e-postprofil innan de registrerats i Intune eller Office 365 MDM, kan inte e-postprofilen som distribuerats av Intune fungerar som förväntat:

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
3. Välj din e-postprofil > **egenskaper** > **inställningar**.
4. Ange den **Tillåt e-post skickas från tredjepartsprogram** att ställa in **aktivera**.

### <a name="configuration-manager-hybrid"></a>Configuration Manager-hybrid

1. Öppna Configuration Manager-konsolen > **Tillgångar och efterlevnad**.

2. Expandera **Översikt** > **Kompatibilitetsinställningar** > **Åtkomst till företagsresurs** och välj **E-postprofiler**.

3. Högerklicka på e-postprofilen och öppna **Egenskaper**.

4. Välj **Tillåt att e-post skickas från tredjepartsprogram** på fliken **Synkroniseringsinställningar**.

## <a name="next-steps"></a>Nästa steg

Få [support från Microsoft](get-support.md) eller använd [community-forumen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
