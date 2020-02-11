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
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: dfa93bb758447c872d172ded7706fd7507a42f11
ms.sourcegitcommit: c7c6be3833d9a63d43f31d598b555b49b33cf5cb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2020
ms.locfileid: "76966291"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Slutpunkter för amerikanska myndigheter för Microsoft Intune

På den här sidan visas en lista över slutpunkter för myndigheter i USA som krävs för proxyinställningarna i dina Intune-distributioner.

Om du vill hantera enheter bakom brandväggar och proxyservrar, måste du aktivera kommunikation för Intune.

- Proxyservern måste ha stöd för både **HTTP (80)** och **HTTPS (443)** eftersom Intune-klienter använder båda protokollen
- För vissa åtgärder (t.ex. nedladdning av programuppdateringar) kräver Intune att det finns en oautentiserad åtkomst till proxyservern för att få åtkomst till manage.microsoft.com

Du kan ändra inställningarna för proxyservern på enskilda klientdatorer. Du kan också använda grupprincipinställningar till att ändra inställningarna för alla klientdatorer som finns bakom en angiven proxyserver.

Hanterade enheter kräver konfigurationer som låter **Alla användare** komma åt tjänster genom brandväggar.

För ytterligare information om automatisk registrering av Windows 10 och enhetsregistrering för amerikanska myndighetskunder, se [Konfigurera registrering för Windows-enheter](../enrollment/windows-enroll.md#windows-10-auto-enrollment-and-device-registration).

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

## <a name="windows-push-notification-services"></a>Windows Push Notification Services
På Intune-hanterade enheter som hanteras med MDM krävs Windows Push Notification Services (WNS) för enhetsåtgärder och andra omedelbara aktiviteter. Mer information finns i [Företagsbrandväggar och proxykonfigurationer som stödjer WNS-trafik](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)

## <a name="apple-device-network-information"></a>Nätverksinformation för Apple-enhet

|**Används för**|**Värdnamn (IP-adress/undernät)**|**Protokoll**|**Port**|
|------------|-----------|------------|-----------|
|Hämta och visa innehåll från Apple-servrar|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br>\*.phobos.itunes-apple.com.akadns.net|HTTP|80|
|Kommunikation med APNS-servrar|#-courier.push.apple.com<br>”#” är ett slumpmässigt tal från 0 till 50.|TCP|5223 och 443|
|Olika funktioner, bland annat åtkomst till Internet, iTunes-butiken, macOS App Store, iCloud, meddelanden etc.|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 eller 443|

Mer information finns i:

- [TCP- och UDP-portar som används av Apples programvaruprodukter](https://support.apple.com/HT202944)
- [Om macOS-, iOS-och iTunes-serverns värdanslutningar och bakgrundsprocesser i iTunes](https://support.apple.com/HT201999)
- [Om dina macOS- och iOS-klienter inte får push-meddelanden från Apple](https://support.apple.com/HT203609)

## <a name="next-steps"></a>Nästa steg
[Nätverksslutpunkter för Microsoft Intune](intune-endpoints.md)

