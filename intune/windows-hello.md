---
title: "Så här använder du Windows Hello för företag"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs mer om att skapa en princip för att kontrollera användningen av Windows Hello för företag på hanterade enheter."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 541be8b8-8668-41be-afce-3f3e08c12191
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4d375a40283a5f3c1e9b7302d659739d4ca3d508
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="use-windows-hello-for-business"></a>Använda Windows Hello för företag


[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Microsoft Intune integreras med Windows Hello för företag (tidigare Microsoft Passport for Work), en alternativ inloggningsmetod som använder Active Directory eller ett Azure Active Directory-konto för att ersätta ett lösenord, smartkort eller virtuellt smartkort.

Med Hello för företag kan du logga in med en *användargest* istället för ett lösenord. En användargest kan vara en enkel PIN-kod, biometrisk autentisering, t.ex. Windows Hello, eller en extern enhet, t.ex. en fingeravtrycksläsare.

Intune kan integreras med Hello för företag på två sätt:

-   Du kan använda en Intune-princip för att styra vilka gester användare kan och inte kan använda för inloggning.

<!--- -   You can store authentication certificates in the Windows Hello for Business key storage provider (KSP). For more information, see [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md). --->

> [!IMPORTANT]
> Du kunde ange två olika PIN-koder för att autentisera åtkomst till resurser i Windows 10 Desktop- och Mobile-versionerna före Anniversary Update:
- **PIN-koden för enheten** kunde användas för att låsa upp enheten och ansluta till molnresurser.
- **PIN-koden för arbetsplatsen** användes för att komma åt resurser i Azure AD på användarnas personliga enheter (BYOD).

>I och med Anniversary Update sammanfogades dessa två PIN-koder till en enda PIN-kod för enheten.
Alla principer för konfiguration i Intune som du anger för att styra PIN-koden för enheten och alla principer för Windows Hello för företag du konfigurerat ställer nu båda in det nya PIN-värdet.
Om båda principer har ställts in för att styra PIN-koden kommer principen för Windows Hello för företag att tillämpas på både enheter som använder Windows 10 Desktop och enheter som använder Windows 10 Mobile.
Uppdatera din princip för Windows Hello för företag så att den matchar inställningarna i konfigurationsprincipen och be dina användare att synkronisera sina enheter i företagsportalappen för att säkerställa att principkonflikter inte uppstår och att PIN-principen tillämpas korrekt.



## <a name="create-a-windows-hello-for-business-policy"></a>Skapa en princip för Windows Hello för företag

1.  På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2.  Välj **Registrera enheter** på Intune-bladet och sedan **Hantera** > **Windows Hello för företag**.

3.  På bladet som öppnas väljer du inställningen **Standard**.

4.  På bladet **Alla användare** klickar du på **Egenskaper** och anger sedan ett **Namn** och valfri **Beskrivning** för Windows Hello för företag-inställningarna.

5. På bladet **Alla användare** klickar du på **Inställningar** och väljer bland följande för att **Konfigurera Windows Hello för företag**:

    - **Inaktiverad**. Välj den här inställningen om du inte vill använda Windows Hello för företag. Alla andra inställningar på skärmen inaktiveras.
    - **Aktiverad**. Välj den här inställningen om du vill konfigurera inställningarna för Windows Hello för företag.
    - **Inte konfigurerat**. Välj den här inställningen om du inte vill konfigurera inställningarna för Windows Hello för företag. Eventuella befintliga inställningar för Windows Hello för företag på Windows 10-enheter ändras inte. Alla andra inställningar på bladet inaktiveras.

6.  Om du har valt **Aktiverad** i föregående steg, konfigurerar du de obligatoriska inställningar som kommer att gälla på alla registrerade Windows 10- och Windows 10 Mobile-enheter.

 - **Använd TPM (Trusted Platform Module)**. Ett TPM-chip ger ett ytterligare lager med datasäkerhet.<br>Välj ett av följande värden:

     - **Obligatoriskt** (standard). Endast enheter med en tillgänglig TPM kan etablera Windows Hello för företag.
     - **Önskad**. Enheterna försöker först använda TPM. Om det inte är tillgängligt kan de använda programvarukryptering.

 - **Kräv minsta PIN-kodslängd**/**Kräv största PIN-kodslängd**. Konfigurerar enheterna så att de använder de minsta och största PIN-kodslängder du anger för att hjälpa till att säkerställa säker inloggning. Standardlängden för PIN-kod är 6 tecken, men du kan ange en minsta längd på 4 tecken. Den maximala längden för PIN-kod är 127 tecken.

 - **Kräv gemener i PIN-koden**/**Kräv versaler i PIN-koden**/**Kräv specialtecken i PIN-koden**. Du kan tillämpa en starkare PIN-kod genom att kräva att versaler, gemener och specialtecken används i PIN-koden. Välj mellan:

     - **Tillåts**. Användarna kan använda teckentypen i sina PIN-koder, men det är inte obligatoriskt.
    
     - **Krävs**. Användarna måste inkludera minst en av teckentyperna i sina PIN-koder. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.

     - **Tillåts inte** (standard). Användarna får inte använda dessa teckentyper i sina PIN-koder. (Det är också det som gäller om inställningen inte konfigureras.)<br>Specialtecken omfattar följande: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

 - **PIN-kodens giltighetstid (dagar)**. Det tillhör god praxis att ange en giltighetstid för en PIN-kod och efter denna tid måste användaren ändra den. Standarden är 41 dagar.

 - **Spara PIN-kodshistorik**. Begränsar återanvändning av PIN-koder som har använts tidigare. Standardvärdet är att de 5 senaste PIN-koderna inte kan återanvändas.

 - **Tillåt biometrisk autentisering**. Aktiverar biometrisk autentisering, t.ex. ansiktsigenkänning eller fingeravtryck, som ett alternativ till PIN-koden för Windows Hello för företag. Användarna måste ändå konfigurera en PIN-kod om den biometriska autentiseringen skulle misslyckas. Välj mellan:

     - **Ja**. Windows Hello för företag tillåter biometrisk autentisering.
     - **Nej**. Windows Hello för företag förhindrar biometrisk autentisering (för alla kontotyper).

 - **Använd utökat skydd mot förfalskning när det är tillgängligt**. Konfigurerar om funktionerna för skydd mot förfalskning i Windows Hello används på enheter som har stöd för detta (t.ex. identifiering av ett foto av ett ansikte i stället för ett riktigt ansikte).<br>Om detta är inställt på **Ja** kräver Windows att alla användare använder skydd mot förfalskning för ansiktsdrag när detta stöds.

 - **Använd telefoninloggning**. Om det här alternativet är inställt på **Ja** kan användarna använda ett fjärranslutet Passport som fungerar som en bärbar tillhörande enhet för autentisering på stationär dator. Den stationära datorn måste vara ansluten med Azure Active Directory och den tillhörande enheten måste vara konfigurerad med en PIN-kod för Windows Hello för företag.


## <a name="further-information"></a>Ytterligare information
Mer information om Microsoft Passport finns i [guiden](https://technet.microsoft.com/library/mt589441.aspx) i Windows 10-dokumentationen.

