---
title: Registrera företagsägda iOS-enheter
description: Registrera företagsägda iOS-enheter med Apples enhetsregistreringsprogram (DEP) eller Apple Configurator
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 93ff84d263c2fe8825d2cf5a86249bbf19cb9173
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020919"
---
# <a name="enroll-corporate-owned-ios-devices-in-microsoft-intune"></a>Registrera företagsägda iOS-enheter i Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune stöder registrering av företagsägda iOS-enheter med hjälp av Apples enhetsregistreringsprogram (DEP) eller verktyget [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017) på en Mac-dator.

**Förutsättning:** Ett [certifikat för Apple Push Notification Service](set-up-ios-and-mac-management-with-microsoft-intune.md)

Du kan registrera företagsregistrerade iOS-enheter på tre sätt:

- Apple Configurator med installationsassistenten eller direktregistrering
- Program för enhetsregistrering
- Företagsportalappen

>[!NOTE]
>Registreringsmetoderna för Apple Configurator och Programmet för enhetsregistrering (DEP) kan inte användas med [hanteraren av enhetsregistrering](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) (DEM).

Som standard tillåts alla iOS-enheter registreras i Intune. Om du vill blockera personliga eller företagsägda enheter från registrering loggar du in på [administrationsportalen för Microsoft Intune](https://manage.microsoft.com) med dina autentiseringsuppgifter som administratör. Välj **Admin** > **Hantering av mobila enheter** > **Registreringsregler** och avmarkera de tillämpliga alternativen.

## <a name="use-apple-configurator"></a>Använd Apple Configurator

Du kan registrera iOS-enheter genom att exportera en företagsregistreringsprofil och sedan ansluta de mobila enheterna till en Mac som kör Apple Configurator. Apple Configurator stöder två typer av registrering:

- **Registrering av installationsassistenten**: Återställer enheten till fabriksinställningarna och förbereder den för installation av enhetens nya användare. Den här metoden kräver att administratören ansluter iOS-enheten via USB till en Mac-dator som kör [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017) så att registreringen kan förkonfigureras. Enheterna levereras sedan till de användare som kör installationsassistensprocessen. Den här processen konfigurerar enheten med användarnas autentiseringsuppgifter arbetet eller skolan och slutför registreringen. Mer information finns i [Registrera iOS-enheter med hjälp av Apple Configurator och installationsassistenten](ios-setup-assistant-enrollment-in-microsoft-intune.md).

- **Direktregistrering**: Skapar en Apple Configurator-kompatibel fil som används vid förberedelse av enheten. Den registrerade enheten är inte fabriksåterställd, men den har ingen anknytning till användaren. Den här metoden kräver att administratören ansluter iOS-enheten via USB till en Mac-dator som kör [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017) för att registrera enheten. Mer information finns i [Registrera iOS-enheter som använder direktregistrering i Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md).

## <a name="use-the-device-enrollment-program-dep"></a>Använd enhetsregistreringsprogrammet (DEP)
DEP distribuerar en registreringsprofil trådlöst till enheter som köpts via DEP. Enheten registreras i Intune när användaren kör installationsassistenten på enheten. Mer information finns i [Registrera iOS-enheter med enhetsregistreringsprogrammet](ios-device-enrollment-program-in-microsoft-intune.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Använda företagsportalen på enheter som registrerats med enhetsregistreringsprogrammet eller Apple Configurator

Enheter som har konfigurerats med mappning mellan användare kan installera och köra företagsportalsappen och ladda ned appar och hantera enheter. Efter det att användarna fått sina enheter måste de utföra ett antal ytterligare steg för att slutföra installationen och installera företagsportalsappen.

Användartillhörighet krävs för att ge stöd åt följande:
  - Hantering av mobilprogramsappar (MAM, Mobile Application Management)
  - Villkorlig åtkomst till e-post och företagsdata
  - Företagsportalappen

**Hur en användare registrerar företagsägda iOS-enheter med användartillhörighet**
1. När användaren startar enheten uppmanas han eller hon att slutföra arbetet med installationsassistenten. Under installationen uppmanas användarna att ange sina autentiseringsuppgifter. Användaren måste använda de autentiseringsuppgifter (unikt namn eller UPN) som är associerade med prenumerationen i Intune.

2. Under installationen uppmanas användarna att ange ett Apple-ID. Användaren måste ange ett Apple-ID för att företagsportalen ska få installeras på enheten. Användaren kan även ange ID från iOS-inställningsmenyn när installationen har slutförts.

3. När installationen har slutförts måste företagsportalappen installeras på iOS-enheten från App Store.

4. Användaren kan nu logga in på företagsportalen med det UPN som angavs när enheten konfigurerades.

5. Efter inloggningen uppmanas användaren att registrera enheten. Det första steget är att identifiera enheten. I appen visas en lista över iOS-enheter som redan är företagsregistrerade och har tilldelats till användarens Intune-konto. Användaren ska välja motsvarande enhet.

   Om enheten inte är företagsregistrerad ska användaren välja **ny enhet** och fortsätta med standardregistreringsflödet.

6. På nästa skärm måste användaren bekräfta den nya enhetens serienummer. Användaren kan trycka på länken **Bekräfta serienumret** vilket kommer att starta instruktioner för användning av inställningsappen för att verifiera serienumret. Sedan måste användaren ange de fyra sista tecknen i serienumret i företagsportalappen.

   I det här steget verifieras att enheten är den företagsenhet som har registrerats i Intune. Om serienumret på enheten inte matchar har fel enhet valts. Användaren bör gå tillbaka till föregående sida och välja en annan enhet.

7. När serienumret har verifierats omdirigeras användaren från företagsportalappen till företagsportalens webbplats för att slutföra registreringen. På webbplatsen uppmanas sedan användaren att återgå till appen.

8. Registreringen är slutförd. Användaren kan nu använda den här enheten med fullständiga funktioner.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Om företagsägda hanterade enheter som saknar användartillhörighet

Det går inte att använda företagsportalen i enheter som har konfigurerats utan användartillhörighet. Appen ska därför inte installeras på dessa. Företagsportalen är avsedd för användare som har företagsautentiseringsuppgifter och behöver åtkomst till anpassade företagsresurser (t.ex. e-post). Enheter som har registrerats utan användartillhörighet är inte avsedda för dedikerad användarinloggning. Informationsenheter, POS-enheter (Point Of Sale) och enheter med delade verktyg är typiska exempel på enheter som registrerats utan användartillhörighet.

Om användartillhörighet krävs måste du välja **Användartillhörighet** för enhetens registreringsprofil innan du registrerar enheten. Om du vill ändra tillhörighetsstatus på en enhet måste du ta enheten ur bruk och registrera den på nytt.



### <a name="see-also"></a>Se även
[Krav för att registrera enheter i Microsoft Intune](prerequisites-for-enrollment.md)
