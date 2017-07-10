---
title: "Kontrollera Windows Hello för företagsinställningar på enheter"
description: "Läs om hur Intune kan integreras med Windows Hello för företag, en alternativ inloggningsmetod som använder Active Directory eller ett Azure Active Directory-konto för att ersätta ett lösenord, smartkort eller virtuellt smartkort."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 09/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7c4ac0b79e30283b90612c77acf1462a25bb6093
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="control-windows-hello-for-business-settings-on-devices-with-microsoft-intune"></a>Kontrollera inställningarna för Windows Hello för företag på enheter med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune integreras med Windows Hello för företag (tidigare Microsoft Passport for Work), en alternativ inloggningsmetod som använder Active Directory eller ett Azure Active Directory-konto för att ersätta ett lösenord, smartkort eller virtuellt smartkort.

Med Hello för företag kan du logga in med en *användargest* istället för ett lösenord. En användargest kan vara en enkel PIN-kod, biometrisk autentisering, t.ex. Windows Hello, eller en extern enhet, t.ex. en fingeravtrycksläsare.

Intune kan integreras med Hello för företag på två sätt:

-   Du kan använda en Intune-princip för att styra vilka gester användare kan och inte kan använda för inloggning.

-   Du kan lagra autentiseringscertifikat i KSP:n för Windows Hello för företag. Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).

> [!IMPORTANT]
> Du kunde ange två olika PIN-koder för att autentisera åtkomst till resurser i Windows 10 Desktop- och Mobile-versionerna före Anniversary Update:
- **PIN-koden för enheten** kunde användas för att låsa upp enheten och ansluta till molnresurser.
- **PIN-koden för arbetsplatsen** användes för att komma åt resurser i Azure AD på användarnas personliga enheter (BYOD).

>I och med Anniversary Update sammanfogades dessa två PIN-koder till en enda PIN-kod för enheten.
Alla principer för konfiguration i Intune som du anger för att styra PIN-koden för enheten och alla principer för Windows Hello för företag du konfigurerat ställer nu båda in det nya PIN-värdet.
Om båda principer har ställts in för att styra PIN-koden kommer principen för Windows Hello för företag att tillämpas på både enheter som använder Windows 10 Desktop och enheter som använder Windows 10 Mobile.
Uppdatera din princip för Windows Hello för företag så att den matchar inställningarna i konfigurationsprincipen och be dina användare att synkronisera sina enheter i företagsportalappen för att säkerställa att principkonflikter inte uppstår och att PIN-principen tillämpas korrekt.



## <a name="create-a-windows-hello-for-business-policy"></a>Skapa en princip för Windows Hello för företag

1.  Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och välj **Admin** &gt; **Hantering av mobila enheter** &gt; **Windows** &gt; **Windows Hello för företag** så öppnas sidan Windows Hello för företag.

    ![Sidan Windows Hello för företag](../media/passport.png)

2.  Välj någon av följande inställningar:
    - **Inaktivera Windows Hello för företag på registrerade enheter**. Välj den här inställningen om du inte vill använda Windows Hello för företag. Alla andra inställningar på skärmen inaktiveras.
    - **Aktivera Windows Hello för företag på registrerade enheter**. Välj den här inställningen om du vill konfigurera inställningarna för Windows Hello för företag.
    - **Inte konfigurerat**. Välj den här inställningen om du inte vill konfigurera inställningarna för Windows Hello för företag. Eventuella befintliga inställningar för Windows Hello för företag på Windows 10-enheter ändras inte. Alla andra inställningar på skärmen inaktiveras.
3.  Om du har valt **Aktivera Windows Hello för företag på registrerade enheter** konfigurerar du de nödvändiga inställningar som ska gälla för alla registrerade Windows 10- och Windows 10 Mobile-enheter.
4.  Välj **Spara** när du är klar.


## <a name="settings-for-the-windows-hello-for-business-policy"></a>Principinställningar för Windows Hello för företag

- **Använd TPM (Trusted Platform Module)**. Ett TPM-chip ger ett ytterligare lager med datasäkerhet.<br>Välj ett av följande värden:
    - **Obligatoriskt** (standard). Endast enheter med en tillgänglig TPM kan etablera Windows Hello för företag.
    - **Önskad**. Enheterna försöker först använda TPM. Om det inte är tillgängligt kan de använda programvarukryptering.
- **Kräv minsta PIN-kodslängd**/**Kräv största PIN-kodslängd**. Konfigurerar enheterna så att de använder de minsta och största PIN-kodslängder du anger för att hjälpa till att säkerställa säker inloggning. Standardlängden för PIN-kod är 6 tecken, men du kan ange en minsta längd på 4 tecken. Den maximala längden för PIN-kod är 127 tecken.
- **Kräv gemener i PIN-koden**/**Kräv versaler i PIN-koden**/**Kräv specialtecken i PIN-koden**. Du kan tillämpa en starkare PIN-kod genom att kräva att versaler, gemener och specialtecken används i PIN-koden. Välj mellan:
    - **Tillåts**. Användarna kan använda teckentypen i sina PIN-koder, men det är inte obligatoriskt.
    - **Krävs**. Användarna måste inkludera minst en av teckentyperna i sina PIN-koder. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.
    - **Tillåts inte** (standard). Användarna får inte använda dessa teckentyper i sina PIN-koder. (Det är också det som gäller om inställningen inte konfigureras.)<br>Exempel på specialtecken är: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**.
- **PIN-kodens giltighetstid (dagar)**. Det tillhör god praxis att ange en giltighetstid för en PIN-kod och efter denna tid måste användaren ändra den. Standarden är 41 dagar.
- **Spara PIN-kodshistorik**. Begränsar återanvändning av PIN-koder som har använts tidigare. Standardvärdet är att de 5 senaste PIN-koderna inte kan återanvändas.
- **Tillåt biometrisk autentisering**. Aktiverar biometrisk autentisering, t.ex. ansiktsigenkänning eller fingeravtryck, som ett alternativ till PIN-koden för Windows Hello för företag. Användarna måste ändå konfigurera en PIN-kod om den biometriska autentiseringen skulle misslyckas. Välj mellan:
    - **Ja**. Windows Hello för företag tillåter biometrisk autentisering.
    - **Nej**. Windows Hello för företag förhindrar biometrisk autentisering (för alla kontotyper).
- **Använd utökat skydd mot förfalskning när det är tillgängligt**. Konfigurerar om funktionerna för skydd mot förfalskning i Windows Hello används på enheter som har stöd för detta (t.ex. identifiering av ett foto av ett ansikte i stället för ett riktigt ansikte).<br>Om detta är inställt på **Ja** kräver Windows att alla användare använder skydd mot förfalskning för ansiktsdrag när detta stöds.
- **Använd telefoninloggning**. Om det här alternativet är inställt på **Ja** kan användarna använda ett fjärranslutet Passport som fungerar som en bärbar tillhörande enhet för autentisering på stationär dator. Den stationära datorn måste vara ansluten med Azure Active Directory och den tillhörande enheten måste vara konfigurerad med en PIN-kod för Windows Hello för företag.

## <a name="further-information"></a>Ytterligare information
Mer information om Microsoft Passport finns i [guiden](https://technet.microsoft.com/library/mt589441.aspx) i Windows 10-dokumentationen.
