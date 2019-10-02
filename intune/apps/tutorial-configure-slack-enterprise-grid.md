---
title: Självstudier – konfigurera Slack till att använda Intune för EMM och appkonfiguration
titleSuffix: Microsoft Intune
description: I de här självstudierna kommer du att konfigurera Slack till att använda Intune för EMM och appkonfiguration.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a210e45ddb181da4db1c1cff1e63a5d9b9ea2343
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724470"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>Självstudie: Konfigurera Slack till att använda Intune för EMM och appkonfiguration

Slack är en samarbetsapp som du kan använda med Microsoft Intune.   

I de här självstudierna får du:
> [!div class="checklist"]
> - Ange Intune som Enterprise Mobility Management (EMM)-provider i din Slack Enterprise Grid. Du kommer att kunna begränsa åtkomsten till din Grid-plans arbetsytor till Intune-hanterade enheter.
> - Skapa appkonfigurationsprinciper för att hantera Slack för EMM-appen i iOS och Slack-appen för Androids arbetsprofilenheter.
> - Skapa efterlevnadsprinciper för Intune-enheter för att ange de villkor som Android- och iOS-enheter måste uppfylla för att anses vara kompatibla.

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav
Du behöver en testklient med följande prenumerationer för den här självstudien:
- Azure Active Directory Premium ([kostnadsfri utvärderingsversion](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Intune-prenumeration ([kostnadsfri utvärderingsversion](../fundamentals/free-trial-sign-up.md))

Du måste också en [Slack Enterprise Grid](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-)-plan.

## <a name="configure-your-slack-enterprise-grid-plan"></a>Konfigurera din Slack Enterprise Grid-plan
Du aktiverar EMM för din Slack Enterprise Grid-plan genom att följa [Slacks instruktioner](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm) och [ansluta Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) som Grid-planens identitetsprovider (IDP).

## <a name="sign-in-to-intune"></a>Logga in i Intune
Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) som global administratör eller Intune-tjänstadministratör. Om du har skapat en prenumeration för en Intune-utvärdering, är det konto som du skapade prenumerationen med den globala administratören.

## <a name="set-up-slack-for-emm-on-ios-devices"></a>Konfigurera Slack för EMM på iOS-enheter
Lägg till iOS-appen Slack för EMM till Intune-klienten och skapa en appkonfigurationsprincip för att möjliggöra för dina organisationers iOS-användare att få åtkomst till Slack med Intune som EMM-provider.

### <a name="add-slack-for-emm-to-intune"></a>Lägg till Slack för EMM i Intune
Lägg till Slack för EMM som en hanterad iOS-app i Intune och tilldela dina Slack-användare. Appar är plattformsspecifika så du måste lägga till en separat Intune-app för dina Slack-användare på Android-enheter.
1. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**.
2. Under Apptyp väljer du **Store-app – iOS**.
3. Välj **Sök i App Store**. Ange sökorden ”Slack för EMM” och välj appen.
4. Välj **Appinformation** och konfigurera eventuella ändringar som du tycker behövs.
5. Välj **Lägg till**.
6. Ange ”Slack för EMM” i sökfältet och välj den app som du just lade till.
7. Välj **Tilldelningar** under Hantera.
8. Välj **Lägg till grupp**. Beroende på vilka som du har valt ska påverkas när du aktiverade EMM för Slack, kan du under **Tilldelningstyp** välja:
    - **Tillgänglig för registrerade enheter** om du väljer ”Alla medlemmar (inklusive gäster)” ELLER
    - **Tillgänglig med eller utan registrering** om du väljer ”Alla medlemmar (exklusive gäster)” eller ”Valfritt”.
9. Välj **Inkluderade grupper**. Under Gör den här appen tillgänglig för alla användare väljer du **Ja**.
10. Klicka på **OK** och sedan på **OK** igen.
11. Klicka på **Spara**.

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>Lägga till en appkonfigurationsprincip till Slack för EMM
Lägg till en appkonfigurationsprincip till Slack för EMM iOS. Appkonfigurationsprinciper för hanterade enheter är plattformsspecifika, så du måste lägga till en separat princip för dina Slack-användare på Android-enheter.
1. Gå till Intune och välj **Klientappar** > **Appkonfigurationsprinciper** > **Lägg till**.
2. Ange Test av appkonfigurationsprincip för Slack vid Namn.
3. Under Registreringstyp för enhet väljer du **Hanterade enheter**.
4. Under Plattform väljer du **iOS**.
5. Välj **Tillhörande app**.
6. Ange ”Slack för EMM” i sökfältet och välj appen.
7. Klicka på **OK** och välj sedan **Konfigurationsinställningar**. 
8. Välj **OK** och välj sedan **Lägg till**.
9. Ange ”Test av appkonfigurationsprincip för Slack” i sökfältet och välj den princip som du just lade till.
10. Välj **Tilldelningar** under Hantera.
11. Välj **Alla användare + Alla enheter** under Tilldela till.
12. Klicka på **Spara**.

### <a name="optional-create-an-ios-device-compliance-policy"></a>(Valfritt) Skapa en iOS-enhetsefterlevnadsprincip
Konfigurera en efterlevnadsprincip för Intune-enheter som anger de villkor som en enhet måste uppfylla för att anses vara kompatibel. I den här självstudien skapar vi en enhetsefterlevnadsprincip för iOS-enheter. Efterlevnadspolicyer är plattformsspecifika så du måste skapa en separat princip för dina Slack-användare på Android-enheter.
1. Välj **Enhetsefterlevnad** > **Principer** > **Skapa princip** i Intune.
2. Vid Namn anger du ”Test av iOS-efterlevnadsprincip”.
3. I Beskrivning anger du ”Test av iOS-efterlevnadsprincip”.
4. Under Plattform väljer du **iOS**.
5. Välj **Enhetens hälsotillstånd**. Bredvid Jailbrokade enheter väljer du **Blockera** och sedan **OK**.
6. Välj **Systemsäkerhet** och ange inställningar för Lösenord. Välj följande rekommenderade inställningar för den här självstudien:
    - Vid Kräv ett lösenord för att låsa upp mobila enheter, väljer du **Kräv**.
    - För Enkla lösenord, väljer du **Blockera**.
    - För Minsta längd på lösenord, anger du 4.
    - För Krav på lösenordstyp, väljer du **Alfanumeriskt**.
    - För Maximalt antal minuter efter skärmlås innan ett lösenord krävs, väljer du **Omedelbart**.
    - För Lösenordets giltighetstid (dagar), anger du 41.
    - För Antal tidigare lösenord för att förhindra återanvändning, anger du 5.
7. Klicka på **OK** och välj sedan **OK** igen.
8. Klicka på **Skapa**.

## <a name="set-up-slack-on-android-work-profile-devices"></a>Konfigurera Slack på Android-arbetsprofilenheter
Lägg till det hanterade Google Play-kontot för Slack till din Intune-klient och skapa en appkonfigurationsprincip för att möjliggöra för dina organisationers Android-användare att få åtkomst till Slack med Intune som EMM-provider.

### <a name="add-slack-to-intune"></a>Lägga till Slack i Intune
Lägg till Slack som en hanterad Google Play-app i Intune och tilldela dina Slack-användare. Appar är plattformsspecifika så du måste lägga till en separat Intune-app för dina Slack-användare på iOS-enheter.
1. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**.
2. Under Apptyp väljer du **Store-app – Hanterat Google Play-konto**.
3. Välj **Hanterat Google Play-konto – Godkänn**. Ange sökorden ”Slack för EMM” och välj appen.
4. Välj **Godkänn**.
5. Ange ”Slack” i sökfältet och välj den app som du just lade till.
6. Välj **Tilldelningar** under Hantera.
7. Välj **Lägg till grupp**. Beroende på vilka som du har valt ska påverkas när du aktiverade EMM för Slack, kan du under **Tilldelningstyp** välja:
    - **Tillgänglig för registrerade enheter** om du väljer ”Alla medlemmar (inklusive gäster)” ELLER
    - **Tillgänglig med eller utan registrering** om du väljer ”Alla medlemmar (exklusive gäster)” eller ”Valfritt”.
8. Välj Inkluderade grupper. Under Gör den här appen tillgänglig för alla användare väljer du **Ja**.
9. Klicka på **OK** och sedan på **OK** igen.
10. Klicka på **Spara**.

### <a name="add-an-app-configuration-policy-for-slack"></a>Lägga till en appkonfigurationsprincip för Slack
Lägg till en appkonfigurationsprincip för Slack. Appkonfigurationsprinciper för hanterade enheter är plattformsspecifika, så du måste lägga till en separat princip för dina Slack-användare på iOS-enheter.
1. Gå till Intune och välj **Klientappar** > **Appkonfigurationsprinciper** > **Lägg till**.
2. Ange Test av appkonfigurationsprincip för Slack vid Namn.
3. Under Registreringstyp för enhet väljer du **Hanterade enheter**.
4. Under Plattform väljer du **Android**.
5. Välj **Tillhörande app**.
6. Ange ”Slack” i sökfältet och välj appen.
7. Välj **OK** och sedan **Konfigurationsinställningar**.
    - Mer information om konfigurationsnycklar och deras värden finns i dokumentationen på fliken ”Tekniskt” på [Slacks AppConfig-webbsida](https://www.appconfig.org/company/slack/).
8. Klicka på **OK** och välj sedan **Lägg till**.
9. Ange ”Test av appkonfigurationsprincip för Slack” i sökfältet och välj den princip som du just lade till.
10. Välj **Tilldelningar** under Hantera.
11. Välj **Alla användare + Alla enheter** under Tilldela till.
12. Klicka på **Spara**.

### <a name="optional-create-an-android-device-compliance-policy"></a>(Valfritt) Skapa en Android-enhetsefterlevnadsprincip
Konfigurera en efterlevnadsprincip för Intune-enheter som anger de villkor som en enhet måste uppfylla för att anses vara kompatibel. I de här självstudierna skapar vi en enhetsefterlevnadsprincip för Android-enheter. Efterlevnadspolicyer är plattformsspecifika så måste du skapa en separat princip för dina Slack-användare på iOS-enheter.
1. Välj **Enhetsefterlevnad** > **Principer** > **Skapa princip** i Intune.
2. Vid Namn anger du ”Test av Android-efterlevnadsprincip”.
3. Vid Beskrivning anger du ”Test av Android-efterlevnadsprincip”.
4. Välj **Android Enterprise** under Plattform.
5. Välj **Arbetsprofil** under profiltyp.
6. Välj **Enhetens hälsotillstånd**. Bredvid Rotade enheter väljer du **Blockera** och sedan **OK**.
7. Välj **Systemsäkerhet** och ange inställningar för **Lösenord**. Välj följande rekommenderade inställningar för den här självstudien:
    - Vid Kräv ett lösenord för att låsa upp mobila enheter, väljer du **Kräv**.
    - Välj **Minst alfanumeriskt** för Krav på lösenordstyp.
    - För Minsta längd på lösenord, anger du 4.
    - För Maximalt antal minuter efter skärmlås innan ett lösenord krävs, väljer du **15 minuter**.
    - För Lösenordets giltighetstid (dagar), anger du 41.
    - För Antal tidigare lösenord för att förhindra återanvändning, anger du 5.
8. Klicka på **OK** och sedan på **OK** igen.
9. Klicka på **Skapa**.

## <a name="launch-slack"></a>Starta Slack

Med de principer som du just har skapat måste alla iOS- eller Android-arbetsprofilenheter som försöker logga in till en av dina arbetsytor vara Intune-registrerade. Försök starta Slack för EMM på en Intune-registrerad iOS-enhet eller starta Slack på en Intune-registrerad Android-arbetsprofilenhet för att testa det här scenariot. 

## <a name="next-steps"></a>Nästa steg

I de här självstudierna har du
- angett Intune som Enterprise Mobility Management (EMM)-provider i din Slack Enterprise Grid. 
- skapat appkonfigurationsprinciper för att hantera Slack för EMM-appen i iOS och Slack-appen för Android-arbetsprofilenheter.
- skapat efterlevnadsprinciper för Intune-enheter för att ange de villkor som Android- och iOS-enheter måste uppfylla för att anses vara kompatibla.

Mer information om appkonfigurationsprinciper finns i [Appkonfigurationsprinciper för Microsoft Intune](app-configuration-policies-overview.md). Mer information om enhetsefterlevnadspolicyer finns i [Ange regler för enheter som tillåter åtkomst till resurser i din organisation med Intune](../protect/device-compliance-get-started.md).
