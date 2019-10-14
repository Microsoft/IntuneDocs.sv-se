---
title: Intune-åtgärder och Intune-alternativ som stöds med Apples användarregistrering
titleSuffix: Microsoft Intune
description: Lär dig vilka Intune-åtgärder och Intune-alternativ som stöds med Apples användarregistrering
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: acf1112f96b28b156b3c4857485de30d7ad553ef
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955255"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Intune-åtgärder och Intune-alternativ som stöds med Apples användarregistrering

Användarregistrering har stöd för en deluppsättning av enhetshanteringsalternativen. Om en redan befintlig konfigurationsprofil tillämpas på en enhet som registreras via Användarregistrering, tillämpas bara de inställningar som stöds av Användarregistrering på enheten.

## <a name="password-settings"></a>Inställningar för lösenord

Om du konfigurerar en lösenordsinställning på en enhet som registreras via Användarregisterring används automatiskt inställningen **Blockera** för **Enkla lösenord**, och en 6-siffrig PIN-kod krävs.

Du kan till exempel konfigurera inställningen **Lösenordets giltighetstid** och skicka den här principen till användarregistrerade enheter. Följande händer på enheterna:
- Inställningen **Lösenordets giltighetstid** ignoreras.
- Enkla lösenord, till exempel `1111` eller `1234`, tillåts inte.
- En 6-siffrig PIN-kod krävs.

## <a name="administrator-remote-device-actions-and-options"></a>Administratörsåtgärder på fjärrenheter
Administratörer kan utföra följande åtgärder på enheter som registrerats via Användarregistrering:
- Pensionera
- Ta bort
- Fjärrlåsning
- Synkronisera

Inga andra åtgärder stöds.

## <a name="end-user-actions"></a>Användaråtgärder
Slutanvändarna kan utföra följande åtgärder på enheter som registrerats via Användarregistrering från appen eller webbplatsen för företagsportalen:
- Byta namn. Den här åtgärden gäller endast namnet på företagsportalen. Namnet ändras inte utanför portalen.
- Ta bort
- Fjärrlåsning
- Kontrollera status

## <a name="other-supported-options"></a>Andra alternativ som stöds

Följande alternativ stöds i Intune för enheter som har registrerats via Apples användarregistrering:
- Per app-VPN. Det här alternativet gäller inte Safari-domäner eftersom det inte går att konfigurera Safari-inställningar i Användarregistrering.
- WiFi 
- Borttagning av företagsappar vid avregistrering
- Appdistribution via användarlicensierad volyminköpsplan (VPP)
- Upplåsningsidentifiering

Följande begränsningar stöds:
- Visa företagsdokument i ohanterade appar
- Visa dokument som inte gäller företag i företagsappar
- Tillåt ohanterade appar att läsa från hanterade kontaktkonton
- Behandla AirDrop som ohanterat mål
- Obligatorisk krypterad säkerhetskopiering
- Synkronisering av hanterade appar till molnet
- Åtkomst till Kontrollcenter när enheten är låst
- Åtkomst till Meddelandecenter när enheten är låst
- Dagsvyn när enheten är låst
- Blockera skärmbilder
- Blockera säkerhetskopiering av företagsbok
- Blockera synkronisering av metadata för företagsbok
- Kräv krypterad säkerhetskopiering
- Kräv handledsavkänning för klockor
- Blockera Siri
- Tillåt Siri när enheten är lås
- Kräv bedrägerivarningar från Safari
- Tillåt inte att diagnostik skickas till Apple


## <a name="options-not-supported"></a>Alternativ som inte stöds
Följande alternativ stöds inte på enheter som har registrerats via Användarregistrering. Om du behöver använda dessa alternativ kan du använda Enhetsregistrering för privatägda enheter eller Automatisk enhetsregistrering för företagsenheter.
- Samla in appinventering för appar utanför den hanterade APFS-volymen.
- Samla in inventering av certifikat och etableringsprofiler utanför den hanterade APFS-volymen.
- Samla in UDID och andra permanenta enhetsidentifierare.
- Användarregistrering stöder unika registrerings-ID:n för registrerade enheter. Dessa ID:n bevaras dock inte efter en avregistrering.
- Följande Intune-funktioner stöds inte på grund av den här begränsningen:
- SCEP-användarprofiler som använder serienummer som format för mottagarnamn.
- VPN på enhetsnivå.
- Enhetslicensierad VPP-appdistribution.
- MDM-kontroll av program utanför den hanterade APFS-volymen.
- Programskyddsprinciper används fortfarande för dessa appar. Men du kan inte ta över hanteringen eller distribuera en hanterad version av dessa appar om inte användaren tar bort dem från enheten.
- Åtgärder, konfigurationer, inställningar och kommandon som kräver övervakning. 

## <a name="next-steps"></a>Nästa steg

[Konfigurera användarregistrering för iOS och iPadOS](ios-user-enrollment.md)