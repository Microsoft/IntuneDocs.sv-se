---
title: "Integrera Jamf Pro med Microsoft Intune för kompatibilitet"
titlesuffix: 
description: "Använd Microsoft Intunes efterlevnadsprinciper med Azure Active Directorys villkorliga åtkomst för att skydda Jamf-hanterade enheter."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 01/04/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f4b040c6aa7001e8ebdd7c05571276428c7ef9bd
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrera Jamf Pro med Intune för kompatibilitet

|Gäller för: Intune på Azure Portal |
|--|
|Letar du efter dokumentation om Intune på den klassiska portalen? [Gå hit](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

Om din organisation använder [Jamf Pro](https://www.jamf.com) för att hantera dina slutanvändares Mac-datorer, kan du använda Microsoft Intunes efterlevnadsprinciper med villkorlig åtkomst i Azure Active Directory för att se till att enheter inom din organisation är kompatibla.

## <a name="prerequisites"></a>Nödvändiga komponenter

Du behöver följande för att konfigurera villkorlig åtkomst med Jamf Pro:

- Jamf Pro 10.1.0 eller senare
- [Företagsportalappen för macOS](https://aka.ms/macoscompanyportal)
- macOS-enheter med OS X 10.11 Yosemite eller senare

## <a name="connecting-intune-to-jamf-pro"></a>Anslut Intune till Jamf Pro

Du kan ansluta Intune till Jamf Pro genom att:

1. Skapa ett nytt program i Azure
2. Låta Intune integreras med Jamf Pro
3. Konfigurera villkorlig åtkomst i Jamf Pro

## <a name="create-a-new-application-in-azure-active-directory"></a>Skapa ett nytt program i Azure Active Directory

1. Öppna **Azure Active Directory** > **Appregistreringar**.
2. Klicka på **+Ny programregistrering**.
3. Ange ett **visningsnamn**, som **Jamf villkorlig åtkomst**.
4. Välj **webbapp / API**.
5. Ange **inloggnings-URL** med URL:en för din Jamf Pro-instans.
6. Klicka på **skapa program**.
7. Spara det nyligen skapade **Program-ID:t**, öppna sedan **Inställningar** och gå till **API-åtkomst** > **Nycklar** för att skapa en ny programnyckel. Ange en **beskrivning** och hur lång tid som ska passera innan den **Förfaller**. Spara sedan programnyckeln.

  > [!IMPORTANT]
  > Programnyckeln visas bara en gång under den här processen. Glöm inte att spara den någonstans där du enkelt kan hämta den.

8. Öppna **Inställningar** och gå till **API-åtkomst** > **Nödvändiga behörigheter** och ta bort alla behörigheter.

  > [!NOTE]
  > Lägg till en ny nödvändig behörighet. Programmet kan endast fungera korrekt om det har den enda nödvändiga behörigheten.

9.  Välj **Microsoft Intune API** och klicka på **välj**.
10. Välj **skicka enhetsattribut till Microsoft Intune** och klicka på **välj**.
11. Klicka på knappen **bevilja behörighet** när du har sparat de nödvändiga behörigheterna för programmet.

  > [!NOTE]
  > Om programnyckeln upphör att gälla, måste du skapa en ny programnyckel i Microsoft Azure och uppdatera data för villkorlig åtkomst i Jamf Pro. Azure låter dig ha både den gamla och nya nyckeln aktiv för att förhindra tjänsteavbrott.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Låt Intune integreras med Jamf Pro

1. I Microsoft Azure Portal öppnar du **Microsoft Intune** > **enhetskompatibilitet** > **Enhetshantering för partner**.
2. Aktivera Compliance Connector för Jamf genom att klistra in program-ID i fältet **Jamf Azure Active Directory App-ID**.
3. Klicka på **Spara**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Konfigurera Microsoft Intune-integrering i Jamf Pro

1. I Jamf Pro, går du till **global hantering** > **villkorlig åtkomst**. Klicka på knappen **Redigera** på fliken **Microsoft Intune-integrering**.
2. Klicka i kryssrutan **Aktivera Microsoft Intune-integrering**.
3. Ange nödvändig information om din Azure-klient, inklusive **plats**, **domännamn** och den **program-ID** och **programnyckel** du sparade från föregående steg.
4. Klicka på **Spara**. Jamf Pro testar dina inställningar och verifierar att det fungerar.

## <a name="set-up-compliance-policies-and-register-devices"></a>Ställ in efterlevnadsprinciper och registrera enheter

När du har konfigurerat integrationen mellan Intune och Jamf måste du [applicera principer för efterlevnad för enheter som hanteras av Jamf](conditional-access-assign-jamf.md).

## <a name="information-shared-from-jamf-pro-to-intune"></a>Information som delas från Jamf Pro till Intune

Jamf Pro samlar in programvaruinventering om hanterade macOS-enheter. Jamf Pro rapporterar följande information till Intune:

* Enhetens Azure AD-ID
* JAMF-inventeringstillstånd (inventeringstillstånd på en dator som checkats in med Jamf Pro under de senaste 24 timmarna)
* OS-version
* Användarens Azure AD-ID
* Krypterade (FileVault 2)
* Gatekeeper-status
* Lösenord: lägst antal teckenuppsättningar
* Lösenordets giltighetstid (i dagar)
* Lösenordstyp – enkel, alfanumerisk eller okänd
* Förhindra automatisk inloggning
* Nödvändig längd på lösenord
* Lösenord: antalet tidigare lösenord för att förhindra återanvändning
* Systemintegritetsskydd
* Senaste incheckningstid
* Arkitekturtyp
* Tillgängliga RAM-minnesplatser
* Batterikapacitet
* Start-ROM
* Busshastighet
* Cachestorlek
* Enhetsnamn
* Domänanslutning
* Jamf-ID
* MAC-adress
* Tillverkning
* Modell
* Modellidentifierare
* NIC-hastighet
* Antal kärnor
* Antal processorer
* Operativsystem
* Plattform
* Processorhastighet
* Processortyp
* Sekundär MAC-adress
* Serienummer
* SMC-version
* RAM-minne totalt
* UDID
* Användarens e-post

## <a name="next-steps"></a>Nästa steg

- [Tillämpa efterlevnadsprinciper för Jamf-hanterade enheter](conditional-access-assign-jamf.md)
