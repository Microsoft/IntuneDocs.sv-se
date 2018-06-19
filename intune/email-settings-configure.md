---
title: Konfigurera e-postinställningar i Microsoft Intune
titleSuffix: ''
description: Läs om att konfigurera Microsoft Intune för att skapa anslutningar till företagets e-post på enheter som du hanterar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b71c004a165bd6d38cd1907eadc05ac20f27bd1a
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31834218"
---
# <a name="how-to-configure-email-settings-in-microsoft-intune"></a>Så här konfigurerar du e-postinställningar i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du kan använda e-postprofiler till att konfigurera de enheter som du hanterar med de inställningar som krävs för att ansluta till och synkronisera med företagets e-post. Detta gör det enklare för dig att se till att standardinställningarna är gemensamma för alla dina enheter, och det bidrar även till att minska antalet supportsamtal från slutanvändare som vill veta de rätta e-postinställningarna.

Den inbyggda e-postklienten stöds för de flesta plattformar. Merparten av e-postapparna från tredje part stöds inte.

Du kan använda e-postprofiler för att konfigurera den interna e-postklienten på följande enhetstyper:

- Android Samsung Knox Standard 4.0 och senare
- Android for Work
- iOS 8.0 och senare
- Windows Phone 8.1 och senare
- Windows 10 Desktop och Windows 10 Mobile

Använd informationen i den här artikeln om du vill lära dig grunderna för hur du konfigurerar en e-postprofil. Läs sedan de specifika avsnitten om respektive plattform om du vill ha mer detaljerad information.

## <a name="create-a-device-profile-containing-email-settings"></a>Skapa en enhetsprofil som innehåller e-postinställningar

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enhetskonfiguration**.
2. I fönstret **Enhetskonfiguration** under avsnittet **Hantera** väljer du **Profiler**.
3. I fönstret Profiler väljer du **Skapa profil**.
4. På sidan **Skapa profil** anger du ett **Namn** och en **Beskrivning** för e-postprofilen.
5. Välj den enhetsplattform på vilken du vill tillämpa e-postinställningarna från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för enhetsinställningar för e-post:
    - **Android** (endast Samsung Android Knox Standard)
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**
6. Välj **E-post** i listrutan **Profil**.
7. Vilka inställningar du kan konfigurera varierar beroende på vilken plattform du väljer. Gå till något av följande avsnitt om du vill ha detaljerad information om respektive plattform:
    - [Android for Work- och Samsung Knox Standard-inställningar](email-settings-android.md)
    - [Inställningar för iOS](email-settings-ios.md)
    - [Inställningar för Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Inställningar för Windows 10](email-settings-windows-10.md)
8. När du är klar går du tillbaka till fönstret **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas i fönstret med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).

## <a name="further-information"></a>Ytterligare information

### <a name="remove-an-email-profile"></a>Ta bort en e-postprofil

Om du vill ta bort en e-postprofil från en enhet redigerar du tilldelningen och tar bort alla grupper där enheten är medlem. Du kan inte ta bort en e-postprofil på det här sättet om det är den enda e-postprofilen på en enhet.

### <a name="securing-email-access"></a>Skydda e-poståtkomst

Du kan skydda e-postprofiler på något av följande två sätt:

1. **Certifikat** – När du skapar en e-postprofil väljer du en certifikatprofil som du tidigare har skapat i Intune. Detta kallas identitetscertifikat och används för att autentisera mot en betrodd certifikatprofil (eller ett rotcertifikat) för att fastställa att användarens enhet får ansluta. Det betrodda certifikatet tilldelas datorn som verifierar e-postanslutningen, vanligtvis den interna e-postservern.
Mer information om hur du skapar och använder certifikatprofiler i Intune finns i [Konfigurera certifikat i Intune](certificates-configure.md).
2. **Användarnamn och lösenord** – Användaren autentiseras mot den interna e-postservern genom att ange sitt användarnamn och lösenord.
Lösenordet finns inte i e-postprofilen. Användarna måste ange detta när de ansluter till sin e-post.


### <a name="how-intune-handles-existing-email-accounts"></a>Hur Intune hanterar befintliga e-postkonton

Om användaren redan har konfigurerat ett e-postkonto beror resultatet av tilldelningen av Intune e-postprofil på enhetsplattformen:

- **iOS**: En befintlig duplicerad e-postprofil identifieras utifrån värdnamn och e-postadress. E-postprofildubbletten blockerar tilldelningen av en Intune-profil. I det här fallet informerar företagsportalen användaren om att denne inte uppfyller kraven och uppmanar användaren att ta bort den manuellt konfigurerade profilen. Om du vill förhindra det här problemet bör du uppmana användarna registrera sig innan de installerar någon e-postprofil, så att Intune kan konfigurera profilen.
- **Windows** En befintlig duplicerad e-postprofil identifieras utifrån värdnamn och e-postadress. Intune skriver över den befintliga e-postprofilen som skapats av användaren.
- **Android Samsung Knox Standard**: En befintlig, duplicerad e-postprofil identifieras baserat på e-postadressen, och skrivs över med Intune-profilen.
Eftersom Android inte använder värdnamn för att identifiera profilen, rekommenderar vi att du inte skapar flera e-postprofiler för samma e-postadress på olika värdar, eftersom dessa kommer att skriva över varandra.
- **Android for Work** Intune har två olika e-postprofiler för Android for Work, en vardera för e-postapparna Gmail och Nine Work. Dessa appar är tillgängliga i Google Play Store och installeras i enhetens arbetsprofil. Så de kan inte resultera i dubblettprofiler. Båda apparna stöder anslutningar till Exchange. Distribuera en av dessa e-postappar till användarnas enheter och skapa och distribuera en lämplig profil för att aktivera e-postprofil. E-postappar som Nine Work kanske inte är kostnadsfria. Granska appens licensieringsinformation eller kontakta företaget som skapat appen om du har frågor.

### <a name="update-an-email-profile"></a>Uppdatera en e-postprofil

Om du gör ändringar i en e-postprofil som du tidigare tilldelat, kan användarna få ett meddelande som ber dem godkänna omkonfigurationen av deras e-postinställningar.
