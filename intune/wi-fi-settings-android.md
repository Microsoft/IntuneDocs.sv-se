---
title: Konfigurera Wi-Fi-inställningar för Android-enheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Skapa eller lägga till en Wi-Fi-enhetskonfigurationsprofil för Android. Se de olika inställningarna, inklusive att lägga till certifikat, välja en EAP-typ och välja en autentiseringsmetod i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e99b934597806ea8ee4fbc8d37f53e32cf5c9abf
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842634"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Lägga till Wi-Fi-inställningar för enheter som kör Android i Microsoft Intune

Du kan skapa en profil med specifika Wi-Fi-inställningar och sedan distribuera profilen till dina Android-enheter. Microsoft Intune innehåller många funktioner, inklusive autentisering till ditt nätverk, lägga till ett PKS- eller ett SCEP-certifikat och mycket mer.

Dessa Wi-Fi-inställningar är indelade i två kategorier: Grundinställningar och inställningar på företagsnivå.

Den här artikeln beskriver dessa inställningar.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetsprofil](device-profile-create.md).

## <a name="basic-profile"></a>Grundläggande profil

- **Wi-Fi-typ**: Välj **Basic**.
- **SSID**: Förkortning för **Service Set Identifier**. Den här inställningen är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till.
- **Anslut automatiskt**: Välj **Aktivera** för att ansluta till nätverket automatiskt när enheten är i närheten. Välj **Inaktivera** för att förhindra att enheter ansluts automatiskt.
- **Dolt nätverk**: Välj **Aktivera** för att dölja nätverket i listan med tillgängliga nätverk på enheten. SSID skickas inte. Välj **Inaktivera** för att visa nätverket i listan med tillgängliga nätverk på enheten.

## <a name="enterprise-profile"></a>Företagsprofil

- **Wi-Fi-typ**: Välj **Företag**.
- **SSID**: Förkortning för **Service Set Identifier**. Den här inställningen är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till.
- **Anslut automatiskt**: Välj **Aktivera** för att ansluta till nätverket automatiskt när enheten är i närheten. Välj **Inaktivera** för att förhindra att enheter ansluts automatiskt.
- **Dolt nätverk**: Välj **Aktivera** för att dölja nätverket i listan med tillgängliga nätverk på enheten. SSID skickas inte. Välj **Inaktivera** för att visa nätverket i listan med tillgängliga nätverk på enheten.
- **EAP-typ**: Välj den EAP-typ (Extensible Authentication Protocol) som används för att autentisera säkra trådlösa anslutningar. Alternativen är: 

  - **EAP-TLS**: Ange även:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatsprofil. Det här certifikatet presenteras för servern när klienten ansluter till nätverket och används för att autentisera anslutningen.

      Klicka på **OK** för att spara ändringarna.

    - **Klientautentisering** - **Klientcertifikat för klientautentisering (identitetscertifikat)**: Välj den SCEP- eller PKCS-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

      Klicka på **OK** för att spara ändringarna.

  - **EAP-TTLS**: Ange även:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatsprofil. Det här certifikatet presenteras för servern när klienten ansluter till nätverket och används för att autentisera anslutningen.

      Klicka på **OK** för att spara ändringarna.

    - **Klientautentisering** – Välj en **Autentiseringsmetod**. Alternativen är:

      - **Användarnamn och lösenord**: Be användaren ange ett användarnamn och ett lösenord för att autentisera anslutningen. Ange även:
        - **Annan metod än EAP (inre identitet)**: Välj hur du ska autentisera anslutningen. Du måste välja samma protokoll som är konfigurerat på ditt Wi-Fi-nätverk.

          Alternativen är: **Okrypterat lösenord (PAP)**, **CHAP (Challenge Handshake Authentication Protocol)**, **MS-CHAP (Microsoft CHAP)** eller **MS-CHAP v2 (Microsoft CHAP Version 2)**

      - **Certifikat**: Välj den SCEP- eller PKCS-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

        Klicka på **OK** för att spara ändringarna.

      - **Identitetssekretess (yttre identitet)**: Ange den text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

  - **PEAP**: Ange även:

    - **Serverförtroende** - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatsprofil. Det här certifikatet presenteras för servern när klienten ansluter till nätverket och används för att autentisera anslutningen.

      Klicka på **OK** för att spara ändringarna.

    - **Klientautentisering** – Välj en **Autentiseringsmetod**. Alternativen är:

      - **Användarnamn och lösenord**: Be användaren ange ett användarnamn och ett lösenord för att autentisera anslutningen. Ange även:
        - **Annan metod än EAP för autentisering (inre identitet)**: Välj hur du ska autentisera anslutningen. Du måste välja samma protokoll som är konfigurerat på ditt Wi-Fi-nätverk.

          Alternativen är: **Ingen** eller **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certifikat**: Välj den SCEP- eller PKCS-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

        Klicka på **OK** för att spara ändringarna.

      - **Identitetssekretess (yttre identitet)**: Ange den text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

Välj **OK** > **Skapa** för att spara ändringarna. Profilen skapas och visas i profillistan.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. Nu ska vi [tilldela den här profilen](device-profile-assign.md).

## <a name="more-resources"></a>Fler resurser

- [Översikt över Wi-Fi-inställningar](wi-fi-settings-configure.md), inklusive andra plattformar.

- Använder du Android Enterprise- eller Android Kiosk-enheter? Om ja, se [Wi-Fi-inställningar för enheter som kör Android Enterprise och Android Kiosk](wi-fi-settings-android-enterprise.md).
