---
title: Lägga till slutpunktsskydd i macOS i Microsoft Intune – Azure | Microsoft Docs
description: På macOS-enheter använder du gatekeepern för att avgöra var appar kan installeras, inklusive Mac App Store. Genom att aktivera eller konfigurera en brandvägg kan man också tillåta eller blockera specifika appar, använda Stealthläge och även blockera vissa typer av inkommande anslutningar med Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2c3a33b996a68263550fc05d3af853c263c930a
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565952"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Inställningar av slutpunktsskydd för macOS i Intune

I den här artikeln visas inställningarna för slutpunktsskydd som du kan konfigurera för enheter som kör macOS. Dessa inställningar inkluderar gatekeeper- och brandväggsinställningar på enheterna och kan konfigureras med en enhetsprofil i Microsoft Intune.

## <a name="gatekeeper"></a>Gatekeeper

- **Tillåt appar som hämtats från dessa platser**: Begränsa appar beroende på var de hämtas från. Avsikten är att skydda enheter mot skadlig kod och endast tillåta appar från källor som du litar på. Alternativen är: 
  - **Mac App Store**
  - **Mac App Store och identifierade utvecklare**
  - **Överallt**

- **Användaren kan åsidosätta gatekeeper**: Förhindrar användare från att åsidosätta denna inställning och från att installera en app med Ctrl+klick. När den är aktiverad kan användare installera appar med Ctrl+klick.

## <a name="firewall"></a>Brandvägg

Använd brandväggen för att styra anslutningar per program i stället för per port. Med programspecifika inställningar är det lättare att använda brandväggsskyddet. Du också förhindra att oönskade appar tar kontroll över nätverksportar som är öppna för legitima appar.

- **Använd brandväggen för att skydda enheter mot obehörig nätverksåtkomst genom att styra anslutningar per app.**
  - **Brandvägg**: Aktivera brandväggen för att konfigurera hur inkommande anslutningar ska hanteras i din miljö.
  - **Inkommande anslutningar**: Blockera alla inkommande anslutningar utom de anslutningar som krävs för grundläggande Internet-tjänster, till exempel DHCP, Bonjour och IPSec. Funktionen blockerar också alla delade tjänster, till exempel fildelning och skärmdelning. Om du använder delningstjänster behåller du inställningen som **Inte konfigurerad**.

- **Tillåta eller blockera inkommande anslutningar för specifika appar**
  - **Appar som tillåts**: Välj de appar som uttryckligen ska tillåtas ta emot inkommande anslutningar.
  - **Appar som blockeras**: Välj de appar som ska blockera inkommande anslutningar.
  - **Stealthläge**: Aktivera detta om du vill förhindra att datorn svarar på avsökningsbegäranden. Enheten fortsätter att besvara inkommande begäranden för godkända appar. Oväntade begäranden, till exempel ICMP (ping) ignoreras.
