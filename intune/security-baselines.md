---
title: Använda säkerhetsbaslinjer i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller konfigurera rekommenderade gruppsäkerhetsinställningar för att skydda användare och data på enheter som använder Microsoft Intune till att hantera mobilenheter. Aktivera BitLocker, konfigurera Microsoft Defender Advanced Threat Protection, styr Internet Explorer, använd SmartScreen, ange lokala säkerhetsprinciper, kräv ett lösenord, blockera hämtningar från Internet och mycket mer.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e4d5c23d598641256c196cd7217797f87f99d1c
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66374136"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>Skapa en säkerhetsbaslinje för Windows 10 i Intune

Säkerhetsbaslinjer är en funktion som är tillgänglig i en förhandsversion för enheter som kör Windows 10 och senare. Den här funktionen innehåller många inställningar som stöds av Intune som skyddar dina användare och enheter. Inställningarna anges också automatiskt till värden som rekommenderas av säkerhetsteamen. Till exempel aktiverar baslinjen automatiskt BitLocker, kräver automatiskt ett lösenord för att låsa upp en enhet, inaktiverar automatiskt grundläggande autentisering och mycket mer.

Den här funktionen gäller för:

- Windows 10 version 1809 och senare

> [!NOTE]
> När säkerhetsbaslinjer används i en förhandsversion rekommenderar Microsoft att man inte använder profiler i en produktionsmiljö, eftersom baslinjerna kan komma att ändras i förhandsversionen. När säkerhetsbaslinjer är allmänt tillgängliga konverteras inte befintliga profiler till de senaste profilerna som stöds.

Målet med att använda säkerhetsbaslinjer är att få ett säkert arbetsflöde från slutpunkt till slutpunkt när du arbetar med Microsoft 365. Några av fördelarna är:

- En säkerhetsbaslinje innehåller metodtips och rekommendationer för inställningar som påverkar säkerheten. Intune samarbetar med samma Windows-säkerhetsteam som skapar grupprincipernas säkerhetsbaslinjer. De här rekommendationerna baseras på vägledning och omfattande erfarenhet.
- Om Intune är nytt för dig och du inte är säker på var du ska börja, kan säkerhetsbaslinjerna vara till hjälp. Du kan snabbt skapa och distribuera en säker profil, där du vet att du hjälper till att skydda din organisations data och resurser.
- Om du använder en grupprincip är det mycket enklare att migrera till Intune för hantering med dessa baslinjer. Baslinjerna är inbyggda i Intune och innehåller moderna hanteringsfunktioner.

Säkerhetsbaslinjerna skapar en ”konfigurationsprofil” i Intune. Profilen innehåller alla inställningar som finns i baslinjen. Du kan sedan tillämpa eller tilldela profilen till dina användare, grupper och enheter.

När profilen har tilldelats kan du övervaka profilen och baslinjen. Du kan till exempel se vilka enheter som matchar baslinjen, eller vilka som inte matchar baslinjen.

Den här artikeln kan hjälpa dig att använda säkerhetsbaslinjer till att skapa en profil, tilldela profilen och övervaka profilen.

[Windows säkerhetsbaslinjer](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) är en bra resurs om man vill lära sig mer om den här funktionen. [Hantering av mobilenheter](https://docs.microsoft.com/windows/client-management/mdm/) är en bra resurs om du vill lära dig mer om MDM och vad du kan göra på Windows-enheter.

## <a name="available-security-baselines"></a>Tillgängliga säkerhetsbaslinjer  

Följande säkerhetsbaslinjer är tillgängliga för användning med Intune.
- **Förhandsversion: MDM-säkerhetsbaslinje för oktober 2018**  
  [Visa inställningarna](security-baseline-settings-windows.md)

- **FÖRHANDSVERSION: Windows Defender ATP-baslinje**  
  [Visa inställningarna](security-baseline-settings-defender-atp.md)  
  *(Denna baslinje finns tillgänglig när din miljö uppfyller förhandskraven för att använda [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites))* .


## <a name="prerequisites"></a>Krav
För att hantera baslinjer i Intune måste ditt konto ha den inbyggda rollen [Princip- och profilhanterare](role-based-access-control.md#built-in-roles).


## <a name="co-managed-devices"></a>Samhanterade enheter

Säkerhetsbaslinjer på Intune-hanterade enheter liknar samhanterade enheter med Configuration Manager. Samhanterade enheter använder System Center Configuration Manager och Microsoft Intune för att kunna hantera flera Windows 10-enheter samtidigt. Det innebär att du kan använda din befintliga Configuration Manager i molnet tillsammans med Intunes fördelar. [Översikt över samhantering](https://docs.microsoft.com/sccm/comanage/overview) är en bra resurs om du använder Configuration Manager och vill ha fördelarna med molnet.

När du använder samhanterade enheter, måste du ändra arbetsbelastningen i **Enhetskonfiguration** (i dess inställningar) till Intune. Mer information finns i [Enhetskonfigurationens arbetsbelastningar](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration).

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=20909) och välj sedan **Enhetssäkerhet** > **Säkerhetsbaslinjer (förhandsversion)** . Det finns en lista med tillgängliga baslinjer. 

    ![Välj en säkerhetsbaslinje att konfigurera](./media/security-baselines/available-baselines.png)

   >[!TIP]  
   > Windows Defender ATP-baslinjen finns tillgänglig när din miljö uppfyller förhandskraven för att använda [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites).
2. Välj den baslinje som du vill använda och välj sedan **Skapa profil**.  

3. På fliken **Grundinställningar** anger du följande egenskaper:

    - **Namn**: Ange ett namn på säkerhetsbaslinjernas profil. Ange till exempel *Standardprofil för Defender ATP*
    - **Beskrivning**: Ange text som beskriver vad baslinjen gör. Du kan ange vilken text du vill i beskrivningen. Det är valfritt, men rekommenderas definitivt.

4. Välj fliken **Konfiguration** för att visa tillgängliga grupper med **Inställningar** i den här baslinjen. Välj en grupp för att expandera den och visa de enskilda inställningarna som den innehåller. Inställningarna har standardkonfigurationer för säkerhetsbaslinjen. Konfigurera om standardinställningarna för att uppfylla dina affärsbehov.  

    ![Expandera en grupp om du vill visa inställningarna för den gruppen](./media/security-baselines/sample-list-of-settings.png)

5. Välj fliken **Tilldelningar** för att tilldela baslinjen till grupper. Tilldela baslinjen till en befintlig grupp eller skapa en ny grupp med hjälp av standardprocessen i Intune-konsolen för att slutföra konfigurationen.  

   ![Tilldela en profil](./media/security-baselines/assignments.png)
  
6. När du är redo att distribuera baslinjen väljer du fliken **Granska och skapa** för att granska informationen för baslinjen. Välj sedan **Spara profil** för att spara och distribuera profilen. 

   ![Granska baslinjen](./media/security-baselines/review.png) 

   När du har sparat skickas profilen till enheterna när de checkar in med Intune. Därför kan detta inträffa omedelbart.

   > [!TIP]  
   > Du kan spara en profil utan att första tilldela den till grupper. Du kan redigera profilen vid ett senare tillfälle för att lägga till grupper. 

7. När du har skapat profilen kan du redigera den genom att gå till **Enhetssäkerhet** > **Säkerhetsbaslinjer**, välja den baslinje du konfigurerat och sedan välja **Profiler**.  Välj profilen och välj sedan **Egenskaper** för att redigera inställningar och välj **Tilldelningar** för att redigera de grupper som tar emot denna baslinje. 

## <a name="q--a"></a>Frågor och svar

#### <a name="why-these-settings"></a>Varför ska man använda de här inställningarna?

Microsofts säkerhetsteam har många års erfarenhet av att arbeta direkt med Windows-utvecklare och säkerhets-communityn för att skapa de här rekommendationerna. Inställningarna i baslinjen anses vara de mest relevanta säkerhetsrelaterade konfigurationsalternativen. Teamet justerar sina rekommendationer baserat på nyligen utgivna funktioner i varje ny Windows-version.

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Finns det någon skillnad i rekommendationerna för Windows säkerhetsbaslinjer för grupprinciper och Intune?

Det är samma Microsoft-säkerhetsteam som har valt och organiserat inställningarna för varje baslinje. Intune innehåller alla relevanta inställningar i Intunes säkerhetsbaslinje. Det finns vissa inställningar i grupprincipens baslinje som är specifika för en lokal domänkontrollant. De här inställningarna är undantagna från Intunes rekommendationer. De andra inställningarna är likadana.

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Är Intune-säkerhetsbaslinjerna CIS- och NIST-kompatibla?

Egentligen inte. Microsofts säkerhetsteam har kontakt med organisationer, som exempelvis CIS, när man sammanställer sina rekommendationer. Men det finns inte någon en-till-en-mappning mellan ”CIS-kompatibel” och Microsofts baslinjer.

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Vilka certifieringar har Microsofts säkerhetsbaslinjer? 

- Microsoft fortsätter att publicera säkerhetsbaslinjer för grupprinciper (GPO:er) och [verktyg för säkerhetsefterlevnad](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) på samma sätt som vi har gjort under många år. Dessa baslinjer används av många organisationer. Rekommendationerna i dessa baslinjer kommer från Microsoft-säkerhetsteamets samverkan med företagskunder och externa myndigheter, bland annat DoD (Department of Defense) och NIST (National Institute of Standards and Technology). Vi delar våra rekommendationer och baslinjer med dessa organisationer. Organisationerna har också egna rekommendationer som avspeglar Microsofts rekommendationer. Eftersom hantering av mobilenheter (MDM) fortsätter att växa i molnet, har Microsoft skapat motsvarande MDM-rekommendationer för dessa grupprincipbaslinjer. Dessa ytterligare baslinjer är inbyggda i Microsoft Intune och innehåller efterlevnadsrapporter för användare, grupper och enheter som följer (eller inte följer) baslinjen.

- Många kunder använder Intunes baslinjerekommendationer som utgångspunkt, och anpassar dem sedan för att uppfylla sina IT- och säkerhetskrav. Microsofts Windows 10 RS5 **MDM-säkerhetsbaslinje** är den första baslinjen som lanseras. Den här baslinjen har utformats som en allmän infrastruktur där kunderna kommer att kunna importera andra säkerhetsbaslinjer som baseras på CIS, NIST och andra standarder. För närvarande är den tillgänglig för Windows och kommer även att finnas för iOS och Android så småningom.

- Att migrera från lokala Active Directory-grupprinciper till en ren molnlösning med hjälp av Azure Active Directory (AD) och Microsoft Intune kan kännas övermäktigt. Som hjälp finns det dock tillhörande grupprincipobjekt som har publicerats för hybrid AD- och Azure AD-anslutna enheter. Dessa enheter kan hämta MDM-inställningar från molnet (Intune) och grupprincipinställningar från lokala domänkontrollanter när det behövs.

## <a name="next-steps"></a>Nästa steg
- Visa [inställningarna för Windows-säkerhetsbaslinjer](security-baseline-settings-windows.md) som stöds av Intune.  
- Kontrollera statusen och övervaka [baslinje och profil](security-baselines-monitor.md).
