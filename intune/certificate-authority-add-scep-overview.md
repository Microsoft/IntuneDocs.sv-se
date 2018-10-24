---
title: Använd tredjeparts certifikatutfärdare med SCEP i Microsoft Intune – Azure | Microsoft Docs
description: I Microsoft Intune kan du lägga till en leverantör eller tredjeparts certifikatutfärdare (CA) för att utfärda certifikat till mobila enheter med hjälp av SCEP-protokollet. I den här översikten ger ett Azure Active Directory-program (Azure AD) Microsoft Intune behörigheter för att verifiera certifikat. Använd sedan program-ID:t, autentiseringsnyckeln och klientorganisations-ID för AAD-programmet i konfigurationen av din SCEP-server för att utfärda certifikat.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e088dbf4080cb6092ff506519b81438a0d5ce64c
ms.sourcegitcommit: ab08dd841f16ae11f958c43b6262a9f6a0cabdd4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49102114"
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

Se till att du har behörighet att registrera en Azure AD-app. [Nödvändiga behörigheter](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) innehåller stegen.

**Steg 1: Skapa ett Azure AD-program**

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Azure Active Directory** > **Appregistreringar** > **Ny programregistrering**.
3. Ange ett namn och inloggnings-URL. Välj **Webbapp/API** för programtypen.
4. Välj **Skapa**.

[Integrera program med Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) innehåller viss vägledning om hur du skapar en app, inklusive tips om URL och namn.

**Steg 2: Ge behörigheter**

När du har skapat ditt program ger du Microsoft Intune-API de behörigheter som krävs:

1. I din Azure AD-app öppnar du **Inställningar** > **Nödvändiga behörigheter**.  
2. Välj **Lägg till** > **Välj ett API** > välj **Microsoft Intune API** > **Välj**.
3. I **Välj behörigheter** väljer du **SCEP-utmaningsverifiering** > **Välj**.
4. Klicka på **Klar** för att spara ändringarna.

**Steg 3: Hämta program-ID och autentiseringsnyckel**

Hämta ID- och nyckelvärden för ditt Azure AD-program. Följande värden behövs:

- Program-ID
- Autentiseringsnyckel
- Klientorganisations-ID

**Så här hämtar du program-ID och autentiseringsnyckel**:

1. I Azure AD väljer du ditt nya program (**Appregistreringar**).
2. Kopiera **program-ID** och lagra det i din programkod.
3. Generera sedan en autentiseringsnyckel. I din Azure AD-app öppnar du **Inställningar** > **Nycklar**.
4. I **Lösenord** anger du en beskrivning och väljer varaktighet för nyckeln. **Spara** ändringarna. Kopiera och spara det värde som visas.

    > [!IMPORTANT]
    > Kopiera och spara den här nyckeln omedelbart eftersom den inte visas igen. Det här nyckelvärdet behövs med implementeringen av din tredjeparts certifikatutfärdare. Var noga med att läsa deras vägledning om hur de vill att program-ID, autentiseringsnyckeln och klientorganisations-ID konfigureras.

**Klientorganisations-ID** är domäntexten efter @-tecknet i ditt konto. Om ditt konto till exempel är `admin@name.onmicrosoft.com` är ditt klientorganisations-ID **namn.onmicrosoft.com**.

[Hämta program-ID och autentiseringsnyckel](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key) visar stegen för att hämta dessa värden och innehåller mer information om Azure AD-appar.

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

Om du är tredjeparts certifikatutfärdare som är intresserad av att integrera din produkt med Intune kan du läsa API-vägledningen:

- [GitHub-lagringsplats för Intune SCEP API](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune SCEP API-vägledning för tredjeparts certifikatutfärdare](scep-libraries-apis.md)

## <a name="see-also"></a>Se även

- [Konfigurera certifikatprofiler](certificates-scep-configure.md)
- [GitHub-lagringsplats för Intune SCEP API](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune SCEP API-vägledning för tredjeparts certifikatutfärdare](scep-libraries-apis.md)
