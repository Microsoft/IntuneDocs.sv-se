---
title: Konfigurera Symantec-integration med Microsoft Intune | Microsoft Intune
description: Konfigurera Symantec Endpoint Protection Mobile-lösningen med Microsoft Intune för att styra mobil enhetsåtkomst till företagets resurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4b519c30f432a6d8584c2bd5bca94ead95a862b1
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817355"
---
# <a name="set-up-symantec-endpoint-protection-mobile-integration-with-intune"></a>Konfigurera Symantec Endpoint Protection Mobile-integrering med Intune

Utför följande steg om du vill integrera lösningen Symantec Endpoint Protection Mobile (SEP Mobile) med Intune. Du måste lägga till SEP Mobile-appar i Azure AD för att kunna använda enkel inloggning.

## <a name="before-you-begin"></a>Innan du börjar

### <a name="azure-ad-account-used-to-integrate-intune-and-sep-mobile"></a>Azure AD-kontot som används för att integrera Intune och SEP Mobile

-   Kontrollera att Azure AD-kontot har konfigurerats korrekt i [Symantec Endpoint Protection Mobile-hanteringskonsol](https://aad.skycure.com), innan du startar den grundläggande Skycure-installationsprocessen.
- Azure AD-kontot måste vara ett globalt administratörskonto för att utföra integrationen.
### <a name="network-setup"></a>Nätverkskonfiguration

Du kan kontrollera att nätverket har konfigurerats korrekt för integrering med SEP Mobile-installationen genom att referera till Symantec-artikeln [Ställa in din nätverkskonfiguration](https://portal.skycure.com/articles/Documentation/Setting-up-your-network-configuration-26-8-2016).

### <a name="full-integration-vs-read-only"></a>Fullständig integrering resp. Skrivskyddad

SEP Mobile har stöd för två integreringslägen med Intune:

-   **Skrivskyddad integrering (grundinställning):** Inventerar endast enheter från Azure Active Directory och fyller i dem i Symantec Endpoint Protection Mobile-hanteringskonsolen.
<br>
    -   Om rutorna **Rapportera hälsotillstånd och enhetsrisker till Intune** och **Rapportera även säkerhetsincidenter till Intune** inte är markerade i Symantec Endpoint Protection Mobile-hanteringskonsolen, är integreringen skrivskyddad och ändrar därför aldrig tillståndet för en enhet (kompatibel eller icke-kompatibel) i Intune.
<br></br>
-   **Fullständig integrering:** Tillåter att SEP Mobile rapporterar information om enheternas risker och säkerhetsincidenter till Intune, vilket skapar en dubbelriktad kommunikation mellan båda molntjänsterna.

### <a name="how-are-the-sep-mobile-apps-used-with-azure-ad-and-intune"></a>Hur används SEP Mobile-appar med Azure AD och Intune?

-   **iOS-app:** Slutanvändarna kan logga in på Azure AD med en iOS-app.

-   **Android-app:** Slutanvändarna kan logga in på Azure AD med en Android-app.

-   **Hanteringsapp:** Detta är SEP Mobile Azure AD-appen för flera innehavare som möjliggör kommunikation från tjänst till tjänst med Intune.

## <a name="to-set-up-the-read-only-integration-between-intune-and-sep-mobile"></a>Så här konfigurerar du skrivskyddad integrering mellan Intune och SEP Mobile

> [!IMPORTANT]
> SEP Mobile-administratörens autentiseringsuppgifter måste bestå av ett e-postkonto som tillhörar en giltig användare i Azure Active Directory, annars misslyckas inloggningen. SEP Mobile använder Azure Active Directory till att autentisera sin administratör med enkel inloggning (SSO).

1.  Gå till [Symantec Endpoint Protection Mobile-hanteringskonsol](https://aad.skycure.com).

2.  Ange dina **SEP Mobile-autentiseringsuppgifter för administratör** och välj sedan **Fortsätt**.

3.  Gå till **Inställningar** och välj **Grundinställning** under **Intune-integrering**.

4.  Bredvid **iOS-appen**, välj **Lägg till i Active Directory**.

    ![Bild av Symantec Endpoint Protection Mobile-hanteringskonsolen](./media/symantec-portal-basic-add.png)

5.  När inloggningssidan öppnas anger du dina autentiseringsuppgifter för Intune och väljer sedan på **Acceptera**.

    ![Bild av iOS-app i Intune, inloggningsfråga](./media/symantec-portal-basic-accept.png)

6.  När appen har lagts till Azure AD kan se du en indikation om att appen har lagts till.

    ![Bild av iOS-appens slutförandeskärm](./media/symantec-portal-basic-added.png)

7. Upprepa dessa steg för **SEP Mobile Android**-apparna och **hanterings**apparna.

### <a name="add-an-azure-ad-security-group-into-sep-mobile"></a>Lägg till en Azure AD-säkerhetsgrupp i SEP Mobile

Du måste lägga till en Azure AD-säkerhetsgrupp som innehåller alla enheter som kör SEP Mobile.

-  Ange och välj alla säkerhetsgrupper med enheter som kör SEP Mobile och spara sedan ändringarna.

    ![Bild som visar användargrupper för SEP Mobile-appar](./media/symantec-portal-basic-groups.png)   

SEP Mobile synkroniserar de enheter som kör Mobile Threat Defense-tjänsten med Azure AD-säkerhetsgrupperna.

![Bild som visar säkerhetsgruppens konfiguration i SEP Mobile-hanteringskonsolen](./media/symantec-portal-basic-status.png)

## <a name="to-set-up-the-full-integration-between-intune-and-sep-mobile"></a>Konfigurera fullständig integrering mellan Intune och SEP Mobile

### <a name="retrieve-the-directory-id-in-azure-ad"></a>Hämta katalog-ID i Azure AD

1. Logga in på [Azure Portal](https://portal.azure.com).

2. Skriv ”Active Directory” i sökrutan och välj sedan **Azure Active Directory**.

3. Välj **Egenskaper**.

4. Bredvid **katalog-ID**, väljer du ikonen kopiera och klistrar sedan in den på en säker plats. Du behöver den här identifieraren i ett senare steg.

    ![Bild som visar katalog-ID i Azure Portal](./media/symantec-azure-portal-directory-ID.png)

### <a name="optional-create-a-dedicated-security-group-for-devices-that-need-to-run-the-sep-mobile-apps"></a>(Valfritt) Skapa en dedikerad säkerhetsgrupp för enheter som behöver köra SEP Mobile-appar
1. I [Azure Portal](https://portal.azure.com) under **Hantera**, välj **Användare och grupper** och välj sedan **Alla grupper**.

2. Välj knappen **Lägg till**. Skriv ett grupp**namn**. Under **Medlemskapstyp**, välj **Tilldelad**.

3. På bladet **Medlemmar** välj gruppmedlemmarna och välj sedan knappen **Välj**.

4. Välj **Skapa** på bladet **Grupp**.

### <a name="set-up-the-integration-between-symantec-endpoint-protection-mobile-and-intune"></a>Konfigurera integrationen mellan Symantec Endpoint Protection Mobile och Intune

1.  Gå till [Symantec Endpoint Protection Mobile-hanteringskonsol](https://aad.skycure.com).

2.  Ange dina **SEP Mobile-autentiseringsuppgifter för administratör**, välj sedan **Fortsätt**.

3.  Gå till avsnittet **Inställningar** > **Integreringar** > **Intune** > **Val av EMM-integrering**.

4. I rutan **katalog-ID**, klistra in det katalog-ID som du kopierade från Azure Active Directory i föregående avsnitt och spara inställningarna.

    ![Bild som visar katalog-ID i SEP Mobile-portalen](./media/symantec-portal-directory-ID.png)     

5. Gå till avsnittet **Inställningar** > **Integreringar** > **Intune** > **Grundinställning**.

6. Bredvid **iOS-appen**, välj knappen **Lägg till i Active Directory**.

    ![Bild som visar hur du lägger till iOS-appen i Active Directory](./media/symantec-portal-basic-add.png)   

7.  Logga in med Azure Active Directory-autentiseringsuppgifterna för det Office 365-kontot som hanterar katalogen.

8.  Välj knappen **Acceptera** för att lägga till SEP Mobile iOS-appen i Azure Active Directory.

    ![Bild som visar knappen för att acceptera](./media/symantec-portal-basic-accept.png)     

9.  Upprepa samma steg för **Android-appen** och **Hanteringsappen**.

10. Välj alla användargrupper som måste köra SEP Mobile-apparna, till exempel säkerhetsgruppen du skapade tidigare.

    ![Bild som visar användargrupper för SEP Mobile-appar](./media/symantec-portal-basic-groups.png)   

11.  SEP Mobile synkroniserar enheterna i de valda grupperna och börjar rapportera information till Intune. Du kan visa dessa data i avsnittet Fullständig integrering. Gå till avsnittet **Inställningar** > **Integreringar** > **Intune** > **Fullständig integrering**.

     ![Bild som visar att SEP Mobiles fullständiga integrering slutfördes](media/symantec-portal-basic-status.PNG)
## <a name="next-steps"></a>Nästa steg

[Ställ in SEP Mobile-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)
