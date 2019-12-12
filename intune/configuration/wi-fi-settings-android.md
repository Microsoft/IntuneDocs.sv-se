---
title: Konfigurera Wi-Fi-inställningar för Android-enheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Skapa eller lägga till en Wi-Fi-enhetskonfigurationsprofil för Android. Se de olika inställningarna, inklusive att lägga till certifikat, välja en EAP-typ och välja en autentiseringsmetod i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: maholdaa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a9bd1691b7943f02c9577e962fb1bcd5d9cf40a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72585336"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Lägga till Wi-Fi-inställningar för enheter som kör Android i Microsoft Intune

Du kan skapa en profil med specifika Wi-Fi-inställningar och sedan distribuera profilen till dina Android-enheter. Microsoft Intune innehåller många funktioner, inklusive autentisering till ditt nätverk, lägga till ett PKS- eller ett SCEP-certifikat och mycket mer.

Dessa Wi-Fi-inställningar är uppdelade i två kategorier: Grundläggande inställningar och inställningar på företagsnivå.

Den här artikeln beskriver dessa inställningar.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetsprofil](device-profile-create.md).

## <a name="basic"></a>Grundläggande

- **Wi-Fi-typ**: Välj **Grundläggande**.
- **SSID**: ange **tjänst uppsättnings identifieraren**, som är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till. Användarna ser dock bara det **nätverksnamn** som du konfigurerade när de väljer anslutningen.
- **Dolt nätverk**: Välj **Aktivera** för att dölja nätverket i listan med tillgängliga nätverk på enheten. SSID skickas inte. Välj **Inaktivera** för att visa nätverket i listan med tillgängliga nätverk på enheten.

## <a name="enterprise"></a>Företag

- **Wi-Fi-typ**: Välj **Företag**.
- **SSID**: ange **tjänst uppsättnings identifieraren**, som är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till. Användarna ser dock bara det **nätverksnamn** som du konfigurerade när de väljer anslutningen.
- **Dolt nätverk**: Välj **Aktivera** för att dölja nätverket i listan med tillgängliga nätverk på enheten. SSID skickas inte. Välj **Inaktivera** för att visa nätverket i listan med tillgängliga nätverk på enheten.
- **EAP-typ**: Välj den EAP-typ (Extensible Authentication Protocol) som används för att autentisera skyddade trådlösa anslutningar. Alternativen är: 

  - **EAP-TLS**: Ange också:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatprofil. Det här certifikatet presenteras för servern när klienten ansluter till nätverket. Den autentiserar anslutningen.

    - **Klientautentisering** - **Klientcertifikat för klientautentisering (identitetscertifikat)** : Välj den SCEP- eller PKCS-profil för klientcertifikatet som också distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

    - **Identitetsskydd (yttre identitet)** : Ange den text som skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

  - **EAP-TTLS**: Ange också:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatprofil. Det här certifikatet presenteras för servern när klienten ansluter till nätverket. Den autentiserar anslutningen.

    - **Klientautentisering**: Välj en **Autentiseringsmetod**. Alternativen är:

      - **Användarnamn och lösenord**: Be användaren ange ett användarnamn och ett lösenord för att autentisera anslutningen. Ange även:
        - **Annan metod än EAP (inre identitet)** : Välj hur anslutningen ska autentiseras. Du måste välja samma protokoll som är konfigurerat på ditt Wi-Fi-nätverk. Alternativen är:

          - **Okrypterat lösenord (PAP)**
          - **CHAP (Challenge Handshake Authentication Protocol)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certifikat**: Välj den SCEP- eller PKCS-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

      - **Identitetsskydd (yttre identitet)** : Ange den text som skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

  - **PEAP**: Ange också:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatprofil. Det här certifikatet presenteras för servern när klienten ansluter till nätverket. Den autentiserar anslutningen.

    - **Klientautentisering**: Välj en **Autentiseringsmetod**. Alternativen är:

      - **Användarnamn och lösenord**: Be användaren ange ett användarnamn och ett lösenord för att autentisera anslutningen. Ange även:
        - **Annan metod än EAP för autentisering (inre identitet)** : Välj hur anslutningen ska autentiseras. Du måste välja samma protokoll som är konfigurerat på ditt Wi-Fi-nätverk. Alternativen är:

          - **Inga**
          - **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certifikat**: Välj den SCEP- eller PKCS-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

      - **Identitetsskydd (yttre identitet)** : Ange den text som skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. Nu ska vi [tilldela den här profilen](device-profile-assign.md).

## <a name="more-resources"></a>Fler resurser

- [Översikt över Wi-Fi-inställningar](wi-fi-settings-configure.md), inklusive andra plattformar.

- Använder du Android Enterprise- eller Android Kiosk-enheter? Om ja, se [Wi-Fi-inställningar för enheter som kör Android Enterprise och dedikerade enheter](wi-fi-settings-android-enterprise.md).
