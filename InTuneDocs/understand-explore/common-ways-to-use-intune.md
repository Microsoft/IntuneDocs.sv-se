---
title: "Vanliga sätt att använda Intune | Microsoft Intune"
description: "Sex vanliga saker som Intune kan hjälpa dig med"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: robstackmsft
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 39e68e467c3295f4751bf3466957a8a377a8e7d6
ms.openlocfilehash: 095be86be3658a294d3f0aab525f5e0dd29b4cfe


---

# <a name="common-ways-to-use-intune"></a>Vanliga sätt att använda Intune

Innan du ger dig in på implementeringsåtgärder är det viktigt att samla företagets intressenter för Enterprise Mobility kring affärsmålen.  Det är viktigt oavsett om ni precis har börjat med Enterprise Mobility eller om ni migrerar från en annan produkt.  

Behovet av företagsmobilitet utvecklas dynamiskt och Microsofts metoder för att möta dem skiljer sig ibland från andra lösningar på marknaden.  Det bästa sättet att sätta affärsmål är att formulera dem utifrån de scenarier som du vill möjliggöra för anställda, partner och IT-avdelningen.  

Nedan följer korta introduktioner till de sex vanligaste scenarierna som förlitar sig på Intune, tillsammans med länkar till mer information om hur du planerar och distribuerar respektive scenario.

>[!NOTE]
>Vill du veta hur Microsofts IT-avdelning använder Intune för ge åtkomst till företagsresurser på mobila enheter, samtidigt som företagets data skyddas? [Läs denna tekniska fallstudie](https://www.microsoft.com/itshowcase/Article/Content/588) för att få reda på hur Microsoft IT använder Intune och andra tjänster för att hantera identitet, enheter, appar och data.  

>[!IMPORTANT]
>Vi vill säkerställa att mobila enheter är uppdaterade med hänsyn till de senaste ”Trident”-attackerna på iOS-enheter. Därför har vi publicerat blogginlägget [Kontrollera att mobila enheter är uppdaterade med hjälp av Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/). Här hittar du information om hur Intune kan hjälpa dig att hålla dina enheter skyddade och uppdaterade.

## <a name="protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Skydda lokal e-post och lokala data så att det går att komma åt dem på ett säkert sätt från mobila enheter
De flesta Enterprise Mobility-strategier börjar med en plan för att möjliggöra säker åtkomst till e-post för anställda med mobila enheter som ansluter till Internet. Många organisationer har fortfarande lokala data och programservrar, t.ex. Microsoft Exchange, som finns i företagets nätverk.

Intune och Microsoft Enterprise Mobility + Security (EMS) tillhandahåller en unik integrerad [lösning för villkorlig åtkomst](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune) för Exchange Server, som ser till att ingen mobilapp kan komma åt e-post förrän enheten har registrerats med Intune. Du kan göra allt detta utan att distribuera en till gateway-dator vid gränsen till företagets nätverk.

Med Intune kan du också aktivera åtkomst till mobilappar som kräver säker åtkomst till lokala data, t.ex. servrar för affärsappar. Detta görs normalt med [Intune-hanterade certifikat](/intune/deploy-use/secure-resource-access-with-certificate-profiles) för åtkomstkontroll som kombineras med en VPN-gateway eller proxy av standardtyp i perimeternätverket, t.ex. Microsoft Azure Active Directory-programproxy.  

I dessa fall är det enda sättet att komma åt företagets data att registrera enheten i hanteringen. När enheterna har registrerats kontrollerar hanteringssystemet att de är kompatibla med dina principer innan de kan komma åt företagsdata.  Dessutom kan Intunes [programhanteringsverktyg och App SDK](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune) användas för att hålla kvar data i den verksamhetsspecifika appen, så att det inte går att vidareföra företagsdata till konsumentappar eller konsumenttjänster.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->


## <a name="protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Skydda e-post och data i Office 365 så att det går att komma åt dem på ett säkert sätt från mobila enheter
Det kan inte bli enklare för dig eller smidigare för användarna att skydda företagets data i Office 365 (e-post, dokument, snabbmeddelanden, kontakter).

Intune och Microsoft Enterprise Mobility + Security ger en unikt integrerad lösning för villkorlig åtkomst som säkerställer att inga användare, appar eller enheter kan få åtkomst till Office 365-data om de inte uppfyller företagets efterlevnadskrav (genomförd [multifaktorautentisering](/intune/deploy-use/protect-windows-devices-with-multi-factor-authentication), registrering med Intune, använder hanterad app, OS-version som stöds, PIN-kod för enhet, profil med låg användarrisk osv.). Office-mobilapparna i respektive appbutik är redo att köras med datainneslutningsprinciper som du kan konfigurera via Intune, som gör det möjligt att förhindra att data delas med appar (t.ex. intern e-postapp) och lagringsplatser (t.ex. Dropbox) som inte hanteras av IT-avdelningen.  Alla dessa funktioner är inbyggda i Office 365 och EMS.  Du behöver inte distribuera ytterligare infrastruktur för att dra nytta av detta mervärde.

Office-mobilapparna i deras respektive appbutiker är redo att användas med datainneslutningsprinciper som du kan konfigurera via Intune. Det gör att du kan förhindra att data delas med appar (t.ex. med interna e-postappar) och lagringsplatser (t.ex. Dropbox) som inte hanteras av IT.  Alla dessa funktioner är inbyggda i Office 365 och EMS.  Du behöver inte distribuera ytterligare infrastruktur för att dra nytta av detta mervärde.


En vanlig Office 365-distributionsmetod är att kräva att enheterna registreras för hantering om de måste vara helt konfigurerade med företagsappar, certifikat, Wi-Fi eller VPN-konfigurationer, vilket ofta är fallet med företagsägda enheter.  

Om användaren bara behöver åtkomst till företagets e-post och dokument, vilket ofta är fallet med personligt ägda enheter, måste användaren använda Office-mobilapparna (som du har [tillämpat datainneslutningsprinciper](/intune/deploy-use/protect-apps-and-data-with-microsoft-intune) på) och behöver inte registrera enheten.  

Vilken metod som än används skyddas Office 365-data av principer som du har definierat.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->


## <a name="offer-a-bring-your-own-device-program-to-all-employees"></a>Erbjuder ett BYOD-program (”Bring Your Own Device”) för alla anställda
BYOD blir allt populärare hos organisationer som ett sätt att minska maskinvaruutgifterna eller öka medarbetarnas valmöjligheter för mobil produktivitet. I princip alla har en egen telefon idag så varför ska de behöva en till att bära på? Den främsta utmaningen har alltid varit att övertyga medarbetarna att registrera sina personliga enheter i hantering, eftersom de är oroliga för vad IT-avdelningen kommer att kunna se och göra med enheten.  

Om enhetsregistrering inte är ett genomförbart alternativ erbjuder Intune en alternativ BYOD-metod som innebär att helt enkelt [hantera de appar som innehåller företagsdata](/intune/deploy-use/protect-apps-and-data-with-microsoft-intune).  Intune skyddar företagets data även om appen i fråga har åtkomst till både företagsrelaterade och personliga data, som är fallet för Office-mobilappar.  

Som administratör kan du kräva att användarna kommer åt Office 365 från Office-mobilapparna och konfigurera apparna med principer som ser till att data är skyddade (t.ex. kryptering, PIN-kod och så vidare).  Dessa principer förhindrar dataförlust från ohanterade appar och lagringsplatser – i eller utanför dessa appar.  Principerna förhindrar till exempel att en användare kopierar text från en e-postprofil för företaget till en privat e-postprofil, även om båda profilerna är konfigurerade i Outlook Mobile.  Liknande konfigurationer kan distribueras för andra tjänster och program som krävs av BYOD-användarna.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## <a name="issue-corporate-owned-phones-to-your-information-workers"></a>Utfärda företagsägda telefoner till informationsarbetarna
De flesta informationsarbetare är idag mobila, vilket gör att produktivitet på mobila enheter är avgörande för att vara konkurrenskraftig.  Dessa medarbetare behöver smidig åtkomst till alla företagets appar och data, när som helst, var som helst.  Du måste se till att företagets data är säkra och att de administrativa kostnaderna är låga.  

Intune erbjuder [massetablering och hanteringslösningar](/intune/deploy-use/manage-corporate-owned-devices) som är integrerade med de flesta stora enhetshanteringsplattformar som finns på marknaden idag, inklusive Apple Device Enrollment Program och mobilsäkerhetsplattformen Samsung KNOX.  Centraliserad redigering av enhetskonfigurationer med Intune gör att det i hög grad går att automatisera etableringen av företagsenheter.  

Tänk dig detta: ge en medarbetare en oöppnad låda med en iPhone. Medarbetaren aktiverar den och går igenom ett företagsanpassat konfigurationsflöde där användaren måste autentisera sig. iPhone konfigureras sömlöst med [säkerhetsprinciper](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) (t.ex. en krypterad hårddisk och PIN-kod för enheter),  [e-post-, Wi-Fi/VPN- och certifikatprofiler](/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune) och en baslinjeuppsättning med [appar](/intune/deploy-use/add-apps).

Den anställda startar sedan Intune-företagsportalappen för att komma åt valfria företagsappar som är tillgängliga.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## <a name="issue-limited-use-shared-tablets-to-your-task-workers"></a>Utfärda delade surfplattor med begränsad användning till uppdragspersonal
Uppdragspersonal använder mobil teknik i allt större omfattning.  Exempelvis används delade surfplattor ofta av anställda inom detaljhandeln.  Oavsett om de används för att hantera en försäljning eller för att snabbt kontrollera lagret hjälper surfplattorna till att skapa positiva kundmöten.

Den enkla användarupplevelsen är avgörande i detta fall.  Därför får anställda ofta surfplattor med begränsad användning, så att en enda branschspecifik app är allt de kan interagera med.  Intune gör det möjligt att massetablera, skydda och centralt hantera dessa delade [iOS](/intune/deploy-use/ios-policy-settings-in-microsoft-intune#general-configuration-policy-settings)- och [Android](/intune/deploy-use/android-policy-settings-in-microsoft-intune#general-configuration-policy)-surfplattor som kan konfigureras för att köras i detta läge med begränsad användning.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## <a name="enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk"></a>Gör det möjligt för medarbetarna att på ett säkert sätt få åtkomst till Office 365 från en ej hanterad offentlig dator
Ibland behöver anställda använda enheter, appar eller webbläsare som du inte kan hantera, t.ex. offentliga datorer på mässor och hotell.

Ska du tillåta att medarbetarna får åtkomst till företagets e-post från dem? Med Intune och Microsoft Enterprise Mobility + Security <!--you have choices. The--> kan du enkelt välja att inte göra det genom att [begränsa e-poståtkomsten till enheter som hanteras av din organisation](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).  <!-- Alternatively, you can choose to allow limited access to these untrusted computers by requiring multi-factor authentication and only allowing browser access (Outlook Web Access) in a mode where files cannot be downloaded (e.g. email attachments).--> Detta säkerställer att en autentiserad anställd oavsiktligt lämnar företagsdata på den icke-betrodda datorn.

<!-- Learn more about how to plan and deploy Intune to support kiosks. -->



<!--HONumber=Nov16_HO3-->

