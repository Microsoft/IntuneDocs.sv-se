---
title: Konfigurera iOS-enhetsåtkomst till företagsresurser | Microsoft Docs
description: Beskriver hur du hämtar en iOS-enhet som hanteras av Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 50fc19410b280e984c8dc3abe620baad7c3267de
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959544"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Konfigurera iOS-enhetsåtkomst till företagsresurser

Registrera din iOS-enhet i Intune-företagsportalappen för att få säker åtkomst till organisationens e-post, filer och appar.

Innan du kan komma åt upphovsrättsskyddade data från en företagsenhet eller personlig enhet måste enheten vara hanterad. När enheten är hanterad tilldelar din organisation principer och appar till enheten via en MDM-provider för hantering av mobilenheter. 

För att kunna komma åt arbets- eller skolinformation från din enhet måste du konfigurera enheten så att den matchar organisationens önskade inställningar. Den här artikeln beskriver hur företagsportalen hjälper dig att registrera, konfigurera och underhålla din enhet så att den uppfyller dessa krav.

> [!NOTE]
> Om du försökte komma åt företagets e-post i e-postprogrammet och du fick ett meddelande om att enheten måste vara hanterad, är du på rätt plats. Följ anvisningarna nedan för att få åtkomst till din e-post och andra företagsresurser på iOS-enheten.

## <a name="what-to-expect-from-the-company-portal-app"></a>Vad du kan förvänta dig av företagsportalappen

### <a name="security"></a>Säkerhet
Under installationen kräver appen att du autentiserar dig själv hos organisationen. Du informeras sedan om eventuella enhetsinställningar som du behöver uppdatera. Organisationer anger exempelvis ofta krav på lägsta eller högsta antal tecken i lösenordet som du måste uppfylla.    

### <a name="protection"></a>Skydd
När enheten har registrerats fortsätter företagsportalappen att se till att enheten är skyddad. Om du till exempel installerar en app från en ej betrodd källa kommer appen meddela dig och återkallar ibland åtkomst till företagets data. Appskyddsprinciper som den här är vanliga i organisationer. De kräver ofta att du avinstallerar den obetrodda appen innan du kan få åtkomst igen.

### <a name="setting-notifications"></a>Konfigurera meddelanden
Om organisationen inför ett nytt säkerhetskrav efter registreringen, t.ex. multifaktorautentisering, meddelar företagsportalappen dig. Du får möjlighet att justera dina inställningar så att du kan fortsätta arbeta från enheten.  

Mer information om registrering finns i [Vad händer när jag installerar företagsportalappen och registrerar min enhet?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios). 

## <a name="before-you-start"></a>Innan du börjar

- När du väl påbörjar registreringen är det viktigt att du slutför hela processen. Om du pausar under mer än ett par minuter kan installationsprogrammet avslutas och du måste börja om från början.  
- Om processen skulle misslyckas återgår du till företagsportalappen och försöker igen.  
- Kontrollera att ditt Wi-Fi fungerar och att Safari fungerar på din enhet.
- Ladda ner och installera [Intune-företagsportalappen](install-and-sign-in-to-the-intune-company-portal-app-ios.md).  


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>Använd företagsportalappen för att konfigurera åtkomst till företagsresurser

|Det här ser du|Förklaring|
|---|---|
|![Inloggningsskärmen för företagsportalen, med inloggningsknappen längst ned.](./media/ios-01-cp-enroll-1802.PNG)|Öppna företagsportalappen och tryck på **Logga in**.|
|![Azure AD-inloggningsprompt.](./media/ios-02-cp-enroll-1802.PNG)|Ange din företags-e-post och tryck på **nästa**.|
|![Azure AD-lösenordsprompt.](./media/ios-03-cp-enroll-1802.PNG)|Ange ditt lösenord och tryck på **logga in**.|
|![Läser in välkomstskärmen för företagets resurser.](./media/ios-04-cp-enroll-1802.PNG)|Vänta tills den här skärmen har lästs in.|
|![Sidan Allmänna villkor.](./media/ios-05-cp-enroll-1802.PNG)|Läs och **godkänn alla** villkor.|
|![Skärmen för konfiguration av företagsåtkomst. Både hantering och inställningar behöver lösas.](./media/ios-06-cp-enroll-1802.PNG)|Tryck på **Börja** för att påbörja processen med att ge enheten åtkomst till företagsresurser. Om du inte kan göra det just nu, kan du **skjuta upp** processen, men det innebär att du inte längre kommer åt e-post, dokument och mer.|
|![Skärmen vad kan mitt företag se.](./media/ios-07-cp-enroll-1802.PNG)|Du kan **läsa mer** om vad ditt företag kan se genom att trycka på länken längst ned. Annars trycker du på **fortsätt**.|
|![Skärmen vad händer nu.](./media/ios-08-cp-enroll-1802.PNG)|På den här skärmen får du veta vad som händer i installationen. Du kommer att använda Safari, inställningsappen och företagsportalappen. Tryck på **Fortsätt**.|
|![Laddningsskärmen efter att du trycker nästa på vad händer nu.](./media/ios-09-cp-enroll-1802.PNG)|Vänta tills den här skärmen har lästs in.|
|![Växlade till Safari för registrering.](./media/ios-cp-sent-to-safari-1808.png)|Du skickas till Safari att hämta hanteringsinformation för din enhet.|
|![Systemprompt som ber att inställningsappen öppnas.](./media/ios-8-cp-enroll-1711.PNG)|Tryck på **tillåt** för att öppna inställningsappen och ladda ner konfigurationsprofilen. Du installerar den här för att låta ditt företag hantera företagsinformation på din enhet.|
|![Skärmbild av skärmen Installera profil i enhetsinställningarna.](./media/ios-9-cp-enroll-1711.PNG)|Tryck på **Installera**.|
|![Den modala dialogrutan installerar profilen längst ned på skärmen.](./media/ios-10-cp-enroll-1711.PNG)|Tryck på **Installera**.|
|![Laddningsskärmen profilen installeras.](./media/ios-11-cp-enroll-1711.PNG)|Vänta tills den här skärmen har lästs in.|
|![Skärmen profilhanteringsvarning.](./media/ios-12-cp-enroll-1711.PNG)|Den här varningen, skriven av Apple, ger dig mer information om vilka typer av åtgärder som kan utföras på en hanterad enhet. Läs mer om [vilken information som ditt företag kan se](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).|
|![Systemprompt som frågar om förtroende för fjärrhantering.](./media/ios-13-cp-enroll-1711.PNG)|Tryck på **lita på** för att låta ditt företag hantera företagsinformation och inställningar på din enhet.|
|![Laddningsskärmen profilen färdigställs.](./media/ios-14-cp-enroll-1711.PNG)|Vänta tills den här skärmen har lästs in.|
|![Skärmen profilen installerad.](./media/ios-15-cp-enroll-1711.PNG)|Din profil är installerad och din enhets företagsinformation och inställningar är mycket närmare att vara hanterade.|
|![Växlade till Safari för registrering.](./media/ios-16-cp-enroll-1711.PNG)|Du skickas tillbaka till Safari för att hämta hanteringsinformation för din enhet. |
|![Systemprompt om att öppna företagsportalen.](./media/ios-17-cp-enroll-1711.PNG)|Tryck på **Öppna**.|
|![Skärmen läser in företagsresurser.](./media/ios-21-cp-enroll-1802.PNG)|Vänta tills den här skärmen har lästs in.|
|![Välj enhetskategori i företagsportalappen.](./media/ios-22-cp-enroll-1802.PNG)|Välj den bästa kategorin för din enhet. Vanligtvis handlar det om vem som äger enheten eller var den befinner sig.|
|![Vald kategori.](./media/ios-23-cp-enroll-1802.PNG)||
|![Enhetshanteringen lyckades. Nu måste inställningarna uppdateras.](./media/ios-24-cp-enroll-1802.PNG)|Du har lyckats få din enhet hanterad. Det finns troligen fortfarande inställningar, som lösenordslängden, som ditt företag kan vilja att du uppdaterar. Tryck på **Fortsätt** för att fortsätta.|
|![Bekräftar enhetsinställningarna.](./media/ios-25-cp-enroll-1802.PNG)|Företagsportalen kontrollerar om någon av dina inställningar behöver uppdateras.|
|![Inställningskontrollen slutförd med en felaktig OS-version](./media/ios-26-cp-enroll-1802.PNG)|Företagsportalen ger dig instruktioner för hur du kan lösa eventuella problem med dina inställningar. När du har löst problemen, trycker du på **kontrollera inställningar**.|
|![Laddningsskärmen bekräftar enhetsinställningarna](./media/ios-27-cp-enroll-1802.PNG)|Din enhet kontrollerar om dina inställningar är säkra nog för åtkomst till företagets resurser.|
|![Registrerade och uppdaterade inställningarna](./media/ios-28-cp-enroll-1802.PNG)|Gratulerar! Enheten har nu registrerats i Intune.|

> [!Note]
> Du kan behöva utföra några steg till innan enheten är fullständigt hanterad. Lär dig mer om [hur du registrerar enheten med kostnadsuppföljning av telekommunikation](enroll-your-device-with-telecom-expense-management-ios.md). Om din organisation använder Apples enhetsregistreringsprogram (DEP) kan du läsa mer [här](enroll-your-device-dep-ios.md).

Behöver du fortfarande hjälp? Kontakta företagets support. Du hittar kontaktinformationen på [Företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  
