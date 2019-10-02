---
title: Integrera Jamf Pro med Microsoft Intune för kompatibilitet
titleSuffix: Microsoft Intune
description: Använd Microsoft Intunes efterlevnadsprinciper med Azure Active Directorys villkorliga åtkomst för att skydda Jamf-hanterade enheter.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b439067d06cf49a4ff83288e109d1fccd3801106
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722728"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrera Jamf Pro med Intune för kompatibilitet

Gäller för: Intune i Azure Portal

Om din organisation använder [Jamf Pro](https://www.jamf.com) för att hantera dina slutanvändares Mac-datorer, kan du använda Microsoft Intunes efterlevnadsprinciper med villkorlig åtkomst i Azure Active Directory för att se till att enheter inom din organisation är kompatibla.

## <a name="prerequisites"></a>Krav

Du behöver följande för att konfigurera villkorlig åtkomst med Jamf Pro:

- Jamf Pro 10.1.0 eller senare
- [Företagsportalappen för macOS](https://aka.ms/macoscompanyportal)
- macOS-enheter med OS X 10.11 Yosemite eller senare

## <a name="connect-intune-to-jamf-pro"></a>Ansluta Intune till Jamf Pro

Så här ansluter du Intune till Jamf Pro:

1. Skapa ett nytt program i Azure.
2. Låt Intune integreras med Jamf Pro.
3. Konfigurera villkorlig åtkomst i Jamf Pro.

## <a name="create-an-application-in-azure-active-directory"></a>Skapa ett program i Azure Active Directory

1. På [Azure-portalen](https://portal.azure.com) går du till **Azure Active Directory** > **Appregistreringar** och väljer sedan **Ny registrering**. 

2. På sidan **Registrera ett program** anger du följande information:
   - I avsnittet **Namn** anger du ett beskrivande namn, till exempel **Jamf villkorlig åtkomst**.
   - I avsnittet **Kontotyper som stöds** väljer du **Konton i valfri organisationskatalog**. 
   - Som **Omdirigerings-URI** lämnar du standardinställningen Web och anger sedan inloggnings-URL: en till din instans av Jamf Pro.  

3. Välj **Registrera** för att skapa programmet och öppna sidan **Översikt** för den nya appen.  

4. På appsidan **Översikt** kopierar du värdet **Program-ID (klient)** och sparar det till senare. Du behöver det här värdet senare.  

5. Välj **Certifikat och hemligheter** under **Hantera**. Klicka på knappen **Ny klienthemlighet**. Ange ett värde i **Beskrivning**, välj ett alternativ för **Förfaller** och välj **Lägg till**.

   > [!IMPORTANT]  
   > Innan du lämnar den här sidan ska du kopiera värdet för klienthemligheten och spara det till senare. Du behöver det här värdet senare. Det här värdet visas inte igen, om man inte återskapar appregistreringen.  

6. Välj **API-behörigheter** under **Hantera**. Välj de befintliga behörigheterna och välj sedan **Ta bort behörighet** för att ta bort dessa behörigheter. Du måste ta bort alla befintliga behörigheter när du lägger till en ny behörighet och programmet fungerar bara om det har den enskilda nödvändiga behörigheten.  

7. Om du vill tilldela en ny behörighetsuppsättning väljer du **Lägg till en behörighet**. På sidan **Begär API-behörigheter** väljer du **Intune** och väljer sedan **Programbehörigheter**. Markera enbart kryssrutan för **update_device_attributes**.  

   Välj **Lägg till behörighet** för att spara konfigurationen.  

8. På sidan **API-behörigheter** väljer du **Bevilja administratörens godkännande för Microsoft** och väljer sedan **Ja**.  

   Registreringsprocessen i Azure AD har slutförts.


    > [!NOTE]
    > Om klienthemligheten upphör att gälla måste du skapa en ny klienthemlighet i Microsoft Azure och uppdatera data för villkorlig åtkomst i Jamf Pro. Azure låter dig ha både den gamla och nya hemligheten aktiv för att förhindra tjänsteavbrott.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Låt Intune integreras med Jamf Pro

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och gå till **Microsoft Intune** > **Enhetsefterlevnad** > **Enhetshantering för partner**.

2. Aktivera Compliance Connector för Jamf genom att klistra in det program-ID du sparade under föregående procedur i fältet **Jamf Azure Active Directory App-ID**.

3. Välj **Spara**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Konfigurera Microsoft Intune-integrering i Jamf Pro

1. I Jamf Pro, går du till **global hantering** > **villkorlig åtkomst**. Klicka på knappen **Edit** (Redigera) på fliken **macOS Intune Integration** (Intune-integrering för macOS).

2. Markera kryssrutan **Aktivera Intune-integrering för macOS**.

3. Ange nödvändig information om din Azure-klient, inklusive **Plats**, **Domännamn**, **Program-ID** och värdet för den *klienthemlighet* som du sparade när du skapade appen i Azure AD.  

4. Välj **Spara**. Jamf Pro testar dina inställningar och verifierar att det fungerar.

## <a name="set-up-compliance-policies-and-register-devices"></a>Ställ in efterlevnadsprinciper och registrera enheter

När du har konfigurerat integrationen mellan Intune och Jamf måste du [tillämpa efterlevnadsprinciper för enheter som hanteras av Jamf](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Koppla från Jamf Pro och Intune 

Om du inte längre använder Jamf Pro för att hantera Mac-enheter i organisationen och vill att användarna ska hanteras av Intune måste du ta bort anslutningen mellan Jamf Pro och Intune. Ta bort anslutningen med hjälp av Jamf Pro-konsolen. 

1. I Jamf Pro går du till **Global Management** > **Conditional Access** (Global hantering > Villkorlig åtkomst). På fliken **macOS Intune Integration** (Intune-integrering för macOS) väljer du **Edit** (Redigera).
2. Avmarkera kryssrutan **Enable Intune Integration for macOS** (Aktivera Intune-integrering för macOS).
3. Välj **Spara**. Jamf Pro skickar din bekräftelse till Intune och integreringen avslutas.
4. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Gå till **Microsoft Intune** > **Enhetsefterlevnad** > **Enhetshantering för partner** för att verifiera att statusen nu är **Avslutad**. 

   > [!NOTE]
   > Organisationens Mac-enheter tas bort på datumet (3 månader) som visas i konsolen. 

## <a name="next-steps"></a>Nästa steg

- [Tillämpa efterlevnadsprinciper för Jamf-hanterade enheter](conditional-access-assign-jamf.md)
- [Data som Jamf skickar till Intune](data-jamf-sends-to-intune.md)
