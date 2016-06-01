---
# required metadata

title: Kommande nyheter | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 05/03/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Kommande nyheter i Microsoft Intune
Den här informationen omfattas av vårt sekretessavtal och tillhandahålls på ett ytterst begränsat sätt. Informationen kan komma att ändras. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta din Intune- eller PM-representant om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka då och då för nytillkommet innehåll.

Följande ändringar är under utveckling för Intune. Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## Introduktion av Meddelandecenter
Som en del av migreringen av Intune till [hanteringsportalen för Office 365](https://portal.office.com/) kommer vi att börja utnyttja Meddelandecenter för att informera om nya funktioner och annan kommunikation.  Genom att installera den medföljande mobilappen för Office 365-administratör kan du också ta emot meddelanden på din mobiltelefon och enkelt vidarebefordra meddelanden till användare eller ett distributionsalias.<br>  
Från och med majutgåvan kommer vi att börja använda Meddelandecenter för att meddela dig när uppdateringar är färdiga och för att publicera information om nya och förbättrade Intune-funktioner.  Kolla in Meddelandecenter redan nu genom att logga in på [hanteringsportalen för Office 365](https://portal.office.com/) och välja alternativet **MEDDELANDECENTER** i det vänstra navigeringsfönstret.
<!---TFS 1242782--->


## Apphantering
- **Villkorlig åtkomst för webbläsare.** Du kan skapa en princip för villkorlig åtkomst för Exchange Online och SharePoint Online så att programmen bara kan användas av hanterade och godkända iOS- och Android-enheter. Användare som försöker logga in till Outlook Web Access (OWA) och SharePoint-webbplatser med iOS- och Android-enheter uppmanas att registrera sina enheter med Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS 1175844--->

- **MAM SDK: Stöd för konfiguration av PIN-kodens längd.** Du kan ange längden på PIN-koden för MAM-appar på samma sätt som PIN-koden för en enhet. Detta innebär att slutanvändaren måste uppfylla de nya begränsningar som du anger. Användaren ser en lite annorlunda PIN-skärm som är anpassad till den längre inmatningen.
<!--- TFS 1104753--->

- **MAM-kontroller för att förhindra att Outlook-kontakter synkroniseras (iOS).** En ny inställning är tillgänglig för hantering av mobila program utan enhetsregistrering. Med den här inställningen kan Intune-administratören förhindra att ett program synkroniserar kontakter till den interna adressboken på iOS-enheter. När den här inställningen är aktiverad kan appen inte längre spara kontakter i den interna adressboken. När den här inställningen är inaktiverad kan appen spara kontakter i den interna adressboken. När en Intune-administratör rensar en enhet selektivt tas alla kontakter som redan har sparats i den interna adressboken bort. Den här nya inställningen stöds nu av Outlook-appen på iOS-enheter.
<!---TFS item 1276166--->

- **Skype för företag för Android.** Intune-administratörer kan nu välja att rikta MAM mot Skype för företag utan registreringsprinciper.  När användarna har loggat in tillämpas MAM-principerna.
<!--- TFS item 1248444 --->

- **Skype för företag för iOS.** Intune-administratörer kan nu välja att rikta MAM mot Skype för företag utan registreringsprinciper.  När användarna har loggat in tillämpas MAM-principerna.
<!--- TFS item 1248443 --->

### Stöd för Xamarin
Nu har Microsoft Intune App SDK stöd för Xamarin-appar i följande scenarier:

- När du skriver nya appar eller ändrar koden i befintliga affärsappar med hjälp av Intune SDK. Du kan hämta plugin-programmet på [Microsoft Intune-sidan på Github](https://github.com/msintuneappsdk).
- Lägga till stöd för MAM till befintliga affärsappar med hjälp av Intunes programhanteringsverktyg

Om du behöver hjälp med att välja metod läser du [Förbereda appar för hantering av mobilprogram med Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->


## Enhetshantering
- **Fjärrhjälpsessioner för Windows-datorer.** TeamViewer-integration för agenthanterade Windows-datorer innebär att du kan underlätta supportavdelningens arbete genom att upprätta fjärrhjälpsessioner med agenthanterade Windows-datorer. Detta gäller Windows 7, 8, 8.1 och Windows 10.
<!--- TFS 1284856--->


<!--- TFS item 1274326 --->

## Åtkomstkontroll
* **Skype för företag – Online stöder villkorlig åtkomst.** Intune-administratörer kan skapa en princip för villkorlig åtkomst för Skype för företag – Online så att programmet bara kan användas av hanterade och kompatibla iOS- och Android-enheter. Användare som försöker logga in i mobilappen för Skype för företag på iOS och Android uppmanas att registrera sig i Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS item 1254499--->

## Företagsportal
* **En banderoll för enhetsidentifikation ger mer information till slutanvändaren.** Slutanvändarna kan enkelt identifiera den enhet de valt när de använder företagsportalens webbplats. Om fel enhet har valts kan de välja rätt enhet genom att trycka på länken ”Tryck här” på banderollens startsida.
<!--- TFS 1231157--->

* **Windows-appaket är tillgängliga direkt från företagsportalen**: Användare av Windows 8-, Windows 8.1- och Windows RT-datorer kan nu installera Windows-appaket (med filtillägget .appx) direkt från företagsportalens webbplats. Tidigare var Intune-administratörerna tvungna att sköta distributionen eller så var användarna tvungna att installera företagsportalappen på sina enheter för att installera appar.
<!--- TFS item 1082481 --->

* **Användare kan fjärrlåsa sina enheter från företagsportalen** Ett nytt alternativ för fjärrlåsning har lagts till på företagsportalens webbplats så att användarna kan fjärrlåsa sina enheter från portalen om de tappar bort enheten eller om den blir stulen. Följande tabell visar plattformsstödet för fjärrlåsning för Intune och Intune med Configuration Manager.
<!--- TFS item 1195661 --->

|Plattform  |Information om stöd|
|---------|---------|
|iOS | Stöds|
|Android | Stöds|
|Windows Phone 8.1 | Stöds|
|Windows 10 Mobil | Stöds endast om telefonen har ett konfigurerat lösenord|
|PC (Windows 8.0 och tidigare) | Stöds inte|
|PC (Windows 8.1) | Stöds inte|
|Windows Phone 8.0 | Stöds inte|
|Windows 10 Desktop | Stöds inte|

## Tjänstens utfasning
* **Borttagning av anpassade meddelanderegler för specifika grupper.** Från början av juni 2016 kommer du inte längre att kunna använda guiden Skapa meddelanderegel för att tillämpa meddelanderegler på specifika användarskapade grupper.

    För närvarande, om du vill rikta in dig på en viss användardefinierad grupp, väljer du **Admin** > **Meddelanderegler** > **Skapa ny regel** från Microsoft Intune Administrationskonsol. I steg två i guiden Skapa meddelanderegel måste du välja de enhetsgrupper som regeln ska tillämpas på. Det här steget, **Välj enhetsgrupper**, håller på att fasas ut från Intune-konsolen.

    **Välj enhetsgrupper** stöds inte efter 1606-versionen i juni av Intune. Dock visas alternativet fram till augusti 2016. Efter augusti börjar vi fasa ut våra klientorganisationer till den nya upplevelsen under en tvåmånadersperiod. Alla befintliga kunder bör ha gått över till den nya miljön senast i oktober 2016. När du har migrerat till den nya miljön visas inte längre alternativet för att tillämpa meddelanderegler på en viss grupp.
<!---   TFS 1278864--->







### Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).


<!--HONumber=May16_HO1-->


