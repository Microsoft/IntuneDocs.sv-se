---
title: Ställ in åtkomst till ditt företags resurser | Microsoft Docs
description: Beskriver hur du hämtar en iOS-enhet som hanteras av Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
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
ms.openlocfilehash: 51492c1a8d7e32ab7dbdd5d896e7726c877d62d5
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43149591"
---
# <a name="set-up-access-to-your-company-resources"></a>Ställ in åtkomst till ditt företags resurser

Registrera din iOS-enhet i Intune-företagsportalappen för att få säker åtkomst till organisationens e-post, filer och appar.

Organisationer kräver ofta att din enhet blir hanterad innan du kan komma åt egna data från den. När en enhet blir hanterad kan organisationer skicka principer och appar till enheten via sin leverantör av hantering av mobilenheter. 

För att få kontinuerlig tillgång till arbets- eller skolinformation från enheten måste du konfigurera den så att principinställningarna matchar. Den här artikeln beskriver hur Intune-företagsportalappen för iOS hjälper dig att registrera, konfigurera och underhålla enheten så att den uppfyller organisationens krav.

> [!NOTE]
> Om du försöker komma åt företagets e-post i e-postprogrammet är det troligt att du har uppmanats att hantera din enhet för att skydda den. Följ anvisningarna nedan för att få åtkomst till din e-post och andra företagsresurser på iOS-enheten.

## <a name="what-to-expect-from-the-company-portal-app"></a>Vad du kan förvänta dig av företagsportalappen

### <a name="security"></a>Säkerhet
Under installationen kräver appen att du autentiserar dig själv hos organisationen. Den informerar dig sedan om eventuella enhetsinställningar du måste göra. Organisationer anger exempelvis ofta krav på lägsta eller högsta antal tecken i lösenordet som du måste uppfylla.    

### <a name="protection"></a>Skydd
När enheten har registrerats fortsätter företagsportalappen att se till att enheten är skyddad. Om du till exempel installerar en app från en ej betrodd källa kommer appen meddela dig och återkallar ibland åtkomst till företagets data. Appskyddsprinciper som den här är vanliga i organisationer och kräver ofta att du avinstallerar ej betrodda appar innan du kan få åtkomst.

### <a name="setting-notifications"></a>Konfigurera meddelanden
Om organisationen inför ett nytt säkerhetskrav efter registreringen, t.ex. multifaktorautentisering, meddelar företagsportalappen dig. Du får möjlighet att justera dina inställningar så att du kan fortsätta arbeta från enheten.  

Mer information om registrering finns i [Vad händer när jag installerar företagsportalappen och registrerar min enhet?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md). 

## <a name="before-you-start"></a>Innan du börjar

- Var noga med att slutföra hela processen när du har startat. Om du pausar under mer än ett par minuter kan installationsprogrammet avslutas och du måste börja om från början.  
    - Om processen skulle misslyckas återgår du till företagsportalappen och försöker igen.  
- Kontrollera att ditt Wi-Fi fungerar och att Safari fungerar på din enhet.
- Ladda ner och installera [Intune-företagsportalappen](install-and-sign-in-to-the-intune-company-portal-app-ios.md).


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>Använd företagsportalappen för att konfigurera åtkomst till företagsresurser

|Det här ser du|Förklaring|
|---|---|
|![Inloggningsskärmen för företagsportalen, med inloggningsknappen längst ned.](./media/ios-01-cp-enroll-1802.png)|Öppna företagsportalappen och tryck på **Logga in**.|
|![Azure AD-inloggningsprompt.](./media/ios-02-cp-enroll-1802.png)|Ange din företags-e-post och tryck på **nästa**.|
|![Azure AD-lösenordsprompt.](./media/ios-03-cp-enroll-1802.png)|Ange ditt lösenord och tryck på **logga in**.|
|![Läser in välkomstskärmen för företagets resurser.](./media/ios-04-cp-enroll-1802.png)|Vänta tills den här skärmen har lästs in.|
|![Sidan Allmänna villkor.](./media/ios-05-cp-enroll-1802.png)|Läs och **godkänn alla** villkor.|
|![Skärmen för konfiguration av företagsåtkomst. Både hantering och inställningar behöver lösas.](./media/ios-06-cp-enroll-1802.png)|Tryck på **Börja** för att påbörja processen med att ge enheten åtkomst till företagsresurser. Om du inte kan göra det just nu, kan du **skjuta upp** processen, men det innebär att du inte längre kommer åt e-post, dokument och mer.|
|![Skärmen vad kan mitt företag se.](./media/ios-07-cp-enroll-1802.png)|Du kan **läsa mer** om vad ditt företag kan se genom att trycka på länken längst ned. Annars trycker du på **fortsätt**.|
|![Skärmen vad händer nu.](./media/ios-08-cp-enroll-1802.png)|På den här skärmen får du veta vad som händer i installationen. Du kommer att använda dig av Safari, inställningsappen och företagsportalappen för att slutföra den här processen. Tryck på **Fortsätt**.|
|![Laddningsskärmen efter att du trycker nästa på vad händer nu.](./media/ios-09-cp-enroll-1802.png)|Vänta tills den här skärmen har lästs in.|
|![Växlade till Safari för registrering.](./media/ios-7-cp-enroll-1711.png)|Du skickas till Safari att hämta hanteringsinformation för din enhet.|
|![Systemprompt som ber att inställningsappen öppnas.](./media/ios-8-cp-enroll-1711.png)|Tryck på **tillåt** för att öppna inställningsappen och ladda ner konfigurationsprofilen. Du installerar den här för att låta ditt företag hantera företagsinformation på din enhet.|
|![Profilen öppnar enhetsinställningar.](./media/ios-9-cp-enroll-1711.png)|Tryck på **Installera**.|
|![Den modala dialogrutan installerar profilen längst ned på skärmen.](./media/ios-10-cp-enroll-1711.png)|Tryck på **Installera**.|
|![Laddningsskärmen profilen installeras.](./media/ios-11-cp-enroll-1711.png)|Vänta tills den här skärmen har lästs in.|
|![Skärmen profilhanteringsvarning.](./media/ios-12-cp-enroll-1711.png)|Den här varningen, skriven av Apple, ger dig mer information om vilka typer av åtgärder som kan utföras på en hanterad enhet. Läs mer om [vilken information som ditt företag kan se](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).|
|![Systemprompt som frågar om förtroende för fjärrhantering.](./media/ios-13-cp-enroll-1711.png)|Tryck på **lita på** för att låta ditt företag hantera företagsinformation och inställningar på din enhet.|
|![Laddningsskärmen profilen färdigställs.](./media/ios-14-cp-enroll-1711.png)|Vänta tills den här skärmen har lästs in.|
|![Skärmen profilen installerad.](./media/ios-15-cp-enroll-1711.png)|Din profil är installerad och din enhets företagsinformation och inställningar är mycket närmare att vara hanterade.|
|![Växlade till Safari för registrering.](./media/ios-16-cp-enroll-1711.png)|Du skickas tillbaka till Safari för att hämta hanteringsinformation för din enhet. |
|![Systemprompt om att öppna företagsportalen.](./media/ios-17-cp-enroll-1711.png)|Tryck på **Öppna**.|
|![Skärmen läser in företagsresurser.](./media/ios-21-cp-enroll-1802.png)|Vänta tills den här skärmen har lästs in.|
|![Välj enhetskategori i företagsportalappen.](./media/ios-22-cp-enroll-1802.png)|Välj den bästa kategorin för din enhet. Vanligtvis handlar det om vem som äger enheten eller var den befinner sig.|
|![Vald kategori.](./media/ios-23-cp-enroll-1802.png)||
|![Enhetshanteringen lyckades. Nu måste inställningarna uppdateras.](./media/ios-24-cp-enroll-1802.png)|Du har lyckats få din enhet hanterad. Det finns troligen fortfarande inställningar, som lösenordslängden, som ditt företag kan vilja att du uppdaterar. Tryck på **Fortsätt** för att fortsätta.|
|![Bekräftar enhetsinställningarna.](./media/ios-25-cp-enroll-1802.png)|Företagsportalen kontrollerar om någon av dina inställningar behöver uppdateras.|
|![Inställningskontrollen slutförd med en felaktig OS-version](./media/ios-26-cp-enroll-1802.png)|Företagsportalen ger dig instruktioner för hur du kan lösa eventuella problem med dina inställningar. När du har löst problemen, trycker du på **kontrollera inställningar**.|
|![Laddningsskärmen bekräftar enhetsinställningarna](./media/ios-27-cp-enroll-1802.png)|Din enhet kontrollerar om dina inställningar är säkra nog för åtkomst till företagets resurser.|
|![Registrerade och uppdaterade inställningarna](./media/ios-28-cp-enroll-1802.png)|Gratulerar! Enheten har nu registrerats i Intune.|

> [!Note]
> Du kan behöva utföra några steg till innan enheten är fullständigt hanterad. Lär dig mer om [hur du registrerar enheten med kostnadsuppföljning av telekommunikation](enroll-your-device-with-telecom-expense-management-ios.md). Om din organisation använder Apples enhetsregistreringsprogram (DEP) kan du läsa mer [här](enroll-your-device-dep-ios.md).

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).
