---
title: Lägga till grupper för att organisera användare och enheter
titleSuffix: Microsoft Intune
description: Lägg till grupper för att organisera användare och enheter efter geografi, avdelning eller maskinvaruegenskaper.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 183e8cc5924f6ce1f002225150d808841924e20c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514650"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Lägga till grupper för att organisera användare och enheter

Intune använder Azure Active Directory-grupper (Azure AD) till att hantera enheter och användare. I egenskap av Intune-administratör kan du skapa grupper som passar organisationens behov. Skapa grupper för att ordna användare eller enheter efter geografisk plats, avdelning eller maskinvaruegenskaper. Använd grupper för att hantera skalanpassade aktiviteter. Du kan t.ex. ange principer för många användare eller distribuera appar till en uppsättning enheter.

Du kan lägga till följande typer av grupper:

- **Tilldelade grupper** – Lägg manuellt till användare eller enheter i en statisk grupp. 
- **Dynamiska grupper** (kräver Azure AD Premium) – Lägg automatiskt till användare eller enheter i användargrupper eller enhetsgrupper baserat på ett uttryck som du skapar.

  Till exempel när en användare läggs till med en chefstitel, läggs användaren automatiskt till i användargruppen **Alla chefer**. Eller när en enhet har operativsystemet iOS/iPadOS, läggs enheten automatiskt till i enhetsgruppen **Alla iOS/iPadOS-enheter**.

## <a name="add-a-new-group"></a>Lägg till en ny grupp

Använd följande anvisningar för att skapa en ny grupp.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Grupper** > **Ny grupp**:

   ![Skärmbild av Azure-portalen med Ny grupp vald](./media/groups-add/groups-add-new.png)

3. Välj något av följande alternativ i **Grupptyp**:

    - **Säkerhet**: Säkerhetsgrupper definierar vem som har åtkomst till resurser. Vi rekommenderar att du använder detta för dina grupper i Intune. Du kan till exempel skapa grupper för användare, t.ex. **Alla anställda i Charlotte** eller **Distansarbetare**. Du kan också skapa grupper för enheter, till exempel **Alla iOS/iPadOS-enheter** eller **Alla Windows 10 Student-enheter**.

        > [!TIP]
        > De användare och grupper som skapas visas också i [Administrationscenter för Microsoft 365](https://admin.microsoft.com), Administrationscenter för Azure Active Directory och [Microsoft Intune i Azure-portalen](https://go.microsoft.com/fwlink/?linkid=2090973). I din organisationsklient kan du skapa och hantera grupper inom alla dessa områden.
        >
        > Om din primära roll är enhetshantering, rekommenderar vi att du använder [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

    - **Office 365**: Tillhandahåller samarbetsmöjligheter genom att ge medlemmar åtkomst till en delad postlåda, kalender, filer, SharePoint-webbplats med mera. Med det här alternativet kan du också ge personer utanför organisationen åtkomst till gruppen. Mer information finns i [Mer information om Office 365-grupper](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).

4. Ange ett **gruppnamn** och en **gruppbeskrivning** för den nya gruppen. Var specifik och inkludera information som beskriver gruppen för andra personer.

    Ange till exempel **Alla Windows 10 Student-enheter** som gruppnamn och **Alla Windows 10-enheter som används av elever i Contoso High School 9–12** som gruppbeskrivning.

5. Ange **Medlemskapstyp**. Alternativen är:

    - **Tilldelade**: Administratörer tilldelar manuellt användare eller enheter till den här gruppen och tar bort användare eller enheter manuellt.
    - **Dynamisk användare**: Administratörer skapar medlemskapsregler för att automatiskt kunna lägga till och ta bort medlemmar.
    - **Dynamisk enhet**: Administratörer skapar dynamiska gruppregler för att automatiskt kunna lägga till och ta bort enheter.

        ![Skärmbild av Intune-gruppegenskaper](./media/groups-add/groups-add-properties.png)

    Mer information om dessa medlemskapstyper och hur du skapar dynamiska uttryck finns i:

    - [Skapa en basgrupp och lägg till medlemmar med hjälp av Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Regler för dynamiskt medlemskap i grupper i Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)

    > [!NOTE]
    > När du skapar användare eller grupper i det här administrationscentret kanske du inte ser **Azure Active Directory**-anpassningen. Men det är det som du använder.

6. Välj **Skapa** om du vill lägga till en ny grupp. Gruppen visas i listan.

> [!TIP]
> Du kan även skapa andra dynamiska användar- och enhetsgrupper, till exempel:
>
> - Alla elever i Contoso High School
> - Alla Android Enterprise-enheter
> - Alla iOS 11-enheter och äldre enheter
> - Marknadsföring
> - Personalfrågor
> - Alla anställda i Charlotte
> - Alla anställda i WA

## <a name="groups-and-policies"></a>Grupper och principer

Åtkomsten till organisationens resurser styrs av vilka användare och grupper som du skapar.

När du skapar grupper bör du fundera på hur du ska tillämpa [efterlevnadsprinciper](../protect/device-compliance-get-started.md) och [konfigurationsprofiler](../configuration/device-profiles.md). Du kan till exempel ha:

- Principer som är specifika för en enhets operativsystem.
- Principer som är specifika för olika roller i din organisation.
- Principer som är specifika för organisationsenheter som du har definierat i Active Directory Domain Services.

När du skapar de grundläggande kompatibilitetskraven för din organisation, kan du skapa en standardprincip som gäller alla grupper och enheter. Sedan kan du skapa mer specifika principer för de bredaste användar- och enhetskategorierna. Du kan till exempel skapa e-postprinciper för vart och ett av enhetsoperativsystemen.

Rekommendationer och vägledning för konfigurationsprofiler finns i [Tilldela principer till användargrupper eller enhetsgrupper](../configuration/device-profile-assign.md#user-groups-vs-device-groups) och [profilrekommendationer](../configuration/device-profile-create.md#recommendations).

## <a name="see-also"></a>Se även

- [Rollbaserad åtkomstkontroll (RBAC) med Microsoft Intune](role-based-access-control.md)
- [Hantera åtkomst till resurser med Azure AD-grupper](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
