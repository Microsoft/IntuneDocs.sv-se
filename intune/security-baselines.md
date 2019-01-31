---
title: Använda säkerhetsbaslinjer i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller konfigurera rekommenderade gruppsäkerhetsinställningar för att skydda användare och data på enheter som använder Microsoft Intune till att hantera mobilenheter. Aktivera BitLocker, konfigurera Windows Defender Avancerat skydd, styr Internet Explorer, använd SmartScreen, ange lokala säkerhetsprinciper, kräv ett lösenord, blockera hämtningar från Internet och mycket mer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d78adf8e7d6d2ce05951171e6248dcc8c389945d
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55070296"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>Skapa en säkerhetsbaslinje för Windows 10 i Intune

Säkerhetsbaslinjer är en funktion som är tillgänglig i en förhandsversion för enheter som kör Windows 10 och senare. Den här funktionen innehåller många Intune-inställningar som skyddar dina användare och enheter. Inställningarna anges också automatiskt till värden som rekommenderas av säkerhetsteamen. Till exempel aktiverar baslinjen automatiskt BitLocker, kräver automatiskt ett lösenord för att låsa upp en enhet, inaktiverar automatiskt grundläggande autentisering och mycket mer.

Den här funktionen gäller för:

- Windows 10 version 1809 och senare

> [!NOTE]
> När säkerhetsbaslinjer används i en förhandsversion rekommenderar Microsoft att man inte använder profiler i en produktionsmiljö, eftersom baslinjerna kan komma att ändras i förhandsversionen.

Målet med att använda säkerhetsbaslinjer är att få ett säkert arbetsflöde från slutpunkt till slutpunkt när du arbetar med Microsoft 365. Några av fördelarna är:

- En säkerhetsbaslinje innehåller metodtips och rekommendationer för inställningar som påverkar säkerheten. Intune samarbetar med samma Windows-säkerhetsteam som skapar grupprincipernas säkerhetsbaslinjer. De här rekommendationerna baseras på vägledning och omfattande erfarenhet.
- Om Intune är nytt för dig och du inte är säker på var du ska börja, kan säkerhetsbaslinjerna vara till hjälp. Du kan snabbt skapa och distribuera en säker profil, där du vet att du hjälper till att skydda din organisations data och resurser.
- Om du använder en grupprincip är det mycket enklare att migrera till Intune för hantering med dessa baslinjer. Baslinjerna är inbyggda i Intune och innehåller moderna hanteringsfunktioner.

Säkerhetsbaslinjerna skapar en ”konfigurationsprofil” i Intune. Profilen innehåller alla inställningar som finns i baslinjen. Du kan sedan tillämpa eller tilldela profilen till dina användare, grupper och enheter.

När profilen har tilldelats kan du övervaka profilen och baslinjen. Du kan till exempel se vilka enheter som matchar baslinjen, eller vilka som inte matchar baslinjen.

Den här artikeln visar hur du använder säkerhetsbaslinjer till att skapa en profil, tilldela profilen och övervaka profilen.

[Windows säkerhetsbaslinjer](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) är en bra resurs om man vill lära sig mer om den här funktionen. [Hantering av mobilenheter](https://docs.microsoft.com/windows/client-management/mdm/) är en bra resurs om du vill lära dig mer om MDM och vad du kan göra på Windows-enheter.

## <a name="co-managed-devices"></a>Samhanterade enheter

Säkerhetsbaslinjer på Intune-hanterade enheter liknar samhanterade enheter med Configuration Manager. Samhanterade enheter använder System Center Configuration Manager och Microsoft Intune för att kunna hantera flera Windows 10-enheter samtidigt. Det innebär att du kan använda din befintliga Configuration Manager i molnet tillsammans med Intunes fördelar. [Översikt över samhantering](https://docs.microsoft.com/sccm/comanage/overview) är en bra resurs om du använder Configuration Manager och vill ha fördelarna med molnet.

När du använder samhanterade enheter, måste du ändra arbetsbelastningen i **Enhetskonfiguration** (i dess inställningar) till Intune. Mer information finns i [Enhetskonfigurationens arbetsbelastningar](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration).

## <a name="create-the-profile"></a>Skapa profilen

1. I [Azure-portalen](https://portal.azure.com/) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Säkerhetsbaslinjer (förhandsversion)**. Det finns en lista med tillgängliga baslinjer. Vartefter flera baslinjer läggs till ser du dem här:

    ![Visa en lista med tillgängliga säkerhetsbaslinjer i Intune](./media/security-baselines/available-baselines.png)

3. Välj den baslinje som du vill använda > **Skapa profil**.
4. Ange följande egenskaper i **Grundinställningar**:

    - **Namn**: Ange ett namn på säkerhetsbaslinjernas profil. Ange till exempel `pilot Windows 10 MDM baseline - Oct 2018`.
    - **Beskrivning**: Ange text som beskriver vad baslinjen gör. Du kan ange vilken text du vill i beskrivningen. Det är valfritt, men rekommenderas definitivt.

5. Expandera **Inställningar**. I listan visas alla inställningar för säkerhetsbaslinjen, samt vad inställningen ställs in på automatiskt. Inställningarna och deras värden rekommenderas och kan ändras av dig.

    ![Expandera inställningen för att se alla inställningar för den här säkerhetsbaslinjen i Intune](./media/security-baselines/sample-list-of-settings.png)

    Expandera några av inställningarna för att kontrollera deras värden. Expandera exempelvis **Windows Defender**. Lägg märke till några av inställningarna och vad de är inställda på:

    ![Se vad vissa av inställningarna i Windows Defender ställs in på automatiskt i Intune](./media/security-baselines/expand-windows-defender.png)

6. **Skapa** profilen. 
7. Välj **Profiler**. Profilen skapas och visas i listan. Men den gör inte något ännu. Nu ska du tilldela profilen.

## <a name="assign-the-profile"></a>Tilldela profilen

När profilen har skapats är den klar att tilldelas till dina användare, enheter och grupper. När den har tilldelats kommer profilen och dess inställningar att tillämpas på de användare, enheter och grupper som du väljer.

1. I Intune väljer du **Säkerhetsbaslinjer** > välj en baslinje > **Profiler**.
2. Välj din profil > **Tilldelningar**.

    ![Välj din säkerhetsbaslinjeprofil i Intune och klicka på tilldelningarna för att distribuera profilen](./media/security-baselines/assignments.png)

3. På fliken **Inkludera** lägger du till de grupper, användare eller enheter som du vill tillämpa principen på.

    > [!TIP]
    > Observera att du också kan **Undanta** grupper. Om du tillämpar en princip på **Alla användare** kan du t.ex. skapa ett undantag för administratörsgrupperna. Om något händer är det bra om du och dina administratörer inte har blockerats.

4. **Spara** ändringarna.

När du har sparat skickas profilen till enheterna när de checkar in med Intune. Därför kan detta inträffa omedelbart.

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

Kontrollera statusen och övervaka [baslinje och profil](security-baselines-monitor.md).
