---
# required metadata

title: Förbered dig för att konfigurera hanteringsprinciper för mobila appar | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Förbered dig för att konfigurera hanteringsprinciper för mobila appar med Microsoft Intune
Den här artikeln beskriver vad du behöver göra innan du kan skapa principer för hantering av mobilappar (MAM) i Azure Portal.
Om du för närvarande använder **Intune-administratörskonsolen** för att hantera enheter kan du skapa en MAM-princip som har stöd för enheter som har registrerats i Intune med [Intune-administratörskonsolen](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)
>[!IMPORTANT]
> Du kanske inte kan se alla MAM-principinställningar i Intune-administratörskonsolen. Azure Portal är den nya administratörskonsolen för att skapa MAM-principer.

##  Plattformar som stöds
- iOS 8.1 eller senare

- Android 4 eller senare

##  Appar som stöds
Om du vill se en fullständig lista över appar som stöds kan du gå till [Microsoft Intune-galleriet för mobilprogram](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) på sidan för Microsoft Intune-programpartner.
Klicka på appen för att se vilka scenarier och plattformar som stöds och huruvida appen stöder flera identiteter.

**Innan** du kan konfigurera MAM-principer behöver du följande:

-   **En prenumeration på Microsoft Intune**.    Slutanvändare behöver [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licenser för att hämta appar med MAM-principen.

-   **Auktoriteten för hanteringen av mobila enheter** måste vara inställd på antingen **Intune** eller **Configuration Manager**, beroende på om du använder bara Intune eller Configuration Manager integrerat med Intune för att hantera dina enheter. Om du använder inbyggd hantering av mobila enheter i O365 måste du köpa en Intune-prenumeration och [ange Intune som auktoritet för hanteringen av mobila enheter](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)
-   En prenumeration på **Office 365 (O365)** som krävs för följande:
  - Tillämpa MAM-principer för appar med stöd för flera identiteter.
  - Skapa konton för SharePoint Online och Exchange Online-arbete. Lokalt Exchange och lokalt SharePoint stöds inte.


- **Azure Active Directory (Azure AD)** för att skapa användare. Azure AD autentiserar användaren när slutanvändaren startar appen och anger sina autentiseringsuppgifter.

    > Om du konfigurerar användare via [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-konsolen bör du tänka på att konfigurationen av MAM-principen flyttar till Azure Portal framöver och för att använda den här portalen måste du skapa användargrupper i Azure AD med Office 365-portalen.


## Skapa användare och tilldela Microsoft Intune-licenser

1. Du behöver en Intune-prenumeration: Du har redan en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-prenumeration om du för närvarande använder [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] för att hantera enheter.  Du har också en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-prenumeration om du har köpt en EMS-licens. Om du provar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] för att kolla in MAM-funktionerna kan du skapa ett provkonto [här](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/)

    Kontrollera om du har en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-prenumeration genom att besöka sidan Fakturering på Office-portalen.  Du bör se [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] som **aktivt** under prenumerationerna.

2.  Logga in på   [Office-portalen](http://portal.office.com) med dina autentiseringsuppgifter som administratör.

3.  Navigera till sidan **Aktiva användare** för att lägga till användare och tilldela [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licenser.

    ![Sidan för att lägga till användare i Office-portalen](../media/AppManagement/OfficePortal_AddUsers.png)

4.  Om du vill ge en användare möjlighet att komma åt Office-portalen, Azure AD-portalen och Azure Portal tilldelar du användaren rollen **Global administratör**.

    ![Skärmbild av office-portalen som visar sidan Aktiva användare ](../media/AppManagement/OfficePortal_AddRoletoUser.png)

5.  MAM-principer har distribuerats till användargrupper i Azure Active Directory. Om du vill skapa användargrupper som ska användas i MAM-principerna navigerar du till sidan **Grupper** på **Office-portalen** och klickar på ikonen **+** för att skapa en ny säkerhetsgrupp.  Skriv ett namn och en beskrivning och klicka på **Skapa**. När gruppen skapas kan du lägga till användaren i gruppen genom att klicka på **Redigera medlemmar** i den nya säkerhetsgruppen. Säkerhetsgruppen har skapats i Azure Active Directory.

    ![Skärmbild av sidan som visar urval för den globala administratörsrollen på sidan Redigera användarroller](../media/AppManagement/OfficePortal_CreateGroups.png)

I följande tabell visas rollen och behörigheterna som du kan tilldela administrativa användare.

|||
|--|----|
|**Roll**|**Behörigheter**|
|Global administratör (O365-portalen)|Åtkomst till O365-portalen och Azure AD-portalen<br /><br />Åtkomst till Azure Portal (kan utföra uppgifter för både roll- och mobilappshantering).|
|Ägarrollen (Azure Portal)|Åtkomst till Azure Portal (kan utföra uppgifter för både roll- och mobilappshantering).|
|Deltagarrollen (Azure Portal)|Åtkomst till Azure Portal (kan bara utföra uppgifter för mobilappshantering).|

## Tilldela en användare deltagarrollen

**Globala administratörer** har åtkomst till Azure Portal.  Om du vill att andra administrativa användare ska kunna konfigurera principer och utföra andra uppgifter för hantering av mobilappar kan du tilldela användaren **deltagarrollen** enligt beskrivningen nedan:


1.  På bladet **Inställningar** i avsnittet **Resurshantering** klickar du på **Användare**

    ![Skärmbild av bladet Användare på Azure Portal](../media/AppManagement/AzurePortal_MAM_AddUsers.png)

2.  Klicka på **Lägg till** för att öppna bladet **Lägg till åtkomst** .

3.  Klicka på **Välj en roll** och sedan på **Deltagarroll**

    ![Skärmbild av bladet Välj en roll på Azure Portal](../media/AppManagement/AzurePortal_MAM_AddRole.png)

4.  När du har valt rollen klickar du på **Lägg till användare**och söker efter användaren med användarnamn eller e-postadress. Användarna som visas i listan är de 1 000 första användarna som du tidigare skapade i Azure AD med hjälp av Office-portalen. Klicka på **Ok** på bladet **Lägg till åtkomst** för att spara och tilldela användaren rollen.

    ![Skärmbild av bladet Lägg till användargrupp på Azure Portal](../media/AppManagement/AzurePortal_MAM_AddusertoRole.png)

    > Om du väljer en användare som inte har tilldelats någon [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licens kommer den användaren inte att komma åt portalen.

## Nästa steg
[Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


