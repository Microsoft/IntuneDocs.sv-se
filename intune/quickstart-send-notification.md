---
title: Snabbstart – Skicka meddelanden till icke-kompatibla enheter
titleSuffix: Microsoft Intune
description: I den här snabbstarten använder du Microsoft Intune för att skicka e-postmeddelanden till icke-kompatibla enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/27/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb175d2133cf2a7bc5b064c13afb7e252147c729
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044250"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Snabbstart: Skicka meddelanden till icke-kompatibla enheter

I den här snabbstarten använder du Microsoft Intune för att skicka ett e-postmeddelande till de användare i personalen som har icke-kompatibla enheter.

När Intune identifierar en enhet som inte är kompatibel, markerar Intune omedelbart enheten som inkompatibel som standard. Den [villkorliga åtkomsten](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) i Azure Active Directory (AAD) blockerar sedan enheten. När en enhet inte är kompatibel gör Intune att du kan lägga till åtgärder för icke-kompatibilitet, vilket ger mer flexibilitet när du ska bestämma dig för vad du bör göra. Du kan till exempel ge användarna en respitperiod för att uppnå kompatibilitet innan icke-kompatibla enheter blockeras.

En av de åtgärder du kan vidta när en enhet inte uppfyller efterlevnad är att skicka e-post till de slutanvändarna. Du kan även anpassa ett e-postmeddelande innan det skickas till slutanvändare. Specifikt kan du anpassa mottagare, ämne, brödtext, företagslogotyp och kontaktinformation. Intune inkluderar även information om den icke-kompatibla enheten i e-postmeddelandet.

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav
- Du måste ha konfigurerat villkorlig AAD-åtkomst när du använder principer för enhetsefterlevnad till att blockera enheter från företagets resurser. Om du har slutfört snabbstarten [Skapa en enhetsefterlevnadsprincip](quickstart-set-password-length-android.md) använder du Azure Active Directory. Mer information om AAD finns i [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) och [Vanliga sätt att använda villkorlig åtkomst med Intune](conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in i [Intune-portalen](https://aka.ms/intuneportal) som [global administratör](users-add.md#types-of-administrators) eller Intune-[tjänstadministratör](users-add.md#types-of-administrators). Om du har skapat en prenumeration för en Intune-utvärdering, är det konto som du skapade prenumerationen med den globala administratören.

## <a name="create-a-notification-message-template"></a>Skapa en mall för aviseringsmeddelanden

Om du vill skicka ett e-postmeddelande till användarna skapar du en mall för aviseringsmeddelanden. När en enhet är inkompatibel visas informationen som du anger i mallen i e-postmeddelandet som skickas till användarna.

1. I Intune väljer du **Enhetsefterlevnad** > **Meddelanden** > **Skapa meddelande**. 
2. Ange följande information:

   - **Namn**: *Contoso-administratör*
   - **Ämne**: *Efterlevnad för enhet*
   - **Meddelande**: *Din enhet uppfyller för närvarande inte organisationens efterlevnadskrav.*
   - **E-postsidhuvud – Infoga företagets logotyp**: Ange som **Aktiverad** om du vill visa organisationens logotyp.
   - **E-postsidfot – Infoga företagets namn**: Ange som **Aktiverad** om du vill visa organisationens namn.
   - **E-postsidfot – Infoga kontaktinformation**: Ange som **Aktiverad** om du vill visa organisationens kontaktinformation.

   ![Exempel på ett kompatibelt aviseringsmeddelande i Intune](./media/quickstart-send-notification-01.png)

3. När du har lagt till informationen väljer du **Skapa**. Mallen för aviseringsmeddelanden är klar att användas.

    > [!NOTE]
    > Du kan även redigera en meddelandemall som du skapat tidigare.

Mer information om hur du anger företagsnamn, företagets kontaktuppgifter och företagets logotyp finns i [Företagsinformation och sekretesspolicy](company-portal-app.md#company-information-and-privacy-statement), [Supportinformation](company-portal-app.md#support-information) och [Varumärkesanpassning för företagsidentitet](company-portal-app.md#company-identity-branding-customization). 

## <a name="add-a-noncompliance-policy"></a>Lägga till en princip för icke-kompatibilitet

När du skapar en princip för enhetsefterlevnad skapar Intune automatiskt en åtgärd för inkompatibilitet. När en enhet inte uppfyller din efterlevnadsprincip markerar Intune automatiskt den här enheten som icke-kompatibel. Du kan anpassa hur länge enheten ska vara markerad som icke-kompatibel. Du kan även lägga till ytterligare en åtgärd när du skapar en efterlevnadsprincip eller uppdatera en befintlig efterlevnadsprincip. 

Följande steg skapar en efterlevnadsprincip för Windows 10-enheter.

1. I Intune väljer du **Enhetsefterlevnad**.
2. Välj **Principer** > **Skapa princip**.
3. Ange följande information:

   - **Namn**: *Windows 10-efterlevnad*
   - **Beskrivning**: *Windows 10-efterlevnadsprincip*
   - **Plattform**: Windows 10 och senare

4. Välj **Inställningar** > **Systemsäkerhet** för att visa de inställningarna för enhetssäkerhet.
5. Ange **Kräv ett lösenord för att låsa upp mobila enheter** till **Kräv**. Den här inställningen anger huruvida användaren måste ange ett lösenord för att komma åt information på sin mobila enhet. 
6. Ange **Minsta längd på lösenord** till **6**. Den här inställningen anger det minsta antal siffror eller tecken som lösenordet måste innehålla.

    <img alt="System Security settings for a new compliance policy" src="./media/quickstart-send-notification-02.png" width="600">

7. Klicka på **OK** > **OK** > **Skapa** för att skapa din efterlevnadsprincip.
8. Välj **Egenskaper** > **Åtgärd vid icke-kompatibilitet** > **Lägg till**.
9. I listrutan **Åtgärd** bekräftar du att **Skicka e-post till slutanvändare** har valts.
10. Välj **Meddelandemall** > **Contoso-administratör** > **Välj** för att välja den meddelandemall som du skapade tidigare i det här avsnittet.
11. Välj **Lägg till** > **OK** > **Spara** om du vill spara dina ändringar.

## <a name="assign-the-policy"></a>Tilldela principen

Du kan tilldela efterlevnadsprincipen till en specifik grupp med användare eller till alla användare. När Intune identifierar att en enhet är icke-kompatibel meddelas användaren om att enheten måste uppdateras för att uppfylla efterlevnadsprincipen. Med följande steg kan du tilldela principen.

1. Välj den **Windows 10-efterlevnadsprincip** som du skapade tidigare.
2. Välj **Tilldelningar**.
3. I listrutan **Tilldela till** väljer du **Alla användare**. Detta väljer alla användare. Alla användare som har en enhet med **Windows 10 och senare** som inte uppfyller den här efterlevnadsprincipen meddelas.

    > [!NOTE]
    > Du kan inkludera och exkludera grupper när du tilldelar efterlevnadsprinciper.

4. Klicka på **Spara**.

När du har skapat och sparat principen visas den i listan **Enhetsefterlevnad – Principer**. Observera att **Tilldelad** i listan har angetts till **Ja**.

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten använde du Intune till att skapa och tilldela en efterlevnadsprincip för personalens Windows 10-enheter som kräver ett lösenord på minst sex tecken. Mer information om hur du skapar efterlevnadsprinciper för Windows-enheter finns i [Lägga till en enhetsefterlevnadsprincip för Windows-enheter i Intune](compliance-policy-create-windows.md).

Om du vill följa den här serien med Intune-snabbstarter fortsätter du till nästa snabbstart.

> [!div class="nextstepaction"]
> [Snabbstart: Lägga till och tilldela en klientapp](quickstart-add-assign-app.md)
