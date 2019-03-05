---
title: Inställningar i Windows Hello för företag i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista med alla inställningar för PIN-kod, biometri och skydd mot förfalskning i en identitetsskyddsprofil som använder och konfigurerar Windows Hello för företag på Windows 10-enheter i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5eb4097ab2bedf032270b1d4230d81f7b326fbf1
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57228586"
---
# <a name="windows-10-and-newer-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Inställningar i enheter som kör Windows 10 (och senare) för att aktivera Windows Hello för företag i Intune

Den här artikeln visar och beskriver inställningarna i Windows Hello för företag som du kan styra på Windows 10-enheter i Intune. Använd inställningarna som en del av din MDM-lösning när du vill använda PIN-kod eller fingeravtryck vid inloggning etc.

Som Intune-administratör kan du skapa och tilldela dessa inställningar till enheter som kör Windows 10 och senare.

Mer information om Windows Hello för företag-profiler i Intune finns i [Konfigurera identitetsskydd](identity-protection-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en konfigurationsprofil](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello för företag

- **Konfigurera Windows Hello för företag**: Om du vill använda den här funktionen och konfigurera dess inställningar, väljer du **Aktivera**.
- **Minimilängd för PIN-kod**: Ange den minsta PIN-kodslängd som du vill tillåta på enheterna. Standardlängden för PIN-koder är sex tecken. Minimilängden för PIN-koder är fyra tecken.
- **Maximal längd för PIN-kod**: Ange den maximala längd för PIN-koder som du vill tillåta på enheterna. Standardlängden för PIN-koder är sex tecken. Den maximala längden för PIN-kod är 127 tecken.  
- **Gemener i PIN-kod**: Du kan tillämpa en starkare PIN-kod genom att kräva att slutanvändarna även använder små bokstäver. Alternativen är:

  - **Tillåts inte** (standard): Användarna får inte använda gemener i PIN-koden. Denna inställning tillämpas även när inställningen inte har konfigurerats.
  - **Tillåts**: Användarna får använda gemener i PIN-koden, men det krävs inte.
  - **Obligatoriskt**: Användarna måste inkludera minst en gemen i PIN-koden. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.

- **Versaler i PIN-kod**: Du kan tillämpa en starkare PIN-kod genom att kräva att slutanvändarna använder stora bokstäver. Alternativen är:

  - **Tillåts inte** (standard): Användarna får inte använda versaler i PIN-koden. Denna inställning tillämpas även när inställningen inte har konfigurerats.
  - **Tillåts**: Användarna får använda versaler i PIN-koden, men det krävs inte.
  - **Obligatoriskt**: Användarna måste inkludera minst en versal i PIN-koden. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.

- **Specialtecken i PIN-kod**: Du kan tillämpa en starkare PIN-kod genom att kräva att slutanvändarna använder specialtecken. Alternativen är:

  - **Tillåts inte** (standard): Användarna får inte använda specialtecken i PIN-koden. Denna inställning tillämpas även när inställningen inte har konfigurerats.
    Exempel på specialtecken är: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`
  - **Tillåts**: Användarna får använda versaler i PIN-koden, men det krävs inte.
  - **Obligatoriskt**: Användarna måste inkludera minst en versal i PIN-koden. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.

- **PIN-kodens giltighetstid (dagar)**: Det tillhör god praxis att ange en giltighetstid för en PIN-kod och efter denna tid måste användaren ändra den. Standarden är 41 dagar.

- **Spara PIN-kodshistorik**: Begränsar återanvändning av PIN-koder som har använts tidigare. Standardvärdet är att de 5 senaste PIN-koderna inte kan återanvändas.  
- **Aktivera återställning av PIN-kod**: Användaren kan ändra sin PIN-kod med hjälp av tjänsten för återställning av PIN-kod i Windows Hello för företag.

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **Använd TPM (Trusted Platform Module)**: Ett TPM-chip ger ett ytterligare lager med datasäkerhet. Välj ett av följande värden:  
  - **Aktivera**: Endast enheter med en tillgänglig TPM kan etablera Windows Hello för företag.
  - **Inte konfigurerad**: Alla enheter kan etablera Windows Hello för företag, även om det inte finns någon användbar TPM. Enheterna försöker först använda TPM, men om ingen är tillgänglig kan enheterna använda programvarukryptering.  

- **Tillåt biometrisk autentisering**: Aktiverar biometrisk autentisering, t.ex. ansiktsigenkänning eller fingeravtryck, som ett alternativ till PIN-koden för Windows Hello för företag. Användarna måste ändå konfigurera en PIN-kod om den biometriska autentiseringen skulle misslyckas. Välj mellan:

  - **Aktivera**: Windows Hello för företag tillåter biometrisk autentisering.
  - **Inte konfigurerat** (standard): Windows Hello för företag förhindrar biometrisk autentisering (för alla kontotyper).

- **Använd utökat skydd mot förfalskning när det är tillgängligt**: Välj om funktionerna för skydd mot förfalskning i Windows Hello ska användas på enheter som stöder detta. Till exempel att identifiera ett foto av ett ansikte, i stället för ett riktigt ansikte.

  - **Aktivera**: Windows kräver att alla användare använder skydd mot förfalskning för ansiktsdrag när detta stöds.  
  - **Inte konfigurerat** (standard): Windows godkänner konfigurationerna för skydd mot förfalskning på enheten.

- **Certifikat för lokala resurser**: 

  - **Aktivera**: Tillåter att Windows Hello för företag använder certifikat för att autentisera mot resurser lokalt.
  - **Inte konfigurerat** (standard): Förhindrar att Windows Hello för företag använder certifikat för att autentisera mot resurser lokalt.  

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
