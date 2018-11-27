---
title: S/MIME-signering och kryptering för e-post – Azure | Microsoft Docs
description: Använd eller aktivera S/MIME för att signera och kryptera e-postmeddelanden i Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: eaa85870b289bb3b65ce997d8610324f43d69452
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185652"
---
# <a name="smime-email-signing-and-encryption-in-intune"></a>S/MIME-signering och kryptering för e-post i Intune

> [!IMPORTANT]
> Vi har gjort några förbättringar av S/MIME-funktionen som beskrivs i den här artikeln. S/MIME-funktionen är därför tillfälligt borttagen i Intune. När funktionen lanseras tar vi bort det här meddelandet.

S/MIME ger en extra nivå av säkerhet till dina e-postmeddelanden med hjälp av kryptering och dekryptering. Microsoft Intune kan använda S/MIME för att signera och kryptera e-postmeddelande till mobila enheter som kör iOS, Windows, Windows Phone, Android och macOS.

På iOS-enheter kan du skapa en Intune-hanterad e-postprofil som använder S/MIME och certifikat för att signera och kryptera inkommande och utgående e-post. Andra plattformar har kanske men inte nödvändigtvis stöd för S/MIME. Om det stöds kan du installera certifikat som använder S/MIME-signering och kryptering. En slutanvändare kan sedan aktivera S/MIME i sitt e-postprogram.

Mer information om S/MIME-signering och kryptering för e-post finns på sidan om [S/MIME för signering och kryptering av meddelanden](https://docs.microsoft.com/Exchange/policy-and-compliance/smime).

## <a name="signing-certificates"></a>Signeringscertifikat

Certifikat som används för signering gör att klientens e postapp kan kommunicera säkert med e-postservern.

För att använda signeringscertifikat skapar du en mall på din certifikatutfärdare som fokuserar på signering. På Microsoft Active Directory-certifikatutfärdare visar sidan om att [konfigurera certifikatmall för server](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) hur du skapar certifikatmallar.

Signeringscertifikat i Intune använder PKCS-certifikat. [Konfigurera och använda PKCS-certifikat](certficates-pfx-configure.md) beskriver hur du distribuerar och använder PKCS-certifikat i din Intune-miljö. De här stegen innefattar:

- Ladda ned och installera Microsoft Intune-certifikatanslutningsappen för att stödja PKCS-certifikatbegäranden.
- Skapa en profil för betrott rotcertifikat för dina enheter. Det här steget omfattar användning av betrodda rotcertifikat och mellanliggande certifikat för certifikatutfärdaren och sedan distribuering av profilen till enheter.
- Skapa en PKCS-certifikatprofil med hjälp av den certifikatmall som du skapade. Den här profilen utfärdar signeringscertifikat till enheter och distribuerar PKCS-certifikatprofilen till enheter.

Du kan även importera ett signeringscertifikat för en viss användare. Signeringscertifikatet distribueras över alla enheter som en användare registrerar. Om du vill importera certifikat till Intune använder du [PowerShell-cmdletar i GitHub](https://github.com/Microsoft/Intune-Resource-Access). Om du vill distribuera ett PKCS-certifikat som importerats i Intune för användning för signering av e-post följer du stegen i [Konfigurera och använda PKCS-certifikat med Intune](certficates-pfx-configure.md). De här stegen innefattar:

- Ladda ned och installera PFX-certifikatanslutningsappen för Microsoft Intune. Den här anslutningsappen tillhandahåller importerade PKCS-certifikat till enheter.
- Importera S/MIME-e-postsigneringscertifikat till Intune.
- Skapa en PKCS-importerad certifikatprofil. Den här profilen levererar importerade PKCS-certifikat till en lämplig användares enheter.

## <a name="encryption-certificates"></a>Krypteringscertifikat

Certifikat som används för kryptering bekräftar att ett krypterat e-postmeddelande endast kan dekrypteras av den avsedda mottagaren. S/MIME-kryptering är ett extra lager av säkerhet som kan användas i e-postmeddelanden.

När du skickar ett krypterat e-postmeddelande till en annan användare hämtas den offentliga nyckeln för den användarens krypteringscertifikat, och det e-postmeddelande du skickar krypteras. Mottagaren dekrypterar e-postmeddelandet med hjälp av den privata nyckeln på sin enhet. Användare kan ha en historik för certifikat som används för att kryptera e-post. Vart och ett av dessa certifikat måste distribueras till alla enheter för en specifik användare så att användarens e-post dekrypteras på rätt sätt.

Det rekommenderas att e-postkrypteringscertifikat inte skapas i Intune. Intune har stöd för att utfärda PKCS-certifikat som har stöd för kryptering, men Intune skapar ett unikt certifikat per enhet. Ett unikt certifikat per enhet inte är idealiskt för ett scenario för S/MIME-kryptering där krypteringscertifikatet ska delas mellan alla användarens enheter.

Om du vill distribuera S/MIME-certifikat med hjälp av Intune måste du importera alla krypteringscertifikat för en användare till Intune. Intune distribuerar sedan alla de certifikaten till varje enhet som en användare registrerar. Om du vill importera certifikat till Intune använder du [PowerShell-cmdletar i GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Om du vill distribuera ett PKCS-certifikat som importerats i Intune för användning för kryptering av e-post följer du stegen i [Konfigurera och använda PKCS-certifikat med Intune](certficates-pfx-configure.md). De här stegen innefattar:

- Ladda ned och installera PFX-certifikatanslutningsappen för Microsoft Intune. Den här anslutningsappen tillhandahåller importerade PKCS-certifikat till enheter.
- Importera S/MIME-e-postkrypteringscertifikat till Intune.
- Skapa en PKCS-importerad certifikatprofil. Den här profilen levererar importerade PKCS-certifikat till en lämplig användares enheter.

 > [!NOTE]
 > Importerade S/MIME-krypteringscertifikat tas bort av Intune när företagsdata tas bort eller när användarna avregistreras från hantering. Certifikat återkallas dock inte på certifikatutfärdaren.

## <a name="smime-email-profiles"></a>S/MIME-e-postprofiler

När du har skapat certifikatprofiler för S/MIME-signering och kryptering kan du [aktivera S/MIME för intern iOS-e-post](email-settings-ios.md).