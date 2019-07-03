---
title: Konfigurera Lookout-integreringen med Microsoft Intune
titleSuffix: Microsoft Intune
description: Läs mer om hur du integrerar Intune med Lookout Endpoint Security som Mobile Threat Defense-lösning för att styra mobila enheters åtkomst till företagsresurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be2e9371288961d0afdf7ad6e8cfec8f734087f6
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529998"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>Konfigurera Lookout Mobile Endpoint Security-integration med Intune
Med en miljö som uppfyller [kraven](lookout-mobile-threat-defense-connector.md#prerequisites) kan du integrera Lookout Mobile Endpoint Security med Intune. Informationen i den här artikeln vägleder dig genom stegen för att integrera och konfigurera viktiga inställningar i Lookout för användning med Intune.  

> [!IMPORTANT]
> En befintlig Lookout Mobile Endpoint Security-klient som inte redan är associerad med Azure AD-klient kan inte användas för integreringen med Azure AD och Intune. Kontakta Lookout-supporten för att skapa en ny Lookout Mobile Endpoint Security-klient. Använd den nya klienten att publicera dina Azure AD-användare.

## <a name="collect-azure-ad-information"></a>Hämta Azure AD-information  
Om du vill integrera Lookout med Intune, associerar du Mobility Endpoint Security-klienten med din Azure AD-prenumeration.

Om du vill aktivera prenumerationsintegrering för Lookout Mobile Endpoint Security med Intune, måste du tillhandahålla följande information till Lookout-supporten (enterprisesupport@lookout.com):  

- **Katalog-ID för Azure AD-klient**  

- **Objekts-ID för Azure AD-grupp** för gruppen med **fullständig** konsolåtkomst för Lookout Mobile Endpoint Security (MES).  
  Du skapar den här användargruppen i Azure AD för de användare som har *fullständig åtkomst* till att logga in på **Lookout-konsolen**. Användarna måste vara medlem i den här gruppen eller den valfria gruppen med *begränsad åtkomst* för att kunna att logga in på Lookout-konsolen. 

- **Objekts-ID för Azure AD-grupp** för gruppen med **begränsad** konsolåtkomst till Lookout MES-konsolen *(valfri grupp)* . 
  Den här valfria användargruppen skapar du i Azure AD för användare som inte ska ha åtkomst till flera konfigurations- och registreringsrelaterade moduler i Lookout-konsolen. I stället får dessa användare skrivskyddad åtkomst till den **säkerhetsprincipsmodulen** i Lookout-konsolen. Användarna måste vara medlem i den här valfria gruppen, eller den med obligatorisk *fullständig åtkomst*, för att kunna att logga in på Lookout-konsolen.

 > [!TIP] 
 > Mer information om behörigheterna finner du i [den här artikeln](https://personal.support.lookout.com/hc/articles/114094105653) på webbplatsen Lookout.

### <a name="collect-information-from-azure-ad"></a>Samla in information från Azure AD 

1. Logga in på [Azure-portalen](https://portal.azure.com) med ett globalt administratörskonto.

2. Gå till **Azure Active Directory** > **Egenskaper** och leta upp ditt **Katalog-ID**. Använd knappen *Kopiera* för att kopiera ditt katalog-ID och spara det i en textfil.

   ![Azure AD-egenskaper](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. Leta sedan reda på ditt Azure AD-grupp-ID för de konton som du använder för att bevilja Azure AD-användare åtkomst till Lookout-konsolen. En grupp är för *fullständig åtkomst* och den andra, för *begränsad åtkomst*, är valfri. Hämta *objekt-ID* för varje konto:  
   1. Gå till **Azure Active Directory** > **Grupper** för att öppna fönstret *Grupper – Alla grupper*.  

   2. Välj den grupp som du skapade för *fullständig åtkomst* för att öppna dess fönster *Översikt*.  

   3. Använd knappen *Kopiera* för att kopiera aktuellt katalog-ID och spara det sedan i en textfil.  

   4. Upprepa processen för gruppen med *begränsad åtkomst*, om du använder den gruppen.  

      ![Objekts-ID för Azure AD-grupp](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   Kontakta Lookout-supporten (e-post: enterprisesupport@lookout.com) när du har samlat in den här informationen. Lookout-supporten kommer att samarbeta med din primära kontakt för att publicera din prenumeration och skapa ditt Lookout Enterprise-konto med hjälp av den information som du tillhandahåller.  

## <a name="configure-your-lookout-subscription"></a>Konfigurera din Lookout-prenumeration  
Efter att Lookout-supporten har skapat ditt Lookout Enterprise-konto, skickar de ett e-postmeddelande till ditt företags primära kontakt med en länk till webbadressen för inloggning: https://aad.lookout.com/les?action=consent. 

### <a name="initial-sign-in"></a>Första inloggningen  
Vid den första inloggningen på Lookout MES-konsolen visas en samtyckessida (https://aad.lookout.com/les?action=consent). En global Azure AD-administratör behöver bara logga bara in och välja **Acceptera**. Efterföljande inloggningar kräver inte att användaren har Azure AD-behörighet på den här nivån. 

 En samtyckessida visas. Välj **Acceptera** för att slutföra registreringen. 
   ![skärmbild av sidan för den första inloggningen i Lookout-konsolen](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

När du accepterar och samtycker, omdirigeras du till Lookout-konsolen.

När den första inloggningen är klar och samtycket har getts, omdirigeras användare som loggar in från https://aad.lookout.com till MES-konsolen. Om samtycket ännu inte har beviljats, resulterar alla inloggningsförsök i en felaktig inloggning.

### <a name="configure-the-intune-connector"></a>Konfigurera Intune Connector  
Följande procedur förutsätter att du tidigare har skapat en användargrupp i Azure AD för testning av din Lookout-distribution. Det bästa sättet är att börja med en liten grupp användare så att dina Lookout- och Intune-administratörer får bekanta sig med produktintegreringarna. När de är bekanta med systemet kan du utöka registreringen till ytterligare användargrupper.

1. Logga in på [Lookout MES-konsolen](https://aad.lookout.com) och gå till **System** > **Anslutningar** och välj sedan **Lägg till anslutningsprogram**.  Välj **Intune**.

   ![Bild som visar Lookout-konsolen med alternativet Intune på fliken för anslutningar](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. I fönstret *Microsoft Intune* väljer du **Anslutningsinställningar** och specificerar **pulsslagsfrekvensen** i minuter. 

   ![Bild av fliken för anslutningsinställningar som visar hur pulsslagsfrekvensen konfigurerats](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. Välj **Registreringshantering**. För **Använd följande Azure AD-säkerhetsgrupper för att identifiera enheter som ska registreras i Lookout for Work**, anger du *gruppnamnet* för en Azure AD-grupp som ska användas med Lookout och väljer sedan **Spara ändringar**.

    ![skärmbild som visar sidan registrering av Intune-anslutning](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **Om grupperna som du använder**:
   - En bra praxis är att börja med en Azure AD-säkerhetsgrupp som innehåller ett litet antal användare för att testa Lookout-integreringen.
   - **Gruppnamnet** är skiftlägeskänsligt i säkerhetsgruppens **Egenskaper** i Azure-portalen.  
   - De grupper som du anger för **registreringshantering** definierar den uppsättning användare vars enheter kommer att registreras med Lookout. När en användare finns i en registreringsgrupp, registreras dennes enheter som finns i Azure AD och är tillgängliga för aktivering i Lookout MES. Första gången som en användare öppnar *Lookout for Work-appen* program på en stödd enhet, visas en uppmaning om att aktivera den.

4. Välj **Tillståndssynkronisering** och se till att både *enhetsstatus* och *hotstatus* är inställda på **På**.  Båda krävs för att integrationen mellan Lookout och Intune ska fungera korrekt.  

5. Välj **Felhantering**, ange den e-postadress som ska ta emot felrapporterna och välj sedan **Spara ändringar**.
 
   ![skärmbild som visar sidan för felhantering för Intune Connector](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. Välj **Skapa anslutning** för att slutföra konfigurationen av anslutningsprogrammet. När du sedan är nöjd med resultatet kan du utöka registreringen till ytterligare användargrupper.

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>Konfigurera Intune för att använda Lookout som Mobile Threat Defense-provider
När du har konfigurerat Lookout MES, måste du konfigurera en anslutning till Lookout i Intune.  

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Gå till **Enhetsefterlevnad** > **Mobile Threat Defense** och välj **Lägg till**.

3. I fönstret *Lägg till anslutningsprogram* använder du listrutan och väljer **Lookout for Work**.  

4. Välj **Skapa**. När anslutningsprogrammet har upprättat kontakt med Lookout MES blir alternativen för *anslutningsappinställningar* tillgängliga.

5. Ställ in **Aktivera appsynkronisering för iOS-enheter** till **På**. 

6. Välj **Spara** att slutföra konfigurationen.  Intune och Lookout MES är nu integrerade och redo att användas.


## <a name="additional-settings-in-the-lookout-mes-console"></a>Ytterligare inställningar i Lookout MES-konsolen
Nesan följer ytterligare inställningar som du kan konfigurera i Lookout MES-konsolen.  

### <a name="configure-enrollment-settings"></a>Konfigurera registreringsinställningar
I Lookout MES-konsolen väljer du **System** > **Hantera registrering** > **Registreringsinställningar**.  

- För **statusen Frånkopplad** anger du antalet dagar innan en enhet som är frånkopplad markeras som frånkopplad.  

  Frånkopplade enheter betraktas som icke-kompatibla och kommer att blockeras från att komma åt företagsprogrammen baserat på principer för villkorlig åtkomst i Intune. Du kan ange värden mellan 1 och 90 dagar.

  ![Lookout-registreringsinställningar i modulen System](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>Konfigurera e-postaviseringar
Om du vill ta emot e-postaviseringar om hot, loggar du in på [Lookout MES-konsolen](https://aad.lookout.com) med det användarkonto som ska ta emot aviseringarna.  

- Gå till **Inställningar** och ange sedan inställningen till **PÅ** för de aviseringar som du vill ta emot till och **spara** sedan ändringarna.  

- Om du inte längre vill ta emot e-postaviseringar väljer du alternativet **AV** för meddelanden och sparar ändringarna.

  ![skärmbild av sidan Inställningar där användarkontot visas](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)



## <a name="configure-threat-classifications"></a>Konfigurera hotklassificeringar  
Lookout Mobile Threat Endpoint Security klassificerar olika typer av mobila hot. Lookout-hotklassificeringarna är kopplade till standardrisknivåer. Risknivåerna kan ändras när som helst för att passa företagets krav.

Information om hotnivåklassificeringarna, och hur du hanterar risknivåerna associerade med dem, finns i [Lookout-hotklassificeringar](https://enterprise.support.lookout.com/hc/articles/360011812974).

>[!IMPORTANT]
> Risknivåerna är en viktig aspekt av Mobile Endpoint Security eftersom Intune-integreringen beräknar enhetens efterlevnad enligt dessa risknivåer vid körning.  
> 
> Intune-administratören anger en regel i principen för att identifiera att en enhet är icke-kompatibel om den har ett aktivt hot med miniminivån **Hög**, **Medel** eller **Låg**. Hotklassificeringsprincipen i Lookout Mobile Endpoint Security styr efterlevnadsberäkningen för enheten i Intune direkt.  

## <a name="monitor-enrollment"></a>Övervaka registrering
När konfigureringen är klar börjar Lookout Mobile Endpoint Security söka av Azure AD efter enheter som motsvarar de angivna registreringsgrupperna.  Du hittar information om registrerade enheter genom att gå till **Enheter** i Lookout MES-konsolen.  
- Den första statusen för enheterna är *väntar*.  
- Enhetens status uppdateras när *Lookout for Work-appen* har installerats, öppnats och aktiverats på enheten.

Mer information om hur du distribuerar *Lookout for Work-appen* till enheten finns i [Lägg till Lookout for work-appar med Intune](mtd-apps-ios-app-configuration-policy-add-assign.md).

## <a name="next-steps"></a>Nästa steg

[Konfigurera Lookout-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)
