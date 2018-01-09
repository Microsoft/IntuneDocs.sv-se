---
title: "Wi-Fi-inställningar i Intune för Android-enheter"
titleSuffix: Azure portal
description: "Lär dig om hur du konfigurerar Wi-Fi-inställningarna för Intune på enheter med Android och Android for Work.”"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 103e17a4-2993-4359-b340-73e2acf4cf7d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36690343efc8c632a6b0e4326125ed85d93ed600
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/30/2017
---
# <a name="wi-fi-settings-for-android-and-android-for-work-devices-in-microsoft-intune"></a>Wi-Fi-inställningar för Android och Android for Work-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Wi-Fi-inställningar för bas- och företagsprofiler

Följande Wi-Fi-inställningar är tillgängliga för enheter med Android och Android for Work:

- **Nätverksnamn** – Ange ett namn för den här Wi-Fi-anslutningen. Detta är det namn som användarna ser när de söker i listan över tillgängliga anslutningar på sina enheter.
- **SSID** – Förkortning för nätverksnamn. Detta är det verkliga namnet på det trådlösa nätverk som enheterna ska ansluta till. Användare ser dock bara det nätverksnamn som du skapade ovan när de väljer anslutningen.
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
|**Certifikatservernamn**|Ange ett eller flera gemensamma namn som används i de certifikat som utfärdats av en betrodd certifikatutfärdare (CA). Om du anger den här informationen kan du hoppa över dialogrutan för dynamiskt förtroende som visas på slutanvändares enheter när de ansluter till det här Wi-Fi-nätverket.|EAP-typen är **EAP-TLS** eller **EAP-TTLS**|
|**Rotcertifikat för serververifiering**|Välj den betrodda rotcertifikatsprofil som ska användas för att autentisera anslutningen. |EAP-typen är **EAP-TLS**, **EAP-TTLS** eller **PEAP**|
|**Identitetssekretess (yttre identitet)**|Ange vilken text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.|EAP-typen är **PEAP**|


#### <a name="client-authentication"></a>Klientautentisering


|Inställningsnamn|Mer information|Använd när|
|----------|--------------|----------|
|**Klientcertifikat för klientautentisering (identitetscertifikat)**|Välj den SCEP- eller PKCS-certifikatsprofil som ska användas för att autentisera anslutningen.|EAP-typen är **EAP-TLS**|
|**Autentiseringsmetod**|Välj autentiseringsmetod för anslutningen:<br>- **Certifikat** för att markera det SCEP- eller PKCS- klientcertifikat som är identitetscertifikatet som presenterats för servern.<br><br>- **Användarnamn och lösenord** för att ange en annan metod för autentisering. <br><br>Om du har valt **Användarnamn och lösenord**, konfigurera:<br><br>-  **Annan metod än EAP (inre identitet)** och välj sedan hur du ska autentisera anslutningen:<br>- **Inga**<br>- **Okrypterat lösenord (PAP)**<br>- **CHAP (Challenge Handshake Authentication Protocol)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP Version 2 (MS-CHAP v2)**<br>Vilka alternativ som är tillgängliga beror på vilken EAP-typ du väljer.<br><br>**och**<br><br>- **Identitetssekretess (yttre identitet)** – Ange texten som skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.|EAP-typen är **EAP-TTLS** eller **PEAP**|
