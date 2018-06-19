---
title: Inkompatibilitetsmeddelande och åtgärder med Microsoft Intune – Azure | Microsoft Docs
description: Skapa ett e-postmeddelande som ska skickas till inkompatibla enheter. Lägg till åtgärder när en enhet har markerats som inkompatibel, t.ex. en respitperiod för att bli kompatibel, eller skapa ett schema som blockerar åtkomst tills enheten är kompatibel. Gör detta med Microsoft Intune i Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8e8603ca59b46937b1529e710a8bc83aec5dd4d6
ms.sourcegitcommit: 4c18352d5b3b30080f7c7257fa63d852b1894850
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/27/2018
ms.locfileid: "32017965"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>Automatisera e-post och lägga till åtgärder för inkompatibla enheter – Intune

Funktionen för **åtgärder vid inkompatibilitet** konfigurerar en tidssorterad sekvens med åtgärder. Dessa åtgärder gäller enheter som inte uppfyller din efterlevnadsprincip. 

## <a name="overview"></a>Översikt
När Intune identifierar en enhet som inte är kompatibel, markerar Intune omedelbart enheten som inkompatibel som standard. Den [villkorliga åtkomsten](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) i Azure Active Directory (AD) blockerar sedan enheten. När en enhet inte är kompatibel kan du med **åtgärder vid inkompatibilitet** få mer flexibilitet när du ska bestämma dig för vad du bör göra. Du kan t.ex. låta bli att blockera enheten omedelbart och ge användaren en respitperiod för att bli kompatibel.

Det finns två typer av åtgärder:

- **Meddela slutanvändarna via e-post**: Anpassa ett e-postmeddelande innan du skickar det till slutanvändaren. Du kan anpassa mottagare, ämne, brödtext, företagslogotyp och kontaktinformation.

    Dessutom inkluderar Intune information om den inkompatibla enheten i e-postmeddelandet.

- **Markera enheten som inkompatibel**: Skapa ett schema (med antal dagar) efter att enheten markerats som inkompatibel. Du kan konfigurera åtgärden till att börja gälla omedelbart, eller ge användaren en respitperiod för att bli kompatibel.

## <a name="before-you-begin"></a>Innan du börjar

- Du måste ha minst en efterlevnadsprincip för enheter för att kunna konfigurera åtgärder vid inkompatibilitet. Se följande plattformar när du ska skapa en efterlevnadsprincip för enheter:

  - [Android](compliance-policy-create-android.md)
  - [Android for Work](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Du måste ha konfigurerat villkorlig Azure AD-åtkomst när du använder principer för enhetsefterlevnad till att blockera enheter från företagets resurser. Läs mer i [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

- Du måste skapa en mall för aviseringsmeddelanden. När du skickar e-postmeddelanden till användarna, används den här mallen för att skapa åtgärder vid inkompatibilitet.

## <a name="create-a-notification-message-template"></a>Skapa en mall för aviseringsmeddelanden

1. Logga in i [Azure-portalen](https://portal.azure.com) med dina autentiseringsuppgifter för Intune. 
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetsefterlevnad** och sedan **Meddelanden**. 
4. Välj **Skapa meddelande** och ange sedan följande information:

   - Namn
   - Ärende
   - Meddelande
   - E-postsidhuvud – Infoga företagets logotyp
   - E-postsidfot – Infoga företagets namn
   - E-postsidfot – Infoga kontaktinformation

   ![Exempel på ett kompatibelt aviseringsmeddelande i Intune](./media/actionsfornoncompliance-1.PNG)

När du har lagt till informationen väljer du **Skapa**. Mallen för aviseringsmeddelanden är klar att användas.

> [!NOTE]
> Du kan också redigera en meddelandemall som du skapat tidigare.

## <a name="add-actions-for-noncompliance"></a>Lägga till åtgärder vid inkompatibilitet

Intune skapar automatiskt en åtgärd vid inkompatibilitet som standard. När en enhet inte uppfyller din efterlevnadsprincip, markerar den här åtgärden enheten som inkompatibel. Du kan anpassa hur länge enheten ska markeras som inkompatibel. Det går inte att ta bort åtgärden.

Du kan lägga till en åtgärd när du skapar en ny efterlevnadsprincip, eller när du uppdaterar en befintlig efterlevnadsprincip. 

1. I [Azure-portalen](https://portal.azure.com) öppnar du **Microsoft Intune** och väljer **Enhetsefterlevnad**.
2. Välj **Principer**, välj en av dina principer och sedan **Egenskaper**. 

  Har du inte någon princip än? Skapa en princip för [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) eller någon annan plattform.
  
  > [!NOTE]
  > JAMF-enheter och enheter som är mål för enhetsgrupper kan inte ta emot efterlevnadsåtgärder just nu.

3. Välj alternativet för **åtgärder vid inkompatibilitet** och sedan **Lägg till** för att ange åtgärdsparametrar. Du kan välja den meddelandemall som skapades tidigare, lägga till ytterligare mottagare och uppdatera schemat för respitperioden. I schemat kan du ange antalet dagar (0 till 365) och sedan kan du tillämpa villkorliga åtkomstprinciper. Om du anger **0** antal dagar kommer den villkorliga åtkomsten **omedelbart** blockera åtkomsten till företagets resurser.

4. När du är klar väljer du **Lägg till** > **OK** för att spara ändringarna.

## <a name="next-steps"></a>Nästa steg
Övervaka aktiviteten för enhetsefterlevnad genom att köra rapporterna. Du hittar mer information i [Övervaka enhetsefterlevnad med Intune](device-compliance-monitor.md).
