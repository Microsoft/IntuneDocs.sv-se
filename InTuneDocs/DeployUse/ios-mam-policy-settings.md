---
# required metadata

title: iOS MAM-principinställningar | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

#  Inställningar för iOS-princip för hantering av mobila program
Principinställningar som beskrivs nedan kan [konfigureras](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) för MAM-principen på **inställningsbladet** på Azure Portal.

Det finns två typer av principinställningar – Dataflytt- och Åtkomstinställningar:

##  Inställningar för dataflytt
Termen **principhanterade appar** används för att referera till appar som är konfigurerade med MAM-principer.

- Förhindra säkerhetskopiering av iTunes och iCloud:

  **Välj **Ja** om du vill förhindra eller **Nej** om du vill tillåta säkerhetskopiering av företagsdata från appar som hanteras av principer.**

- Standardvärde = Ja
  - **Tillåt att appen överför data till andra appar:**   Välj ett alternativ för att ange de appar som kan ta emot data från principhanterade appar:
  - **Principhanterade appar**: Tillåt överföring endast till appar som har MAM-principen
  - **Alla appar**: Tillåt överföring till alla appar

  **Inga**: Tillåt inte dataöverföring till någon app, inklusive andra principhanterade appar.

  **Om du anger det här alternativet till **Principhanterade appar** eller **Ingen** blockeras dessutom iOS 9-funktionen som gör att Spotlight-sökning kan söka efter data i appar.**

- Standardvärde = Principhanterade appar
  -  **Tillåt att appen tar emot data från andra appar:**  Ange appar som tillåts att överföra data till principhanterade appar:
  -  **Principhanterade appar**: Tillåt endast dataöverföring från andra principhanterade appar.
  -  **Alla appar**: Tillåt dataöverföring från alla appar

  ****Inga**: Tillåt inte dataöverföring från någon app.**

- Standardvärde = Alla appar Förhindra Spara som:

  **Välj **Ja** om du vill inaktivera alternativet Spara som i appar som använder den här principen.**

- Välj **Nej** om du vill tillåta att Spara som används. Standardvärde = Ja
  -   Begränsa klipp ut, kopiera och klistra in med andra appar:
  -   Ange när åtgärderna Klipp ut, Kopiera och Klistra in ska begränsas.
  -   Välj mellan: **Blockerad**: Tillåt inte åtgärderna Klipp ut, Kopiera och Klistra in mellan principhanterade appar.
  - **Principhanterade appar**: Tillåt endast åtgärderna Klipp ut, Kopiera och Klistra in mellan principhanterade appar.

  ****Principhanterade appar med inklistring**: Tillåt klipp ut och kopiera mellan principhanterade appar.**

- Tillåt att data som klipps ut eller kopieras från en annan app kan klistras in i den här appen.

  **Alla appar**: Inga begränsningar för Klipp ut, Kopiera och Klistra in mellan appar.

  Standardvärde = Principhanterade appar med Klistra in

    ****Begränsa visning av webbinnehåll i Managed Browser:** När den här inställningen är aktiverad öppnas alla länkar i appen i Managed Browser.**

- För enheter som inte är registrerade i Intune är webblänkar i principhanterade appar begränsade så att de bara öppnas i appen Managed Browser med hanteringsprincipen för mobila appar. Om du använder Intune för att hantera dina enheter läser du [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](manage-internet-access-using-managed-browser-policies.md) Standardvärde = Ja

  **Kryptera appdata:** För appar som är associerade med en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] princip för hantering av mobila program, krypteras data i viloläge med hjälp av den enhetskryptering som finns i operativsystemet.  När en PIN-kod krävs krypteras data enligt inställningarna i hanteringsprincipen för mobilappar. Enligt informationen i Apples dokumentation är de [moduler som används av iOS 7 FIPS 140-2-certifierade](http://support.apple.com/en-us/HT202739)
  - Du kan ange PIN-krypteringsvärden i principinställningarna.
  -   Dessa värden avgör när data krypteras.
  -   Alternativen är:
  -   **När enheten är låst:** Alla appdata som är associerade med den här principen krypteras när enheten är låst.
  **När enheten är låst (förutom för öppna filer):** Alla appdata som är associerade med den här principen krypteras när enheten är låst, utom data i filer som är öppnade i appen.  **Efter omstart av enheten:** Alla appdata som är associerade med den här principen krypteras när enheten startas om, tills den första gången enheten låses upp.

  ****Använd enhetsinställningar:** Appdata krypteras baserat på standardinställningarna på enheten.**
- När du aktiverar den här inställningen måste slutanvändaren konfigurera och använda en PIN-kod för att komma åt sin enhet. Om det inte finns någon PIN startar inte apparna och slutanvändaren uppmanas att ange en PIN-kod. Ett meddelande visas som informerar användaren om att dennes företag kräver att enheten har en PIN-kod för att det ska gå att komma åt programmet.

  Standardvärde -Krypteringsalternativet är inte valt **ContactSyncDisabled:**  Välj **Ja** för att förhindra att kontaktinformation synkroniseras till den interna adressboken på enheten. Om du väljer **Nej** sparar appen kontaktinformation till den interna adressboken på enheten.

  **När du gör en selektiv rensning för att ta bort företagsdata tas kontakter som synkroniserats direkt från appen till den interna adressboken bort.**
##  Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas.
Detta gäller för närvarande endast för **Microsoft Outlook**-appen.
- Standardvärde = Ja Principinställningar för iOS-åtkomst

  **Termen **principhanterade appar** används för att referera till appar som är konfigurerade med MAM-principer.**
- **Kräv enkel PIN-kod för åtkomst:**  Välj **Ja** för att kräva en PIN-kod för att använda principhanterade appar.

  Användarna uppmanas att konfigurera detta första gången de kör appen i en arbetskontext.
- Standardvärde = Ja
**Antal försök innan PIN-koden återställs:** Ange antalet tillåtna PIN-inmatningsförsök innan användaren måste återställa PIN-koden. Det finns inget standardvärde för den här inställningen

  ****Kräv fingeravtryck istället för PIN (iOS 8.0+):** Välj **Ja** om du vill kräva att ett fingeravtryck används i stället för en PIN-kod för åtkomst till appen.**
- På iOS-enheter kan du tillåta att användarna identifierar sig med fingeravtryck i stället för med en PIN-kod. **När slutanvändarna försöker ansluta till appen med ett arbetskonto uppmanas de att lämna sitt fingeravtryck i stället för att ange en PIN-kod.** Standardvärde = Ja

  ****Kräv företagets autentiseringsuppgifter för åtkomst:** Välj **Ja** om du vill kräva att företagets autentiseringsuppgifter anges i stället för en PIN-kod för åtkomst till appen.**
- Om du väljer Ja åsidosätts kraven på PIN-kod eller Touch ID. Användaren uppmanas att ange sina autentiseringsuppgifter för företaget.

  **Standardvärde = Nej**
- **Blockera hanterade appar från att köras på jailbrokade eller rotade enheter:** Välj **Ja** för att blockera appar från att köras på jailbrokade eller rotade enheter.
  -   Användaren kan fortfarande använda apparna för personliga uppgifter, men måste använda en annan enhet för arbete.

  **Standardvärde = Ja**
  - **Kontrollera åtkomstkraven på nytt efter (minuter)**|-   **Tidsgräns:** Tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen.  **Offlinerespittid:** Specificera tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen om enheten är offline. Standardvärde = 30 minuters timeout och 720 minuters offlinerespittid

  ****Intervallet innan appdata rensas efter att enheten varit offline (dagar):** Du kan välja att rensa företagsdata om en enhet har varit offline en viss tid.**


<!--HONumber=May16_HO2-->


