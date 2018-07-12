---
title: Övervaka efterlevnadsprinciper för enheter i Microsoft Intune – Azure | Microsoft Docs
description: Använd instrumentpanelen för enhetsefterlevnad för att övervaka övergripande enhetsefterlevnad, visa rapporter och visa enhetsefterlevnad per princip och per inställning.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e9de6f1ac8bca1d65a94294d3b049dfccbe44c7
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905367"
---
# <a name="monitor-intune-device-compliance-policies"></a>Övervaka efterlevnadsprinciper för Intune-enheter

Med efterlevnadsrapporter kan administratörer analysera enheternas efterlevnadsstatus i organisationen och snabbt felsöka efterlevnadsrelaterade problem som användarna upplever i organisationen. Du kan visa information om den övergripande efterlevnadsstatusen för enheter, efterlevnadsstatusen för enskilda inställningar, efterlevnadsstatusen för enskilda principer och gå vidare till enskilda enheter och visa de specifika inställningar och principer som påverkar dem.

## <a name="before-you-begin"></a>Innan du börjar

Så här hittar du **instrumentpanelen för Intune-enhetsefterlevnad** i Azure Portal:

1. I [Azure-portalen](https://portal.azure.com) loggar du in med dina Intune-autentiseringsuppgifter.

2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.

3. Välj **Enhetsefterlevnad** > **Översikt**. **Instrumentpanelen för enhetsefterlevnad** öppnas.

> [!IMPORTANT]
> Enheter måste registreras i Intune för att kunna ta emot principer för enhetsefterlevnad.

## <a name="device-compliance-dashboard"></a>Instrumentpanelen för enhetsefterlevnad

I **instrumentpanelen för enhetsefterlevnad** kan du övervaka efterlevnad för olika enheter, deras skyddsstatus och mer. Du kan visa följande rapporter:

- Övergripande samlad enhetsefterlevnad

- Enhetsefterlevnad per princip

- Enhetsefterlevnad per inställning

- Enhetsskyddsstatus

- Status för hotagent

![Bild på instrumentpanelen för enhetsefterlevnad](./media/idc-1.png)

Du kan också visa specifika efterlevnadsprinciper och inställningar som gäller för enskilda enheter, och den slutliga efterlevnadsstatusen för var och en av dessa inställningar på enheten.

### <a name="overall-device-compliance-aggregate-report"></a>Rapport om övergripande samlad enhetsefterlevnad

Det är ett ringdiagram som visar den samlade enhetsstatusen för alla Intune-registrerade enheter. Enhetens efterlevnadsstatusar sparas i två olika databaser – Intune och Azure Active Directory. Här finns mer information om statusen för enhetens efterlevnadsprinciper:

- **Kompatibel**: Enheten har tillämpat en eller flera av principer för enhetsefterlevnad som administratören har satt upp som mål.

- **Inte kompatibel:** Enheten har inte tillämpat en eller flera av principer för enhetsefterlevnad som administratören har satt upp som mål, eller så har användaren inte uppfyllt de principer administratören har satt upp som mål.

- **Respitperiod:** Administratören har satt upp en eller flera principer för enhetsefterlevnad som mål för enheten, men användaren har inte tillämpats principerna ännu, vilket innebär att enheten är inkompatibel, men att den fortfarande befinner sig i en respitperiod som administratören har definierat.

  - Läs mer om åtgärder för inkompatibla enheter.

- **Enheten har inte synkroniserats:** Enheten kunde inte rapportera sin enhetsefterlevnadsstatus på grund av någon av följande orsaker:

  - **Okänd**: Enheten är offline eller kunde inte kommunicera med Intune eller Azure AD av andra orsaker.

  - **Fel**: Enheten kunde inte kommunicera med Intune eller Azure AD och tog emot ett felmeddelande som angav orsaken.

> [!IMPORTANT]
> Enheter som har registrerats i Intune men inte utgör mål för någon enhetsefterlevnadsprincip, inkluderas i den här rapporten under bucketen **Kompatibel**.

#### <a name="drill-down-option"></a>Alternativet Öka detaljnivån

I **instrumentpanelen för enhetsefterlevnad** väljer du en enhetsefterlevnadsruta för att öka detaljnivån till en specifik **efterlevnadsstatus**, **användarens e-postalias**, **enhetsmodell** och **plats** för varje enhet är mål för enhetsefterlevnadsprinciperna.

![Bild på ökad detaljnivå på instrumentpanelen för enhetsefterlevnad](./media/idc-2.png)

Om du behöver mer information om en viss användare kan du filtrera diagramrappoten för enhetsefterlevnad genom att skriva användarens e-postalias.

![Bild på viss användare på instrumentpanelen för enhetsefterlevnad](./media/idc-3.png)

Du kan också klicka på de olika efterlevnadsstatusarna i diagrammet över enhetsefterlevnad om du vill se mer detaljerad information om användarens enhetsefterlevnadsstatusar.

![Bild som visar status på instrumentpanelen för enhetsefterlevnad](./media/idc-4.png)

#### <a name="filter"></a>Filter

När du väljer **filterknappen** visas följande alternativ:

- Modell

  - Textruta för fritextsökning

- Plattform

  - Android

  - iOS

  - macOS

  - Windows

  - Windows Phone

- Status

  - Kompatibel

  - Ej kompatibel

  - Respitperiod

  - Okänt

  - Fel

När du väljer **uppdateringsknappen** stängs fältet och resultatet uppdateras enligt de valda filtervillkoren.

##### <a name="device-details"></a>Information om enhet

Om du markerar en enhet öppnas **Enheter** med enheten markerad. Där finns mer information om inställningarna för enhetens efterlevnadsprincip.

När du markerar enhetens principinställning visas namnet på enhetsefterlevnadsprincip som gav upphov till den enhetsefterlevnadsinställning som administratören har satt upp som mål.

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

## <a name="view-status-of-device-policies"></a>Visa status för enhetsprinciper

Du kan kontrollera principernas olika statusar per plattform. Du kan till exempel ha en efterlevnadsprincip för macOS. Du vill se de enheter som påverkas av den här principen och se om det uppstår konflikter eller fel.

Den här funktionen ingår i statusrapporteringen för enheter:

1. Välj **Enhetsefterlevnad** > **Principer**. En lista över principer visas, inklusive plattformen, om principen har tilldelats, samt ytterligare information.
2. Välj en princip > **Översikt**. I den här vyn innehåller principtilldelningen följande statusar:

  - Lyckades
  - Fel
  - Konflikt
  - Väntar
  - Inte tillämpligt

3. Om du vill visa information om de enheter som använder den här principen väljer du en av statusarna. Välj till exempel **Lyckades**. I nästa fönster visas specifik enhetsinformation, inklusive enhetsnamn och distributionsstatus.

## <a name="how-intune-resolves-policy-conflicts"></a>Så här löser Intune principkonflikter
Principkonflikter kan uppstå när flera Intune-principer används på en enhet. Om principinställningarna överlappar varandra löser Intune eventuella konflikter med hjälp av följande regler:

- Om de motstridiga inställningarna gäller en Intune-konfigurationsprincip och en efterlevnadsprincip, prioriteras inställningarna i efterlevnadsprincipen framför inställningarna i konfigurationsprincipen. Detta gäller även om inställningarna i konfigurationsprincipen är säkrare.

- Om du har distribuerat flera efterlevnadsprinciper använder Intune den säkraste av dessa principer.

