---
title: "Enheter som stöds – Microsoft Intune"
description: "Visar en lista över enhetsplattformar och webbläsare som stöds för Intunes enhetshantering"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 00fc685062c090b40e20ed3dfa30afbeeb5c9780
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="supported-devices-and-browsers"></a>Enheter och webbläsare som stöds

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Den här artikeln är avsedd för systemadministratörer som ansvarar för hanteringen av enheter i företaget. Hjälp om hur du installerar Intune på din telefon finns i [Använda hanterade enheter för att få arbetet gjort](/intune-user-help/company-portal-frequently-asked-questions).

Innan du börjar konfigurera Microsoft Intune, bör du granska följande krav:

- [Enheter och datorer som stöds](#intune-supported-devices)
- [En lista över vilka webbläsare som använder Intune](#intune-supported-web-browsers)

Du bör också känna till [Användning av nätverksbandbredd i Intune](network-bandwidth-use.md) ([klassisk portal](/intune-classic/get-started/network-bandwidth-use)).

## <a name="intune-supported-devices"></a>Enheter som har stöd för Intune

Du kan hantera följande enheter med mobil enhetshantering för Intune:

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

Intune kan inte användas för att hantera operativsystem med Windows Server.

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
- Firefox (senaste versionen)

### <a name="intune-classic-portal"></a>Intunes klassiska portal

Intunes klassiska funktioner, som t.ex. Intunes programvaruklient och integration med Mobile Threat Defense-partners, är tillgängliga i den klassiska Intune-portalen (https://manage.microsoft.com). Den klassiska Intune-portalen kräver stöd för Silverlight-webbläsaren.

Följande Silverlight-webbläsare har stöd för Intune-konsolen:
- Internet Explorer 10 eller senare
- Google Chrome (versioner före version 42)
- Mozilla Firefox med Silverlight aktiverat [Läs mer](https://go.microsoft.com/fwlink/?linkid=836872)

> [!Note]
> Den klassiska Intune-portalen stöder inte Microsoft Edge och mobila webbläsare eftersom de inte stöder [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx).

Endast användare med behörighet som tjänsteadministratör eller innehavaradministratören med den globala administratörsrollen kan logga in på den här portalen. Om du vill få åtkomst till administrationskonsolen måste kontot ha en licens för att använda Intune och inloggningsstatusen **Tillåten**.
