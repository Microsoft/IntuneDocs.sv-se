---
title: "Krav för MAM-principer | Microsoft Docs"
description: "I det här avsnittet beskrivs förutsättningar för hur du konfigurerar användare innan du skapar hanteringsprinciper för mobilappar."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: a85b9f603e022b3296cb16754effd06087074a72
ms.openlocfilehash: 9759c1331a3fb5308e1dbc53564059618a8ef45c
ms.lasthandoff: 04/01/2017


---

# <a name="get-ready-to-configure-app-protection-policies-in-the-azure-portal"></a>Förbereda konfigurationen av appskyddsprinciper på Azure-portalen

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet beskriver kraven och de steg du måste utföra **innan** du kan skapa appskyddsprinciper på Azure-portalen.

Information om hur du kan skydda företagsdata med Intune-appskyddsprinciper finns i [Skydda appar och data med hjälp av appskyddsprinciper](protect-apps-and-data-with-microsoft-intune.md).

## <a name="what-is-the-azure-portal"></a>Vad är Azure-portalen?

Azure-portalen är den nya administratörskonsolen för att skapa appskyddsprinciper. Den har stöd för följande MAM-scenarier:
- Enheter som har registrerats i Intune
- Enheter som hanteras av en annan lösning för Mobile Device Management (MDM)
- Enheter som inte hanteras av någon MDM-lösning (BYOD)

Du kan konfigurera appskyddsprinciper både i **Intune-administratörskonsolen** och på **Azure-portalen**.  Tänk på följande:

* Principerna som du skapar på **Azure Portal** har stöd för **alla MAM-scenarier** som angivits innan. I **Intune-administratörskonsolen** kan du bara skapa principer för **enheter som har registrerats i och som hanteras av Intune**.

* Du kanske inte ser alla apprincipinställningar i Intune-administratörskonsolen eftersom **nya inställningar** endast kan läggas till på **Azure-portalen**.

* Om du skapar appskyddsprinciper i **både** Intune-administratörskonsolen och på Azure-portalen är det principen på **Azure-portalen som tillämpas på apparna och som distribueras till användarna**.
    * Appskyddsprinciper som skapas i Intune-administratörskonsolen kan inte importeras till Azure-portalen.  Appskyddsprinciperna måste återskapas på Azure-portalen.


* Andra **apphanteringsfunktioner**, t.ex. distribution av appar och appkonfigurationsprinciper, är för närvarande endast tillgängliga i **Intune-administratörskonsolen**.


Om du inte är van vid att använda Azure-portalen kan du läsa avsnittet om [Azure-portalen för appskyddsprinciper i Microsoft Intune](azure-portal-for-microsoft-intune-mam-policies.md), där du lär dig grunderna om Azure-portalen.

Anvisningar för hur du skapar en apprincip i Intune-administratörskonsolen finns i [Configure and deploy app protection policies in the Microsoft Intune console](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) (Konfigurera och distribuera appskyddsprinciper i Microsoft Intune-konsolen).


##  <a name="supported-platforms"></a>Plattformar som stöds
- iOS 8.1 eller senare
- Android 4 eller senare
- Windows 10

>[!NOTE]
>Från och med version 1703 kan appskyddsprinciper definieras för Windows 10-enheter i MAM utan registreringsscenario. Mer information finns i avsnittet om hur du [skyddar dina företagsdata med hjälp av Windows Information Protection (WIP)](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/protect-enterprise-data-using-wip).

##  <a name="supported-apps"></a>Appar som stöds
* **Microsoft-appar:** Dessa appar har en inbyggd app-SDK för Intune och kräver ingen ytterligare bearbetning innan du tillämpar appskyddsprinciper.
Om du vill se en fullständig lista över Microsoft-appar som stöds går du till [galleriet för Microsoft Intune-mobilprogram](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps) på sidan för Microsoft Intune-programpartner. Klicka på appen om du vill se vilka scenarier och plattformar som stöds och huruvida appen har stöd för flera identiteter.

* **Verksamhetsspecifika appar:** Du måste förbereda dessa appar så att de integrerar Intune App SDK innan du kan tillämpa appskyddsprinciper.

  * För enheter som hanteras av Intune, se [Besluta hur du ska förbereda appar för MAM](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).

  * Mer information om enheter som inte hanteras (t.ex. personalägda enheter) eller om enheter som hanteras av en annan lösning för hantering av mobila enheter finns i [Skydda branschspecifika appar och data på enheter som inte har registrerats i Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

## <a name="prerequisites"></a>Förutsättningar

-   **En Microsoft Intune-prenumeration**. Användarna behöver [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licenser för att kunna hämta appar med appskyddsprinciper.
Du har redan en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-prenumeration om du för närvarande använder [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] för att hantera enheter. Du har också en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-prenumeration om du har köpt en EMS-licens (Enterprise Mobility Suite). Om du provar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] för att få en överblick över MAM-funktionerna kan du skapa ett utvärderingskonto på [Sidan för Microsoft Intune](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/).

    Du kan kontrollera om du har en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-prenumeration på sidan **Fakturering** på Office-portalen.  Om du har en prenumeration bör du se [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] som **Aktiv** i prenumerationerna.

-   **En prenumeration på Office 365**, vilket krävs för följande:

  - Använda appskyddsprinciper för appar med stöd för flera identiteter.

  - Skapa konton för SharePoint Online och Exchange Online-arbete. Lokalt Exchange och lokalt SharePoint stöds inte.

-   **Installation av Skype för företag – Online för modern autentisering**. Mer information finns i [Aktivera modern autentisering](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).


- Azure Active Directory (Azure AD) för att skapa användare. Azure AD autentiserar användare när de öppnar appen och anger sina autentiseringsuppgifter för arbetet.

    > [!NOTE]
    > Användargrupper måste konfigureras i Azure AD. Intune-användargrupper kan inte användas för att distribuera appskyddsprinciper på Azure-portalen.

### <a name="create-users-and-assign-microsoft-intune-licenses"></a>Skapa användare och tilldela Microsoft Intune-licenser

1.  Logga in som administratör på [Office-portalen](http://portal.office.com).

2.  Lägg till användare såsom beskrivs i avsnittet **Steg för att slutföra en 30-dagars utvärderingsversion av Intune** i [utvärderingsguiden för Intune](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) och tilldela sedan Intune-licenser. Om du vill ge en användare möjlighet att komma åt Office-portalen, Azure AD-portalen och Azure Portal tilldelar du användaren rollen **Global administratör**.

5.  Appskyddsprinciper distribueras till användargrupper i Azure Active Directory. Du skapar användargrupper för appskyddsprinciper genom att först skapa en användargrupp. Följ anvisningarna i avsnittet **Skapa en användargrupp** i [Skapa grupper för att organisera användare och enheter som prenumererar på utvärderingen](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3).

### <a name="assign-roles-to-non-global-admin-users"></a>Tilldela roller till icke-globala administratörer

Globala administratörer har åtkomst till [Azure Portal](https://portal.azure.com).  Om du vill att användare som inte är globala administratörer ska kunna konfigurera principer och utföra andra hanteringsuppgifter för mobila appar läser du artikeln [Use role assignments to manage access to your Azure subscription resources](https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-configure/) (Använda rolltilldelningar för att hantera åtkomsten till Azure-prenumerationsresurser).

## <a name="next-steps"></a>Nästa steg
[Skapa och distribuera appskyddsprinciper med Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

