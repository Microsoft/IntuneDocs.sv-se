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
ms.openlocfilehash: 2f698f03ed3c7523ef1d768d2a1361d6d1a55008
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883877"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>Registrera enheten för åtkomst till arbets-eller skol resurser
Om du vill registrera din enhet och få åtkomst till e-post och appar måste du installera antingen appen Intune-företagsportal eller Microsoft Intune. När du registrerar, tillämpas de grundläggande hanterings principerna som din organisation har konfigurerat, till exempel lösen ord, PIN-kod och kryptering, på din enhet. När enhets inställningarna uppfyller alla organisationens krav kan du på ett säkert sätt komma åt din arbets information från i princip var som helst.  

Företagsportal-och Microsoft Intune-apparna låter din registrerade enhet vara säker genom att se till att enhets inställningarna matchar organisationens principer. 

Företagsportalsappen gör även följande:  
* Håller din personliga och arbetsrelaterade information separat.  
* Gör det enkelt att hitta och installera relevanta appar för arbete och skola.   

## <a name="get-the-apps"></a>Hämta apparna
Så här skaffar du företagsportalen:

- Installera Företagsportal-appen från det plattformsspecifika App Store. I vissa fall kommer din organisation att installera Företagsportal-appen åt dig.  
- Gå till [företagsportal webbplats](https://go.microsoft.com/fwlink/?linkid=2010980) för att få åtkomst till appen från en webbläsare.  

Om du måste använda Microsoft Intune-appen kommer din organisation att installera den åt dig.  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>Vilken information kan företaget se när jag registrerar mig?
När enheten har registrerats kan organisationens support personer bara se information som är relevant för arbetet. De kan inte se någon personlig information. Om du registrerar en personlig enhet för användning i arbetet kan du [läsa mer om vad som kan och inte kan visas](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>Vad är skillnaden mellan apparna och webbplatsen?
Företagsportal-appen är tillgänglig för Windows 10-, iOS-, macOS-och Android-enheter. Den integreras sömlöst med enhetens respektive plattform. Webbplatsversionen är tillgänglig på valfri enhet och du får samma, universella miljö oavsett vilken enhet du använder. 

Microsoft Intune-appen är för företagsägda Android-enheter.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>Vilken typ av enheter kan du registrera med Företagsportal?
- Apple-enheter som använder iOS (som iPhone och iPad) och macOS (som MacBook och iMac)
- Android-enheter:
- Windows-enheter
  - Windows 10 Mobil
  - Windows 10 Desktop
  - Windows Phone 8.1
  - Windows 8,1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Vilken typ av enheter kan du registrera med Microsoft Intune-appen?  
Du kan registrera företagsägda Android-enheter som din organisation har konfigurerat för användning med appen. Appen stöder Android 6,0 och senare. 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>Kan du ta bort en dator eller enhet från företagsportalen?
Du kan ta bort eller återställa en dator eller enhet på företagsportalen. Det är skillnad mellan att **ta bort** och att **återställa**.

När du tar bort en dator eller enhet från företagsportalen avregistrerar du enheten från Intune. När du tar bort en dator eller enhet har du inte längre åtkomst till företagsportalen från den enheten och viss företagsinformation kan tas bort från enheten. Information om hur du tar bort enheten från Företagsportal finns i följande länkar:  

- [Avregistrera din Android-enhet](unenroll-your-device-from-intune-android.md)
- [Avregistrera din iOS-enhet](unenroll-your-device-from-intune-ios.md)
- [Avregistrera din macOS-enhet](unenroll-your-device-from-intune-macos.md)
- [Avregistrera din Windows-enhet](unenroll-your-device-from-intune-windows.md)

När du återställer en dator eller enhet försöker företagsportalen att återställa datorn eller enheten till tillverkarens standardinställningar. Om du återställer enheten tas alla företagsdata och personliga data bort från enheten. Om du har blivit av med enheten kan du även fjärråterställa den från företagsportalens webbplats.  

Information om hur du återställer din enhet finns i [återställa enheten från företagsportal webbplats](reset-erase-your-device-cpwebsite.md).  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>Kan du ta bort en dator eller enhet från Microsoft Intune-appen?
Nej, du kan inte ta bort en enhet som ägs av företaget från Microsoft Intune-appen.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>Vad händer om jag inte kan se min enhet i Företagsportal-eller Microsoft Intune-appen?
För att se en enhet måste du först lägga till den i företagsportalen. Gå till den företagsportal som administratören har rekommenderat och följ anvisningarna för din enhet. Enheter som ägs och hanteras av ditt företag visas inte.

Om du använder Microsoft Intune-appen ser du bara den enhet som du använder just nu. Andra registrerade enheter visas inte i appen.  

## <a name="where-else-can-i-go-for-help"></a>Var finns ytterligare hjälp?  
Information om hur du felsöker vanliga problem och frågor finns i plattforms oberoende dokument:  

- [Åtgärda vanliga problem med din Android-enhet](check-compliance-on-your-device-android.md)  
- [Åtgärda vanliga problem med din iOS-enhet](troubleshoot-your-device-ios.md)
- [Åtgärda vanliga problem med din macOS-enhet](troubleshoot-your-device-macos.md)
- [Åtgärda vanliga problem med din Windows-enhet](troubleshoot-your-device-windows.md)

Du kan också kontakta din support person. Företagsportal-och Microsoft Intune-appen erbjuder hjälp-och support sidor som visar kontakt information och sätt att rapportera ett problem. Kontakt information finns också på din organisations [företagsportal webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="next-steps"></a>Nästa steg  

Få hjälp med att börja med registreringen, som är speciell för enhetens plattform:  

- [Använda din Android-enhet](using-your-android-device-with-intune.md)
- [Använda en iOS-enhet](using-your-ios-device-with-intune.md)
- [Använda en macOS-enhet](using-your-macos-device-with-intune.md)
- [Använda din Windows-enhet](using-your-windows-device-with-intune.md)
- [Använda företagsportalswebbplatsen](using-the-intune-company-portal-website.md)


