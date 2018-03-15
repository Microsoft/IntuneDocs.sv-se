---
title: Introduktion till Intune i Azure-portalen
titlesuffix: 
description: "Microsoft Intune är tillgängligt i Azure Portal. Läs om grunderna för Intune i Azure-portalen."
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/28/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: 
ms.openlocfilehash: c9c8485a3ab68be745c8903659df0fd35af2a644
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2018
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Introduktion till Microsoft Intune i Azure-portalen


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune är tillgängligt i Azure Portal, precis som många andra Azure-tjänster. Genom att välja **Intune** i Azure Portal kan du hantera din organisations mobila enheter, datorer och appar.

>[!NOTE] 
> Om du har använt en tidigare version av Microsoft Intune så kan följande information vara till hjälp:
    * [Var tog mina saker vägen i Azure? ](ui-changes.md) är en referens till specifika arbetsflöden och användargränssnitt som har ändrats med övergången till Azure.
    * [Klassiska Intune-grupper i Azure portal](groups-get-started.md) beskriver konsekvenserna av en övergång till Azure Active Directory-säkerhetsgrupper för grupphantering.

Exempel på viktiga funktioner i Microsoft Intune-miljön i Azure Portal:

- En integrerad konsol för alla dina EMS-komponenter (Enterprise Mobility + Security)
- En HTML-baserad konsol byggd på webbstandarder
- Microsoft Graph API-stöd för att automatisera många åtgärder
- Azure Active Directory (AD)-grupper för att ge kompatibilitet åt alla dina Azure-program
- Stöd för de flesta moderna webbläsare

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

## <a name="microsoft-intune-in-the-azure-portal"></a>Microsoft Intune i Azure-portalen

Du hittar Microsoft Intune-tjänsten på [Azure Portal](https://portal.azure.com). Det finns många tjänster i Azure och några av dem kommer du nog inte använda regelbundet. [Komma igång med Intune på Azure Portal](get-started-azure.md) innehåller en snabbguide som hjälper dig att anpassa din portal.

## <a name="the-microsoft-intune-documentation"></a>Microsoft Intune-dokumentationen

Det här avsnittet och hela dokumentationsuppsättningen för Microsoft Intune uppdateras kontinuerligt. Om du har några förslag är du välkommen att lämna feedback i kommentarsavsnittet. Vi vill gärna att du hör av dig.

Dokumentationen visar layouten för Microsoft Intune i Azure Portal (visas nedan) så att du lättare hittar den information du behöver.

![Arbetsbelastningar i Azure-portalen](./media/azure-portal-workloads.png)

### <a name="documentation-guide"></a>Dokumentationsguide

Använd följande tabell för att snabbt hitta och förstå huvudområdena i Microsoft Intune.

| Avsnitt                                                      | Description                                                                                                                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Introduktion och att komma igång](introduction-intune.md)       | Förstå grunderna i Intune, inklusive:<br /> – Vanliga lösningar<br /> – Hur Microsoft Intune fungerar<br /> – Enhetshantering i Intune<br /> – Apphantering i Intune<br /> – Enterprise Mobility Management (EMM) med och utan enhetsregistrering                                                         |
| [Planera och utforma](planning-guide.md)                         | Vägledning som hjälper dig att planera och utforma din Microsoft Intune-miljö.                                                                                                                                                                                                             |
| [Enhetsregistrering](device-enrollment.md)                    | Förstå hur Microsoft Intune hjälper dig att hantera personalens enheter genom att registrera enheter i Intune-tjänsten. Det finns flera metoder för att registrera personalens enheter.                                                                                                         |
| [Efterlevnad för enhet](device-compliance.md)                    | Efterlevnadsprinciper definierar de regler och inställningar som en Intune-enhet måste följa för att anses vara kompatibla med Microsoft Intune. Några exempel på efterlevnad är till exempel att kräva ett lösenord för enhetsåtkomst, kryptera enheter eller kräva en lägsta version av operativsystemet. |
| [Enhetskonfiguration](device-profiles.md)                   | Konfigurera inställningar och funktioner på alla enheter som hanteras med Microsoft Intune genom att skapa enhetsprofiler. Du kan till exempel konfigurera funktioner som meddelanden, delning av data, e-postsupport, Wi-Fi-anslutning, certifikat och slutpunktsskydd.              |
| [Enheter](device-management.md)                              | Se till att enheter som du hanterar tillhandahåller de resurser som slutanvändarna behöver för att utföra sitt arbete, samtidigt som du skyddar företagets data så att de inte utsätts för risk. Hantera enheter genom att granska personalens enhetsinventering och utföra åtgärder på enheterna via en fjärranslutning.                                                      |
| [Mobilappar](app-management.md)                             | Förstå hur du lägger till, distribuerar, övervakar, konfigurerar och skyddar appar.                                                                                                                                                                                                                             |
| [Villkorlig åtkomst](conditional-access.md)                  | Definiera enhetsbaserade och appbaserade villkor som förhindrar åtkomst till företagets data.                                                                                                                                                                                                            |
| [Användare](users-add.md)                                        | Lär dig hur du lägger till användare av enheter och appar som du hanterar.                                                                                                                                                                                                                                           |
| [Grupper](groups-get-started.md)                              | Läs mer om hur du kan skapa och hantera grupper med Intune. Med hjälp av grupper kan du snabbt tilldela principer för att konfigurera och skydda enheter och appar.                                                                                                                                             |
| [Intune-roller](role-based-access-control.md)                 | Lär dig hur du kontrollerar vem som kan utföra olika Intune-åtgärder och hur de här åtgärderna tillämpas. Du kan antingen använda de inbyggda roller täcker vissa vanliga scenarier för Intune eller du kan skapa egna roller.                                                                                 |
| [Programuppdateringar](windows-update-for-business-configure.md) | Lär dig hur du konfigurerar programuppdateringar för Windows 10-enheter.                                                                                                                                                                                                                                  |

## <a name="whats-new"></a>Nyheter

Läs informationen i [Nyheter](whats-new.md) och lär dig mer om de senaste funktionerna i Microsoft Intune.
