---
title: Skydda e-post till Exchange On-premises | Microsoft Docs
description: "Skydda och styr åtkomsten till företagets e-post på Exchange On-premises med villkorlig åtkomst."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a55071f5-101e-4829-908d-07d3414011fc
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f316b332c3f1b80b9d6af488943298fcfea13741
ms.openlocfilehash: f1d8ecdf64b680940e46afc90dec79d237d80030
ms.lasthandoff: 03/30/2017


---

# <a name="protect-email-access-to-exchange-on-premises-and-legacy-exchange-online-dedicated-with-intune"></a>Skydda e-poståtkomsten till Exchange On-premises och äldre Exchange Online Dedicated med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Du kan konfigurera villkorlig åtkomstkontroll för e-post i Exchange On-premises eller till äldre Exchange Online Dedicated med hjälp av Microsoft Intune.
Mer information om hur villkorlig åtkomst fungerar finns i artikeln [Skydda åtkomsten till e-post och O365-tjänster](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

> [!NOTE]
> Om du har en Exchange Online Dedicated-miljö och vill veta om den har den nya eller gamla konfigurationen kontaktar du din kontoansvariga.

## <a name="before-you-begin"></a>Innan du börjar

Se till att kontrollera följande:

-   Din Exchange-version måste vara **Exchange 2010 eller senare**. Matrisen för Exchange Server-klientåtkomstservern (CAS) stöds.

-   Du måste använda [Intune On-Premises Connector](intune-on-premises-exchange-connector.md), som ansluter [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] till Exchange On-premises. Den här anslutningen gör att du kan hantera enheter via [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-konsolen.

    -   Intune-konsolens lokala Exchange Connector är specifik för din Intune-klientorganisation och kan inte användas med andra innehavare. Vi rekommenderar att du också kontrollerar att Exchange Connector för klienten är installerad **på endast en dator**.

        Du kan hämta anslutningsappen från Intune-administratörskonsolen. En genomgång av hur du konfigurerar den lokala Exchange-anslutningen finns i avsnittet om hur du [konfigurerar den lokala Exchange Connector-anslutningen för lokal eller värdbaserad Exchange](intune-on-premises-exchange-connector.md).

    -   Anslutningsappen kan installeras på valfri dator, förutsatt att den datorn kan kommunicera med Exchange-servern.

    -   Anslutningsappen stöder **Exchange CAS-miljön**. Tekniskt sett kan du installera anslutningsappen direkt på Exchange CAS-servern om du vill. Vi rekommenderar dock inte detta, eftersom det ökar belastningen på servern. När du konfigurerar anslutningen måste du ställa in den så att den kommunicerar med en av Exchange CAS-servrarna.

-   Du måste konfigurera **Exchange ActiveSync** med certifikatbaserad autentisering eller genom att användaren anger autentiseringsuppgifter.

### <a name="device-compliance-requirements"></a>Krav på efterlevnad för enhet

När du konfigurerar och tillämpar principer för villkorlig åtkomst för en användare, och innan användaren kan ansluta till sin e-post, måste användarens **enhet**:

-  Antingen vara en domänansluten dator eller **registrerad** i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-  **Registreras i Azure Active Directory**. Dessutom måste klientens Exchange ActiveSync-ID registreras med Azure Active Directory.

  Registreringstjänsten för Azure AD-enhet aktiveras automatiskt för Intune- och Office 365-kunder. Kunder som redan har använt ADFS Device Registration Service ser inte registrerade enheter i lokala Active Directory-kataloger. **Detta gäller inte för Windows-datorer och Windows Phone-enheter**.

-   Vara **kompatibel** med eventuella [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-efterlevnadsprinciper som har distribuerats till den enheten.

### <a name="how-conditional-access-works-with-exchange-on-premises"></a>Så här fungerar villkorlig lokal åtkomst till Exchange on-premises

Följande diagram illustrerar flödet som används av principer för villkorlig åtkomst för Exchange On-premises för att utvärdera om enheter ska tillåtas eller blockeras.

![Diagram som visar beslutspunkter som avgör om en enhet kan komma åt Exchange On-premises eller om den ska blockeras](../media/ConditionalAccess8-2.png)

Om en princip för villkorlig åtkomst inte uppfylls, öppnas ett tidsfönster på 10 minuter mellan det att enheten blockeras och användaren får något av följande karantänmeddelanden vid inloggning:

- Om enheten inte är registrerad i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] eller i Azure Active Directory visas ett meddelande med instruktioner för att installera företagsportalappen, registrera enheten och aktivera e-post. Den här processen associerar även enhetens Exchange ActiveSync-ID med enhetsposten i Azure Active Directory.

-   Om enheten inte är kompatibel visas ett meddelande som leder användaren till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-företagsportalens webbplats eller till företagsportalappen, som innehåller mer information om problemet och hur det kan åtgärdas.

## <a name="support-for-mobile-devices"></a>Stöd för mobila enheter
Följande stöds:
-   Windows Phone 8.1 och senare.

-   Den interna e-postappen för iOS.

-   Exchange ActiveSync-e-postklienter som Gmail på Android 4 eller senare.
-   Exchange ActiveSync-e-postklienter och **Android for Work-enheter:** Endast **Gmail**- och **Nine Work**-apparna i **arbetsprofilen** stöds på Android for Work-enheter. För att villkorlig åtkomst ska fungera med Android for Work måste du distribuera en e-postprofil för Gmail- eller Nine Work-appen och distribuera de apparna som en obligatorisk installation. 

<!---
[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]
--->
> [!NOTE] 
> Microsoft Outlook-appen for Android and iOS stöds inte.

## <a name="support-for-pcs"></a>Stöd för datorer
Följande stöds:
-   **E-post**-programmet i Windows 8.1 och senare (om datorn har registrerats med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).

##  <a name="configure-a-conditional-access-policy"></a>Konfigurera en princip för villkorlig åtkomst

1.  I [Microsoft Intune-administrationskonsolrn](https://manage.microsoft.com) väljer du **Princip** > **Villkorlig åtkomst** > **Exchange On-premises-princip**.
![IntuneSA5aSelectExchOnPremPolicy](../media/IntuneSA5aSelectExchOnPremPolicy.png)

2.  Konfigurera principen med de inställningar som du behöver: ![Skärmbild av sidan för Exchange On-premises-princip](../media/IntuneSA5bExchangeOnPremPolicy.png)

  - **Blockera e-postappar från att få åtkomst till Exchange On-premises om enheten inte är kompatibel med eller inte är registrerad i Microsoft Intune:** Om du väljer det här alternativet kan inte enheter som inte hanteras av [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] eller som inte är kompatibla med en efterlevnadsprincip komma åt Exchange-tjänster.

  - **Åsidosätt standardregel – Tillåt att registrerade och kompatibla enheter alltid får åtkomst till Exchange:** Om du väljer det här alternativet kan enheter som är registrerade i Intune och kompatibla med efterlevnadsprinciper komma åt Exchange.
  Den här regeln åsidosätter **standardregeln**, vilket innebär att även om du ställer in **standardregeln** för att blockera åtkomstförsök eller sätta dem i karantän så kommer registrerade och kompatibla enheter fortfarande att kunna få åtkomst till Exchange.

  - **Målgrupper:** Välj de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-användargrupper som måste registrera sina enheter med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] innan de kan komma åt Exchange.

  - **Undantagna grupper:** Välj de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-användargrupper som är undantagna från principen för villkorlig åtkomst. Användare i den här listan undantas även om de också finns med i listan **Målgrupper**.

  - **Plattformsundantag:** Välj **Lägg till regel** om du vill konfigurera en regel som definierar åtkomstnivåer för angivna familjer och modeller av mobila enheter. Eftersom dessa enheter kan tillhöra vilken typ som helst kan du även konfigurera enhetstyper som inte stöds av [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

  - **Standardregel:** För en enhet som inte omfattas av någon av de andra reglerna kan du välja att ge enheten åtkomst till Exchange, blockera den eller placera den i karantän. När du ställer in regeln för att tillåta åtkomst för enheter som är registrerade och kompatibla beviljas e-poståtkomst automatiskt för iOS-, Windows- och Samsung KNOX-enheter. Användaren behöver inte gå igenom någon särskild process för att få sin e-post.
      - Användare av Android-enheter som inte kör Samsung KNOX får ett karantänmeddelande med stegvisa anvisningar för att verifiera registreringen och efterlevnaden innan de kan komma åt e-posten. Om du ställer in regeln för att blockera åtkomst eller sätta enheten i karantän blir alla enheter blockerade från att få åtkomst till Exchange oavsett om de redan har registrerats i Intune eller inte. Om du vill förhindra att registrerade och kompatibla enheter påverkas av den här regeln markerar du rutan **Åsidosätt standardregel**.
>[!TIP]
>Om din avsikt är att först blockera alla enheter innan du beviljar åtkomst till e-posten väljer du regeln Blockera åtkomst eller Karantän. Standardregeln gäller för alla enhetstyper. Det betyder att även enhetstyper som du konfigurerar som plattformsundantag och som inte stöds av [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] påverkas.

  - **Meddelande till användare:** Förutom e-postmeddelandet som skickas från Exchange skickar Intune ett e-postmeddelande med stegvisa anvisningar för att låsa upp enheten. Du kan redigera standardmeddelandet och anpassa det efter dina behov. Om användarens enhet blockeras innan Intunes e-postmeddelande med instruktionerna har kommit fram (det här meddelandet skickas till användarens Exchange-postlåda) kan användaren använda en enhet som inte är blockerad eller en annan metod för att komma åt Exchange och läsa meddelandet.
      - Detta är särskilt viktigt om **standardregeln** har konfigurerats att blockera eller placera enheter i karantän. I så fall måste användaren besöka sin appbutik, ladda ned Microsofts företagsportalsapp och registrera sin enhet. Detta gäller iOS-, Windows- och Samsung KNOX-enheter. Du måste skicka e-postmeddelandet om karantän till ett alternativt e-postkonto för enheter som inte kör Samsung KNOX. Användaren måste kopiera e-postmeddelandet till sin blockerade enhet för att kunna slutföra registreringen och efterlevnadsprocessen.
  > [!NOTE]
  > För att Exchange ska kunna skicka e-postmeddelandet måste du ange det konto som används för att skicka meddelandet.
  >
  > Mer information finns i [Konfigurera lokal Exchange-anslutning för lokal eller värdbaserad Exchange](intune-on-premises-exchange-connector.md).

3.  När du är klar väljer du **Spara**.

-   Du behöver inte använda principen för villkorlig åtkomst. Den träder i kraft omedelbart.

-   När en användare har konfigurerat en Exchange ActiveSync-profil kan det ta en till tre timmar innan enheten blockeras (om den inte hanteras av [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).

-   Om en blockerad användare sedan registrerar enheten med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och åtgärdar efterlevnadsproblemet avblockeras e-poståtkomsten inom två minuter.

-   Om användaren avregistrerar sig från [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] kan det ta en till tre timmar innan enheten blockeras.

**Några exempelscenarier som beskriver hur du konfigurerar principer för villkorlig åtkomst som skyddar enhetsåtkomsten finns i [Exempelscenarier för skydd av e-poståtkomst](restrict-email-access-example-scenarios.md).**

## <a name="next-steps"></a>Nästa steg
-   [Skydda åtkomsten till SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

-   [Skydda åtkomsten till Skype för företag – Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)

