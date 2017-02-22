---
title: "Nyheter i Microsoft Intune-förhandsversionen | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Ta reda på vad är nytt i förhandsversionen av Intune Azure"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/02/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e405363f9d0a89b1589b01d18ee8d2861b07ec60
ms.openlocfilehash: 70007f5501fba37964a0a54807c0e0f565510a74


---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Nyheter i Microsoft Intune-förhandsversionen


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


I takt med att den offentliga förhandsversionen utvecklas och fler funktioner läggs till, meddelar vi dig om dem här.

<!--## February 2017-->

<!--### Custom app categories <!--748805
You can now create, edit, and assign categories for apps you add to Intune. Currently, categories can only be specified in English.
See [How to add an app to Intune](/intune-azure/manage-apps/add-apps).-->

<!--### Display device categories <!--814654
You can now view the device category as a column in the device list. You can also edit the category from the properties section of the device properties blade.-->

## <a name="january-2017"></a>Januari 2017

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>Tilldela branschspecifika appar oavsett om enheterna har registrerats eller inte <!--748823-->
Du kan nu tilldela branschspecifika appar och appar från butiken till användare, oavsett om deras enheter är registrerade i Intune eller inte. Om användarens enhet inte har registrerats i Intune måste användaren gå till webbplatsen för företagsportalen för att installera den, i stället för företagsportalappen. Se [Vad är apphantering](/intune-azure/manage-apps/what-is-app-management)?

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Lös problemet med att iOS-enheterna är inaktiva eller att administratörskonsolen inte kan kommunicera med dem
När användarnas enheter förlorar kontakt med Intune kan du ge dem nya felsökningssteg för att hjälpa dem att återfå åtkomst till företagets resurser. Se [Enheterna är inaktiva eller så kan administratörskonsolen inte kommunicera med dem](/intune-azure/enroll-devices/troubleshoot-device-enrollment#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="december-2016-initial-release"></a>December 2016 (ursprunglig version)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Hantering av telekomkostnad i förhandsversionen av Azure-portalen<!--747605-->
Vi börjar nu att förhandsgranska integrering med tredje parters hantering av telekomkostnad (TEM) i Azure-portalen. Du kan använda Intune för att tvinga gränser för nationell och central dataanvändning. Vi börjar de här integreringarna med [Saaswedo](http://www.saaswedo.com). Om du vill aktivera den här funktionen i utvärderingsversionen av klienten kan du [kontakta Microsoft support](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

- Distribuera och hantera appar från en butik till iOS-, Android- och Windows-enheter
- Distribuera och hantera branschspecifika (LOB) appar till iOS-, Android- och Windows-enheter
- Distribuera och hantera volyminköpta appar till iOS- och Windows-enheter
- Distribuera och hantera webbappar till Android-, iOS- och Windows-enheter
- Konfigurationsprofiler för iOS-hanterade appar
- Konfigurera appskyddsprinciper och distribuera branschspecifika appar till enheter som inte har registrerats med Intune
- VPN-profiler, per-app VPN, Wi-Fi, e-post och certifikatprofiler
- Efterlevnadsprinciper
- Villkorlig åtkomst för Azure AD
- Villkorlig åtkomst för lokal Exchange
- Enhetsregistrering
- Rollbaserad åtkomstkontroll

## <a name="deprecated-features-in-the-azure-portal"></a>Inaktuella funktioner i Azure-portalen

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>Stöd för rad för rad-granskning av maskinvaruidentifierare
Azure-portalen stöder inte granskning rad för rad av maskinvaruidentifierare för IMEI-nummer och Apple-serienummer. I den klassiska Intune-konsolen kan du importera information från en fil med kommateckenavgränsade fält (.csv) och skriva över den befintliga informationen för enskilda maskinvaruidentifierare. Azure-portalen har ett enda, effektiviserat alternativ som automatiskt skriver över informationen för alla maskinvaruidentifierare eller ignorerar ny information för befintliga identifierare.

#### <a name="how-this-affects-you"></a>Hur detta påverkar dig
I Azure-portalen kan du inte bestämma rad för rad vilka IMEI-enheter (International Mobile Equipment Identity) som ska uppdateras. Den klassiska Intune-konsolen fortsätter att stödja den här funktionen.

#### <a name="how-to-get-ready-for-this-change"></a>Hur du förbereder för ändringen
Vi meddelar den här informationen i förväg så att du, om den påverkar dig, kan göra dina supportadministratörer medvetna om den här ändringen. Den här ändringen kommer sammanfalla med flytten till Azure-portalen som förväntas äga rum under första halvan av 2017.


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Stöd för standardprofiler för företagsenhetsregistrering i Apples DEP
Azure-portalen stöder inte standardprofilen för företagsenhetsregistrering för enhetsserienumren i Apples enhetsregistreringsprogram DEP. Den här funktionen, som finns tillgänglig i den klassiska Intune-konsolen, kommer upphöra för att förhindra oavsiktligt tilldelade profiler. i Azure-portalen kommer serienummer som synkroniserats från ett Apple DEP-konto inledningsvis inte ha någon profil för företagsenhetsregistrering tilldelad.

#### <a name="how-this-affects-you"></a>Hur detta påverkar dig
I Azure-portalen kommer du inte att kunna ställa in en standardprofilprincip för alla Apple-enheter. Den klassiska Intune-konsolen fortsätter att stödja den här funktionen.

#### <a name="how-to-get-ready-for-this-change"></a>Hur du förbereder för ändringen
Vi meddelar den här informationen i förväg så att du, om den påverkar dig, kan göra dina supportadministratörer medvetna om den här ändringen. Den kommer sammanfalla med flytten till Azure-portalen som förväntas äga rum under första halvan av 2017.



<!--HONumber=Feb17_HO1-->


