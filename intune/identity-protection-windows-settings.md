---
title: Inställningar i Windows Hello för företag i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista med alla inställningar för PIN-kod, biometri och skydd mot förfalskning i en identitetsskyddsprofil som använder och konfigurerar Windows Hello för företag på Windows 10-enheter i Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 1cbf45fc337cbe7d7a45081a3b9e05002ca126d8
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402928"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Inställningar i enheter som kör Windows 10 för att aktivera Windows Hello för företag i Intune

Den här artikeln visar och beskriver inställningarna i Windows Hello för företag som du kan styra på Windows 10-enheter i Intune. Som Intune-administratör kan du konfigurera och tilldela dessa inställningar till Windows 10-enheter som en del av din MDM-lösning (hantering av mobilenheter). 

Du hittar mer information om de här inställningarna i [Konfigurera Windows Hello för företagsprincipinställningar](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings) i Windows Hello-dokumentationen.


Mer information om Windows Hello för företag-profiler i Intune finns i [Konfigurera identitetsskydd](identity-protection-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en konfigurationsprofil](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello för företag
- **Konfigurera Windows Hello för företag**:
  - **Inte konfigurerad** – Välj den här inställningen om du inte vill konfigurera inställningarna för Windows Hello för företag. Eventuella befintliga inställningar för Windows Hello för företag på Windows 10-enheter ändras inte. Alla andra inställningar i fönstret inaktiveras.

  - **Avaktiverad** – Välj den här inställningen om du inte vill använda Windows Hello för företag. Alla andra inställningar på skärmen inaktiveras.
  - **Aktivera** – Välj den här inställningen om du vill konfigurera inställningarna för Windows Hello för företag.  
  
  **Standard**: Inte konfigurerat

  När värdet *aktiverad*, följande inställningar är tillgängliga:

    - **Minimilängd för PIN-kod**  
     Ange en minsta kodslängd för PIN-för enheter för att säker inloggning. Standardvärdena för Windows-enhet är sex tecken, men den här inställningen kan ange minst fyra till 127 tecken. 
  
      **Standard**: *Inte konfigurerat*

    - **Maximal längd för PIN-kod**  
    Ange en maximal kodslängd för PIN-för enheter för att säker inloggning. Standardvärdena för Windows-enhet är sex tecken, men den här inställningen kan ange minst fyra till 127 tecken.  

      **Standard**: *Inte konfigurerat*  

    - **Gemener i PIN-kod**  
      Du kan tillämpa en starkare PIN-kod genom att kräva att slutanvändarna även använder små bokstäver. Alternativen är:

      - **Inte tillåtet** – Användarna får inte använda gemener i PIN-koden. Denna inställning tillämpas även när inställningen inte har konfigurerats.
      - **Tillåtet** – Användarna får använda gemener i PIN-koden, men det krävs inte.
      - **Krävs** – Användarna måste inkludera minst en gemen i PIN-koden. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.

    - **Versaler i PIN-kod**  
    Du kan tillämpa en starkare PIN-kod genom att kräva att slutanvändarna använder stora bokstäver. Alternativen är:

      - **Inte tillåtet** – Användarna får inte använda versaler i PIN-koden. Denna inställning tillämpas även när inställningen inte har konfigurerats.
      - **Tillåtet** – Användarna får använda versaler i PIN-koden, men det krävs inte.
      - **Krävs** – Användarna måste inkludera minst en versal i PIN-koden. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.

    - **Specialtecken i PIN-kod**  
    Du kan tillämpa en starkare PIN-kod genom att kräva att slutanvändarna använder specialtecken. Exempel på specialtecken är: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`  
 
      Alternativen är:
      - **Inte tillåtet** – Användarna får inte använda specialtecken i PIN-koden. Denna inställning tillämpas även när inställningen inte har konfigurerats.
      - **Tillåtet** – Användarna får använda versaler i PIN-koden, men det krävs inte.
      - **Krävs** – Användarna måste inkludera minst en versal i PIN-koden. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.

      **Standard**: inte tillåtet

  - **PIN-kodens giltighetstid (dagar)**  
      Det tillhör god praxis att ange en giltighetstid för en PIN-kod och efter denna tid måste användaren ändra den. Standardvärdena för Windows-enhet är 41 dagar.

    **Standard**: Inte konfigurerat

  - **Spara PIN-kodshistorik**  
    Begränsar återanvändning av PIN-koder som har använts tidigare. Windows-enheter som standard förhindrar återanvändning av de sista fem PIN-koderna.  

    **Standard**: Inte konfigurerat  

  - **Aktivera återställning av PIN-kod**   
    Tillåter användare att använda Windows Hello för företag PIN-kod recovery-tjänsten. 
    
    - **Aktiverad** - hemlighet för PIN-koden recovery lagras på enheten och användaren kan ändra sin PIN-kod om det behövs.  
    - **Inaktiverad** -recovery hemligheten inte skapas eller lagras.

    **Standard**: Inte konfigurerat

  - **Använd TPM (Trusted Platform Module)**    
    Ett TPM-chip ger ett ytterligare lager med datasäkerhet.  

    - **Aktivera** – Endast enheter med en tillgänglig TPM kan etablera Windows Hello för företag.
    - **Ej konfigurerad** – Enheterna försöker först använda TPM. Om det inte är tillgängligt kan de använda programvarukryptering.
    
    **Standard**: Inte konfigurerat

  - **Tillåt biometrisk autentisering**  
     Aktiverar biometrisk autentisering, t.ex. ansiktsigenkänning eller fingeravtryck, som ett alternativ till PIN-koden för Windows Hello för företag. Användarna måste ändå konfigurera en PIN-kod om den biometriska autentiseringen skulle misslyckas. Välj mellan:

    - **Aktivera** – Windows Hello för företag tillåter biometrisk autentisering.
    - **Inte konfigurerat** – Windows Hello för företag förhindrar biometrisk autentisering (för alla kontotyper).

    **Standard**: Inte konfigurerat

  - **Använd utökat skydd mot förfalskning när det är tillgängligt**  
    Konfigurerar om funktionerna för skydd mot förfalskning i Windows Hello används på enheter som har stöd för detta (t.ex. identifiering av ett foto av ett ansikte i stället för ett riktigt ansikte).  
    - **Aktivera** – Windows kräver att alla användare använder skydd mot förfalskning för ansiktsdrag när detta stöds.
    - **Inte tillåtet** – Windows godkänner konfigurationerna för skydd mot förfalskning på enheten.

    **Standard**: Inte konfigurerat

  - **Certifikat för lokala resurser**  

    - **Aktivera** – Tillåter att Windows Hello för företag använder certifikat för att autentisera mot resurser lokalt.
    - **Inte konfigurerad** – Förhindrar att Windows Hello för företag använder certifikat för att autentisera mot resurser lokalt. I stället använder enheter standardbeteendet för *lokal nyckelförtroendeautentisering*. Mer information finns i [Användarcertifikat för lokal autentisering](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication) i Windows Hello-dokumentationen.  

  **Standard**: Inte konfigurerat

- **Använda säkerhetsnycklar för att logga in**  
  Den här inställningen är tillgänglig för enheter som kör Windows 10 version 1903 eller senare. Du kan använda den för att hantera stöd för att använda Windows Hello säkerhetsnycklar för att logga in.  

  - **Aktiverad** -användare kan använda en Windows Hello säkerhetsnyckel som en inloggning med autentiseringsuppgifter för datorer som är mål för den här principen. 
  - **Inaktiverad** – säkerhetsnycklar inaktiveras och användarna kan inte använda dem för att logga in på datorer.   

  **Standard**: Inte konfigurerat

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
