---
title: "Mobila enheter och webbläsare som stöds | Microsoft Intune"
description: "Visar enheter och webbläsare med stöd för att köra Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/01/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aeeccfa4-0f14-447e-a3df-c8435c8a4bb2
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: b0eab195c00aae4b593fff535179a1b993c36dde


---

# <a name="supported-devices-and-web-browsers-for-intune"></a>Enheter och webbläsare med stöd för Intune

Som Intune-administratör kan du hantera många olika enheter från en webbläsare. Det här avsnittet innehåller:

- [Listor över enhetsplattformar som stöds](#intune-supported-devices)
- [En lista över vilka webbläsare som använder Intune](#intune-supported-web-browsers)

## <a name="intune-supported-devices"></a>Enheter som har stöd för Intune

Du kan hantera följande enheter med mobil enhetshantering för Intune:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

Intune kan inte användas för att hantera operativsystem med Windows Server.

Intunes hantering av enheter ger [dessa funktioner](mobile-device-management-capabilities-in-microsoft-intune.md).

### <a name="windows-pc-software-client"></a>Windows PC-programvaruklient

En [Intune-programvaruklient](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune) kan distribueras och installeras på Windows-datorer som en alternativ metod för registrering. Du kan använda Intune-programvaruklient för att hantera Windows 7 och senare datorer, förutom Windows 10 Home Edition. Genom att hantera datorer med klientprogramvaran får du tillgång till [dessa funktioner](windows-pc-management-capabilities-in-microsoft-intune.md).

### <a name="exchange-activesync-management"></a>Exchange ActiveSync-hantering

Du kan hantera [Exchange ActiveSync-enheter](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) från Intune-konsolen. Det här alternativet innehåller en begränsad uppsättning funktioner för hantering jämfört med andra metoder. Se [Funktionerna för inbyggd hantering av mobilenheter i Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) för en lista över enheter som stöds.

## <a name="intune-supported-web-browsers"></a>Webbläsare som stöds av Intune

Olika administrativa uppgifter som kräver att du använder en av följande administrativa webbplatser.

- [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune-administratörskonsolen](https://admin.manage.microsoft.com/)

|Intune-funktion |Webbläsare som stöds|
|---------|---------|
|**Administrationskonsolen för Intune**     |  Internet Explorer 10 eller senare<br /><br />Google Chrome (versioner före version 42)<br /><br />Mozilla Firefox med Silverlight aktiverat<br />**OBS!** Mozillas stöd för Silverlight tas bort fr.o.m. mars 2017. [Läs mer](https://go.microsoft.com/fwlink/?linkid=836872). |
|**Administrationsportalen för Office 365**     |Alla webbläsare, inklusive mobila webbläsare och hanterade webbläsare  |
|**Företagsportalens webbplats**     |**På mobila enheter:** använd standardwebbläsaren för varje plattform som stöds   <br /><br />**På Windows-datorer:** Internet Explorer 10 eller senare eller Microsoft Edge<br /><br />**På Mac OS X 10.9 eller senare:** Apple Safari    |

> [!Note]
> Administrationskonsolen stöder inte Microsoft Edge och mobila webbläsare eftersom de inte stöder [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). Intune-konsolen håller på att migreras från Silverlight-miljön. När det är klart kommer alla Intunes funktioner för hantering av mobila enheter och program att [göras tillgängliga på den nya Microsoft Azure-portalen](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).


Endast användare med behörighet som tjänsteadministratör eller innehavaradministratören med den globala administratörsrollen kan logga in på den här portalen. Om du vill få åtkomst till administrationskonsolen måste kontot ha en licens för att använda Intune och inloggningsstatusen **Tillåten**.
>[!div class="step-by-step"]

>[&larr; **Förutsättningar**](what-to-know-before-you-start-microsoft-intune.md)     [**Nätverk** &rarr;](network-bandwidth-use.md)  



<!--HONumber=Dec16_HO2-->


