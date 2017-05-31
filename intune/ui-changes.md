---
title: "Var är Intune-funktionen i Azure?"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: hjälper dig att hitta Intune-funktioner i Azure-konsolen."
keywords: 
author: dagerrit
ms.author: dagerrit
manager: angrobe
ms.date: 03/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 9dd6e93108ffc46e9e52b6928cf513161d29f7a4
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---
# <a name="where-did-my-intune-feature-go-in-azure"></a>Var är Intune-funktionen i Azure?
Vi passade på att ordna några uppgifter på ett mer logiskt sätt när vi flyttade Intune till Azure-portalen. Men alla förbättringar innebär att man måste lära sig den nya ordningen. Därför har vi skapat den här guiden för dem som är bekanta med Intune i den klassiska konsolen och undrar hur de ska arbeta i Intune på Azure. Om du letar efter en funktion som inte tas upp i den här artikeln kan du lämna en kommentar vid artikelns slut så kan vi uppdatera den.
## <a name="quick-reference-guide"></a>Snabbguide
|Funktion |Sökväg i klassisk konsol |Sökväg i Intune på Azure| |------------||---------------|---------------|
|Programmet för enhetsregistrering (DEP) |Admin > Hantering av mobila enheter > iOS och Mac OS X > Programmet för enhetsregistrering|[Enhetsregistrering > Apple-registrering > Token för registreringsprogram](#where-did-apple-dep-go) |
|Programmet för enhetsregistrering (DEP)| Admin > Hantering av mobila enheter > iOS och Mac OS X > Programmet för enhetsregistrering |[Enhetsregistrering > Apple-registrering > Serienummer för registreringsprogram](#where-did-apple-dep-go) |
|Registreringsregler |Admin > Hantering av mobila enheter > Registreringsregler |[Enhetsregistrering > Registreringsbegränsningar](#where-did-enrollment-rules-go) |
|Grupper efter iOS-serienummer |Grupper > Alla enheter > Företagets förregistrerade enheter > Efter iOS-serienummer |[Enhetsregistrering > Apple-registrering > Serienummer för registreringsprogram](#where-did-corporate-pre-enrolled-devices-go) |
|Grupper efter iOS-serienummer |Grupper > Alla enheter > Företagets förregistrerade enheter > Efter iOS-serienummer | [Enhetsregistrering > Apple-registrering > AC-serienummer](#where-did-corporate-pre-enrolled-devices-go)|
|Grupper efter IMEI (alla plattformar)| Grupper > Alla enheter > Företagets förregistrerade enheter > Efter IMEI (Alla plattformar) | [Enhetsregistrering > ID:n för företagsenheter](#by-imei-all-platforms)|
| Registreringsprofil för företagsenhet | Princip > Företagsenhetsregistrering | [Enhetsregistrering > Apple-registrering > Profiler för registreringsprogram](#where-did-corporate-pre-enrolled-devices-go) |
| Registreringsprofil för företagsenhet | Princip > Företagsenhetsregistrering | [Enhetsregistrering > Apple-registrering > AC-profiler](#where-did-corporate-pre-enrolled-devices-go) |
| Android för arbete | Administratör > Mobil enhetshantering > Android för arbete | Enhetsregistrering > Registrering av Android för arbete | | Allmänna villkor | Princip > Allmänna villkor | Enhetsregistrering > Allmänna villkor |


## <a name="where-do-i-manage-groups"></a>Var hanterar jag grupper?
Intune på Azure använder [Azure Active Directory (AD)](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) för att hantera grupper.

## <a name="where-did-enrollment-rules-go"></a>Var finns registreringsreglerna?
I den klassiska konsolen gick det att ange regler för att styra MDM-registrering av mobila och moderna Windows- och macOS-enheter:

![Bild av klassiska regler för registrering av mobil enhet](./media/01-classic-rules.png)

Dessa regler tillämpades på alla användare i Intune-kontot utan undantag. I Azure-portalen visas dessa regler nu i två olika principtyper: Begränsningar av enhetstyp och Begränsningar för enhetsgräns:

![Bild av registreringsbegränsningar för mobil enhet](./media/02-azure-enroll-restrictions.png)

Standarden för Begränsningar för enhetsgräns motsvarar enhetsregistreringsgränsen i den klassiska konsolen:

![Bild av begränsningar för enhetsgräns i Azure](./media/03-azure-device-limit.png)

Standarden för Begränsningar av enhetstyp motsvarar plattformsbegränsningarna i den klassiska konsolen:

![Bild av begränsningar av enhetstyp i Azure](./media/04-azure-platform-restrictions.png)

Möjligheten att tillåta eller blockera personligt ägda enheter hanteras nu under plattformskonfigurationerna för Begränsningar av enhetstyp:

![Bild av blockeringsinställningar för personlig enhet i Azure](./media/05-azure-personal-block.png)

De nya begränsningsfunktionerna läggs endast till i Azure-portalen.

## <a name="where-did-apple-dep-go"></a>Var finns Apple DEP?
I den klassiska konsolen kunde du konfigurera Intune för att integrera med Apples enhetsregistreringsprogram och manuellt begära synkronisering med Apple-tjänsten:

![Bild av klassisk DEP-token](./media/06-classic-dep-token.png)

I Azure-portalen konfigurerar du Apples enhetsregistreringsprogram på samma sätt som i klassiska Intune:

![Bild av Azure DEP-token](./media/07-azure-dep-token.png)

Alternativet **Synkronisera** har dock flyttats till arbetsflödet för hantering av serienummer, eftersom resultatet av en manuell synkronisering visas där:

![Bild av Azure DEP-synkronisering](./media/08-azure-dep-sync.png)

## <a name="where-did-corporate-pre-enrolled-devices-go"></a>Var finns företagets förregistrerade enheter?
### <a name="by-ios-serial-number"></a>Efter iOS-serienummer
I den klassiska konsolen går det att registrera iOS-enheter via Apples enhetsregistreringsprogram (DEP) och verktyget Apple Configurator. Båda metoderna ger förregistrering av enheter efter serienummer och omfattar tilldelning av särskilda profiler för registrering av företagsenheter. Innan du registrerar kan tilldelning av registreringsprofiler hanteras via enhetsgruppen **Företagets förregistrerade enhet efter iOS-serienummer**:

![Bild av klassiska Apple-serienummer](./media/09-classic-apple-serials.png)

Här visas serienummer för både Apple DEP- och Configurator-registrering i en lista. Vi har delat upp serienumren i två listor i Azure-portalen för att minska felmatchningar av profiltilldelning (DEP-profil till AC-serienummer och tvärtom):

**DEP-serienummer**
![Bild av Azure DEP-serienummer](./media/10-azure-dep-serials.png)

**Apple Configurator-serienummer**
![Bild av Azure Apple Configurator-serienummer](./media/11-azure-ac-serials.png)

### <a name="by-imei-all-platforms"></a>Efter IMEI (alla plattformar)

I den klassiska konsolen kan du på förhand ange en lista med IMEI-nummer för att markera dem som företagsenheter när de registreras i Intune:

![Bild av klassisk lista med IMEI-nummer](./media/12-classic-corp-imei.png)

I Azure-konsolen måste du överföra samma IMEI till företagets lista med enhetsidentifierare med hjälp av en fil med kommaavgränsade värden (CSV). Den nya portalen har inte stöd för manuell inmatning av IMEI-nummer:

![Bild av Azure-lista med IMEI-nummer](./media/13-azure-corp-imei.png)

Intune i Azure-portalen har framtidssäkrats med stöd för andra typer av identifierare utöver IMEI, men för närvarande kan bara IMEI-nummer användas för förhandslistor.

## <a name="where-did-corporate-device-enrollment-profiles-go"></a>Var finns profiler för Företagsenhetsregistrering?
Du måste ange en profil för Företagsenhetsregistrering som ska tilldelas till enheten för att registrera iOS-enheter via Apples enhetsregistreringsprogram eller med verktyget Apple Configurator. I den klassiska konsolen fanns skapande och hantering av dessa profiler i en enda lista:

![Bild av klassiska profiler för enhetsregistrering](./media/14-classic-corp-profiles.png)

Den här listan visar profiler som har aktiverats för användning med Apples enhetsregistreringsprogram (**DEP på**) och profiler som endast är aktiverade för användning med verktyget Apple Configurator (**DEP av**).

Vi har skilt på skapande och hantering av profiler för registreringsprogram (med stöd för både Apples enhetsregistreringsprogram och Apple School Manager) och Apple Configurator-profiler i syfte att minska förvirring mellan de två profiltyperna och risken för felmatchade tilldelningar (DEP-profil till Configurator-enheter och tvärtom):

**DEP-profiler**
![Bild av Azure DEP-profiler](./media/15-azure-dep-profiles.png)

**Apple Configurator-profiler**
![Bild av Azure Apple Configurator-profiler](./media/16-azure-ac-profiles.png)

