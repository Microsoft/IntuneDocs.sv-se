---
title: Felsöka Exchange Connector
titleSuffix: Microsoft Intune
description: Felsöka problem med lokal Intune Exchange-anslutning.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 962e66a9fdf6d8abcf6855f645775026ee4db850
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508835"
---
# <a name="troubleshoot-the-intune-exchange-connector"></a>Felsöka Intune Exchange Connector

I den här artikeln beskrivs hur du felsöker problem med Intune Exchange Connector.

## <a name="before-you-start"></a>Innan du börjar

Innan du börjar felsöka ett Exchange Connector-problem i Intune samlar du in lite grundläggande information så att du arbetar med en solid grund. Den här metoden kan hjälpa dig att bättre förstå problemets beskaffenhet och lösa det snabbare.

- Kontrol lera att processen uppfyller installations kraven. Mer information finns i [Konfigurera lokala Intune Exchange Connector](exchange-connector-install.md).
- Kontrol lera att ditt konto har både Exchange-och Intune-administratörs behörighet.
- Observera den fullständiga och exakta fel meddelande texten, information och var meddelandet visas.
- Ta reda på när problemet har startats: 
  - Konfigurerar du anslutningen för första gången? 
  - Fungerade kopplingen korrekt och kunde sedan inte köras?
  - Om det fungerade, vilka ändringar som gjorts i Intune-miljön, Exchange-miljön eller på datorn som kör anslutnings programmet?
- Vad är MDM-utfärdare? Om det är System Center Configuration Manager, vilken version av Configuration Manager använder du?
- Vilken version av Exchange använder du?

### <a name="use-powershell-to-get-more-data-on-exchange-connector-issues"></a>Använda PowerShell för att få mer information om problem med Exchange Connector

- Om du vill hämta en lista över alla mobila enheter för en post låda använder du `Get-ActiveSyncDeviceStatistics -mailbox mbx`
- Om du vill hämta en lista över SMTP-adresser för en post låda använder du `Get-Mailbox -Identity user | select emailaddresses | fl`
- Om du vill hämta detaljerad information om en enhets åtkomststatus använder du `Get-CASMailbox <upn> | fl`

## <a name="review-the-connector-configuration"></a>Granska anslutnings konfigurationen

Granska kraven för den [lokala Exchange Connector](exchange-connector-install.md#intune-exchange-connector-requirements) för att kontrol lera att din miljö och anslutningen är korrekt konfigurerade. 

### <a name="general-considerations-for-the-connector"></a>Allmänna överväganden för anslutningen

- Kontrol lera att brand väggen och proxyservrar tillåter kommunikation mellan den server som är värd för Intune Exchange Connector och Intune-tjänsten.

- Datorn som är värd för Intune Exchange-anslutaren och Exchange-klientens åtkomst Server (CAS) måste vara domänansluten och på samma LAN. Kontrol lera att de nödvändiga behörigheterna har lagts till för kontot som används av Intune Exchange Connector.

- Aviserings kontot används för att hämta inställningar för *Automatisk identifiering* . Mer information om Autodisover i Exchange finns i [identifiera tjänsten för automatisk identifiering i Exchange Server](https://docs.microsoft.com/exchange/architecture/client-access/autodiscover?view=exchserver-2016).

- Intune Exchange Connector skickar en begäran till EWS-URL: en med hjälp av autentiseringsuppgifterna för aviserings kontot för att skicka meddelanden via e-post tillsammans med länken *Kom igång* (för att registrera i Intune). Användning av länken *Kom igång* för att registrera är ett krav för Android-enheter som inte är Knox. Annars kommer dessa enheter att blockeras av villkorlig åtkomst.

### <a name="common-issues-for-connector-configurations"></a>Vanliga problem för anslutnings konfiguration

- **Kontobehörigheter**: I dialogrutan för Microsoft Intune Exchange Connector ser du till att du har angett ett användarkonto som har nödvändiga behörigheter för att köra [Windows PowerShell Exchange-cmdletar](exchange-connector-install.md#exchange-cmdlet-requirements).
- **E-postmeddelanden för aviseringar**: Aktivera meddelanden och ange ett meddelande konto.
- **Synkronisering av klient åtkomst Server**: när du konfigurerar Exchange Connector ska du ange en certifikat utfärdare som har den lägsta nätverks fördröjning som är möjlig för servern som är värd för Exchange Connector. Svarstiden för kommunikationen mellan klientåtkomstservern och Exchange-anslutningen kan orsaka fördröjningar i enhetsidentifieringen, särskilt om Dedikerad Exchange Online används.
- **Synkroniseringsschema**: Åtkomst för en användare med en nyligen registrerad enhet kan fördröjas tills Exchange-anslutningen synkroniserar med Exchange-CAS. En fullständig synkronisering görs en gång per dag, och en deltasynkronisering (snabbsynkronisering) görs flera gånger per dag. Du kan [manuellt framtvinga en snabbsynkronisering eller en fullständig synkronisering](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync) för att minimera fördröjningar.

## <a name="next-steps"></a>Nästa steg
Följande artiklar kan hjälpa till att lösa vanliga problem och fel:

- [Lös vanliga problem för Intune Exchange Connector](troubleshoot-exchange-connector-common-problems.md).
- [Lös vanliga fel för Intune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

Kontakta hjälp från support eller Intune-communityn:

- Se [få support](../fundamentals/get-support.md) för att felsöka problemet med hjälp av Intune-konsolen eller att öppna ett support ärende med Microsoft. 
- Publicera ditt problem i [Microsoft Intune forum](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
