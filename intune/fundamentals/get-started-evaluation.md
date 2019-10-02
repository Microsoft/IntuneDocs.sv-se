---
title: Vad kan Microsoft Intune göra för mitt företag
titleSuffix: ''
description: Microsoft Intune hjälper dig att lösa vanliga affärsproblem.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/26/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 845eb22522895e04f6ec4f46eda7a817e27a830c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726537"
---
# <a name="what-can-intune-do-for-my-company"></a>Vad kan Intune göra för mitt företag?
Microsoft Intune är en molnbaserad tjänst för hantering av företagsmobilitet (EMM) som hjälper anställda att vara produktiva samtidigt som företagets data skyddas.

Med Intune kan du:

- Hantera mobila enheter som anställda använder för att komma åt företagets data.
- Hantera mobila appar som används av anställda.
- Skydda företagets information genom att styra hur anställda får åtkomst till och delar den.
- Säkerställa att enheter och program är kompatibla med företagets säkerhetskrav.

## <a name="common-business-problems-that-intune-helps-solve"></a>Exempel på vanliga affärsproblem som Intune kan lösa

* [Skydda lokal e-post och lokala data så att mobila enheter kan komma åt dem](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Skydda e-post och data i Office 365 så att mobila enheter kan komma åt dem på ett säkert sätt](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Dela ut företagsägda telefoner till anställda](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Erbjud BYOD (Bring Your Own Device) eller ett program för personliga enheter till alla anställda](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Gör det möjligt för anställda att på ett säkert sätt få åtkomst till Office 365 från en ej hanterad offentlig dator](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Utfärda delade surfplattor med begränsad användning till uppdragspersonal](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="quickstarts"></a>Snabbstarter

Vi förstår att det kan vara svårt att komma igång med hanteringen av mobila enheter. Det finns många olika beslut som du måste fatta på företagets vägnar. Slutför följande snabbstarter för att komma igång med Intune och genomföra några vanliga uppgifter på kortast möjliga tid.

Du kan följa **snabbstarterna** i avsedd ordning med hjälp av innehållsförteckningen till vänster.

- [Prova Intune utan kostnad](free-trial-sign-up.md) – Skapa en kostnadsfri prenumeration för att prova Intune i en testmiljö.    
- [Skapa en användare](quickstart-create-user.md) – Lägg till användare i Intune och låt dem få tillgång till företagsresurser på mobila enheter.
- [Skapa en grupp](quickstart-create-group.md) – Dela upp användare i grupper för att göra det lättare att hantera de principer och appar som användarna har åtkomst till.
- [Konfigurera automatisk registrering](../enrollment/quickstart-setup-auto-enrollment.md) – Konfigurera Intune till att automatiskt registrera enheter när specifika användare loggar in på Windows 10-enheter.
- [Registrera din enhet](../enrollment/quickstart-enroll-windows-device.md) – Anta rollen som Intune-användare och registrera din enhet i Microsoft Intune. Gå sedan tillbaka till Intune och bekräfta att enheten har registrerats.
- [Skapa en enhetsefterlevnadsprincip](../protect/quickstart-set-password-length-android.md) – Skapa en enhetsefterlevnadsprincip och tilldela en grupp till principen.
- [Skicka meddelanden till icke-kompatibla enheter](../protect/quickstart-send-notification.md) – Skicka ett e-postmeddelande till de medlemmar i personalen som har icke-kompatibla enheter genom att skapa och tilldela en policy för efterlevnad.
- [Lägg till och tilldela en app](../apps/quickstart-add-assign-app.md) – Lägg till och tilldela en klientapp till företagets personal.
- [Skapa och tilldela en appskyddsprincip](../apps/quickstart-create-assign-app-policy.md) – Skapa och tilldela en appskyddsprincip till en klientapp på en slutanvändares enhet.
- [Skapa och tilldela en anpassad roll](create-custom-role.md) – Skapa och tilldela en anpassad roll med särskilda behörigheter för en säkerhetsåtgärdsavdelning. 
- [Skapa en e-enhetsprofil för iOS](../configuration/quickstart-email-profile.md) – skapa en e-postenhetsprofil för iOS-enheter.

## <a name="prerequisites"></a>Krav

Du måste ha ett konto för en Intune-administratör och för en klientorganisation aktiverat innan du börjar. [Prova Intune utan kostnad](free-trial-sign-up.md) – Skapa en kostnadsfri prenumeration för att prova Intune i en testmiljö. Befintliga prenumeranter kan också utföra aktiviteterna i deras aktiverade klientorganisation. Dessa artiklar för att komma igång förutsätter att du arbetar på testenheter.

Du måste också säkerställa att du är global administratör för din organisation för att kunna utföra alla kom igång-aktiviteter i guiden.

## <a name="intune-architecture"></a>Intune-arkitektur

Intune är en komponent i Enterprise Mobility + Security (EMS) som hanterar mobila enheter och appar. Det är nära integrerat med andra EMS-komponenter som Azure Active Directory (Azure AD) för identitets- och åtkomstkontroll och Azure Information Protection för dataskydd. När du använder det tillsammans med Office 365 gör du det möjligt för dina anställda att vara produktiva på alla deras enheter samtidigt som organisationens information skyddas.

![Övergripande arkitekturdiagram för Microsoft Intune](./media/get-started-evaluation/intunearchitecture.svg)

## <a name="next-steps"></a>Nästa steg

[Kom igång med Azure](tutorial-walkthrough-intune-portal.md) – Förstå hur Azure Portal är uppbyggt och hur du gör ändringar på den sida som visas.

## <a name="learn-more"></a>Läs mer

- [Vad är Intune?](what-is-intune.md)
- [Vad är Azure-portalen?](what-is-intune.md)
- [Översikt över enhets- och applivscykler](device-lifecycle.md)
