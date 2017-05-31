---
title: "Skydda Skype för företag – Online | Microsoft Docs"
description: "Skydda och styr åtkomsten till Skype för företag – Online med villkorlig åtkomst."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1b2d7125-f63f-43cf-ac1e-94fbedf2a7e8
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 46dc5bc7d7b4107b87a41aa8a454453d591d0ef9
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="protect-access-to-skype-for-business-online-with-microsoft-intune"></a>Skydda åtkomsten till Skype för företag – Online med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Du kan använda principen för villkorlig åtkomst för **Skype för företag – Online** om du vill kontrollera åtkomsten till Skype för företag – Online.
Villkorlig åtkomst består av två komponenter:
- En princip för enhetsefterlevnad som enheten måste uppfylla för att anses vara kompatibel.
- En princip för villkorlig åtkomst där du anger de villkor som enheten måste uppfylla för att du ska kunna komma åt tjänsten.
Mer information om hur villkorlig åtkomst fungerar finns i artikeln [Skydda åtkomsten till e-post och O365-tjänster](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

När en målanvändare försöker använda Skype för företag – Online på sin enhet görs följande utvärdering:

![Diagram som visar beslutspunkterna som används för att avgöra om en enhet får åtkomst till Skype för företag – Online eller blockeras](../media/ConditionalAccess_SkypeforBusiness.png)

**Innan** du konfigurerar en princip för villkorlig åtkomst för Skype för företag – Online måste du:
- Ha en **prenumeration på Skype för företag – Online** och tilldela användare Skype för företag – Online-licenser.
- Ha en **Enterprise Mobility + Security-prenumeration (EMS)** eller en **Azure Active Directory Premium-prenumeration (Azure AD)**, och användarna måste ha licens för EMS eller Azure AD. Mer information finns på [Priser för Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) eller [Priser för Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

-   [Aktivera modern autentisering](/intune-classic/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) för Skype för företag – Online.
-  Låt alla dina användare använda **Skype för företag – Online**. Om du har en distribution med både Skype för företag – Online och Skype för företag lokalt tillämpas inte principen för villkorlig åtkomst på användarna.

Enheten som behöver åtkomst till Skype för företag – Online måste:

-   Vara en **Android**- eller **iOS**-enhet.

-   Vara **registrerad** i Intune.

-   Vara **kompatibel** med alla distribuerade efterlevnadsprinciper för Intune.


Enhetens tillstånd lagras i Azure Active Directory som beviljar eller blockerar åtkomst baserat på de villkor som du anger.

Om ett villkor inte är uppfyllt, kommer användaren att visas ett följande meddelanden när de loggar in:

-   Om enheten inte har registrerats för Intune, eller registrerats i Azure Active Directory, visas ett meddelande med instruktioner om hur du installerar företagsportalsappen och registrerar dig.

-   Om enheten inte är kompatibel visas ett meddelande som leder användaren till Intune-företagsportalens webbplats eller till företagsportalappen som innehåller mer information om problemet och hur det kan åtgärdas.

## <a name="configure-conditional-access-for-skype-for-business-online"></a>Konfigurera villkorlig åtkomst för Skype för företag – Online

### <a name="step-1-configure-azure-active-directory-security-groups"></a>Steg 1: Konfigurera Azure Active Directory-säkerhetsgrupper
Konfigurera säkerhetsgrupper för Azure Active Drive Directory för villkorlig åtkomstpolicy innan du börjar. Du kan konfigurera dessa grupper i **administrationscenter för Office 365**. Dessa grupper används för att bestämma målanvändare eller undantagna användare för principen. När en användare är angiven som mål för principen, måste varje enhet de använder vara godkänd för att få åtkomst till resurser.

Du kan ange två typer av grupper för principen för Skype för företag – Online:

-   **Målgrupper**: Innehåller användargrupper för vilka principen gäller.

-   **Undantagna grupper**: Innehåller användargrupper som är undantagna från principen.

Om en användare finns i båda grupperna, kommer de att vara befriade från policyn.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Steg 2: Ställ in och distribuera en efterlevnadsprincip
[Skapa](create-a-device-compliance-policy-in-microsoft-intune.md) och [distribuera](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) en efterlevnadsprincip för alla enheter som påverkas av principen. Detta motsvarar alla enheter som används av användarna i **Målgrupper**.

> [!NOTE]
> Medan efterlevnadsprinciper distribueras till Intune-grupper är principer för villkorlig åtkomst avsedda för Azure Active Directory-säkerhetsgrupper.


> [!IMPORTANT]
> Om du inte har distribuerat någon efterlevnadsprincip behandlas enheterna som kompatibla.

När du är klar, fortsätt till **Steg 3**.

### <a name="step-3-configure-the-skype-for-business-online-policy"></a>Steg 3: Konfigurera principen för Skype för företag – Online
Nu ska du konfigurera principen så att endast hanterade och kompatibla enheter kan komma åt Skype för företag – Online. Denna policy kommer att lagras i Azure Active Directory.

1.  I [Microsoft Intune Administrationskonsol](https://manage.microsoft.com) väljer du **Princip** > **Villkorlig åtkomst** > **Princip för Skype för företag – Online**.

  ![Skärmbild av sidan för principen för villkorlig åtkomst för Skype för företag – Online](./media/conditional_access_SFBPolicy.png)

2.  Välj **Aktivera princip för villkorlig åtkomst**.

3.  Under **Programåtkomst** kan du välja att använda principen för villkorlig åtkomst för:

    -   **iOS**

    -   **Android**

4.  Välj **Ändra** under **Målgrupper** och välj de Azure Active Directory-säkerhetsgrupper som principen ska gälla för. Du kan välja att omfatta alla användare eller bara en viss grupp med användare.

5.  Under **Undantagna Grupper** kan du alternativt välja **Modifiera** om det finns säkerhetsgrupper i Azure Active Directory som ska vara undantagna principen.

6.  När du är klar väljer du **Spara**.

Nu har du konfigurerat villkorlig åtkomst för Skype för företag – Online. Du behöver inte använda principen för villkorlig åtkomst. Den träder i kraft omedelbart.


## <a name="monitor-the-compliance-and-conditional-access-policies"></a>Övervaka efterlevnaden och villkorlig åtkomstpolicy
I arbetsytan **Grupper** , kan du se statusen för villkorlig åtkomst för dina enheter.

Välj en mobil enhetsgrupp. Klicka på fliken **Enheter**, välj något av följande **Filter**:

* **Enheter som inte är registrerade i AAD**: Dessa enheter blockeras från Skype för företag – Online.

* **Enheter som inte är kompatibla**: Dessa enheter blockeras från Skype för företag – Online.

* **Enheter som är registrerade i AAD och kompatibla**: Dessa enheter kan komma åt Skype för företag – Online.

