---
title: "Introduktion till Intune i förhandsversionen av Azure Portal"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig grunderna om Intune i förhandsversionen av Azure-portalen och hur det kan hjälpa dig att hantera dina enheter."
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 04/24/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 92e07a49205ffaf287fc3aa2da6a6376b75fda4f
ms.lasthandoff: 04/24/2017


---


# <a name="introduction-to-microsoft-intune-in-the-azure-portal-preview"></a>Introduktion till Microsoft Intune i förhandsversionen av Azure-portalen


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune flyttar till Azure-portalen och detta innebär att de arbetsflöden och de funktioner som du har vant dig vid kommer att ändras.
Den nya portalen erbjuder en förhandsversion av nya och uppdaterade funktioner i Azure Portal där du kan hantera din organisations mobila enheter, datorer och appar.
Alla Intune-funktioner kommer så småningom att flytta till Azure, men du kan utföra många Intune-aktiviteter i Azure-portalen redan idag. Eftersom det här är en förhandsversion kanske vissa funktioner inte finns i portalen ännu. Mer information finns i avsnittet [Nyheter](#what's-new).

> [!IMPORTANT]
> **Ser du inte den nya portalen?**<br>
> Vi har redan börjat lansera förhandsversionen till vissa klienter. Befintliga klienter kommer att migreras med start tidigt 2017. Du kommer att få ett meddelande i Office Message Center innan migreringen av din klientorganisation.


Du kommer att hitta ny produktdokumentationen i det här biblioteket och den kommer att uppdateras kontinuerligt. Om du har några förslag är du välkommen att lämna feedback i kommentarsavsnittet. Vi vill gärna att du hör av dig.

<!--- You can view the new Intune technical preview console in Azure at [portal.azure.com]. --->

Viktiga nya funktioner:

- En integrerad konsol för alla dina EMS-komponenter (Enterprise Mobility + Security)
- En HTML-baserad konsol byggd på webbstandarder
- Microsoft Graph API-stöd för att automatisera många åtgärder
- Azure Active Directory (AD)-grupper för att ge kompatibilitet åt alla dina Azure-program
- Stöd för de flesta moderna webbläsare

Om du letar efter dokumentation för den klassiska Intune-konsolen kan du gå till [Dokumentationsbiblioteket för Microsoft Intune](https://docs.microsoft.com/en-us/intune/).

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
Det här avsnittet innehåller information om [nyheter](/intune-azure/introduction/whats-new), [kända problem](/intune-azure/introduction/known-issues-in-the-intune-preview), [hur du kan få support](/intune-azure/introduction/how-to-get-support-for-microsoft-intune) och hur du [kommer igång med en kostnadsfri utvärderingsversion](/intune-azure/introduction/sign-up-free-trial-microsoft-intune) av Intune.
### <a name="plan-and-design"></a>Planera och utforma
Information som hjälper dig att [planera och utforma](/intune-azure/plan-and-design/get-started) din Intune-miljö.
### <a name="device-enrollment"></a>Enhetsregistrering
[Hur du får dina enheter att hanteras av Intune](/intune-azure/enroll-devices/what-is).
### <a name="device-compliance"></a>Efterlevnad för enhet
[Definiera en efterlevnadsnivå för dina enheter och rapportera sedan om alla enheter som inte är kompatibla](/intune-azure/set-device-compliance/what-is-device-compliance).
### <a name="device-configuration"></a>Enhetskonfiguration
[Lär dig om profilerna som du kan använda för att konfigurera inställningar och funktioner på enheter som du hanterar](/intune-azure/configure-devices/what-are-device-profiles).
### <a name="devices"></a>Egenskaper
[Bekanta dig med de enheter du hanterar med hjälp av inventering och rapporter](/intune-azure/manage-devices/what-is).
### <a name="mobile-apps"></a>Mobilappar
[Så publicerar, hanterar, konfigurerar och skyddar du appar](/intune-azure/manage-apps/what-is-app-management).
### <a name="conditional-access"></a>Villkorlig åtkomst
[Begränsa åtkomsten till Exchange-tjänster utifrån de villkor som du anger](/intune-azure/conditional-access/what-is-conditional-access).
### <a name="on-premises-access"></a>Lokal åtkomst
[Konfigurera åtkomst till Exchange ActiveSync och Exchange On-premises](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)
### <a name="users"></a>Användare
[Lär dig mer om användarna av de enheter du hanterar och sortera resurser i grupper](/intune-azure/manage-users/what-is).
### <a name="groups"></a>Grupper
[Läs om hur du kan använda Azure Active Directory-grupper med Intune](/intune-azure/manage-users/get-started-with-groups)
### <a name="intune-roles"></a>Intune-roller
[Kontrollera vem som kan utföra olika Intune-åtgärder och vem dessa åtgärder gäller för](/intune-azure/access-control/role-based-access-control). Du kan antingen använda de inbyggda roller täcker vissa vanliga scenarier för Intune eller du kan skapa egna roller.
### <a name="software-updates"></a>Programuppdateringar
[Läs om hur du konfigurerar programuppdateringar för Windows 10-enheter](/intune-azure/configure-devices/how-to-configure-windows-update-for-business).



## <a name="whats-new"></a>Nyheter

[Ta reda på vad är nytt i förhandsversionen](/intune-azure/introduction/whats-new).

