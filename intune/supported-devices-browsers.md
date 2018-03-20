---
title: "Operativsystem och webbläsare som stöds av Microsoft Intune"
titleSuffix: 
description: "Visar en lista över enhetsplattformar och webbläsare som stöds för Intunes enhetshantering"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/03/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1e58201620612118f0984a1c477b3fa3bc7e923a
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="supported-operating-systems-and-browsers"></a>Operativsystem och webbläsare som stöds

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Granska de operativsystem och webbläsare som stöds innan du installerar Microsoft Intune.

Hjälp om hur du installerar Intune på din enhet finns i [Använda hanterade enheter för att få arbetet gjort](/intune-user-help/company-portal-frequently-asked-questions). Du bör också känna till [Användning av nätverksbandbredd i Intune](network-bandwidth-use.md) ([klassisk portal](/intune-classic/get-started/network-bandwidth-use)).

## <a name="intune-supported-operating-systems"></a>Operativsystem som stöds i Intune

Du kan hantera enheter som kör följande operativsystem:

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>Samsung Knox Standard-enheter som stöds

Företagsportalappen försöker endast aktivera Samsung Knox under MDM-registrering om enheten visas i [listan över Knox-enheter som stöds](https://www.samsungknox.com/knox-supported-devices/knox-workspace). På så sätt kan man undvika Knox-aktiveringsfel som förhindrar MDM-registrering. Enheter som inte har stöd för Samsung Knox-aktivering registreras som Android-standardenheter. En Samsung-enhet kan ha vissa modellnummer som har stöd för Knox medan andra inte stöds. Kontrollera att Knox är kompatibelt med enhetsåterförsäljaren innan du köper och distribuerar Samsung-enheter.

> [!NOTE]
> Registrering av Samsung Knox-enheter kan kräva att du [ger åtkomst till Samsung-servrar](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers). 

Följande lista över Samsung-enhetsmodeller har inte stöd för Knox och registreras som ursprungliga Android-enheter av företagsportalappen för Android:

| **Enhetsnamn** | **Enhetsmodellnummer** |
| --- | --- |
| Galaxy Avant | SM-G386T |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0&quot; | SM-T280<br>SM-T285 |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116<br>SM-T210<br>SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |


### <a name="windows-pc-software-client"></a>Windows PC-programvaruklient

En [Intune-programvaruklient](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) kan distribueras och installeras på Windows-datorer som en alternativ metod för registrering. Den här funktionen är bara tillgänglig i den klassiska Intune-portalen. Du kan använda Intune-programvaruklienten för att hantera datorer med Windows 7 och senare, förutom Windows 10 Home Edition.

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Webbläsare som stöds av Intune

Olika administrativa uppgifter som kräver att du använder en av följande administrativa webbplatser.

- [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Azure Portal](https://portal.azure.com/)

Följande webbläsare stöds för dessa portaler:
- Microsoft Edge (senaste versionen)
- Microsoft Internet Explorer 11
- Safari (senaste versionen, endast Mac)
- Chrome (senaste versionen)
- Mozilla Firefox med Silverlight aktiverat [Läs mer (tidigare versioner än version 52)](https://go.microsoft.com/fwlink/?linkid=836872)




### <a name="intune-classic-portal"></a>Intunes klassiska portal

Intunes klassiska funktioner, som t.ex. Intunes programvaruklient och integration med Mobile Threat Defense-partners, är tillgängliga i den klassiska Intune-portalen (https://manage.microsoft.com). Den klassiska Intune-portalen kräver stöd för Silverlight-webbläsaren.

Följande Silverlight-webbläsare har stöd för Intune-konsolen:
- Internet Explorer 10 eller senare
- Google Chrome (versioner före version 42)
- Mozilla Firefox med Silverlight aktiverat [Läs mer](https://go.microsoft.com/fwlink/?linkid=836872)

> [!Note]
> Den klassiska Intune-portalen stöder inte Microsoft Edge och mobila webbläsare eftersom de inte stöder [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx).

Endast användare med behörighet som tjänsteadministratör eller innehavaradministratören med den globala administratörsrollen kan logga in på den här portalen. Om du vill få åtkomst till administrationskonsolen måste kontot ha en licens för att använda Intune och inloggningsstatusen **Tillåten**.
