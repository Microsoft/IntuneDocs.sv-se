---
title: "Övervaka efterlevnadsprinciper för Intune-enheter"
titlesuffix: Azure portal
description: "Lär dig hur du övervakar principer för enhetsefterlevnad"
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 2/27/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2f80d46e3e7c25c2b2e7a7c1af9604de1257a21e
ms.sourcegitcommit: a55c009a2ab223f79dc7439539937b284aee0626
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/28/2018
---
# <a name="monitor-intune-device-compliance-policies"></a>Övervaka efterlevnadsprinciper för Intune-enheter

Med efterlevnadsrapporter kan administratörer analysera enheternas efterlevnadsstatus i organisationen och snabbt felsöka efterlevnadsrelaterade problem som användarna upplever i organisationen. Du kan visa information om den övergripande efterlevnadsstatusen för enheter, efterlevnadsstatusen för enskilda inställningar, efterlevnadsstatusen för enskilda principer och gå vidare till enskilda enheter och visa de specifika inställningar och principer som påverkar dem.

## <a name="before-you-begin"></a>Innan du börjar

Gå till **Instrumentpanelen för Intune-enhetsefterlevnad** i Azure Portal genom att följa stegen nedan:

1.  Gå till [Azure Portal](https://portal.azure.com) och logga in med dina Intune-autentiseringsuppgifter.

2.  Välj **Fler tjänster** på den vänstra menyn och skriv sedan **Intune** i textrutefiltret.

3.  Välj **Intune** &gt; **Enhetsefterlevnad** &gt; **Översikt**. **Instrumentpanelen för enhetsefterlevnad** öppnas.

> [!IMPORTANT] 
> Enheter måste registreras i Intune för att kunna ta emot principer för enhetsefterlevnad.

## <a name="device-compliance-dashboard"></a>Instrumentpanelen för enhetsefterlevnad

På **instrumentpanelen för enhetsefterlevnad** kan du övervaka enhetens olika efterlevnadsstatusar genom rapporter från olika paneler som tillhandahåller efterlevnadsstatusarna för olika enheter i din organisation. Du kan visa följande rapporter:

-   Övergripande samlad enhetsefterlevnad

-   Enhetsefterlevnad per princip

-   Enhetsefterlevnad per inställning

![Instrumentpanelen för enhetsefterlevnad](./media/idc-1.png)

Du kan också visa specifika efterlevnadsprinciper och inställningar som gäller för enskilda enheter, och den slutliga efterlevnadsstatusen för var och en av dessa inställningar på enheten.

### <a name="overall-device-compliance-aggregate-report"></a>Rapport om övergripande samlad enhetsefterlevnad

Det är ett ringdiagram som visar den samlade enhetsstatusen för alla Intune-registrerade enheter. Enhetens efterlevnadsstatusar sparas i två olika databaser – Intune och Azure Active Directory. Här finns mer information om statusen för enhetens efterlevnadsprinciper:

-   **Kompatibel**: Enheten har tillämpat en eller flera av principer för enhetsefterlevnad som administratören har satt upp som mål.

-   **Inte kompatibel:** Enheten har inte tillämpat en eller flera av principer för enhetsefterlevnad som administratören har satt upp som mål, eller så har användaren inte uppfyllt de principer administratören har satt upp som mål.

-   **Respitperiod:** Administratören har satt upp en eller flera principer för enhetsefterlevnad som mål för enheten, men användaren har inte tillämpats principerna ännu, vilket innebär att enheten är inkompatibel, men att den fortfarande befinner sig i en respitperiod som administratören har definierat.

    -   Läs mer om åtgärder för inkompatibla enheter.

-   **Enheten är inte synkroniserad:** Enheten kunde inte rapportera sin enhetsefterlevnadsstatus pga. någon av följande orsaker:

    -   **Okänd**: Enheten är offline eller kunde inte kommunicera med Intune eller Azure AD av andra orsaker.

    -   **Fel**: Enheten kunde inte kommunicera med Intune eller Azure AD och tog emot ett felmeddelande som angav orsaken.

> [!IMPORTANT] 
> Enheter som har registrerats i Intune men inte utgör mål för någon enhetsefterlevnadsprincip, inkluderas i den här rapporten under bucketen **Kompatibel**.

#### <a name="drill-down-option"></a>Alternativet Öka detaljnivån

Om du klickar på ikonen Enhetsefterlevnad i **instrumentpanelen för enhetsefterlevnad** kan du öka detaljnivån för en enskild **efterlevnadsstatus**, **användarens e-postalias**, **enhetsmodell** och **plats** för varje enhet som varit mål för enhetsefterlevnadsprinciperna.

![Ökad detaljnivå på instrumentpanelen för enhetsefterlevnad](./media/idc-2.png)

Om du behöver mer information om en viss användare kan du filtrera diagramrappoten för enhetsefterlevnad genom att skriva användarens e-postalias.

![Specifik användare på instrumentpanelen för enhetsefterlevnad](./media/idc-3.png)

Du kan också klicka på de olika efterlevnadsstatusarna i diagrammet över enhetsefterlevnad om du vill se mer detaljerad information om användarens enhetsefterlevnadsstatusar.

![Olika statusar på instrumentpanelen för enhetsefterlevnad](./media/idc-4.png)

#### <a name="filter"></a>Filter

Om du klickar på **filterknappen** visas följande alternativ:

-   Modell

    -   Textruta för fritextsökning
<br></br>
-   Plattform

    -   Android

    -   iOS

    -   Mac OS

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

Om du klickar på en enhet öppnas bladet **Enheter** med den valda enheten markerad. Här får du mer information om inställningarna för enhetens efterlevnadsprincip.

![Instrumentpanelen för enhetsefterlevnad](./media/idc-6.png)

När du klickar på enhetens principinställning visas namnet på enhetsefterlevnadsprincip som gav upphov till den enhetsefterlevnadsinställning som administratören har satt upp som mål.

![Namn på inställning för enhetsefterlevnad](./media/idc-7.png)

## <a name="policy-compliance-report"></a>Principefterlevnadsrapport

Den här rapporten visar enhetsefterlevnad per princip och det totala antalet enheter med respektive efterlevnadsstatus. Rubriken för **principefterlevnad** är tillgänglig på instrumentpanelen **Enhetsefterlevnad** och visar alla principer som tidigare har skapats av administratören, de plattformar där principen har tillämpats, antalet kompatibla enheter och antalet inkompatibla enheter.

![Rapport om enhetsefterlevnad per princip](./media/idc-8.png)

När du klickar på ikonen Principefterlevnad kan du fortsätta med att klicka på någon av enhetsefterlevnadsprinciperna. Då visas **efterlevnadsstatus**, **användarens e-postalias**, **enhetsmodell** och **plats** för varje enhet som varit mål för enhetsefterlevnadsprinciperna.

![Ikonen för principefterlevnad](./media/idc-9.png)

## <a name="setting-compliance-report"></a>Inställning av efterlevnadsrapport

Den här rapporten visar enhetsefterlevnadsinställningar och det totala antalet enheter med respektive efterlevnadsstatus. Rubriken **Principefterlevnad** är tillgänglig på **instrumentpanelen för enhetsefterlevnad** och visar alla principinställningar för enhetsefterlevnad som har skapats av administratören, de plattformar där principinställningarna har tillämpats samt antalet inkompatibla enheter.

![Rapport om enhetsefterlevnad per inställning](./media/idc-10.png)

När du klickar på ikonen Inställningsefterlevnad kan du fortsätta med att klicka på någon av enhetsefterlevnadens principinställningar. Då visas **efterlevnadsstatus**, **användarens e-postalias**, **enhetsmodell** och **plats** för varje enhet som varit mål för enhetsefterlevnadens principinställning.

![Ikonen för inställningsefterlevnad](./media/idc-11.png)

## <a name="threat-agent-status-report"></a>Rapport om agentstatus för hot

Med den här rapporten kan du se status och hälsa för Windows Defender-agenten. Med hjälp av en rapport om statussammanställningen i **Enhetsefterlevnad** kan du se de enheter som behöver någon av följande åtgärder:
- Signaturuppdatering
- Starta om
- Manuell åtgärd
- Fullständig genomsökning
- Övriga agenttillstånd som kräver åtgärder

En detaljerad rapport för varje statuskategori visar de enskilda datorer som behöver åtgärdas, eller datorer som rapporteras som **Rengör**.
