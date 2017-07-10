---
title: "Certifikatprofiler för åtkomst till resurser"
description: "Skydda åtkomsten via VPN, Wi-Fi och e-post med ett certifikat som installeras på varje användarenhet."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5570c13b9ca1782b12ad7ca718d18c98bda7bbfa
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="secure-resource-access-with-certificate-profiles-in-microsoft-intune"></a>Skydda resursåtkomst med certifikatprofiler i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

När du ger användare åtkomst till företagets resurser via VPN, Wi-Fi eller e-postprofiler kan du skydda åtkomsten genom att använda ett certifikat som installeras på varje användarenhet. Så här fungerar det:

1. Kontrollera att du har rätt certifikatinfrastruktur på plats. Mer information finns i [Konfigurera certifikatinfrastruktur för SCEP](configure-certificate-infrastructure-for-scep.md) och [Konfigurera certifikatinfrastruktur för PFX](configure-certificate-infrastructure-for-pfx.md).

2. Installera ett rotcertifikat eller en mellanliggande certifikatutfärdare på alla enheter så att enheterna kan identifiera certifikatutfärdarens giltighet. Om du vill göra detta måste du skapa och distribuera en **betrodd certifikatprofil**. När du distribuerar den här profilen kommer enheter som du hanterar med Intune att begära och ta emot rotcertifikatet. Du måste skapa en separat profil för varje plattform. **Profilen för betrodda certifikat** är tillgänglig för följande plattformar:
 -  iOS 8.0 och senare
 -  Mac OS X 10.9 och senare
 -  Android 4.0 och senare
 -  Android for Work
 -  Windows 8.1 och senare
 -  Windows Phone 8.1 och senare

3. Skapa certifikatprofiler så att enheterna begär att ett certifikat ska användas för autentisering av VPN-, Wi-Fi- och e-poståtkomst. Mer information finns i [Konfigurera Intune-certifikatprofiler](configure-intune-certificate-profiles.md). Du kan skapa och distribuera en **PKCS #12-certifikatprofil (.PFX)** *eller* en **SCEP-certifikatprofil** för enheter som kör följande plattformar:

  -  iOS 8.0 och senare
  -  Android 4.0 och senare
  -  Android for Work
  -  Windows 10 (Desktop och Mobile) och senare

  Använd en **SCEP profil** för enheter som kör dessa plattformar:
    -   Mac OS X 10.9 och senare
    -   Windows Phone 8.1

Du måste skapa en separat profil för varje plattform. När du skapar profilen kopplar du den med den **betrodda rotcertifikatprofilen** som du redan skapat.

> [!NOTE]           
> - Du måste skapa en utfärdare av företagscertifikat om du inte redan har en.
>- Om du, beroende på dina enhetsplattformar, väljer att använda SCEP-profilen (Simplified Certificate Enrollment Protocol) måste du också konfigurera en NDES-server (Network Device Enrollment Service).
>-  Om du planerar att använda SCEP- eller PFX-profiler måste du hämta och konfigurera Microsoft Intune Certificate Connector.
>-  Lär dig hur du konfigurerar alla dess nödvändiga tjänster i [Konfigurera certifikatinfrastruktur för SCEP](configure-certificate-infrastructure-for-scep.md) och [Konfigurera certifikatinfrastruktur för PFX](configure-certificate-infrastructure-for-pfx.md).

### <a name="next-steps"></a>Nästa steg
- [Konfigurera certifikatinfrastruktur för SCEP](configure-certificate-infrastructure-for-scep.md)
- [Konfigurera certifikatinfrastruktur för PFX](configure-certificate-infrastructure-for-pfx.md)
- [Konfigurera certifikatprofiler för Intune](configure-intune-certificate-profiles.md)
