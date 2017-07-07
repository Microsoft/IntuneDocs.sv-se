---
title: "Hitta ett paketfamiljenamn (PFN) för per app-VPN"
description: "Hitta ett PFN så att du kan konfigurera en per app-VPN."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76
ms.reviewer: tycast
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: eea3b9e2888f07399c8cda1e81ae8a5318d02d42
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn-configuration"></a>Hitta ett paketfamiljenamn (PFN) för per app-VPN-konfiguration

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det finns två sätt att hitta ett PFN så att du kan konfigurera en per app-VPN.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Hitta ett PFN för en app som är installerad på en Windows 10-dator

Om den app som du arbetar med redan är installerad på en Windows 10-dator kan du hämta PFN med hjälp av PowerShell-cmdleten [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx).

Syntaxen för Get-AppxPackage är:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
Du kan behöva köra PowerShell som administratör för att kunna hämta PFN.

Om du exempelvis vill få information om alla universella appar som är installerade på datorn använder du `Get-AppxPackage`.

Använd `Get-AppxPackage *<app_name>` om du vill få information om en app som du känner till hela eller en del av namnet på. Observera användning av jokertecken, vilket är särskilt användbart om du inte är säker på appens fullständiga namn. Använd till exempel `Get-AppxPackage *OneNote` om du vill hämta info för OneNote.


Här är den information som har hämtats för OneNote:

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>Hitta en PFN om appen inte har installerats på en dator

1.  Gå till https://www.microsoft.com/store/apps.
2.  Ange namnet på appen i sökfältet. I vårt exempel söker du efter OneNote.
3.  Välj länken till appen. Observera att URL:en har en serie bokstäver i slutet. I vårt exempel ser URL:en ut så här: `https://www.microsoft.com/store/apps/onenote/9wzdncrfhvjl`.
4.  Klistra in följande URL på en annan flik: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`. Ersätt `<app id>` med det app-ID som du har fått från https://www.microsoft.com/store/apps – serien med bokstäver i slutet av webbadressen i steg 3. I vårt exempel med OneNote skulle du klistra in: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

I Microsoft Edge visas den information som du vill ha. Välj **Öppna** i Internet Explorer om du vill se informationen. PFN-värdet anges på första raden. Här följer resultaten i vårt exempel:


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`
