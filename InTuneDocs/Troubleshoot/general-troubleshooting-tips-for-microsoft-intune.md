---
# required metadata

title: Allmänna felsökningstips | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Allmänna felsökningstips för Microsoft Intune
Det kan hända att du upptäcker problem med konfigurationen eller med klienter efter att du har distribuerat Microsoft Intune. Resurserna nedan kan hjälpa dig att ta reda på vad som kan vara orsaken till problemet så att du kan lösa det.

> [!NOTE]
> Klicka [här](https://portal.office.com/admin/default.aspx) om du vill besöka administrationscentret för Office 365  där du kan skapa en supportbegäran eller visa en befintlig begäran. Mer information om supportalternativen finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).
## Definiera problemet

-   Vad är problemet?

-   Vem stöter på problemet, och på vilka plattformar och enheter?

-   Fungerade enheten korrekt tidigare?

-   Vilka ändringar gjorde du i Intune eller enhetskonfigurationen?

-   Tänk efter om andra ändringar än konfigurationsändringar har gjorts i den aktuella miljön.

-   Hur ofta uppstår problemet och förekommer det sporadiska eller hela tiden?

-   Kan användaren ha autentiseringsproblem? Om det är en möjlighet kontrollerar du om användaren kan logga in till andra tjänster som använder Azure Active Directory. Kontrollera också om användaren kan logga in från en annan enhet.

## Samla in tillgängliga data

-   Enhetsloggar. Lär dig mer om att samla in enhetsloggar i:
  - [Skicka loggar med Android-diagnostikdata till IT-administratören via USB-kabel](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Skicka loggar med Android-diagnostikdata till IT-administratören via e-post](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [Skicka Android-registreringsfel till IT-administratören](/intune/enduser/send-enrollment-errors-to-your-it-administrator-android)
  - [Skicka iOS-registreringsfel till IT-administratören](/intune/enduser/send-errors-to-your-it-admin-ios.md)

-   Data från administratörskonsolen. Vid problem relaterade till principimplementeringen bör du till exempel undersöka den avsedda principen och principens status genom att följa anvisningarna i [Använda grupper för att hantera användare och enheter med Microsoft Intune](/indune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## Undersök lösningen

-   Sök efter en lösning på webben. Om du till exempel får felmeddelandet 0x80073CF0 kan du söka på **technet intune 0x80073cf0** på webben så returneras artikeln [Felsöka problem med appdistributionen i Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md), där du får förslag på hur du kan lösa problemet

-   Du kan söka efter svar i [Intune TechNet-forumet](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  Om problemet inte har diskuterats tidigare kan du ställa din fråga och se vilka förslag community-medlemmarna kan ha.

-   Du kan öppna en supportbegäran. Det är lättare för Intunes support att hjälpa dig att lösa ett problem om du har definierat problemet och samlat in tillgängliga data.

    Om du vill skapa en supportbegäran klickar du [här](https://portal.office.com/admin/default.aspx) för att gå till administrationscenter för Office 365. Mer information om supportalternativen finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## Community-resurser
Du kan hitta annan användbar information i dessa gruppresurser:

-   [Överlevnadsguide till Microsoft Intune](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx) innehåller länkar till många resurser som kan hjälpa dig att konfigurera, underhålla och felsöka Intune.

-   [Intune-bloggen](http://blogs.technet.com/b/windowsintune/)

-   [Följ Intune på Twitter](https://twitter.com/MSIntune)

-   [Intune-forum](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

## Nästa steg
Artiklarna nedan innehåller felsökningshjälp för specifika problem. Om den informationen inte hjälper kan du kontakta Microsoft Support enligt beskrivningen i [Få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

[Troubleshoot Endpoint Protection in Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Felsökning av problem med åtkomst till företagsresurser med Microsoft Intune](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Felsöka problem med appdistributionen i Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Felsöka enhetsregistrering i Intune](troubleshoot-device-enrollment-in-intune.md)

[Felsökningsprinciper i Microsoft Intune](troubleshoot-policies-in-microsoft-intune.md)

[Felsöka klientinstallationen i Microsoft Intune](troubleshoot-client-setup-in-microsoft-intune.md)

[Felsökning av programuppdateringar i Microsoft Intune](troubleshoot-software-updates-in-microsoft-intune.md)
g


<!--HONumber=May16_HO1-->


