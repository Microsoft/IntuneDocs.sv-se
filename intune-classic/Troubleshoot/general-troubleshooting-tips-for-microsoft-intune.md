---
title: Allmänna felsökningstips
description: Allmänna resurser för att lösa problem med Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/08/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d5d55f6c3efabdde51b5627d5ddd409c2b282f6c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="general-troubleshooting-tips-for-microsoft-intune"></a>Allmänna felsökningstips för Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Det kan hända att du upptäcker problem med konfigurationen eller med klientenheter efter att du har distribuerat Microsoft Intune. Använd följande resurser för att identifiera vad som orsakar problemet så att du kan lösa det.

> [!NOTE]
> Om du vill skapa en supportbegäran eller visa en befintlig begäran [går du till Office 365-administrationscentret](https://portal.office.com/admin/default.aspx). Mer information om supportalternativen finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## <a name="define-the-problem"></a>Definiera problemet

-   Vad är problemet?

-   Vem stöter på problemet, och på vilka plattformar och enheter?

-   Fungerade enheten korrekt tidigare?

-   Vilka ändringar gjorde du i Intune eller enhetskonfigurationen?

-   Har andra ändringar än konfigurationsändringarna gjorts i den aktuella miljön?

-   Hur ofta uppstår problemet och förekommer det sporadiska eller hela tiden?

-   Kan användaren ha autentiseringsproblem? Om det är en möjlighet kontrollerar du om användaren kan logga in till andra tjänster som använder Azure Active Directory. Kontrollera också om användaren kan logga in från en annan enhet.

-   Har du kontrollerat status för tjänsten? Du kan övervaka hälsotillståndet för Intune-tjänsten i den [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx). Välj **Tjänstens hälsa** i det vänstra fönstret.

## <a name="collect-available-data"></a>Samla in tillgängliga data

- Med hjälp av följande resurser kan du lära dig att samla in enhetens loggar:
  - [Skicka loggar med Android-diagnostikdata till IT-administratören via en USB-kabel](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Skicka loggar med Android-diagnostikdata till IT-administratören via e-post](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [Skicka Android-registreringsfel till IT-administratören](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)
  - [Skicka iOS-registreringsfel till IT-administratören](/intune-user-help/send-errors-to-your-it-admin-ios)

- Du kan använda data från administratörskonsolen (t.ex. vid problem med principimplementering) för att undersöka den avsedda principen och principens status genom att följa anvisningarna i [Använda grupper för att hantera användare och enheter med Microsoft Intune](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## <a name="research-the-solution"></a>Undersök lösningen

-   Sök efter en lösning på webben. Om du till exempel får felmeddelandet 0x80073CF0 kan du söka på **technet intune 0x80073cf0** på webben för att läsa artikeln [Felsöka problem med appdistribution i Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md). Artikeln innehåller förslag på hur du åtgärdar det här felet.

-   Sök efter ett svar i [Intune TechNet-forumet](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  Om problemet inte har diskuterats tidigare kan du ställa din fråga och se vilka förslag community-medlemmarna kan ha.

-   Öppna en supportbegäran. Det är lättare för Intunes support att hjälpa dig att lösa ett problem om du har definierat problemet och samlat in tillgängliga data.

    Om du vill skapa en supportbegäran går du till [administrationscenter för Office 365](https://portal.office.com/admin/default.aspx). Mer information om supportalternativen finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## <a name="find-community-resources"></a>Hitta community-resurser
Du kan hitta annan användbar information i dessa gruppresurser:

-   [Överlevnadsguide till Microsoft Intune](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx) innehåller länkar till många resurser som kan hjälpa dig att konfigurera, underhålla och felsöka Intune.

-   [Intune-bloggen](http://blogs.technet.com/b/windowsintune/)

-   [Följ Intune på Twitter](https://twitter.com/MSIntune)

-   [Intune-forum](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### <a name="next-steps"></a>Nästa steg
Följande artiklar innehåller felsökningshjälp för specifika problem. Om den informationen inte hjälper kan du kontakta Microsofts support enligt beskrivningen i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

[Felsöka Endpoint Protection i Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Felsöka problem med åtkomst till företagsresurser med Microsoft Intune](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Felsöka problem med appdistribution i Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Felsöka enhetsregistrering i Intune](troubleshoot-device-enrollment-in-intune.md)

[Felsöka principer i Microsoft Intune](troubleshoot-policies-in-microsoft-intune.md)

[Felsöka klientinstallationen i Microsoft Intune](troubleshoot-client-setup-in-microsoft-intune.md)

[Felsöka programuppdateringar i Microsoft Intune](troubleshoot-software-updates-in-microsoft-intune.md)
