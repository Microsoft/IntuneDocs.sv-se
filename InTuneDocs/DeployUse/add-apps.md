---
# required metadata

title: Lägg till appar | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Lägg till appar med Microsoft Intune
Innan du börjar distribuera appar med Microsoft Intune är det bra om du bekantar dig med de olika begreppen i det här avsnittet. Det hjälper dig att förstå vilka appar som du kan distribuera till vilken plattform och förstå de krav som måste vara uppfyllda innan du gör det.

## Apptyper som du kan distribuera med Intune
Du kan distribuera appar till alla enhetstyper som stöds av Intune. Processen och vilka enheter som stöds varierar beroende på vilken typ av app du distribuerar. Använd dig av följande information för att få hjälp att förstå vad som går respektive inte går att distribuera:


### **Windows Installer (&#42;.exe, &#42;.msi)**
- Den här typen av app måste ha stöd för obevakad installation utan användarindata. Dokumentationen till din app ska innehålla relevanta kommandoradsalternativ för obevakad installation av appen (t.ex. **/q**). En lista över vanliga kommandoradsalternativ finns [här](https://support.microsoft.com/en-us/kb/227091).
- Alla eventuella ytterligare filer och mappar som krävs av appens installationsprogram måste vara tillgängliga från den plats som du anger för appens installationsfiler.
- I de flesta fall kräver inte Windows Installer-filer (.msi) eller Windows Installer Patch-filer (.msp) några kommandoradsargument för att kunna installeras av Intune. Läs dokumentationen till din app. Om det krävs kommandoradsargument måste de anges som Name=Value pairs (t.ex. TRANSFORMS=custom_transform.mst).

Den här typen av app överförs till ditt molnlagringsutrymme.
### **Appaket för Android (&#42;.apk-fil)**
Den här typen av app överförs till ditt molnlagringsutrymme.
### **Appaket för iOS (&#42;.ipa-fil)**
- Om du vill distribuera iOS-appar måste du ha ett giltigt IPA-paket.
- IPA-paketet måste ha signerats av Apple och det utgångsdatum som anges i etableringsprofilen måste vara giltigt. Intune kan distribuera iOS-appar med företagscertifikat Inte alla Apple-utvecklarcertifikatsappar stöds.
- Ditt företag måste vara registrerat för iOS Developer Enterprise-programmet.
- Kontrollera att din organisations brandvägg tillåter åtkomst till iOS-etablerings- och certifieringswebbplatserna.
- En manifestfil (.plist) måste inte distribueras med appen.

Den här typen av app överförs till ditt molnlagringsutrymme.

För närvarande kan slutanvändare inte installera företagsappar från Intune-företagsportalappen för iOS. Det beror på begränsningar för appar som publiceras i iOS App Store (se [App Stores riktlinjer för granskning](https://developer.apple.com/app-store/review/guidelines/)). Användarna får åtkomst till företagsappar (inklusive hanterade App Store-appar och paket med branschanpassade appar) genom att starta företagsportalsappen på sin enhet och peka på Företagsappar, vilket öppnar webbläsaren och omdirigerar dem till Intunes webbportal.

### **Appaket för Windows Phone (&#42;.xap, .appx, .appxbundle)**
- För att kunna distribuera appar behöver du ett företagskodsigneringscertifikat för mobila enheter. Mer information finns i [Konfigurera hantering av Windows Phone med Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md).

Den här typen av app överförs till ditt molnlagringsutrymme.

Nedan finns information om hur du installerar affärsappar för UWP med Intune.

### **Windows-app-paket (.appx, .appxbundle)**
- För att kunna distribuera appar behöver du ett företagskodsigneringscertifikat för mobila enheter. Mer information finns i [Konfigurera hantering av Windows-enheter med Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).

Den här typen av app överförs till ditt molnlagringsutrymme.
### **Windows Installer via MDM (&#42;.msi)**
Med den här installationstypen kan du skapa och distribuera Windows Installer-baserade appar till registrerade datorer som kör Windows 10.<br /><br />Följande gäller när du använder den här installationstypen:
- Du kan bara ladda upp en enstaka fil med filnamnstillägget .msi.
- Filens produktkod och produktversion används för appidentifiering.
- Appens standardbeteende för omstart används. Intune styr inte det här.
- MSI-paket per användare installeras för en enskild användare.
- MSI-paket per dator installeras för alla användare på enheten.
- MSI-paket för dubbla lägen kan för närvarande bara installeras för alla användare på enheten.
- Appuppdateringar stöds om MSI-produktkoden för respektive version är densamma.

Den här typen av app överförs till ditt molnlagringsutrymme.
### **Extern länk**
Används när du har en
- **URL** som låter användarna ladda ned en app från en appbutik.
- **Länk** till en webbaserad app som körs från webbläsaren.

Appar som är baserade på externa länkar lagras inte i Intune-molnlagringsutrymmet.
### **Hanterade iOS-appar från App Store**
Du kan hantera och distribuera kostnadsfria iOS-appar från App Store. Det gör det också möjligt att koppla [hanteringsprinciper för mobila program](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) med [kompatibla appar](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) och granska deras status i administratörskonsolen.<br /><br />Hanterade iOS-appar lagras inte i ditt Intune-molnlagringsutrymme.
> [!TIP] Alternativen för mobila enheter är inte tillgängliga förrän du [ställer in hanteringsutfärdaren för mobila enheter](get-ready-to-enroll-devices-in-microsoft-intune.md) på Intune.

## Stöd för UWP-appar (Universal Windows Platform)
Windows 10-datorer kräver inte en nyckel för att installera branschspecifika appar. Dock måste registernyckeln **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** ha värdet **1** för att aktivera separat inläsning.

Om registernyckeln inte är konfigurerad ställer Intune automatiskt in värdet på **1** första gången du distribuerar en app till enheten. Om det här värdet har angetts till **0** kan inte Intune automatiskt ändra värdet och distributionen av affärsappar kommer att misslyckas.

Affärsappar för UWP måste vara signerade med ett kodsigneringscertifikat som är betrott på varje enhet där appen har distribuerats. Du kan använda certifikat från en egen PKI-infrastruktur eller ett certifikat från offentliga rotcertifikat från tredje part som har installerats på enheten.

På Windows 10 Mobile-enheter kan du använda ett icke-Symantec-kodsigneringscertifikat för att logga universella **.appx**-appar. För **.xap**-appar och även **.appx**-paket som skapats för Windows Phone 8.1 som du vill installera på Windows 10 Mobile-enheter måste du använda ett Symantec-kodsigneringscertifikat.

## Nästa steg 

Därefter måste du lägga till appar i Intune-konsolen innan du kan distribuera dem. Du kan lägga till appar för [registrerade enheter](add-apps-for-mobile-devices-in-microsoft-intune.md) eller för [Windows-datorer som du hanterar med Intune-klientprogrammet](add-apps-for-windows-pcs-in-microsoft-intune.md).

<!--HONumber=Jun16_HO2-->


