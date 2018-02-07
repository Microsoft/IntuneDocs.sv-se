---
title: "Hur du konfigurerar e-postinställningar i Intune"
titleSuffix: Azure portal
description: "Läs om hur du kan konfigurera Intune för att skapa anslutningar till företagets e-post på enheter som du hanterar.”"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 484bd9b0-fbf1-4f4f-940c-6b12fa07e228
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b8558da2460b6443cbd4d42f7dec420d3e7abc7d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-configure-email-settings-in-microsoft-intune"></a>Så här konfigurerar du e-postinställningar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Du kan använda e-postprofiler för att konfigurera de enheter som du hanterar med de inställningar som behövs för att ansluta till och synkronisera med företagets e-post. Detta gör det enklare för dig att se till att standardinställningarna är gemensamma för alla dina enheter, och det bidrar även till att minska antalet supportsamtal från slutanvändare som vill veta de rätta e-postinställningarna.

Den inbyggda e-postklienten stöds för de flesta plattformar. Merparten av e-postapparna från tredje part stöds inte.

Du kan använda e-postprofiler för att konfigurera den interna e-postklienten på följande enhetstyper:

- Android Samsung Knox Standard 4.0 och senare
- Android for Work
- iOS 8.0 och senare
- Windows Phone 8.1 och senare
- Windows 10 Desktop och Windows 10 Mobile

Använd informationen i det här avsnittet om du vill lära dig grunderna för hur du konfigurerar en e-postprofil. Läs sedan de specifika avsnitten om respektive plattform om du vill ha mer detaljerad information.

## <a name="create-a-device-profile-containing-email-settings"></a>Skapa en enhetsprofil som innehåller e-postinställningar

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. Ange **Namn** och **Beskrivning** för e-postprofilen på bladet **Skapa profil**.
5. Välj den enhetsplattform på vilken du vill tillämpa e-postinställningarna från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för enhetsinställningar för e-post:
    - **Android** (endast Samsung Android Knox Standard)
    - **Android for Work**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 och senare**
6. Välj **E-post** i listrutan **Profil**.
7. Beroende på vilken plattform du har valt så varierar de inställningar som du kan konfigurera. Gå till något av följande avsnitt om du vill ha detaljerad information om respektive plattform:
    - [Android for Work- och Samsung Knox Standard-inställningar](email-settings-android.md)
    - [Inställningar för iOS](email-settings-ios.md)
    - [Inställningar för Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Inställningar för Windows 10](email-settings-windows-10.md)
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).

## <a name="further-information"></a>Ytterligare information

### <a name="remove-an-email-profile"></a>Ta bort en e-postprofil

Om du vill ta bort en e-postprofil från en enhet redigerar du tilldelningen och tar bort alla grupper där enheten är medlem. Observera att du inte kan ta bort en e-postprofil på det här sättet om det är den enda e-postprofilen på en enhet.

### <a name="securing-email-access"></a>Skydda e-poståtkomst

Du kan skydda e-postprofiler på något av följande två sätt:

1. **Certifikat** – När du skapar en e-postprofil väljer du en certifikatprofil som du tidigare har skapat i Intune. Detta kallas identitetscertifikat och används för att autentisera mot en betrodd certifikatprofil (eller ett rotcertifikat) för att fastställa att användarens enhet får ansluta. Det betrodda certifikatet tilldelas datorn som verifierar e-postanslutningen, vanligtvis den interna e-postservern.
Mer information om hur du skapar och använder certifikatprofiler i Intune finns i [Konfigurera certifikat i Intune](certificates-configure.md).
2. **Användarnamn och lösenord** – Användaren autentiseras mot den interna e-postservern genom att ange sitt användarnamn och lösenord.
Lösenordet finns inte i e-postprofilen. Användarna måste ange detta när de ansluter till sin e-post.


### <a name="how-intune-handles-existing-email-accounts"></a>Hur Intune hanterar befintliga e-postkonton

Om användaren redan har konfigurerat ett e-postkonto beror resultatet av tilldelningen av Intune e-postprofil på enhetsplattformen:

- **iOS**: En befintlig duplicerad e-postprofil identifieras utifrån värdnamn och e-postadress. E-postprofilsdubbletten blockerar tilldelningen av en Intune-profil. I det här fallet informerar företagsportalen användaren om att denne inte uppfyller kraven och uppmanar användaren att ta bort den manuellt konfigurerade profilen. Om du vill förhindra det här problemet bör du uppmana användarna registrera sig innan de installerar någon e-postprofil, så att Intune kan konfigurera profilen.
- **Windows** En befintlig duplicerad e-postprofil identifieras utifrån värdnamn och e-postadress. Intune skriver över den befintliga e-postprofilen som skapats av användaren.
- **Android Samsung Knox Standard**: En befintlig, duplicerad e-postprofil identifieras baserat på e-postadressen, och skrivs över med Intune-profilen.
Eftersom Android inte använder värdnamn för att identifiera profilen, rekommenderar vi att du inte skapar flera e-postprofiler för samma e-postadress på olika värdar, eftersom dessa kommer att skriva över varandra.
- **Android for Work** Intune har två olika e-postprofiler för Android for Work, en vardera för e-postapparna Gmail och Nine Work. Dessa appar är tillgängliga i Google Play Store och installeras i enhetens arbetsprofil. Så de kan inte resultera i dubblettprofiler. Båda apparna stöder anslutningar till Exchange. Distribuera en av dessa e-postappar till användarnas enheter och skapa och distribuera en lämplig profil för att aktivera e-postprofil. E-postappar som Nine Work kanske inte är kostnadsfria. Granska appens licensieringsinformation eller kontakta företaget som skapat appen om du har frågor.

### <a name="update-an-email-profile"></a>Uppdatera en e-postprofil

Om du gör ändringar i en e-postprofil som du tidigare tilldelat, kan användarna få ett meddelande som ber dem godkänna omkonfigurationen av deras e-postinställningar.
