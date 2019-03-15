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
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34d1cbe969b8e186d9e067660237da9c4ca88fb8
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57396213"
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

Vi vet att det kan vara svårt att komma igång med att hantering av mobila enheter eftersom man måste fatta många svåra beslut å företagets vägnar. Slutför följande snabbstarter för att komma igång med Intune och genomför några vanliga uppgifter på kortast möjliga tid.

Du kan följa **snabbstarterna** i avsedd ordning med hjälp av innehållsförteckningen till vänster på sidan.

- [Prova Intune utan kostnad](free-trial-sign-up.md) – Skapa en kostnadsfri prenumeration för att prova Intune i en testmiljö.    
- [Skapa en användare](quickstart-create-user.md) – Lägg till användare i Intune och låt dem få tillgång till företagsresurser på mobila enheter.
- [Skapa en grupp](quickstart-create-group.md) – Dela upp användare i grupper för att göra det lättare att hantera principer och appar som de har åtkomst till.
- [Konfigurera automatisk registrering](quickstart-setup-auto-enrollment.md) – Konfigurera Microsoft Intune till att automatiskt registrera enheter när specifika användare loggar in på Windows 10-enheter.
- [Registrera din enhet](quickstart-enroll-windows-device.md) – Anta rollen som Intune-användare och registrera din enhet i Microsoft Intune. Gå sedan tillbaka till Intune och bekräfta den registrerade enheten.
- [Skapa en enhetsefterlevnadsprincip](quickstart-set-password-length-android.md) – Skapa en enhetsefterlevnadsprincip och tilldela en grupp till principen.
- [Skicka meddelanden till icke-kompatibla enheter](quickstart-send-notification.md) – Skicka ett e-postmeddelande till de medlemmar i personalen som har icke-kompatibla enheter genom att skapa och tilldela en policy för efterlevnad.
- [Lägg till och tilldela en app](quickstart-add-assign-app.md) – Lägg till och tilldela en klientapp till företagets personal.
- [Skapa och tilldela en appskyddsprincip](quickstart-create-assign-app-policy.md) – Skapa och tilldela en appskyddsprincip till en klientapp på en slutanvändares enhet.
- [Skapa och tilldela en anpassad roll](quickstart-create-custom-role.md) – Skapa och tilldela en anpassad roll med särskilda behörigheter för en säkerhetsåtgärdsavdelning. 
- [Skapa en e-enhetsprofil för iOS](quickstart-email-profile.md) – skapa en e-postenhetsprofil för iOS-enheter.

## <a name="prerequisites"></a>Krav

Du måste ha en Intune-administratör och ett klientkonto aktiverat innan du börjar. [Prova Intune utan kostnad](free-trial-sign-up.md) – Skapa en kostnadsfri prenumeration för att prova Intune i en testmiljö. Alla befintliga prenumeranter kan också utföra aktiviteter i liveklienten. Dessa artiklar för att komma igång förutsätter att du arbetar på testenheter.

Du måste också säkerställa att du är global administratör för din organisation för att kunna utföra alla kom igång-aktiviteter i guiden.

## <a name="intune-architecture"></a>Intune-arkitektur

Intune är en komponent i Enterprise Mobility + Security (EMS) som hanterar mobila enheter och appar. Det är nära integrerat med andra EMS-komponenter som Azure Active Directory (Azure AD) för identitets- och åtkomstkontroll och Azure Information Protection för dataskydd. När du använder det tillsammans med Office 365 gör du det möjligt för dina anställda att vara produktiva på alla deras enheter samtidigt som organisationens information är skyddad.

![Övergripande arkitekturdiagram för Microsoft Intune](/intune/media/intunearchitecture.svg)

## <a name="next-steps"></a>Nästa steg

[Kom igång med Azure](get-started-azure.md) – Förstå hur Azure Portal är uppbyggt och hur du gör ändringar på den sida som visas.

## <a name="learn-more"></a>Läs mer

* [Vad är Intune?](introduction-intune.md)
* [Vad är Azure-portalen?](what-is-intune.md)
* [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md)
