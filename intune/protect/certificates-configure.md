---
title: Skapa certifikatprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa en certifikatprofil för enheterna genom att konfigurera SCEP- eller PKCS-miljön, exportera det offentliga certifikatet, skapa profilen i Azure Portal och sedan tilldela SCEP eller PKCS till certifikatprofilerna i Microsoft Intune i Azure Portal
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 345d039fede2a77ba0485944cb601683bdcebfda
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999298"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Använda certifikat för autentisering i Microsoft Intune  

Använd certifikat med Intune för att autentisera dina användare till program och företagsresurser via VPN, Wi-Fi eller e-postprofiler. När du använder certifikat för att autentisera dessa anslutningar behöver dina slutanvändare inte ange användarnamn och lösenord, vilket gör att deras åtkomst mer sömlös. Certifikat används även för signering och kryptering av e-post med hjälp av S/MIME.

## <a name="intune-supported-certificates-and-usage"></a>Intune-kompatibla certifikat och användning
| Typ              | Autentisering | S/MIME-signering | S/MIME-kryptering  |
|--|--|--|--|
| PKCS-importerat certifikat |  | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png)|
| PKCS#12 (eller PFX)    | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) |  |
| Simple Certificate Enrollment Protocol (SCEP)  | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | |

Du distribuerar de här certifikaten genom att skapa och tilldela certifikatprofiler till enheter.  

Varje enskild certifikatprofil som du skapar stöder en enda plattform. Om du till exempel använder PKCS-certifikat skapar du en PKCS-certifikatprofil för Android och en separat PKCS-certifikatfil för iOS. Om du även använder SCEP-certifikat för dessa två plattformar skapar du en SCEP-certifikatprofil för Android och en annan för iOS.  

**Generella saker att tänka på**:  
- Om du inte har en företagscertifikatutfärdare (CA) måste du skapa en eller använda [någon av våra partner som stöds](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners).
- Om du använder SCEP-certifikatprofiler med hjälp av Microsoft Active Directory Certificate Services konfigurerar du en NDES-server (registreringstjänst för nätverksenheter).
- Om du använder SCEP med en av våra certifikatutfärdarpartner behöver du [integrera den med Intune](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration).
- Både SCEP- och PKCS-certifikatprofiler kräver att du laddar ned, installerar och konfigurerar Microsoft Intune Certificate Connector. 
- PCKS-importerade certifikat kräver att du laddar ned, installerar och konfigurerar PFX-certifikatets anslutningsprogram för Microsoft Intune.
- PKCS-importerade certifikat kräver att du exporterar certifikat från din certifikatutfärdare och importerar dem till Microsoft Intune. Se [PFXImport PowerShell-projektet](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)
- För att en enhet ska kunna använda SCEP-, PCKS- eller PKCS-importerade certifikatprofiler måste enheten lita på rotcertifikatutfärdaren. Du använder en *betrodd certifikatutfärdare* för att distribuera ditt betrodda rotcertifikatutfärdarcertifikat till enheter.  

## <a name="supported-platforms-and-certificate-profiles"></a>Plattformar och certifikatprofiler som stöds  
| Plattform              | Betrodd certifikatprofil | PKCS-certifikatprofil | SCEP-certifikatprofil | PKCS-importerad certifikatprofil  |
|--|--|--|--|---|
| Android-enhetsadministratör | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png)|  ![Stöds](./media/certificates-configure/green-check.png) |
| Android enterprise <br> – Enhetens ägare   | ![Stöds](./media/certificates-configure/green-check.png) |   |  |   |
| Android enterprise <br> – Arbetsprofil    | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) |
| iOS                   | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) |
| macOS                 | ![Stöds](./media/certificates-configure/green-check.png) |   |![Stöds](./media/certificates-configure/green-check.png)|![Stöds](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![Stöds](./media/certificates-configure/green-check.png)  |  | ![Stöds](./media/certificates-configure/green-check.png)| ![Stöds](./media/certificates-configure/green-check.png) |
| Windows 8.1 och senare |![Stöds](./media/certificates-configure/green-check.png)  |  |![Stöds](./media/certificates-configure/green-check.png) |   |
| Windows 10 och senare  | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) | ![Stöds](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>Exportera det betrodda rotcertifikatutfärdarcertifikatet  
För att enheter ska kunna använda PKCS, SCEP- och PKCS-importerade certifikat måste de lita på din rotcertifikatutfärdare. Du skapar detta förtroende genom att exportera det betrodda rotcertifikatutfärdarcertifikatet (CA), samt alla mellanliggande eller utfärdande certifikatutfärdarcertifikat som ett offentligt certifikat. Du kan hämta dessa certifikat från den utfärdande certifikatutfärdaren eller från valfri enhet som litar på din utfärdande certifikatutfärdare.  

Information om hur du exporterar certifikatet finns i dokumentationen för certifikatutfärdaren. Du behöver exportera det offentliga certifikatet som en .cer-fil.  Exportera inte den privata nyckeln som en .pfx-fil.  

Du använder den här .cer-filen när du [skapar betrodda certifikatprofiler](#create-trusted-certificate-profiles) för att distribuera det certifikatet till dina enheter.  

## <a name="create-trusted-certificate-profiles"></a>Skapa profiler för betrodda certifikat  
Skapa en betrodd certifikatprofil innan du kan skapa en SCEP-, PKCS- eller PKCS-importerad certifikatprofil. Genom att distribuera en betrodd certifikatprofil ser du till att varje enhet känner igen giltigheten hos din certifikatutfärdare. SCEP-certifikatprofiler refererar direkt till en betrodd certifikatprofil. PKCS-certifikatprofiler refererar inte direkt till den betrodda certifikatprofilen, men de refererar direkt till den server som är värd för din certifikatutfärdare. PKCS-importerade certifikatprofiler refererar inte direkt till den betrodda certifikatprofilen men kan använda den på enheten. Distribution av en betrodd certifikatprofil till enheter säkerställer att det här förtroendet upprättas. När en enhet inte litar på rotcertifikatutfärdaren misslyckas SCEP- eller PKCS-certifikatprofilprincipen.  

Skapa en separat betrodd certifikatprofil för varje enhetsplattform som du vill stödja, precis som du gör för SCEP-, PCKS- och PKCS-importerade certifikatprofiler.  


### <a name="to-create-a-trusted-certificate-profile"></a>Så här skapar du en betrodd certifikatprofil  

1. Logga in på [Intune-portalen](https://aka.ms/intuneportal).  
2. Välj **Enhetskonfiguration** > **Hantera** > **Profiler** > **Skapa profil**.  
3. Ange ett **namn och en beskrivning** för den betrodda certifikatprofilen.  
4. Från listrutan **Plattform** väljer du enhetsplattformen för detta betrodda certifikat.  
5. Från listrutan **Profil** väljer du **Betrodda certifikat**.  
6. Bläddra till det betrodda rotcertifikatutfärdarcertifikatets .cer-fil som du exporterade för användning med den här certifikatprofilen och välj sedan **OK**.  
7. För Windows 8.1- och Windows 10-enheter, väjer du **Målarkiv** för det betrodda certifikatet från:  
   - **Datorcertifikatarkiv – rot**
   - **Datorcertifikatarkiv – mellannivå**
   - **Användarcertifikatarkiv – mellannivå**
8. När du är klar väljer du **OK**, går tillbaka till fönstret **Skapa profil** och väljer **Skapa**.
Profilen visas i listan över profiler i visningsfönstret *Enhetskonfiguration – Profiler*, med profiltypen **Betrott certifikat**.  Se till att tilldela den här profilen till enheter som ska använda SCEP- eller PCKS-certifikat. Om du vill tilldela profilen till grupper kan du läsa [Tilldela enhetsprofiler](../configuration/device-profile-assign.md).

> [!NOTE]  
> Android-enheter visar kanske ett meddelande om att en tredje part har installerat ett betrott certifikat.  

## <a name="additional-resources"></a>Ytterligare resurser  
- [Tilldela enhetsprofiler](../configuration/device-profile-assign.md)  
- [Använd S/MIME att signera och kryptera e-postmeddelanden](certificates-s-mime-encryption-sign.md)  
- [Använd certifikatutfärdare från tredje part](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>Nästa steg  
När du har skapat och tilldelat betrodda certifikatprofiler skapar du SCEP-, PKCS- eller PKCS-utfärdade certifikatprofiler för varje plattform som du vill använda. Fortsätt med följande artiklar:  
- [Konfigurera infrastrukturen för att stödja SCEP-certifikat med Intune](certificates-scep-configure.md)  
- [Konfigurera och hantera PKCS-certifikat med Intune](certficates-pfx-configure.md)  
- [Skapa en PKCS-importerad certifikatprofil](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)  

