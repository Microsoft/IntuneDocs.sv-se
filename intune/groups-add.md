---
title: "Ange registreringsbegränsningar i Intune"
titlesuffix: Azure portal
description: "Begränsa registrering per plattform och ange en gräns för enhetsregistrering i Intune. \""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e55a96ee1bee5b1f25a4ddf3366f3e7dc94122a
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="add-groups-in-intune"></a>Lägg till grupper i Intune
Intune använder Azure Active Directory-grupper (AD) för att hantera enheter och användare. I egenskap av Intune-administratör kan du skapa grupper som passar organisationens behov. Skapa grupper för att ordna användare eller enheter efter geografisk plats, avdelning eller maskinvaruegenskaper. Använd grupper för att hantera skalanpassade aktiviteter. Du kan t.ex. ange principer för många användare eller distribuera appar till en uppsättning enheter.

Det här avsnittet beskriver hur du lägger till grupper för användning i Intune.

Du kan lägga till följande typer av grupper:
- **Tilldelade grupper** – Lägg manuellt till användare eller enheter i en statisk grupp
- **Dynamiska grupper** – (med Azure Active Directory Premium) Möjliggör dynamiskt skapande av antingen användar- eller enhetsgrupper som definierats med enkla eller avancerade regler

## <a name="add-a-new-group"></a>Lägg till en ny grupp

Använd följande anvisningar för att skapa en ny grupp.
1. Gå till **Grupper** i Azure-portalen och välj sedan **Ny grupp** på bladet **Alla grupper**.
  ![Skärmbild av Azure-portalen med Ny grupp vald](./media/groups-add-new.png)
2. Redigera den nya gruppens **namn** och **beskrivning**. Egenskaperna visas endast i hanteringsportalen och inte för användarna.

3. Välj **Medlemskapstyp**:
  - **Tilldelad** för att skapa gruppen med manuellt tilldelade medlemmar. Läs mer om [grupper som tilldelats i Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
  - **Dynamisk användare** för att skapa en användargrupp som definierats med en **dynamisk fråga**.
  - **Dynamisk enhet** för att skapa en enhetsgrupp som definierats med en **dynamisk fråga**.

  ![Skärmbild av Intune-gruppegenskaper med namn, beskrivning, medlemskapstyp, aktivering av Office-funktioner och medlemmar](./media/groups-add-properties.png)

  Med Azure AD kan du skapa dynamiska grupper baserat på regler som definierar medlemskap. Läs mer om hur du [skapar attributbaserade dynamiska grupper](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

4. Du kan välja **Aktivera Office-funktioner** och ge medlemmarna i användargruppen tillgång till delade Office 365-appar. Läs mer om [Office 365-grupper](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).
5. Välj **Skapa** om du vill lägga till en ny grupp.

## <a name="see-also"></a>Se även
- [Hantera åtkomst till resurser med Azure Active Directory-grupper](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Klassiska Intune-grupper i Azure-portalen](groups-get-started.md)
