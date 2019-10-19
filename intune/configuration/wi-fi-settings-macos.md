---
title: Konfigurera Wi-Fi-inställningar för macOS-enheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Skapa eller lägg till en Wi-Fi-enhetskonfigurationsprofil för macOS-enheter. Se de olika inställningarna, inklusive att lägga till certifikat, välja en EAP-typ och välja en autentiseringsmetod i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c4134ada3593d316b717ff3c3239ff771736def
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490910"
---
# <a name="add-wi-fi-settings-for-macos-devices-in-microsoft-intune"></a>Lägga till Wi-Fi-inställningar för macOS-enheter i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Du kan skapa en profil med specifika Wi-Fi-inställningar och sedan distribuera profilen till dina macOS-enheter. Microsoft Intune innehåller många funktioner, inklusive autentisering till ditt nätverk, lägga till ett PKS- eller ett SCEP-certifikat och mycket mer.

Dessa Wi-Fi-inställningar är uppdelade i två kategorier: Grundläggande inställningar och inställningar på företagsnivå.

Den här artikeln beskriver dessa inställningar.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetsprofil](device-profile-create.md).

> [!NOTE]
> De här inställningarna är tillgängliga för alla registrerings typer. Mer information om registrerings typerna finns i [MacOS-registrering](../enrollment/macos-enroll.md).

## <a name="basic-profiles"></a>Grundläggande profiler

- **Wi-Fi-typ**: Välj **Grundläggande**.
- **Nätverksnamn**: Ange ett namn på Wi-Fi-anslutningen. Detta värde är det namn som användarna ser när de bläddrar i listan med tillgängliga anslutningar på sin enhet.
- **SSID**: Förkortning för **Service Set Identifier**. Den här egenskapen är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till. Användarna ser dock bara det nätverksnamn som du konfigurerade när de väljer anslutningen.
- **Anslut automatiskt**: Välj **Aktivera** för att ansluta till nätverket automatiskt när enheten är i närheten. Välj **Inaktivera** för att förhindra att enheter ansluts automatiskt.
- **Dolt nätverk**: Välj **Aktivera** för att dölja nätverket i listan med tillgängliga nätverk på enheten. SSID skickas inte. Välj **Inaktivera** för att visa nätverket i listan med tillgängliga nätverk på enheten.
- **Säkerhetstyp**: Välj det säkerhetsprotokoll som autentiserar med Wi-Fi-nätverket. Alternativen är:

  - **Öppet (ingen autentisering)** : Använd bara det här alternativet om nätverket är oskyddat.
  - **WPA/WPA2 – Personlig**: Ange lösenordet i **I förväg delad nyckel**. När nätverket är konfigurerat, konfigureras också ett lösenord eller en nätverksnyckel. Ange lösenordet eller nätverksnyckeln för PSK-värdet.
  - **WEP**

- **Proxyinställningar**: Dina alternativ:
  - **Inga**: Inga proxyinställningar konfigureras.
  - **Manuell** – Ange **Proxyserveradress** som en IP-adress och dess **Portnummer**.
  - **Automatisk**: Använd en fil för att konfigurera proxyservern. Ange den **Proxyserver-URL** (till exempel `http://proxy.contoso.com`) som innehåller konfigurationsfilen.

## <a name="enterprise-profiles"></a>Företagsprofiler

- **Wi-Fi-typ**: Välj **Företag**.
- **SSID**: Förkortning för **Service Set Identifier**. Den här egenskapen är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till. Användarna ser dock bara det nätverksnamn som du konfigurerade när de väljer anslutningen.
- **Anslut automatiskt**: Välj **Aktivera** för att ansluta till nätverket automatiskt när enheten är i närheten. Välj **Inaktivera** för att förhindra att enheter ansluts automatiskt.
- **Dolt nätverk**: Välj **Aktivera** för att dölja nätverket i listan med tillgängliga nätverk på enheten. SSID skickas inte. Välj **Inaktivera** för att visa nätverket i listan med tillgängliga nätverk på enheten.

- **EAP-typ**: Välj den EAP-typ (Extensible Authentication Protocol) som används för att autentisera skyddade trådlösa anslutningar. Alternativen är:

  - **EAP-FAST**: Ange **PAC-inställningar (Protected Access Credential)** . Det här alternativet använder autentiseringsuppgifter för skyddad åtkomst till att skapa en autentiserad tunnel mellan klienten och autentiseringsservern. Alternativen är:
    - **Använd inte (PAC)**
    - **Använd (PAC)** : Om det finns en befintlig PAC-fil använder du den.
    - **Använd och etablera PAC**: Skapa och lägg till PAC-filen till dina enheter.
    - **Använd och etablera PAC anonymt**: Skapa och lägg till PAC-filen i dina enheter utan att autentisera till servern.

  - **EAP-SIM**

  - **EAP-TLS**: Ange också:

    - **Serverförtroende** - **Certifikatservernamn**: **Lägg till** ett eller flera egna namn som används i de certifikat som utfärdats av en betrodd certifikatutfärdare (CA). När du anger den här informationen kan du hoppa över fönstret för dynamiskt förtroende som visas på användarenheter när de ansluter till Wi-Fi-nätverket.
    - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatprofil. Det här certifikatet presenteras för servern när klienten ansluter till nätverket och används för att autentisera anslutningen.

    - **Klientautentisering** - **Klientcertifikat för klientautentisering (identitetscertifikat)** : Välj den SCEP- eller PKCS-profil för klientcertifikatet som också distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

  - **EAP-TTLS**: Ange också:

    - **Serverförtroende** - **Certifikatservernamn**: **Lägg till** ett eller flera egna namn som används i de certifikat som utfärdats av en betrodd certifikatutfärdare (CA). När du anger den här informationen kan du hoppa över fönstret för dynamiskt förtroende som visas på användarenheter när de ansluter till Wi-Fi-nätverket.
    - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatprofil. Det här certifikatet presenteras för servern när klienten ansluter till nätverket och används för att autentisera anslutningen.

    - **Klientautentisering** – Välj en **Autentiseringsmetod**. Alternativen är:

      - **Användarnamn och lösenord**: Be användaren ange ett användarnamn och ett lösenord för att autentisera anslutningen. Ange även:
        - **Annan metod än EAP (inre identitet)** : Välj hur anslutningen ska autentiseras. Du måste välja samma protokoll som är konfigurerat på ditt Wi-Fi-nätverk.

          Dina alternativ: **PAP (Password Authentication Protocol)** , **CHAP (Challenge Handshake Authentication Protocol)** , **MS-CHAP (Microsoft CHAP)** eller **MS-CHAP v2 (Microsoft CHAP Version 2)**

      - **Certifikat**: Välj den SCEP- eller PKCS-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

      - **Identitetsskydd (yttre identitet)** : Ange den text som skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

  - **LEAP**

  - **PEAP**: Ange också:

    - **Serverförtroende** - **Certifikatservernamn**: **Lägg till** ett eller flera egna namn som används i de certifikat som utfärdats av en betrodd certifikatutfärdare (CA). När du anger den här informationen kan du hoppa över fönstret för dynamiskt förtroende som visas på användarenheter när de ansluter till Wi-Fi-nätverket.
    - **Rotcertifikat för serververifiering**: Välj en befintlig betrodd rotcertifikatprofil. Det här certifikatet presenteras för servern när klienten ansluter till nätverket och används för att autentisera anslutningen.

    - **Klientautentisering** – Välj en **Autentiseringsmetod**. Alternativen är:

      - **Användarnamn och lösenord**: Be användaren ange ett användarnamn och ett lösenord för att autentisera anslutningen. 

      - **Certifikat**: Välj den SCEP- eller PKCS-profil för klientcertifikatet som även distribueras till enheten. Det här certifikatet är den identitet som presenterades av enheten till servern när anslutningen autentiserades.

      - **Identitetsskydd (yttre identitet)** : Ange den text som skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst, t.ex. `anonymous`. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.

- **Proxyinställningar**: Dina alternativ:
  - **Inga**: Inga proxyinställningar konfigureras.
  - **Manuell** – Ange **Proxyserveradress** som en IP-adress och dess **Portnummer**.
  - **Automatisk**: Använd en fil för att konfigurera proxyservern. Ange den **Proxyserver-URL** (till exempel `http://proxy.contoso.com`) som innehåller konfigurationsfilen.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. Därefter [tilldelar du profilen](device-profile-assign.md) och [övervakar dess status](device-profile-monitor.md).

Konfigurera Wi-Fi-inställningar på [Android](wi-fi-settings-android.md)-, [Android Enterprise](wi-fi-settings-android-enterprise.md)-, [iOS](wi-fi-settings-ios.md)-och [Windows 10](wi-fi-settings-windows.md) -enheter.
