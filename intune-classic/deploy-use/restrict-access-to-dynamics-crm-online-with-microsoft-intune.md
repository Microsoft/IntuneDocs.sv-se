---
title: Protect Dynamics CRM Online
description: Skydda och styr åtkomsten till Dynamics CRM Online med villkorlig åtkomst.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f1c4522b-5a34-4f5a-89d2-7809c4352af7
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e2f720c8a6613884397111c2a421fa1cfdc0eb53
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31021803"
---
# <a name="protect-access-to-dynamics-crm-online-with-intune"></a>Skydda åtkomsten till Dynamics CRM Online med Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Du kan kontrollera åtkomsten till Microsoft Dynamics CRM Online från iOS- och Android-enheter med villkorlig åtkomst i Microsoft Intune.  Villkorlig åtkomst i Intune består av två komponenter:
* En [princip för enhetsefterlevnad](introduction-to-device-compliance-policies-in-microsoft-intune.md) som enheten måste uppfylla för att anses vara kompatibel.
* En [princip för villkorlig åtkomst](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) där du anger de villkor som enheten måste uppfylla för att komma åt tjänsten.

Om du vill ha mer information om hur villkorlig åtkomst fungerar läser du artikeln [Skydda åtkomsten till e-post, O365 och andra tjänster](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

> [!IMPORTANT]
> Om du vill distribuera villkorlig åtkomst måste du ha prenumerationer för Intune och Azure Active Directory Premium och användarna måste ha licens för båda produkterna. **Enterprise Mobility + Security-prenumerationen (EMS)** innehåller både Intune- och Azure Active Directory Premium-prenumerationer. Mer information finns på [sidan med priser för Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing). Om du inte har EMS-prenumerationen kan du skaffa en Azure Active Directory Premium-prenumeration. Mer information finns på [sidan med priser för Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

När en målanvändare försöker använda Dynamics CRM-appen på sin enhet görs följande utvärdering:

![Ett diagram som visar de beslutspunkter som används för att avgöra om en enhet ska beviljas åtkomst till en tjänst eller om den ska blockeras](../media/mdm-ca-dynamics-crm-flow-diagram.png)

Den enhet som behöver åtkomst till Dynamics CRM Online måste vara:
* En **Android**- eller **iOS**-enhet.
* **Registrerad** med Intune.
* **Kompatibel** med alla distribuerade efterlevnadsprinciper för Intune.

Enhetens tillstånd lagras i Azure Active Directory som beviljar eller blockerar åtkomst baserat på de villkor som du anger.

Om ett villkor inte är uppfyllt, kommer användaren att visas ett följande meddelanden när de loggar in:
* Om enheten inte har registrerats för Intune, eller registrerats i Azure Active Directory, visas ett meddelande med instruktioner om hur du installerar företagsportalsappen och registrerar dig.
* Om enheten inte är godkänd visas ett meddelande som leder användaren till webbplatsen för Microsoft Intunes företagsportal eller företagsportalsappen där de kan hitta information om problemet och hur det kan åtgärdas.

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Konfigurera villkorlig åtkomst för Dynamics CRM Online  
### <a name="step-1-configure-active-directory-security-groups"></a>Steg 1: Konfigurera Active Directory-säkerhetsgrupper

Konfigurera säkerhetsgrupper för Azure Active Drive Directory för villkorlig åtkomstpolicy innan du börjar. Du kan konfigurera dessa grupper i **administrationscenter för Office 365**. Du använder de här grupperna när du vill fokusera på eller undanta användare från principen. När en användare är angiven som mål för en policy, måste varje enhet de använder vara godkänd för att få åtkomst till resurser.

Du kan ange två typer av grupper för Dynamics CRM-principen:
* **Målgrupper**. Innehåller användargrupper för vilka principen gäller.
* **Undantagna grupper**. Innehåller användargrupper som är undantagna från principen.

Användare som finns i båda grupperna undantas från principen.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Steg 2: Ställ in och distribuera en efterlevnadsprincip
[Skapa](create-a-device-compliance-policy-in-microsoft-intune.md) en efterlevnadsprincip och [distribuera](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) den till alla enheter som påverkas av principen. Detta motsvarar alla de enheter som användarna i målgrupperna använder.

> [!NOTE]
> Medan efterlevnadsprinciper distribueras till Intune-grupper är principer för villkorlig åtkomst avsedda för Azure Active Directory-säkerhetsgrupper.

> [!IMPORTANT]
> Om du inte har distribuerat någon efterlevnadsprincip behandlas enheterna som kompatibla.

När du är klar, fortsätt till Steg 3.
### <a name="step-3-configure-the-dynamics-crm-policy"></a>Steg 3: Konfigurera Dynamics CRM-principen
Konfigurera sedan policyn som kräver att enbart hanterade och godkända enheter kan komma åt Dynamics CRM. Denna policy kommer att lagras i Azure Active Directory.

1. Välj **Princip > Villkorlig åtkomst > Dynamics CRM Online-princip** i Microsoft Intune-administratörskonsolen.

   ![Skärmbild av sidan för principer för villkorlig åtkomst för Dynamics CRM Online](../media/mdm-ca-dynamics-crm-policy-configuration.png)

2. Välj principen **Aktivera villkorlig åtkomst**.
3. Under **Programåtkomst**kan du välja att tillämpa en princip för villkorlig åtkomst på:
   * **iOS**
   * **Android**
4. Välj **Ändra** under **Målgrupper** och välj de Azure Active Directory-säkerhetsgrupper som principen ska gälla för. Du kan välja att rikta detta till alla användare eller bara en viss grupp med användare.
5. Under **Undantagna Grupper** kan du alternativt välja **Modifiera** om det finns säkerhetsgrupper i Azure Active Directory som ska vara undantagna principen.
6. När du är klar väljer du **Spara**.

Nu har du konfigurerat villkorlig åtkomst för Dynamics CRM. Du behöver inte använda principen för villkorlig åtkomst. Den träder i kraft omedelbart.
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>Övervaka efterlevnaden och villkorlig åtkomstpolicy

I arbetsytan **Grupper** , kan du se statusen för villkorlig åtkomst för dina enheter.

Välj en mobil enhetsgrupp och välj sedan något av följande **filter** på fliken **Enheter**:
* **Enheter som inte är ADD-registrerade**. De här enheterna blockeras från Dynamics CRM.
* **Enheter som inte är kompatibla**. De här enheterna blockeras från Dynamics CRM.
* **Enheter som är AAD-registrerade och uppfyller kraven**. De här enheterna har åtkomst till Dynamics CRM.

##  <a name="next-steps"></a>Nästa steg
* [Skydda åtkomsten till Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)

* [Skydda åtkomsten till Exchange lokalt](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
* [Skydda åtkomsten till SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

* [Skydda åtkomsten till Skype för företag – Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
