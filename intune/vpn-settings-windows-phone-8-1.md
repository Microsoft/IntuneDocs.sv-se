---
title: "VPN-inställningar i Intune för Windows Phone 8.1-enheter"
titleSuffix: Azure portal
description: "Lär dig mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på Windows Phone 8.1-enheter.”"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1a9053f-02a7-4735-bc0d-fe4573b31ed4
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: debfe6cde108daf88db8d18db1e7da2186fc32ea
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="vpn-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>VPN-inställningar för Windows Phone 8.1-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Beroende på vilka inställningar du väljer, är inte alla värden i listan nedan konfigurerbara.

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar

- **Använd alla inställningar endast för Windows Phone 8.1** – Detta är en inställning som du kan konfigurera i den klassiska Intune-portalen. Den här inställningen kan inte ändras i Azure-portalen. Om inställningen anges till **Konfigurerad**, tillämpas inställningar endast på Windows Phone 8.1-enheter. Om inställningen anges till **Inte konfigurerad**, gäller de här inställningarna även för Windows 10 Mobile-enheter.
- **Anslutningsnamn** – Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **Autentiseringsmetod** – Välj hur enheter ska autentiseras mot VPN-servern från:
    - **Certifikat** – Under **Autentiseringscertifikat** väljer du den SCEP- eller PKCS-certifikatprofil som du skapade tidigare för att autentisera anslutningen. Mer information om certifikatprofiler finns i [Så här konfigurerar du certifikat](certificates-configure.md).
    - **Användarnamn och lösenord** – Slutanvändare måste ange ett användarnamn och lösenord för att logga in på VPN-servern.
- **Servrar** – Lägg till en eller flera VPN-servrar som enheterna ska ansluta till.
    - **Lägg till** – Öppnar bladet **Lägg till rad** där du kan ange följande information:
        - **Beskrivning** – Ange ett beskrivande namn för servern, som t.ex. **Contoso VPN-server**.
        - **IP-adress eller FQDN** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
        - **Standardserver** – Gör den här servern till den standardserver som enheterna använder för att upprätta anslutningen. Du ska endast ange en server som standard.
    - **Importera** – Bläddra till en fil som innehåller en kommateckenavgränsad lista med servrar i formatbeskrivning, IP-adress eller FQDN, samt standardserver. Välj **OK** för att importera dessa till listan **Servrar**.
    - **Exportera** – Exporterar listan med servrar till en kommateckenavgränsad fil (csv).

- **Kringgå VPN i företagets trådlösa nätverk** – Aktivera det här alternativet om du vill ange att VPN-anslutningen inte ska användas när enheten är ansluten till företagets trådlösa nätverk.
- **Kringgå VPN i trådlöst hemnätverk** – Aktivera det här alternativet om du vill ange att VPN-anslutningen inte ska användas när enheten är ansluten till ett trådlöst hemnätverk.

- **Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
    - **Check Point Capsule VPN**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

- **Inloggningsgrupp eller domän** (endast Dell SonicWALL Mobile Connect) – Ange namnet på den inloggningsgrupp eller domän som du vill ansluta till.
- **Roll** (endast Pulse Secure) – Ange namnet på den användarroll som har åtkomst till anslutningen. En användarroll definierar personliga inställningar och alternativ, och aktiverar eller inaktiverar vissa åtkomstfunktioner.
- **Sfär** (endast Pulse Secure) – Ange namnet på den autentiseringssfär som du vill använda. En autentiseringssfär är en grupp av autentiseringsresurser som används av Pulse Secure-anslutningstypen.

- **Söklista för DNS-suffix** - **Lägg till** ett eller flera DNS-suffix. Varje DNS-suffix som du anger genomsöks vid anslutning till en webbplats med ett kort namn. Ange till exempel DNS-suffixen **domain1.contoso.com** och **domain2.contoso.com**. Besök webbadressen **http://mywebsite** så genomsöks webbadresserna **http://mywebsite.domain1.contoso.com** och **http://mywebsite.domain2.contoso.com**.

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

- **Delade tunnlar** - **Aktivera** eller **Inaktivera** detta alternativ för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.




## <a name="proxy-settings"></a>Proxyinställningar

- **Identifiera proxyinställningar automatiskt** – Om VPN-servern kräver en proxyserver för anslutningen, kan du ange om du vill att enheterna automatiskt ska identifiera anslutningsinställningarna. Mer information finns i dokumentationen till Windows Server.
- **Skript för automatisk konfigurering** – Använd en fil för att konfigurera proxyservern. Ange den **webbadress till proxyserver** (till exempel **http://proxy.contoso.com**) som innehåller konfigurationsfilen.
- **Använd proxyserver** – Aktivera det här alternativet om du vill ange inställningarna för proxyservern manuellt.
    - **Adress** – Ange proxyns serveradress (som en IP-adress).
    - **Portnummer** – Ange det portnummer som är kopplat till proxyservern.
- **Kringgå proxy för lokala adresser** – Välj det här alternativet om VPN-servern kräver en proxyserver för anslutningen och du inte vill använda proxyservern för de lokala adresser som du anger. Mer information finns i dokumentationen till Windows Server.
