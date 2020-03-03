---
title: Integrera Jamf Pro med Microsoft Intune för kompatibilitet
titleSuffix: Microsoft Intune
description: Använd Microsoft Intunes efterlevnadsprinciper med Azure Active Directorys villkorsstyrda åtkomst för att integrera och skydda Jamf-hanterade enheter.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9dab1025e283ed1591c22b03ed4e3a61d40a20c3
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515092"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrera Jamf Pro med Intune för kompatibilitet

Om din organisation använder [Jamf Pro](https://www.jamf.com) för att hantera macOS-enheter, kan du använda Microsoft Intune-efterlevnadsprinciper med villkorsstyrd åtkomst i Azure AD (Azure Active Directory) för att kontrollera att enheterna i organisationen är kompatibla innan de får åtkomst till företagets resurser. Den här artikeln beskriver hur du konfigurerar Jamf-integrering med Intune.

När Jamf Pro integreras med Intune kan du synkronisera inventeringsdata från macOS-enheter med Intune via Azure AD. Intunes efterlevnadsmotor analyserar sedan inventeringsdata för att generera en rapport. Intunes analys kombineras med information om enhetsanvändarens Azure AD-identitet för att kräva efterlevnad med villkorlig åtkomst. Enheter som är kompatibla med principerna för villkorlig åtkomst kan få åtkomst till skyddade företagsresurser.

När du har konfigurerat integrationen [konfigurerar du Jamf och Intune för att kräva efterlevnad med villkorlig åtkomst](conditional-access-assign-jamf.md) på enheter som hanteras av Jamf.

## <a name="prerequisites"></a>Krav

### <a name="products-and-services"></a>Produkter och tjänster

Du behöver följande för att konfigurera villkorlig åtkomst med Jamf Pro:

- Jamf Pro 10.1.0 eller senare
- [Företagsportalappen för macOS](https://aka.ms/macoscompanyportal)
- macOS-enheter med OS X 10.12 Yosemite eller senare

### <a name="network-ports"></a>Nätverksportar

<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
Följande portar måste vara tillgängliga för att Jamf och Intune ska kunna integreras korrekt:

- **Intune**: Port 443
- **Apple**: Portarna 2195, 2196 och 5223 (push-meddelanden till Intune)
- **Jamf**: Portarna 80 och 5223

För att APN ska fungera korrekt i nätverket måste du även aktivera utgående anslutningar till och omdirigerar från:

- Apple 17.0.0.0/8-blocket över TCP-portarna 5223 och 443 från alla klientnätverk.
- portarna 2195 och 2196 från Jamf Pro-servrar.  

Mer information om dessa portar finns i följande artiklar:

- [Krav för Intune-nätverkskonfiguration och bandbredd](../fundamentals/network-bandwidth-use.md).
- [Nätverksportar som används av Jamf Pro](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro) på jamf.com.
- [TCP- och UDP-portar som används av Apples programvaruprodukter](https://support.apple.com/HT202944) på support.apple.com

## <a name="connect-intune-to-jamf-pro"></a>Ansluta Intune till Jamf Pro

Så här ansluter du Intune till Jamf Pro:

1. Skapa ett nytt program i Azure.
2. Låt Intune integreras med Jamf Pro.
3. Konfigurera villkorlig åtkomst i Jamf Pro.

### <a name="create-an-application-in-azure-active-directory"></a>Skapa ett program i Azure Active Directory

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

6. Välj **API-behörigheter** under **Hantera**. 

7. På sidan API-behörigheter tar du bort alla behörigheter från den här appen genom att välja ikonen **...** bredvid varje befintlig behörighet. Observera att detta är obligatoriskt. Integreringen misslyckas om det finns oväntade extra behörigheter i den här appregistreringen.

8. Nu ska vi lägga till behörigheter för att uppdatera enhetsattribut. Längst upp till vänster på sidan **API-behörigheter** väljer du **Lägg till en behörighet** för att lägga till en ny behörighet. 

9. På sidan **Begär API-behörigheter** väljer du **Intune** och väljer sedan **Programbehörigheter**. Markera enbart kryssrutan för **update_device_attributes** och spara den nya behörigheten.

10. Bevilja sedan administratörsgodkännande för den här appen genom att välja **Bevilja administratörsgodkännande för _\<din klientorganisation>_** längst upp till vänster på sidan **API-behörigheter**. Du kan behöva autentisera ditt konto i det nya fönstret och ge programmet åtkomst genom att följa instruktionerna.  

11. Uppdatera genom att klicka på knappen **Uppdatera** överst på sidan. Kontrollera att ett administratörsmedgivande har beviljats för behörigheten **update_device_attributes**. 

12. När appen har registrerats ska API-behörigheterna bara innehålla en behörighet med namnet **update_device_attributes** och bör visas på följande sätt:

   ![Lyckade behörigheter](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   Registreringsprocessen i Azure AD har slutförts.

    > [!NOTE]
    > Om klienthemligheten upphör att gälla måste du skapa en ny klienthemlighet i Microsoft Azure och uppdatera data för villkorlig åtkomst i Jamf Pro. Azure låter dig ha både den gamla och nya hemligheten aktiv för att förhindra tjänsteavbrott.

### <a name="enable-intune-to-integrate-with-jamf-pro"></a>Låt Intune integreras med Jamf Pro

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Innehavaradministratör** > **Anslutningar och token** > **Hantering av partnerenhet**.

3. Aktivera *Compliance Connector för Jamf* genom att klistra in det program-ID som du sparade under föregående procedur i fältet **Ange Azure Active Directory App-ID för Jamf**.

4. Välj **Spara**.

### <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Konfigurera Microsoft Intune-integrering i Jamf Pro

1. Aktivera anslutningen i Jamf Pro-konsolen:

   1. Öppna Jamf Pro-konsolen och gå till **Global hantering** > **Villkorlig åtkomst**. Klicka på knappen **Edit** (Redigera) på fliken **macOS Intune Integration** (Intune-integrering för macOS).
   2. Markera kryssrutan **Aktivera Intune-integrering för macOS**.
   3. Ange nödvändig information om din Azure-klient, inklusive **Plats**, **Domännamn**, **Program-ID** och värdet för den *klienthemlighet* som du sparade när du skapade appen i Azure AD.
   4. Välj **Spara**. Jamf Pro testar dina inställningar och verifierar att det fungerar.

   Gå tillbaka till sidan **Enhetshantering för partner** i Intune för att slutföra konfigurationen.

2. I Intune går du till sidan **Enhetshantering för partner**. Under **Anslutningsappinställningar** konfigurerar du grupper för tilldelningen:

   - Välj **Inkludera** och ange vilka användargrupper som är målet för macOS-registreringen med Jamf.
   - Använd **Exkludera** för att välja de användargrupper som inte ska registreras med Jamf utan i stället registrera sina Mac-enheter direkt med Intune.

   *Exkludera* åsidosätter *Inkludera*, vilket innebär att enheter som finns i båda grupperna undantas från Jamf och dirigeras till registrering med Intune.

   >[!NOTE]
   > Den här metoden för att inkludera och exkludera användargrupper påverkar användarens registreringsupplevelse. Alla användare med en Mac som redan har registrerats i antingen Jamf eller Intune och som sedan dirigeras till att registreras hos den andra MDM:en, måste avregistrera sin enhet och sedan registrera den igen med den nya MDM:en innan hanteringen av enheten fungerar korrekt.

3. Välj **Utvärdera** för att se hur många enheter som ska registreras med Jamf, baserat på dina gruppkonfigurationer.

4. Välj **Spara** när du är redo att tillämpa konfigurationen.

5. Om du vill fortsätta måste du använda [Jamf till att distribuera företagsportalen för Mac](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) så att användarna kan registrera sina enheter i Intune.

## <a name="set-up-compliance-policies-and-register-devices"></a>Ställ in efterlevnadsprinciper och registrera enheter

När du har konfigurerat integrationen mellan Intune och Jamf måste du [tillämpa efterlevnadsprinciper för enheter som hanteras av Jamf](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Koppla från Jamf Pro och Intune

Om du inte längre använder Jamf Pro för att hantera Mac-enheter i organisationen och vill att användarna ska hanteras av Intune måste du ta bort anslutningen mellan Jamf Pro och Intune. Ta bort anslutningen med hjälp av Jamf Pro-konsolen.

1. I Jamf Pro går du till **Global Management** > **Conditional Access** (Global hantering > Villkorlig åtkomst). På fliken **macOS Intune Integration** (Intune-integrering för macOS) väljer du **Edit** (Redigera).

2. Avmarkera kryssrutan **Enable Intune Integration for macOS** (Aktivera Intune-integrering för macOS).

3. Välj **Spara**. Jamf Pro skickar din bekräftelse till Intune och integreringen avslutas.

4. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

5. Välj **Innehavaradministratör** > **Anslutningar och token** > **Hantering av partnerenhet** för att verifiera att statusen är **avslutad**.

   > [!NOTE]
   > Organisationens Mac-enheter tas bort på datumet (3 månader) som visas i konsolen.

## <a name="next-steps"></a>Nästa steg

- [Tillämpa efterlevnadsprinciper för Jamf-hanterade enheter](conditional-access-assign-jamf.md)
- [Data som Jamf skickar till Intune](data-jamf-sends-to-intune.md)
