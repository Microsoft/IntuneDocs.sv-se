---
# required metadata

title: Översikt över applivscykeln | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Översikt över applivscykeln

Applivscykeln i Intune börjar när en app läggs till och fortsätter genom fler faser tills du tar bort dem.

![Applivscykeln](./media/applifecycle_nobg.png "the Intune app lifecycle")

## Lägg till

Det första steget i appdistribution är att lägga till de appar som du vill hantera och distribuera i Intune. Det finns många olika apptyper som du kan arbeta med, men de grundläggande procedurerna är samma. Med Intune kan du lägga till appar för både [registrerade enheter](add-apps-for-mobile-devices-in-microsoft-intune.md) och [Windows-datorer som du hanterar med Intune-klientprogramvaran](add-apps-for-windows-pcs-in-microsoft-intune.md).

## Distribuera

När du har lagt till appen i Intune kan du sedan [distribuera den till enheter som du hanterar](deploy-apps.md). I Intune är den här processen enkel och när appen har distribuerats kan du [övervaka framgången](monitor-apps-in-microsoft-intune.md) för distributionen från Intune-administrationskonsolen. Dessutom kan du i vissa appbutiker, till exempel appbutikerna för [Apple](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md) och [Windows](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md), köpa applicenser gruppvis till företaget. Intune kan synkronisera data med dessa butiker så att du kan distribuera och spåra licensanvändning för dessa typer av appar direkt från Intune-administrationskonsolen.

## Konfigurera

Som en del av applivscykeln släpps regelbundet nya versioner av appar. Intune tillhandahåller verktyg för att enkelt [uppdatera appar](update-apps-using-microsoft-intune.md) som du har distribuerat till en senare version. Dessutom kan du i vissa appar konfigurera ytterligare funktioner, till exempel:
- [Konfigurationsprinciper för iOS-appar](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md) gör att du kan ange inställningar för kompatibla iOS-appar som används när appen körs. En app kan till exempel kräva specifika inställningar för anpassning eller namnet på en server som den ska ansluta till.
- [Hanterade webbläsarprinciper](manage-internet-access-using-managed-browser-policies.md) hjälper dig att konfigurera inställningar för den hanterade webbläsaren i Intune som ersätter enhetens standardwebbläsare och du kan begränsa vilka webbplatser som användarna kan besöka.

## Skydda

Intune ger många sätt att skydda data i dina appar. De viktigaste metoderna är:
- [Villkorlig åtkomst](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) gör att du kan styra åtkomsten till e-post och andra tjänster utifrån villkor du anger som enhetstyper, eller efterlevnad av en [princip för enhetsefterlevnad](introduction-to-device-compliance-policies-in-microsoft-intune.md) som du har distribuerat.
- [Hantering av mobilprogram (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md) fungerar med enskilda appar för att skydda de företagsdata som de använder. Du kan till exempel begränsa kopiering av data mellan ohanterade appar och appar som du hanterar, eller förhindra att appar körs på enheter som har jailbreakats eller rotats.

## Pensionera

Så småningom är det troligt att appar som du har distribuerat blir inaktuella och måste tas bort. Intune gör det enkelt att [dra tillbaka appar från tjänsten](retire-apps-using-microsoft-intune.md).


<!--HONumber=May16_HO1-->


