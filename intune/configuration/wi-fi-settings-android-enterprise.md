---
title: Wi-Fi-inställningar för Android Enterprise-enheter och enheter med helskärmsläge – Microsoft Intune | Microsoft Docs
description: Skapa eller lägg till en konfigurationsprofil för Wi-Fi-enheter för Android Enterprise och Android Kiosk. Se de olika inställningarna, inklusive att lägga till certifikat, välja en EAP-typ och välja en autentiseringsmetod i Microsoft Intune. För Kiosk-enheter anger du också den i förväg delade nyckeln för ditt nätverk.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: maholdaa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: aef1747fdbb3118db82f6e99c2838632c8a9d369
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512457"
---
# <a name="add-wi-fi-settings-for-android-enterprise-dedicated-and-fully-managed-devices-in-microsoft-intune"></a>Lägg till Wi-Fi-inställningar för dedikerade och fullständigt hanterade Android Enterprise-enheter i Microsoft Intune

Du kan skapa en profil med specifika Wi-Fi-inställningar och sedan distribuera profilen till dina dedikerade och fullständigt hanterade Android Enterprise-enheter. Microsoft Intune innehåller många funktioner, inklusive autentisering till ditt nätverk med en i förväg delad nyckel och mycket mer.

Den här artikeln beskriver dessa inställningar. I [Använda Wi-Fi på dina enheter](wi-fi-settings-configure.md) finns mer information om Wi-Fi-funktionen i Microsoft Intune.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetsprofil](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only"></a>Endast enhetens ägare

Välj det här alternativet om du distribuerar till en dedikerad eller fullständigt hanterad Android Enterprise-enhet.  Dedikerade och fullständigt hanterade Android Enterprise-enheter stöder för närvarande SCEP-certifikatdistribution men inte PKCS.

### <a name="basic"></a>Basic

- **Wi-Fi-typ**: Välj **Basic**.
- **Nätverksnamn**: Ange ett namn på Wi-Fi-anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten efter tillgängliga Wi-FI-anslutningar. Ange till exempel **Contoso WiFi**.
- **SSID**: Ange **nätverksnamn**, som är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till. Användarna ser dock bara det **nätverksnamn** som du konfigurerade när de väljer anslutningen.
- **Dolt nätverk**: Välj **Aktivera** för att dölja nätverket i listan med tillgängliga nätverk på enheten. SSID skickas inte. Välj **Inaktivera** för att visa nätverket i listan med tillgängliga nätverk på enheten.
- **Wi-Fi-typ**: Välj det säkerhetsprotokoll som ska autentiseras med Wi-Fi-nätverket. Alternativen är:

  - **Öppet (ingen autentisering)** : Använd bara det här alternativet om nätverket är oskyddat.
  - **I förväg delad WEP-nyckel**: Ange lösenordet i **I förväg delad nyckel**. När nätverket är konfigurerat, konfigureras också ett lösenord eller en nätverksnyckel. Ange lösenordet eller nätverksnyckeln för PSK-värdet.
  - **I förväg delad WPA-nyckel**: Ange lösenordet i **I förväg delad nyckel**. När nätverket är konfigurerat, konfigureras också ett lösenord eller en nätverksnyckel. Ange lösenordet eller nätverksnyckeln för PSK-värdet.

### <a name="enterprise"></a>Enterprise

- **Wi-Fi-typ**: Välj **Företag**.
- **SSID**: Ange **nätverksnamn**, som är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till. Användarna ser dock bara det **nätverksnamn** som du konfigurerade när de väljer anslutningen.
- **Dolt nätverk**: Välj **Aktivera** för att dölja nätverket i listan med tillgängliga nätverk på enheten. SSID skickas inte. Välj **Inaktivera** för att visa nätverket i listan med tillgängliga nätverk på enheten.
- **EAP-typ**: Välj den EAP-typ (Extensible Authentication Protocol) som används för att autentisera säkra trådlösa anslutningar. Alternativen är:

  - **EAP-TLS**: Ange även:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatsprofil. När klienten ansluter till nätverket presenteras certifikatet för servern och används för att autentisera anslutningen.

    - **Klientautentisering** - **Klientcertifikat för klientautentisering (identitetscertifikat)** : Välj den SCEP-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

    - **Identitetssekretess (yttre identitet)** : Ange den text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

  - **EAP-TTLS**: Ange även:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatsprofil. När klienten ansluter till nätverket presenteras certifikatet för servern och används för att autentisera anslutningen.

    - **Klientautentisering**: Välj en **Autentiseringsmetod**. Alternativen är:

      - **Användarnamn och lösenord**: Be användaren ange ett användarnamn och ett lösenord för att autentisera anslutningen. Ange även:
        - **Annan metod än EAP (inre identitet)** : Välj hur du ska autentisera anslutningen. Du måste välja samma protokoll som är konfigurerat på ditt Wi-Fi-nätverk. Alternativen är:

          - **Okrypterat lösenord (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certifikat**: Välj den SCEP-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

      - **Identitetssekretess (yttre identitet)** : Ange den text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

  - **PEAP**: Ange även:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatsprofil. När klienten ansluter till nätverket presenteras certifikatet för servern och används för att autentisera anslutningen.

    - **Klientautentisering**: Välj en **Autentiseringsmetod**. Alternativen är:

      - **Användarnamn och lösenord**: Be användaren ange ett användarnamn och ett lösenord för att autentisera anslutningen. Ange även:
        - **Annan metod än EAP för autentisering (inre identitet)** : Välj hur du ska autentisera anslutningen. Du måste välja samma protokoll som är konfigurerat på ditt Wi-Fi-nätverk. Alternativen är:

          - **Inga**
          - **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certifikat**: Välj den SCEP-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

      - **Identitetssekretess (yttre identitet)** : Ange den text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

## <a name="work-profile-only"></a>Endast arbetsprofil

### <a name="basic"></a>Basic

- **Wi-Fi-typ**: Välj **Basic**.
- **SSID**: Ange **nätverksnamn**, som är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till. Användarna ser dock bara det **nätverksnamn** som du konfigurerade när de väljer anslutningen.
- **Dolt nätverk**: Välj **Aktivera** för att dölja nätverket i listan med tillgängliga nätverk på enheten. SSID skickas inte. Välj **Inaktivera** för att visa nätverket i listan med tillgängliga nätverk på enheten.

### <a name="enterprise"></a>Enterprise

- **Wi-Fi-typ**: Välj **Företag**.
- **SSID**: Ange **nätverksnamn**, som är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till. Användarna ser dock bara det **nätverksnamn** som du konfigurerade när de väljer anslutningen.
- **Dolt nätverk**: Välj **Aktivera** för att dölja nätverket i listan med tillgängliga nätverk på enheten. SSID skickas inte. Välj **Inaktivera** för att visa nätverket i listan med tillgängliga nätverk på enheten.
- **EAP-typ**: Välj den EAP-typ (Extensible Authentication Protocol) som används för att autentisera säkra trådlösa anslutningar. Alternativen är:

  - **EAP-TLS**: Ange även:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatsprofil. När klienten ansluter till nätverket presenteras certifikatet för servern och används för att autentisera anslutningen.

    - **Klientautentisering** - **Klientcertifikat för klientautentisering (identitetscertifikat)** : Välj den SCEP- eller PKCS-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

    - **Identitetssekretess (yttre identitet)** : Ange den text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

  - **EAP-TTLS**: Ange även:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatsprofil. När klienten ansluter till nätverket presenteras certifikatet för servern och används för att autentisera anslutningen.

    - **Klientautentisering**: Välj en **Autentiseringsmetod**. Alternativen är:

      - **Användarnamn och lösenord**: Be användaren ange ett användarnamn och ett lösenord för att autentisera anslutningen. Ange även:
        - **Annan metod än EAP (inre identitet)** : Välj hur du ska autentisera anslutningen. Du måste välja samma protokoll som är konfigurerat på ditt Wi-Fi-nätverk. Alternativen är:

          - **Okrypterat lösenord (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certifikat**: Välj den SCEP- eller PKCS-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

      - **Identitetssekretess (yttre identitet)** : Ange den text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

  - **PEAP**: Ange även:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatsprofil. När klienten ansluter till nätverket presenteras certifikatet för servern och används för att autentisera anslutningen.

    - **Klientautentisering**: Välj en **Autentiseringsmetod**. Alternativen är:

      - **Användarnamn och lösenord**: Be användaren ange ett användarnamn och ett lösenord för att autentisera anslutningen. Ange även:
        - **Annan metod än EAP för autentisering (inre identitet)** : Välj hur du ska autentisera anslutningen. Du måste välja samma protokoll som är konfigurerat på ditt Wi-Fi-nätverk. Alternativen är:

          - **Inga**
          - **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certifikat**: Välj den SCEP- eller PKCS-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

      - **Identitetssekretess (yttre identitet)** : Ange den text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. Därefter [tilldelar du profilen](device-profile-assign.md) och [övervakar dess status.](device-profile-monitor.md)

Du kan också skapa Wi-Fi-profiler för [Android](wi-fi-settings-android.md)-, [iOS-/iPadOS](wi-fi-settings-ios.md)-, [macOS](wi-fi-settings-macos.md)-, [Windows 10](wi-fi-settings-windows.md)- och [Windows 8.1](wi-fi-settings-import-windows-8-1.md)-enheter.
