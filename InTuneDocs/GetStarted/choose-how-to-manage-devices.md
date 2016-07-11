---
title: "Välj hur du vill hantera enheter | Microsoft Intune"
description: 
keywords: 
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: c9b34408e4af34dafc700d016304a6d29c2e8585


---

# Välj hur du vill hantera enheter
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] gör det möjligt att hantera ett antal enheter genom att *registrera* dem i tjänsten. Användarna kan sedan använda en *företagsportal* för att utföra ett antal åtgärder, till exempel registrera sin enhet, bläddra bland och installera appar, se till att enheten är kompatibel med företagets principer och kontakta IT-supporten.

## Metoder för att hantera mobila enheter
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] kan hantera följande enhetsplattformar:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Tips</h5>
  <p>Om du tidigare har registrerat enheter som kör en tidigare version av iOS än versionen som stöds ovan förblir dessa registrerade. Läs dock dokumentationen för varje [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] för att se till att den iOS-versionen stöds av funktionen.</p>
</div>

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] kan hantera användares enheter, vilket populärt kallas "bring your own device" (BYOD). Det kan också hantera företagsägda enheter, inklusive scenarion där företaget tillhandahåller en lista på enheter som användare kan välja mellan, kallas "choose your own device" (CYOD).

### Registrera enheter i hantering
Du måste alltid registrera enheter för mobila enhetsoperativsystem, inklusive iOS, Android och Windows Phone. Metoden för att registrera beror dock på organisationens behov:

|Typ av registrering|BYOD|CYOD|Delad enhet med hanteringskonto|Delade enheten utan användarkonto|
|-------------------|--------|--------|--------------------------------------|----------------------------------------|
|**Beskrivning**|Personlig enhet registrerad med Microsoft Intune|Företagsägd enhet för en användare|Företagsägd enhet som hanteras med hjälp av en hanteringskonto som delas av flera användare|Företagsägd användarlös enhet som används av flera användare.|
|**Enhetens användare**|Ägare|Tilldelad användare|Inget specifikt användarkonto|Ingen specifik användare|
|**Vem registrerar?**|Ägare|Administratör|Enhetshanteraren|Vem som helst|
|**Vem avregistrerar?**|Ägare eller administratör|Administratör|Administratör|Administratör|
|**Vem kan återställa?**|Ägare eller administratör|Administratör|Administratör|Administratör|

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Tips</h5>
  <p>Se [Funktioner för hantering av mobila enheter](mobile-device-management-capabilities-in-microsoft-intune.md) för en fullständig lista över de funktioner som du får vid registrering av enheter.</p>
</div>



## Metoder för att hantera Windows-datorer
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] kan hantera Windows Vista-datorer och senare Windows-datorer med hjälp av Intune-datorklienten. För Windows-datorer kan du dock välja mellan att registrera dem eller installera [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-klientprogramvaran som innehåller en del funktioner som inte är tillgängliga när du registrerar enheter. I de flesta fall registrerar du Windows-enheten med Intune, vilket ger en större uppsättning funktioner än datorklienten.

Överväg att använda Intune-datorklienten när du vill:
<ul>
<li>Använda någon av funktionerna i Microsoft Intune-klienten för att hantera Windows-datorer.</li>
<li>Hantera en Windows-dator som kör ett operativsystem som inte stöds för registrering.</li>
</ul>

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Tips</h5>
  <p>I [Windows-datorhanteringsfunktioner](windows-pc-management-capabilities-in-microsoft-intune.md) finns en fullständig lista över de funktioner som du får genom installation av Intune-datorklienten på Windows-datorer som stöds.</p>
</div>

## Exchange ActiveSync-hantering
Du kan också hantera enheter med Exchange ActiveSync. Det kräver att du installerar den lokala anslutningen eller använder den inbyggda tjänst-till-tjänst-anslutningen för att ansluta till Exchange Server.

Information om maskin- och programvarukraven för att installera den lokala anslutningen finns i [Krav för den lokala anslutningen](/intune/deploy-use/intune-on-premises-exchange-connector#requirements-for-the-on-premises-connect).

Information om hur du använder den lokala anslutningen eller tjänst-till-tjänst-anslutningen med Exchange finns i [Hantering av mobila enheter med Exchange ActiveSync och Microsoft Intune](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune).



## Nästa steg
Nu har du upptäckt några av de funktioner som du kan använda när du registrerar dina enheter med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Nu måste du [registrera dina enheter](/intune/deploy-use/enroll-devices-in-microsoft-intune). När du har registrerat enheterna kan du dra nytta av alla de funktioner som du har läst om i det här avsnittet. <!--lindavr: There's a logical flaw in our "get to know/get started" content. You can take the path in this topic or you can take the path in the What to know before your get started topic. And they don't cover the same ground. -->



<!--HONumber=Jun16_HO4-->


