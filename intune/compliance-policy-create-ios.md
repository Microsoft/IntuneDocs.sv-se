---
title: Kompatibilitetsinställningar för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Visa en lista över alla inställningar som du kan använda när du ställer in kompatibilitet för iOS-enheter i Microsoft Intune. Kräv ett e-postmeddelande, kontrollera jailbrokade eller rotade enheter, ange den lägsta och högsta tillåtna operativsystemversionen, ange begränsningar för lösenord, inklusive lösenordslängd och enhetsinaktivitet, begränsa appar och mycket mer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bde1c296abb99e8c0c81b44908e78b204c62388e
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "71304137"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>iOS-inställningar för att markera enheter som kompatibla eller inkompatibla med hjälp av Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Den här artikeln innehåller en lista över och beskriver de olika kompatibilitetsinställningar som du kan konfigurera på iOS-enheter i Intune. Som en del av din MDM-lösning för hantering av mobilenheter kan du använda dessa inställningar för att kräva ett e-postmeddelande, markera rotade (jailbreakade) enheter som inkompatibla, ange tillåten hotnivå, ange när lösenord ska upphöra att gälla och mycket mer.

Den här funktionen gäller för:

- iOS

Som Intune-administratör kan du använda dessa kompatibilitetsinställningar för att skydda din organisations resurser. Mer om kompatibilitetsprinciper och vad de gör finns i [Komma igång med kompatibilitet](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en efterlevnadsprincip](create-compliance-policy.md#create-the-policy). För **Plattform**, välj **iOS**.

## <a name="email"></a>E-post

- **Kräv att mobila enheter har en hanterad e-postprofil**: När inställningen **Kräv** används betraktas enheter som inte har en e-postmeddelandeprofil som hanteras av Intune som inkompatibla. En enhet kan inte ha en hanterad e-postprofil om den inte är korrekt inriktad, eller om användaren konfigurerar e-postkontot manuellt på enheten. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

  Enheten betraktas som inkompatibel i följande situationer:

  - E-postprofilen är associerad med en annan användargrupp än användargruppen som kompatibilitetsprincipen körs mot.
  - Användaren har redan konfigurerat ett e-postkonto på enheten som matchar Intune-e-postprofilen som distribuerats till enheten. Intune kan inte skriva över den användarkonfigurerade profilen och Intune kan inte hantera den. För att vara kompatibel måste slutanvändaren ta bort de befintliga e-postinställningarna. Sedan kan Intune installera den hantera e-postprofilen.

- **Välj den e-postprofil som måste hanteras av Intune**: Om inställningen **E-postkontot måste hanteras av Intune** används väljer du **Välj** för att ange Intune-e-postprofilen. E-postprofilen måste finnas på enheten.

Mer information om e-postprofiler finns i [Använda e-postprofiler med Intune för att konfigurera åtkomst till organisationens e-post](email-settings-configure.md).

## <a name="device-health"></a>Device health

- **Jailbrokade enheter**: Välj **Blockera** om du vill markera rotade (jailbreakade) enheter som inkompatibla. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Kräv att enheten ska hållas vid eller under hotnivån för enheten** (iOS 8.0 och senare): Använd den här inställningen om du vill använda riskbedömningen som ett kompatibilitetsvillkor. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen. Om du vill använda den här inställningen väljer du den tillåtna hotnivån:
  - **Skyddad**: Det här alternativet är säkrast och innebär att enheten inte kan ha några hot. Om hot på någon nivå identifieras på enheten betraktas den som inkompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög**: Det här alternativet är det minst säkra då det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.

## <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemversion som krävs** (iOS 8.0 och senare): När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändarna kan välja att uppgradera sina enheter. Därefter kan de komma åt organisationens resurser.
- **Högsta tillåtna operativsystemversion** (iOS 8.0 och senare): När en enhet använder en senare operativsystemversion än versionen i regeln, blockeras åtkomsten till organisationens resurser. Slutanvändaren uppmanas att kontakta IT-administratören. Enheten kan inte komma åt organisationens resurser förrän en regel ändras så att operativsystemversionen stöds.
- **Lägsta operativsystembyggversion** (iOS 8.0 och senare): När Apple publicerar säkerhetsuppdateringar uppdateras oftast versionsnumret, inte operativsystemversionen. Använd denna funktion för att ange ett minsta tillåtna versionsnummer på enheten.
- **Högsta operativsystembyggversion** (iOS 8.0 och senare): När Apple publicerar säkerhetsuppdateringar uppdateras oftast versionsnumret, inte operativsystemversionen. Använd denna funktion för att ange ett högsta tillåtna versionsnummer på enheten.

## <a name="system-security"></a>Systemsäkerhet

### <a name="password"></a>Lösenord

> [!NOTE]
> När en efterlevnads- eller konfigurationsprincip används på en iOS-enhet, uppmanas användarna att ange ett lösenord var 15:e minut. Användarna uppmanas kontinuerligt tills ett lösenord anges.

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter. iOS-enheter som använder lösenord krypteras.
- **Enkla lösenord**: Ställ in på **Blockera** om du vill att användaren inte ska kunna skapa enkla lösenord såsom **1234** eller **1111**. Ange till **Inte konfigurerad** så att användarna kan skapa lösenord som **1234** eller **1111**.
- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som lösenordet måste innehålla.
- **Krav på lösenordstyp**: Ange om ett lösenord endast ska ha **numeriska** tecken, eller om det ska vara en blandning av siffror och andra tecken (**alfanumeriska**).
- **Antal icke-alfanumeriska tecken i lösenord**: Ange det lägsta antalet specialtecken, t.ex. `&`, `#`, `%` och `!`, som lösenordet måste innehålla.

    Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext.

- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.
- **Antal tidigare lösenord för att förhindra återanvändning**: Ange det antal tidigare lösenord som inte får återanvändas.

### <a name="device-security"></a>Enhetssäkerhet

- **Begränsade appar**: Du kan begränsa appar genom att lägga till deras paket-ID:n till principen. Om appen är installerad på en enhet markeras enheten som inkompatibel.

  - **Appnamn**: Ange ett användarvänligt namn som hjälper dig att identifiera samlings-ID:t.
  - **Appsamlings-ID**: Ange det unika samlings-ID som tilldelats av appleverantören. Information om hur du hittar paket-ID:t finns i [Hitta paket-ID:t för en iOS-app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (en annan Microsoft-webbplats öppnas).  

Välj **OK** > **Skapa** för att spara ändringarna.

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [Filtrera principer med hjälp av omfångstaggar](scope-tags.md).
- [Övervaka dina kompatibilitetsprinciper](compliance-policy-monitor.md).
- Mer information finns i [Inställningar för kompatibilitetsprinciper för macOS-enheter](compliance-policy-create-mac-os.md).
