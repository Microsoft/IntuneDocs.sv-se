---
# required metadata

title: Hitta ett paketfamiljenamn (PFN) för per app-VPN | Microsoft Intune|
description:
keywords:
author: nbigman
manager: [ALIAS]
ms.date: 05/10/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: tycast
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Hitta ett produktfamiljenamn (PFN) för per app-VPN-konfiguration

Det finns två sätt att hitta ett PFN så att du kan konfigurera en per app-VPN.

## Hitta ett PFN för en app som är installerad på en Windows 10-dator 

Om den app som du arbetar med redan är installerad på en Windows 10-dator kan du hämta PFN med hjälp av PowerShell-cmdleten [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx).

Syntaxen för Get-AppxPackage är:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> Obs! Du kan behöva köra PowerShell som administratör om du vill kunna hämta PFN

Om du exempelvis vill få information om alla universella appar som är installerade på datorn använder du `Get-AppxPackage`.

Använd `Get-AppxPackage *<app_name>` om du vill få information om en app som du känner till namnet eller en del av namnet på. Observera användning av jokertecken, vilket är särskilt användbart om du inte är säker på appens fullständiga namn. Använd till exempel `Get-AppxPackage *OneNote` om du vill hämta info för OneNote.


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



## Hitta en PFN om appen inte har installerats på en dator

1.  Gå till https://www.microsoft.com/en-us/store/apps
2.  Ange namnet på appen i sökfältet. I vårt exempel söker du efter OneNote.
3.  Klicka på länken till appen. Observera att den URL som du har åtkomst till har en serie bokstäver i slutet. I vårt exempel ser URL-adressen ser ut så här:
`https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.  Klistra in följande URL i en annan flik `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`, och ersätt `<app id>` med det app-id som du har fått från https://www.microsoft.com/en-us/store/apps – serien med bokstäver i slutet av URL:en i steg 3. I vårt exempel med OneNote skulle du klistra in: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

Den information du vill visa visas i Edge; i Internet Explorer klickar du på **Öppna** om du vill se informationen. PFN-värdet anges på första raden. Så här ser resultatet ut i vårt exempel:
 

`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`



<!--HONumber=Jun16_HO1-->


