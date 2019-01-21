---
title: Supportavdelningens felsökningsportal
titlesuffix: Microsoft Intune
description: Supportavdelningen använder felsökningsportalen till att lösa användarnas tekniska problem.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 37483f0fa33db109510ee537772a7bdead79e4f3
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203560"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Använd felsökningsportalen för att hjälpa användare i ditt företag

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I felsökningsportalen kan supportansvariga och Intune-administratörer se användarinformation för att tillgodose användarnas begäran om hjälp. Organisationer som har en supportavdelning kan tilldela rollen **supportavdelning** till en grupp användare. Rollen som supportansvarig kan nu använda **felsökningsfönstret**.

Fönstret **Felsökning** visar nu även problem med användarregistreringen. Information om problemet och förslagna lösningar kan hjälpa administratörer och medarbetare på supportavdelningen att felsöka problem. Vissa problem med registreringen inte fångas upp, och vissa fel kanske inte har några reparationsförslag.

Anvisningar om att lägga till rollen supportansvarig finns i [Rollbaserad administrationskontroll (RBAC) med Intune](/intune/role-based-access-control)

När en användare kontaktar supporten om ett tekniskt problem i Intune kan supportansvarig ange användarens namn. Intune visar användbara data som kan hjälpa dig att lösa många nivå 1-problem, inklusive:

- Användarstatus
- Tilldelningar
- Efterlevnadsproblem
- Enheten svarar inte
- Enheten saknar VPN- eller Wi-Fi-inställningar
- Appinstallationsfel

## <a name="to-review-troubleshooting-details"></a>Granska information om felsökning

I felsökningsfönstret kan du välja **Välj användare** för att visa information om en användare. Med hjälp av användarinformation kan du få en bättre förståelse för det aktuella tillståndet för användarna och deras enheter.  

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Felsök** i fönstret **Intune**.
4. Klicka på **Välj** för att välja en användare att felsöka.
5. Välj en användare genom att skriva namnet eller e-postadressen. Klicka på **Välj**. Felsökningsinformationen för användaren visas i fönstret Felsökning. Följande tabell förklarar informationen.

> [!Note]  
> Du kan också få åtkomst till **felsökningsfönstret** genom att gå till: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="areas-of-troubleshooting-dashboard"></a>Områden för felsökning av instrumentpanelen

Du kan använda fönstret **Felsökning** för att granska användarinformation.

![](/intune/media/troubleshooting-dash.png)

| Område | Namn | Beskrivning |
| ---  | ---  | ---         |
| 1.   | Kontostatus  | Visar status för aktuell Intune-klient som **Aktiv** eller **Inaktiv**.       |
| 2.   | Val av användare  | Namnet på den valda användaren. Välj en ny användare genom att klicka på **Ändra användare**.       |
| 3.   | Användarstatus  | Visar status för användarens Intune-licens, antal enheter, varje enhetskompatibilitet, antalet appar och appkompatibilitet.       |
| 4.   | Användarinformation  | Använd listan för att välja information som du vill läsa i fönstret. <br>Du kan välja: <ul><li>Klientappar<li>Efterlevnadsprinciper<li> Konfigurationsprinciper<li>Appskyddsprinciper <li>Registreringsbegränsningar</ul>      |
| 5.   | Gruppmedlemskap  | Visar de grupper som den valda användaren är medlem i.       |

## <a name="client-apps-reference"></a>Referens för klientappar

Apparna som kör enheter
- hanteras av Intune och Azure Active Directory (AD) 
- ägs av användare som hanteras av Intune och Azure Active Directory (AD).

### <a name="properties"></a>Enheter

Egenskaperna för klientappar.

| Egenskap      | Beskrivning                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Namn          | Namnet på programmet.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Operativsystem            | Operativsystemet som är installerat på enheten.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Typ          | Du kan välja en tilldelningstyp för varje program.  <br> **Tillgänglig** – Användarna installerar appen från företagsportalappen eller webbplatsen.  <br> **Inte tillämpligt** – Appen varken installeras eller visas i företagsportalen. <br> **Avinstallera** – Appen avinstalleras från enheter i valda grupper.  <br> **Tillgänglig med eller utan registrering** – Tilldela den här appen till grupper av användare vars enheter inte har registrerats med Intune. |
| Senast ändrad | Namnet på enhetstypen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### <a name="devices"></a>Egenskaper

Enheter som hanteras av Intune eller av användare som hanteras av Intune eller Azure AD.

| Egenskap           | Beskrivning                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Enhetsnamn        | Namnet på enhetstypen.                                                                                                     |
| Hanteras av         | Tidsstämpelprincipen har ändrats.                                                                                              |
| Azure AD-anslutningstyp | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Äganderätt          | Typen av enhetsägarskap (**företag**, **personlig** eller **okänd**).                                               |
| Kompatibel med Intune   | Namnet på enhetstypen.                                                                                                     |
| Kompatibel med Azure AD | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Appinstallation | Anger om en appinstallation har lyckats eller misslyckats på den enskilda enheten. |
| Operativsystem                 | Operativsystemet som är installerat på enheten.                                                                                       |
| OS-version         | Enhetens operativsystemversionsnummer.                                                                                  |
| Senaste incheckning      | Namnet på enhetstypen.                                                                                                     |

### <a name="app-protection-status"></a>Appskyddsstatus

En appskyddsprincip är tillgänglig för mobilappar som integreras med EMS-teknik (Enterprise Mobility Solution). Dessa principer skapar en baslinje för skydd av företagets data när de laddas ned till mobilappar, inklusive Office-mobilappar. 

| Egenskap    | Beskrivning                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Typen av enhetsägarskap (**företag**, **personlig** eller **okänd**). |
| Appnamn    | Namnet på programmet                                                           |
| Enhetsnamn | Namnet på enhetstypen.                                                       |
| Enhetstyp | Namnet på enhetstypen.                                                       |
| Policys    | Typen av enhetsägarskap (**företag**, **personlig** eller **okänd**). |
| Senaste synkronisering   | Tidsstämpel för den senaste gången enheten synkroniserades med Intune.                   |

## <a name="app-protection-policies-reference"></a>Appskyddsprinciper för referens

En appskyddsprincip är tillgänglig för mobilappar som integrerar med EMS-teknik. De här principerna skapar en baslinje för skydd av företagets data när de laddas ned till mobilappar, inklusive Office-mobilapparna. 

### <a name="properties"></a>Enheter

I tabellen sammanfattas appskyddsprincipernas status för enheter som hanteras av Intune.

| Egenskap    | Beskrivning                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Namn        | Namnet på programmet.                                                                                                        |
| Distribuerad    | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Plattform    | Typen av enhetsägarskap (**företag**, **personlig** eller **okänd**).                                               |
| Registrering  | Namnet på enhetstypen.                                                                                                     |
| Senaste uppdateringen | Tidsstämpelprincipen har ändrats.                                                                                              |

### <a name="devices"></a>Egenskaper

Enheter som hanteras av Intune eller av användare som hanteras av Intune eller Azure AD.

| Egenskap           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Enhetsnamn        | Namnet på enhetstypen.                                                                                                     |
| Hanteras av         | Tidsstämpelprincipen har ändrats.                                                                                              |
| Azure AD-anslutningstyp | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Äganderätt          | Typen av enhetsägarskap (**företag**, **personlig** eller **okänd**).                                               |
| Kompatibel med Intune   | Namnet på enhetstypen.                                                                                                     |
| Kompatibel med Azure AD | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Kompatibel med Azure AD | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Operativsystem                 | Operativsystemet som är installerat på enheten.                                                                                       |
| OS-version         | Enhetens operativsystemversionsnummer.                                                                                  |
| Senaste incheckning      | Namnet på enhetstypen.                                                                                                     |

## <a name="compliance-policies-reference"></a>Referens för efterlevnadsprinciper

Ser till att de enheter som används för åtkomst till företagets appar och data följer vissa regler, t.ex. använder en PIN-kod för att komma åt enheten, och kryptering av data som lagras på enheten.

### <a name="properties"></a>Enheter

Egenskaperna för efterlevnadsprinciperna.

| Egenskap      | Beskrivning                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Tilldelning    | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Namn          | Namnet på programmet.                                                                                                        |
| Operativsystem            | Operativsystemet som är installerat på enheten.                                                                                       |
| Principtyp   | Typen av enhetsägarskap (**företag**, **personlig** och **okänd**).                                               |
| Senast ändrad | Namnet på enhetstypen.                                                                                                     |

### <a name="devices"></a>Egenskaper

Enheter som hanteras av Intune eller av användare som hanteras av Intune eller Azure AD.

| Egenskap           | Beskrivning                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Enhetsnamn        | Namnet på enhetstypen.                                                                                                     |
| Hanteras av         | Tidsstämpelprincipen har ändrats.                                                                                              |
| Azure AD-anslutningstyp | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Äganderätt          | Typen av enhetsägarskap (**företag**, **personlig** och **okänd**).                                               |
| Kompatibel med Intune   | Namnet på enhetstypen.                                                                                                     |
| Kompatibel med Azure AD | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Operativsystem                 | Operativsystemet som är installerat på enheten.                                                                                       |
| OS-version         | Enhetens operativsystemversionsnummer.                                                                                  |
| Senaste incheckning      | Namnet på enhetstypen.                                                                                                     |

### <a name="app-protection-policies"></a>Appskyddsprinciper

En appskyddsprincip är tillgänglig för mobilappar som integreras med EMS-teknik. Dessa principer skapar en baslinje för skydd av företagets data när de laddas ned till mobilappar, inklusive Office-mobilappar. 

| Egenskap    | Beskrivning                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Typen av enhetsägarskap (**företag**, **personlig** eller **okänd**). |
| Appnamn    | Namnet på programmet                                                           |
| Enhetsnamn | Namnet på enhetstypen.                                                       |
| Enhetstyp | Namnet på enhetstypen.                                                       |
| Policys    | Typen av enhetsägarskap (**företag**, **personlig** eller **okänd**). |
| Senaste synkronisering   | Tidsstämpel för den senaste gången enheten synkroniserades med Intune.                   |

## <a name="configuration-policies-reference"></a>Referens för konfigurationsprinciper

En appskyddsprincip är tillgänglig för mobilappar med leverantörsspecifika konfigurationer. 

### <a name="properties"></a>Enheter

Egenskaperna för konfigurationspolicyerna.

| Egenskap      | Beskrivning                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Tilldelning    | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Namn          | Namnet på programmet.                                                                                                        |
| Operativsystem            | Operativsystemet som är installerat på enheten.                                                                                       |
| Principtyp   | Typen av enhetsägarskap (**företag**, **personlig** eller **okänd**).                                               |
| Senast ändrad | Namnet på enhetstypen.                                                                                                     |

### <a name="devices"></a>Egenskaper

Enheter som hanteras av Intune eller av användare som hanteras av Intune eller Azure AD.

| Egenskap           | Beskrivning                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Enhetsnamn        | Namnet på enhetstypen.                                                                                                     |
| Hanteras av         | Tidsstämpelprincipen har ändrats.                                                                                              |
| Azure AD-anslutningstyp | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Äganderätt          | Typen av enhetsägarskap (**företag**, **personlig** eller **okänd**).                                               |
| Kompatibel med Intune   | Namnet på enhetstypen.                                                                                                     |
| Kompatibel med Azure AD | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Operativsystem                 | Operativsystemet som är installerat på enheten.                                                                                       |
| OS-version         | Enhetens operativsystemversionsnummer.                                                                                  |
| Senaste incheckning      | Namnet på enhetstypen.                                                                                                     |


### <a name="app-protection-policies"></a>Appskyddsprinciper

En appskyddsprincip är tillgänglig för mobilappar som integreras med EMS-teknik. Dessa principer skapar en baslinje för skydd av företagets data när de laddas ned till mobilappar, inklusive Office-mobilappar. 

| Egenskap    | Beskrivning                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Typen av enhetsägarskap (**företag**, **personlig** eller **okänd**). |
| Appnamn    | Namnet på programmet                                                           |
| Enhetsnamn | Namnet på enhetstypen.                                                       |
| Enhetstyp | Namnet på enhetstypen.                                                       |
| Policys    | Typen av enhetsägarskap (**företag**, **personlig** eller **okänd**). |
| Senaste synkronisering   | Tidsstämpel för den senaste gången enheten synkroniserades med Intune.                   |

## <a name="enrollment-failure-reference"></a>Referens för registreringsfel

Tabellen för registreringsfel visar misslyckade registreringsförsök. En enhet som visas i tabellen nedan kan ha registrerats korrekt vid ett senare försök. Vissa misslyckade försök kanske inte visas. Åtgärdsinformation är inte tillgänglig för alla fel.

| Tabellkolumn | Beskrivning |
|-------------|----------|
| Registreringsstart | Starttiden när användaren påbörjade registreringen. |
| Operativsystem | Enhetens operativsystem. |
| OS-version | Enhetens operativsystemversion. |
| Fel | Orsaken till felet. |

### <a name="failure-details"></a>Information om felet

När du väljer en felrad visas mer information.

| Sektion | Beskrivning |
|-------------|----------|
| Information om felet | En mer detaljerad förklaring av felet. |
| Potentiella åtgärder | Föreslagna steg för att lösa problemet. Vissa fel kanske inte har någon rekommenderad åtgärd. |
| Resurser (valfritt) | Länkar till ytterligare läsning eller områden på portalen där du kan vidta åtgärder. |

### <a name="enrollment-errors"></a>Registreringsfel

| Fel | Information |
|-------------|----------|
| iOS-timeout eller iOS-fel | En timeout mellan enheten och Intune som beror på att användaren tar för lång tid på sig att slutföra registreringen. |
| Användaren hittades inte eller är inte licensierad | Användaren saknar en licens eller har tagits bort från tjänsten. |
| Enheten är redan registrerad | Någon har försökt registrera en enhet med hjälp av företagsportalen på en enhet som fortfarande är registrerad av en annan användare. |
| Inte registrerad i Intune | En registrering gjordes när MDM-utfärdaren (hantering av mobilenheter) för Intune inte hade konfigurerats. |
| Registreringsauktoriseringen misslyckades | Ett registreringsförsök gjordes med hjälp av en äldre version av företagsportalen. |
| Enheten stöds inte | Enheten uppfyller inte minimikraven för Intune-registrering. |
| Registreringsbegränsningarna uppfylls inte | Registreringen blockerades på grund av att en administratör har konfigurerat registreringsbegränsningar. |
| Enhetsversionen är för låg | Administratören har konfigurerat en registreringsbegränsning som kräver en högre enhetsversion. |
| Enhetsversionen är för hög | Administratören har konfigurerat en registreringsbegränsning som kräver en lägre enhetsversion. |
| Enheten kan inte registreras som privat | Administratören har konfigurerat en registreringsbegränsning för att blockera privata registreringar och enheten som misslyckades var inte fördefinierad som företagsenhet. |
| Enhetsplattform har blockerats | Administratören har konfigurerat en registreringsbegränsning som blockerar den här enhetens plattform. |
| Masstoken har upphört att gälla | Masstoken i konfigurationspaketet har upphört att gälla. |
| Autopilot-enheten eller informationen hittades inte | Autopilot-enheten hittades inte vid försök till registrering. |
| Autopilot-profilen hittades inte eller har inte tilldelats | Enheten har ingen aktiv Autopilot-profil. |
| Oväntad registreringsmetod för Autopilot | Enheten försökte registrera med en otillåten metod. |
| Autopilot-enheten har tagits bort | Enheten som försökte registrera har tagits bort från Autopilot för det här kontot. |
| Enhetstaket har nåtts | Registreringen blockerades på grund av att en administratör har konfigurerat enhetsbegränsningar. |
| Apple-registrering | Inga iOS-enheter registrerades vid detta tillfälle eftersom ett Apple MDM-pushcertifikat i Intune saknas eller har upphört att gälla. |
| Enheten har inte förregistrerats | Enheten har inte förregistrerats som företagsägd och alla personliga registreringar blockerades av en administratör. |
| Funktionen stöds inte | Användaren försökte antagligen registrera via en metod som inte är kompatibel med din Intune-konfiguration. |

## <a name="collect-available-data-from-mobile-device"></a>Samla in tillgängliga data från mobil enhet

Använd följande resurser för att samla in enhetsdata när du felsöker problem med användarens enheter:
  - [Skicka iOS-registreringsfel till IT-administratören](/intune-user-help/send-errors-to-your-it-admin-ios)
  - [Hjälp företagets support att åtgärda enhetsproblem med hjälp av utförlig loggning](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)
  - [Skicka Android-loggar till företagets support via en USB-kabel](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Skicka loggar med Android-diagnostikdata till IT-administratören via e-post](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
  - [Skicka Android-registreringsfel till IT-administratören](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>Nästa steg

Du kan läsa mer om rollbaserad administrationskontroll (RBAC) för att definiera roller till organisationens enheter, hantering av mobilprogram och dataskyddsåtgärder. Mer information finns i [Rollbaserad administrationskontroll (RBAC) med Intune](/intune/role-based-access-control).

Lär dig om kända problem i Microsoft Intune. Mer information finns i [Kända problem i Microsoft Intune](/intune/known-issues).

Lär dig hur du skapar ett supportärende och får hjälp när du behöver det. [Få support](/intune/get-support).
