---
title: "Kända problem i Microsoft Intune på Azure"
titleSuffix: Intune on Azure
description: "Läs om kända problem i Intune”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4fda224613d8b69be82ef7f9681ba9165be33e52
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="known-issues-in-microsoft-intune"></a>Kända problem i Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Läs det här ämnet för att lära dig om kända problem i Microsoft Intune.

Om du vill rapportera en bugg som inte visas här, [öppnar du en supportförfrågan](get-support.md).

Om du vill föreslå en ny funktion för Intune så kan du skicka in en rapport på vår [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console)-webbplats.

## <a name="migration"></a>Migrering

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>Grupper som skapats av Intune under migreringen kan påverka funktionen för andra Microsoft-produkter

När du migrerar från klassiska Intune till Azure, kan det visas en ny grupp med namnet **Alla användare – b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Den gruppen innehåller alla användare i Azure Active Directory, inte bara Intune-licensierade användare. Det kan orsaka problem med andra Microsoft-produkter om du förväntar dig att vissa befintliga eller nya användare inte ska vara medlemmar i några grupper.

### <a name="secondary-migration-required-for-select-capabilities"></a>Sekundär migrering som krävs för utvalda funktioner

Intune-konton som skapats före januari 2017 måste migreras innan de här funktionerna kan användas i Azure-portalen:

- Registreringsprofiler för företagsenheter
- Apples DEP (Device Enrollment Program)
- Gruppen förregistrerade företagsenheter efter iOS-serienummer
- Hanterare av enhetsregistrering
- Apples volymköpsprogram

Eftersom de här funktionerna inte kan hanteras både från klassiska Silverlight- och Azure-konsoler, gör migreringen att:
- De inaktiveras i den klassiska konsolen
- De aktiveras i Azure-konsolen.  

Om du hanterar de här Intune-funktioner i Azure-portalen nu så måste du vara medveten om följande punkter:

#### <a name="removes-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Tar bort standardprofiler för registrering av företagsenheter i Apple DEP
Azure-portalen stöder inte en standardprofil för registrering av företagsenheter för Apples enhetsregistreringsprogram DEP. Den här funktionen, som är tillgänglig i den klassiska Silverlight Intune-konsolen, kommer upphöra för att förhindra oavsiktlig profiltilldelning. När DEP-serienummer synkroniseras i Azure-portalen, tilldelas ingen profil för registrering av företagsenheter. En registreringsprofil måste tilldelas innan du använder enheten.

#### <a name="apple-dep-token-restored-with-migration"></a>Apple DEP-token återställs vid migrering

Om du tog bort en Apples DEP-token i den klassiska Intune-portalen (Silverlight) och inte laddar upp en ny token till Azure-portalen, återställs den ursprungliga token i Azure-portalen när du migrerar. Om du vill ta bort denna token och förhindra DEP-registrering, tar du bort token från Azure-portalen.

### <a name="status-blades-for-migrated-policies-do-not-work"></a>Statusbladen för migrerade principer fungerar inte

Du kan inte visa statusinformation för principer som har migrerats från den klassiska portalen i Azure Portal. Du kan dock fortsätta att visa rapporter för dessa principer i den klassiska portalen.
Om du vill visa statusinformation för migrerade konfigurationsprinciper, måste du återskapa dem i Azure Portal.

## <a name="apps"></a>Appar

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>Volyminköpta iOS-appar är endast tillgängliga i standardspråket för Intune-klienten
Volyminköpta iOS-appar kan endast visas och tilldelas för samma landskod som Intune-kontot. Intune synkroniserar endast appar från iTunes med det språk som motsvarar landskoden för Intune-klientkontot. Om du t.ex. köper en app som bara är tillgänglig i den amerikanska butiken, men ditt Intune-konto är tyska, visas inte appen i Intune.

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>Flera kopior av samma volyminköpta iOS-program laddas upp
Klicka inte på knappen **Ladda upp** flera gånger för samma VPP-token. Det leder till att dubbla VPP-token laddas upp och att appar synkroniseras flera gånger för samma VPP-token. 

<!-- ## Groups -->

## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>Du kan inte spara en Windows Information Protection-princip för vissa enheter

För enheter som inte har registrerats med Intune, kan du bara ange en primär domän i fältet **identifiera företaget** i inställningarna för en Windows Information Protection-princip.
Om du lägger till ytterligare domäner (med hjälp av **avancerade inställningar** > **nätverksperimeter** > **lägg till en skyddad domän**) så går det inte att spara principen. Felmeddelandet du får upp kommer snart att ändras för att bli mer rättvisande.

### <a name="cisco-anyconnect-vpn-client-support"></a>Stöd för Cisco AnyConnect VPN-klienter
 
Den senaste versionen av Cisco AnyConnect VPN-klienten (4.0.07072) är inte kompatibel med Intune. En framtida uppdatering av Intune inkluderar kompatibilitet med den här VPN-klientversionen. Fram till dess rekommenderar vi att du inte uppdaterar Cisco AnyConnect VPN-klienten och fortsätter att använda den befintliga versionen.

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>Använd den numeriska lösenordstypen med macOS Sierra-enheter

Om du för tillfället väljer den **numeriska** **krävd lösenordstyp** i en enhets begränsningsprofil för macOS Sierra enheter, tillämpas det som **alfanumeriskt**. Konfigurera inte den här inställningen om du vill använda ett numeriskt lösenord för de här enheterna.
Det här problemet kan komma att åtgärdas i en framtida version av macOS.

Mer information om de här inställningarna finns i [macOS-inställningar för enhetsbegränsning i Microsoft Intune](device-restrictions-macos.md).

## <a name="compliance"></a>Efterlevnad

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>Efterlevnadsprinciper från Intune visas inte i den nya konsolen

Efterlevnadsprinciper som du har skapat i den klassiska portalen migreras, men visas inte i Azure-portalen på grund av designändringar i den. Efterlevnadsprinciper som du skapade i den klassiska Intune-portalen används fortfarande, men du måste visa och redigera dem i den klassiska Intune-portalen.
Dessutom syns nya efterlevnadsprinciper som du skapar i Azure-portalen inte i den klassiska Intune-portalen.

Mer information finns i [Vad är enhetsefterlevnad?](device-compliance.md).

<!-- ## Enrollment -->


<!-- ## Data protection -->


## <a name="administration-and-accounts"></a>Administration och konton

Globala administratörer (även kallade innehavaradministratörer) kan fortsätta att utföra dagliga administrationsuppgifter utan separata Intune- eller EMS-licenser (Enterprise Mobility Suite). Men för att använda tjänsten, till exempel registrera sina egna enheter, en företagsenhet eller för att använda Intunes företagsportal, behöver de en Intune- eller EMS-licens.

<!-- ## Additional items -->












 
