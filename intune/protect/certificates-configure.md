---
title: Skapa certifikatprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Lär dig hur du använder SCEP-certifikat (Simple Certificate Enrollment Protocol) eller PKCS-certifikat (Public Key Cryptography Standards) och certifikatprofiler med Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63fa9f461fc9884d8c21e40cb4b5e3831f3b4b03
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576522"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Använda certifikat för autentisering i Microsoft Intune

Använd certifikat med Intune för att autentisera dina användare till program och företagsresurser via VPN, Wi-Fi eller e-postprofiler. När du använder certifikat för att autentisera dessa anslutningar behöver dina slutanvändare inte ange användarnamn och lösenord, vilket kan göra deras åtkomst sömlös. Certifikat används även för signering och kryptering av e-post med hjälp av S/MIME.

## <a name="intune-supported-certificates-and-usage"></a>Intune-kompatibla certifikat och användning

| Typ              | Autentisering | S/MIME-signering | S/MIME-kryptering  |
|--|--|--|--|
| PKCS-importerat certifikat (Public Key Cryptography Standards) |  | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png)|
| PKCS#12 (eller PFX)    | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) |  |
| Simple Certificate Enrollment Protocol (SCEP)  | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | |

Du distribuerar de här certifikaten genom att skapa och tilldela certifikatprofiler till enheter.

Varje enskild certifikatprofil som du skapar stöder en enda plattform. Om du till exempel använder PKCS-certifikat skapar du en PKCS-certifikatprofil för Android och en separat PKCS-certifikatfil för iOS/iPadOS. Om du även använder SCEP-certifikat för dessa två plattformar skapar du en SCEP-certifikatprofil för Android och en annan för iOS/iPadOS.

### <a name="general-considerations-when-you-use-a-microsoft-certification-authority"></a>Allmänna överväganden när du använder en Microsoft-certifikatutfärdare

När du använder en Microsoft-certifikatutfärdare:

- Om du vill använda SCEP-certifikatprofiler måste du [konfigurera en server för registreringstjänst för nätverksenheter (NDES)](certificates-scep-configure.md#set-up-ndes) för användning med Intune.
- Om du vill använda följande typer av certifikatprofiler måste du [installera Microsoft Intune Certificate Connector](certificates-scep-configure.md#install-the-intune-certificate-connector):
  - SCEP-certifieringsprofil
  - PKCS-certifikatprofil

- Så här använder du PKCS-importerade certifikat:
  - [Installera PFX-certifikatanslutningsprogrammet för Microsoft Intune](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
  - Exportera certifikat från certifikatutfärdaren och importera dem sedan till Microsoft Intune. Se [PFXImport PowerShell-projektet](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

- Distribuera certifikat med hjälp av följande metoder:
  - [Betrodda certifikatprofiler](certificates-configure.md#create-trusted-certificate-profiles) för att distribuera betrodda rotcertifikat för certifikatutfärdare från din rot- eller mellanliggande (utfärdande) certifikatutfärdare till enheter
  - SCEP-certifikatprofiler
  - PKCS-certifikatprofiler
  - PKCS-importerade certifikatprofiler

### <a name="general-considerations-when-you-use-a-third-party-certification-authority"></a>Allmänna överväganden när du använder en certifikatutfärdare från tredje part

När du använder en certifikatutfärdare från tredje part (inte Microsoft):

- Så här använder du SCEP-certifikatprofiler:
  - Konfigurera integration med en certifikatutfärdare från tredje part från [en av våra partners som stöds](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners). Konfigureringen innefattar att följa instruktioner från certifikatutfärdaren från tredje part för att slutföra integreringen av deras certifikatutfärdare med Intune.
  - [Skapa ett program i Azure Active Directory](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration) som delegerar rättigheter att utföra SCEP-certifikatutmaningsverifiering till Intune.

- PKCS-importerade certifikat kräver att du [installerar PFX-certifikatets anslutningsprogram för Microsoft Intune](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).

- Distribuera certifikat med hjälp av följande metoder:
  - [Betrodda certifikatprofiler](certificates-configure.md#create-trusted-certificate-profiles) för att distribuera betrodda rotcertifikat för certifikatutfärdare från din rot- eller mellanliggande (utfärdande) certifikatutfärdare till enheter
  - SCEP-certifikatprofiler
  - PKCS-certifikatprofiler *(stöds endast med [DigiCert PKI-plattformen](certificates-digicert-configure.md))*
  - PKCS-importerade certifikatprofiler

## <a name="supported-platforms-and-certificate-profiles"></a>Plattformar och certifikatprofiler som stöds

| Plattform              | Betrodd certifikatprofil | PKCS-certifikatprofil | SCEP-certifikatprofil | PKCS-importerad certifikatprofil  |
|--|--|--|--|---|
| Android-enhetsadministratör | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png)|  ![Stöds](./media/certificates-configure/green-check.png) |
| Android enterprise <br> – Fullständigt hanterad (enhetsägare)   | ![Stöds](./media/certificates-configure/green-check.png) |   | ![Stöds](./media/certificates-configure/green-check.png) |   |
| Android enterprise <br> – Dedikerad (enhetsägare)   | ![Stöds](./media/certificates-configure/green-check.png)  |   | ![Stöds](./media/certificates-configure/green-check.png)  |   |
| Android enterprise <br> – Arbetsprofil    | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) |
| iOS/iPadOS                   | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) |
| macOS                 | ![Stöds](./media/certificates-configure/green-check.png) |  ![Stöds](./media/certificates-configure/green-check.png) |![Stöds](./media/certificates-configure/green-check.png)|![Stöds](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![Stöds](./media/certificates-configure/green-check.png)  |  | ![Stöds](./media/certificates-configure/green-check.png)| ![Stöds](./media/certificates-configure/green-check.png) |
| Windows 8.1 och senare |![Stöds](./media/certificates-configure/green-check.png)  |  |![Stöds](./media/certificates-configure/green-check.png) |   |
| Windows 10 och senare  | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>Exportera det betrodda rotcertifikatutfärdarcertifikatet

För att enheter ska kunna använda PKCS, SCEP- och PKCS-importerade certifikat måste de lita på din rotcertifikatutfärdare. Du skapar förtroende genom att exportera det betrodda rotcertifikatutfärdarcertifikatet samt alla mellanliggande eller utfärdande certifikatutfärdarcertifikat som ett offentligt certifikat (.cer). Du kan hämta dessa certifikat från den utfärdande certifikatutfärdaren eller från valfri enhet som litar på din utfärdande certifikatutfärdare.

Information om hur du exporterar certifikatet finns i dokumentationen för certifikatutfärdaren. Du behöver exportera det offentliga certifikatet som en .cer-fil.  Exportera inte den privata nyckeln som en .pfx-fil.

Du använder den här .cer-filen när du [skapar betrodda certifikatprofiler](#create-trusted-certificate-profiles) för att distribuera det certifikatet till dina enheter.

## <a name="create-trusted-certificate-profiles"></a>Skapa profiler för betrodda certifikat

Skapa en betrodd certifikatprofil innan du kan skapa en SCEP-, PKCS- eller PKCS-importerad certifikatprofil. Genom att distribuera en betrodd certifikatprofil ser du till att varje enhet känner igen giltigheten hos din certifikatutfärdare. SCEP-certifikatprofiler refererar direkt till en betrodd certifikatprofil. PKCS-certifikatprofiler refererar inte direkt till den betrodda certifikatprofilen, men de refererar direkt till den server som är värd för din certifikatutfärdare. PKCS-importerade certifikatprofiler refererar inte direkt till den betrodda certifikatprofilen men kan använda den på enheten. Distribution av en betrodd certifikatprofil till enheter säkerställer att det här förtroendet upprättas. När en enhet inte litar på rotcertifikatutfärdaren misslyckas SCEP- eller PKCS-certifikatprofilprincipen.

Skapa en separat betrodd certifikatprofil för varje enhetsplattform som du vill stödja, precis som du gör för SCEP-, PKCS- och PKCS-importerade certifikatprofiler.

### <a name="to-create-a-trusted-certificate-profile"></a>Så här skapar du en betrodd certifikatprofil

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.

   ![Navigera till Intune och skapa en ny profil för ett betrott certifikat](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. Ange följande egenskaper:

   - **Namnet** på profilen
   - Om du vill kan du ange en **beskrivning**
   - **Plattform** att distribuera profilen till
   - Ange **profiltypen** som **betrott certifikat**

4. Välj **Inställningar** och bläddra till den betrodda .CER-filen för rotcertifikatutfärdarens certifikat som du exporterade för användning med den här certifikatprofilen och välj sedan **OK**.

5. För Windows 8.1- och Windows 10-enheter, väjer du **Målarkiv** för det betrodda certifikatet från:

   - **Datorcertifikatarkiv – rot**
   - **Datorcertifikatarkiv – mellannivå**
   - **Användarcertifikatarkiv – mellannivå**

6. När du är klar väljer du **OK**, går tillbaka till fönstret **Skapa profil** och väljer **Skapa**.

Profilen visas i listan med profiler i fönstret *Enheter – Konfigurationsprofiler*, med profiltypen **Betrott certifikat**. Se till att tilldela den här profilen till enheter som ska använda SCEP- eller PKCS-certifikat. Om du vill tilldela profilen till grupper kan du läsa [Tilldela enhetsprofiler](../configuration/device-profile-assign.md).

> [!NOTE]
> Android-enheter visar kanske ett meddelande om att en tredje part har installerat ett betrott certifikat.

## <a name="additional-resources"></a>Ytterligare resurser

- [Tilldela enhetsprofiler](../configuration/device-profile-assign.md)  
- [Använd S/MIME att signera och kryptera e-postmeddelanden](certificates-s-mime-encryption-sign.md)  
- [Använd certifikatutfärdare från tredje part](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>Nästa steg

Skapa SCEP-, PKCS- eller PKCS-utfärdade certifikatprofiler för varje plattform som du vill använda. Fortsätt med följande artiklar:

- [Konfigurera infrastrukturen för att stödja SCEP-certifikat med Intune](certificates-scep-configure.md)  
- [Konfigurera och hantera PKCS-certifikat med Intune](certficates-pfx-configure.md)  
- [Skapa en PKCS-importerad certifikatprofil](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)
