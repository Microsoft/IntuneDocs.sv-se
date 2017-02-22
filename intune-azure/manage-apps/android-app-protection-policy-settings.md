---
title: "Principinställningar för Android-appskydd | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: I det här avsnittet beskrivs principinställningarna för appskydd för Android-enheter."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9e9ef9f5-1215-4df1-b690-6b21a5a631f8
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 6720c163e712e9d27319b16b0e1515e9e7f13ee8


---

# <a name="android-app-protection-policy-settings"></a>Principinställningar för Android-appskydd
Principinställningarna som beskrivs i det här avsnittet kan [konfigureras](app-protection-policies.md) för en appskyddsprincip på bladet **Inställningar** i Azure-portalen.
Det finns två kategorier för principinställningar: inställningar för dataflytt och åtkomst. I det här avsnittet används termen *principhanterade appar* för att hänvisa till appar som har konfigurerats med appskyddsprinciper.

##  <a name="data-relocation-settings"></a>Inställningar för dataflytt

| Inställningar | Använd så här | Standardvärde(n) |
|------|------|------|
| **Förhindra Android-säkerhetskopieringar** | Välj **Ja** för att förhindra att den här appen säkerhetskopierar arbets- eller skoldata i [Android Backup Service](https://developer.android.com/google/backup/index.html) Välj **Nej** för att tillåta att den här appen säkerhetskopierar arbets- eller skoldata.| Ja |
| **Tillåt att appen överför information till andra appar** | Ange vilka appar som kan ta emot data från den här appen: <ul><li> **Principhanterade appar**: Tillåt endast överföring till andra principhanterade appar.</li> <li>**Alla appar**: Tillåt överföring till alla appar. </li> <li>**Inga**: Tillåt inte dataöverföring till någon app, inklusive andra principhanterade appar.</li></ul> | Alla appar |
| **Tillåt att appen hämtar data från andra appar** | Ange vilka appar som kan överföra data till den här appen: <ul><li>**Principhanterade appar**: Tillåt endast överföring från andra principhanterade appar.</li><li>**Alla appar**: Tillåt dataöverföring från alla appar.</li><li>**Ingen**: Tillåt inte dataöverföring från någon app, inklusive andra principhanterade appar. | Alla appar |
| **Förhindra "Spara som"** | Välj **Ja** om du vill inaktivera alternativet Spara som i den här appen. Välj **Nej** om du vill tillåta att Spara som används. | Nej |
| **Begränsa klipp ut, kopiera och klistra in med andra appar** | Ange när åtgärderna klippa ut, kopiera och klistra in kan användas med den här appen. Välj mellan: <ul><li>**Blockerad**: Tillåt inte åtgärderna klipp ut, kopiera och klistra in mellan den här appen och andra appar.</li><li>**Principhanterade appar**: Tillåt endast åtgärderna klipp ut, kopiera och klistra in mellan den här appen och andra principhanterade appar.</li><li>**Principhanterade appar med inklistring**: Tillåt klipp ut och kopiera mellan den här appen och andra principhanterade appar. Tillåt att data från en annan app klistras in i den här appen.</li><li>**Alla appar**: Inga begränsningar för klipp ut, kopiera och klistra in till och från den här appen. | Alla appar |
|**Begränsa webbinnehåll till visning i Managed Browser** | Välj **Ja** för att tvinga webblänkar i appen att öppnas i appen Managed Browser. <br><br> För enheter som inte har registrerats i Intune kan webblänkar i principhanterade appar endast öppnas i appen Managed Browser. <br><br> Om du använder Intune för att hantera dina enheter läser du [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/manage-internet-access-using-managed-browser-policies). | Nej |
| **Kryptera appdata** | Välj **Ja** om du vill aktivera kryptering av arbets- eller skoldata i den här appen. Intune använder ett OpenSSL-krypteringsschema tillsammans med Android Keystore-systemet för att kryptera appdata på ett säkert sätt. Data krypteras synkront under I/O-åtgärder. Innehållet i enhetens lagringsutrymme krypteras alltid. <br><br> Krypteringsmetoden är **inte** FIPS 140-2-certifierad.  | Ja |
| **Inaktivera synkronisering av kontakter** | Välj **Ja** att förhindra att appen sparar data i den interna appen Kontakter på enheten. Om du väljer **Nej** kan appen spara data i den interna appen Kontakter på enheten. <br><br>När du utför en selektiv rensning för att ta bort arbets- eller skoldata från appen kommer kontakter som har synkats direkt från appen till den inbyggda appen Kontakter att tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. Detta gäller för närvarande endast för Microsoft Outlook-appen. | Nej |
| **Inaktivera utskrift** | Välj **Ja** att förhindra att appen skriver ut arbets- eller skoldata. | Nej |


  >[!NOTE]
  >Krypteringsmetoden för inställningen **Kryptera appdata** är **inte** FIPS 140-2-certifierad.




##  <a name="access-settings"></a>Åtkomstinställningar

| Inställningar | Använd så här | Standardvärde(n) |
|------|------|------|
| **Kräv PIN-kod för åtkomst** | Välj **Ja** för att kräva en PIN-kod för att använda den här appen. Användarna uppmanas att konfigurera denna PIN-kod första gången de kör appen i en arbets- eller skolkontext. Standardvärde = **Ja**.<br><br> Konfigurera följande inställningar för PIN-styrka: <ul><li>**Antal försök före återställning av PIN**: Ange antalet försök som användaren har att ange rätt PIN-kod innan den måste återställas. Standardvärde = **5**.</li><li> **Tillåt enkel PIN-kod:** Välj **Ja** du om du vill tillåta att användarna använder enkla PIN-kodssekvenser, till exempel 1234 eller 1111. Välj **Nej** om du vill förhindra att de använder enkla sekvenser. Standardvärde = **Ja**. </li><li> **PIN-kodslängd**: Ange det minsta antalet siffror i en PIN-kodssekvens. Standardvärde = **4**. </li><li> **Kräv fingeravtryck istället för PIN (Android 6.0+)**: Välj **Ja** om du vill kräva att [autentisering med fingeravtryck](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) används i stället för en PIN-kod för åtkomst till appen. Standardvärde = **Ja**.<br><br> På Android-enheter kan du låta användaren bekräfta sin identitet med hjälp av [Android-autentisering med fingeravtryck](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) i stället för en PIN-kod. När användarna försöker använda appen med ett arbets- eller skolkonto uppmanas de att lämna sitt fingeravtryck i stället för att ange en PIN-kod. </li></ul>| Kräv PIN-kod: Ja <br><br> PIN-återställningsförsök: 5 <br><br> Tillåt enkel PIN-kod: Ja <br><br> PIN-kodslängd: 4 <br><br> Tillåt fingeravtryck: Ja |
| **Kräv företagets autentiseringsuppgifter för åtkomst** | Välj **Ja** om du vill kräva att användaren loggar in med sitt arbets- eller skolkonto i stället för att ange en PIN-kod för åtkomst till appen. Om du väljer **Ja** åsidosätts kraven på PIN-kod eller Touch ID.  | Nej |
| **Hindra hanterade appar från att köras på jailbrokade eller rotade enheter** |  Välj **Ja** om du vill förhindra att den här appen körs på jailbrokade eller rotade enheter. Användaren kan fortfarande använda apparna för personliga uppgifter, men måste använda en annan enhet för att komma åt arbets- eller skoldata i denna app. | Ja |
| **Kontrollera åtkomstbehörigheterna på nytt efter (minuter)** | Konfigurera följande inställningar: <ul><li>**Tidsgräns**: Ange tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen. Standardvärde = **30** minuter.</li><li>**Offlinerespittid**: Specificera tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen om enheten är offline. Standardvärde = **720** minuter (12 timmar).</li></ul>| Tidsgräns: 30 <br><br> Offline: 720 |
| **Offlineintervall innan appdata rensas (dagar)** | Arbets- eller skoldata i den här appen kan rensas om en enhet har varit offline längre än en viss tid. Ange hur många dagar en enhet kan vara offline innan arbets- eller skoldata tas bort från enheten. <br><br> | 90 dagar |
| **Blockera skärmdump och Android Assistant (Android 6.0+)** | Välj **Ja** om du vill blockera funktionerna för skärmdumpar och **Android-assistenten** på enheten när appen används. Om du väljer **Ja** blir även förhandsgranskningsbilden i appväxlaren suddig när den här appen används med ett arbets- eller skolkonto. | Nej |



<!--HONumber=Feb17_HO1-->


