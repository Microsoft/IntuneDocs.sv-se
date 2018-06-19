---
title: Övervaka Microsoft Intunes enhetsefterlevnadsprinciper
titlesuffix: ''
description: Använd instrumentpanelen för enhetsefterlevnad för att övervaka övergripande enhetsefterlevnad, visa rapporter och visa enhetsefterlevnad per princip och per inställning.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 2/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c4c3c3a2d73c6390ef5761f1bd0b12fe55855c6e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831879"
---
# <a name="monitor-intune-device-compliance-policies"></a>Övervaka efterlevnadsprinciper för Intune-enheter

Med efterlevnadsrapporter kan administratörer analysera enheternas efterlevnadsstatus i organisationen och snabbt felsöka efterlevnadsrelaterade problem som användarna upplever i organisationen. Du kan visa information om den övergripande efterlevnadsstatusen för enheter, efterlevnadsstatusen för enskilda inställningar, efterlevnadsstatusen för enskilda principer och gå vidare till enskilda enheter och visa de specifika inställningar och principer som påverkar dem.

> [!NOTE]
> Vi inför vissa säkerhetsförbättringar som baserats på dina synpunkter i Intune-tjänsten i mars. Beroende på hur dina efterlevnadsprinciper har konfigurerats, kan du behöva vidta åtgärder för att undvika att förlora e-poståtkomsten för dina slutanvändare. Mer information finns i [Kommande säkerhetsförbättringar](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

## <a name="before-you-begin"></a>Innan du börjar

Så här hittar du **instrumentpanelen för Intune-enhetsefterlevnad** i Azure Portal:

1.  Gå till [Azure Portal](https://portal.azure.com) och logga in med dina Intune-autentiseringsuppgifter.

2.  Välj **Alla tjänster** i den vänstra menyn och skriv sedan **Intune** i textrutans filter.

3.  Välj **Intune** &gt; **Enhetsefterlevnad** &gt; **Översikt**. **Instrumentpanelen för enhetsefterlevnad** öppnas.

> [!IMPORTANT]
> Enheter måste registreras i Intune för att kunna ta emot principer för enhetsefterlevnad.

## <a name="device-compliance-dashboard"></a>Instrumentpanelen för enhetsefterlevnad

På **instrumentpanelen för enhetsefterlevnad** kan du övervaka enhetens olika efterlevnadsstatusar genom rapporter från olika paneler som tillhandahåller efterlevnadsstatusarna för olika enheter i din organisation. Du kan visa följande rapporter:

-   Övergripande samlad enhetsefterlevnad

-   Enhetsefterlevnad per princip

-   Enhetsefterlevnad per inställning

![Bild på instrumentpanelen för enhetsefterlevnad](./media/idc-1.png)

Du kan också visa specifika efterlevnadsprinciper och inställningar som gäller för enskilda enheter, och den slutliga efterlevnadsstatusen för var och en av dessa inställningar på enheten.

### <a name="overall-device-compliance-aggregate-report"></a>Rapport om övergripande samlad enhetsefterlevnad

Det är ett ringdiagram som visar den samlade enhetsstatusen för alla Intune-registrerade enheter. Enhetens efterlevnadsstatusar sparas i två olika databaser – Intune och Azure Active Directory. Här finns mer information om statusen för enhetens efterlevnadsprinciper:

-   **Kompatibel**: Enheten har tillämpat en eller flera av principer för enhetsefterlevnad som administratören har satt upp som mål.

-   **Inte kompatibel:** Enheten har inte tillämpat en eller flera av principer för enhetsefterlevnad som administratören har satt upp som mål, eller så har användaren inte uppfyllt de principer administratören har satt upp som mål.

-   **Respitperiod:** Administratören har satt upp en eller flera principer för enhetsefterlevnad som mål för enheten, men användaren har inte tillämpats principerna ännu, vilket innebär att enheten är inkompatibel, men att den fortfarande befinner sig i en respitperiod som administratören har definierat.

    -   Läs mer om åtgärder för inkompatibla enheter.

-   **Enheten har inte synkroniserats:** Enheten kunde inte rapportera sin enhetsefterlevnadsstatus på grund av någon av följande orsaker:

    -   **Okänd**: Enheten är offline eller kunde inte kommunicera med Intune eller Azure AD av andra orsaker.

    -   **Fel**: Enheten kunde inte kommunicera med Intune eller Azure AD och tog emot ett felmeddelande som angav orsaken.

> [!IMPORTANT]
> Enheter som har registrerats i Intune men inte utgör mål för någon enhetsefterlevnadsprincip, inkluderas i den här rapporten under bucketen **Kompatibel**.

#### <a name="drill-down-option"></a>Alternativet Öka detaljnivån

Om du klickar på ikonen Enhetsefterlevnad i **instrumentpanelen för enhetsefterlevnad** kan du öka detaljnivån för en enskild **efterlevnadsstatus**, **användarens e-postalias**, **enhetsmodell** och **plats** för varje enhet som varit mål för enhetsefterlevnadsprinciperna.

![Bild på ökad detaljnivå på instrumentpanelen för enhetsefterlevnad](./media/idc-2.png)

Om du behöver mer information om en viss användare kan du filtrera diagramrappoten för enhetsefterlevnad genom att skriva användarens e-postalias.

![Bild på viss användare på instrumentpanelen för enhetsefterlevnad](./media/idc-3.png)

Du kan också klicka på de olika efterlevnadsstatusarna i diagrammet över enhetsefterlevnad om du vill se mer detaljerad information om användarens enhetsefterlevnadsstatusar.

![Bild som visar status på instrumentpanelen för enhetsefterlevnad](./media/idc-4.png)

#### <a name="filter"></a>Filter

Om du klickar på **filterknappen** visas följande alternativ:

-   Modell

    -   Textruta för fritextsökning
<br></br>
-   Plattform

    -   Android

    -   iOS

    -   macOS

    -   Windows

    -   Windows Phone

-   Status

    -   Kompatibel

    -   Ej kompatibel

    -   Respitperiod

    -   Okänt

    -   Fel

Om du klickar på knappen **Uppdatera** stängs fältet och resultatet uppdateras enligt de valda filtervillkoren.

##### <a name="device-details"></a>Information om enhet

Om du klickar på en enhet öppnas **fönstret Enheter** med enheten vald, och mer information om enhetens efterlevnadsprincipinställning visas.

När du klickar på enhetens principinställning visas namnet på enhetsefterlevnadsprincip som gav upphov till den enhetsefterlevnadsinställning som administratören har satt upp som mål.

### <a name="devices-without-compliance-policy"></a>Enheter utan policy för efterlevnad
Den här rapporten identifierar enheter som inte har några tilldelade efterlevnadsprinciper. Med införandet av säkerhetsinställningen som markerar alla enheter utan efterlevnadsprinciper som ”icke-kompatibla” är det viktigt att kunna identifiera dessa enheter. Du kan sedan tilldela minst en policy för efterlevnad till dem.

> [!NOTE]
> Den nya säkerhetsinställningen kan konfigureras i Intune-portalen. Välj **Enhetsefterlevnad** och under **Konfiguration** väljer du **Inställningar för policyer för efterlevnad**. Använd växlingsknappen för att ange **Markera enheter som saknar en policy för efterlevnad som** till antingen **Kompatibel** eller **Inte kompatibel**. Läs mer om denna [förbättrade säkerhet i Intune-tjänsten](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

![Bild som visar rapport för Enheter utan policy för efterlevnad](./media/idc-12.png)

Ikonen **Enheter utan policy för efterlevnad** finns i instrumentpanelen Enhetsefterlevnad och visar alla enheter utan en policy för efterlevnad, enhetens användare, efterlevnadsstatus och enhetsmodell.

> [!NOTE]
> Användare som är tilldelade en policy för efterlevnad av valfri typ visas inte i rapporten, oavsett enhetsplattform. Om du exempelvis oavsiktligt har tilldelat en Windows-policy för efterlevnad till en användare med en Android-enhet, visas enheten inte i rapporten. Intune kommer emellertid anse att Android-enheten inte är kompatibel. För att undvika problem rekommenderar vi att du skapar principer för varje enhetsplattform och distribuerar dem till alla användare.

### <a name="per-policy-device-compliance-report"></a>Rapport om enhetsefterlevnad per princip

Den här rapporten visar enhetsefterlevnad per princip och det totala antalet enheter med respektive efterlevnadsstatus. Rubriken för **principefterlevnad** är tillgänglig på instrumentpanelen **Enhetsefterlevnad** och visar alla principer som tidigare har skapats av administratören, de plattformar där principen har tillämpats, antalet kompatibla enheter och antalet inkompatibla enheter.

![Bild som visar rapport om enhetsefterlevnad per princip](./media/idc-8.png)

När du klickar på ikonen Principefterlevnad kan du fortsätta med att klicka på någon av enhetsefterlevnadsprinciperna. Då visas **efterlevnadsstatus**, **användarens e-postalias**, **enhetsmodell** och **plats** för varje enhet som varit mål för enhetsefterlevnadsprinciperna.

## <a name="setting-compliance-report"></a>Inställning av efterlevnadsrapport

Den här rapporten visar enhetsefterlevnadsinställningar och det totala antalet enheter med respektive efterlevnadsstatus. Rubriken för **principefterlevnad** är tillgänglig på instrumentpanelen **Enhetsefterlevnad** och visar alla principer som tidigare har skapats av administratören, de plattformar som principen har tillämpats på, antalet kompatibla enheter och antalet inkompatibla enheter.

![Bild som visar rapport om enhetsefterlevnad per inställning](./media/idc-10.png)

När du klickar på ikonen Inställningsefterlevnad kan du fortsätta med att klicka på någon av enhetsefterlevnadens principinställningar. Då visas **efterlevnadsstatus**, **användarens e-postalias**, **enhetsmodell** och **plats** för varje enhet som varit mål för enhetsefterlevnadens principinställning.
