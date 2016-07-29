---
title: "Certifikatprofiler för åtkomst till resurser | Microsoft Intune"
description: "Skydda åtkomsten via VPN, Wi-Fi och e-post med ett certifikat som installeras på varje användarenhet."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 98c32f924b60734d9a592ebdd7e00429dc32af26


---

# Skydda resursåtkomst med certifikatprofiler i Microsoft Intune
När du aktiverar åtkomst till företagets resurser via VPN, Wi-Fi eller e-postprofiler har du möjlighet att skydda åtkomsten med ett certifikat som installeras på varje användarenhet. Så här fungerar det:

1. Kontrollera att du har rätt certifikatinfrastruktur på plats. Mer information finns i [Konfigurera certifikatinfrastruktur för SCEP](configure-certificate-infrastructure-for-scep.md) eller [Konfigurera certifikatinfrastruktur för PFX](configure-certificate-infrastructure-for-pfx.md).

2. Installera ett rotcertifikat (eller mellanliggande certifikatutfärdare) på alla enheter så att enheterna kan bekräfta certifikatutfärdarens giltighet. Det gör du genom att skapa och distribuera en **betrodd certifikatprofil**. När du distribuerar den här profilen kommer enheter som du hanterar med Intune att begära och ta emot rotcertifikatet. Du måste skapa en separat profil för varje plattform. **Profilen för betrodda certifikat** är tillgänglig för följande plattformar:
 -  iOS 7.1 och senare
 -  Mac OS X 10.9 och senare
 -  Android 4.0 och senare
 -  Windows 8.1 och senare
 -  Windows Phone 8.1 och senare

3. Tvinga alla enheter att begära ett certifikat som ska användas för autentisering av e-post, VPN och Wi-Fi-åtkomst. Mer information finns i [Konfigurera Intune-certifikatprofiler](configure-intune-certificate-profiles.md). Du kan skapa och distribuera en **PKCS #12-certifikatprofil (.PFX)** eller en **SCEP-certifikatprofil** för enheter på följande plattformar:

-  Android 4.0 och senare
-  iOS 7.1 och senare
-  Windows 10 (Desktop och Mobile) och senare

Använd **SCEP-certifikatprofilen** för:
-   Mac OS X 10.9 och senare
-   Windows Phone 8.1 och senare

Du måste skapa en separat profil för varje plattform. När du skapar profilen kopplar du den med den **betrodda rotcertifikatprofilen** som du redan skapat.

> [!NOTE]           
> -    Du måste skapa en utfärdare av företagscertifikat om du inte redan har en.
>- Om du, beroende på dina enhetsplattformar, väljer att använda SCEP-profilen (Simplified Certificate Enrollment Protocol) måste du också konfigurera en NDES-server (Network Device Enrollment Service).
>-  Om du planerar att använda SCEP- eller PFX-profiler måste du hämta och konfigurera Microsoft Intune Certificate Connector.
> Konfigurationen av alla dessa beskrivs i [Konfigurera certifikatinfrastruktur för SCEP](configure-certificate-infrastructure-for-scep.md) och [Konfigurera certifikatinfrastruktur för PFX](configure-certificate-infrastructure-for-pfx.md).

### Nästa steg
- [Konfigurera certifikatinfrastruktur för SCEP](configure-certificate-infrastructure-for-scep.md)
- [Konfigurera certifikatinfrastruktur för PFX](configure-certificate-infrastructure-for-pfx.md)
- [Konfigurera certifikatprofiler för Intune](configure-intune-certificate-profiles.md)



<!--HONumber=Jul16_HO4-->


