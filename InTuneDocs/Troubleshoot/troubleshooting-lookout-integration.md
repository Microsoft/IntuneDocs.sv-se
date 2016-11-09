---
title: "Felsöka Lookout-integrering | Microsoft Intune"
description: "I det här avsnittet beskrivs felsökning av problem som ofta uppstår vid Lookout-integrering"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0736b5f24065f55d8fbd312395e4bb7226ebf619
ms.openlocfilehash: 5acf5c707a93aa0b5e7cefdcb0b160af09b9cf70


---

# Felsöka Lookout-integrering med Intune
Det här avsnittet beskriver några vanliga problem som kan uppstå vid installation av Lookout mobilt skydd (MTP).
## Felsöka inloggning
### 403-fel
Du kan få ett 403-fel när du loggar in i [Lookout MTP-konsolen](https://aad.lookout.com):  **you are not authorized to access the service** (du har inte åtkomsträttigheter till den här tjänsten). Detta kan hända när användarnamnet som du angav inte är medlem i Azure Active Directory (Azure AD)-gruppen som är konfigurerad för att ha åtkomst till Lookout MTP.

Lookout MTP är konfigurerat så att endast användare från en konfigurerad Azure AD-grupp har åtkomst. Om du är osäker på vilken grupp som är konfigurerad att ha åtkomst till Lookout MTP kontaktar du Lookout-supporten.

Du kan kontakta Lookout-supporten på följande sätt:

* E-post: enterprisesupport@lookout.com
* Logga in på [MTP Console](http://aad.lookout.com) (MTP-konsolen), och gå till **support**-modulen.
* Gå till: https://enterprise.support.lookout.com/hc/en-us/requests och fyll i en supportförfrågan.

### Det går inte att logga in
Du kan få följande fel när den globala Azure AD-administratöranvändaren inte har accepterat den inledande Lookout-installationen.

![skärmbild av inloggningsskärmen för Lookout som visar inloggningsfelet](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

För att lösa problemet måste en global administratör logga in på https://aad.lookout.com/les?action=consent och acceptera uppmaningen att starta installationen. Mer information finns i avsnittet [Set up your subscription with Lookout MTP](set-up-your-subscription-with-lookout-mtp.md) (Konfigurera din prenumeration med Lookout MTP)

## Felsöka problem med enhetsstatus

### Enheten visas inte i listan över enheter i Lookout MTP-konsolen

Detta kan inträffa i något av följande scenarier:
* När användaren som äger den här enheten inte är i **Enrollment Group** (Registreringsgruppen) som anges i **Lookout MTP Console** (Lookout MTP-konsolen).  Gå till **Intune Connector**-fliken i **System**-modulen och titta på inställningarna för **Enrollment Management** (Registreringshantering).  Du bör se en eller flera Azure AD-grupper som konfigurerats för registrering.  Kontrollera att den användare som äger den saknade enheten är medlem i en av de angivna Azure AD-grupperna.  När en ny användare har lagts till i registreringsgruppen tar det upp till det konfigurerade avsökningsintervallet (standardinställningen är fem minuter) innan enheten visas i **Enheter**-modulen i Lookout MTP-konsolen.

* Om enheten inte stöds av Lookout MTP.  Enheter som inte stöds kommer visas i sektionen **Hanterade enheter** under anslutningsinställningarna i Lookout MTP-konsolen.

### Enheterna fortsätter att rapporteras som **väntar**

Att en enhet visar **väntar** betyder att användaren inte har öppnat Lookout for work-appen och tryckt på knappen **Aktivera**. Läs följande avsnitt för mer information om enhetsaktivering med Lookout for work-appen:

[Du uppmanas att installera Lookout for Work på din Android-enhet ](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### En enhet visas som aktiv, men har inte ett enhets-ID i Lookout MTP-konsolen.  
Det betyder att användaren som äger den här enheten inte är i registreringsgruppen som anges i Lookout MTP-konsolen.   En enhet kan hamna i det här tillståndet om användaren som äger enheten har tagits bort från registreringsgruppen eller om registreringsgruppen som användaren tillhör har tagits bort.

Gå till **Intune Connector**-fliken i **System**-modulen i Lookout MTP-konsolen och se över inställningarna för **Registrering**.  Du bör se en eller flera Azure AD-grupper som konfigurerats för registrering.  Kontrollera att den användare som äger enheten är medlem i en av de angivna Azure AD-grupperna.  

När en enhet är i det här tillståndet kan Lookout fortsätter att meddela användaren om eventuella hot som identifieras, men det skickar inte någon information om hotet till Intune.

### Enheten visar frånkopplat tillstånd

Frånkopplad innebär att Lookout MTP inte har hört från enheten under ett förinställt tidsintervall (standardvärdet är 30 dagar med lägst 7 dagar). Det innebär antingen att företagsportalappen eller Lookout for Work-appen inte har installerats på enheten eller har avinstallerats. Att installera om apparna bör lösa problemet. När användaren öppnar Lookout for Work och aktiverar appen synkroniseras enheten med Lookout MTP och Intune igen.    

### Tvinga fram synkronisering på enheten
Administratören kan välja enheten och välja att ta bort den från **Enheter**-modulen i Lookout MTP-konsolen.   Nästa gång ägaren till enheten öppnar Lookout for Work-appen och trycker på **Aktivera** kommer enhetens tillstånd att göra en fullständig synkronisering.

### Ägaren till enheten använder inte längre den här enheten
Du måste rensa enheten och be den nya användaren att registrera sig.  Markera enheten, högerklicka och välj **Ta bort/Rensa** i [Intune-administratörskonsolen](https://manage.microsoft.com) för att ta bort enheten från hanteringen. När du har tagit bort enheten kan du radera den.

![skärmbild som visar enhetsmodulen i Intune-administratörskonsolen och alternativet Ta bort/Rensa](../media/mtp/mtp-retire-device-intune-console.png)

Du kan även gå till **Enheter**-modulen i Lookout MTP-konsolen och välja **Ta bort**.  

Så länge som den nya användaren är i en av registreringsgrupperna som angetts i Lookout MTP-konsolen kommer enheten att visas när Azure AD kopplar enheten till den nya användaren.

## Arbetsflöden för reparation av efterlevnadsproblem
[Du uppmanas att installera Lookout for Work på din Android-enhet]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[Du måste åtgärda ett hot som Lookout for Work har hittat på din Android-enhet ](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)


### Se även
[Konfigurera din prenumeration med Lookout MTP](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-your-subscription-with-lookout-mtp)



<!--HONumber=Oct16_HO1-->


