---
title: Inkompatibilitetsmeddelande och åtgärder med Microsoft Intune – Azure | Microsoft Docs
description: Skapa ett e-postmeddelande som ska skickas till inkompatibla enheter. Lägg till åtgärder när en enhet har markerats som inkompatibel, t.ex. en respitperiod för att bli kompatibel, eller skapa ett schema som blockerar åtkomst tills enheten är kompatibel. Gör detta med Microsoft Intune i Azure.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e3867bfc2de29c059766e134bd0d2c8801e1c70
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712905"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>Automatisera e-post och lägga till åtgärder för inkompatibla enheter i Intune

För enheter som inte uppfyller dina principer eller regler för efterlevnad kan du lägga till **åtgärder för inkompatibilitet**. Den här funktionen konfigurerar en tidssorterad sekvens med åtgärder, till exempel att skicka e-post till slutanvändaren och mer.

## <a name="overview"></a>Översikt

När Intune identifierar en enhet som inte är kompatibel, markerar Intune omedelbart enheten som inkompatibel som standard. Den [villkorliga åtkomsten](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) i Azure Active Directory (AD) blockerar sedan enheten. När en enhet inte är kompatibel kan du med **åtgärder för inkompatibilitet** få mer flexibilitet när du ska bestämma dig för vad du bör göra. Du kan t.ex. låta bli att blockera enheten omedelbart och ge användaren en respitperiod för att bli kompatibel.

Det finns flera typer av åtgärder:

- **Skicka e-post till slutanvändare**: Anpassa en e-postavisering innan den skickas till slutanvändaren. Du kan anpassa mottagare, ämne, brödtext, företagslogotyp och kontaktinformation.

    Dessutom inkluderar Intune information om den inkompatibla enheten i e-postmeddelandet.

- **Fjärrlåsa en icke-kompatibel enhet**: För enheter som inte är kompatibla kan du utfärda en fjärrlåsning. Användaren uppmanas i så fall att ange en PIN-kod eller ett lösenord för att låsa upp enheten. Mer om funktionen [Fjärrlåsning](../remote-actions/device-remote-lock.md).

- **Markera enhet som inkompatibel**: Skapa ett schema (med antal dagar) varefter enheten markeras som inkompatibel. Du kan konfigurera åtgärden till att börja gälla omedelbart, eller ge användaren en respitperiod för att bli kompatibel.

Den här artikeln visar hur du:

- Skapa en mall för meddelandeaviseringar
- Skapa en åtgärd för inkompatibilitet. Du kan till exempel skicka ett e-postmeddelande eller fjärrlåsa en enhet


## <a name="before-you-begin"></a>Innan du börjar

- Du måste ha minst en efterlevnadsprincip för enheter för att kunna konfigurera åtgärder vid inkompatibilitet. Se följande plattformar när du ska skapa en efterlevnadsprincip för enheter:

  - [Android](compliance-policy-create-android.md)
  - [Android-arbetsprofiler](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Du måste ha konfigurerat villkorlig Azure AD-åtkomst när du använder principer för enhetsefterlevnad till att blockera enheter från företagets resurser. Mer information finns i [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) eller [Vanliga sätt att använda villkorlig åtkomst med Intune](conditional-access-intune-common-ways-use.md).

## <a name="create-a-notification-message-template"></a>Skapa en mall för aviseringsmeddelanden

Om du vill skicka ett e-postmeddelande till användarna skapar du en mall för aviseringsmeddelanden. När en enhet är inkompatibel visas informationen som du anger i mallen i e-postmeddelandet som skickas till användarna.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Efterlevnadsprinciper** > **Meddelanden** > **Skapa meddelande**.
3. Ange följande information under *Grundläggande*:

   - **Namn**
   - **Ämne**
   - **Meddelande**

4. Under *Grundläggande* konfigurerar du även följande alternativ för meddelandet, som alla är *aktiverade* som standard:

   - **E-postsidhuvud – Infoga företagets logotyp**
   - **E-postsidfot – Infoga företagets namn**
   - **E-postsidfot – Infoga kontaktinformation**

   Den logotyp som du laddar upp som en del av varumärkesanpassningen av företagsportalen används för e-postmallar. Läs mer om varumärkesanpassning av företagsportalen i [Varumärkesanpassning för företagsidentitet](../apps/company-portal-app.md#company-identity-branding-customization).

   ![Exempel på ett kompatibelt aviseringsmeddelande i Intune](./media/actions-for-noncompliance/actionsfornoncompliance-1.PNG)

   Fortsätt genom att välja **Nästa**.

5. Under **Granska + skapa** granskar du dina konfigurationer för att säkerställa att meddelandemallen är redo att användas. Välj **Skapa** för att skapa meddelandet.

> [!NOTE]
> Du kan också välja en befintlig meddelandemall som du skapat tidigare och uppdatera den genom att **redigera** informationen i den.

## <a name="add-actions-for-noncompliance"></a>Lägga till åtgärder vid inkompatibilitet

När du skapar en princip för enhetsefterlevnad skapar Intune automatiskt en åtgärd för inkompatibilitet. Om en enhet inte uppfyller din efterlevnadsprincip markerar den här åtgärden enheten som inkompatibel. Du kan anpassa hur länge enheten ska markeras som inkompatibel. Det går inte att ta bort åtgärden.

Du kan också lägga till en till åtgärd när du skapar en princip för efterlevnad eller uppdatera en befintlig princip.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Efterlevnadsprinciper** > **Principer**, välj en av dina principer och välj sedan **Egenskaper**.

   Har du inte någon princip än? Skapa en princip för [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) eller någon annan plattform.

   > [!NOTE]
   > JAMF-enheter och enheter som är mål för enhetsgrupper kan inte ta emot efterlevnadsåtgärder just nu.

3. Välj **Åtgärder för inkompatibilitet** > **Lägg till**.

4. Välj din **åtgärd**:

   - **Skicka e-post till slutanvändare**: Välj att skicka ett e-postmeddelande till användaren om enheten inte är kompatibel. Du kan också:
     - Välj den **meddelandemall** som du skapade tidigare
     - Ange eventuella **ytterligare mottagare** genom att välja grupper

   - **Fjärrlåsa en icke-kompatibel enhet**: Lås enheten när den är inkompatibel. Den här åtgärden tvingar användaren att ange en PIN-kod eller ett lösenord för att låsa upp enheten.

5. Konfigurera ett **schema**: Ange hur många dagar (0 till 365) efter en inkompatibilitet som åtgärden ska utlösas på användarnas enheter. Efter den här respittiden kan du tillämpa en [princip för villkorlig åtkomst](conditional-access-intune-common-ways-use.md). Om du anger **0** (noll) dagar tillämpas den villkorliga åtkomsten **omedelbart**. Om en enhet till exempel inte är kompatibel kan du använda villkorlig åtkomst för att blockera åtkomsten till e-post, SharePoint och andra organisationsresurser omedelbart.

   När du skapar en efterlevnadsprincip skapas automatiskt åtgärden **Markera enheten som inkompatibel**, och den ställs automatiskt in på **0** dagar (omedelbart). Med den här åtgärden bedöms enheten som icke-kompatibel direkt när den checkar in. Om du även använder villkorlig åtkomst träder den villkorliga åtkomsten i kraft direkt. Om du vill tillåta en respitperiod ändrar du **Schema** för åtgärden **Markera enheten som inkompatibel**.

   I efterlevnadsprincipen kanske du även vill meddela användaren. Du kan lägga till åtgärden **Skicka e-post till slutanvändare**. I åtgärden **Skicka e-post** anger du 2 dagar för **Schema**. Om enheten eller slutanvändaren fortfarande bedöms som icke-kompatibel dag 2 skickas e-postmeddelandet dag 2. Om du vill skicka e-post till användaren på dag 5 i lägger du till en annan åtgärd och anger 5 dagar för **Schema**.

   Mer information om efterlevnad och de inbyggda åtgärderna finns i [översikt över efterlevnad](device-compliance-get-started.md).

6. När du är klar väljer du **Lägg till** > **OK** för att spara ändringarna.

## <a name="next-steps"></a>Nästa steg

[Övervaka dina principer](compliance-policy-monitor.md).
