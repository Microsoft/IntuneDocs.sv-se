---
title: Konfigurera VPN-inställningar för Windows 8.1-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa en konfigurations profil för VPN med hjälp av konfigurations inställningar för virtuella privata nätverk (VPN), inklusive anslutnings information och proxyinställningarna för att inkludera IP-eller FQDN-adress och TCP-port i Microsoft Intune på enheter som kör Windows 8,1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f9a1399d5474d79ac8fd48a8aa3a844f20eb640
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207051"
---
# <a name="add-vpn-settings-on-windows-81-devices-in-microsoft-intune"></a>Lägga till VPN-inställningar för Windows 8.1-enheter i Microsoft Intune



I den här artikeln beskrivs de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på enheter som kör Windows 8.1.

Beroende på vilka inställningar du väljer kan bara vissa värden i följande lista konfigureras.

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar

- **Använd alla inställningar endast för Windows 8,1**: Konfigurera den här inställningen i den klassiska Intune-portalen. Den här inställningen kan inte ändras i administrations Center för Microsoft Endpoint Manager. Om detta är inställt på **Konfigurerad**, tillämpas inställningarna endast på Windows 8.1-enheter. Om det är inställt på **Inte konfigurerad**, gäller inställningarna även för Windows 10-enheter.
- **Anslutningens namn**: Ange ett namn på anslutningen. Användarna ser det här namnet när de bläddrar på enheten i listan med tillgängliga VPN-anslutningar.
- **Servrar**: Lägg till en eller flera VPN-servrar som enheterna ska ansluta till.
  - **Lägg till**: Öppnar sidan **Lägg till rad** där du kan ange följande information:
    - **Beskrivning**: Ange ett beskrivande namn för servern, som t.ex. **Contoso VPN-server**.
    - **IP-adress eller fullständigt domännamn**: Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
    - **Standardserver**: Gör servern till den standardserver som enheterna använder för att upprätta anslutningen. Du ska endast ange en server som standard.
  - **Importera**: Bläddra till en kommateckenavgränsad fil som innehåller en lista med servrar i formatet: beskrivning, IP-adress eller FQDN, samt standardserver. Välj **OK** för att importera dessa servrar till listan **Servrar**.
  - **Exportera**: Exporterar listan med servrar till en kommateckenavgränsad fil (csv).

- **Anslutningstyp**: Välj VPN-anslutningstypen från följande leverantörslista:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only): Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Inloggningsgrupp eller domän** (endast SonicWall Mobile Connect): Ange namnet för den inloggningsgrupp eller domän som du vill ansluta till.

- **Roll** (endast Pulse Secure): Ange namnet för den användarroll som har åtkomst till anslutningen. En användarroll definierar personliga inställningar och alternativ, och aktiverar eller inaktiverar vissa åtkomstfunktioner.

- **Område** (endast Pulse Secure): Ange namnet för den autentiseringssfär som ska användas. En autentiseringssfär är en grupp av autentiseringsresurser som används av Pulse Secure-anslutningstypen.

- **Anpassad XML**: Ange anpassade XML-kommandon som konfigurerar VPN-anslutningen.

  **Pulse Secure-exempel**:

  ```xml
  <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
  ```

  **Kontrollpunkt för mobilt VPN-exempel**:

  ```xml
  <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
  ```

  **SonicWall Mobile Connect-exempel**:

  ```xml
  <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
  ```

  **F5 Edge Client-exempel**:

  ```xml
  <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
  ```

  Mer information om hur du skriver anpassade XML-kommandon finns i tillverkarens VPN-dokumentation.

## <a name="proxy-settings"></a>Proxyinställningar

- **Identifiera proxyinställningar automatiskt**: Om VPN-servern kräver en proxyserver för anslutningen kan du ange om du vill att enheterna automatiskt ska identifiera anslutningsinställningarna.
- **Automatiskt konfigurationsskript**: Använd en fil för att konfigurera proxyservern. Ange den **URL för proxyserver** som innehåller konfigurationsfilen. Ange till exempel `http://proxy.contoso.com`.
- **Använd proxyserver**: Aktivera det här alternativet om du vill ange inställningarna för proxyservern manuellt.
  - **Adress**: Ange proxyserverns adress (som en IP-adress).
  - **Portnummer**: Ange det portnummer som är associerat med proxyservern.
- **Kringgå proxy för lokala adresser**: Om VPN-servern kräver en proxyserver för anslutningen och du inte vill använda proxyservern för de lokala adresser som du anger väljer du det här alternativet.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Konfigurera VPN-inställningar på [Android](vpn-settings-android.md)-, [Android Enterprise](vpn-settings-android-enterprise.md)-, [MacOS](vpn-settings-macos.md)-och [Windows 10](vpn-settings-windows-10.md) -enheter.
