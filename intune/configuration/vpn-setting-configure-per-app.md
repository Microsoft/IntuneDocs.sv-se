---
title: Konfigurera VPN per app för iOS/iPadOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se förutsättningarna, och skapa en grupp för VPN-användare (virtuella privata nätverk), lägg till en SCEP-certifikatsprofil, konfigurera en VPN-profil per app och tilldela vissa appar till VPN-profilen i Microsoft Intune på iOS/iPadOS-enheter. Visar också stegen för att verifiera VPN-anslutningen på enheten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd53172a1086f48dc1646e1b8a63de8bec37b934
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512610"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-iosipados-devices-in-intune"></a>Konfigurera ett virtuellt privat nätverk (VPN) per app för iOS/iPadOS-enheter i Intune

I Microsoft Intune kan du skapa och använda virtuella privata nätverk (VPN) tilldelade till en app. Den här funktionen kallas för "per app-VPN". Du väljer de hanterade apparna som kan använda ditt VPN på enheter som hanteras av Intune. När du använder en per app-VPN ansluter slutanvändarna automatiskt via VPN och får åtkomst till organisationsresurser, till exempel dokument.

Den här funktionen gäller för:

- iOS 9 och senare
- iPadOS 13.0 och senare

Kontrollera VPN-leverantörens dokumentation för att se om VPN stöder per app-VPN.

Den här artikeln visar hur du skapar en per app-VPN-profil och tilldelar profilen till dina appar. Använd dessa steg för att skapa en sömlös per app-VPN-miljö för dina slutanvändare. För de flesta VPN:er som stöder per app-VPN öppnar användaren en app och ansluter automatiskt till VPN.

Vissa VPN:er tillåter autentisering med användarnamn och lösenord med per app-VPN. Det betyder att användarna måste ange ett användarnamn och lösenord för anslutning till VPN.

> [!IMPORTANT]
> Per app-VPN stöds inte för IKEv2 VPN-profiler för iOS/iPadOS.

## <a name="per-app-vpn-with-zscaler"></a>Per app-VPN med Zscaler

Zscaler Private Access (ZPA) integreras med Azure Active Directory (Azure AD) för autentisering. När du använder ZPA behöver du inte profilerna för [betrott certifikat](#create-a-trusted-certificate-profile) eller [SCEP- eller PKCS-certifikat](#create-a-scep-or-pkcs-certificate-profile) (som beskrivs i den här artikeln). Om du har en per app-VPN-profil konfigurerad för Zscaler och öppnar någon av de associerade apparna ansluts den inte automatiskt till ZPA. Istället måste användaren logga in på Zscaler-appen först. Sedan begränsas fjärråtkomst till de associerade apparna.

## <a name="prerequisites-for-per-app-vpn"></a>Krav för VPN per app

> [!IMPORTANT]
> Din VPN-leverantör kan ha andra krav för VPN per app, till exempel specifik maskinvara eller licensiering. Läs leverantörens dokumentation och kontrollera att du uppfyller kraven innan du konfigurerar VPN per app i Intune.

För att bevisa sin identitet visar VPN-servern det certifikat som måste godkännas av enheten utan att tillfråga att användaren. Skapa en profil för betrott certifikat som innehåller VPN-serverns rotcertifikat som utfärdats av certifikatutfärdaren (CA) för att bekräfta automatiskt godkännande av certifikatet. 

### <a name="export-the-certificate-and-add-the-ca"></a>Exportera certifikatet och lägg till certifikatutfärdaren (CA)

1. Öppna administrationskonsolen på VPN-servern.
2. Bekräfta att VPN-servern använder certifikatbaserad autentisering. 
3. Exportera den betrodda rotcertifikatfilen. Den har filnamnstillägget CER och du lägger till den när du skapar en profil för betrott certifikat.
4. Lägg till namnet på den certifikatutfärdare som utfärdade certifikatet för autentisering till VPN-servern.

    Om certifikatutfärdaren som presenterades för enheten matchar en certifikatutfärdare i listan över betrodda certifikatutfärdare på VPN-servern autentiserar VPN-servern enheten.

## <a name="create-a-group-for-your-vpn-users"></a>Skapa en grupp för VPN-användare

Skapa eller välj en befintlig grupp i Azure Active Directory (AD Azure) för användarna eller enheterna som använder per app-VPN. Information om hur du skapar en ny grupp finns i [Lägga till grupper för att organisera användare och enheter](../fundamentals/groups-add.md).

## <a name="create-a-trusted-certificate-profile"></a>Skapa en betrodd certifikatprofil

Importera VPN-serverns rotcertifikat som utfärdats av certifikatutfärdaren till en profil som skapats i Intune. Den betrodda certifikatprofilen instruerar iOS/iPadOS-enheten att automatiskt ha förtroende för den certifikatutfärdare som VPN-servern anger.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande egenskaper:
    - **Namn**: Ange ett beskrivande namn på profilen. Namnge dina profiler så att du enkelt kan identifiera dem senare. Ett exempel på ett bra profilnamn är **iOS trusted certificate VPN profile for entire company** (VPN-profil för betrodda iOS/iPadOS-certifikat för hela företaget).
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **iOS/iPadOS**.
    - **Profiltyp**: Välj **Betrott certifikat**.
4. Välj mappikonen och bläddra till VPN-certifikatet (CER-filen) som du exporterade från VPN-administrationskonsolen. 
5. Välj **OK** > **Skapa**.

    ![Skapa en profil för betrott certifikat för iOS/iPadOS-enheterna i Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>Skapa en SCEP- eller PKCS-certifikatprofil

Den betrodda rotcertifikatprofilen gör det möjligt för enheten att automatiskt ha förtroende för VPN-servern. SCEP- eller PKCS-certifikatet tillhandahåller autentiseringsuppgifter från iOS/iPadOS VPN-klienten till VPN-servern. Certifikatet tillåter att enheten autentiserar tyst utan att användaren tillfrågas om användarnamn och lösenord. 

Om du vill konfigurera och tilldela klientautentiseringscertifikatet läser du någon av följande artiklar:

- [Konfigurera infrastrukturen för att stödja SCEP med Intune](../protect/certificates-scep-configure.md)
- [Konfigurera och hantera PKCS-certifikat med Intune](../protect/certficates-pfx-configure.md)

Se till att konfigurera certifikatet för klientautentisering. Du kan ange det här direkt i SCEP-certifikatprofiler (listan **Förbättrad nyckelanvändning** > **Klientautentisering**). För PKCS anger du klientautentisering i certifikatmallen i certifikatutfärdaren (CA).

![Skapa en SCEP-certifikatprofil i Microsoft Intune, inklusive ämnesnamnets format, nyckelanvändning med mera](./media/vpn-setting-configure-per-app/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Skapa profil för VPN per app

VPN-profilen innehåller SCEP- eller PKCS-certifikatet med klientens autentiseringsuppgifter, anslutningsinformation för det virtuella privata nätverket och VPN per app-flaggan för aktivering av funktionen i iOS/iPadOS-appen.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
2. Ange följande egenskaper:
    - **Namn**: Ange ett beskrivande namn för den anpassade profilen. Namnge dina profiler så att du enkelt kan identifiera dem senare. Ett exempel på ett bra profilnamn är **iOS/iPadOS per-app VPN profile for entire company** (VPN-profil per iOS/iPadOS-app för hela företaget).
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **iOS/iPadOS**.
    - **Profiltyp**: Välj **VPN**.
3. I **Anslutningstyp** väljer du din VPN-klientapp.
4. Välj **Bas-VPN**. [iOS/iPadOS VPN-inställningar](vpn-settings-ios.md) listar och beskriver alla inställningar. När du använder per app-VPN ser du till att ange följande egenskaper enligt listan:

    - **Autentiseringsmetod**: Välj **Certifikat**. 
    - **Autentiseringscertifikat**: Välj ett befintligt SCEP- eller PKCS-certifikat > **OK**.
    - **Delade tunnlar**: Välj **Inaktivera** för att tvinga all trafik att använda VPN-tunneln när VPN-anslutningen är aktiv. 

      ![I en per app-VPN-profil anger du en anslutning, en IP-adress eller ett fullständigt domännamn, en autentiseringsmetod samt delade tunnlar i Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-create-vpn-profile.png)

    Information om de andra inställningarna finns i [iOS/iPadOS VPN-inställningar](vpn-settings-ios.md).

5. Välj **Automatisk VPN** > **Typ av automatiskt virtuellt privat nätverk** > **Per app-VPN**

    ![I Intune anger du Automatisk VPN till per app-VPN på iOS/iPadOS-enheter](./media/vpn-setting-configure-per-app/vpn-per-app-automatic.png)

6. Välj **OK** > **OK** > **Skapa**.

## <a name="associate-an-app-with-the-vpn-profile"></a>Associera en app med VPN-profilen

När du har lagt till VPN-profilen associerar du appen och Azure AD-gruppen med profilen.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Appar** > **Alla appar**.
2. Välj en app i listan > **Tilldelningar** > **Lägg till grupp**.
3. I **Tilldelningstyp** väljer du **Krävs** eller **Tillgänglig för registrerade enheter**.
4. Välj **Inkluderade grupper** > **Välj grupper att ta med** > välj gruppen [du har skapat](#create-a-group-for-your-vpn-users) (i den här artikeln) > **Välj**.
5. I **VPN-anslutningar** väljer du per app-VPN-profilen [du har skapat](#create-a-per-app-vpn-profile) (i den här artikeln).

    ![Tilldela en app till per app-VPN-profilen i Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-app-to-vpn.png)

6. Välj **OK** > **Spara**.

En association mellan en app och en profil tas bort nästa gång enheten checkar in när alla följande villkor är uppfyllda:

- appen har ett mål med obligatorisk installation som avsikt
- både profilen och appen har samma grupp som mål.
- Du tar bort VPN per app-konfigurationen från apptilldelningen.

En association mellan en app och en profil finns kvar tills slutanvändaren begär en ominstallation från Företagsportal om följande villkor är uppfyllda:

- appen har ett mål med tillgänglig installation som avsikt
- både profilen och appen har samma grupp som mål.
- Slutanvändaren begärde appinstallationen från Företagsportal, så appen och profilen installeras på enheten.
- Du tar bort eller ändrar VPN per app-konfigurationen från apptilldelningen.

## <a name="verify-the-connection-on-the-iosipados-device"></a>Kontrollera anslutningen till iOS/iPadOS-enheten

När VPN per app har konfigurerats och associerats med appen kontrollerar du att anslutningen fungerar från en enhet.

### <a name="before-you-attempt-to-connect"></a>Innan du försöker ansluta

- Se till att du distribuerar alla ovan nämnda principer till samma grupp. Annars fungerar inte per app-VPN-gränssnittet.
- Om du använder Pulse Secure VPN-appen eller en anpassad VPN-klientapp kan välja du att använda händelsedirigering nedåt på appnivå eller på paketnivå. Ställ in värdet **Providertyp** på **app-proxy** för händelsedirigering på appnivå eller **paket-tunnel** för händelsedirigering på paketnivå. Kontrollera VPN-leverantörens dokumentation för att se till att du använder rätt värde.

### <a name="connect-using-the-per-app-vpn"></a>Ansluta via VPN per app

Kontrollera att zero touch-upplevelsen fungerar genom att ansluta utan att behöva välja det virtuella privata nätverket eller ange dina autentiseringsuppgifter. Zero touch-upplevelse innebär:

- Enheten ber dig inte att ha förtroende för VPN-servern. Med andra ord visas dialogrutan **Dynamiskt förtroende** för användaren.
- Användaren behöver inte ange autentiseringsuppgifterna.
- Användarens enhet är ansluten till VPN när användaren öppnar någon av de associerade apparna.

## <a name="next-steps"></a>Nästa steg

- I dokumentationen om [VPN-inställningar för iOS/iPadOS-enheter i Microsoft Intune](vpn-settings-ios.md) finns information om iOS/iPadOS-inställningar.
- I dokumentationen om hur du [konfigurerar VPN-inställningar i Microsoft Intune](vpn-settings-configure.md) finns information om VPN-inställningar och Intune.
