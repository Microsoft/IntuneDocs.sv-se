---
title: Konfigurera Microsoft Intunes WiFi-inställningar för Android-enheter
titleSuffix: ''
description: Lär dig mer om Wi-Fi-konfigurationsinställningarna för enheter med Android och Android for Work.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ee82da997a794bb2f65929a6fd9e0de0cc776a6e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831069"
---
# <a name="configure-wi-fi-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>Konfigurera Wi-Fi-inställningar i Microsoft Intune för enheter som kör Android och Android for Work  

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de WiFi-inställningar som du kan konfigurera i Microsoft Intune för enheter som kör Android och Android for Work.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Wi-Fi-inställningar för bas- och företagsprofiler

Följande Wi-Fi-inställningar är tillgängliga för enheter med Android och Android for Work:

- **Nätverksnamn** – Ange ett namn för den här Wi-Fi-anslutningen. Detta är det namn som användarna ser när de bläddrar i listan med tillgängliga anslutningar på sin enhet.
- **SSID** – Förkortning för nätverksnamn. Detta är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till. Användarna ser dock bara det nätverksnamn som du konfigurerade när de väljer anslutningen.
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
|**Certifikatservernamn**|Ange ett eller flera gemensamma namn som används i de certifikat som utfärdats av en betrodd certifikatutfärdare (CA). Om du anger den här informationen kan du hoppa över dialogrutan för dynamiskt förtroende som visas på användarnas enheter när de ansluter till WiFi-nätverket.|EAP-typen är **EAP-TLS** eller **EAP-TTLS**|
|**Rotcertifikat för serververifiering**|Välj den betrodda rotcertifikatsprofil som ska användas för att autentisera anslutningen. |EAP-typen är **EAP-TLS**, **EAP-TTLS** eller **PEAP**|
|**Identitetssekretess (yttre identitet)**|Ange vilken text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.|EAP-typen är **PEAP**|


#### <a name="client-authentication"></a>Klientautentisering


|                                     Inställningsnamn                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Mer information                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                            Använd när                            |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| <strong>Klientcertifikat för klientautentisering (identitetscertifikat)</strong> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Välj den SCEP- eller PKCS-certifikatsprofil som ska användas för att autentisera anslutningen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |              EAP-typen är <strong>EAP-TLS</strong>              |
|                        <strong>Autentiseringsmetod</strong>                        | Välj autentiseringsmetod för anslutningen:<br>- <strong>Certifikat</strong> för att markera det SCEP- eller PKCS- klientcertifikat som är identitetscertifikatet som presenterats för servern.<br><br>- <strong>Användarnamn och lösenord</strong> för att ange en annan metod för autentisering. <br><br>Om du har valt <strong>Användarnamn och lösenord</strong>, konfigurera:<br><br>-  <strong>Annan metod än EAP (inre identitet)</strong> och välj sedan hur du ska autentisera anslutningen:<br>- <strong>Inga</strong><br>- <strong>Okrypterat lösenord (PAP)</strong><br>- <strong>CHAP (Challenge Handshake Authentication Protocol)</strong><br>- <strong>Microsoft CHAP (MS-CHAP)</strong><br>- <strong>Microsoft CHAP Version 2 (MS-CHAP v2)</strong><br>Vilka alternativ som är tillgängliga beror på vilken EAP-typ du väljer.<br><br><strong>och</strong><br><br>- <strong>Identitetssekretess (yttre identitet)</strong> – Ange texten som skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel. | EAP-typen är <strong>EAP-TTLS</strong> eller <strong>PEAP</strong> |

