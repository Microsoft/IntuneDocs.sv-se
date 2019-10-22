---
title: Enhetshantering i Microsoft 365
description: Microsoft 365 Enterprise innehåller Microsoft Intune. Se hur Intune hjälper din organisation att hantera mobilenheter och mobilprogram. Läs vanliga scenarier och använd Intune för att distribuera Microsoft 365 i din miljö.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/14/2019
ms.topic: conceptual
audience: ITPro
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfa7e34d19465eb43b5eb9cd68b7513545938fa8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504788"
---
# <a name="device-management-overview"></a>Översikt över enhetshantering

En viktig uppgift för alla administratörer är att skydda och säkra en organisations resurser och data. Den här uppgiften är *enhetshantering*. Användare har många enheter där de öppnar och delar personliga filer, besöker webbplatser och installerar appar och spel. Dessa användare är också anställda och elever. De vill använda sina enheter för att få åtkomst till arbets- och skolresurser, till exempel e-post och OneNote.

Med enhetshantering kan organisationer skydda sina resurser och data, även från olika enheter.

Med hjälp av en enhetshanteringsprovider kan organisationen se till att endast behöriga personer och enheter får åtkomst till skyddad information. På samma sätt kan enhetsanvändare enkelt få åtkomst till arbetsdata från sina telefoner eftersom de vet att deras enheter uppfyller organisationens säkerhetskrav. Å organisationens vägnar kan du ställa frågan **Vad ska vi använda för att skydda våra resurser?**

Svaret är [Microsoft Intune](what-is-intune.md). Intune erbjuder hantering av mobilenheter (MDM) och hantering av mobilprogram (MAM). Vissa viktiga uppgifter för alla MDM- och MAM-lösningar är att:

- Stödja flera olika mobila miljöer och hantera iOS-, Android-, Windows- och macOS-enheter på ett säkert sätt.
- Säkerställa att enheter och program är kompatibla med organisationens säkerhetskrav.
- Skapa principer som hjälper organisationen att skydda data på företagsägda och personliga enheter.
- Använda en enda enhetlig mobil lösning för att implementera dessa principer och hjälpa till med att hantera enheter, appar, användare och grupper.
- Skydda företagets information genom att styra hur anställda får åtkomst till och delar den.

Intune ingår i Microsoft Azure och Microsoft 365, och kan integreras med Azure Active Directory (Azure AD). Azure AD hjälper till med att kontrollera vem som har åtkomst och vad de har åtkomst till.

## <a name="microsoft-intune"></a>Microsoft Intune

Många organisationer, t.ex. Microsoft, använder Intune för att skydda egna data som användare hämtar från sina företagsägda och personliga mobila enheter. Intune innehåller konfigurationsprinciper för enheter och appar, principer för programvaruuppdatering och installationsstatus (diagram, tabeller och rapporter) som skyddar och övervakar åtkomsten till data.

Det är vanligt att personer har flera enheter som använder olika plattformar. En medarbetare kan t.ex. använda Surface Pro i arbetet och en Android-mobilenhet privat. Och det är vanligt att en person har åtkomst till företaget resurser, t.ex. Microsoft Outlook och SharePoint, från dessa olika enheter.

Med Intune kan du hantera flera enheter per person och de olika plattformar som körs på varje enhet, t.ex. iOS, macOS, Android och Windows. Intune håller principer och inställningar åtskilda på olika enhetsplattformar. Det gör det enkelt att hantera och visa enheter som hör till en viss plattform.

**[Vanliga scenarier](common-scenarios.md)** är en fantastisk resurs med vilken du kan se hur Intune ger svar på vanliga frågor när du arbetar med mobila enheter. Du hittar scenarier om:  

- Skydda e-postmeddelanden i Exchange lokalt
- Få åtkomst till Office 365 på ett säkert och skyddat sätt
- Använda personliga enheter för att få åtkomst till företagsresurser

Mer information om Intune finns i [Vad är Intune](what-is-intune.md).

## <a name="integration-with-secure-and-protect-services"></a>Integrering med tjänster för att säkra och skydda

En viktig uppgift i en enhetshanteringslösning är att tillhandahålla säkerhet och skydd. Intune gör ett bra jobb med att genomföra den här uppgiften genom integration med andra tjänster. Exempel:

- **Microsoft 365** är en viktig komponent när det gäller att förenkla vanliga IT-uppgifter. I Microsoft 365 Administrationscenter skapar du användare och hanterar grupper. Du får även åtkomst till andra tjänster, till exempel Intune och Azure AD.

  Skapa till exempel en grupp för iOS-enheter i Microsoft 365. Använd sedan Intune för att push-överföra principer till den iOS-enhetsgrupp som fokuserar på iOS-funktioner, t.ex. åtkomst till App Store, med hjälp av AirDrop, säkerhetskopiering till iCloud, användning av hjälp av Apples webbfilter och mycket mer.

- **Windows Defender** innehåller många säkerhetsfunktioner som skyddar Windows 10-enheter. Om du t.ex. använder Intune och Windows Defender tillsammans kan du:

  - Aktivera [Windows Defender SmartScreen](../protect/endpoint-protection-windows-10.md) och söka efter misstänkt aktivitet i filer och appar på mobila enheter.
  - Använd [Microsoft Defender Advanced Threat Protection (ATP)](../protect/advanced-threat-protection.md) för att förhindra säkerhetsintrång på mobila enheter. Och begränsa effekten av en säkerhetsöverträdelse genom att blockera en användares åtkomst till företagets resurser.

- **Villkorsstyrd åtkomst** är en funktion i Azure Active Directory som integreras smidigt med Intune. Med hjälp av [Villkorsstyrd åtkomst](../protect/conditional-access.md) kan du se till att endast kompatibla enheter får åtkomst till e-post, SharePoint och andra appar.

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Välj den enhetshanteringslösning som passar dig

Det finns ett par olika metoder att hantera enheter på. Du kan hantera olika enhetsaspekter med hjälp av de inbyggda funktionerna i Intune. Den här metoden kallas för **hantering av mobilenheter (MDM)** . Användare ”registrerar” sina enheter och använder certifikat för att kommunicera med Intune. Som IT-administratör kan du push-överföra appar till enheter, begränsa enheter till ett specifikt operativsystem, blockera personliga enheter och mycket annat. Om du tappar bort en enhet eller om den blir stulen kan du dessutom ta bort alla data från enheten.

I den andra metoden hanterar du appar på enheter. Den här metoden kallas för **hantering av mobilprogram (MAM)** . Användarna kan använda sina personliga enheter för att få åtkomst till företagsresurser. När användarna öppnar en app, t.ex. e-post eller SharePoint, uppmanas de att autentisera sig ytterligare. Om du tappar bort en enhet eller om den blir stulen kan du ta bort alla företagsdata från enheten.

Du kan också använda en kombination av [MDM och MAM](byod-technology-decisions.md).

När du har konfigurerat Intune kan välja att enbart arbeta i Azure Portal, eller använda Intune och Microsoft 365 tillsammans, när du hanterar enheter. [Migrera hantering av mobilenheter till Intune på Azure-portalen](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) är en Microsoft IT-fallstudie. I den här fallstudien ser du hur Microsoft IT valde en modern metod för hantering av mobilenheter. Du får också ta del av viktiga lärdomar.

## <a name="simplify-it-tasks-using-the-device-management-admin-center"></a>Förenkla IT-uppgifter med hjälp av vårt administrationscenter för enhetshantering

I vårt administrationscenter för [enhetshantering](https://devicemanagement.microsoft.com/) kan du hantera och utföra alla åtgärder för dina mobilenheter. Arbetsytan innehåller de tjänster som används för hantering av enheter, t.ex. Intune och Azure Active Directory, och även för hantering av klientappar.

I administrations centret för enhets hantering kan du:

- [Registrera enheter](../enrollment/device-enrollment.md)
- [Ange enhetsefterlevnad](../protect/device-compliance-get-started.md)
- [Hantera enheter](../remote-actions/device-management.md)
- [Hantera appar](../apps/app-management.md)  
- [iOS e-böcker](../apps/vpp-ebooks-ios.md)  
- [Installera Exchange On-premises Connector](../protect/exchange-connector-install.md)  
- [Hantera roller](role-based-access-control.md)  
- Hantera programuppdateringar
  - [Hantera Windows 10-uppdateringar](../protect/windows-update-for-business-configure.md)  
  - [Hantera iOS-uppdateringar](../protect/software-updates-ios.md)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Hantera användare](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Hantera grupper och medlemmar](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Felsöka](help-desk-operators.md)

## <a name="next-steps"></a>Nästa steg

När du är redo att sätta igång med en MDM- eller MAM-lösning går du igenom de olika stegen för att konfigurera Intune, registrera enheter och skapa principer. [Hantering av mobilenheter för Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) är också en bra resurs.
