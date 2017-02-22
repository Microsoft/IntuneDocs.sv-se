---
title: "Vilka enhetsprofiler finns i Microsoft Intune? | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Mer information om enhetsprofiler i Intune och hur de kan hjälpa dig att hantera och skydda enheter i företaget."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 89afae81076d563f4ebba289f8fa82eaea6ab234
ms.openlocfilehash: 0e126c067b5c212ae5bfe1cf69e01128a00b1c8e


---

# <a name="what-are-device-profiles"></a>Vad är enhetsprofiler?
<!--- This topic doesn't really answer the topic title: What are device profiles?" It needs to answer that question, then it can go on to discuss what profiles are in Intune and how to use them. Linda--->

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Använd arbetsbelastningen **Konfigurera enheter** i Microsoft Intune för att hantera inställningar och funktioner på alla enheter som du hanterar.

När du öppnar den här arbetsbelastningen ser du följande alternativ:

- **Översikt** – På den här sidan kan du se status och rapporter som hjälper dig övervaka enhetskonfigurationer som du har tilldelat till användare och enheter.
- **Hantera profiler** – Det här avsnittet används för att skapa konfigurationsprofiler för enheten. Nedan finns en lista med alla profiltyper som du kan skapa.
- **Konfigurera certifikatutfärdare** – Arbetsflödet vägleder dig genom de steg som krävs för att konfigurera certifikat. Du måste göra detta om du vill använda Intunes certifikatprofiler.

## <a name="getting-started"></a>Komma igång

Arbetsflödet för att skapa enhetsprofiler är likadant för alla profiler. Läs [Så här skapar du enhetskonfigurationsprofiler i Microsoft Intune](/intune-azure/configure-devices/how-to-create-device-profiles) för information om hur du skapar profiler. Läs vidare för specifik information om att skapa inställningar för varje profiltyp.

Du kan hantera följande funktioner på dina enheter:

## <a name="device-restrictions"></a>Enhetsbegränsningar
Med enhetsbegränsningar kan du kontrollera en mängd olika inställningar och funktioner som du hanterar i flera kategorier, bland annat säkerhet, webbläsare, maskinvara och datadelning. Du kan till exempel skapa en profil för enhetsbegränsningar som förhindrar användare av iOS-enheter från att komma åt kameran på enheten.
Mer information finns i [Så här konfigurerar du inställningar för enhetsbegränsningar](how-to-configure-device-restrictions.md) Stöder: Android, iOS, macOS, Windows 10 och Windows 10 Team.

## <a name="email"></a>E-post
Med e-postprofiler kan du skapa, distribuera och övervaka e-postinställningarna för Exchange ActiveSync på enheterna som du hanterar. Genom att distribuera inställningarna uppnår du konsekvens, minskar supportsamtalen och ger slutanvändarna åtkomst till företagets e-post på sina personliga enheter utan de behöver konfigurera något själva.
Mer information finns i [Så här konfigurerar du e-postinställningar](how-to-configure-email-settings.md) Stöder: Android, iOS, Windows 8.1 och Windows 10.

## <a name="wi-fi"></a>Wi-Fi
Använd trådlösa profiler för att distribuera trådlösa nätverksinställningar till användare och enheter i din organisation. När du distribuerar en Wi-Fi-profil får användarna åtkomst till ditt företags trådlösa nätverk utan att de behöver göra några inställningar själva.
Mer information finns i [Så här konfigurerar du trådlösa inställningar](how-to-configure-wi-fi-settings.md) Stöder: Android, iOS, macOS och Windows 8.1 (endast import).

## <a name="vpn"></a>VPN
Virtuella privata nätverk (VPN, Virtual Private Networks) ger användarna säker fjärråtkomst till företagets nätverk. Enheterna använder en profil för VPN-anslutning för att initiera en anslutning till VPN-servern. Använd VPN-profiler för att distribuera VPN-inställningar till användare och enheter i din organisation, så att de enkelt och säkert kan ansluta till nätverket.
Mer information finns i [Så här konfigurerar du VPN-inställningar](how-to-configure-vpn-settings.md).
Stöder: Android, iOS, macOS, Windows Phone 8.1, Windows 8.1 och Windows 10.

## <a name="certificates"></a>Certifikat
Med den här profiltypen kan du konfigurera betrodda, SCEP- och PKCS-certifikat som kan tilldelas till enheter och användas för att autentisera trådlösa profiler, VPN- och e-postprofiler.
Mer information finns i [Så här konfigurerar du certifikat](how-to-configure-certificates.md) Stöder: Android, iOS, Windows Phone 8.1, Windows 8.1 och Windows 10.

## <a name="education"></a>Utbildning
Hjälper dig att ange rätt certifikat när iOS-enheter används i en utbildningsmiljö.
Mer information finns i [Så här konfigurerar du inställningar för Intune-utbildning på iOS-enheter](education-settings-for-ios.md) Stöder: endast iOS.

## <a name="edition-upgrade"></a>Versionsuppgradering
Med den här profiltypen kan du automatiskt uppgradera enheter som kör vissa versioner av Windows 10 till en nyare version. För mer information, se [Så här konfigurerar du Windows 10-uppgraderingar](how-to-configure-windows-10-edition-upgrade.md) Stöder: endast Windows 10.

## <a name="windows-information-protection"></a>Windows informationsskydd
Windows informationsskydd bidrar till att skydda mot dataläckage utan att störa medarbetarnas användning. Informationsskyddet skyddar även företagsappar och företagsdata mot oavsiktliga dataläckage i företagsägda enheter och personliga enheter som medarbetarna tar med sig till jobbet utan att det behövs några ändringar i miljön eller andra appar.
Mer information finns i [Så här konfigurerar du Windows informationsskydd](how-to-configure-windows-information-protection.md) Stöder: endast Windows 10.

## <a name="custom"></a>Anpassad
Med anpassade inställningar kan du tilldela enhetsinställningar som inte är inbyggda i Intune. Du kan till exempel ange OMA-URI-värden som konfigurerar Android-enheter. På iOS-enheter kan du importera en konfigurationsfil som du har skapat i Apple Configurator.
Mer information finns i [Så här konfigurerar du anpassade inställningar](how-to-configure-custom-settings.md) Stöder: Android, iOS, macOS och Windows Phone 8.1.



<!--HONumber=Feb17_HO1-->


