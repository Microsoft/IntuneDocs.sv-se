---
title: "Kända problem med Microsoft Intune i Azure-portalen"
titlesuffix: Azure portal
description: "Läs om kända problem i Intune”"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c4210d77e52abba07454d8606ba7715c03078ca6
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/12/2018
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
