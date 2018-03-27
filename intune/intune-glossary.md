---
title: Microsoft Intune-ordlista
titleSuffix: Microsoft Intune
description: Lär dig innebörden av den terminologi som används i Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 07/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bd7b5613-ee9f-4dc3-990c-ab4c1d40720d
ms.custom: intune-azure
ms.openlocfilehash: f5f413ed050bd5f5620d0e15d5584a7db06eaaff
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="microsoft-intune-glossary"></a>Microsoft Intune-ordlista
Läs om definitionerna av vanliga termer som används i Microsoft Intune.

## <a name="a"></a>A

|||
|-|-|
|Apptilldelning|Låter användare [hitta, ladda ned och installera](/intune/app-management) de appar de behöver. Detta kallades tidigare för *appdistribution*.|
|Appkonfigurationsprofil <br/><br/>Appkonfigurationsprincip|Tillgänglig för mobilappar med leverantörsspecifika konfigurationer. Konfigurerar en [iOS](/intune/app-configuration-policies-use-ios)- eller [Android](/intune/app-configuration-policies-use-android)-app med specifika inställningar innan den körs.|
|Appövervakning|Låter dig [granska senaste status och aktivitet](/intune/apps-monitor) relaterad till apptilldelning.|
|Borttagningsåtgärd för appskyddsdata|[Tar bort appdata](/intune/app-protection-policies) från användarens enhet.|
|Appskyddsprincip|Tillgänglig för mobilappar som integreras med Enterprise Mobility + Security-teknik (EMS). Säkerställer att användarens appar är kompatibla med [företagets dataskyddsprinciper](/intune/app-protection-policies).|
|App SDK|Med [Microsoft Intune App SDK](/intune/app-sdk) kan du lägga till funktioner i dina interna skrivna appar som innebär att de kan hanteras av Intunes appskyddsprinciper.|
|Appens avinstallationsåtgärd|Låter dig [avinstallera appar](/intune/apps-deploy) från användarnas enheter.|
|Apphanteringsverktyg|Ett [kommandoradsprogram](/intune/apps-prepare-mobile-application-management) som skapar en omslutning runt en branschspecifik app, så att den kan hanteras av en Intune-appskyddsprincip.|
|Tilldelningsåtgärd|En åtgärd som du utför när du [tilldelar en app](/intune/apps-deploy). Du kan välja att göra appinstallationen obligatorisk (krav), valfri (tillgänglig) eller avinstallera appen.|
|Tillgänglig installation|När du tilldelar en app med denna åtgärd visas den i företagsportalen och användarna kan [installera den på begäran](/intune/apps-deploy).|
|Azure Portal|Den nya konsolen för Intune [Läs mer](/intune/what-is-intune).|

## <a name="b"></a>B
|||
|-|-|
|BYOD|[Bring your own device](/intune/device-enrollment). Användare kan installera appen för Intunes företagsportal på sin enhet och sedan registrera sig, få åtkomst till företagsresurser som e-post, företagsappar, företagets data och support.|

## <a name="c"></a>C
|||
|-|-|
|Certifikatprofil|Du använder den här principtypen för [secure access to corporate resources](/intune/certificates-configure) (säker åtkomst till företagets resurser) med certifikat när du använder Wi-Fi, e-post eller VPN-profiler.|
|COD|[Företagsägda enheter](/intune/device-enrollment) kan registreras på olika sätt, beroende på behoven i organisationen och de typer av enheter som hanteras.|
|Företagsportal|En app eller en webbplats som ger användarna [åtkomst till företagets data och appar](/intune/company-portal-customize).|
|Policy för efterlevnad|Kontrollerar att enheterna [följer vissa regler](/intune/device-compliance) som att använda en PIN-kod för att få åtkomst till enheten och kryptering av data som lagras på enheten.|
|Kompatibla och icke-kompatibla appar|Med dessa inställningar, som ingår i en [enhetsbegränsningsprofil](/intune/device-restrictions-configure), kan du definiera en lista med appar som användare får eller inte får köra. Intune informerar dig sedan via rapporter om att ett icke-kompatibelt program har installerats, eller kör. Intune kan även blockera installationen av en icke-kompatibel app för vissa plattformar.|
|Villkorlig åtkomst|[Allows access to company email, Office 365, and other services](/intune/conditional-access) (Tillåter åtkomst till företagets e-post, Office 365 och andra tjänster) från endast enheter som är kompatibla med regler som du anger.|
|Anpassad princip|Du [använder dessa principer](/intune/custom-settings-configure) när en princip för allmän konfiguration inte innehåller en inbyggd inställning som uppfyller dina behov. Du kan använda en anpassad princip för att skapa en inställning på ett annat sätt, som till exempel med Apple Configurator eller OMA-URI.|

## <a name="d"></a>D
|||
|-|-|
|distribution|Att skicka en app eller en princip till en enhet eller användare som du hanterar. Åtgärden kallas nu att *tilldela*.|
|Hanterare av enhetsregistrering|Organisationer kan använda Intune för att hantera ett stort antal mobila enheter med ett enda användarkonto. [Kontot för enhetsregistreringshanteraren](/intune/device-enrollment-program-enroll-ios) är ett speciellt Intune-konto som kan registrera upp till 1 000 enheter.|
|Enhetsprofiler|Med [dessa profiler](/intune/device-profile-create) kan du konfigurera olika säkerhets-, funktions- och åtkomstinställningar på enheter som du hanterar.|

## <a name="e"></a>E
|||
|-|-|
|E-postprofil|Principen kan användas för att konfigurera [åtkomstinställningar för e-post](/intune/email-settings-configure) för mobila enheter, vilket minimerar mängden konfiguration som slutanvändaren behöver utföra.|
|EMS|Microsoft Enterprise Mobility + Security (tidigare Enterprise Mobility Suite) skyddar företagets data och låter användarna att [få åtkomst till apparna och det innehåll som de behöver](https://www.microsoft.com/cloud-platform/enterprise-mobility).|
|Slutanvändare|[Användare av enheter som telefoner och datorer](/intune/end-user-educate) som du hanterar med Intune.|
|Registrera|Microsoft Intune använder [registrering](/intune/device-enrollment) för att hantera enheter och tillåta åtkomst till resurser.|

## <a name="f"></a>F
|||
|-|-|
|FastTrack|En [Microsoft-tjänst](https://technet.microsoft.com/library/mt228265.aspx) för Intune-användare med 150 licenser i en berättigad plan. Med den här tjänsten kan Microsoft-specialister hjälpa dig att komma igång med Intune.|

## <a name="g"></a>G
|||
|-|-|
|Grupper|Grupper låter dig [logiskt samla ihop användare eller enheter](/intune/groups-get-started). Du kan till exempel skapa en grupp med alla Windows-datorer. Du kan sedan tilldela appar och profiler till dessa grupper.|

## <a name="h"></a>H
|||
|-|-|
|Hybrid|En konfiguration där du kan hantera enheter som är registrerade med Intune i System Center Configuration Manager-konsolen.|

## <a name="i"></a>I
|||
|-|-|
|Azure-portalen|Den Azure-portal som du använder för de flesta hanteringsåtgärderna i Intune.|
|Intune-klientprogrammet|Ett annat sätt att [hantera vissa Windows-datorer](/intune-classic/get-started/choose-how-to-manage-devices) om du behöver hjälp med att bestämma vilken metod du ska använda.|
|Intune Software Publisher|Ett verktyg som du använder för att [define apps you want to deploy and upload them to your cloud storage space](/intune-classic/deploy-use/add-apps) (definiera appar som du vill distribuera och överföra dem till ditt molnlagringsutrymme).|
|Inventering|Använd för att visa [maskinvara och program som finns installerade](/intune/device-inventory) på enheter som du hanterar.|

## <a name="k"></a>K
|||
|-|-|
|Helskärmsläge|Med det här läget, som är konfigurerat som en del av en [enhetsbegränsningsprofil](/intune/device-restrictions-configure), kan du låsa enheter. Du kan t.ex. konfigurera att en butiksenhet endast tillåter att vissa appar körs.|

## <a name="m"></a>M
|||
|-|-|
|Hanterad webbläsare|Ett [webbläsningsprogram](/intune/app-configuration-managed-browser) som du kan tilldela i din organisation med Intune. En princip för hanterad webbläsare konfigurerar en lista över tillåtna eller blockerade webbplatser som begränsar vilka webbplatser användare av den hanterade webbläsaren kan besöka.|
|MDM-utfärdare|[MDM-utfärdaren](/intune/mdm-authority-set) definierar den hanteringstjänst som har behörighet att hantera en uppsättning enheter. Alternativen för MDM-utfärdare innefattar själva Intune och Configuration Manager med Intune.|
|Konfigurationsprincip för mobilappar|Tillgänglig för mobilappar med leverantörsspecifika konfigurationer. Till exempel en [iOS](/intune/app-configuration-policies-use-ios)- eller [Android](/intune/app-configuration-policies-use-android)-princip som används för att skicka inställningar till kompatibla appar när de körs, exempelvis ett företagsnamn eller en serveradress.|
|Etableringsprincip för mobilappar|En iOS-princip som hjälper dig säkerställa att de [etableringsprofiler](/intune/app-provisioning-profile-ios) för iOS-appar som du tilldelar inte upphör att gälla.|
|Hantering av mobila program|[MAM (Moblie Application Management)](/intune/app-lifecycle) låter dig att publicera, pusha, konfigurera, skydda, övervaka och uppdatera mobilappar för dina användare.
|Hantering av mobila enheter|Med [hanteringen av mobila enheter(MDM)](/intune/device-lifecycle) kan du registrera enheter i Intune så att du kan etablera, konfigurera, övervaka och hantera dessa enheter.



## <a name="o"></a>O
|||
|-|-|
|OMA-DM|Open Mobile Alliance Device Management. Ett enhetshanteringsprotokoll som uppfyller industristandard som används av många maskinvarutillverkare för att aktivera kontroll av funktioner i mobila enheter och datorer.|
|OMA-URI|Open Mobile Alliance Uniform Resource Identifier. Dessa objekt identifierar enskilda enhetsinställningar som överensstämmer med OMA-DM-standard. Inställningarna kan användas i [Intunes anpassade profiler](/intune/custom-settings-configure) när det inte finns någon inbyggd inställning som uppfyller behoven.|

## <a name="p"></a>P
|||
|-|-|
|Återställning av lösenord|En Intune-funktion som gör att du kan tvinga användaren att [återställa lösenordet](/intune/device-passcode-reset) på enheter som stöds.|

## <a name="r"></a>R
|||
|-|-|
|Fjärrlåsning|En Intune-funktion som låter dig [låsa enheter som stöds](/intune/device-remote-lock), även om du inte äger enheten.|
|Nödvändig installation|När du tilldelar en app med denna funktion krävs inte någon [användaråtgärd](/intune/apps-deploy) för att slutföra installationen. På vissa plattformar måste slutanvändaren godkänna installationen).|


## <a name="s"></a>S
|||
|-|-|
|Selektiv rensning|En [selektiv rensning](/intune/device-company-data-remove) tar endast bort företagsdata som skyddas av en appskyddsprincip, inklusive inställningar och e-postprofiler från en enhet. Med en selektiv rensning lämnas användarens personliga data på enheten.|
|Sidladdning|Åtgärden att installera en branschspecifik app utan att ha åtkomst till den i en appbutik.|
|Prenumeration|Det avtal som du ingår och som ger dig tillgång till en Intune-klient.|

## <a name="t"></a>T
|||
|-|-|
|TeamViewer|Ett program från en tredje part som används med Intune för att ge [fjärrhjälpsfunktioner](/intune/device-profile-android-teamviewer) för Android-enheter som du hanterar med Intune.|
|Klient|En enskild instans av Intune-tjänsten som du kan använda med en prenumeration.|
|Villkor|En principtyp som du tilldelar till användare med information som användarna måste [läsa och godkänna](/intune/terms-and-conditions-create) innan de kan använda företagsportalen för att registrera sig och få åtkomst till sitt arbete.|

## <a name="v"></a>V
|||
|-|-|
|Volyminköpta appar och böcker|I vissa appbutiker kan du köpa flera licenser av en app eller bok som du vill använda i företaget. Intune hjälper dig att hantera appar och böcker som du har [köpt via ett sådant program](/intune/vpp-apps). Du kan importera licensinformationen från appbutiken, spåra hur många licenser du har använt och förhindra att du installerar fler kopior av appen än du äger.|
|VPN-profil|En princip som tilldelar [VPN-inställningar](/intune/vpn-settings-configure) till enheter som du hanterar och minimerar den konfiguration som krävs av slutanvändarna.|

## <a name="w"></a>W
|||
|-|-|
|Wi-Fi-profil|En princip som tilldelar [inställningar för trådlöst nätverk](/intune/wi-fi-settings-configure) till enheter för att användarna ska kunna ansluta till företagsnätverket utan att behöva känna till eller konfigurera några inställningar.
