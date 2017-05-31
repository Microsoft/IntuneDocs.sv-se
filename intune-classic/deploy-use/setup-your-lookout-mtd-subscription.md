---
title: Konfigurera din prenumeration med Lookout | Microsoft Docs
description: "Detta avsnitt tillhandahåller information om hur du konfigurerar Lookout-skydd mot enhetshot."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3c777d8857fd177e5a27840ab8a97c8a137aa189
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="set-up-your-lookout-mobile-threat-defense-subscription"></a>Konfigurera din prenumeration för Lookout Mobile Threat Defense

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Följande steg krävs för att konfigurera Lookout Mobile Threat Defense:

| #        |Steg  |
| ------------- |:-------------|
| 1 | [Hämta Azure AD-information](#collect-azure-ad-information) |
| 2 | [Konfigurera din prenumeration](#configure-your-subscription) |
| 3 | [Konfigurera registreringsgrupper](#configure-enrollment-groups) |
| 4 | [Konfigurera tillståndssynkronisering](#configure-state-sync) |
| 5 | [Konfigurera information om e-postmottagare av felrapporter](#configure-error-report-email-recipient-information) |
| 6 | [Konfigurera registreringsinställningar](#configure-enrollment-settings) |
| 7 | [Konfigurera e-postaviseringar](#configure-email-notifications) |
| 8 | [Konfigurera hotklassificering](#configure-threat-classification) |
| 1 | [Bevaka registrering](#watching-enrollment) |


> [!IMPORTANT]
> En befintlig Lookout Mobile Endpoint Security-klient som inte redan är associerad med Azure AD-klient kan inte användas för integreringen med Azure AD och Intune. Kontakta Lookout-supporten för att skapa en ny Lookout Mobile Endpoint Security-klient. Använd den nya klienten att publicera dina Azure AD-användare.

## <a name="collect-azure-ad-information"></a>Hämta Azure AD-information
Din Lookout Mobility Endpoint Security-klient kommer att associeras med din Azure AD-prenumeration för att integrera Lookout med Intune. Om du vill aktivera tjänsteprenumerationen för Lookout Mobile Threat Defense, behöver Lookout-supporten (enterprisesupport@lookout.com) följande information:  

* **Azure AD-klient-ID**
* **Azure AD-gruppobjekt-ID** för **fullständig** Lookout-konsolåtkomst
* **Azure AD-gruppobjekt-ID** för **begränsad** Lookout-konsolåtkomst (valfritt)

Använd följande steg för att samla in den information du måste förse Lookout-supportteamet med.

1. Logga in på [Azure AD-hanteringsportalen](https://manage.windowsazure.com) och välj din prenumeration. 
  ![skärmbild av Azure AD-sidan som visar namnet på klienten](../media/mtp/aad_tenant_name.png)
2. När du väljer namnet på din prenumeration måste den URL som bildas omfatta prenumerations-ID.  Om du har problem med att hitta ditt prenumerations-ID kan du läsa den här [Microsoft support-artikeln](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b) och få hjälp. 
3. Hitta ditt grupp-ID för Azure AD. Lookout-konsolen stöder två åtkomstnivåer:  
  * **Fullständig åtkomst:** Azure AD-administratören kan skapa en grupp för användare som kommer att ha fullständig åtkomst och de kan även skapa en grupp med användare som har begränsad tillgång.  Endast användare i dessa grupper kommer att kunna logga in till **Lookout-konsolen**.
  * **Begränsad åtkomst:** Användarna i den här gruppen kommer inte ha åtkomst till ett flertal konfigurations- och registreringsrelaterade moduler i Lookout-konsolen, och ha skrivskyddad åtkomst till **Säkerhetsprincip**-modulen i Lookout-konsolen.  

  Mer information om behörigheterna finner du i [den här artikeln](https://personal.support.lookout.com/hc/articles/114094105653) på webbplatsen Lookout.

  **Grupp-objekt-ID:t** finns på **egenskapssidan** för gruppen i **Azure AD-hanteringskonsolen**.

  ![skärmbild av egenskapssidan med Grupp-ID-fältet markerat](../media/mtp/aad_group_object_id.png)

4. Kontakta Lookout-supporten (e-post: enterprisesupport@lookout.com) när du har samlat in den här informationen. Lookout-supporten kommer att samarbeta med din primära kontakt för att publicera din prenumeration och skapa ditt företagskonto för Lookout med hjälp av informationen som du samlat in.

## <a name="configure-your-subscription"></a>Konfigurera din prenumeration
1. När Lookout har skapat ditt Lookout Enterprise-konto skickas ett e-postmeddelande från Lookout till den primära kontakten för ditt företag med en länk till inloggnings-url-adressen: https://aad.lookout.com/les?action=consent.

2.  Den första inloggningen på Lookout-konsolen måste ske med ett användarkonto som har Azure AD-rollen global administratör för att kunna registrera Azure AD-klienten. Inloggningen kräver inte denna nivå på Azure AD-behörighet senare. En samtyckessida visas. Välj **Acceptera** för att slutföra registreringen.

  ![skärmbild som visar inloggningssidan första gången användaren loggar in i Lookout-konsolen](../media/mtp/lookout_mtp_initial_login.png) När du har accepterat och godkänt villkoren omdirigeras du till Lookout-konsolen.

  Se [felsöka Lookout-integrering](/intune-classic/troubleshoot/troubleshooting-lookout-integration) om du vill ha hjälp med inloggningsproblem.

3.  I [Lookout-konsolen](https://aad.lookout.com) går du till **System**-modulen och väljer fliken **Kopplingar** och sedan **Intune**.

  ![skärmbild som visar Lookout-konsolen med fliken för anslutningar öppen och alternativet Intune markerat](../media/mtp/lookout_mtp_setup-intune-connector.png)

4.  Välj **Kopplingar** > **Anslutningsinställningar** och ange **Pulsslagsfrekvens** i minuter.

  ![skärmbild av fliken för anslutningsinställningar som visar hur pulsslagsfrekvensen konfigurerats](../media/mtp/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>Konfigurera registreringsgrupper
1. Du bör skapa en Azure AD-säkerhetsgrupp i [Azure AD-hanteringsportalen](https://manage.windowsazure.com) som innehåller ett litet antal användare för att testa Lookout-integreringen.

  Alla Intune-registrerade enheter som stöds av Lookout som tillhör användare i en registreringsgrupp som har identifierats och har stöd registreras, och dessa enheter kan aktiveras i Lookout-skydd mot enhetshot.

2. I [Lookout-konsolen](https://aad.lookout.com) går du till **System**-modulen, väljer fliken **Anslutningar** och väljer **Registreringshantering** för att definiera en uppsättning användare vars enheter ska registreras med Lookout. Lägg till Azure AD-säkerhetsgruppens **Visningsnamn** för registrering.

  ![skärmbild som visar sidan registrering av Intune-anslutning](../media/mtp/lookout-mtp-enrollment.png)

  >[!IMPORTANT]
  > Detta **Visningsnamn** är skiftlägeskänsligt så som visas i **Egenskaper** i säkerhetsgruppen i Azure-portalen. Som bilden nedan visar är säkerhetsgruppens **Visningsnamn** en kamelnotation medan titeln endast använder gemener. I Lookout-konsolen är skiftläget för **Visningsnamn** samma som för säkerhetsgruppen.
  >![skärmbild av egenskaper-sidan för Azure Active Directory-tjänsten i Azure-portalen](../media/mtp/aad-group-display-name.png)

  Det rekommenderas att använda de inställningar som är standard (fem minuter) för tidsintervallerna då nya enheter eftersöks.

  **Aktuella begränsningar:**
  * Lookout kan inte validera visningsnamn för gruppen.  Se till att fältet **VISNINGSNAMN** i Azure-portalen exakt matchar Azure AD-säkerhetsgruppen.
  * Det går inte att skapa kapslade grupper.  Azure AD-säkerhetsgrupper som används i Lookout får endast innehålla användare. De får inte innehålla andra grupper.

3.  Första gången en användare öppnar Lookout for Work-appen på en enhet efter att en grupp har lagts till aktiveras enheten i Lookout.

4.  När du är nöjd med resultaten kan du utöka registreringen till ytterligare användargrupper.

## <a name="configure-state-sync"></a>Konfigurera tillståndssynkronisering
För alternativet **Synkronisering av programtillstånd** anger du vilken typ av data som ska skickas till Intune.  Både enhetsstatus och hotstatus krävs för att Lookout Intune-integrationen ska fungera korrekt.  De här verktygen är aktiverade som standard.

## <a name="configure-error-report-email-recipient-information"></a>Konfigurera information om e-postmottagare av felrapporter
Ange den e-postadress som ska ta emot felrapporter i alternativet **Error Management** (Felhantering).

![skärmbild som visar sidan för felhantering för Intune Connector](../media/mtp/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>Konfigurera registreringsinställningar
I modulen **System** på sidan **Kopplingar** anger hur många dagar innan en enhet betraktas som frånkopplad.  Frånkopplade enheter betraktas som icke-kompatibla och kommer att blockeras från att komma åt företagsprogrammen baserat på principer för villkorlig åtkomst i Intune. Du kan ange värden mellan 1 och 90 dagar.

![](../media/mtp/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>Konfigurera e-postaviseringar
Logga in i [Lookout-konsolen](https://aad.lookout.com) med det användarkonto som ska ta emot meddelanden om du vill ta emot e-postaviseringar för hot. På fliken **Inställningar** i **System**-modulen väljer du de hotnivåer som ska generera meddelanden och ställer in dem på **PÅ**. Spara ändringarna.

![skärmbild som visar sidan för inställningar där användarkontot visas](../media/mtp/lookout-mtp-email-notifications.png) Om du inte längre vill ta emot e-postaviseringar väljer du alternativet **AV** för meddelanden och sparar ändringarna.

### <a name="configure-threat-classification"></a>Konfigurera hotklassificering
Lookout Mobile Threat Defense klassificerar olika typer av mobila hot. [Lookout-hotklassificeringar](http://personal.support.lookout.com/hc/articles/114094130693) är kopplade till standardrisknivåer. Dessa kan ändras när som helst för att passa företagets krav.

![skärmbild av sidan för principer som visar hot och klassificeringar](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Risknivåerna är en viktig del av Mobile Threat Defense eftersom Intune-integreringen beräknar enhetens efterlevnad enligt dessa risknivåer vid körning. Intune-administratören anger en regel i principen för att identifiera att en enhet är icke-kompatibel om den har ett aktivt hot med miniminivån **Hög**, **Medel** eller **Låg**. Principen för hotklassificering i Lookout Mobile Threat Defense styr direkt efterlevnadsberäkningen för enheten i Intune.

## <a name="watching-enrollment"></a>Bevakar registreringen
När installationen är klar börjar Lookout Mobile Threat Defense avsöka Azure AD efter enheter som motsvarar de angivna registreringsgrupperna.  Du hittar information om de enheter som registrerats i modulen Enheter.  Den första statusen för enheterna är ”väntar”.  Enhetens status ändras när Lookout for Work-appen har installerats, öppnats och aktiverats på enheten.  Mer information om hur du skickar Lookout for work-appen till enheten finner du i artikeln [Configure and deploy Lookout for work apps](configure-deploy-lookout-for-work-app.md) (Konfigurera och distribuera Lookout for work-appar).
## <a name="next-steps"></a>Nästa steg
[Aktivera anslutning till Lookout MTP i Intune](/intune-classic/deploy-use/enable-lookout-mtd-connection)

