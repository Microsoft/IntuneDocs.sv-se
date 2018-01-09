---
title: "Konfigurera virtuellt privat nätverk per app i Microsoft Intune för iOS-enheter"
titleSuffix: Intune on Azure
description: "Ange vilka hanterade appar som kan använda ditt virtuella privata nätverk på Intune-hanterade iOS-enheter."
keywords: 
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 10/5/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1a37fcc372db6fec9f460fdc242cd6d2294f96e1
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2018
---
# <a name="set-up-per-app-vpn-in-microsoft-intune-for-ios-devices"></a>Konfigurera virtuellt privat nätverk per app i Microsoft Intune för iOS-enheter

Du kan ange vilka hanterade appar som ska kunna använda ditt virtuella privata nätverk (VPN) på Intune-hanterade iOS-enheter. När du anger ett virtuellt privat nätverk per app i Intune ansluter en slutanvändare automatiskt via ditt virtuella privata nätverk vid åtkomst till företagets dokument.

## <a name="prerequisites-for-the-per-app-vpn"></a>Krav för virtuellt privat nätverk per app

För att bevisa sin identitet visar VPN-servern det certifikat som måste godkännas av enheten utan att tillfråga att användaren. Skapa en profil för betrott certifikat som innehåller VPN-serverns rotcertifikat som utfärdats av certifikatutfärdaren (CA) för att säkerställa automatiskt godkännande av certifikatet. 

Exportera certifikatet och lägg till certifikatutfärdaren (CA).

1. Öppna administrationskonsolen på VPN-servern.
2. Verifiera att VPN-servern använder certifikatbaserad autentisering. 
3. Exportera den betrodda rotcertifikatfilen. Den har filnamnstillägget CER och du lägger till den när du skapar en profil för betrott certifikat.
4. Lägg till namnet på den certifikatutfärdare som utfärdade certifikatet för autentisering till VPN-servern.
    Om certifikatutfärdaren som presenterades för enheten matchar en av certifikatutfärdarna i listan över betrodda certifikatutfärdare på VPN-servern autentiserar VPN-servern enheten.

## <a name="create-a--group-for-your-vpn-users"></a>Skapa en grupp för VPN-användare

Skapa eller välj en befintlig grupp i Azure Active Directory (AD Azure) som innehåller de medlemmar som har åtkomst till det virtuella privata nätverket per app.

1. Öppna Azure-portalen. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
2. Välj **Grupper** och klicka på **Ny grupp**.
3. Ange **namnet** för gruppen. 
4. Ange en kort **beskrivning** av gruppen. 
5. Välj **Tilldelad** som **Medlemskapstyp**.
6. Välj **Nej** för **Aktivera Office funktioner**.
7. Sök efter VPN-användare efter namn eller e-postadress på bladet **Medlemmar**.
8. Markera varje användare och klicka på **Välj**.
9. Klicka på **Skapa**

## <a name="create-a-trusted-certificate-profile"></a>Skapa en betrodd certifikatprofil

Importera VPN-serverns rotcertifikat som utfärdats av certifikatutfärdaren till en profil som skapats i Intune. Den betrodda certifikatprofilen instruerar iOS-enheten att automatiskt ha förtroende för den certifikatutfärdare som VPN-servern anger.

1. Öppna Azure-portalen. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
2. Välj **Enhetskonfiguration** och klicka sedan på **Profiler**.
3. Klicka på **+ Skapa profil**. I **Skapa profil**:
    1. Ange **namnet**.
    2. Ange **beskrivningen**.
    3. Välj **iOS** för **plattformen**.
    4. Välj **Betrott certifikat** för **profiltypen**.
4. Klicka på mappikonen och bläddra till VPN-certifikatet (CER-filen) som du exporterade från VPN-administrationskonsolen. Klicka på OK
5. Klicka på **Skapa**.

    ![Skapa en betrodd certifikatprofil](media\vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-certificate-profile"></a>Skapa en SCEP-certifikatprofil

Den betrodda rotcertifikatprofilen gör det möjligt för iOS att automatiskt ha förtroende för VPN-servern. SCEP-certifikatet tillhandahåller autentiseringsuppgifter från iOS VPN-klienten till VPN-servern. Certifikatet tillåter att enheten autentiserar tyst utan att användaren av iOS-enheten tillfrågas om användarnamn och lösenord. 

1. Öppna Azure-portalen. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**. 
2. Välj **Enhetskonfiguration** och klicka sedan på **Profiler**.
3. Klicka på **+ Skapa profil**. I **Skapa profil**:
    1. Ange **namnet**.
    2. Ange **beskrivningen**.
    3. Välj **iOS** för **plattformen**.
    4. Välj **SCEP-certifikat** för **profiltypen**.
4. Välj **År** och ange `2` för **certifikatets giltighetsperiod**.
5. Välj **Eget namn** för **Ämnesnamnets format**.
6. Välj **Användarens unika namn (UPN)** för **Alternativt namn för certifikatmottagare**.
7. Välj **Digital signatur** och **Nyckelchiffrering** för **Nyckelanvändning**.
8. Välj **2048** för **Nyckelstorlek (bitar)**.
9. Klicka på rotcertifikat och välj ett SCEP-certifikat. Klicka på **OK**.
10. Ange `Client Authentication` i **Namn** för **Förbättrad nyckelanvändning**.
11. Ange `1.3.6.1.5.5.7.3.2` i **Objektidentifierare**.
12. Klicka på **Lägg till**.
13. Ange ***server-URL:en*** och klicka på **Lägg till**.
14. Klicka på **OK**.
15. Klicka på **Skapa**.

    ![Skapa en SCEP-certifikatprofil](media\vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Skapa profil för virtuellt privat nätverk per app

VPN-profilen innehåller SCEP-certifikatet med klientens autentiseringsuppgifter, anslutningsinformationen för det virtuella privata nätverket och flaggan för det virtuella privata nätverket per app för att aktivera funktionen för det virtuella privata nätverket per app för användning av iOS-programmet.

1. Öppna Azure-portalen. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
2. Välj **Enhetskonfiguration** och klicka sedan på **Profiler**.
3. Klicka på **+ Skapa profil**. I **Skapa profil**:
    1. Ange **namnet**.
    2. Ange **beskrivningen**.
    3. Välj **iOS** för **plattformen**.
    4. Välj **VPN** för **profiltypen**.
4. Välj **Bas-VPN**. I **Bas-VPN**:
    1. Ange **Anslutningsnamn**.
    2. Ange **IP-adress eller fullständigt domännamn**.
    3. Välj **Certifikat** för **autentiseringsmetoden**.
    4. Välj SCEP-certifikatet under **Autentiseringscertifikat** och klicka på **OK**.
    5. Välj ditt virtuella privata nätverk för **anslutningstypen**.
    6. Konfigurera attributen för det virtuella privata nätverket om det behövs.
    7. Välj **Inaktivera delade** tunnlar.
5. Klicka på **Automatiskt virtuellt privat nätverk**. I **Automatiskt virtuellt privat nätverk**:
    1. Välj **Virtuellt privat nätverk per app** för **Typ av automatiskt virtuellt privat nätverk**.
    2. Ange URL:en för det virtuella privata nätverket och klicka på **Lägg till**.
    3. Klicka på **OK**.
6. Klicka på **OK**.
7. Klicka på **Skapa**.

    ![Skapa en profil för virtuellt privat nätverk per app](media\vpn-per-app-create-vpn-profile.png)


## <a name="associate-an-app-with-the-vpn-profile"></a>Associera en app med VPN-profilen

När du har lagt till VPN-profilen associerar du appen och Azure AD-gruppen med profilen.

1. Öppna Azure-portalen. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
2. Välj **Mobile Apps**.
3. Klicka på **Appar**.
4. Välj appen från listan över appar.
5. Klicka på **Tilldelningar**.
6. Klicka på **Välj grupper** och välj den grupp som du angav tidigare. Klicka på **Välj**.
7. Välj **Krävs** för **Typ** på bladet **Tilldelningar**.
8. Välj din VPN-definition för de **virtuella privata nätverken**.
 
    > [!NOTE]  
    > Ibland tar det upp till en minut för VPN-definitionen att hämta värdet. Vänta 3–5 minuter innan du klickar på **Spara**.

9. Klicka på **Spara**.

    ![Associera en app med det virtuella privata nätverket](media\vpn-per-app-app-to-vpn.png)

## <a name="verify-the-connection-on-the-ios-device"></a>Kontrollera anslutningen till iOS-enheten

När det virtuella privata nätverket per app har konfigurerats och associerats med appen kan du kontrollera att anslutningen fungerar från en enhet.

### <a name="before-you-attempt-to-connect"></a>Innan du försöker ansluta

 - Kontrollera att du kör iOS 7 eller senare.
 - Se till att du distribuerar *alla* ovan nämnda principer till samma grupp av användare. Det virtuella privata nätverket per app kommer inte att fungera som det ska om du inte utför dessa åtgärder.  
 - Kontrollera att VPN-appen från tredje part är installerad. Följande VPN-appar stöds:
    - Pulse Secure
    - Checkpoint
    - F5
    - SonicWall

### <a name="connect-using-the-per-app-vpn"></a>Anslut med hjälp av det virtuella privata nätverket per app

Kontrollera att zero touch-upplevelsen fungerar genom att ansluta utan att behöva välja det virtuella privata nätverket eller ange dina autentiseringsuppgifter. Zero touch-upplevelse innebär:

 - Enheten ber dig inte att ha förtroende för VPN-servern. Med andra ord visas dialogrutan **Dynamiskt förtroende**.
 - Du behöver inte ange autentiseringsuppgifterna.
 - När du trycker på anslutningsknappen ansluts du till det virtuella privata nätverket.

Kontrollera anslutningen på en iOS-enhet.

1. Tryck på VPN-appen.
2. Tryck på **Anslut**.  
Det virtuella privata nätverket ansluter utan några fler uppmaningar.

<!-- ## Troubleshooting the Per-App VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>Nästa steg

- I dokumentationen om [VPN-inställningar för iOS-enheter i Microsoft Intune](vpn-settings-ios.md) finns information om iOS-inställningar.
-  I dokumentationen om hur du [konfigurerar VPN-inställningar i Microsoft Intune](vpn-settings-configure.md) finns information om VPN-inställningar och Intune.