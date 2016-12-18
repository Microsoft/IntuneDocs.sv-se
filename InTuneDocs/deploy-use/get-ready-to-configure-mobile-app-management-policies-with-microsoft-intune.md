---
title: "Krav för MAM-principer | Microsoft Intune"
description: "I det här avsnittet beskrivs förutsättningar för hur du konfigurerar användare innan du skapar hanteringsprinciper för mobilappar."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: ac820146d81fb121a60f7029f6a52a0056d6ab0a


---

# <a name="get-ready-to-configure-mobile-app-management-policies-on-the-azure-portal"></a>Gör dig redo att konfigurera hanteringsprinciper för mobila appar på Azure-portalen
Det här avsnittet beskriver kraven och de steg du måste utföra **innan** du kan skapa MAM-principer för hantering av mobilappar på Azure-portalen.

Information om hur Intunes MAM-principer kan skydda företagets data finns i [Skydda appar och data med principer för hantering av mobila appar](protect-apps-and-data-with-microsoft-intune.md).

## <a name="what-is-the-azure-portal"></a>Vad är Azure-portalen?

Azure Portal är den nya administratörskonsolen för att skapa MAM-principer. Den har stöd för följande MAM-scenarier:
- Enheter som har registrerats i Intune
- Enheter som hanteras av en annan lösning för Mobile Device Management (MDM)
- Enheter som inte hanteras av någon MDM-lösning (BYOD)

Du kan konfigurera MAM-principer både i **Intune-administratörskonsolen** och på **Azure-portalen**.  Tänk på följande:

* Principerna som du skapar på **Azure Portal** har stöd för **alla MAM-scenarier** som angivits innan. I **Intune-administratörskonsolen** kan du bara skapa principer för **enheter som har registrerats i och som hanteras av Intune**.

* Du kanske inte ser alla MAM-principinställningar i Intune-administratörskonsolen eftersom **nya inställningar** endast kan läggas till på **Azure-portalen**.

* Om du skapar MAM-principer i **både** Intune-administratörskonsolen och Azure Portal är det principen på **Azure-portalen som tillämpas på apparna och som distribueras till användarna**.
    * MAM-principer som skapas i Intune-administratörskonsolen kan inte importeras till Azure Portal.  MAM-principer måste återskapas i Azure Portal.


* Andra **apphanteringsfunktioner**, t.ex. distribution av appar och appkonfigurationsprinciper, är för närvarande endast tillgängliga i **Intune-administratörskonsolen**.


Om du inte är van vid att använda Azure-portalen kan du läsa [Azure-portalen för Microsoft Intune MAM-principer](azure-portal-for-microsoft-intune-mam-policies.md), där du lär dig grunderna om Azure-portalen.

Anvisningar om hur du skapar en MAM-princip i Intune-administratörskonsolen finns i [Konfigurera och distribuera hanteringsprinciper för mobilprogram i Microsoft Intune-konsolen](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).


##  <a name="supported-platforms"></a>Plattformar som stöds
- iOS 8.1 eller senare
- Android 4 eller senare

>[!NOTE]
>Windows-enheter stöder inte dessa principer för hantering av mobila program. När du registrerar Windows 10-enheter med Intune kan du använda Windows Information Protection, som innehåller liknande funktioner. Mer information finns i avsnittet om hur du [skyddar dina företagsdata med hjälp av Windows Information Protection (WIP)](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/protect-enterprise-data-using-wip).

##  <a name="supported-apps"></a>Appar som stöds
* **Microsoft-appar:** Dessa appar har en inbyggd app-SDK för Intune och kräver ingen ytterligare bearbetning innan du tillämpar MAM-principer.
Om du vill se en fullständig lista över Microsoft-appar som stöds går du till [galleriet för Microsoft Intune-mobilprogram](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps) på sidan för Microsoft Intune-programpartner. Klicka på appen om du vill se vilka scenarier och plattformar som stöds och huruvida appen har stöd för flera identiteter.

* **Verksamhetsspecifika appar:** Appen måste förberedas för att innefatta Intune App SDK innan du kan tillämpa MAM-principer.

  * För enheter som hanteras av Intune, se [Besluta hur du ska förbereda appar för MAM](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).

  * Mer information om enheter som inte hanteras (t.ex. personalägda enheter) eller om enheter som hanteras av en annan lösning för hantering av mobila enheter finns i [Skydda branschspecifika appar och data på enheter som inte har registrerats i Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

## <a name="prerequisites"></a>Förutsättningar

-   **En Microsoft Intune-prenumeration**. Användare behöver [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licenser för att hämta appar som har MAM-principer.
Du har redan en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-prenumeration om du för närvarande använder [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] för att hantera enheter. Du har också en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-prenumeration om du har köpt en EMS-licens (Enterprise Mobility Suite). Om du provar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] för att få en överblick över MAM-funktionerna kan du skapa ett utvärderingskonto på [Sidan för Microsoft Intune](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/).

    Du kan kontrollera om du har en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-prenumeration på sidan **Fakturering** på Office-portalen.  Om du har en prenumeration bör du se [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] som **Aktiv** i prenumerationerna.

-   **En prenumeration på Office 365**, vilket krävs för följande:

  - Tillämpa MAM-principer för appar med stöd för flera identiteter.

  - Skapa konton för SharePoint Online och Exchange Online-arbete. Lokalt Exchange och lokalt SharePoint stöds inte.

-   **Installation av Skype för företag – Online för modern autentisering**. Mer information finns i [Aktivera modern autentisering](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).


- Azure Active Directory (Azure AD) för att skapa användare. Azure AD autentiserar användare när de öppnar appen och anger sina autentiseringsuppgifter för arbetet.

    > [!NOTE]
    > Användargrupper måste konfigureras i Azure AD. Intune-användargrupper kan inte användas för att distribuera MAM-principer på Azure-portalen.

### <a name="create-users-and-assign-microsoft-intune-licenses"></a>Skapa användare och tilldela Microsoft Intune-licenser

1.  Logga in som administratör på [Office-portalen](http://portal.office.com).

2.  Lägg till användare såsom beskrivs i avsnittet **Steg för att slutföra en 30-dagars utvärderingsversion av Intune** i [utvärderingsguiden för Intune](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) och tilldela sedan Intune-licenser. Om du vill ge en användare möjlighet att komma åt Office-portalen, Azure AD-portalen och Azure Portal tilldelar du användaren rollen **Global administratör**.

5.  MAM-principer har distribuerats till användargrupper i Azure Active Directory. För att skapa användargrupper för MAM-principer, skapar du en användargrupp enligt beskrivningen i avsnittet **Skapa en användargrupp** av [Skapa grupper för att organisera användare och enheter för utvärderingsprenumeration](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3).

### <a name="assign-roles-to-non-global-admin-users"></a>Tilldela roller till icke-globala administratörer

Globala administratörer har åtkomst till [Azure Portal](https://portal.azure.com).  Om du vill att användare som inte är globala administratörer ska kunna konfigurera principer och utföra andra uppgifter relaterade till hanteringen av mobila appar kan du tilldela rollen som deltagare till användarna. Detaljerade anvisningar finns i [Använda rolltilldelningar för att hantera åtkomsten till dina Azure-prenumerationsresurser](https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-configure/).



I följande tabell visas de roller och behörigheter som du kan tilldela administrativa användare.



|||
|--|----|
|**Roll**|**Behörigheter**|
|Global administratör (Office 365-portalen)|Åtkomst till Office 365-portalen och Azure AD-portalen.<br /><br />Åtkomst till Azure Portal (kan utföra uppgifter för både roll- och mobilappshantering).|
|Ägare (Azure Portal)|Åtkomst till Azure Portal (kan utföra uppgifter för både roll- och mobilappshantering).|
|Deltagare (Azure Portal)|Åtkomst till Azure Portal (kan bara utföra uppgifter för mobilappshantering).|




## <a name="next-steps"></a>Nästa steg
[Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


