---
title: "Supportavdelningens felsökningsportal | Microsoft Docs"
titlesuffix: Azure portal
description: "Supportavdelningen använder felsökningsportalen till att lösa användarnas tekniska problem"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 09/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: f5678752830e2c4c9afbe75c9c6891d525eec34a
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/20/2017
---
# <a name="use-the-troubleshooting-portal-to-help-users"></a>Använd felsökningsportalen för att hjälpa användare

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I felsökningsportalen kan supportansvariga och Intune-administratörer se användarinformation för att tillgodose användarnas begäran om hjälp. Organisationer som har en supportavdelning kan tilldela rollen **supportavdelning** till en grupp användare. Rollen som supportansvarig kan nu använda **felsökningsbladet**.

Anvisningar om att lägga till rollen supportansvarig finns i [Rollbaserad administrationskontroll (RBAC) med Intune](/intune/role-based-access-control)

När en användare kontaktar supporten om ett tekniskt problem i Intune kan supportansvarig ange användarens namn. Intune visar användbara data som kan hjälpa dig att lösa många nivå 1-problem, inklusive:

- Användarstatus
- Tilldelningar
- Efterlevnadsproblem
- Enheten svarar inte
- Enheten saknar VPN- eller Wi-Fi-inställningar
- Appinstallationsfel

## <a name="to-review-troubleshooting-details"></a>Granska information om felsökning

På felsökningsbladet kan du välja **Välj användare** för att visa information om en användare. Med hjälp av användarinformation kan du få en bättre förståelse för det aktuella tillståndet för användarna och deras enheter.  

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Felsök** på bladet **Intune**.
4. Klicka på **Välj användare**.
5. Välj en användare genom att skriva namnet eller e-postadressen. Klicka på **Välj**. Felsökningsinformationen för användaren visas på bladet Felsökning. I följande tabeller förklaras informationen.

> [!Note]  
> Du kan också få åtkomst till **felsökningsbladet** genom att gå till: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="areas-of-troubleshooting-dashboard"></a>Områden för felsökning av instrumentpanelen

Du kan använda bladet **Felsökning** för att granska användarinformation. 

![](/intune/media/troubleshooting-dash.png)

| Område | Namn | Beskrivning |
| ---  | ---  | ---         |
| 1.   | Kontostatus  | Visar status för aktuell Intune-klient som **Aktiv** eller **Inaktiv**.       |
| 2.   | Val av användare  | Namnet på den valda användaren. Välj en ny användare genom att klicka på **Ändra användare**.       |
| 3.   | Användarstatus  | Visar status för användarens Intune-licens, antal enheter, varje enhetskompatibilitet, antalet appar och appkompatibilitet.       |
| 4.   | Användarinformation  | Använd listan för att välja information som du vill läsa på bladet. <br>Du kan välja: <ul><li>Mobilappar<li>Appskyddsprinciper<li>Efterlevnadsprinciper<li> Konfigurationsprinciper</ul>      |
| 5.   | Gruppmedlemskap  | Yadda       |

## <a name="mobile-apps-reference"></a>Referens för mobila appar

Appar som körs på enheter eller enheter som ägs av användare som hanteras av Intune och Azure Active Directory (AD).

### <a name="properties"></a>Enheter

Egenskaper för mobilappar.

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
| Äganderätt          | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**.                                               |
| Kompatibel med Intune   | Namnet på enhetstypen.                                                                                                     |
| Kompatibel med Azure AD | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Operativsystem                 | Operativsystemet som är installerat på enheten.                                                                                       |
| OS-version         | Enhetens operativsystemversionsnummer.                                                                                  |
| Senaste incheckning      | Namnet på enhetstypen.                                                                                                     |

### <a name="app-protection-status"></a>Appskyddsstatus

En appskyddsprincip är tillgänglig för mobilappar som integreras med EMS-teknik (Enterprise Mobility Solution). Detta ger en baslinje för skydd för företagets data när de laddas ned till mobila appar, inklusive Office-mobilappar. 

| Egenskap    | Beskrivning                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**. |
| Appnamn    | Namnet på programmet                                                           |
| Enhetsnamn | Namnet på enhetstypen.                                                       |
| Enhetstyp | Namnet på enhetstypen.                                                       |
| Policys    | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**. |
| Senaste synkronisering   | Tidsstämpel för den senaste gången enheten synkroniserades med Intune.                   |

## <a name="app-protection-policies-reference"></a>Appskyddsprinciper för referens

En appskyddsprincip är tillgänglig för mobilappar som integreras med EMS-teknik. Detta ger en baslinje för skydd för företagets data när de laddas ned till mobila appar, inklusive Office-mobilappar. 

### <a name="properties"></a>Enheter

I tabellen sammanfattas appskyddsprincipernas status för enheter som hanteras av Intune.

| Egenskap    | Beskrivning                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Namn        | Namnet på programmet.                                                                                                        |
| Distribuerad    | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Plattform    | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**.                                               |
| Registrering  | Namnet på enhetstypen.                                                                                                     |
| Senaste uppdateringen | Tidsstämpelprincipen har ändrats.                                                                                              |

### <a name="devices"></a>Egenskaper

Enheter som hanteras av Intune eller av användare som hanteras av Intune eller Azure AD.

| Egenskap           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Enhetsnamn        | Namnet på enhetstypen.                                                                                                     |
| Hanteras av         | Tidsstämpelprincipen har ändrats.                                                                                              |
| Azure AD-anslutningstyp | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Äganderätt          | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**.                                               |
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
| Principtyp   | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**.                                               |
| Senast ändrad | Namnet på enhetstypen.                                                                                                     |

### <a name="devices"></a>Egenskaper

Enheter som hanteras av Intune eller av användare som hanteras av Intune eller Azure AD.

| Egenskap           | Beskrivning                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Enhetsnamn        | Namnet på enhetstypen.                                                                                                     |
| Hanteras av         | Tidsstämpelprincipen har ändrats.                                                                                              |
| Azure AD-anslutningstyp | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Äganderätt          | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**.                                               |
| Kompatibel med Intune   | Namnet på enhetstypen.                                                                                                     |
| Kompatibel med Azure AD | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Operativsystem                 | Operativsystemet som är installerat på enheten.                                                                                       |
| OS-version         | Enhetens operativsystemversionsnummer.                                                                                  |
| Senaste incheckning      | Namnet på enhetstypen.                                                                                                     |

### <a name="app-protection-policies"></a>Appskyddsprinciper

En appskyddsprincip är tillgänglig för mobilappar som integreras med EMS-teknik. Detta ger en baslinje för skydd för företagets data när de laddas ned till mobila appar, inklusive Office-mobilappar. 

| Egenskap    | Beskrivning                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**. |
| Appnamn    | Namnet på programmet                                                           |
| Enhetsnamn | Namnet på enhetstypen.                                                       |
| Enhetstyp | Namnet på enhetstypen.                                                       |
| Policys    | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**. |
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
| Principtyp   | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**.                                               |
| Senast ändrad | Namnet på enhetstypen.                                                                                                     |

### <a name="devices"></a>Egenskaper

Enheter som hanteras av Intune eller av användare som hanteras av Intune eller Azure AD.

| Egenskap           | Beskrivning                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Enhetsnamn        | Namnet på enhetstypen.                                                                                                     |
| Hanteras av         | Tidsstämpelprincipen har ändrats.                                                                                              |
| Azure AD-anslutningstyp | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Äganderätt          | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**.                                               |
| Kompatibel med Intune   | Namnet på enhetstypen.                                                                                                     |
| Kompatibel med Azure AD | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Operativsystem                 | Operativsystemet som är installerat på enheten.                                                                                       |
| OS-version         | Enhetens operativsystemversionsnummer.                                                                                  |
| Senaste incheckning      | Namnet på enhetstypen.                                                                                                     |


### <a name="app-protection-policies"></a>Appskyddsprinciper

En appskyddsprincip är tillgänglig för mobilappar som integreras med EMS-teknik. Detta ger en baslinje för skydd för företagets data när de laddas ned till mobila appar, inklusive Office-mobilappar. 

| Egenskap    | Beskrivning                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**. |
| Appnamn    | Namnet på programmet                                                           |
| Enhetsnamn | Namnet på enhetstypen.                                                       |
| Enhetstyp | Namnet på enhetstypen.                                                       |
| Policys    | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**. |
| Senaste synkronisering   | Tidsstämpel för den senaste gången enheten synkroniserades med Intune.                   |

## <a name="next-steps"></a>Nästa steg

Du kan läsa mer om rollbaserad administrationskontroll (RBAC) för att definiera roller till organisationens enheter, hantering av mobilprogram och dataskyddsåtgärder. Mer information finns i [Rollbaserad administrationskontroll (RBAC) med Intune](/intune/role-based-access-control).

Lär dig om kända problem i Microsoft Intune. Mer information finns i [Kända problem i Microsoft Intune](/intune/known-issues).

Lär dig hur du skapar ett supportärende och får hjälp när du behöver det. [Få support](/intune/get-support).