---
title: "Intunes VPN-inställningar för Windows 8.1-enheter | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Lär dig mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på Windows 8.1-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 21ed25c1c0afd2c3fa45c15d4aa40d9c8d57b35a


---

# <a name="vpn-settings-for-windows-81-devices-in-microsoft-intune"></a>VPN-inställningar för Windows 8.1-enheter i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Beroende på vilka inställningar du väljer, är inte alla värden i listan nedan konfigurerbara.

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar


- **Använd alla inställningar endast för Windows 8.1** – Detta är en inställning som du kan konfigurera i den klassiska Intune-portalen. Den här inställningen kan inte ändras i Azure-portalen. Om detta anges till **Konfigurerad**, tillämpas inställningarna endast på Windows 8.1-enheter. Om värdet anges till **Inte konfigurerad**, gäller de här inställningarna även för Windows 10-enheter.
- **Anslutningsnamn** – Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **Servrar** – Lägg till en eller flera VPN-servrar som enheterna ska ansluta till.
    - **Lägg till** – Öppnar bladet **Lägg till rad** där du kan ange följande information:
        - **Beskrivning** – Ange ett beskrivande namn för servern, som t.ex. **Contoso VPN-server**.
        - **IP-adress eller FQDN** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
        - **Standardserver** – Gör den här servern till den standardserver som enheterna använder för att upprätta anslutningen. Du ska endast ange en server som standard.
    - **Importera** – Bläddra till en fil som innehåller en kommateckenavgränsad lista med servrar i formatbeskrivning, IP-adress eller FQDN, samt standardserver. Välj **OK** för att importera dessa till listan **Servrar**.
    - **Exportera** – Exporterar listan med servrar till en kommateckenavgränsad fil (csv).

- **Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
- **Check Point Capsule VPN**
- **Dell SonicWALL Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Inloggningsgrupp eller domän** (endast Dell SonicWALL Mobile Connect) – Ange namnet på den inloggningsgrupp eller domän som du vill ansluta till.

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

**Exempel för Dell SonicWALL Mobile Connect:**
```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>

```

**Exempel för F5 Edge Client:**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>

```

Läs VPN-dokumentationen för varje tillverkare för mer information om hur du skriver anpassade XML-kommandon.


## <a name="proxy-settings"></a>Proxyinställningar

- **Identifiera proxyinställningar automatiskt** – Om VPN-servern kräver en proxyserver för anslutningen, kan du ange om du vill att enheterna automatiskt ska identifiera anslutningsinställningarna. Mer information finns i dokumentationen till Windows Server.
- **Skript för automatisk konfigurering** – Använd en fil för att konfigurera proxyservern. Ange den **webbadress till proxyserver** (till exempel **http://proxy.contoso.com**) som innehåller konfigurationsfilen.
- **Använd proxyserver** – Aktivera det här alternativet om du vill ange inställningarna för proxyservern manuellt.
    - **Adress** – Ange proxyns serveradress (som en IP-adress).
    - **Portnummer** – Ange det portnummer som är kopplat till proxyservern.
- **Kringgå proxy för lokala adresser** – Välj det här alternativet om VPN-servern kräver en proxyserver för anslutningen och du inte vill använda proxyservern för de lokala adresser som du anger. Mer information finns i dokumentationen till Windows Server.



<!--HONumber=Feb17_HO3-->


