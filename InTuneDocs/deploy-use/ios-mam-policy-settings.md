---
title: "iOS MAM-principinställningar | Microsoft Intune"
description: "I det här avsnittet beskrivs principinställningarna för hantering av mobilappar för iOS-enheter."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 913008568226621de4824c5bac287e8a65dc6533


---

#  <a name="ios-mobile-app-management-policy-settings"></a>Inställningar för iOS-princip för hantering av mobila program
Principinställningarna som beskrivs i det här avsnittet kan [konfigureras](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) för en MAM-princip (hanteringsprincip för mobilappar) på **inställningsbladet** på Azure Portal.

Det finns två kategorier för principinställningar: inställningar för dataflytt och åtkomst. I det här avsnittet används termen *principhanterade appar* för att hänvisa till appar som är konfigurerade med MAM-principer.

##  <a name="data-relocation-settings"></a>Inställningar för dataflytt

- **Förhindra iTunes- och iCloud-säkerhetskopieringar**: Välj **Ja** om du vill förhindra eller **Nej** om du vill tillåta säkerhetskopiering av företagsdata från principhanterade appar.

  Standardvärde = **Ja**.

- **Tillåt att appen överför data till andra appar**: Välj ett alternativ för att ange vilka appar som kan ta emot data från principhanterade appar:
  - **Principhanterade appar**: Tillåt överföring endast till appar som har MAM-principen
  - **Alla appar**: Tillåt överföring till alla appar.
  - **Inga**: Tillåt inte dataöverföring till någon app, inklusive andra principhanterade appar.

  Om du anger det här alternativet till **Principhanterade appar** eller **Ingen** blockeras dessutom iOS 9-funktionen som gör att Spotlight-sökning kan söka efter data i appar.

  >[!NOTE]
  >Den här inställningen styr inte användningen av funktionen Öppna med på mobila enheter. Information om Öppna med finns i [Hantera dataöverföring mellan iOS-appar med Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

  Standardvärde = **Principhanterade appar**.

- **Tillåt att appen tar emot data från andra appar**: Ange appar som tillåts att överföra data till principhanterade appar:
  -  **Principhanterade appar**: Tillåt endast dataöverföring från andra principhanterade appar.
  -  **Alla appar**: Tillåt dataöverföring från alla appar.
  -  **Inga**: Tillåt inte dataöverföring från någon app.

  Standardvärde = **Alla appar**.

- **Förhindra Spara som**: Välj **Ja** om du vill inaktivera alternativet Spara som i appar som använder den här principen. Välj **Nej** om du vill tillåta att Spara som används.

  Standardvärde = **Ja**.

- **Begränsa klipp ut, kopiera och klistra in med andra appar**: Ange när åtgärder för klipp ut, kopiera och klistra in ska begränsas. Välj mellan:
  -   **Blockerad**: Tillåt inte åtgärderna klipp ut, kopiera och klistra in mellan principhanterade appar.
  -   **Principhanterade appar**: Tillåt endast åtgärderna klipp ut, kopiera och klistra in mellan principhanterade appar.
  -   **Principhanterade appar med inklistring**: Tillåt klipp ut och kopiera mellan principhanterade appar. Tillåt att data som klipps ut eller kopieras från en annan app kan klistras in i den här appen.
  - **Alla appar**: Inga begränsningar för klipp ut, kopiera och klistra in mellan appar.

  Standardvärde = **Principhanterade appar med inklistring**.

- **Begränsa webbinnehåll till visning i Managed Browser**: När den här inställningen är aktiverad öppnas alla länkar i appen i Managed Browser.

  För enheter som inte har registrerats i Intune kan webblänkar i principhanterade appar endast öppnas i appen Managed Browser.

  Om du använder Intune för att hantera dina enheter läser du [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

  Standardvärde = **Ja**.

- **Kryptera appdata**: För appar som associeras med en Intune MAM-princip krypteras data i vila med kryptering på enhetsnivå som tillhandahålls av operativsystemet. När en PIN-kod krävs krypteras data enligt inställningarna i MAM-principen. Enligt informationen i Apples dokumentation är [modulerna som används i iOS 7 FIPS 140-2-certifierade](http://support.apple.com/en-us/HT202739).

  Du kan ange PIN-krypteringsvärden i principinställningarna. Dessa värden avgör när data krypteras. Alternativen är:
  -   **När enheten är låst**: Alla appdata som är associerade med den här principen krypteras när enheten är låst.
  -   **När enheten är låst (förutom för öppna filer)**: Alla appdata som är associerade med den här principen krypteras när enheten är låst, utom data i filer som är öppna i appen.
  -   **Efter omstart av enheten**: Alla appdata som är associerade med den här principen krypteras när enheten startas om, tills den första gången enheten låses upp.
  -   **Använd enhetsinställningar**: Appdata krypteras baserat på standardinställningarna på enheten.
  När du aktiverar den här inställningen måste användaren konfigurera och använda en PIN-kod för att komma åt sin enhet.  Om det inte finns någon PIN-kod startar inte apparna och användaren uppmanas att ange en PIN-kod. Ett meddelande visas som informerar användaren om att dennes företag kräver att enheten har en PIN-kod för att det ska gå att komma åt programmet.

  Standardvärde = Krypteringsalternativet är inte valt.
- **Inaktivera kontaktsynkronisering:** Välj **Ja** för att förhindra att kontaktinformation synkroniseras till den interna adressboken på enheten. Om du väljer **Nej** sparar appen kontaktinformation till den interna adressboken på enheten.

  När du gör en selektiv rensning för att ta bort företagsdata tas kontakter som synkroniserats direkt från appen till den interna adressboken bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. Detta gäller för närvarande endast för Microsoft Outlook-appen.

  Standardvärde = **Ja**.

- **Inaktivera utskrifter**: Välj **Ja** att förhindra utskrifter av företagsdata från appar som är associerade med MAM-principen.

    Standardvärde = **Ja**.

##  <a name="access-settings"></a>Åtkomstinställningar

- **Kräv PIN-kod för åtkomst**: Välj **Ja** om du vill kräva en PIN-kod för användning av principhanterade appar. Användarna uppmanas att konfigurera detta första gången de kör appen i en arbetskontext.

  Standardvärde = **Ja**.
    -  **Tillåt enkel PIN-kod:** Ange du om du vill tillåta att användarna använder enkla PIN-kodssekvenser, till exempel 1234 eller 1111. Standardvärde = **Ja**.
    - **PIN-kodslängd:** Ange det minsta antalet siffror i en PIN-kod. Standardvärde = **4**.
    - **Antal försök innan PIN-koden återställs**: Ange antalet tillåtna PIN-inmatningsförsök innan användaren måste återställa PIN-koden. Det finns inget standardvärde för den här inställningen.

- **Kräv fingeravtryck istället för PIN (iOS 8.0+)**: Välj **Ja** om du vill kräva att ett fingeravtryck används i stället för en PIN-kod för åtkomst till appen.
På iOS-enheter kan du låta användarna identifiera sig med hjälp av ett fingeravtryck i stället för en PIN-kod. När användarna försöker öppna appen med ett arbetskonto uppmanas de att lämna sitt fingeravtryck i stället för att ange en PIN-kod.

  Standardvärde = **Ja**.
- **Kräv företagets autentiseringsuppgifter för åtkomst**: Välj **Ja** om du vill kräva att företagets autentiseringsuppgifter anges i stället för en PIN-kod för åtkomst till appen. Om du väljer **Ja** åsidosätts kraven på PIN-kod eller Touch ID. Användaren uppmanas att ange sina autentiseringsuppgifter för företaget.

  Standardvärde = **Nej**.
- **Blockera hanterade appar från att köras på jailbrokade eller rotade enheter**: Välj **Ja** för att blockera appar från att köras på jailbrokade eller rotade enheter. Användaren kan fortfarande använda apparna för personliga uppgifter, men måste använda en annan enhet för arbete.

  Standardvärde = **Ja**.
- **Kontrollera åtkomstbehörigheterna på nytt efter (minuter)**
  -   **Tidsgräns**: Ange tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen.
  -   **Offlinerespittid**: Specificera tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen om enheten är offline.

  Standardvärden = **30** minuters tidsgräns och **720** minuters offlinerespittid.
- **Intervallet innan appdata rensas efter att enheten varit offline (dagar)**: Du kan välja att rensa företagsdata om en enhet har varit offline en viss tid. Ange hur många dagar en enhet kan vara offline innan företagsdata tas bort från enheten.

  >[!TIP]
  >Ange värdet **0** för att inaktivera den här inställningen.

  Standardvärde = **90** dagar.



<!--HONumber=Oct16_HO5-->


