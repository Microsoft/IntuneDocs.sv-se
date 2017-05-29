---
title: "Så här konfigurerar du certifikat med Intune | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Förhandsversionen av Intune Azure: Information om hur du kan använda Intune för att skapa och tilldela certifikat som hjälper dig att skydda Wi-Fi, VPN och andra anslutningar."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 05/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 81c7e04d4b4cc7599b63917e5507775b38b65ba7
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-configure-certificates-in-microsoft-intune"></a>Så här konfigurerar du certifikat i Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

När du ger användarna åtkomst till företagets resurser via VPN, Wi-Fi eller e-postprofiler, kan du autentisera dessa anslutningar med hjälp av certifikat. Certifikaten innebär att man inte längre behöver ange användarnamn och lösenord för att autentisera anslutningar.

Du kan använda Intune för att tilldela dessa certifikat till enheter som du hanterar. Intune har stöd för tilldelning och hantering av följande certifikattyper:

- Simple Certificate Enrollment Protocol (SCEP)
- PKCS#12 (eller PFX)

Alla dessa certifikattyper har sina egna förutsättningar och krav på infrastrukturen.

## <a name="general-workflow"></a>Allmänt arbetsflöde

1. Se till att du har rätt certifikatinfrastruktur på plats. Du kan använda [SCEP-certifikat](certificates-scep-configure.md) och [PKCS-certifikat](certficates-pfx-configure.md).
2. Installera ett rotcertifikat eller en mellanliggande certifikatutfärdare på alla enheter så att enheterna kan identifiera certifikatutfärdarens giltighet. Om du vill göra detta måste du skapa och tilldela en **betrodd certifikatprofil**. När du tilldelar den här profilen kommer enheter som du hanterar med Intune att begära och ta emot rotcertifikatet. Du måste skapa en separat profil för varje plattform. Profilerna för betrodda certifikat är tillgängliga för följande plattformar:
    - iOS 8.0 och senare
    - macOS 10.9 och senare
    - Android 4.0 och senare
    - Android for Work
    - Windows 8.1 och senare
    - Windows Phone 8.1 och senare
    - Windows 10 och senare
3. Skapa certifikatprofiler så att enheter begär ett certifikat som ska användas för autentisering av VPN, Wi-Fi och åtkomst av e-post. Du kan skapa och tilldela en **PKCS**- eller en **SCEP**-certifikatprofil för enheter som kör följande plattformar:
    - iOS 8.0 och senare
    - Android 4.0 och senare
    - Android for Work
    - Windows 10 (Desktop och Mobile) och senare

    Du kan bara använda en SCEP-certifikatprofil med dessa plattformar:

-     macOS 10.9 och senare
-     Windows Phone 8.1 och senare

Du måste skapa en separat profil för varje enhetsplattform. När du skapar profilen kopplar du den med den betrodda rotcertifikatprofilen som du redan skapat.

### <a name="further-considerations"></a>Ytterligare överväganden

- Du måste skapa en utfärdare av företagscertifikat om du inte redan har en.
- Om du, beroende på dina enhetsplattformar, väljer att använda SCEP-profilen (Simplified Certificate Enrollment Protocol) måste du också konfigurera en NDES-server (Network Device Enrollment Service).
- Om du planerar att använda SCEP- eller PKCS-profiler måste du hämta och konfigurera Microsoft Intune Certificate Connector.


## <a name="step-1--configure-your-certificate-infrastructure"></a>Steg 1 – Konfigurera certifikatinfrastrukturen

Se något av följande avsnitt för att få hjälp med att konfigurera infrastrukturen för varje typ av certifikatprofil:

- [Konfigurera och hantera SCEP-certifikat med Intune](certificates-scep-configure.md)
- [Konfigurera och hantera PKCS-certifikat med Intune](certficates-pfx-configure.md)


## <a name="step-2---export-your-trusted-root-ca-certificate"></a>Steg 2 – Exportera ditt betrodda rotcertifikat för certifikatutfärdaren

Exportera certifikatet för betrodda rotcertifikatutfärdare som en **CER**-fil från den utfärdande certifikatutfärdaren eller från en enhet som litar på den utfärdande certifikatutfärdaren. Exportera inte den privata nyckeln.

Det här certifikatet importeras när du konfigurerar en certifikatprofil för en betrodd certifikatutfärdare.

## <a name="step-3-create-trusted-certificate-profiles"></a>Steg 3: Skapa betrodda certifikatprofiler
Du måste skapa en betrodd certifikatprofil innan du kan skapa en SCEP- eller PKCS-certifikatprofil. Du behöver en betrodd certifikatprofil och en SCEP- eller PKCS-profil för varje enhetsplattform. Flödet för att skapa betrodda certifikat fungerar ungefär på samma sätt för varje enhetsplattform.

### <a name="to-create-a-trusted-certificate-profile"></a>Så här skapar du en betrodd certifikatprofil

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för den betrodda certifikatprofilen.
5. Från listrutan **Plattform** väljer du enhetsplattformen för detta betrodda certifikat. I dagsläget kan du välja någon av följande plattformar för certifikatsinställningar:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**
6. I listrutan **Profiltyp** väljer du **Betrott certifikat**.
7. Bläddra till certifikatet du sparade i uppgift 1 och klicka sedan på **OK**.
8. För Windows 8.1- och Windows 10-enheter, väjer du **Målarkiv** för det betrodda certifikatet från:
    - **Datorcertifikatarkiv – rot**
    - **Datorcertifikatarkiv – mellannivå**
    - **Användarcertifikatarkiv – mellannivå**
8. När du är klar väjer du **OK**, går tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.

Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).


> [!Note]
> Android-enheter visar ett meddelande om att en tredje part har installerat ett betrott certifikat.

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>Steg 4: Skapa SCEP- eller PKCS-certifikatprofiler

Se något av följande avsnitt för att få hjälp med att konfigurera och tilldela varje typ av certifikatprofil:

- [Konfigurera och hantera SCEP-certifikat med Intune](certificates-scep-configure.md)
- [Konfigurera och hantera PKCS-certifikat med Intune](certficates-pfx-configure.md)

När du har skapat en certifikatprofil för betrodd certifikatutfärdare skapar du SCEP- eller PKCS-certifikatprofiler för varje plattform som du vill använda. När du skapar en SCEP-certifikatprofil måste du ange en betrodd certifikatprofil för samma plattform. Detta länkar de två certifikatprofilerna, men du måste fortfarande tilldela varje profil separat.


## <a name="next-steps"></a>Nästa steg
Du hittar allmän information om hur du tilldelar enhetsprofilerna i [Tilldela enhetsprofilerna](device-profile-assign.md).

