---
title: Inkompatibilitetsmeddelande och åtgärder med Microsoft Intune – Azure | Microsoft Docs
description: Skapa ett e-postmeddelande som ska skickas till inkompatibla enheter. Lägg till åtgärder när en enhet har markerats som inkompatibel, t.ex. en respitperiod för att bli kompatibel, eller skapa ett schema som blockerar åtkomst tills enheten är kompatibel. Gör detta med Microsoft Intune i Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 953b468337d3317027344573d147b65d765e3db3
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236449"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>Automatisera e-post och lägga till åtgärder för inkompatibla enheter – Intune

Funktionen för **åtgärder vid inkompatibilitet** konfigurerar en tidssorterad sekvens med åtgärder. Dessa åtgärder gäller enheter som inte uppfyller din efterlevnadsprincip. 

## <a name="overview"></a>Översikt
När Intune identifierar en enhet som inte är kompatibel, markerar Intune omedelbart enheten som inkompatibel som standard. Den [villkorliga åtkomsten](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) i Azure Active Directory (AD) blockerar sedan enheten. När en enhet inte är kompatibel kan du med **åtgärder vid inkompatibilitet** få mer flexibilitet när du ska bestämma dig för vad du bör göra. Du kan t.ex. låta bli att blockera enheten omedelbart och ge användaren en respitperiod för att bli kompatibel.

Det finns flera typer av åtgärder:

- **Skicka e-post till slutanvändare**: Anpassa ett e-postmeddelande innan det skickas till slutanvändaren. Du kan anpassa mottagare, ämne, brödtext, företagslogotyp och kontaktinformation.

    Dessutom inkluderar Intune information om den inkompatibla enheten i e-postmeddelandet.

- **Fjärrlås en inkompatibel enhet**: För enheter som inte är kompatibla kan du utfärda en fjärrlåsning. Användaren uppmanas i så fall att ange en PIN-kod eller ett lösenord för att låsa upp enheten. Mer om funktionen [Fjärrlåsning](device-remote-lock.md). 

- **Markera enheten som inkompatibel**: Skapa ett schema (med antal dagar) efter att enheten markerats som inkompatibel. Du kan konfigurera åtgärden till att börja gälla omedelbart, eller ge användaren en respitperiod för att bli kompatibel.

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

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetsefterlevnad** > **Meddelanden**.
3. Välj **Skapa meddelande**. Ange följande information:

   - **Namn**
   - **Ämne**
   - **Meddelande**
   - **E-postsidhuvud – Infoga företagets logotyp**
   - **E-postsidfot – Infoga företagets namn**
   - **E-postsidfot – Infoga kontaktinformation**

   ![Exempel på ett kompatibelt aviseringsmeddelande i Intune](./media/actionsfornoncompliance-1.PNG)

4. När du har lagt till informationen väljer du **Skapa**. Mallen för aviseringsmeddelanden är klar att användas. Observera att logotypen som du laddar upp som en del av varumärkesanpassningen av företagsportalen används för e-postmallar. Läs mer om varumärkesanpassning av företagsportalen i [Varumärkesanpassning för företagsidentitet](company-portal-app.md#company-identity-branding-customization).  

> [!NOTE]
> Du kan också redigera en meddelandemall som du skapat tidigare.

## <a name="add-actions-for-noncompliance"></a>Lägga till åtgärder vid inkompatibilitet

När du skapar en princip för enhetsefterlevnad skapar Intune automatiskt en åtgärd för inkompatibilitet. När en enhet inte uppfyller din efterlevnadsprincip, markerar den här åtgärden enheten som inkompatibel. Du kan anpassa hur länge enheten ska markeras som inkompatibel. Det går inte att ta bort åtgärden.

Du kan också lägga till en till åtgärd när du skapar en princip för efterlevnad eller uppdatera en befintlig princip. 

1. På [Azure-portalen](https://portal.azure.com) öppnar du **Microsoft Intune** > **Enhetsefterlevnad**.
2. Välj **Principer**, välj en av dina principer och sedan **Egenskaper**. 

    Har du inte någon princip än? Skapa en princip för [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) eller någon annan plattform.
  
    > [!NOTE]
    > JAMF-enheter och enheter som är mål för enhetsgrupper kan inte ta emot efterlevnadsåtgärder just nu.

3. Välj **Åtgärder för inkompatibilitet** > **Lägg till**.
4. Välj din **åtgärd**: 

    - **Skicka e-post till slutanvändare**: Välj att skicka ett e-postmeddelande till användaren om enheten inte är kompatibel. Du kan också: 
    
         - Välj den **meddelandemall** som du skapade tidigare
         - Ange eventuella **ytterligare mottagare** genom att välja grupper
    
    - **Fjärrlås en inkompatibel enhet**: Lås enheten om den inte är kompatibel. Detta tvingar användaren att ange en PIN-kod eller ett lösenord för att låsa upp enheten. 
    
    - **Schema**: Ange hur många dagar (0 till 365) efter en inkompatibilitet som åtgärden ska utlösas på användarnas enheter. Efter den här respittiden kan du tillämpa en princip för villkorlig åtkomst. Om du anger **0** antal dagar tillämpas den villkorliga åtkomsten **omedelbart**. Du kan exempelvis blockera åtkomsten till företagsresurser direkt om en enhet inte är kompatibel.

5. När du är klar väljer du **Lägg till** > **OK** för att spara ändringarna.

## <a name="next-steps"></a>Nästa steg
[Övervaka aktivitet rörande enhetsefterlevnad](device-compliance-monitor.md).
