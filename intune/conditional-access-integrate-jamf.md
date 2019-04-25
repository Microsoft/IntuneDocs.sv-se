---
title: Integrera Jamf Pro med Microsoft Intune för kompatibilitet
titleSuffix: Microsoft Intune
description: Använd Microsoft Intunes efterlevnadsprinciper med Azure Active Directorys villkorliga åtkomst för att skydda Jamf-hanterade enheter.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57527d0b1825d0e8d3fefb63d1b960ab3fb5c676
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508132"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrera Jamf Pro med Intune för kompatibilitet

Gäller för: Intune i Azure Portal

Om din organisation använder [Jamf Pro](https://www.jamf.com) för att hantera dina slutanvändares Mac-datorer, kan du använda Microsoft Intunes efterlevnadsprinciper med villkorlig åtkomst i Azure Active Directory för att se till att enheter inom din organisation är kompatibla.

## <a name="prerequisites"></a>Krav

Du behöver följande för att konfigurera villkorlig åtkomst med Jamf Pro:

- Jamf Pro 10.1.0 eller senare
- [Företagsportalappen för macOS](https://aka.ms/macoscompanyportal)
- macOS-enheter med OS X 10.11 Yosemite eller senare

## <a name="connecting-intune-to-jamf-pro"></a>Anslut Intune till Jamf Pro

Du ansluter Intune till Jamf Pro så här:

1. Skapa ett nytt program i Azure
2. Låt Intune integreras med Jamf Pro
3. Konfigurera villkorlig åtkomst i Jamf Pro

## <a name="create-an-application-in-azure-active-directory"></a>Skapa ett program i Azure Active Directory

1. På [Azure-portalen](https://portal.azure.com) går du till **Azure Active Directory** > **Appregistreringar**.
2. Välj **+Ny programregistrering**.
3. Ange ett **visningsnamn**, som **Jamf villkorlig åtkomst**.
4. Välj **webbapp / API**.
5. Ange **inloggnings-URL** med URL:en för din Jamf Pro-instans.
6. Välj **Skapa**. Programmet skapas och programinformationen visas på portalen.
7. Spara en kopia av **program-ID** för det nya programmet. Du anger detta ID i en senare procedur. Välj sedan **Inställningar** och gå till **API-åtkomst** > **Nycklar**.
8. I fönstret *Nycklar* anger du en **Beskrivning**, hur lång tid som ska passera innan den **Förfaller** och väljer sedan **Spara** för att skapa programnyckeln (värde).

   > [!IMPORTANT]
   > Programnyckeln visas bara en gång under den här processen. Glöm inte att spara den någonstans där du enkelt kan hämta den.

8. I fönstret *Inställningar* för appen går du till **API-åtkomst** > **Nödvändiga behörigheter**. Markera eventuella befintliga behörigheter och klicka sedan på **Ta bort** och ta bort alla behörigheter. Du måste ta bort befintliga behörigheter när du lägger till en ny behörighet, och programmet fungerar bara om det har den enskilda nödvändiga behörigheten.  
9. Om du vill tilldela en ny behörighet väljer du **+Lägg till** > **Välj en API** > **Microsoft Intune API** och klickar sedan på **Välj**.
10. I fönstret *Aktivera åtkomst* väljer du **Skicka enhetsattribut till Microsoft Intune**, klickar på **Välj** och sedan på **Klar**.
11. I fönstret *Nödvändiga behörigheter* väljer du **Bevilja behörigheter** och sedan **Ja** för att tillämpa nödvändiga behörigheter i programmet.

    > [!NOTE]
    > Om programnyckeln upphör att gälla, måste du skapa en ny programnyckel i Microsoft Azure och uppdatera data för villkorlig åtkomst i Jamf Pro. Azure låter dig ha både den gamla och nya nyckeln aktiv för att förhindra tjänsteavbrott.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Låt Intune integreras med Jamf Pro

1. På [Azure-portalen](https://portal.azure.com) går du till **Microsoft Intune** > **Enhetsefterlevnad** > **	Enhetshantering för partner**.
2. Aktivera Compliance Connector för Jamf genom att klistra in det program-ID du sparade under föregående procedur i fältet **Jamf Azure Active Directory App-ID**.
3. Välj **Spara**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Konfigurera Microsoft Intune-integrering i Jamf Pro

1. I Jamf Pro, går du till **global hantering** > **villkorlig åtkomst**. Klicka på knappen **Redigera** på fliken **Microsoft Intune-integrering**.
2. Klicka i kryssrutan **Aktivera Microsoft Intune-integrering**.
3. Ange nödvändig information om din Azure-klient, inklusive **plats**, **domännamn** och den **program-ID** och **programnyckel** du sparade från föregående steg.
4. Välj **Spara**. Jamf Pro testar dina inställningar och verifierar att det fungerar.

## <a name="set-up-compliance-policies-and-register-devices"></a>Ställ in efterlevnadsprinciper och registrera enheter

När du har konfigurerat integrationen mellan Intune och Jamf måste du [tillämpa efterlevnadsprinciper för enheter som hanteras av Jamf](conditional-access-assign-jamf.md).



## <a name="next-steps"></a>Nästa steg

- [Tillämpa efterlevnadsprinciper för Jamf-hanterade enheter](conditional-access-assign-jamf.md)
- [Data som Jamf skickar till Intune](data-jamf-sends-to-intune.md)
