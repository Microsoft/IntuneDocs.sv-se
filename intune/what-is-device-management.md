---
title: Enhetshantering i Microsoft 365
description: Microsoft 365 Enterprise innehåller Microsoft Intune. Se hur Intune tillhandahåller hantering av mobilenheter och hantering av mobilprogram för din organisation, inklusive vanliga scenarier, och använder Intune för att distribuera Microsoft 365 i din miljö.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/21/2018
ms.topic: article
audience: ITPro
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.custom: microsoft-intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.openlocfilehash: 153f49ce0799ed181c9cb904c7c8ed88509805cc
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581837"
---
# <a name="what-is-device-management"></a>Vad är enhetshantering? 

En viktig uppgift för alla administratörer är att skydda och säkra en organisations resurser och data. Den här uppgiften är enhetshantering. Användare har många enheter från vilka de öppnar och delar personliga filer, besöker webbplatser och installerar appar och spel. Dessa användare är också anställda och studenter och vill använda sina enheter för att få åtkomst till arbets- och skolrelaterade resurser, t.ex. e-post och OneNote. *Enhetshantering* innebär att organisationer kan skydda och säkra sina resurser och data. 

Med hjälp av en enhetshanteringslprovider kan organisationen se till att endast behöriga personer och enheter får åtkomst till skyddad information. På samma sätt kan enhetsanvändare enkelt få åtkomst till arbetsdata från sina telefoner eftersom de vet att deras enheter uppfyller organisationens säkerhetskrav. Å organisationens vägnar kan du ställa frågan **Vad ska vi använda för att skydda våra resurser?**

Det är här som [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune) kommer in i bilden. Intune erbjuder hantering av mobilenheter (MDM) och hantering av mobilprogram (MAM). Vissa viktiga uppgifter för alla MDM- och MAM-lösningar är att:

- Stödja flera olika mobila miljöer&mdash;hantera iOS, Android, Windows och macOS-enheter på ett säkert sätt
- Säkerställa att enheter och program är kompatibla med organisationens säkerhetskrav
- Skapa principer som hjälper organisationen att skydda data på företagsägda och personliga enheter
- Använda en enda enhetlig mobil lösning för att implementera dessa principer och hjälpa till med att hantera enheter, appar, användare och grupper.

Intune ingår i Microsoft 365 och integreras med Azure Active Directory (Azure AD). Azure AD hjälper till med att kontrollera vem som har åtkomst och vad de har åtkomst till.

## <a name="hello-intune"></a>Hej Intune!
Många organisationer, t.ex. Microsoft, använder Intune för att skydda egna data som användare hämtar från sina företagsägda och personliga mobila enheter. Intune innehåller funktioner som enhets- och konfiguration principer, software update principer, och installation status (samt diagram, tabeller och rapporter) för att skydda och övervaka dataåtkomst.

Det är vanligt att personer har flera enheter som använder olika plattformar. En medarbetare kan t.ex. använda Surface Pro i arbetet och en Android-mobilenhet privat. Och det är vanligt att en person har åtkomst till företaget resurser, t.ex. Microsoft Outlook och SharePoint, från dessa olika enheter.

Med Intune kan du hantera flera enheter per person och de olika plattformar som körs på varje enhet, t.ex. iOS, macOS, Android och Windows. Intune skiljer mellan principer och inställningar efter enhetsplattform, så det är enkelt att hantera och visa enheter med en viss plattform.

**[Vanliga scenarier](https://docs.microsoft.com/intune/common-scenarios)** är en fantastisk resurs med vilken du kan se hur Intune ger svar på vanliga frågor när du arbetar med mobila enheter. Du hittar scenarier om:  
- Skydda e-postmeddelanden i Exchange lokalt
- Få åtkomst till Office 365 på ett säkert och skyddat sätt
- Använda personliga enheter för att få åtkomst till företagsresurser

## <a name="integration-with-secure-and-protect-services"></a>Integrering med tjänster för att säkra och skydda
En viktig uppgift i en enhetshanteringslösning är att tillhandahålla säkerhet och skydd. Intune gör ett bra jobb med att genomföra den här uppgiften genom integration med andra tjänster. Exempel:

- **Microsoft 365** är en viktig komponent när det gäller att förenkla vanliga IT-uppgifter. Med Microsoft 365 Administrationscenter kan du skapa användare, hantera grupper och få åtkomst till andra tjänster som Intune och Azure Active Directory. Du kan t.ex. skapa en grupp för iOS-enheter i Microsoft 365. Använd sedan Intune för att push-överföra principer till den iOS-enhetsgrupp som fokuserar på iOS-funktioner, t.ex. åtkomst till App Store, med hjälp av AirDrop, säkerhetskopiering till iCloud, användning av hjälp av Apples webbfilter och mycket mer.

- **Windows Defender** innehåller många säkerhetsfunktioner som skyddar Windows 10-enheter. Om du t.ex. använder Intune och Windows Defender tillsammans kan du: 

    - Aktivera [Windows Defender SmartScreen](https://docs.microsoft.com/intune/endpoint-protection-windows-10) och söka efter misstänkt aktivitet i filer och appar på mobila enheter. 
    - Använd [Windows Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/intune/advanced-threat-protection) om du vill förhindra säkerhetsintrång på mobila enheter och begränsa effekten av en säkerhetsöverträdelse genom att blockera en användare från företagets resurser.

- **Villkorsstyrd åtkomst** är en funktion i Azure Active Directory som integreras smidigt med Intune. Med hjälp av [villkorsstyrd åtkomst](https://docs.microsoft.com/intune/conditional-access) kan du kontrollera att endast kompatibla enheter får åtkomst till e-post, SharePoint och andra appar. 

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Välj den enhetshanteringslösning som passar dig

Det finns ett par olika metoder att hantera enheter på. Du kan börja hantera alla aspekter av enheterna genom att använda alla inbyggda Intune-funktioner. Detta kallas **Hantering av mobilenheter (MDM)**. I den här metoden ”registrerar” användarna sina enheter och använder certifikat för att kommunicera med Intune. Som IT-administratör kan du push-överföra appar till enheter, begränsa enheter till ett specifikt operativsystem, blockera personliga enheter och mycket annat. Om du tappar bort en enhet eller om den blir stulen kan du dessutom ta bort alla data från enheten. 

I den andra metoden hanterar du appar på enheter. Detta kallas **Hantering av mobilprogram (MAM)**. Med den här metoden kan användare använda sina personliga enheter för att få åtkomst till företagsresurser. När användarna öppnar en app, t.ex. e-post eller SharePoint, uppmanas de att autentisera sig ytterligare. Om du tappar bort en enhet eller om den blir stulen kan du ta bort alla företagsdata från enheten. 

Du kan också använda en kombination av [MDM och MAM](https://docs.microsoft.com/intune/byod-technology-decisions).

När du har konfigurerat Intune kan välja att enbart arbeta i Azure Portal, eller använda Intune och Microsoft 365 tillsammans, när du hanterar enheter. Se hur Microsoft IT valde en modern metod för enhetshantering och ta del av lärdomarna i Microsoft IT-fallstudien [Migrera hantering av mobilenheter till Intune i Azure Portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal). 

## <a name="simplify-it-tasks-using-the-device-management-dashboard"></a>Förenkla IT-uppgifter med hjälp av instrumentpanelen för enhetshantering

På instrumentpanelen för [enhetshantering](https://devicemanagement.portal.azure.com/) kan du hantera och utföra alla åtgärder för dina mobilenheter. Den här instrumentpanelen innehåller de tjänster som används för hantering av enheter, t.ex. Intune och Azure Active Directory, och även för hantering av klientappar. 

På instrumentpanelen för enhetshantering kan du:

- [Registrera enheter](https://docs.microsoft.com/intune/device-enrollment)
- [Ange enhetsefterlevnad](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Hantera enheter](https://docs.microsoft.com/intune/device-management)
- [Hantera appar](https://docs.microsoft.com/intune/app-management)  
- [iOS e-böcker](https://docs.microsoft.com/intune/vpp-ebooks-ios)  
- [Installera Exchange On-premises Connector](https://docs.microsoft.com/intune/exchange-connector-install)  
- [Hantera roller](https://docs.microsoft.com/intune/role-based-access-control)  
- Hantera programuppdateringar
  - [Hantera Windows 10-uppdateringar](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
  - [Hantera iOS-uppdateringar](https://docs.microsoft.com/intune/software-updates-ios)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Hantera användare](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Hantera grupper och medlemmar](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Felsöka](https://docs.microsoft.com/intune/help-desk-operators)

## <a name="next-step"></a>Nästa steg
När du är redo att sätta igång med en MDM- eller MAM-lösning kan du gå igenom de olika stegen för att konfigurera Intune, registrera enheter och börja skapa principer. Mer information finns i [Hantering av mobilenheter för Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure). 
