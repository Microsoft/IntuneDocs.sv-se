---
title: Lägga till grupper för att organisera användare och enheter
titleSuffix: Microsoft Intune
description: Lägg till grupper för att organisera användare och enheter efter geografi, avdelning eller maskinvaruegenskaper.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b11829bad3091b24bead99afc08dc5cdc01f0a0c
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047649"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Lägga till grupper för att organisera användare och enheter
Intune använder Azure Active Directory-grupper (AD) för att hantera enheter och användare. I egenskap av Intune-administratör kan du skapa grupper som passar organisationens behov. Skapa grupper för att ordna användare eller enheter efter geografisk plats, avdelning eller maskinvaruegenskaper. Använd grupper för att hantera skalanpassade aktiviteter. Du kan t.ex. ange principer för många användare eller distribuera appar till en uppsättning enheter.

Du kan lägga till följande typer av grupper:
- **Tilldelade grupper** – Lägg manuellt till användare eller enheter i en statisk grupp
- **Dynamiska grupper** – (med Azure Active Directory Premium) Möjliggör dynamiskt skapande av antingen användar- eller enhetsgrupper som definierats med enkla eller avancerade regler

## <a name="add-a-new-group"></a>Lägg till en ny grupp

Använd följande anvisningar för att skapa en ny grupp.
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Gå till **Intune**-fönstret, välj **Grupper** och sedan **Ny grupp** i fönstret **Alla grupper**.
   ![Skärmbild av Azure-portalen med Ny grupp vald](./media/groups-add-new.png)
4. Välj något av följande alternativ för **Grupptyp**:
    - **Säkerhet**: Säkerhetsgrupper är en bra resurs att använda när du ska fylla användargrupper. Eftersom säkerhetsgrupper definierar vem som har åtkomst till vilka resurser så kan de lätt överföras till Intune-användargrupper. Säkerhetsgrupper som synkroniseras från Active Directory till Azure Active Directory, eller som skapats direkt i Azure Active Directory via Microsoft 365-administrationscentret eller Azure-portalen, kan användas för att skapa användargrupper i Intune.
    - **Office 365**

5. Skriv ett **Namn** och en **Beskrivning** för den nya gruppen. Egenskaperna visas endast i hanteringsportalen och inte för användarna.

6. Välj **Medlemskapstyp**:
   - **Tilldelad** för att skapa gruppen med manuellt tilldelade medlemmar. Läs mer om [grupper som tilldelats i Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
   - **Dynamisk användare** för att skapa en användargrupp som definierats med en **dynamisk fråga**.
   - **Dynamisk enhet** för att skapa en enhetsgrupp som definierats med en **dynamisk fråga**.

   ![Skärmbild av Intune-gruppegenskaper](./media/groups-add-properties.png)

   Med Azure AD kan du skapa dynamiska grupper baserat på regler som definierar medlemskap. Läs mer om hur du [skapar attributbaserade dynamiska grupper](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

7. Du kan välja **Aktivera Office-funktioner** och ge medlemmarna i användargruppen tillgång till delade Office 365-appar. Läs mer om [Office 365-grupper](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).
8. Välj **Skapa** om du vill lägga till en ny grupp.

## <a name="groups-and-policies"></a>Grupper och principer

När du skapar grupper bör du tänka på hur du kommer att tillämpa [principerna](device-compliance-get-started.md). Du kan t.ex. ha principer som är specifika för ett operativsystem för en enhet och principer som är specifika för olika roller i din organisation eller till organisationsenheter som du redan har definierat i Active Directory. Det kan vara praktiskt att ha separata enhetsgrupper för iOS, Android och Windows, och användargrupper som är specifika för olika organisationsroller.

Du vill förmodligen även skapa en standardprincip som gäller för alla grupper och enheter och som fastställer de grundläggande kompatibilitetskraven för din organisation. Sedan kan du skapa mer specifika principer för de bredaste användar- och enhetskategorierna. Du kan till exempel skapa e-postprinciper för vart och ett av enhetsoperativsystemen.



## <a name="see-also"></a>Se även
- [Hantera åtkomst till resurser med Azure Active Directory-grupper](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Klassiska Intune-grupper i Azure-portalen](groups-get-started.md)
