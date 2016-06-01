---
# required metadata

title: Nyhetsarkiv | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


## September 2015
### Uppdateringar för mobil enhet och apphantering
Nu har alla Intune-hanteringsfunktioner för iOS stöd för iOS 9

Mer information om hanteringsfunktioner för iOS 9 finns i [det här blogginlägget](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx) Ny konfigurationsprincip för mobilappar för iOS Använd den nya konfigurationsprincipen för mobilappar för att automatiskt ange inställningar som en iOS-app kan behöva när den körs.

Du kan till exempel ange en nätverksport eller ett användarnamn. Mer information finns i [Konfigurera appar med konfigurationsprinciper för mobilappar i Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx)

 Enklare apphantering för iOS 9-användare

 I den här versionen kan iOS 9-användare hantera appar som redan distribuerats i Intune.

 När det gäller tidigare versioner av iOS måste du fortfarande be användaren att avinstallera appen manuellt innan den hanterade appen kan installeras i Intune om du distribuerar en app och det redan finns en ohanterad version av appen på enheten. Men från och med den här versionen av Intune kan du be användare av iOS 9-enheter att tillåta att Intune tar över hanteringen av appen och tillämpar relevanta hanteringsprinciper för mobilprogram.

### **Windows 10-hantering** Använd den nya [allmänna konfigurationsprincipen för Windows 10](https://technet.microsoft.com/library/mt404697.aspx) för att konfigurera lösenord, enhet, webbläsare och andra inställningar för registrerade enheter som kör Windows 10 och Windows 10 Mobile.
**Skapa och distribuera appar till registrerade Windows 10-enheter** Med den nya programinstallationstypen Windows Installer via MDM (&#42;.msi) kan du skapa och distribuera Windows Installer-appar till registrerade enheter som kör Windows 10.

**Mer information finns i [Kom igång med appdistribution i Microsoft Intune](https://technet.microsoft.com/library/dn646955.aspx)**
* Ändringar och uppdateringar för appar i Microsofts företagsportal Följande ändringar har gjorts för företagsportalens appar i den här versionen:
* iOS
* Microsoft samlar automatiskt in anonymiserade data om prestanda och användning av företagsportalen för att kunna förbättra Microsofts produkter och tjänster.

### Slutanvändare kan inaktivera datainsamling med inställningen Användningsdata på sin enhet, men administratörer har ingen kontroll över datainsamlingen och kan inte ändra slutanvändarens val för den här inställningen.
**Fullständig skärmupplösningsstöd på iPhone 6 och 6 Plus**

|Felkorrigeringar för ökad säkerhet|Nyheter i Intune-dokumentation – september 2015|
|----|--------|
|[Nya frågor](https://technet.microsoft.com/library/mt404697.aspx)|Namn
| [Information](https://technet.microsoft.com/library/mt481447.aspx)|Inställningar för Windows 10-konfigurationsprinciper i Microsoft Intune |

**Det här är en ny konfigurationsprincip med vilken du kan hantera inställningar och funktioner på enheter som kör Windows 10 och Windows 10 Mobile.**

|Konfigurera appar med konfigurationsprinciper för mobilappar i Microsoft Intune|Detta är en ny principtyp som medför att du automatiskt kan tillhandahålla inställningar  som kan krävas när användaren kör en iOS-app.|
|----|-------|
|[Uppdaterade avsnitt](https://technet.microsoft.com/library/dn743712.aspx)|Namn|

## Information
### Använda principer för att hantera datorer och mobila enheter med Microsoft Intune
* Uppdaterad med den senaste informationen för att hjälpa dig att förstå och skapa principer. Augusti 2015 Uppdateringar för mobil enhet och apphantering **Villkor** för Intune-registrering och företagsåtkomst hanteras [nu med principer](https://technet.microsoft.com/library/mt405893.aspx).
* Du kan ha olika uppsättningar med villkor för att uppfylla specifika användargruppskrav. Du kan till exempel distribuera villkor på olika språk till geografiskt definierade användargrupper.
* Du kan också [redigera dina villkor](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) och ange om du vill öka versionsnumren, vilket kräver att användarna accepterar de nya villkoren innan de kan använda företagsportalen. **Flera Intune-principer har döpts om** så att de blir mer konsekventa i produkten och enklare att hitta. En lista över alla tillgängliga Intune-principer finns i [Använda principer för att hantera datorer och mobila enheter med Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx)
* **PKCS #12-certifikatprofiler (.PFX)** finns för Android 4.0 eller nyare och Windows 10 (Desktop och Mobile) och senare.
* .PFX kräver inte en NDES-server. Lär dig hur du använder PFX-certifikatprofiler i [Ge åtkomst till företagsresurser med hjälp av certifikatprofiler med Microsoft Intune](http://technet.microsoft.com/library/dn818904.aspx)
* **Inställningar för Företagsgränser för Windows 10 Desktop och Mobile** stöder detaljerade VPN-inställningar, vilket förklaras i [Hjälp användarna att ansluta till sitt arbete med hjälp av VPN-profiler](https://technet.microsoft.com/library/dn818905.aspx) **OneDrive-appen för Android stöder nu flera identiteter**. Mer information om den här och andra uppdateringar av hanteringsprinciperna för mobila appar finns i [listan över Microsoft-program som du kan hantera](https://technet.microsoft.com/library/dn708489.aspx) **Kringgå iOS-aktiveringslåset**.

### Om företagsägda iOS-enheter skyddas av aktiveringslås, måste du fylla i användarens Apple-ID och -lösenord innan du kan radera eller återaktivera enheten.
Det kan skapa utmaningar om en medarbetare lämnar företaget och lämnar in en företagsägd enhet utan att slå av aktiveringslåset. Du kan åtgärda det här problemet genom att använda [förbikoppling av aktiveringslås i Intune](https://technet.microsoft.com/library/mt414176.aspx).
Villkorlig åtkomst för datorer
* Du kan nu konfigurera villkorliga åtkomstprinciper för datorer.
* Detta medför att Offices skrivbordsappar kan få åtkomst till Exchange Online- och SharePoint Online-tjänster.
* Om du vill aktivera en villkorlig åtkomstprincip för datorer, måste datorn vara domänansluten eller följa reglerna.

### Den fullständiga listan med krav för att aktivera villkorlig åtkomst för PC-datorer finns i avsnittet **Komma igång** i [Hantera åtkomst till e-post och SharePoint med Microsoft Intune](http://technet.microsoft.com/library/dn818907).aspx).
Information om vilka alternativ du kan välja om du vill aktivera villkorlig åtkomst för e-post finns i [Hantera email åtkomst med Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx).

**Information om vilka alternativ du kan välja om du vill aktivera villkorlig åtkomst för SharePoint Online finns i [Hantera SharePoint onlineåtkomst med Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx).**

Ändringar och uppdateringar för appar i Microsofts företagsportal

### Följande ändringar har gjorts för företagsportalens appar i den här versionen:
**Android**

|Användarna visas nu anvisningar för enhetsregistrering efter att du har loggat in, om de inte ännu har registrerat sin enhet för hantering.|Nyheter i Intune-dokumentationen – augusti 2015|
|-----|-------|
|[Nya frågor](https://technet.microsoft.com/library/mt414176.aspx)|Titel|

**Information**

|Skydda iOS-enheter med Kringgå Aktiveringslås för Microsoft Intune|Läs mer om hur du kan använda Intune för att kringgå iOS-aktiveringslås när en användare lämnar företaget och returnerar en låst enhet.|
|-----|-------|
|[Uppdaterade avsnitt](https://technet.microsoft.com/library/dn708489.aspx)|Titel
|[Information](http://technet.microsoft.com/library/dn743712.aspx)|Microsoft-appar som du kan använda med Microsoft Intunes hanteringsprinciper för mobilprogram|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->


<!--HONumber=May16_HO2-->


