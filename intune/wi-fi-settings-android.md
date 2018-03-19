---
title: "Konfigurera Microsoft Intunes WiFi-inställningar för Android-enheter"
titleSuffix: 
description: "Lär dig mer om Wi-Fi-konfigurationsinställningarna för enheter med Android och Android for Work."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d327c2d3cadf441f74e35af86b19438159225771
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="configure-wi-fi-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>Konfigurera Wi-Fi-inställningar i Microsoft Intune för enheter som kör Android och Android for Work  

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de WiFi-inställningar som du kan konfigurera i Microsoft Intune för enheter som kör Android och Android for Work.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Wi-Fi-inställningar för bas- och företagsprofiler

Följande Wi-Fi-inställningar är tillgängliga för enheter med Android och Android for Work:

- **Nätverksnamn** – Ange ett namn för den här Wi-Fi-anslutningen. Detta är det namn som användarna ser när de söker i listan över tillgängliga anslutningar på sina enheter.
- **SSID** – Förkortning för nätverksnamn. Detta är det verkliga namnet på det trådlösa nätverk som enheterna ska ansluta till. Användare ser dock bara det nätverksnamn som du konfigurerade när de väljer anslutningen.
- **Anslut automatiskt** – Gör att enheten ansluter när den är inom intervallet för det här nätverket.
- **Dolt nätverk** – Förhindrar att det här nätverket visas i listan över tillgängliga nätverk på enheten.


## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>Wi-Fi-inställningar endast för företagsprofiler

- **EAP-typ** – Välj den EAP-typ (Extensible Authentication Protocol) som ska användas för att autentisera skyddade trådlösa anslutningar:
    - **EAP-TLS**
    - **EAP-TTLS**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Ange ytterligare alternativ när du väljer en EAP-typ

#### <a name="server-trust"></a>Serverförtroende



|Inställningsnamn|Mer information|Använd när|
|-------------|---------------|-----------|
|**Certifikatservernamn**|Ange ett eller flera gemensamma namn som används i de certifikat som utfärdats av en betrodd certifikatutfärdare (CA). Om du anger den här informationen kan du hoppa över dialogrutan för dynamiskt förtroende som visas på användares enheter när de ansluter till det här Wi-Fi-nätverket.|EAP-typen är **EAP-TLS** eller **EAP-TTLS**|
|**Rotcertifikat för serververifiering**|Välj den betrodda rotcertifikatsprofil som ska användas för att autentisera anslutningen. |EAP-typen är **EAP-TLS**, **EAP-TTLS** eller **PEAP**|
|**Identitetssekretess (yttre identitet)**|Ange vilken text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.|EAP-typen är **PEAP**|


#### <a name="client-authentication"></a>Klientautentisering


|Inställningsnamn|Mer information|Använd när|
|----------|--------------|----------|
|**Klientcertifikat för klientautentisering (identitetscertifikat)**|Välj den SCEP- eller PKCS-certifikatsprofil som ska användas för att autentisera anslutningen.|EAP-typen är **EAP-TLS**|
|**Autentiseringsmetod**|Välj autentiseringsmetod för anslutningen:<br>- **Certifikat** för att markera det SCEP- eller PKCS- klientcertifikat som är identitetscertifikatet som presenterats för servern.<br><br>- **Användarnamn och lösenord** för att ange en annan metod för autentisering. <br><br>Om du har valt **Användarnamn och lösenord**, konfigurera:<br><br>-  **Annan metod än EAP (inre identitet)** och välj sedan hur du ska autentisera anslutningen:<br>- **Inga**<br>- **Okrypterat lösenord (PAP)**<br>- **CHAP (Challenge Handshake Authentication Protocol)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP Version 2 (MS-CHAP v2)**<br>Vilka alternativ som är tillgängliga beror på vilken EAP-typ du väljer.<br><br>**och**<br><br>- **Identitetssekretess (yttre identitet)** – Ange texten som skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.|EAP-typen är **EAP-TTLS** eller **PEAP**|
