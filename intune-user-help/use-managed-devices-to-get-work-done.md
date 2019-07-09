---
title: Använda hanterade enheter för att få arbetet gjort | Microsoft Docs
description: Förstå vad det innebär att registrera en enhet för hantering med Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2c0d3484311d044842daf6718b306d45fc93edf2
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545934"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>Registrera enheten för åtkomst till arbetsplats eller skola resurser
Om du vill registrera din enhet och få åtkomst till e-post och appar, måste du att installera företagsportalappen eller Microsoft Intune app. När du registrerar som de grundläggande hantering-principer som din organisation har konfigurerat, till exempel lösenord, PIN-kod och kryptering, används för din enhet. När dina Enhetsinställningar uppfyller alla krav för din organisation, kan du få säker åtkomst till din arbetsinformation från nästan var som helst.  

Apparna företagsportal och Microsoft Intune skydda den registrerade enheten genom att se till att dina Enhetsinställningar matchar din organisations principer. 

Företagsportalsappen gör även följande:  
* Håller din privat och Arbetsrelaterad information separat.  
* Gör det enkelt att hitta och installera relevanta arbete och skola appar.   

## <a name="get-the-apps"></a>Hämta appar
Så här skaffar du företagsportalen:

- Installera företagsportalappen från plattformsspecifika app store. I vissa fall kan installerar din organisation företagsportalappen åt dig.  
- Gå till den [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980) få åtkomst till appen från en webbläsare.  

Om du blir ombedd att använda Microsoft Intune-appen, installera din organisation det åt dig.  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>Vilken information kan företaget se när jag registrerar mig?
När enheten har registrerats kan din organisation support personer endast att se information som är relevant för arbetet. De kan inte se någon personlig information. Om du registrerar en personlig enhet för användning i arbetet, [mer exakt vad som kan och inte kan ses](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>Vad är skillnaden mellan apparna och webbplatsen?
Företagsportalappen är tillgänglig för Windows 10, iOS, macOS och Android-enheter. Det integreras sömlöst med din enhet respektive plattform. Webbplatsversionen är tillgänglig på valfri enhet och du får samma, universella miljö oavsett vilken enhet du använder. 

Microsoft Intune-appen är för företagsägda Android-enheter.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>Vilka typer av enheter kan du registrera med Företagsportalen?
- Apple-enheter som använder iOS (som iPhone och iPad) och macOS (som MacBook och iMac)
- Android-enheter:
- Windows-enheter
    - Windows 10 Mobil
    - Windows 10 Desktop
    - Windows Phone 8.1
    - Windows 8,1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Vilka typer av enheter kan du registrera med Microsoft Intune app?  
Du kan registrera företagsägda Android-enheter som din organisation har konfigurerat för att använda med appen. Appen har stöd för Android 6.0 och senare. 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>Kan du ta bort en dator eller enhet från företagsportalen?
Du kan ta bort eller återställa en dator eller enhet på företagsportalen. Det är skillnad mellan att **ta bort** och att **återställa**.

När du tar bort en dator eller enhet från företagsportalen avregistrerar du enheten från Intune. När du tar bort en dator eller enhet har du inte längre åtkomst till företagsportalen från den enheten och viss företagsinformation kan tas bort från enheten. Lär dig hur du tar bort enheten från Företagsportalen, se följande länkar:  

- [Avregistrera din Android-enhet](unenroll-your-device-from-intune-android.md)
- [Avregistrera din iOS-enhet](unenroll-your-device-from-intune-ios.md)
- [Avregistrera din macOS-enhet](unenroll-your-device-from-intune-macos.md)
- [Avregistrera din Windows-enhet](unenroll-your-device-from-intune-windows.md)

När du återställer en dator eller enhet försöker företagsportalen att återställa datorn eller enheten till tillverkarens standardinställningar. Om du återställer enheten tas alla företagsdata och personliga data bort från enheten. Om du har blivit av med enheten kan du även fjärråterställa den från företagsportalens webbplats.  

Läs hur du återställer din enhet i [återställa en enhet från Företagsportalens webbplats](reset-erase-your-device-cpwebsite.md).  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>Kan du ta bort en dator eller enhet från Microsoft Intune app?
Nej, det går inte att ta bort företagsägda enheter från Microsoft Intune app.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>Vad händer om jag kan inte se min enhet i appen företagsportal eller Microsoft Intune?
För att se en enhet måste du först lägga till den i företagsportalen. Gå till den företagsportal som administratören har rekommenderat och följ anvisningarna för din enhet. Enheter som ägs och hanteras av ditt företag visas inte.

Om du använder Microsoft Intune app, visas bara den enhet som du använder just nu. Andra registrerade enheter kan inte synliga för dig i appen.  

## <a name="where-else-can-i-go-for-help"></a>Var finns ytterligare hjälp?  
Kolla in dessa plattformsspecifika docs för att felsöka vanliga problem och frågor:  

- [Åtgärda vanliga problem med din Android-enhet](check-compliance-on-your-device-android.md)  
- [Åtgärda vanliga problem med din iOS-enhet](troubleshoot-your-device-ios.md)
- [Åtgärda vanliga problem med din macOS-enhet](troubleshoot-your-device-macos.md)
- [Åtgärda vanliga problem med din Windows-enhet](troubleshoot-your-device-windows.md)

Du kan också kontakta supporten. Företagsportalen och Microsoft Intune app erbjuda hjälp och stöd för sidor som listar kontaktinformation och sätt att rapportera ett problem. Kontaktuppgifter finns också på din organisations [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="next-steps"></a>Nästa steg  

Få den hjälp som börjar med registreringen, som är specifik för din enhetsplattform:  

- [Använda din Android-enhet](using-your-android-device-with-intune.md)
- [Använda en iOS-enhet](using-your-ios-device-with-intune.md)
- [Använda en macOS-enhet](using-your-macos-device-with-intune.md)
- [Använda din Windows-enhet](using-your-windows-device-with-intune.md)
- [Använda företagsportalswebbplatsen](using-the-intune-company-portal-website.md)


