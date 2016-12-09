---
title: "MAM-principinställningar för Android | Microsoft Intune"
description: "I det här avsnittet beskrivs principinställningarna för hantering av mobilappar för Android-enheter."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: d0a1a2b3f4e5dbac8b333db3a5cc4bb32c0d61ef


---

# <a name="android-mobile-app-management-policy-settings-in-microsoft-intune"></a>Inställningar för hanteringsprincip för Android-mobilappar i Microsoft Intune
Principinställningarna som beskrivs i det här avsnittet kan [konfigureras](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) för en MAM-princip (hanteringsprincip för mobilappar) på **inställningsbladet** på Azure Portal.
Det finns två kategorier för principinställningar: inställningar för dataflytt och åtkomst. I det här avsnittet används termen *principhanterade appar* för att hänvisa till appar som är konfigurerade med MAM-principer.

##  <a name="data-relocation-settings"></a>Inställningar för dataflytt

- **Förhindra Android-säkerhetskopieringar:** Välj **Ja** om du vill inaktivera eller **Nej** om du vill aktivera säkerhetskopiering av företagsdata från principhanterade appar.

  Standardvärde = **Ja**
- **Tillåt att appen överför data till andra appar**: Välj ett alternativ för att ange vilken typ av appar som kan ta emot företagsdata från principhanterade appar:
  -   **Principhanterade appar**: Tillåter endast överföring till appar som MAM-principen tillämpas på.
  -   **Alla appar**: Aktiverar överföring till alla appar.
  -   **Ingen**: Tillåter inte dataöverföring till någon app.

 Standardvärde = **Principhanterade appar**.
- **Tillåt att appen tar emot data från andra appar**: Ange vilka appar som kan överföra data till de principhanterade apparna:
  -   **Principhanterade appar**: Tillåter endast dataöverföringar från andra principhanterade appar.
  -   **Alla appar**: Tillåter dataöverföring från alla appar.
  -   **Inga**: Tillåter inte dataöverföring från någon app.

  Standardvärde = **Alla appar**

-   **Förhindra Spara som**: Välj **Ja** om du vill inaktivera alternativet Spara som i appar som använder den här principen. Välj **Nej** om du vill tillåta användningen av Spara som.

  Standardvärde = **Ja**
- **Begränsa klipp ut, kopiera och klistra in med andra appar**: Ange när åtgärderna Klipp ut, Kopiera och Klistra in ska begränsas. Välj mellan:
  -   **Blockerad**: Tillåter inte åtgärderna Klipp ut, Kopiera och Klistra in mellan principhanterade appar.
  -   **Principhanterade appar**: Tillåter endast åtgärderna Klipp ut, Kopiera och Klistra in mellan principhanterade appar.
  -   **Principhanterade appar med inklistring**: Tillåter åtgärderna Klipp ut och Kopiera mellan principhanterade appar. Tillåter att utklippta eller kopierade data från alla appar kan klistras in i den här appen.
  -   **Alla appar**: Inga begränsningar för klipp ut, kopiera och klistra in mellan appar.

  Standardvärde = **Principhanterade appar med inklistring**
-   **Begränsa webbinnehåll till visning i Managed Browser**: Välj **Ja** om du vill ange att alla länkar i appen ska öppnas i Managed Browser-appen.

  För enheter som inte har registrerats i Intune öppnas bara länkar i principhanterade appar i Managed Browser-appen om du använder MAM-principen.

  Om du använder Intune för att hantera dina enheter läser du [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

  Standardvärde = **Ja**
- **Kryptera appdata:** Välj **Ja** för att aktivera kryptering. När den här inställningen är aktiverad tillhandahåller Microsoft kryptering för appar som är associerade med en MAM-princip. Data krypteras synkront under I/O-åtgärder. Innehållet i enhetens lagringsutrymme krypteras alltid.
  >[!NOTE]
  >Krypteringsmetoden är inte FIPS 140-2-certifierad.

  Standardvärde = **Ja**

- **Inaktivera kontaktsynkronisering:** Välj **Ja** för att förhindra att kontaktinformation synkroniseras med den interna adressboken på enheten. Om du väljer **Nej** sparar appen kontaktinformationen till den interna adressboken på enheten.

  När du gör en selektiv rensning för att ta bort företagsdata tas kontakter som synkroniseras direkt mellan appen och den interna adressboken bort. Kontakter som synkroniseras mellan den interna adressboken och en annan extern källa kan inte rensas. Detta gäller för närvarande endast för Microsoft Outlook-appen.

  Standardvärde = **Ja**
- **Inaktivera utskrifter**: Välj **Ja** för att förhindra utskrifter av företagsdata från appar som är associerade med MAM-principen.

  Standardvärde = **Ja**

##  <a name="access-settings"></a>Åtkomstinställningar

- **Kräv PIN-kod för åtkomst**: Välj **Ja** om du vill kräva en PIN-kod för användning av principhanterade appar. Användarna uppmanas att konfigurera detta första gången de kör appen i en arbetskontext.

 Standardvärde = **Ja**

 -  **Tillåt enkel PIN-kod:** Ange du om du vill tillåta att användarna använder enkla PIN-kodssekvenser, till exempel 1234 eller 1111. Standardvärde = **Ja**.
 - **PIN-kodslängd:** Ange det minsta antalet siffror i en PIN-kod. Standardvärde = **4**.
 - **Antal försök innan PIN-koden återställs**: Ange antalet tillåtna PIN-inmatningsförsök innan användaren måste återställa PIN-koden. Det finns inget standardvärde för den här inställningen.
 - **Kräv fingeravtryck istället för PIN (Android 6.0+):** Välj **Ja** om du vill kräva att ett fingeravtryck används i stället för en PIN-kod för åtkomst till appen.
 På Android-enheter kan du tillåta att användare identifierar sig med fingeravtryck i stället för med en numrerad PIN-kod. När de försöker öppna appen med ett arbetskonto uppmanas de att lämna sitt fingeravtryck i stället för att ange en PIN-kod.
 - **Kräv företagsautentiseringsuppgifter för åtkomst**: Välj **Ja** om du vill kräva att företagets autentiseringsuppgifter anges i stället för en PIN-kod eller fingeravtryck för åtkomst till appen. Om du väljer **Ja** åsidosätter den här inställningen kraven på PIN-kod eller Touch-ID. Användaren uppmanas att ange sina autentiseringsuppgifter för företaget. Standardvärde = **Nej**.


- **Blockera hanterade appar från att köras på jailbrokade eller rotade enheter**: Välj **Ja** för att blockera appar från att köras på jailbrokade eller rotade enheter. Användaren kan fortsätta att använda appar för personliga uppgifter, men måste använda en annan enhet för arbete.

  Standardvärde = **Ja**
- **Kontrollera åtkomstbehörigheterna på nytt efter (minuter)**
  -   **Tidsgräns**: Ange tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen.
  -   **Offlinerespittid**: Specificera tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen om enheten är offline.

  Standardvärden = **30** minuters tidsgräns och **720** minuters offlinerespittid.

-   **Intervallet innan appdata rensas efter att enheten varit offline (dagar)**: Välj att rensa företagsdata om en enhet har varit offline en viss tid.  Ange hur många dagar en enhet kan vara offline innan företagsdata tas bort från enheten.

    >[!TIP]
    >Ange värdet **0** för att inaktivera den här inställningen.

  Standardvärde = **90** dagar
- **Blockera skärmdump och Android Assistant (Android 6 Marshmallow eller senare)**: Välj **Ja** för att blockera funktioner för skärmdumpar och **Android Assistant** på enheten när den här appen används.



<!--HONumber=Dec16_HO2-->


