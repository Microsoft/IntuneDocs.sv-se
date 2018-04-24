---
title: Ställ in åtkomst till ditt företags resurser | Microsoft Docs
description: Beskriver hur du hämtar en iOS-enhet som hanteras av Intune
keywords: ''
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 6474688a09c4063c55eff07f3cf84ebcb1911c65
ms.sourcegitcommit: c29241a88e67137f0fbc678b9eae1db2b2cded14
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/03/2018
---
# <a name="set-up-access-to-your-company-resources"></a>Ställ in åtkomst till ditt företags resurser

Ditt företag har mycket upphovsrättsskyddad information, från e-post till filer, nätverk och mer. Ditt företag använder Microsoft Intune för att skydda den informationen när du har åtkomst till den från din iOS-enhet. Det gör att de kan hantera de resurserna, göra dem säkrare och ge dig friheten att använda den enhet du vill för att få jobbet gjort.

> [!NOTE]
> Om du försöker komma åt företagets e-post i e-postprogrammet är det troligt att du har uppmanats att hantera din enhet för att skydda den. Följ anvisningarna nedan för att få åtkomst till din e-post och andra företagsresurser på iOS-enheten.

## <a name="before-you-start"></a>Innan du börjar

- Var noga med att slutföra hela processen när du har startat. Om du pausar i mer än ett par minuter, stoppas vanligtvis processen och du måste starta om.
- Om processen skulle misslyckas, måste du återgå till företagsportalappen och försöka igen.
- Kontrollera att ditt Wi-Fi fungerar och att Safari fungerar på din enhet.
- Ladda ner och installera [Intune-företagsportalappen](install-and-sign-in-to-the-intune-company-portal-app-ios.md).


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>Använd företagsportalappen för att konfigurera åtkomst till företagsresurser

|Det här ser du|Förklaring|
|---|---|
|![Inloggningsskärmen för företagsportalen, med logga in-knappen längst ned.](./media/ios-01-cp-enroll-1802.png)|Öppna företagsportalappen och tryck på **logga in**.|
|![Azure AD-inloggningsprompten.](./media/ios-02-cp-enroll-1802.png)|Ange din företags-e-post och tryck på **nästa**.|
|![Azure AD-lösenordsprompt.](./media/ios-03-cp-enroll-1802.png)|Ange ditt lösenord och tryck på **logga in**.|
|![Läser in välkomstskärmen för företagets resurser.](./media/ios-04-cp-enroll-1802.png)|Vänta tills det har laddats.|
|![Sidan Allmänna villkor.](./media/ios-05-cp-enroll-1802.png)|Läs och **godkänn alla** villkor.|
|![Skärmen för konfiguration av företagsåtkomst. Både hantering och inställningar behöver lösas.](./media/ios-06-cp-enroll-1802.png)|Tryck på **Börja** för att påbörja processen med att ge enheten åtkomst till företagsresurser. Om du inte kan göra det just nu, kan du **skjuta upp** processen, men det innebär att du inte längre kommer åt e-post, dokument och mer.|
|![Skärmen vad kan mitt företag se.](./media/ios-07-cp-enroll-1802.png)|Du kan **läsa mer** om vad ditt företag kan se genom att trycka på länken längst ned. Annars trycker du på **fortsätt**.|
|![Skärmen vad händer nu.](./media/ios-08-cp-enroll-1802.png)|På den här skärmen får du veta vad som händer i installationen. Du kommer att använda dig av Safari, inställningsappen och företagsportalappen för att slutföra den här processen. Tryck på **Fortsätt**.|
|![Laddningsskärmen efter att du trycker nästa på vad händer nu.](./media/ios-09-cp-enroll-1802.png)|Vänta tills det har laddats.|
|![Växlade till Safari för registrering.](./media/ios-7-cp-enroll-1711.png)|Du skickas till Safari att hämta hanteringsinformation för din enhet.|
|![Systemprompt som ber att inställningsappen öppnas.](./media/ios-8-cp-enroll-1711.png)|Tryck på **tillåt** för att öppna inställningsappen och ladda ner konfigurationsprofilen. Du installerar den här för att låta ditt företag hantera företagsinformation på din enhet.|
|![Profilen är öppen i inställningar.](./media/ios-9-cp-enroll-1711.png)|Tryck på **Installera**.|
|![Den modala dialogrutan installerar profilen längst ned på skärmen.](./media/ios-10-cp-enroll-1711.png)|Tryck på **Installera**.|
|![Laddningsskärmen profilen installeras.](./media/ios-11-cp-enroll-1711.png)|Vänta tills det har laddats.|
|![Skärmen profilhanteringsvarning.](./media/ios-12-cp-enroll-1711.png)|Den här varningen, skriven av Apple, ger dig mer information om vilka typer av åtgärder som kan utföras på en hanterad enhet. Läs mer om [vilken information som ditt företag kan se](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).|
|![Systemprompt som frågar om förtroende för fjärrhantering.](./media/ios-13-cp-enroll-1711.png)|Tryck på **lita på** för att låta ditt företag hantera företagsinformation och inställningar på din enhet.|
|![Laddningsskärmen profilen färdigställs.](./media/ios-14-cp-enroll-1711.png)|Vänta tills det har laddats.|
|![Skärmen profilen installerad.](./media/ios-15-cp-enroll-1711.png)|Din profil är installerad och din enhets företagsinformation och inställningar är mycket närmare att vara hanterade.|
|![Växlade till Safari för registrering.](./media/ios-16-cp-enroll-1711.png)|Du skickas tillbaka till Safari för att hämta hanteringsinformation för din enhet. |
|![Systemprompt om att öppna företagsportalen.](./media/ios-17-cp-enroll-1711.png)|Tryck på **Öppna**.|
|![Skärmen läser in företagsresurser.](./media/ios-21-cp-enroll-1802.png)|Vänta tills det har laddats.|
|![Välj enhetskategori i företagsportalappen.](./media/ios-22-cp-enroll-1802.png)|Välj den bästa kategorin för din enhet. Vanligtvis handlar det om vem som äger enheten eller var den befinner sig.|
|![Vald kategori.](./media/ios-23-cp-enroll-1802.png)||
|![Enhetshanteringen lyckades. Nu måste inställningarna uppdateras.](./media/ios-24-cp-enroll-1802.png)|Du har lyckats få din enhet hanterad. Det finns troligen fortfarande inställningar, som lösenordslängden, som ditt företag kan vilja att du uppdaterar. Tryck på **Fortsätt** för att fortsätta.|
|![Bekräftar enhetsinställningarna.](./media/ios-25-cp-enroll-1802.png)|Företagsportalen kontrollerar om någon av dina inställningar behöver uppdateras.|
|![Inställningskontrollen slutförd med en felaktig OS-version](./media/ios-26-cp-enroll-1802.png)|Företagsportalen ger dig instruktioner för hur du kan lösa eventuella problem med dina inställningar. När du har löst problemen, trycker du på **kontrollera inställningar**.|
|![Laddningsskärmen bekräftar enhetsinställningarna](./media/ios-27-cp-enroll-1802.png)|Din enhet kontrollerar om dina inställningar är säkra nog för åtkomst till företagets resurser.|
|![Registrerade och uppdaterade inställningarna](./media/ios-28-cp-enroll-1802.png)|Gratulerar! Enheten har nu registrerats i Intune.|

> [!Note]
> Du kan behöva utföra några steg till innan enheten är fullständigt hanterad. Lär dig mer om [hur du registrerar enheten med kostnadsuppföljning av telekommunikation](enroll-your-device-with-telecom-expense-management-ios.md). Om din organisation använder Apples enhetsregistreringsprogram (DEP) kan du läsa mer [här](enroll-your-device-dep-ios.md).

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
