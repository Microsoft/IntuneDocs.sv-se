---
title: Nätverksslutpunkter för amerikanska myndigheters distributioner – Microsoft Intune
titleSuffix: ''
description: Granska slutpunkter för amerikanska myndigheter för Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9828b04ae30d8f35313564b93dfc9b997795bf76
ms.sourcegitcommit: 8d12ab22e23552f9addaef4c28b732fb211945a2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2019
ms.locfileid: "68306724"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Slutpunkter för amerikanska myndigheter för Microsoft Intune

På den här sidan visas en lista över slutpunkter för myndigheter i USA som krävs för proxyinställningarna i dina Intune-distributioner.

Om du vill hantera enheter bakom brandväggar och proxyservrar, måste du aktivera kommunikation för Intune.

- Proxyservern måste ha stöd för både **HTTP (80)** och **HTTPS (443)** eftersom Intune-klienter använder båda protokollen
- För vissa åtgärder (t.ex. nedladdning av programuppdateringar) kräver Intune att det finns en oautentiserad åtkomst till proxyservern för att få åtkomst till manage.microsoft.com

Du kan ändra inställningarna för proxyservern på enskilda klientdatorer. Du kan också använda grupprincipinställningar till att ändra inställningarna för alla klientdatorer som finns bakom en angiven proxyserver.

Hanterade enheter kräver konfigurationer som låter **Alla användare** komma åt tjänster genom brandväggar.

I följande tabeller visas de portar och tjänster som Intune-klienten har åtkomst till:

|**Slutpunkt**|**IP-adress**|
|---------------------|-----------|
|*. manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>Slutpunkter som tilldelas amerikanska myndighetskunder:
- Azure-portalen: https:\//portal.azure.us/ 
- Office 365: https:\//portal.office365.us/ 
- Intune-företagsportalen: https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Partnertjänstslutpunkter som Intune är beroende av:
- AAD Sync Service: https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS: https:\//login.microsoftonline.us
- Directory Proxy: https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph: https:\//directory.microsoftazure.us and https:\//graph.microsoftazure.us
- MS Graph: https:\//graph.microsoft.us
- ADRS: https:\//enterpriseregistration.microsoftonline.us
