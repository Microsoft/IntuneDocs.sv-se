---
title: "Du får felmeddelanden när du försöker registrera din iOS-enhet i Intune | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58
ROBOTS: noindex
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0708fcca562a1547840c2a382c397265a0e46a44
ms.openlocfilehash: bd63e69f59c6e19aed92fc997f047cfe3f00717a


---


# Du får felmeddelanden när du försöker registrera din iOS-enhet i Intune

Följande tabell innehåller felmeddelanden som kan visas när du registrerar en iOS-enhet i Intune. Dela den här länken med din IT-administratör. Titta efter kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).

|Felmeddelande|Problem|Vad du ska berätta för din IT-administratör|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|Ingen registreringsprincip|Kontrollera att alla krav för registrering har konfigurerats, till exempel APNs-certifikatet och att ”iOS som en plattform” är aktiverat. Anvisningar finns i [Konfigurera iOS- och Mac-enhetshantering](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceCapReached|Du har för många registrerade mobila enheter.|För att kunna registrera en ny enhet måste användaren först ta bort en registrerad mobil enhet från företagsportalen. Se anvisningar för den typ av enhet som du använder: [Android](unenroll-your-device-from-intune-android.md), [iOS](unenroll-your-device-from-intune-ios.md), [Windows](unenroll-your-device-from-intune-windows.md).|
|APNSCertificateNotValid|Det är problem med det certifikat som gör det möjligt för den mobila enheten att kommunicera med företagets nätverk.<br /><br />Kontakta IT-administratörerna och berätta att du fått meddelandet **APNSCertificateNotValid** när du försökte registrera din mobila enhet. Be dem också ta en titt på lösningen i den här tabellen.|Apple Push-aviseringstjänsten (APNS) tillhandahåller en kanal som kan användas för att nå ut till registrerade iOS-enheter. Om alla steg för att erhålla ett APNS-certifikat inte utfördes, eller om APNS-certifikatet har upphört att gälla, misslyckas registreringsförsöket och det här meddelandet visas.<br /><br />Mer information om hur du konfigurerar användare finns i [Synkronisera Active Directory och lägga till användare i Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) och [Ordna användare och enheter](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|AccountNotOnboarded|Det är problem med det certifikat som gör det möjligt för den mobila enheten att kommunicera med företagets nätverk.<br /><br />Kontakta IT-administratörerna och berätta att du fått meddelandet **APNSNotOnboarded** när du försökte registrera din mobila enhet. Be dem också ta en titt på lösningen i den här tabellen.|Apple Push-aviseringstjänsten (APNS) tillhandahåller en kanal som kan användas för att nå ut till registrerade iOS-enheter. Om alla steg för att erhålla ett APNS-certifikat inte utfördes, eller om APNS-certifikatet har upphört att gälla, misslyckas registreringsförsöket och det här meddelandet visas.<br /><br />Mer information finns i [Konfigurera och iOS- och Mac-hantering med Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceTypeNotSupported|Du kan ha försökt att registrera en icke-iOS-enhet. Den typ av mobil enhet som du försöker registrera stöds inte.<br /><br />Kontrollera att enheten kör iOS version 7.1 eller senare.<br /><br />Kontakta IT-administratörerna och berätta att du fått meddelandet **DeviceTypeNotSupported** när du försökte registrera din mobila enhet. Be dem också ta en titt på lösningen i den här tabellen.|Kontrollera att användarens enhet kör iOS version 7.1 eller senare.|
|UserLicenseTypeInvalid|Du kan inte registrera din mobila enhet eftersom ditt användarkonto ännu inte är medlem i någon obligatorisk användargrupp.<br /><br />Kontakta IT-administratörerna och berätta att du fått meddelandet **UserLicenseTypeInvalid** när du försökte registrera din mobila enhet. Be dem också ta en titt på lösningen i den här tabellen.|Innan användarna kan registrera sina enheter måste de vara medlemmar i rätt användargrupp. Det här meddelandet anger att de har fel licenstyp för den angivna hanteringsauktoriteten för mobila enheter. Det här felet visas till exempel om Intune har angetts som utfärdare för hantering av mobila enheter och användarna har en licens för System Center 2012 R2 Configuration Manager.<br /><br />Läs följande om du vill ha mer information:<br /><br />Läs [Konfigurera iOS- och Mac-hantering med Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) och informationen om hur du konfigurerar användare i [Synkronisera Active Directory och lägga till användare i Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) samt [Ordna användare och enheter](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|MdmAuthorityNotDefined|IT-administratören måste konfigurera hur mobila enheter i ditt företag ska hanteras.<br /><br />Kontakta IT-administratörerna och berätta att du fått meddelandet **MdmAuthorityNotDefined** när du försökte registrera din mobila enhet. Be dem också ta en titt på lösningen i den här tabellen.|Utfärdaren för hantering av mobila enheter har inte angetts i Intune.<br /><br />Läs punkt 1 i avsnittet ”Steg 6: Registrera mobila enheter och installera en app” i [Kom igång med en 30-dagars utvärderingsversion av Microsoft Intune](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune).|

### Se även
[Using your iOS or Mac OS X device with Intune](using-your-ios-or-mac-os-x-device-with-intune.md)



<!--HONumber=Jul16_HO1-->


