---
title: Konfigurera Microsoft Intunes WiFi-inställningar för enheter som kör iOS
titleSuffix: ''
description: Läs om Intunes WiFi-konfigurationsinställningar för enheter som kör iOS
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
ms.openlocfilehash: 4b723bd23681d98463adae83be5f74b556dc779e
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321160"
---
# <a name="wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>Wi-Fi-inställningar för iOS-enheter i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de WiFi-inställningar som du kan konfigurera i Microsoft Intune för enheter som kör iOS.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Wi-Fi-inställningar för bas- och företagsprofiler

- **Nätverksnamn** – Ange ett namn för den här Wi-Fi-anslutningen. Detta är det namn som användarna ser när de bläddrar i listan med tillgängliga anslutningar på sin enhet.
- **SSID** – Förkortning för nätverksnamn. Detta är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till. Användarna ser dock bara det nätverksnamn som du konfigurerade när de väljer anslutningen.
- **Anslut automatiskt** – Gör att enheten ansluter när den är inom intervallet för det här nätverket.
- **Dolt nätverk** – Förhindrar att det här nätverket visas i listan över tillgängliga nätverk på enheten.
- **I förväg delad nyckel** - 
- **Proxyinställningar** – Välj från:
    - **Ingen** – Inga proxyinställningar konfigureras.
    - **Manuell** – Ange **proxyserveradressen** (som en IP-adress) och dess tillhörande **portnummer**.
    - **Automatisk** – Använd en fil för att konfigurera proxyservern. Ange den **Proxyserver-URL** (till exempel **http://proxy.contoso.com**) som innehåller konfigurationsfilen.

## <a name="wi-fi-settings-for-basic-profiles-only"></a>Wi-Fi-inställningar endast för basprofiler

- **Säkerhetstyp** – Välj det säkerhetsprotokoll som ska användas för att autentisera med Wi-Fi-nätverket:
    - **Öppet (ingen autentisering)** – Använd bara det här alternativet om nätverket är oskyddat.
    - **WPA/WPA2 – Personal**
    - **WEP**

## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>Wi-Fi-inställningar endast för företagsprofiler

- **EAP-typ** – Välj den EAP-typ (Extensible Authentication Protocol) som ska användas för att autentisera skyddade trådlösa anslutningar:
    - **EAP-FAST**
    - **EAP-SIM**
    - **EAP-TLS**
    - **EAP-TTLS**
    - **LEAP**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Ange ytterligare alternativ när du väljer en EAP-typ


|Inställningsnamn|Mer information|Använd när|
|--------------|-------------|----------|
|**PAC-inställningar (Protected Access Credential)**|Välj det här alternativet om du vill etablera en autentiserad tunnel mellan klienten och autentiseringsservern. Välj en av:<br>- **Använd PAC** – Använd en befintlig PAC-fil om det finns en sådan.<br>- **Använd och etablera PAC** – Etablerar PAC-filen till dina enheter.<br>- **Använd och etablera PAC anonymt** – Etablera PAC-filen till dina enheter och säkerställ att PAC-filen etableras utan att servern autentiseras.|EAP-typen är **EAP-FAST**|

#### <a name="server-trust"></a>Serverförtroende


|Inställningsnamn|Mer information|Använd när|
|--------------|-------------|----------|
|**Certifikatservernamn**|Ange ett eller flera gemensamma namn som används i de certifikat som utfärdats av en betrodd certifikatutfärdare (CA). Om du anger den här informationen kan du hoppa över dialogrutan för dynamiskt förtroende som visas på användarnas enheter när de ansluter till WiFi-nätverket.|EAP-typen är **EAP-TLS**, **EAP-TTLS** eller **PEAP**.|
|**Rotcertifikat för serververifiering**|Välj den betrodda rotcertifikatsprofil som ska användas för att autentisera anslutningen. |EAP-typen är **EAP-TLS**, **EAP-TTLS** eller **PEAP**|
|**Identitetssekretess (yttre identitet)**|Ange vilken text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.|EAP-typen är **PEAP**|


#### <a name="client-authentication"></a>Klientautentisering


| Inställningsnamn | Mer information | Använd när |
|---|---|---|
| **Klientcertifikat för klientautentisering (identitetscertifikat)**** |  Välj den SCEP- eller PKCS-certifikatsprofil som ska användas för att autentisera anslutningen.  |    EAP-typen är **EAP-TLS**    |
| **Autentiseringsmetod** | Välj autentiseringsmetod för anslutningen:<br>- **Certifikat** för att markera det SCEP- eller PKCS- klientcertifikat som är identitetscertifikatet som presenterats för servern.<br><br>- **Användarnamn och lösenord** för att ange en annan metod för autentisering. <br><br>Om du har valt **Användarnamn och lösenord**, konfigurera:<br><br>-  **Annan metod än EAP (inre identitet)** och välj sedan hur du ska autentisera anslutningen:<br>- **Inga**<br>- **Okrypterat lösenord (PAP)**<br>- **CHAP (Challenge Handshake Authentication Protocol)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP Version 2 (MS-CHAP v2)**<br>Vilka alternativ som är tillgängliga beror på vilken EAP-typ du väljer.<br><br>**och**<br><br>- **Identitetssekretess (yttre identitet)** – Ange texten som skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel. | EAP-typen är **EAP-TTLS** eller * |

