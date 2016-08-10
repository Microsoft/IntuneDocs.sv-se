---
title: "Registrera företagsägda iOS-enheter | Microsoft Intune"
description: "Registrera företagsägda iOS-enheter med Apple Device Enrollment Program (DEP) eller Apple Configurator"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9b7b8f6e5182e228458f5ea75e804a638f1e2a2b
ms.openlocfilehash: ca05e94e72269c11db24b667f1d113c794cd8b23


---

# Registrera företagsägda iOS-enheter i Microsoft Intune
Microsoft Intune stöder registrering av företagsägda iOS-enheter med hjälp av Apples DEP (Device Enrollment Program) eller verktyget [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) på en Mac-dator.

**Krav:**  [Certifikat för Apple Push Notification Service](set-up-ios-and-mac-management-with-microsoft-intune.md)

Du kan registrera företagsregistrerade iOS-enheter på tre sätt:

-   **Apple Configurator** – Du kan registrera iOS-enheter genom att exportera en företagsregistreringsprofil och sedan ansluta de mobila enheterna till en Mac som kör Apple Configurator. Apple Configurator stöder två typer av registrering:

    - **Registrering av installationsassistenten** – Fabriksåterställer enheten och förbereder den för installation av enhetens nya användare. Den här metoden kräver att administratören ansluter iOS-enheten via USB till en Mac-dator som kör [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) för att förkonfigurera registreringen. Enheterna levereras sedan till sina användare som kör processen med installationsassistenten, konfigurerar enheten med sina arbets- eller skolautentiseringsuppgifter och slutför registreringsprocessen. [Registrera iOS-enheter med Apple Configurator och installationsassistenten](ios-setup-assistant-enrollment-in-microsoft-intune.md)

    - **Direktregistrering** – Skapar en Apple Configurator-kompatibel fil som används vid förberedelse av enheten. Den registrerade enheten är inte fabriksåterställd, men har ingen anknytning till användaren. Den här metoden kräver att administratören ansluter iOS-enheten via USB till en Mac-dator som kör [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) för att registrera enheten. [Registrera iOS-enheter som använder direktregistrering i Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md)

-   **Device Enrollment Program (DEP)** – Distribuerar en registreringsprofil ”over-the-air” till enheter som har köpts via Apples enhetsregistreringsprogram. Enheten registreras i Intune när användaren kör installationsassistenten på enheten.  Enheter som har registrerats via DEP kan inte avregistreras av användarna. [Registrera iOS-enheter med Device Enrollment Program](ios-device-enrollment-program-in-microsoft-intune.md)

## Använda företagsportalen på DEP- eller Apple Configurator-registrerade enheter

Enheter som har konfigurerats med användartillhörighet kan installera och köra företagsportalappen för att ladda ned appar och hantera enheter. När användarna får sina enheter måste de utföra några ytterligare steg för att slutföra installationsassistenten och installera företagsportalappen.

Registrera företagsägda iOS-enheter med användartillhörighet
1. När användarna startar enheten uppmanas de att slutföra installationsassistenten. Under installationen uppmanas användarna att ange sina autentiseringsuppgifter. De måste använda autentiseringsuppgifterna (d.v.s. unika namn eller UPN) som är associerade med prenumerationen i Intune.

2. Under installationen uppmanas användarna att ange ett Apple-ID. Ett Apple-ID måste anges för att företagsportalen ska få installeras på enheten. Apple-ID:t kan också anges på inställningsmenyn för iOS efter att installationen är klar.

3. När installationen har slutförts måste företagsportalappen installeras på iOS-enheten från App Store, till exempel företagsportalappen.

4. Användaren kan nu logga in på företagsportalen med det unika namn som angavs när enheten konfigurerades.

5. Efter inloggningen uppmanas användaren att registrera enheten. Det första steget är att identifiera enheten. I appen visas en lista över iOS-enheter som redan är företagsregistrerade och har tilldelats till slutanvändarens Intune-konto. Välj motsvarande enhet.

  Om enheten inte är företagsregistrerad väljer du "ny enhet" och fortsätter med standardregistreringsflödet.

6. På nästa skärm måste användaren bekräfta serienumret för den nya enheten. Användaren kan trycka på länken "Bekräfta serienumret" för att starta inställningsappen och verifiera serienumret. Sedan måste användaren ange de 4 sista tecknen i serienumret i företagsportalappen.

  I det här steget verifieras att enheten är den företagsenhet som har registrerats i Intune. Om serienumret på enheten inte matchar har fel enhet valts. Gå tillbaka till föregående sida och välj en annan enhet.

7. När serienumret har verifierats omdirigeras användaren från företagsportalappen till företagsportalens webbplats för att slutföra registreringen. Sedan uppmanas användaren att återgå till appen.

8. Registreringen är slutförd. Nu kan du använda den här enheten med fullständiga funktioner.

### Om företagsägda hanterade enheter som saknar användartillhörighet

Det går inte att använda företagsportalen i enheter som konfigurerats med alternativet Ingen användartillhörighet. Appen ska därför inte installeras på dessa. Företagsportalen är avsedd för användare som har företagsautentiseringsuppgifter och behöver åtkomst till anpassade företagsresurser (t.ex. e-post). Enheter som har registrerats med Ingen användartillhörighet är inte avsedda att ha en dedikerad användarinloggning. Informationsenheter, POS-enheter (Point Of Sale) och enheter med delade verktyg är typiska fall då man använder enheter som registrerats utan användartillhörighet. Om användartillhörighet krävs måste du välja Användartillhörighet för enhetens registreringsprofil innan du registrerar enheten. För att ändra tillhörighetsstatus på en enhet måste du ta enheten ur bruk och registrera den på nytt.



### Se även
[Dags att registrera enheter i Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


