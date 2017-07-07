---
title: "Övervaka efterlevnadsprinciper för Intune-enheter"
titleSuffix: Intune on Azure
description: "Lär dig hur du övervakar principer för enhetsefterlevnad.\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 503d1dd2-a647-4aea-bf48-55319a3dd8a7
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6d0105e49bac2af0c241fe9203c411ef7f9e7d76
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="monitor-intune-device-compliance-policies"></a>Övervaka efterlevnadsprinciper för Intune-enheter

Efterlevnadsrapporter hjälper administratörerna att analysera enheternas efterlevnadsstatus i organisationen och snabbt felsöka efterlevnadsrelaterade problem som användarna kan stöta på i organisationen. Du kan visa information om den övergripande efterlevnadsstatusen för enheter, efterlevnadsstatusen för enskilda inställningar, efterlevnadsstatusen för enskilda principer och gå vidare till enskilda enheter och visa de specifika inställningar och principer som påverkar dem.

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

-   **Enheten har inte synkroniserats:** Enheten kunde inte rapportera sin enhetsefterlevnadsstatus pga någon av följande orsaker:

    -   **Okänd**: Enheten är offline eller kunde inte kommunicera med Intune eller Azure AD av andra orsaker.

    -   **Fel**: Enheten kunde inte kommunicera med Intune eller Azure AD och tog emot ett felmeddelande som angav orsaken.

> [!IMPORTANT] 
> Enheter som har registrerats i Intune, men inte utgör mål för någon princip för enhetsefterlevnad, inkluderas i den här rapporten under bucketen **Kompatibel**.

#### <a name="drill-down-option"></a>Alternativet Öka detaljnivån

Om du klickar på ikonen för enhetsefterlevnad på instrumentpanelen **Enhetsefterlevnad** kan du öka detaljnivån för enskilda **efterlevnadsstatusar**, **e-postalias**, **enhetsmodeller** och **platser** för de enheter som varit mål för principerna för enhetsefterlevnad.

![Ökad detaljnivå på instrumentpanelen för enhetsefterlevnad](./media/idc-2.png)

Om du behöver mer information om en viss användare kan du filtrera diagramrappoten för enhetsefterlevnad genom att skriva användarens e-postalias.

![Viss användare på instrumentpanelen för enhetsefterlevnad](./media/idc-3.png)

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

### <a name="per-policy-device-compliance-report"></a>Rapport om enhetsefterlevnad per princip

Den här rapporten visar enhetsefterlevnad per princip och det totala antalet enheter med respektive efterlevnadsstatus. Rubriken för **principefterlevnad** är tillgänglig på instrumentpanelen **Enhetsefterlevnad** och visar alla principer som tidigare har skapats av administratören, de plattformar där principen har tillämpats, antalet kompatibla enheter och antalet inkompatibla enheter.

![Rapport om enhetsefterlevnad per princip](./media/idc-8.png)

Om du klickar på ikonen för principefterlevnad, så klicka sedan vidare på någon av principerna för enhetsefterlevnad. Då visas **efterlevnadsstatus**, **e-postalias**, **enhetsmodell** och **plats** för de enheter som varit mål för principerna för enhetsefterlevnad.

![Ikonen för principefterlevnad](./media/idc-9.png)

### <a name="per-setting-device-compliance-report"></a>Rapport om enhetsefterlevnad per inställning

Den här rapporten visar enhetsefterlevnadsinställningar och det totala antalet enheter med respektive efterlevnadsstatus. Rubriken för **inställningsefterlevnad** är tillgänglig på instrumentpanelen **Enhetsefterlevnad** och visar alla inställningar för enhetsefterlevnad från alla principer för enhetsefterlevnad som skapats av administratören, de plattformar där inställningarna tillämpats och antalet inkompatibla enheter.

![Rapport om enhetsefterlevnad per inställning](./media/idc-10.png)

Om du klickar på ikonen för inställningsefterlevnad, så klicka sedan vidare på någon av enhetsefterlevnadsinställningarna. Då visas **efterlevnadsstatus**, **e-postalias**, **enhetsmodell** och **plats** för de enheter som varit mål för inställningarna för enhetsefterlevnad.

![Ikonen för inställningsefterlevnad](./media/idc-11.png)
