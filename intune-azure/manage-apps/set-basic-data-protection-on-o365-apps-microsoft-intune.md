---
title: "Ange grundläggande datahantering för Office 365-appar – Intune Azure-förhandsgranskning | Microsoft Docs"
description: "Intune Azure-förhandsgranskning: Supportdokumentation för guiden Hantera Office 365-appar."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 01/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 852612ac-f146-4372-a900-3f6fdebd05ad
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ayesham
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4c45b7fc8a520d869f21717fea36e27b242cf39
ms.openlocfilehash: 7cff88f0365cff1de133fdafdce2bd45b36d551e


---


# <a name="how-your-users-will-experience-basic-protection-on-managed-office-365-apps"></a>Hur användarna upplever det grundläggande skyddet på hanterade Office 365-appar

Guiden **Hantera Office 365-appar** skapar en appskyddsprincip för varje enhetsplattform.

Guiden aktiverar följande principer:

**iOS**
* Kryptera appdata

**Android**
* Kryptera appdata
* Kräv enkel PIN-kod för åtkomst

De här principerna ser till att du kan hantera Office 365-appar, vilket ger dig möjligheten att vid behov rensa arbetsdata från Office-apparna. De säkerställer även grundläggande skydd i händelse av att en enhet blir stulen eller förloras på annat sätt, genom att dina data har krypterats och att du måste ange en PIN-kod när du vill visa data i Office 365-appar.


Det här artikeln använder OneDrive för företag som ett illustrerande exempel för hur du kan ändra användarupplevelsen i program som hanteras av Intune.


>[!NOTE]
>På en personlig enhet laddar slutanvändaren oftast ned appen. Om enheten hanteras av en MDM-lösning kan du distribuera appen till enheten.

## <a name="user-experience-on-an-ios-device"></a>Användarupplevelsen på en iOS-enhet

1. Öppna inloggningssidan genom att starta appen OneDrive för företag.  <br/> ![Bild av OneDrive-inloggningsskärmen för iOS](./media/onedrive-ios-sign-in.png)
2. Skriv användarnamnet för ditt arbetskonto. Du omdirigeras till O365-autentiseringssidan där du kan ange dina autentiseringsuppgifter för arbetet. <br/> ![Bild av inloggningssidan för Office 365](./media/o365-sign-in-ios.png)
3. När dina autentiseringsuppgifter har autentiserats av Azure Active Directory tillämpas MAM-principerna och du uppmanas att starta om appen OneDrive för företag.  <br/>![Bild av omstartsprompten för iOS](./media/ios-restart-prompt.png)
>[!NOTE]
>Meddelandet om nödvändig omstart visas bara på enheter som inte har registrerats i Intune.


4. Starta om appen OneDrive för företag. Appen börjar med MAM-principerna aktiverade och du uppmanas att ange en PIN-kod för enheten (om du ännu inte har konfigurerat någon PIN-kod för enheten). <br/> ![Bild av uppmaningen om att skapa en PIN-kod](./media/pin-prompt-ios.png)

>[!NOTE]
>De flesta av dina användare ser aldrig den här uppmaningen. Det är bara de användare som inte har aktiverat någon PIN-kod på sina iOS-enheter som ser uppmaningen.


5. När du väl har angett PIN-koden och bekräftat den, så gå tillbaka till appen OneDrive för företag. Ett engångsmeddelande visas om att din IT-administratör nu skyddar arbetsdata i OneDrive. <br/> ![Bild av engångsmeddelande från din IT-administratör](./media/one-time-notice.png)
6. Klicka dig förbi meddelandet för att få åtkomst till dina filer på OneDrive för företag. <br/> ![Bild av OneDrive-filer på iOS-enhet](./media/onedrive-files-ios.png) <br/>

>[!NOTE]
>När du ändrar en distribuerad princip tillämpas ändringarna nästa gång du öppnar appen.


## <a name="user-experience-on-an-android-device"></a>Användarupplevelsen på en Android-enhet

1. Öppna inloggningssidan genom att starta appen OneDrive för företag.  <br/> ![Bild av välkomstsida i OneDrive-appen](./media/onedrive-android-welcome.png)
2. Skriv användarnamnet för ditt arbetskonto. Du omdirigeras till O365-autentiseringssidan där du kan ange dina autentiseringsuppgifter för arbetet. <br/> ![Bild av O365-inloggning på Android](./media/o365-sign-in-android.png)
3. Efter det att dina autentiseringsuppgifter har autentiserats av Azure Active Directory visas ett meddelande med anvisningar om hur du installerar företagsportalappen, såvida den inte redan har installerats på enheten. Fortsätt genom att knacka på **Gå till butik**. <br/> ![Bild av meddelande om att hämta företagsportalappen](./media/get-company-portal-android.png) <br/>Om du redan har installerat företagsportalappen på din telefon startas OneDrive för företag appen automatiskt och du kan gå direkt till slutanteckningen.
>[!IMPORTANT]
>När du har konfigurerat de Office-appar på Android som ska hanteras av en MAM-princip **måste** enhetens användare installera företagsportalappen för att få åtkomst till e-post och dokument, även om slutanvändaren inte behöver öppna eller logga in på appen för att faktiskt läsa e-postmeddelandena eller dokumenten.

4. Nu är du i Google Play Store, där du kan hämta och installera företagsportalappen. Appen hjälper till att skydda dina data. <br/> ![Bild av appen i Google Play Store](./media/google-play-get-app-android.png)
5. När du har slutfört appinstallationen godkänner du villkoren genom att välja **Acceptera**. Appen OneDrive för företag startas automatiskt.


>[!NOTE]
>Nästa gång du öppnar OneDrive för företag kan du bli ombedd att ange en PIN-kod om så krävs. När du har konfigurerat och bekräftat PIN-koden kan du fortsätta till OneDrive för företag.

![Bild av fråga om PIN-kod](./media/pin-prompt-android.png)


<!--- Original steps: 6. The next time you open OneDrive for Business, you may be asked to set a PIN, if your IT requires one to use the OneDrive for Business app. ART 7. After you set and confirm the PIN, you can continue on to OneDrive for Business. -->

## <a name="what-policies-does-this-wizard-set"></a>Vilka principer konfigurerar den här guiden?
|     |       | |
|----|--------|-|
|**Namn**|Hantera Office 365-appar| |
| **Beskrivning**|Skapats av guiden Hantera Office 365-appar| |
| |  | |
| **Namn** |**iOS-principvärde** | **Android-principvärde** |
|Förhindra säkerhetskopiering av iTunes och iCloud| Nej | E.t. |
|Förhindra Android-säkerhetskopieringar |E.t. | Nej|
|Tillåt att appen överför information till andra appar | Alla appar | Alla appar|
|Tillåt att appen hämtar data från andra appar| Alla appar | Alla appar|
|Förhindra ”Spara som” | Nej | Nej|
|Begränsa klipp ut, kopiera och klistra in med andra appar | Alla appar | Alla appar |
|Begränsa webbinnehåll till att bara visas i en företagshanterad webbläsare | Nej| Nej|
|Kryptera appdata | När enheten är låst | Ja|
|Inaktivera synkronisering av kontakter | Nej| Nej|
|Inaktivera utskrift | Nej | Nej|
|Kräv PIN-kod för åtkomst | Nej | Ja|
|Antal försök innan PIN-koden återställs | E.t. |5|
|Tillåt enkel PIN-kod | E.t. |Ja|
|PIN-kodslängd | E.t. | 4|
|Tillåt fingeravtryck istället för PIN | E.t. | Ja |
|Kräv företagets autentiseringsuppgifter för åtkomst | Nej | Nej|
|Hindra hanterade appar från att köras på jailbrokade eller rotade enheter | Nej | Nej|
|Kontrollera åtkomstbehörigheterna på nytt efter (minuter) – tidsgräns | 30 | 30|
|Kontrollera åtkomstbehörigheterna på nytt efter (minuter) – offline-respitperiod | 720 |720|
|Offlineintervall (dagar) innan appdata rensas | 90 | 90|
|Blockera skärmdump (endast Android-enheter) | E.t. | Nej |

### <a name="why-is-an-app-pin-policy-only-configured-for-android-devices"></a>Varför konfigureras en PIN-kodsprincip för appar enbart för Android-enheter?
Kryptering fungerar på olika sätt på iOS och Android.

För appar på iOS som associerats med en Intune MAM-princip krypteras data i vila med kryptering på enhetsnivå som tillhandahålls av operativsystemet. Så när du aktiverar appkrypteringsprincipen så kräver du också automatiskt att användaren måste ha och ange en PIN-kod för enheten att komma åt arbetsdata. Användare som inte redan har en enhet PIN-kod som konfigurerats på enheten uppmanas att skapa en PIN-kod för enheten.

För appar på Android som har associerats med en Intune MAM-princip krypteras data synkront under I/O-filaktiviteter. Innehållet i enhetens lagringsutrymme krypteras alltid. På enheter som inte är MDM-hanterade kan inte MAM-principen inte framtvinga några krav på en PIN-kod för enheten. Guiden aktiverar PIN-kodsprincipen så att du kan vara säker på att användarna uppmanas använda PIN-koder för att få åtkomst till arbetsdata.

Du kan alltid redigera dessa principinställningar så att de uppfyller organisationens krav.

### <a name="how-can-i-view-and-edit-the-policies-created-by-the-wizard"></a>Hur kan jag visa och redigera de principer som har skapats av guiden?
Om du vill visa eller uppdatera dessa principer eller alla de principer som du skapat i förhandsversionen av Intune Azure väljer du **Hantera appar** > **Appskyddsprinciper** på instrumentpanelen. Listan över principer öppnas till höger. Välj den princip som du vill använda för att visa och redigera inställningarna. <br/>
![Bild av användargränssnittets sökväg för att visa principer](./media/image-for-faq.png)

## <a name="next-steps"></a>Nästa steg
Läs mer om [appskyddsprinciper](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-protection-policy).



<!--HONumber=Feb17_HO1-->

