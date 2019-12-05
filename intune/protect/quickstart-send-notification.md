---
title: Snabbstart – Skicka meddelanden till icke-kompatibla enheter
titleSuffix: Microsoft Intune
description: I den här snabbstarten kommer du att använda Microsoft Intune för att skicka e-postmeddelanden till icke-kompatibla enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d89cfcafd5452b990509e0fa6fd431a614ee5c1
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410266"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Snabbstart: Skicka meddelanden till icke-kompatibla enheter

I den här snabbstarten kommer du att använda Microsoft Intune för att skicka ett e-postmeddelande till de användare i personalen som har icke-kompatibla enheter.

När Intune identifierar en enhet som inte är kompatibel, markerar Intune omedelbart enheten som inkompatibel som standard. Den [villkorliga åtkomsten](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) i Azure Active Directory (Azure AD) blockerar sedan enheten. När en enhet inte är kompatibel gör Intune att du kan lägga till åtgärder för icke-kompatibilitet, vilket ger mer flexibilitet när du ska bestämma dig för vad du bör göra. Du kan till exempel ge användarna en respitperiod för att uppnå kompatibilitet innan icke-kompatibla enheter blockeras.

En åtgärd som ska vidtas när en enhet inte är kompatibel är att skicka e-postmeddelande till enhetsanvändaren. Du kan även anpassa ett e-postmeddelande innan det skickas. Specifikt kan du anpassa mottagare, ämne, brödtext, företagslogotyp och kontaktinformation. Intune inkluderar även information om den icke-kompatibla enheten i e-postmeddelandet.

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav

Du måste ha konfigurerat villkorlig Azure AD-åtkomst när du använder principer för enhetsefterlevnad till att blockera enheter från företagets resurser. Om du har slutfört snabbstarten [Skapa en enhetsefterlevnadsprincip](quickstart-set-password-length-android.md) använder du Azure Active Directory. Mer information om Azure Active Directory finns i [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) och [Vanliga sätt att använda villkorlig åtkomst med Intune](../protect/conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) som [global administratör](../fundamentals/users-add.md#types-of-administrators) eller [tjänstadministratör](../fundamentals/users-add.md#types-of-administrators) för Intune. Om du har skapat en prenumeration för Intune-utvärdering är det konto som du skapade prenumerationen med den globala administratören.

## <a name="create-a-notification-message-template"></a>Skapa en mall för aviseringsmeddelanden

Om du vill skicka ett e-postmeddelande till användarna skapar du en mall för aviseringsmeddelanden. När en enhet är inkompatibel visas informationen som du anger i mallen i e-postmeddelandet som skickas till användarna.

1. I Intune väljer du **Enheter** > **Efterlevnadsprinciper** > **Meddelanden** > **Skapa meddelande**.
2. Ange följande information:

   - **Namn**: *Contoso-administratör*
   - **Ämne**: *Efterlevnad för enhet*
   - **Meddelande**: *Din enhet uppfyller för närvarande inte organisationens efterlevnadskrav.*
   - **E-postsidhuvud – Infoga företagets logotyp**: Ange som **Aktiverad** om du vill visa organisationens logotyp.
   - **E-postsidfot – Infoga företagets namn**: Ange som **Aktiverad** om du vill visa organisationens namn.
   - **E-postsidfot – Infoga kontaktinformation**: Ange som **Aktiverad** om du vill visa organisationens kontaktinformation.

   ![Exempel på ett kompatibelt aviseringsmeddelande i Intune](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. Välj **Nästa** och granska meddelandet. Välj **Skapa** så är meddelandemallen klar att användas.

   > [!NOTE]
   > Du kan även redigera en meddelandemall som du skapat tidigare.

Mer information om hur du anger företagets namn, företagets kontaktinformation och företagets logotyp finns i följande artiklar:

- [Företagsinformation och sekretesspolicy](../apps/company-portal-app.md#company-information-and-privacy-statement)
- [Supportinformation](../apps/company-portal-app.md#support-information)
- [Varumärkesanpassning för företagsidentitet](../apps/company-portal-app.md#company-identity-branding-customization).

## <a name="add-a-noncompliance-policy"></a>Lägga till en princip för icke-kompatibilitet

När du skapar en princip för enhetsefterlevnad skapar Intune automatiskt en åtgärd för inkompatibilitet. Intune markerar sedan enheterna som icke-kompatibla när de inte uppfyller efterlevnadsprincipen. Du kan anpassa hur länge enheten ska vara markerad som icke-kompatibel. Du kan även lägga till ytterligare en åtgärd när du skapar en efterlevnadsprincip eller uppdatera en befintlig efterlevnadsprincip.

Följande steg skapar en efterlevnadsprincip för Windows 10-enheter.

1. I Intune väljer du **Enheter** > **Efterlevnadsprinciper** > **Skapa princip**.

2. Ange följande information:

   - **Namn**: *Windows 10-efterlevnad*
   - **Beskrivning**: *Windows 10-efterlevnadsprincip*
   - **Plattform**: Windows 10 och senare

3. Välj **Inställningar** > **Systemsäkerhet** för att visa de inställningarna för enhetssäkerhet.

4. Konfigurera följande alternativ:

   - Ange **Kräv ett lösenord för att låsa upp mobila enheter** till **Kräv**. Den här inställningen anger huruvida användaren måste ange ett lösenord för att komma åt information på sin mobila enhet.

   - Ange **Minsta längd på lösenord** till **6**. Den här inställningen anger det minsta antal siffror eller tecken som lösenordet måste innehålla.

   ![Inställningar för systemsäkerhet för en ny efterlevnadsprincip](./media/quickstart-send-notification/system-security-settings-01.png)

5. Klicka på **OK** > **OK** > **Skapa** för att skapa din efterlevnadsprincip.

6. Välj **Egenskaper** > **Åtgärd vid icke-kompatibilitet** > **Lägg till**.

7. I listrutan **Åtgärd** bekräftar du att **Skicka e-post till slutanvändare** har valts.

8. Välj **Meddelandemall**, den mall du skapade i artikeln tidigare och sedan **Välj** för att välja meddelandemallen.

9. Välj **Lägg till** > **OK** > **Spara** om du vill spara dina ändringar.

## <a name="assign-the-policy"></a>Tilldela principen

Du kan tilldela efterlevnadsprincipen till en specifik grupp med användare eller till alla användare. När Intune identifierar att en enhet är icke-kompatibel meddelas användaren om att enheten måste uppdateras för att uppfylla efterlevnadsprincipen. Använd följande steg för att tilldela principen.

1. I Intune går du till **Enheter** > **Efterlevnadsprincip** och väljer den **Princip för Windows 10-efterlevnad** som du skapade tidigare.

2. Välj **Tilldelningar**.

3. I listrutan **Tilldela till** väljer du **Alla användare**. Detta väljer alla användare. Alla användare som har en enhet med **Windows 10 och senare** som inte uppfyller den här efterlevnadsprincipen meddelas.

    > [!NOTE]
    > Du kan inkludera och exkludera grupper när du tilldelar efterlevnadsprinciper.

4. Klicka på **Spara**.

När du har skapat och sparat principen visas den i listan **Efterlevnadsprinciper – Principer**. Observera att **Tilldelad** i listan har angetts till **Ja**.

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten använde du Intune till att skapa och tilldela en efterlevnadsprincip för personalens Windows 10-enheter som kräver ett lösenord på minst sex tecken. Mer information om hur du skapar efterlevnadsprinciper för Windows-enheter finns i [Lägga till en enhetsefterlevnadsprincip för Windows-enheter i Intune](compliance-policy-create-windows.md).

Om du vill följa den här serien med Intune-snabbstarter fortsätter du till nästa snabbstart.

> [!div class="nextstepaction"]
> [Snabbstart: Lägga till och tilldela en klientapp](../apps/quickstart-add-assign-app.md)
