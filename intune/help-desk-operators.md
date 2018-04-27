---
title: Supportavdelningens felsökningsportal
titlesuffix: Microsoft Intune
description: Supportavdelningen använder felsökningsportalen till att lösa användarnas tekniska problem.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 5d924e216dd6d0fe13bc4c7718b5368db1d35f8c
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
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
- Enheten kan inte
- Enheten saknar VPN- eller Wi-Fi-inställningar
- Appinstallationsfel

## <a name="to-review-troubleshooting-details"></a>Granska information om felsökning

I felsökningsfönstret kan du välja **Välj användare** för att visa information om en användare. Med hjälp av användarinformation kan du få en bättre förståelse för det aktuella tillståndet för användarna och deras enheter.  

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Felsök** i fönstret **Intune**.
4. Klicka på **Välj** för att välja en användare att felsöka.
5. Välj en användare genom att skriva namnet eller e-postadressen. Klicka på **Välj**. Felsökningsinformationen för användaren visas i fönstret Felsökning. I följande tabeller förklaras informationen.

> [!Note]  
> Du kan också få åtkomst till **felsökningsfönstret** genom att gå till: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="areas-of-troubleshooting-dashboard"></a>Områden för felsökning av instrumentpanelen

Du kan använda fönstret **Felsökning** för att granska användarinformation.

![](/intune/media/troubleshooting-dash.png)

| Område | Namn | Description |
| ---  | ---  | ---         |
| 1.   | Kontostatus  | Visar status för aktuell Intune-klient som **Aktiv** eller **Inaktiv**.       |
| 2.   | Val av användare  | Namnet på den valda användaren. Välj en ny användare genom att klicka på **Ändra användare**.       |
| 3.   | Användarstatus  | Visar status för användarens Intune-licens, antal enheter, varje enhetskompatibilitet, antalet appar och appkompatibilitet.       |
| 4.   | Användarinformation  | Använd listan för att välja information som du vill läsa i fönstret. <br>Du kan välja: <ul><li>Mobilappar<li>Appskyddsprinciper<li>Efterlevnadsprinciper<li> Konfigurationsprinciper</ul>      |
| 5.   | Gruppmedlemskap  | Yadda       |

## <a name="mobile-apps-reference"></a>Referens för mobila appar

Appar som körs på enheter eller enheter som ägs av användare som hanteras av Intune och Azure Active Directory (AD).

### <a name="properties"></a>Enheter

Egenskaper för mobilappar.

| Egenskap      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Namn          | Namnet på programmet.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Operativsystem            | Operativsystemet som är installerat på enheten.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Typ          | Du kan välja en tilldelningstyp för varje program.  <br> **Tillgänglig** – Användarna installerar appen från företagsportalappen eller webbplatsen.  <br> **Inte tillämpligt** – Appen varken installeras eller visas i företagsportalen. <br> **Avinstallera** – Appen avinstalleras från enheter i valda grupper.  <br> **Tillgänglig med eller utan registrering** – Tilldela den här appen till grupper av användare vars enheter inte har registrerats med Intune. |
| Senast ändrad | Namnet på enhetstypen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### <a name="devices"></a>Egenskaper

Enheter som hanteras av Intune eller av användare som hanteras av Intune eller Azure AD.

| Egenskap           | Description                                                                                                                         |
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

| Egenskap    | Description                                                                           |
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

| Egenskap    | Description                                                                                                                                |
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

| Egenskap      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Tilldelning    | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Namn          | Namnet på programmet.                                                                                                        |
| Operativsystem            | Operativsystemet som är installerat på enheten.                                                                                       |
| Principtyp   | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**.                                               |
| Senast ändrad | Namnet på enhetstypen.                                                                                                     |

### <a name="devices"></a>Egenskaper

Enheter som hanteras av Intune eller av användare som hanteras av Intune eller Azure AD.

| Egenskap           | Description                                                                                                                         |
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

| Egenskap    | Description                                                                           |
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

| Egenskap      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Tilldelning    | Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**. |
| Namn          | Namnet på programmet.                                                                                                        |
| Operativsystem            | Operativsystemet som är installerat på enheten.                                                                                       |
| Principtyp   | Typ av äganderätt till enheten. Det kan vara **Företag**, **Personlig** eller **Okänd**.                                               |
| Senast ändrad | Namnet på enhetstypen.                                                                                                     |

### <a name="devices"></a>Egenskaper

Enheter som hanteras av Intune eller av användare som hanteras av Intune eller Azure AD.

| Egenskap           | Description                                                                                                                         |
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

| Egenskap    | Description                                                                           |
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
