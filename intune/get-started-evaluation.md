---
title: "Komma igång med Intune"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ef58e46118a0a44609abba5de4986b5a1526a151
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2017
---
# <a name="what-is-microsoft-intune"></a>Vad är Microsoft Intune?

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

![Microsoft Intune i Azure-portalen](./media/generic-intune-azure.png)

Microsoft Intune är en ny tjänst från Azure. Den tillhandahåller verktyg för hantering av din organisations mobila enheter, datorer och appar – sådant som [uppdateras regelbundet](whats-new.md). Utöver den moderna Azure-konsolen kan du också använda den klassiska konsolen. Den klassiska konsolen utgör den första versionen av Intune och används fortfarande när du ska [hantera Windows-datorer med Intune-programklienten](/intune-classic/deploy-use/pc-management-comparison.md). Den klassiska portalen är inbyggd i Silverlight och används till ett fåtal aktiviteter. Allt annat, inklusive hantering av mobila enheter och appar, sker i Azure-portalen. Guiden för att komma igång leder dig igenom de grundläggande arbetsuppgifter som du behöver utföra för börja använda Intune i Azure-portalen.

![Hjälp- och supportbladet finns längst ned i listan över åtgärder i vänstra sidopanelen i Intune.](./media/intune-azure-help-support-closeup.png)

## <a name="what-does-intune-in-the-azure-portal-provide"></a>Funktioner som tillhandahålls av Intune i Azure-portalen

Intune i Azure-portalen tillhandahåller följande funktioner:

* En integrerad konsol för alla dina [EMS-komponenter (Enterprise Mobility + Security)](https://docs.microsoft.com/enterprise-mobility-security)
* En HTML-baserad konsol byggd på webbstandarder som stöder [moderna webbläsare](supported-devices-browsers.md)
* [Azure Active Directory-grupper](groups-get-started.md) för att ge kompatibilitet åt alla dina Azure-program
* Automatisering via [Microsoft Graph API](intune-graph-apis.md)

## <a name="prerequisites"></a>Förutsättningar

Du måste ha en Intune-administratör och ett klientkonto aktiverat innan du börjar. Du kan registrera dig för dessa konton [här](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20). Alla befintliga prenumeranter kan också utföra aktiviteter i liveklienten. Kontrollera att du bara arbetar med testenheter!

Du måste också säkerställa att du är global administratör för din organisation, så att du får utföra alla aktiviteter i guiden.
