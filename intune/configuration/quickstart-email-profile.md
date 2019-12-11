---
title: Snabbstart – skapa en e-postenhetsprofil för iOS
titleSuffix: Microsoft Intune
description: Lär dig att använda Microsoft Intune för att skapa en e-postenhetsprofil så att iOS-enheter kan anslutas säkert till företagets e-post.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b2f1372a6d7ced09a9ebdfc11cbad69501827bc
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059318"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>Snabbstart: Skapa en e-postenhetsprofil för iOS

I den här snabbstarten visas hur du skapar en e-postenhetsprofil för iOS-enheter. Den här profilen anger inställningar som krävs för att den inbyggda e-postappen på iOS-enhet ska kunna ansluta till företagets e-post. Med e-postenhetsprofiler uppnår du konsekvens över flera enheter och ger slutanvändarna åtkomst till företagets e-post på sina personliga enheter utan de behöver konfigurera något själva. För att ytterligare skydda din e-post kan du använda en e-postprofil för att avgöra om enheterna är kompatibla och sedan konfigurera villkorlig åtkomst så att endast kompatibla enheter får åtkomst till e-post. Mer information om e-postprofiler finns i [Konfigurera e-postinställningar i Microsoft Intune](email-settings-configure.md)

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) som global administratör eller Intune-tjänstadministratör. Om du har skapat en prenumeration för en Intune-utvärdering, är det konto som du skapade prenumerationen med den globala administratören.

## <a name="create-an-ios-email-profile"></a>Skapa en e-postprofil för iOS

1. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.

   ![Skapa en e-postprofil för iOS](./media/quickstart-email-profile/ios-create-profile.png)

2. Under **Namn** anger du ett beskrivande namn på den nya profilen. I det här exemplet anger du **iOS måste använda e-postadress**.
3. Ange följande profilinformation:
    - För **beskrivning** anger du **iOS-enheter måste använda e-postadress**.
    - För **Plattform**, välj **iOS**.
    - För **Profiltyp** väljer du **e-post**.

        ![Skapa en e-postprofil för användning med iOS](./media/quickstart-email-profile/ios-email-profile-name.png)

4. Välj **inställningar** och ange följande inställningar (lämna standardinställningarna för alla andra inställningar):
   - **E-postserver**: I den här snabbstarten använder vi **outlook.office365.com**. Den här inställningen anger Exchange-platsen (URL) för e-postservern som iOS e-postappen använder för att ansluta till e-post.
   - **Kontonamn**: Ange **Företagets e-postadress**.
   - **Användarnamnattribut från AAD**: Namnet är det attribut som Intune hämtar från Azure Active Directory (Azure AD). Intune genererar användarnamnet som används av den här profilen. I den här snabbstarten kommer vi att anta att **User Principal Name** ska användas som användarnamn för profilen (till exempel user1@contoso.com).
   - **E-postadressattribut från AAD**: Den här inställningen är e-postadressen från Azure AD som används för att logga in på Exchange. I den här snabbstarten använder vi **User Principal Name**.
   - **Autentiseringsmetod**: I den här snabbstarten väljer vi **användarnamn och lösenord**. (Du kan också välja **Certifikat** om du redan har konfigurerat ett certifikat för Intune.)

        ![Skapa en e-postprofil för användning med iOS](./media/quickstart-email-profile/ios-email-profile.png)

5. Välj **OK** > **Skapa**. Den nya profilen visas i profillistan med instrumentpanelen öppen så att du kan övervaka hur profilen har tilldelats till iOS-enheter och iOS-användare.
6. Välj **Tilldelningar**.
7. Välj fliken **inkludera** och välj sedan **Alla användare och Alla enheter**. 
8. Välj **Spara**.

## <a name="clean-up-resources"></a>Rensa resurser

Om du inte planerar att använda profilen du skapade för fler självstudier eller test bör du ta bort den nu.

1. I Intune väljer du **Enhetskonfiguration** och sedan **Profiler**.
2. Välj testprofilen som du skapade **iOS måste använda e-postadress**.
3. Välj ellipserna ( **...** ) intill profilen och välj sedan **Ta bort**.

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten skapade du en e-postprofil för iOS-enheter. Nu kan du använda den här profilen för att avgöra om en iOS-enhet är kompatibel genom att skapa en efterlevnadsprincip som markerar iOS-enheter som inte matchar profilen som icke-kompatibla. För ytterligare skydd, kan du skapa en villkorlig åtkomstprincip som blockerar icke-kompatibla iOS-enheter från att komma åt e-post. Mer information om efterlevnadsprinciper för enheter i [Kom igång med efterlevnadsprinciper för enheter i Intune](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Självstudie: Skydda e-post i Exchange Online på hanterade enheter](../tutorial-protect-email-on-enrolled-devices.md)
