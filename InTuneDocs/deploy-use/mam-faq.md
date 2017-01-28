---
title: "Vanliga frågor och svar om MAM och appskydd"
description: "Den här artikeln ger svar på några vanliga frågor om Intune mobile application management (MAM) och Intune appskydd."
keywords: 
author: oydang
ms.author: oydang
manager: mtillman
ms.date: 01/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: oydang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 474bb04d743290ff78aa0772595b744be46ae1af
ms.openlocfilehash: b6b2d066b773e91003884a8735b6663ebf125aa3


---

# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Vanliga frågor och svar om MAM och appskydd

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Den här artikeln ger svar på några vanliga frågor om Intune mobile application management (MAM) och Intune appskydd.

## <a name="mam-basics"></a>Grundläggande om MAM


**Vad är MAM?** Med [Intune mobile application management](overview-of-app-lifecycle-in-microsoft-intune.md) avses den svit av Intune-hanteringsfunktioner som låter dig publicera, pusha, konfigurera, skydda, övervaka och uppdatera mobilappar för dina användare.

**Vilka är fördelarna med MAM appskydd?** MAM skyddar företagets data inom ett program. Med hjälp av MAM-WE kan en arbets- eller skolrelaterad app som innehåller känsliga data hanteras på nästan alla enheter, inklusive personliga enheter i bring-your-own-device (BYOD)-scenarier. Många produktivitetsappar, som till exempel Microsoft Office-apparna, kan hanteras av Intune MAM. Se listan över officiella [Intune-upplysta appar](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps) tillgängliga för allmänt bruk.

**Vilka enhetskonfigurationer har MAM stöd för?** Intune MAM stöder två konfigurationer:
  1. **Intune MDM + MAM**: Detta är den första konfiguration som hade stöd av MAM när den först lanserades. IT-administratörer kan bara hantera appar med hjälp av MAM och appskyddsprinciper på enheter som registreras med Intune mobile device management (MDM). För att hantera appar med hjälp av MDM + MAM ska kunder använda den fristående Intune-konsolen på http://manage.microsoft.com.

  2. **MAM utan enhetsregistrering**: Med MAM utan enhetsregistrering, eller MAM-WE, kan IT-administratörer hantera appar med hjälp av MAM och appskyddsprinciper på enheter som inte har registrerats med Intune MDM. Detta innebär att appar kan hanteras av Intune på enheter som registrerats med tredje parts EMM-leverantörer. För att hantera appar med hjälp av MAM-WE ska kunder använda Intune-konsolen i Azure-portalen på http://portal.azure.com.


## <a name="app-protection-policies"></a>Appskyddsprinciper

**Vad är appskyddsprinciper**? Appskyddsprinciper är regler som säkerställer att organisationens data förblir säkra eller inkluderas i en hanterad app. En princip kan vara en regel som tillämpas när användaren försöker få åtkomst till eller flytta "företagsdata", eller en uppsättning åtgärder som är förbjudna eller övervakas när användaren är inne i appen.

**Vilka exempel finns det på appskyddsprinciper?** Se [Inställningar för Android-appskyddsprinciper](android-mam-policy-settings.md) och [Inställningar för iOS-appskyddsprinciper](ios-mam-policy-settings.md) för detaljerad information om respektive inställning av appskyddprincip.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Appar som du kan hantera med appskyddsprinciper

**Vilka appar kan hanteras med appskyddsprinciper?** Alla appar som har blivit upplysta av [Intune App-SDK](../develop/intune-app-sdk.md) eller hanteras av [Intunes apphanteringsverktyg](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) kan hanteras med Intunes appskyddsprinciper. Se listan över officiella [Intune-upplysta appar](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps) tillgängliga för allmänt bruk.

**Vilka är de grundläggande kraven för att använda appskyddsprinciper på en Intune-upplyst app?**
  1. Slutanvändaren måste ha ett Azure Active Directory (AAD)-konto. Se [Lägg till användare och ge administrativ behörighet till Intune](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3.md) för information om hur du skapar Intune-användare i Azure Active Directory.

  2. Slutanvändaren måste ha en licens för Microsoft Intune som tilldelats deras Azure Active Directory-konto. Se [Hantera Intune-licenser](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4.md) för information om hur du tilldelar Intune-licenser till slutanvändarna.

  3. Slutanvändaren måste tillhöra en säkerhetsgrupp som är målet för en appskyddsprincip. Samma appskyddsskyddsprincip måste ha den specifika app som används som mål. Appskyddsprinciper kan skapas och distribueras i Intune-konsolen i [Azure-portalen](http://portal.azure.com). Säkerhetsgrupper kan för närvarande skapas i [Office-portalen](http://portal.office.com).

  4. Slutanvändaren måste logga in på appen med sitt AAD-konto.

**Vilka är de ytterligare krav som ställs för användning av [Outlook-mobilappen](https://www.microsoft.com/en-us/outlook-com/mobile/)?**

  1. Slutanvändaren måste ha Outlook-mobilappen installerad på sin enhet.

  2. Slutanvändaren måste ha en [Office 365 Exchange Online](https://products.office.com/en-us/exchange/exchange-online)-postlåda och licens kopplad till deras Azure Active Directory-konto.

  >[!NOTE]
  > Outlook-mobilappen har för närvarande endast stöd för Microsoft Exchange Online och har inte stöd för Exchange på plats eller Exchange i Office 365 Dedicated.

**Vilka är de ytterligare krav som ställs för användning av [Word-, Excel- och PowerPoint](https://products.office.com/business/office)-apparna?**

  1. Slutanvändaren måste ha en licens för [Office 365 Business eller Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) som länkats till deras Azure Active Directory-konto. Prenumerationen måste inkludera Office-apparna på mobila enheter och ett molnlagringskonto med [OneDrive för företag](https://onedrive.live.com/about/business/). Office 365-licenser kan tilldelas i [Office-portalen](http://portal.office.com) med hjälp av följande [instruktioner](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc?ui=en-US&rs=en-US&ad=US).

  2. Slutanvändaren måste ha [OneDrive](https://onedrive.live.com/about/)-appen installerad på sin enhet och logga in med sitt AAD-konto.

  3. OneDrive-appen måste vara mål för appskyddsprincipen som distribueras till slutanvändaren.

  >[!NOTE]
  > Office mobilappar har för närvarande endast stöd för SharePoint Online och inte SharePoint på plats.

**Varför behövs OneDrive för Office?** Intune markerar all data i appen som "företag" eller "personligt." Data anses som "företagets" när det kommer från en företagsplats. För Office-apparna betraktar Intune följande platser som företagets: e-post (Exchange) eller molnlagring (OneDrive-app med ett konto för OneDrive för företag).

**Vilka är de ytterligare krav som ställs för användning av Skype för företag?** Se licenskraven för [Skype för företag](https://products.office.com/skype-for-business/it-pros).
  >[!NOTE]
  > Skype för företag-mobilappen har för närvarande endast stöd för Skype för företag – Online.

## <a name="app-protection-features"></a>Appskyddsfunktioner

**Vad är stöd för flera identiteter?** Stöd för flera identiteter är möjligheten för Intune App SDK att bara tillämpa appskyddsprinciper på arbets- eller skolkontot som använts för inloggning i appen. Om ett personligt konto är inloggat i appen förblir datan orörd.

**Vad är syftet med stöd för flera identiteter?** Stöd för flera identiteter gör att appar med både "företags-" och konsumentanvändare (t.ex. Office-appar) kan släppas offentligt med Intunes appskyddsfunktioner för "företagets" konton.

**När visas PIN-kodsskärmen?** Intunes PIN-kodsskärm visas bara när användaren försöker få åtkomst till företagsdata i appen. I till exempel Word/Excel/PowerPoint-appar visas den när slutanvändaren försöker öppna ett dokument från OneDrive för företag (förutsatt att du har distribuerat en appskyddsprincip med tvingande PIN-kod).

**Vad gäller för Outlook och flera identiteter?** Eftersom Outlook har en kombinerad e-postvy över både personliga och "företagets" e-postmeddelanden frågar Outlook-appen efter Intune-PIN vid start.

**Vad är Intune-appens PIN-kod?** PIN-kod (Personal Identification Number) är ett lösenord som används för att verifiera att rätt användare har åtkomst till organisationens data i en app.

  1. **När uppmanas användaren att ange sin PIN-kod?** Intune frågar endast efter användarens PIN-kod för appen när användaren ska få åtkomst till "företagsdata". I appar för flera identiteter som till exempel Word/Excel/PowerPoint uppmanas användarna att ange sina PIN-koder när de försöker öppna ett "företags"-dokument eller -fil. I appar för en identitet, till exempel branschspecifika appar upplysta med Intune apphanteringsverktyg, efterfrågas PIN-koden redan vid start eftersom Intune App SDK vet att användarupplevelsen i appen alltid är "företag."

  2. **Är PIN-kod säkert?** PIN-koden fungerar så att endast rätt användare får åtkomst till organisationens data i appen. Därför måste slutanvändarna logga in med sina arbets- eller skolkonton innan de kan ange eller återställa Intune-appens PIN-kod. Den här autentiseringen hanteras av Azure Active Directory via utbyte av säker token och är inte transparent för Intune App SDK. Ur ett säkerhetsperspektiv är bästa sättet att skydda data från arbete eller skola att kryptera den. Kryptering är inte relaterad till appens PIN-kod, utan en egen appskyddsprincip.

  3. **Hur skyddar Intune PIN-koden mot nyckelsökningsattacker?** Som en del av appens PIN-princip kan IT-administratören ange det maximala antalet gånger som en användare kan försöka att autentisera sin PIN-kod innan appen blir låst. När antalet försök har uppfyllts kan Intune App SDK rensa företagets data i appen.

**Vad gäller för kryptering?** IT-administratörer kan distribuera en appskyddsprincip som kräver att appdata krypteras. Som en del av principen kan IT-administratören även ange när innehållet krypteras.

  1. **Hur krypterar Intune data?** Se [Inställningar för Android-appskyddsprinciper](android-mam-policy-settings.md) och [Inställningar för iOS-appskyddsprinciper](ios-mam-policy-settings.md) för detaljerad information om inställning av appskyddprincip för kryptering.

  2. **Vad krypteras?** Endast data som har markerats som "företagets" krypteras enligt IT-administratörens appskyddsprincip. Data anses som "företagets" när det kommer från en företagsplats. För Office-apparna betraktar Intune följande platser som företagets: e-post (Exchange) eller molnlagring (OneDrive-app med ett konto för OneDrive för företag). För branschspecifika appar upplysta av Intunes programhanteringsverktyg betraktas all appdata som "företagets."

**Hur fjärrensar Intune data?** Intune kan rensa AppData på tre olika sätt: fullständig rensning av enheten, selektiv rensning för MDM och MAM-selektiv rensning. Mer information om fjärrensning för MDM finns i [Skydda data med fullständig eller selektiv rensning med Microsoft Intune](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md). Mer information om selektiv rensning med MAM finns i [Rensa hanterade företagsdata från appar med Microsoft Intune](wipe-managed-company-app-data-with-microsoft-intune.md)

  1. **Vad är fullständig rensning?** [Fullständig rensning](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe) tar bort all användardata och inställningar från **enheten** genom att återställa den till fabriksinställningarna. Enheten tas bort från Intune.
  >[!NOTE]
  > Fullständig rensning kan bara ske på enheter som registrerats med Intunes hantering av mobila enheter (MDM).

  2. **Vad är selektiv rensning för MDM?** Se [Skydda data med fullständig eller selektiv rensning med Microsoft Intune](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) för att läsa om selektiv rensning.

  3. **Vad är selektiv rensning för MAM?** Selektiv rensning för MAM tar helt enkelt bort företagsdata från en app. Begäran initieras med hjälp av Intune Azure-portalen. Information om hur du startar en rensningsbegäran finns i [Rensa hanterade företagsdata från appar med Microsoft Intune](wipe-managed-company-app-data-with-microsoft-intune.md)

  4. **Hur snabbt sker selektiv rensning för MAM?** Om användaren använder appen när selektiv rensning initieras söker Intune App SDK var 30:e minut efter en begäran om selektiv rensning från Intune MAM-tjänsten. Den söker även efter selektiv rensning när användaren startar appen för första gången och loggar in med sitt arbets- eller skolkonto.

**Varför fungerar inte tjänster på plats med Intunes appskydd?** Intunes appskydd är beroende av att användarens identiteten är konsekvent mellan appen och Intune App SDK. Det enda sättet att garantera detta är via modern autentisering. Det finns scenarier där appar kan fungera med en lokal konfiguration, men de är varken konsekventa eller garanterade.

**Finns det ett säkert sätt att öppna webblänkar från hanterade appar?** Ja! IT-administratören kan distribuera och ange appskyddsprincip för [Intune Managed Browser-appen](manage-internet-access-using-managed-browser-policies.md), en webbläsare som har utvecklats av Microsoft Intune som enkelt kan hanteras med Intune. IT-administratören kan kräva att alla webblänkar i Intune-upplysta appar ska öppnas med Managed Browser-appen.


## <a name="app-experience-on-android"></a>App-upplevelse på Android

**Varför behövs företagsportalappen för att Intunes appskydd ska fungera på Android-enheter?** Mycket av appskyddsfunktionaliteten är inbyggd i företagsportalappen. Enhetsregistrering _krävs inte_, även om företagsportalappen alltid krävs. För MAM-WE behöver slutanvändaren bara ha företagsportalappen installerad på enheten.

## <a name="app-experience-on-ios"></a>App-upplevelse på iOS

**Jag kan använda iOS resurstillägg för att öppna arbets- eller skoldata i ohanterade appar, även om dataöverföringsprincipen är inställd på "endast hanterade appar" eller "inga appar." Kan inte detta läcka data?** Intunes appskyddsprincip kan inte styra iOS resurstillägg utan att hantera enheten. Därför krypterar Intune _ **"företagets" data innan den delas utanför appen**_. Du kan verifiera detta genom att försöka öppna en "företags"-fil utanför den hanterade appen. Filen ska vara krypterad och inte kunna öppnas utanför den hanterade appen.

### <a name="see-also"></a>Se även
- [Inställningar för hanteringsprincip för Android-mobilappar i Microsoft Intune](android-mam-policy-settings.md)
- [Inställningar för hanteringsprincip för iOS-mobilappar](ios-mam-policy-settings.md)
- [Verifiera din konfiguration för hantering av mobilprogram](validate-mobile-application-management.md)
- [Förbered dig på att konfigurera hanteringsprinciper för mobila appar med Microsoft Intune](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
- [Så kan du få support för Microsoft Intune](../troubleshoot/how-to-get-support-for-microsoft-intune.md)



<!--HONumber=Jan17_HO4-->


