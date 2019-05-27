---
title: Använd tredjeparts certifikatutfärdare (CA) med SCEP i Microsoft Intune – Azure | Microsoft Docs
description: I Microsoft Intune kan du lägga till en leverantör eller tredjeparts certifikatutfärdare (CA) för att utfärda certifikat till mobila enheter med hjälp av SCEP-protokollet. I den här översikten ger ett Azure Active Directory-program (Azure AD) Microsoft Intune behörigheter för att verifiera certifikat. Använd sedan program-ID:t, autentiseringsnyckeln och klientorganisations-ID för AAD-programmet i konfigurationen av din SCEP-server för att utfärda certifikat.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5e87b7397d994b089a30fedd9ccedc0107bf0cef
ms.sourcegitcommit: f8bbd9bac2016a77f36461bec260f716e2155b4a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65732497"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Lägg till certifikatutfärdarpartner i Intune med hjälp av SCEP

I Microsoft Intune går det att lägga till tredjeparts certifikatutfärdare (CA). Dessa certifikatutfärdare kan leverera certifikat till mobila enheter med hjälp av Simple Certificate Enrollment Protocol (SCEP). Den här funktionen kan utfärda nya certifikat och förnya certifikat på Windows-, iOS-, Android- och macOS-enheter.

Det finns två delar i att använda den här funktionen: API med öppen källkod och Intune-administratörsuppgifterna.

**Del 1 – Använda ett API med öppen källkod**  
Microsoft har skapat ett API som kan integreras med Intune för att verifiera certifikat, skicka meddelanden om lyckat eller misslyckat samt använda SSL, särskilt SSL socket factory, för att kommunicera med Intune.

API:et är tillgängligt på [den offentliga GitHub-lagringsplatsen för Intune SCEP API](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) så att du kan ladda ned och använda det i dina lösningar. Använd detta API med SCEP-servrar från tredje part för att köra anpassad utmaningsverifiering mot Intune innan du levererar ett certifikat till en enhet.

[Integrera med Intune SCEP-hanteringslösning](scep-libraries-apis.md) innehåller mer information om API:et, dess metoder och testning av den lösning som du skapar.

**Del 2 – Skapa programmet och profilen**  
Med hjälp av ett Azure Active Directory-program (Azure AD) kan du delegera behörigheter till Intune för att hantera SCEP-begäranden som kommer från enheter. Azure AD-programmet innehåller värden för program-ID och autentiseringsnyckel som används i den API-lösning som utvecklaren skapar. Administratörer kan sedan skapa och distribuera SCEP-certifikatprofiler med hjälp av Intune. Du kan även visa rapporter om distributionsstatus på enheterna.

Den här artikeln innehåller en översikt över den här funktionen från ett administratörsperspektiv, bland annat om att skapa Azure AD-programmet.

## <a name="overview"></a>Översikt

Följande steg ger en översikt över utfärdande av SCEP-certifikat i Intune:

1. I Intune skapar en administratör en SCEP-certifikatprofil och riktar sedan profilen till användare eller enheter.
2. Enheten checkar in till Intune.
3. Intune skapar en unik SCEP-utmaning. Det ger även ytterligare information om integritetskontroll, till exempel vad det förväntade ämnet och SAN bör vara.
4. Intune krypterar och signerar både utmaningen och informationen om integritetskontroll, och skickar den här informationen till enheten med SCEP-begäran.
5. Enheten genererar en certifikatsigneringsbegäran (CSR) och offentligt/privat nyckelpar på enheten baserat på den SCEP-certifikatprofil som skickas från Intune.
6. CSR och krypterad/signerad utmaning skickas till tredjeparts SCEP-serverns slutpunkt.
7. SCEP-servern skickar CSR och utmaningen till Intune. Intune verifierar sedan signaturen, dekrypterar nyttolasten och jämför CSR med integritetskontrollinformationen.
8. Intune skickar tillbaka ett svar till SCEP-servern och anger huruvida verifieringen av utmaningen lyckades eller inte.  
9. Om utmaningen lyckades utfärdar SCEP-servern certifikatet till enheten.

Följande diagram visar ett detaljerat flödet av tredjeparts SCEP-integrering med Intune:

![Så integrerar tredjeparts certifikatutfärdar-SCEP med Microsoft Intune](./media/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Konfigurera integrering av tredjeparts certifikatutfärdare

### <a name="validate-third-party-certification-authority"></a>Verifiera tredjeparts certifikatutfärdare

Innan du integrerar tredjeparts certifikatutfärdare med Intune bekräftar du att den certifikatutfärdare du använder har stöd för Intune. [Tredjeparts certifikatutfärdarpartner](#third-party-certification-authority-partners) (i den här artikeln) innehåller en lista. Du kan även läsa certifikatutfärdarens vägledning för mer information. Certifikatutfärdaren kan innefatta konfigurationsanvisningar som är specifika för dess implementering.

### <a name="authorize-communication-between-ca-and-intune"></a>Auktorisera kommunikation mellan ertifikatutfärdare och Intune

För att en tredjeparts SCEP-server ska kunna köra anpassad utmaningsverifiering med Intune måste du skapa en app i Azure AD. Den här appen ger delegerade behörigheter till Intune att verifiera SCEP-förfrågningar.

Se till att du har behörighet att registrera en Azure AD-app. Se [Nödvändiga behörigheter](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) i Azure AD-dokumentationen.

#### <a name="create-an-application-in-azure-active-directory"></a>Skapa ett program i Azure Active Directory  

1. På [Azure-portalen](https://portal.azure.com) går du till **Azure Active Directory** > **Appregistreringar** och väljer sedan **Ny registrering**.  

2. På sidan **Registrera ett program** anger du följande information:  
   - Ange ett beskrivande namn i avsnittet **Namn**.  
   - I avsnittet **Kontotyper som stöds** väljer du **Konton i valfri organisationskatalog**.  
   - Som **Omdirigerings-URI** lämnar du standardinställningen Web och anger sedan inloggnings-URL: en till SCEP-servern från tredje part.  

3. Välj **Registrera** för att skapa programmet och öppna sidan Översikt för den nya appen.  

4. På appsidan **Översikt** kopierar du värdet **Program-ID (klient)** och sparar det till senare. Du behöver det här värdet senare.  

5. I appens navigeringsfönster går du till **Certifikat och hemligheter** under **Hantera**. Klicka på knappen **Ny klienthemlighet**. Ange ett värde i beskrivningen, välj ett alternativ för **Förfaller** och välj sedan **Lägg till** för att generera ett *värde* för klienthemligheten. 
   > [!IMPORTANT]  
   > Innan du lämnar den här sidan ska du kopiera värdet för klienthemligheten och spara det för att användas senare tillsammans med en tredjeparts certifikatutfärdare. Det här värdet visas inte igen. Var noga med att läsa vägledningen från tredjeparts certifikatutfärdare om hur de vill att program-ID, autentiseringsnyckel och klientorganisations-ID ska konfigureras.  

6. Skriv upp ditt **Klientorganisations-ID**. Klientorganisations-ID är domäntexten efter @-tecknet i ditt konto. Om ditt konto till exempel är *admin@name.onmicrosoft.com*, är ditt klientorganisations-ID **namn.onmicrosoft.com**.  

7. I appens navigeringsfönster går du till **API-behörigheter** under **Hantera** och väljer sedan **Lägg till en behörighet**.  

8. På sidan **Begär API-behörigheter** väljer du **Intune** och väljer sedan **Programbehörigheter**. Markera kryssrutan för **scep_challenge_provider** (verifiering av certifikatskontroll SCEP).  

   Välj **Lägg till behörigheter** för att spara konfigurationen.  

9. Stanna kvar på sidan **API-behörigheter** och välj **Bevilja administratörens godkännande för Microsoft** och välj sedan **Ja**.  
   
   Registreringsprocessen i Azure AD har slutförts.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Konfigurera och distribuera en SCEP-certifikatprofil
Som administratör skapar du en SCEP-certifikatprofil att rikta mot användare eller enheter. Tilldela sedan profilen.

- [Skapa en SCEP-certifikatprofil](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [Tilldela certifikatprofilen](certificates-scep-configure.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Ta bort certifikat

När du avregistrerar eller rensar enheten tas certifikaten bort. Certifikaten återkallas inte.

## <a name="third-party-certification-authority-partners"></a>Tredjeparts certifikatutfärdarpartner
Följande tredjeparts certifikatutfärdare har stöd för Intune:

- [Entrust Datacard](http://www.entrustdatacard.com/resource-center/documents/documentation)
- [EJBCA GitHub version med öppen källkod](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)

Om du är tredjeparts certifikatutfärdare som är intresserad av att integrera din produkt med Intune kan du läsa API-vägledningen:

- [GitHub-lagringsplats för Intune SCEP API](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune SCEP API-vägledning för tredjeparts certifikatutfärdare](scep-libraries-apis.md)

## <a name="see-also"></a>Se även

- [Konfigurera certifikatprofiler](certificates-scep-configure.md)
- [GitHub-lagringsplats för Intune SCEP API](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune SCEP API-vägledning för tredjeparts certifikatutfärdare](scep-libraries-apis.md)
