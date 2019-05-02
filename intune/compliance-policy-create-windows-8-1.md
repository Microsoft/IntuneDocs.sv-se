---
title: Utbildningsinställningar för Windows 8.1 i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista över alla inställningar som du kan använda när du ställer in kompatibilitet för din Windows 8.1 och Windows Phone 8.1-enheter i Microsoft Intune. Kontrollera efterlevnad på lägsta och högsta operativsystemet, ange begränsningar för lösenord och längd, aktivera kryptering på datalagring och mycket mer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4ed863378616f8001beab89177c642404287e7d3
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424960"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Inställningar för Windows 8.1 att markera enheter som kompatibla eller inte är kompatibla med Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Den här artikeln visar en lista över och beskriver de olika kompatibilitetsinställningar som du kan konfigurera på Windows 8.1-enheter i Intune. Använd inställningarna som en del av din lösning för hantering av mobila enheter, vill blockera enkla lösenord kan du ange en lägsta och högsta version av Operativsystemet och mycket mer.

Den här funktionen gäller för:

- Windows Phone 8.1
- Windows 8.1 och senare

Som Intune-administratör kan använda dessa kompatibilitetsinställningar för att skydda din organisations resurser. Läs mer om efterlevnadsprinciper och eventuella förutsättningar i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en efterlevnadsprincip](create-compliance-policy.md#create-the-policy). För **plattform**väljer **Windows Phone 8.1** eller **Windows 8.1 och senare**.

## <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta Operativsystemversion som krävs**: Ange den lägsta tillåtna versionen. När en enhet inte uppfyller minimikravet på operativsystemversion, rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta tillåtna operativsystemversion**: Ange den högsta tillåtna version. När en enhet använder en senare version av operativsystemet än den som angivits i regeln, blockeras åtkomsten till företagets resurser. Användaren uppmanas sedan att kontakta IT-administratören. Enheten kan inte komma åt företagsresurser förrän du ändrar regeln för att tillåta operativsystemets version.

Datorer med Windows 8.1 returnerar en **3**-version. Om regeln för operativsystemsversion är inställd på Windows 8.1 för Windows rapporteras enheten som inkompatibel även om den har Windows 8.1.

## <a name="system-security"></a>Systemsäkerhet

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter.
- **Enkla lösenord**: Ställ in på **Blockera** om du vill att användaren inte ska kunna skapa enkla lösenord såsom **1234** eller **1111**. Ange till **Inte konfigurerad** så att användarna kan skapa lösenord som **1234** eller **1111**.
- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som lösenordet måste innehålla.

  För enheter som kör Windows och som nås med ett Microsoft-konto, kan inte efterlevnadsprincipen utvärdera korrekt:
  - Om minsta längd på lösenordet är längre än åtta tecken
  - Eller om minsta antal teckenuppsättningar är större än två

- **Lösenordstyp**: Ange om ett lösenord endast ska ha **numeriska** tecken, eller om det ska vara en blandning av siffror och andra tecken (**alfanumeriska**).
  
  - **Antal icke-alfanumeriska tecken i lösenordet:** Om **Krav på lösenordstyp** är inställt till **Alfanumeriskt** anger den här inställningen det minsta antal teckenuppsättningar som lösenordet måste innehålla. De fyra teckenuppsättningarna är:
    - Gemener
    - Versaler
    - Symboler
    - Siffror

    Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext. För enheter som nås med ett Microsoft-konto, kan efterlevnadsprincipen inte korrekt utvärdera:

    - Om minsta längd på lösenordet är längre än åtta tecken
    - Eller om minsta antal teckenuppsättningar är större än två

- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.
- **Antal tidigare lösenord för att förhindra återanvändning**: Ange det antal tidigare lösenord som inte får återanvändas.

### <a name="encryption"></a>Kryptering

- **Kräv kryptering på mobila enheter**: **Kräv** att enheten krypteras för att ansluta till data-lagringsresurser.

Välj **OK** > **Skapa** för att spara ändringarna.

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [använda omfångstaggar om du vill filtrera principer](scope-tags.md).
- [Övervaka dina efterlevnadspolicyer](compliance-policy-monitor.md).
- Se den [inställningar för efterlevnadsprinciper för Windows 10 och senare](compliance-policy-create-windows.md) enheter.