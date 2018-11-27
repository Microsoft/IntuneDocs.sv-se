---
title: Konfigurera inställningar för identitetsskydd i Microsoft Intune – Azure | Microsoft Docs
description: Lägga till en enhetsprofil för att konfigurera Windows Hello för företag-inställningar på Windows 10-enheter i Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: f9d0db8e15e6de1241984f98bf651fcff1578033
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188653"
---
# <a name="configure-identity-protection-settings-in-microsoft-intune"></a>Konfigurera inställningar för identitetsskydd i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Profiler för identitetsskydd styr hur Windows Hello för företag etableras och konfigureras på hanterade Windows 10-enheter. Skapa den här profilen för att konfigurera:  
* Tillgänglighet för Windows Hello för företag för enheter och användare.
* Krav på PIN-kod för enhet.
* Gester användare kan och inte kan använda för att logga in på sina enheter.  

 Du kan tilldela den här profilen till utvalda användare och enhetsgrupper, eller till alla användare och alla enheter. Grupper får profilen för identitetsskydd när de checkar in på Intune.    

Använd informationen i den här artikeln för att skapa en profil för identitetsskydd. Du kan sedan [tilldela profilen](device-profile-assign.md) till användar- och enhetsgrupper.

Den här funktionen gäller för enheter som kör:  
- Windows 10 och senare
- Windows 10 Holographic for Business  

## <a name="create-a-device-profile-with-identity-protection-settings"></a>Skapa en enhetsprofil med inställningar för identitetsskydd

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
4. Ange **Namn** och **Beskrivning** för identitetsskyddsprofilen.
5. I listrutan **Plattform** väljer du **Windows 10 och senare**. Windows Hello för företag stöds endast stöds på enheter som kör Windows 10 och senare.
6. Välj **Identity Protection** i listrutan **Profiltyp**.
7. I fönstret för Windows Hello för företag väljer du bland följande alternativ för att Konfigurera Windows Hello för företag:
    * Inaktiverat Välj den här inställningen om du inte vill använda Windows Hello för företag. Alla andra inställningar på skärmen inaktiveras.
    * Aktiverad. Välj den här inställningen om du vill konfigurera inställningarna för Windows Hello för företag.  

8. Om du har valt **Aktiverad** i föregående steg, konfigurerar du de obligatoriska inställningar som kommer att gälla på inriktade registrerade Windows 10- och Windows 10 Mobile-enheter och användare.

> [!NOTE]
> När du tilldelar profiler för identitetsskydd till endast användare blir enhetskontext som standard **Inte konfigurerad**.  

   - **Minsta PIN-kodslängd**/**Maximala PIN-kodslängd**. Konfigurerar enheterna så att de använder de minsta och största PIN-kodslängder du anger för att hjälpa till att säkerställa säker inloggning. Standardlängden för PIN-kod är sex tecken, men du kan ange en minsta längd på fyra tecken. Den maximala längden för PIN-kod är 127 tecken.  

   - **Gemener i PIN-koden**/**Versaler i PIN-koden**/**Specialtecken i PIN-koden**. Du kan tillämpa en starkare PIN-kod genom att kräva att versaler, gemener och specialtecken används i PIN-koden. Välj mellan:

     - **Tillåts**. Användarna kan använda teckentypen i sina PIN-koder, men det är inte obligatoriskt.

     - **Krävs**. Användarna måste inkludera minst en av teckentyperna i sina PIN-koder. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.

     - **Tillåts inte** (standard). Användarna får inte använda dessa teckentyper i sina PIN-koder. (Detta inträffar också om inställningen inte konfigureras.)<br>Specialtecken omfattar följande: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **PIN-kodens giltighetstid (dagar)**. Det tillhör god praxis att ange en giltighetstid för en PIN-kod och efter denna tid måste användaren ändra den. Standarden är 41 dagar.

   - **Spara PIN-kodshistorik**. Begränsar återanvändning av PIN-koder som har använts tidigare. Standardvärdet är att de 5 senaste PIN-koderna inte kan återanvändas.  
   - **Aktivera återställning av PIN-kod**: Gör att användaren kan ändra sin PIN-kod med hjälp av tjänsten för återställning av PIN-kod i Windows Hello för företag. 
       - **Aktivera**. Molntjänsten krypterar en hemlighet för återställning av PIN-kod som lagras på enheten. Användaren kan ändra sin PIN-kod vid behov.  
       - **Inte konfigurerat** (standard). En hemlighet för återställning av PIN-kod skapas eller lagras inte. Om användarens PIN-kod har glömts bort är det enda sättet att få en ny PIN-kod att radera den befintliga PIN-koden och skapa en ny. Användaren måste registrera sig på nytt hos alla tjänster som den gamla PIN-koden gav åtkomst till.  
   
   - **Använd TPM (Trusted Platform Module)**. Ett TPM-chip ger ett ytterligare lager med datasäkerhet. Välj ett av följande värden:  
     - **Aktivera**. Endast enheter med en tillgänglig TPM kan etablera Windows Hello för företag.
     - **Inte konfigurerat**. Alla enheter kan etablera Windows Hello för företag, även om det inte finns någon användbar TPM. Enheterna försöker först använda TPM, men om ingen är tillgänglig kan enheterna använda programvarukryptering.  

   - **Tillåt biometrisk autentisering**. Aktiverar biometrisk autentisering, t.ex. ansiktsigenkänning eller fingeravtryck, som ett alternativ till PIN-koden för Windows Hello för företag. Användarna måste ändå konfigurera en PIN-kod om den biometriska autentiseringen skulle misslyckas. Välj mellan:

     - **Aktivera**. Windows Hello för företag tillåter biometrisk autentisering.
     - **Inte konfigurerat** (standard). Windows Hello för företag förhindrar biometrisk autentisering (för alla kontotyper).

   - **Använd utökat skydd mot förfalskning när det är tillgängligt**. Konfigurerar om funktionerna för skydd mot förfalskning i Windows Hello används på enheter som har stöd för detta (t.ex. identifiering av ett foto av ett ansikte i stället för ett riktigt ansikte).
       - **Aktivera**. Windows kräver att alla användare använder skydd mot förfalskning för ansiktsdrag när detta stöds.  
       - **Inte konfigurerat** (standard). Windows godkänner konfigurationerna för skydd mot förfalskning på enheten.

   - **Certifikat för lokala resurser**. 
       - **Aktivera**. Tillåter att Windows Hello för företag använder certifikat för att autentisera mot resurser lokalt.
       - **Inte konfigurerat** (standard). Förhindrar att Windows Hello för företag använder certifikat för att autentisera mot resurser lokalt.  
9. Klicka på **OK** för att spara profilen.  

Profilen skapas och visas i listan **Enhetskonfiguration – Profiler**. Om du vill gå vidare och tilldela den här profilen till grupper kan du läsa [Tilldela enhetsprofiler](device-profile-assign.md).  

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
