---
title: "VPN-inställningar i Microsoft Intune för Windows 8.1-enheter"
titleSuffix: 
description: "Läs mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på enheter som kör Windows 8.1."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8ced3e03fa337034076af75c7984a30cd75105bb
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-81"></a>Konfigurera VPN-inställningar i Microsoft Intune för enheter som kör Windows 8.1

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på enheter som kör Windows 8.1.

Beroende på vilka inställningar du väljer kan bara vissa värden i följande lista konfigureras.

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar


- **Använd alla inställningar endast för Windows 8.1** – Detta är en inställning som du kan konfigurera i den klassiska Intune-portalen. Den här inställningen kan inte ändras i Azure-portalen. Om detta är inställt på **Konfigurerad**, tillämpas inställningarna endast på Windows 8.1-enheter. Om det är inställt på **Inte konfigurerad**, gäller inställningarna även för Windows 10-enheter.
- **Anslutningsnamn** – Ange ett namn på anslutningen. Användarna ser det här namnet när de bläddrar på enheten i listan med tillgängliga VPN-anslutningar.
- **Servrar** – Lägg till en eller flera VPN-servrar som enheterna ansluter till.
    - **Lägg till** – Öppnar sidan **Lägg till rad** där du kan ange följande information:
        - **Beskrivning** – Ange ett beskrivande namn för servern, som t.ex. **Contoso VPN-server**.
        - **IP-adress eller fullständigt domännamn** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
        - **Standardserver** – Gör den här servern till den standardserver som enheterna använder för att upprätta anslutningen. Du ska endast ange en server som standard.
    - **Importera** – Bläddra till en fil som innehåller en kommateckenavgränsad lista med servrar i formatbeskrivning, IP-adress eller FQDN, samt standardserver. Välj **OK** för att importera dessa till listan **Servrar**.
    - **Exportera** – Exporterar listan med servrar till en kommateckenavgränsad fil (csv).

- **Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
- **Check Point Capsule VPN**
- **SonicWall Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Inloggningsgrupp eller domän** (endast SonicWall Mobile Connect) – Ange namnet på den inloggningsgrupp eller domän som du vill ansluta till.

- **Roll** (endast Pulse Secure) – Ange namnet på den användarroll som har åtkomst till anslutningen. En användarroll definierar personliga inställningar och alternativ, och aktiverar eller inaktiverar vissa åtkomstfunktioner.

- **Sfär** (endast Pulse Secure) – Ange namnet på den autentiseringssfär som du vill använda. En autentiseringssfär är en grupp av autentiseringsresurser som används av Pulse Secure-anslutningstypen.


- **Anpassad XML** – Ange anpassade XML-kommandon som konfigurerar VPN-anslutningen.

**Exempel för Pulse Secure:**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>

```

**Exempel för CheckPoint Mobile VPN:**
```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />

```

**Exempel för SonicWall Mobile Connect:**
```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>

```

**Exempel för F5 Edge Client:**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>

```

Mer information om hur du skriver anpassade XML-kommandon finns i varje tillverkares VPN-dokumentation.


## <a name="proxy-settings"></a>Proxyinställningar

- **Identifiera proxyinställningar automatiskt** – Om VPN-servern kräver en proxyserver för anslutningen, kan du ange om du vill att enheterna automatiskt ska identifiera anslutningsinställningarna. Mer information finns i dokumentationen till Windows Server.
- **Skript för automatisk konfigurering** – Använd en fil för att konfigurera proxyservern. Ange den **webbadress till proxyserver** (till exempel **http://proxy.contoso.com**) som innehåller konfigurationsfilen.
- **Använd proxyserver** – Aktivera det här alternativet om du vill ange inställningarna för proxyservern manuellt.
    - **Adress** – Ange proxyns serveradress (som en IP-adress).
    - **Portnummer** – Ange det portnummer som är kopplat till proxyservern.
- **Kringgå proxy för lokala adresser** – Välj det här alternativet om VPN-servern kräver en proxyserver för anslutningen och du inte vill använda proxyservern för de lokala adresser som du anger. Mer information finns i dokumentationen till Windows Server.
