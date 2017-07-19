---
title: Introduktion till Intune i Azure Portal
titleSuffix: Intune on Azure
description: "Lär dig grunderna om Intune i Azure-portalen och hur det kan hjälpa dig att hantera dina enheter.”"
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 06/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7549f3277c23c3951090502f2babfe7c47b0a201
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Introduktion till Microsoft Intune i Azure-portalen


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune finns nu i Azure-portalen och detta innebär att de arbetsflöden och de funktioner som du har vant dig vid har ändrats.
Den nya portalen erbjuder nya och uppdaterade funktioner i Azure Portal där du kan hantera din organisations mobila enheter, datorer och appar.

> [!IMPORTANT]
> **Ser du inte den nya portalen?**<br>
> Befintliga klienter ska migreras till den nya miljön. Ett meddelande visas i Office-meddelandecenter innan din klient migreras.
>
> Intune-konton som skapats före januari 2017 måste migreras vid ett tillfälle innan registrerade Apple-arbetsflöden finns tillgängliga i Azure. Schemat för migrering har ännu inte tillkännagivits. Om ditt befintliga konto inte kan komma åt Azure-portalen, rekommenderar vi att du skapar ett utvärderingskonto.
>
> Granska listan över möjliga blockerare https://blogs.technet.microsoft.com/intunesupport/2017/05/17/intune-migration-blockers-for-grouping-targeting/


Du kan hitta information om den nya portalen i det här biblioteket som uppdateras kontinuerligt. Om du har några förslag är du välkommen att lämna feedback i kommentarsavsnittet. Vi vill gärna att du hör av dig.

Viktiga nya funktioner:

- En integrerad konsol för alla dina EMS-komponenter (Enterprise Mobility + Security)
- En HTML-baserad konsol byggd på webbstandarder
- Microsoft Graph API-stöd för att automatisera många åtgärder
- Azure Active Directory (AD)-grupper för att ge kompatibilitet åt alla dina Azure-program
- Stöd för de flesta moderna webbläsare

Om du letar efter dokumentation för den klassiska Intune-konsolen kan du gå till [Dokumentationsbiblioteket för Microsoft Intune](https://docs.microsoft.com/intune-classic/).

## <a name="before-you-start"></a>Innan du börjar

Du måste ha ett administratörs- och ett klientkonto för Intune om du vill använda Intune i Azure-portalen. [Registrera dig för ett konto](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) om du inte redan har ett.

## <a name="supported-web-browsers-for-the-azure-portal"></a>Webbläsare som stöds för Azure-portalen

Azure-portalen kan köras på de flesta moderna datorer, Mac-datorer och surfplattor. Mobiltelefoner stöds inte.
För närvarande stöds följande webbläsare:

- Microsoft Edge (senaste versionen)
- Microsoft Internet Explorer 11
- Safari (senaste versionen, endast Mac)
- Chrome (senaste versionen)
- Firefox (senaste versionen)

Kolla på [Azure Portal](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices) för den senaste informationen om vilka webbläsare som stöds.

## <a name="whats-in-this-library"></a>Vad finns i det här biblioteket?

Dokumentationen visar layouten för Intune-portalen för att göra det lättare att hitta den information du behöver.

![Arbetsbelastningar i Azure-portalen](./media/azure-portal-workloads.png)

### <a name="introduction-and-get-started"></a>Introduktion och att komma igång
Det här avsnittet innehåller [en introduktion](introduction-intune.md) som hjälper dig att komma igång med Intune.
### <a name="plan-and-design"></a>Planera och utforma
Information som hjälper dig att [planera och utforma](/intune-classic/plan-design/introduction) din Intune-miljö.
### <a name="device-enrollment"></a>Enhetsregistrering
[Hur du får dina enheter att hanteras av Intune](device-enrollment.md).
### <a name="device-compliance"></a>Efterlevnad för enhet
[Definiera en efterlevnadsnivå för dina enheter och rapportera sedan om alla enheter som inte är kompatibla](device-compliance.md).
### <a name="device-configuration"></a>Enhetskonfiguration
[Lär dig om profilerna som du kan använda för att konfigurera inställningar och funktioner på enheter som du hanterar](device-profiles.md).
### <a name="devices"></a>Egenskaper
[Bekanta dig med de enheter du hanterar med hjälp av inventering och rapporter](device-management.md).
### <a name="mobile-apps"></a>Mobilappar
[Så publicerar, hanterar, konfigurerar och skyddar du appar](app-management.md).
### <a name="conditional-access"></a>Villkorlig åtkomst
[Begränsa åtkomsten till Exchange-tjänster utifrån de villkor som du anger](conditional-access.md).
### <a name="on-premises-access"></a>Lokal åtkomst
[Konfigurera åtkomst till Exchange ActiveSync och Exchange On-premises](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)
### <a name="users"></a>Användare
[Lär dig mer om användarna av de enheter du hanterar och sortera resurser i grupper](user-management.md).
### <a name="groups"></a>Grupper
[Läs om hur du kan använda Azure Active Directory-grupper med Intune](groups-get-started.md)
### <a name="intune-roles"></a>Intune-roller
[Kontrollera vem som kan utföra olika Intune-åtgärder och vem dessa åtgärder gäller för](role-based-access-control.md). Du kan antingen använda de inbyggda roller täcker vissa vanliga scenarier för Intune eller du kan skapa egna roller.
### <a name="software-updates"></a>Programuppdateringar
[Läs om hur du konfigurerar programuppdateringar för Windows 10-enheter](windows-update-for-business-configure.md).



## <a name="whats-new"></a>Nyheter

[Nyheter i Intune](whats-new.md).
