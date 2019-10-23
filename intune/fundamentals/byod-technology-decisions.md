---
title: Teknikval för BYOD med EMS
description: Viktiga teknikval för att kunna tillämpa BYOD och skydda företagsdata med Microsoft Enterprise Mobility + Security.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/8/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 297926f6-c029-4003-bda4-9ee031d47dda
ms.reviewer: pfetty
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c1666c55455a630b839f1f007fc93e5a3da20832
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509108"
---
# <a name="technology-decisions-for-enabling-byod-with-microsoft-enterprise-mobility--security-ems"></a>Teknikval för att kunna tillämpa BYOD med Microsoft Enterprise Mobility + Security (EMS)

När du utvecklar en strategi för att låta anställda arbeta externt med egna enheter (BYOD) måste du fatta några viktiga beslut om hur du ska tillämpa BYOD och skydda företagets data. Som tur är har EMS alla funktioner du behöver i en omfattande uppsättning lösningar.  

I det här avsnittet går vi igenom ett enkelt exempel med hur du ger BYOD-åtkomst till företagets e-post. Vi fokuserar på om du behöver hantera hela enheten eller bara programmen. Båda alternativen är giltiga val.

## <a name="assumptions"></a>Antaganden
* Du har grundläggande kunskaper om Azure Active Directory och Microsoft Intune
* Dina e-postkonton finns i Exchange Online

## <a name="common-reasons-to-manage-the-device-mdm"></a>Vanliga anledningar till att hantera enheten (MDM)
Du kan enkelt få användarna att registrera sina enheter i enhetshanteringen genom att distribuera en princip för [villkorlig åtkomst](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) i Exchange Online. Anledningar till varför du kanske vill hantera personliga enheter:

**WiFi/VPN** – Om användarna behöver en företagsanslutningsprofil för att arbeta effektivt är det enkelt att konfigurera detta.

**Program** – Om användarna behöver få en uppsättning appar överförda till deras enhet är det enkelt att leverera dessa. Detta innefattar program som du kanske behöver av säkerhetsskäl, till exempel en app som skyddar mot mobilhot.

**Efterlevnad** – En del organisationer måste följa organisationsprinciper eller andra principer som kräver specifika MDM-kontroller. Du behöver till exempel MDM för att kryptera hela enheten eller skapa en rapport över alla appar på enheten.

## <a name="common-reasons-to-only-manage-the-apps-mam"></a>Vanliga anledningar till att endast hantera appar (MAM)
MAM utan MDM är populärt för organisationer som använder BYOD. Du kan få användarna att komma åt sin e-post via Outlook Mobile (som stöder MAM-skydd) genom att distribuera en princip för villkorlig åtkomst i Exchange Online. Anledningar till att du kanske bara vill hantera appar på personliga enheter:

**Användarupplevelsen** – Vid en MDM-registrering visas många dialogrutor med varningar (från plattformen). Det leder ofta till att användaren till slut väljer att inte använda e-posten på sin personliga enhet. MAM väcker inte lika mycket oro hos användarna. Ett popup-fönster visas en gång för att ange att MAM-skydd tillämpas.

**Efterlevnad** – Vissa organisationer måste följa policyer som kräver mindre hanteringsfunktioner på personliga enheter. Med MAM kan du till exempel bara ta bort företagsdata från appar, men med MDM kan du ta bort alla data från enheten.

![Bild på en jämförelse av enhets- och apphantering på mobila enheter](./media/byod-technology-decisions/byod-app-device-mgmt.png)

Läs mer om [livscyklerna för enhetshantering och apphantering](device-lifecycle.md).

## <a name="mdm-vs-mam-capability-comparison"></a>Jämförelse av funktioner för MDM respektive MAM
Som redan nämnts kan du med hjälp av villkorlig åtkomst få en användare att registrera sin enhet eller använda en hanterad app som Outlook Mobile. I båda fallen finns flera andra villkor som kan kontrolleras, till exempel:

* Vilken användare som försöker få åtkomst
* Om platsen är betrodd eller inte
* Risknivån för inloggning
* Enhetsplattform

Ändå har många organisationer ofta specifika risker de är oroliga för.  I tabellen nedan visas de vanligaste säkerhetsproblemen och hur MDM respektive MAM hanterar dem.

| Säkerhetsproblem   |   MDM  |   MAM  |
|------------|--------|--------|
|Obehörig åtkomst till data | Krav på gruppmedlemskap | Krav på gruppmedlemskap |
|Obehörig åtkomst till data | Krav på enhetsregistrering | Krav på skyddad app |
|Obehörig åtkomst till data | Krav på specifik plats | Krav på specifik plats |
| | | |
|Komprometterat användarkonto| Krav på MFA | Krav på MFA|
|Komprometterat användarkonto | Blockera högriskanvändare | Blockera högriskanvändare |
|Komprometterat användarkonto | PIN-kod för enhet | PIN-kod för app |
| | | |
| Komprometterad enhet eller app | Krav på kompatibel enhet | Upplåsningskontroll (jailbreak) när appen startar |
| Komprometterad enhet eller app | Kryptera enhetsdata | Kryptera appdata |
| | | |
|Borttappad eller stulen enhet | Ta bort alla enhetsdata | Ta bort alla appdata|
| | | |
| Dela data eller spara data till osäkra platser av misstag | Begränsa säkerhetskopiering av enhetsdata | Begränsa klipp ut/kopiera/klistra in|
| Dela data eller spara data till osäkra platser av misstag | Begränsa spara som | Begränsa spara som |
|Dela data eller spara data till osäkra platser av misstag | Inaktivera utskrift | saknas|

## <a name="next-steps"></a>Nästa steg
Nu är det dags att bestämma om du vill använda BYOD i din organisation med fokus på enhetshantering, apphantering eller en kombination av dessa. Valet är ditt, men du kan känna dig trygg med att funktionerna för identitet och säkerhet i Azure AD är tillgängliga oavsett vad du väljer.  

Använd Intunes [planeringsguide](planning-guide.md) för att planera nästa steg.
