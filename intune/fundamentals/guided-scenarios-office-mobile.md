---
title: Guidat scenario – Skydda Microsoft Office-mobilappar
titleSuffix: Microsoft Intune
description: Lär dig mer om det guidade scenariot för att distribuera säkra Microsoft Office-mobilappar från Microsoft 365-enhetshanteringsportalen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd02e2b7f9582308109d1e6986d7e6a8014e5af7
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585715"
---
# <a name="guided-scenario---secure-microsoft-office-mobile-apps"></a>Guidat scenario – Skydda Microsoft Office-mobilappar 

Genom att följa det här guidade scenariot i enhetshanteringsportalen kan du aktivera grundläggande Intune-appskydd på iOS-enheter och Android-enheter.

Det appskydd som du aktiverar kommer att framtvinga följande åtgärder: 
- Kryptera arbetsfiler.
- Kräv en PIN-kod för åtkomst till arbetsfiler.
- Kräv att PIN-koden återställs efter fem misslyckade försök.
- Blockera arbetsfiler från att säkerhetskopieras i säkerhetskopieringstjänster för iTunes, iCloud eller Android.  
- Kräv att arbetsfiler endast sparas på OneDrive eller i SharePoint.
- Förhindra att skyddade appar läser in arbetsfiler på jailbrokade eller rotade enheter.
- Blockera åtkomst till arbetsfiler om enheten är offline i 720 minuter.
- Ta bort arbetsfiler om enheten är offline i 90 dagar. 

## <a name="background"></a>Bakgrund

Office-mobilappar och Microsoft Edge för mobila enheter har stöd för dubbla identiteter. Med dubbla identiteter kan appar hantera arbetsfiler separat från personliga filer. 

![Bild av företagsdata jämfört med personliga data](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-01.png)

[Intune-appskyddsprinciper](~/apps/app-protection-policy.md) hjälper dig att skydda arbetsfiler på enheter som är registrerade i Intune. Du kan även använda appskyddsprinciper på medarbetarnas enheter som inte har registrerats för hantering i Intune. Även om ditt företag inte hanterar enheten i det här fallet måste du fortfarande se till att arbetsfiler och resurser är skyddade.

Du kan använda appskyddsprinciper för att förhindra att användare sparar arbetsfiler på oskyddade platser. Du kan även begränsa dataflytten till andra appar som inte skyddas av appskyddsprinciper. Principinställningar för appskydd inkluderar:
- Dataflyttningsprinciper såsom Förhindra Spara som och Begränsa klipp ut, kopiera och klistra in.
- Åtkomstprincipsinställningar för att kräva enkel PIN för åtkomst och blockera hanterade appar från att köras på jailbrokade eller rotade enheter.

Appbaserad, villkorsstyrd åtkomst och klientapphantering lägger till ett säkerhetslager genom att se till att enbart klientappar som stöder Intunes appskyddsprinciper kommer åt Exchange Online och andra Office 365-tjänster.

Du kan blockera inbyggda e-postappar i iOS och Android genom att bara tillåta att Microsoft Outlook-appen får åtkomst till Exchange Online. Dessutom kan du blockera appar där Intunes appskyddsprinciper inte har tillämpats för åtkomst till SharePoint Online.

I det här exemplet har administratören tillämpat appskyddsprinciper på Outlook-appen, följt av en regel för villkorlig åtkomst som lägger till Outlook-appen i en lista med godkända appar som kan användas för att få åtkomst till företagets e-post.

![Processflöde för villkorsstyrd åtkomst för Outlook-appar](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-02.png)

## <a name="prerequisites"></a>Krav

Du behöver följande Intune-administratörsbehörigheter:

   - Behörighet att läsa, skapa, ta bort och tilldela för hanterade appar
   - Behörighet att läsa, skapa och tilldela för principuppsättningar
   - Behörighet att läsa för organisationen

## <a name="step-1---introduction"></a>Steg 1 – Introduktion

Genom att följa det guidade scenariot för **Intune-appskydd** förhindrar du att data delas eller avslöjas utanför organisationen. 

Tilldelade iOS- och Android-användare måste ange en PIN-kod varje gång de öppnar en Office-app. Efter 5 misslyckade PIN-försök måste användarna återställa PIN-koden. Om du redan kräver en PIN-kod för enheten påverkas inte användarna.

### <a name="what-you-will-need-to-continue"></a>Det här behöver du för att fortsätta

Vi frågar dig angående de appar som dina användare behöver samt vad som behövs för åtkomst till apparna. Kontrollera att du har följande information till hands:
- Lista över Office-appar som har godkänts för företagsanvändning.
- Eventuella PIN-krav för start av godkända appar på icke-hanterade enheter.

## <a name="step-2---basics"></a>Steg 2 – Grunderna

I det här steget måste du ange ett **Prefix** och en **Beskrivning** för din nya appskyddsprincip. När du lägger **prefixet** uppdateras den information som rör de resurser som det guidade scenariot skapar. Med den här informationen blir det enkelt att hitta dina principer senare om du behöver ändra tilldelningarna och konfigurationen. 

> [!TIP]
> Överväg att göra en anteckning om de resurser som ska skapas, så att du kan referera till dem senare.

## <a name="step-3---apps"></a>Steg 3 – Appar

För att hjälpa dig att komma igång väljer det här guidade scenariot följande mobilappar att skydda på iOS- och Android-enheter:
- Microsoft Excel 
- Microsoft Word 
- Microsoft Teams 
- Microsoft Edge 
- Microsoft PowerPoint 
- Microsoft Outlook 
- Microsoft OneDrive 

Det här guidade scenariot konfigurerar även dessa appar att öppna webblänkar i Microsoft Edge för att garantera att arbetswebbplatser öppnas i en skyddad webbläsare.

Ändra listan över principhanterade appar som du vill skydda. Lägg till eller ta bort appar från den här listan. 

När du har valt apparna klickar du på **Nästa**.

## <a name="step-4---configuration"></a>Steg 4 – Konfiguration

I det här steget måste du konfigurera kraven för åtkomst till och delning av företagsfiler och e-postmeddelanden i dessa appar. Som standard kan användare spara data till organisationens OneDrive- och SharePoint-konton.

| Inställningen | Beskrivning | Standardvärde |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| Typ av PIN-kod | Numeriska PIN-koder består uteslutande av siffror. Lösenord består av alfanumeriska tecken och specialtecken.  För att konfigurera ”lösenordstypen” i iOS/iPadOS måste appen ha Intune SDK version 7.1.12 eller senare. Numerisk typ har ingen begränsning för Intune-SDK-version. | Numeriskt |
| Välja minimilängd för PIN-kod | Ange det minsta antalet siffror i en PIN-kodsekvens. | 6 |
| Kontrollera åtkomstbehörigheterna på nytt efter (minuters inaktivitet) | Om den principhanterade appen är inaktiv längre än antalet minuters inaktivitet uppmanar appen att åtkomstkrav (det vill säga PIN-kod, inställningar för villkorsstyrd start) ska kontrolleras igen efter att appen har startats. | 30 |
| Utskrift av organisationsdata | Om detta blockeras kan appen inte skriva ut skyddade data. | Blockera |
| Öppna länkar för principhanterade appar i ohanterade webbläsare | Om detta blockeras måste länkar för principbaserade appar öppnas i en hanterad webbläsare. | Blockera |
| Kopiera data till ohanterade appar | Om detta blockeras behålls hanterade data i hanterade appar. | Tillåt |

## <a name="step-5---assignments"></a>Steg 5 – Tilldelningar

I det här steget kan du välja de användargrupper som du vill inkludera för att säkerställa att de har åtkomst till dina företagsdata. Appskydd tilldelas till användare, inte enheter, så dina företagsdata är säkra oavsett vilken enhet som används och dess registreringsstatus.

Användare utan appskyddsprinciper och inställningar för villkorsstyrd åtkomst kommer att kunna spara data från sin företagsprofil till personliga appar och ohanterad lokal lagring på sina mobila enheter. De kan även ansluta till företagsdatatjänster, till exempel Microsoft Exchange, med personliga appar.

## <a name="step-6---review--create"></a>Steg 6 – Granska och skapa

I det sista steget kan du granska en sammanfattning av de inställningar som du har konfigurerat. När du har granskat dina val klickar du på **Skapa** för att slutföra det guidade scenariot. När det guidade scenariot är klart visas en tabell med resurser. Du kan redigera dessa resurser senare, men när du lämnar sammanfattningsvyn sparas inte tabellen.

> [!IMPORTANT]
> När det guidade scenariot är klart visas en sammanfattning. Du kan ändra de resurser som visas i sammanfattningen senare, men den tabell som visar dessa resurser kommer inte att sparas.
## <a name="next-steps"></a>Nästa steg

- Förbättra säkerheten för arbetsfiler genom att tilldela användare en appbaserad princip för villkorsstyrd åtkomst för att skydda molntjänster från att skicka arbetsfiler till oskyddade appar. Mer information finns i [Konfigurera appbaserade principer för villkorsstyrd åtkomst med Intune](~/protect/app-based-conditional-access-intune-create.md).

