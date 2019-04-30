---
title: Skapa certifikatprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa en certifikatprofil för enheterna genom att konfigurera SCEP- eller PKCS-miljön, exportera det offentliga certifikatet, skapa profilen i Azure Portal och sedan tilldela SCEP eller PKCS till certifikatprofilerna i Microsoft Intune i Azure Portal
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 569ddd9be0c59cf9a4bd7ba1f8b114183ce46d7d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508290"
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>Konfigurera en certifikatprofil för enheterna i Microsoft Intune

Du ger användare åtkomst till företagsresurser via VPN, Wi-Fi eller e-postprofiler. Du kan använda certifikat för att autentisera dessa anslutningar. När du använder certifikat behöver dina slutanvändare inte ange användarnamn och lösenord för att autentisera.

Du kan använda Intune för att tilldela dessa certifikat till enheter som du hanterar. Intune har stöd för tilldelning och hantering av följande certifikattyper:

- Simple Certificate Enrollment Protocol (SCEP)
- PKCS#12 (eller PFX)

Alla dessa certifikattyper har sina egna förutsättningar och krav på infrastrukturen.


## <a name="overview"></a>Översikt

1. Se till att rätt certifikatinfrastruktur har konfigurerats. Du kan använda [SCEP-certifikat](certificates-scep-configure.md) och [PKCS-certifikat](certficates-pfx-configure.md).

2. Installera ett rotcertifikat eller en mellanliggande certifikatutfärdare på alla enheter så att enheterna kan identifiera certifikatutfärdarens giltighet. För att installera certifikatet skapar och tilldelar du en **profil för betrott certifikat** till varje enhet. När du tilldelar den här profilen begär och tar Intune-hanterade enheter emot rotcertifikatet. Du måste skapa en separat profil för varje plattform. Profilerna för betrodda certifikat är tillgängliga för följande plattformar:

    - iOS 8.0 och senare
    - macOS 10.11 och senare
    - Android 4.0 och senare
    - Android enterprise  
    - Windows 8.1 och senare
    - Windows Phone 8.1 och senare
    - Windows 10 och senare

    > [!NOTE]  
    > Certifikatprofiler stöds inte på enheter som kör *Android Enterprise för dedikerade enheter*.

3. Skapa certifikatprofiler så att enheter begär ett certifikat som ska användas för autentisering av VPN, Wi-Fi och åtkomst av e-post. Följande profiltyper av är tillgängliga för olika plattformar:  

   | Plattform     |PKCS-certifikat|SCEP-certifikat| PKCS-importerat certifikat | 
   |--------------|----------------|----------------|-------------------|
   | Android                | Ja    | Ja    | Ja    |
   | Android enterprise     | Ja    | Ja    | Ja    |
   | iOS                    | Ja    | Ja    | Ja    |
   | macOS                  |        | Ja    | Ja    |
   | Windows Phone 8.1      |        | Ja    | Ja    |
   | Windows 8.1 och senare  |        | Ja    |        |
   | Windows 10 och senare   | Ja    | Ja    | Ja    |

   Se till att du skapar en separat profil för varje enhetsplattform. När du skapar profilen kopplar du den med den betrodda rotcertifikatprofilen som du redan skapat.

### <a name="further-considerations"></a>Ytterligare överväganden

- Du måste skapa en utfärdare av företagscertifikat om du inte redan har en
- Om du använder SCEP-profiler konfigurerar du en server för registreringstjänsten för nätverksenheter (NDES)
- Oavsett om du tänker använda SCEP- eller PKCS-profiler ska du hämta och konfigurera Microsoft Intune Certificate Connector


## <a name="step-1-configure-your-certificate-infrastructure"></a>Steg 1: Konfigurera certifikatinfrastrukturen

Se någon av följande artiklar för att få hjälp med att konfigurera infrastrukturen för varje typ av certifikatprofil:

- [Konfigurera och hantera SCEP-certifikat med Intune](certificates-scep-configure.md)
- [Konfigurera och hantera PKCS-certifikat med Intune](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>Steg 2: Exportera ditt betrodda rotcertifikat för certifikatutfärdaren

Exportera certifikatet för betrodda rotcertifikatutfärdare som ett offentligt certifikat (CER-fil) från den utfärdande certifikatutfärdaren eller från en enhet som litar på den utfärdande certifikatutfärdaren. Exportera inte den privata nyckeln (.pfx).

Det här certifikatet importeras när du konfigurerar en certifikatprofil för en betrodd certifikatutfärdare.

## <a name="step-3-create-trusted-certificate-profiles"></a>Steg 3: Skapa profiler för betrodda certifikat
Skapa en betrodd certifikatprofil innan du skapar en SCEP- eller PKCS-certifikatprofil. En betrodd certifikatprofil och en SCEP- eller PKCS-profil krävs för varje enhetsplattform. Stegen för att skapa betrodda certifikat fungerar ungefär på samma sätt för varje enhetsplattform.

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetskonfiguration** > **Hantera** > **Profiler** > **Skapa profil**.
4. Ange ett **namn** och en **beskrivning** för den betrodda certifikatprofilen.
5. Från listrutan **Plattform** väljer du enhetsplattformen för detta betrodda certifikat. Alternativen är:

    - **Android**
    - **Android enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**

6. Från listrutan **Profil** väljer du **Betrodda certifikat**.
7. Bläddra till det certifikat som du sparade i [Steg 2: Exportera ditt betrodda rotcertifikat för certifikatutfärdaren](#step-2-export-your-trusted-root-ca-certificate) och välj sedan **OK**.
8. För Windows 8.1- och Windows 10-enheter, väjer du **Målarkiv** för det betrodda certifikatet från:

    - **Datorcertifikatarkiv – rot**
    - **Datorcertifikatarkiv – mellannivå**
    - **Användarcertifikatarkiv – mellannivå**

9. När du är klar väljer du **OK**, går tillbaka till fönstret **Skapa profil** och väljer **Skapa**.

Profilen skapas och visas i listan. Om du vill tilldela profilen till grupper kan du läsa [Tilldela enhetsprofiler](device-profile-assign.md).

   >[!NOTE]
   > Android-enheter kan visa ett meddelande om att en tredje part har installerat ett betrott certifikat.

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>Steg 4: Skapa SCEP- eller PKCS-certifikatprofiler

Se någon av följande artiklar för att få hjälp med att konfigurera och tilldela varje typ av certifikatprofil:

- [Konfigurera och hantera SCEP-certifikat med Intune](certificates-scep-configure.md)
- [Konfigurera och hantera PKCS-certifikat med Intune](certficates-pfx-configure.md)

När du har skapat en certifikatprofil för betrodd certifikatutfärdare skapar du SCEP- eller PKCS-certifikatprofiler för varje plattform som du vill använda. När du skapar en SCEP-certifikatprofil anger du en betrodd certifikatprofil för samma plattform. Detta steg länkar de två certifikatprofilerna, men du måste fortfarande tilldela varje profil separat.

## <a name="next-steps"></a>Nästa steg
[Tilldela enhetsprofiler](device-profile-assign.md)  
[Använd S/MIME att signera och kryptera e-postmeddelanden](certificates-s-mime-encryption-sign.md)  
[Använd tredje parts certifikatutfärdare](certificate-authority-add-scep-overview.md)
