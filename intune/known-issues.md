---
title: "Kända problem med Microsoft Intune i Azure-portalen"
titlesuffix: Azure portal
description: "Läs om kända problem i Intune”"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 372e25968005258fd1e00cbab7db542ad0211206
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/01/2017
---
# <a name="known-issues-in-microsoft-intune"></a>Kända problem i Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Läs det här ämnet för att lära dig om kända problem i Microsoft Intune.

Om du vill rapportera en bugg som inte visas här, [öppnar du en supportförfrågan](get-support.md).

Om du vill föreslå en ny funktion för Intune så kan du skicka in en rapport på vår [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console)-webbplats.

## <a name="migration"></a>Migrering

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Äldre Intune-PC-klientfunktioner är endast tillgängliga i Silverlight-konsolen

Möjligheten att hantera Windows 10 i Intune på Azure Portal är tillgänglig via Windows MDM-registrering. Mer information finns i [Intune i Azure-konsolen och den äldre Intune PC-klienten](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure).

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>Grupper som skapats av Intune under migreringen kan påverka funktionen för andra Microsoft-produkter

När du migrerar från Intune till Azure-portalen kan det visas en ny grupp med namnet **All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Den gruppen innehåller alla användare i Azure Active Directory, inte bara Intune-licensierade användare. Det kan orsaka problem med andra Microsoft-produkter om du förväntar dig att vissa befintliga eller nya användare inte ska vara medlemmar i några grupper.

### <a name="secondary-migration-required-for-select-capabilities"></a>Sekundär migrering som krävs för utvalda funktioner

Intune-konton som skapats före januari 2017 måste migreras innan följande funktioner kan användas i Azure Portal:

- Registreringsprofiler för företagsenheter
- Apples DEP (Device Enrollment Program)
- Förhandsdeklarera företagsenheter via iOS-serienumret
- Konton för enhetsregistreringshanterare
- Apples volymköpsprogram

Eftersom de här funktionerna inte kan hanteras både från Intune-konsolen (Silverlight) och Azure-portalen innebär migreringen att:
- De inaktiveras i den klassiska portalen
- De aktiveras i Azure Portal  

Efter 22 september 2017 sker migreringen av de här funktionerna tillsammans den första migreringen till Azure. Om ditt konto redan har migrerats för användning av Azure Portal kan den andra migreringen redan har slutförts. Om inte migreras dessa funktioner till Azure i november. Migreringen av ditt konto slutförs samma dag det påbörjas. Migreringen kan ta upp till 6 timmar från det att funktionerna har inaktiverats i den klassiska Intune-portalen.

Om du hanterar de här Intune-funktioner i Azure-portalen nu så måste du vara medveten om följande punkter:

#### <a name="removes-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Tar bort standardprofiler för registrering av företagsenheter i Apple DEP
Azure-portalen stöder inte en standardprofil för registrering av företagsenheter för Apples enhetsregistreringsprogram DEP. Den här funktionen, som är tillgänglig i Intune-konsolen (Silverlight), kommer att upphöra för att förhindra oavsiktlig profiltilldelning. När DEP-serienummer synkroniseras i Azure-portalen, tilldelas ingen profil för registrering av företagsenheter. En registreringsprofil måste tilldelas innan du använder enheten.

#### <a name="apple-dep-token-restored-with-migration"></a>Apple DEP-token återställs vid migrering

Om du tog bort Apples token för enhetsregistreringsprogram i Intune-portalen (Silverlight) och inte laddade upp någon ny token till Azure-portalen, återställs din ursprungliga token i Azure-portalen när du migrerar. Om du vill ta bort denna token och förhindra DEP-registrering, tar du bort token från Azure-portalen.

### <a name="status-blades-for-migrated-policies-do-not-work"></a>Statusbladen för migrerade principer fungerar inte

Du kan inte visa statusinformation för principer som har migrerats från den klassiska portalen i Azure Portal. Du kan dock fortsätta att visa rapporter för dessa principer i den klassiska portalen. Om du vill visa statusinformation för migrerade konfigurationsprinciper, måste du återskapa dem i Azure Portal.

## <a name="apps"></a>Appar

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>Volyminköpta iOS-appar är endast tillgängliga i standardspråket för Intune-klienten
Volyminköpta iOS-appar kan endast visas och tilldelas för samma landskod som Intune-kontot. Intune synkroniserar endast appar från iTunes med det språk som motsvarar landskoden för Intune-klientkontot. Om du t.ex. köper en app som bara är tillgänglig i den amerikanska butiken, men ditt Intune-konto är tyskt, visas inte appen i Intune.

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>Flera kopior av samma volyminköpta iOS-program laddas upp
Klicka inte på knappen **Ladda upp** flera gånger för samma VPP-token. Det leder till att dubbla VPP-token laddas upp och att appar synkroniseras flera gånger för samma VPP-token.

<!-- ## Groups -->

## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>Du kan inte spara en Windows Information Protection-princip för vissa enheter

För enheter som inte har registrerats med Intune, kan du bara ange en primär domän i fältet **identifiera företaget** i inställningarna för en Windows Information Protection-princip.
Om du lägger till ytterligare domäner (med hjälp av **avancerade inställningar** > **nätverksperimeter** > **lägg till en skyddad domän**) så går det inte att spara principen. Felmeddelandet du får upp kommer snart att ändras för att bli mer rättvisande.

### <a name="cisco-anyconnect-vpn-client-support"></a>Stöd för Cisco AnyConnect VPN-klienter

Den senaste versionen av Cisco AnyConnect VPN-klienten (4.0.07072) är inte kompatibel med Intune.
En framtida uppdatering av Intune inkluderar kompatibilitet med den här VPN-klientversionen. Fram till dess rekommenderar vi att du inte uppdaterar Cisco AnyConnect VPN-klienten och fortsätter att använda den befintliga versionen.

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>Använd den numeriska lösenordstypen med macOS Sierra-enheter

Om du för tillfället väljer den **numeriska** **krävd lösenordstyp** i en enhets begränsningsprofil för macOS Sierra enheter, tillämpas det som **alfanumeriskt**. Konfigurera inte den här inställningen om du vill använda ett numeriskt lösenord för de här enheterna.
Det här problemet kan komma att åtgärdas i en framtida version av macOS.

Mer information om de här inställningarna finns i [macOS-inställningar för enhetsbegränsning i Microsoft Intune](device-restrictions-macos.md).

## <a name="compliance"></a>Efterlevnad

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>Efterlevnadsprinciper från Intune visas inte i den nya konsolen

Efterlevnadsprinciper som du har skapat i den klassiska portalen migreras, men visas inte i Azure-portalen på grund av designändringar i den. Efterlevnadsprinciper som du skapade i den klassiska Intune-portalen används fortfarande, men du måste visa och redigera dem i den klassiska portalen.

Dessutom syns nya efterlevnadsprinciper som du skapar i Azure-portalen inte i den klassiska portalen.

Mer information finns i [Vad är enhetsefterlevnad?](device-compliance.md).

<!-- ## Enrollment -->


## <a name="data-protection"></a>Dataskydd

### <a name="ios-app-protection-policies"></a>iOS-appskyddsprinciper

Du kan definiera [appskyddsprinciper för iOS](app-protection-policy-settings-ios.md) som är tillgängliga för användarna på enheter som hanteras via hantering av mobilappar (MAM) utan registrering. Du kan bara definiera dessa principer för iOS-versioner med ett decimaltecken i versionnumret i stället för flera decimaltecken på grund av ett tillfälligt fel. I stället för att ange en lägsta version av iOS som 10.3.1 kan du kalla den iOS 10.3. Detta kommer att lösas med en kommande uppdatering av iOS SDK.


## <a name="administration-and-accounts"></a>Administration och konton

Globala administratörer (även kallade innehavaradministratörer) kan fortsätta att utföra dagliga administrationsuppgifter utan separata Intune- eller EMS-licenser (Enterprise Mobility Suite). Men för att använda tjänsten, till exempel registrera sina egna enheter, en företagsenhet eller för att använda Intunes företagsportal, behöver de en Intune- eller EMS-licens.

<!-- ## Additional items -->
