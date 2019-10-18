---
title: Vad är Microsoft Intune? – Azure | Microsoft Docs
description: Lär dig mer om hur Microsoft Intune är en komponent för hantering av mobilenheter (MDM) och hantering av mobilappar (MAM) i Enterprise Mobility + Security-lösningen, och se hur den kan hjälpa dig att skydda företagets data.
keywords: what is Intune
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/14/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 56c76663330cae5cb771358542fd22ff09398118
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314722"
---
# <a name="microsoft-intune-is-an-mdm-and-mam-provider-for-your-devices"></a>Microsoft Intune är en MDM- och MAM-provider för dina enheter

Microsoft Intune är en molnbaserad tjänst som fokuserar på hantering av mobilenheter (MDM) och hantering av mobilprogram (MAM). Intune ingår i Microsofts [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/microsoft-365/enterprise-mobility-security) och gör det möjligt för användarna att vara produktiva samtidigt som organisationens data skyddas. Den integreras med andra tjänster, inklusive Microsoft 365 och Azure Active Directory (Azure AD) för att styra vilka som har åtkomst och vad de har åtkomst till, samt Azure Information Protection för dataskydd. När du använder den tillsammans med Microsoft 365 kan dina anställda vara produktiva på alla sina enheter, samtidigt som organisationens information skyddas.

![Bild av Intune-arkitektur](./media/what-is-intune/intunearch_sm.png)

Visa en [större version](./media/what-is-intune/intunearchitecture.svg) av Intune-arkitekturdiagrammet.

Med Intune kan du:

- Välj att vara 100 % i molnet med Intune, eller vara [samhanterade](https://docs.microsoft.com/sccm/comanage/overview) med Configuration Manager och Intune.
- Ange regler och konfigurera inställningar för personliga och organisationsägda enheter som ska ha åtkomst till data och nätverk.
- Distribuera och autentisera appar på enheter – lokalt och mobilt.
- Skydda företagets information genom att styra hur användarna får åtkomst till och delar information.
- Säkerställ att enheter och appar följer säkerhetskraven.

## <a name="manage-devices"></a>Hantera enheter

I Intune hanterar du enheter med hjälp av den metod som passar dig. Om du har organisationsägda enheter kanske du vill ha fullständig kontroll över enheterna, inklusive inställningar, funktioner och säkerhet. Med den här metoden ”registreras” enheter och användare i Intune. När de har registrerats får de dina regler och inställningar via principer som konfigureras i Intune. Du kan till exempel ange krav på lösenord och PIN-kod, skapa en VPN-anslutning, konfigurera skydd mot hot och mycket annat.

Användarna kanske inte vill att organisationens administratörer ska ha fullständig behörighet till deras personliga enheter eller BYOD-enheter. Med den här metoden får användarna alternativ. Till exempel kan användarna [registrera](../enrollment/device-enrollment.md) sina enheter om de vill ha fullständig åtkomst till organisationens resurser. Om användarna i stället bara vill ha åtkomst till e-post eller Microsoft Teams, använder du skyddsprinciper för appar som kräver multifaktorautentisering (MFA) för att använda dessa appar.

När enheterna har registrerats och hanteras i Intune kan administratörerna:

- Se vilka enheter som har registrerats och få en lista över de enheter som har åtkomst till organisationens resurser.
- Konfigurera enheterna så att de uppfyller säkerhets- och hälsostandarder. Till exempel vill du förmodligen blockera jailbrokade enheter.
- Skicka certifikat till enheterna så att användarna enkelt kan komma åt ditt Wi-Fi-nätverk, eller använd ett VPN för att ansluta till nätverket.
- Se rapporter om användare och enheter som är kompatibla och de som inte uppfyller kraven.
- Ta bort organisationsdata om en enhet tappas bort, blir stulen eller inte längre används.

**Onlineresurser**:

- [Vad är enhetsregistrering](../enrollment/device-enrollment.md)

- [Tillämpa funktioner och inställningar på dina enheter med enhetsprofiler](../configuration/device-profiles.md)

- [Skydda enheter med Microsoft Intune](../protect/device-protect.md)

## <a name="manage-apps"></a>Hantera appar

Hanteringen av mobilprogram (MAM) i Intune är utformat för att skydda organisationens data på programnivå, inklusive anpassade appar och Store-appar. Apphanteringen kan användas på organisationsägda enheter och personliga enheter.

När appar hanteras i Intune kan administratörerna:

- Lägga till och tilldela mobilappar till användargrupper och enheter, inklusive användare i vissa grupper, enheter i vissa grupper med mera.
- Konfigurera att apparna startas eller körs med vissa inställningar aktiverade, samt uppdatera befintliga appar som redan finns på enheten.
- Se rapporter om vilka appar som används och spåra deras användning.
- Göra en selektiv rensning genom att enbart ta bort organisationens data från apparna.

En metod i Intune som ger säkerhet för mobilappar är med hjälp av **[appskyddsprinciper](../apps/app-protection-policy.md)** . Appskyddsprinciper:

- Använd Azure AD-identitet till att isolera organisationens data från personliga data. Den personliga informationen isoleras därmed från organisationens IT-hantering. Data som nås med autentiseringsuppgifter för organisationen ges ytterligare säkerhetsskydd.
- Skydda åtkomsten till personliga enheter genom att begränsa de åtgärder som användarna kan vidta, till exempel att kopiera och klistra in, spara och visa.
- Kan skapas och distribueras på enheter som har registrerats i Intune, registrerats i en annan MDM-tjänst, eller som inte är registrerade i någon MDM-tjänst. På registrerade enheter kan appskyddsprinciperna ge ett extra skyddslager.

Till exempel kan en användare logga in på en enhet med sina autentiseringsuppgifter för organisationen. Organisationens identitet ger åtkomst till data som användarens personliga identitet inte har åtkomst till. När den här organisationsinformationen används reglerar appskyddsprinciperna hur datan får sparas och delas. När användarna loggar in med sin personliga identitet tillämpas inte samma skydd. På så sätt har IT-administratörerna kontroll över organisationens data, samtidigt som slutanvändarna har kvar sin integritet och kontroll över den personliga datan.

Du kan också använda Intune med de andra tjänsterna i EMS. Den här funktionen ger organisationen en säkerhet för mobilappar som går utöver vad som ingår i operativsystem och appar. Appar som hanteras med EMS har åtkomst till en bredare uppsättning mobilapps- och dataskyddsfunktioner.

![Bild som visar datasäkerhetsnivåerna för apphantering](./media/what-is-intune/managing-mobile-apps.png)

## <a name="compliance-and-conditional-access"></a>Efterlevnad och villkorsstyrd åtkomst

Intune är integrerat med Azure AD för att ge stöd för en bred uppsättning åtkomstkontrollscenarier. Kräv till exempel att mobila enheter ska följa organisationens standarder som definierats i Intune innan åtkomst ges till nätverkets resurser, t.ex. e-post eller SharePoint. På samma sätt kan du låsa tjänsterna så att de bara är tillgängliga för en specifik uppsättning mobilappar. Du kan till exempel låsa Exchange Online så att tjänsten endast kan nås av Outlook eller Outlook Mobile.

**Onlineresurser**:

- [Ange regler för enheter som tillåter åtkomst till resurser i din organisation](../protect/device-compliance-get-started.md)

- [Vanliga sätt att använda villkorlig åtkomst på med Intune](../protect/conditional-access-intune-common-ways-use.md)

## <a name="how-to-get-intune"></a>Så här skaffar du Intune

Intune är tillgängligt:

- Som fristående [Azure-tjänst](https://go.microsoft.com/fwlink/?linkid=2090973)
- Ingår i [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune) och [Microsoft 365 för myndigheter](https://www.microsoft.com/microsoft-365/government)
- Som [hantering av mobilenheter i Office 365](https://support.office.com/article/choose-between-mdm-for-office-365-and-microsoft-intune-c93d9ab9-efb2-4349-9b93-30c30562ee22), vilken utgörs av vissa begränsade Intune-funktioner

Intune används i många branscher, bland annat [myndigheter](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description), [utbildning](https://www.microsoft.com/en-us/education/intune), [kioskenheter eller särskilda enheter](../configuration/kiosk-settings.md), tillverkning och detaljhandel m.m.

## <a name="next-steps"></a>Nästa steg

- Läs om några av de [vanligt förekommande affärsproblem som Intune hjälper till att lösa](https://docs.microsoft.com/intune/common-scenarios).
- Börja med en [30-dagars kostnadsfri utvärderingsversion av Intune](free-trial-sign-up.md).
- Planera din [migrering till Intune](migration-guide.md).
- Använd din kostnadsfria utvärderingsversion eller prenumeration och gå igenom [Snabbstart: Skapa en e-postenhetsprofil för iOS](../configuration/quickstart-email-profile.md).
