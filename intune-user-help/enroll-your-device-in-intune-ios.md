---
title: "Ställ in åtkomst till ditt företags resurser | Microsoft Docs"
description: "Beskriver hur du hämtar en iOS-enhet som hanteras av Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope: User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 7e1ff77fef9e084000938022fb36217b21279c28
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2017
---
# <a name="set-up-access-to-your-company-resources"></a>Ställ in åtkomst till ditt företags resurser

Ditt företag har mycket upphovsrättsskyddad information, från e-post till filer, nätverk och mer. Ditt företag använder Microsoft Intune för att skydda den informationen när du har åtkomst till den från din iOS-enhet. Det gör att de kan hantera de resurserna, göra dem säkrare och ge dig friheten att använda den enhet du vill för att få jobbet gjort.

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment/player]

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
|![Inloggningsskärmen för företagsportalen, med logga in-knappen längst ned.](./media/ios-0-cp-enroll-1711.png)|Öppna företagsportalappen och tryck på **logga in**.|
|![Azure AD-inloggningsprompten.](./media/ios-0a-cp-enroll-1711.png)|Ange din företags-e-post och tryck på **nästa**.|
|![Azure AD-lösenordsprompt.](./media/ios-0b-cp-enroll-1711.png)|Ange ditt lösenord och tryck på **logga in**.|
|![Läser in välkomstskärmen för företagets resurser.](./media/ios-1-cp-enroll-1711.png)|Vänta tills det har laddats.|
|![Villkor.](./media/ios-2-cp-enroll-1711.png)|Läs och **godkänn alla** villkor.|
|![Skärmen för konfiguration av företagsåtkomst. Både hantering och inställningar behöver lösas.](./media/ios-3-cp-enroll-1711.png)|Tryck på **Börja** för att påbörja processen med att ge enheten åtkomst till företagsresurser. Om du inte kan göra det just nu, kan du **skjuta upp** processen, men det innebär att du inte längre kommer åt e-post, dokument och mer.|
|![Skärmen vad kan mitt företag se.](./media/ios-4-cp-enroll-1711.png)|Du kan **läsa mer** om vad ditt företag kan se genom att trycka på länken längst ned. Annars trycker du på **fortsätt**.|
|![Skärmen vad händer nu.](./media/ios-5-cp-enroll-1711.png)|På den här skärmen får du veta vad som händer i installationen. Du kommer att använda dig av Safari, inställningsappen och företagsportalappen för att slutföra den här processen. Tryck på **nästa**.|
|![Laddningsskärmen efter att du trycker nästa på vad händer nu.](./media/ios-6-cp-enroll-1711.png)||
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
|![Skärmen läser in företagsresurser.](./media/ios-18-cp-enroll-1711.png)|Vänta tills det har laddats.|
|![Välj enhetskategori i företagsportalappen.](./media/ios-19-cp-enroll-1711.png)|Välj den bästa kategorin för din enhet. Vanligtvis handlar det om vem som äger enheten eller var den befinner sig.|
|![Vald kategori.](./media/ios-20-cp-enroll-1711.png)||
|![Enhetshanteringen lyckades. Nu måste inställningarna uppdateras.](./media/ios-21-cp-enroll-1711.png)|Du har lyckats få din enhet hanterad. Det finns troligen fortfarande inställningar, som lösenordslängden, som ditt företag kan vilja att du uppdaterar. Tryck på **Fortsätt** för att fortsätta.|
|![Bekräftar enhetsinställningarna.](./media/ios-22-cp-enroll-1711.png)|Företagsportalen kontrollerar om någon av dina inställningar behöver uppdateras.|
|![Inställningskontrollen slutförd med en felaktig OS-version](./media/ios-23-cp-enroll-1711.png)|Företagsportalen ger dig instruktioner för hur du kan lösa eventuella problem med dina inställningar. När du har löst problemen, trycker du på **kontrollera inställningar**.|
|![Laddningsskärmen bekräftar enhetsinställningarna](./media/ios-24-cp-enroll-1711.png)|Din enhet kontrollerar om dina inställningar är säkra nog för åtkomst till företagets resurser.|
|![Registrerade och uppdaterade inställningarna](./media/ios-25-cp-enroll-1711.png)|Gratulerar! Enheten har nu registrerats i Intune.|

> [!Note]
> Du kan behöva utföra några steg till innan enheten är fullständigt hanterad. Lär dig mer om [hur du registrerar enheten med kostnadsuppföljning av telekommunikation](enroll-your-device-with-telecom-expense-management-ios.md). Om din organisation använder Apples enhetsregistreringsprogram (DEP) kan du läsa mer [här](enroll-your-device-dep-ios.md).

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
