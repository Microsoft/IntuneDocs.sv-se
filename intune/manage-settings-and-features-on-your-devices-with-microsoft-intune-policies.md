---
title: Enhetsprinciper, profiler och vanliga frågor om Intune – Azure | Microsoft Docs
description: Läs om de olika principer och profiler som du kan använda i Microsoft Intune, inklusive principer för att konfigurera enheter, få åtkomst till företagets resurser, aktivera villkorlig åtkomst och registrera företagsenheter. Du kan även få svar på vanliga frågor.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ROBOTS: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e8a7a7405fe40d3568e736c244d9fcb308350709
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43317934"
---
# <a name="manage-settings-and-features-on-your-devices-with-intune-policies"></a>Hantera inställningar och funktioner på dina enheter med Intune-principer

Microsoft Intune-*principer* är grupper med inställningar som styr funktioner på datorer och mobila enheter. Du skapar principer genom att använda mallar som omfattar rekommenderade eller anpassade inställningar. Sedan distribuerar du dem till enhets- eller användargrupper.

## <a name="types-of-policies"></a>Typer av principer

Intune-principer hör till följande kategorier. Den kategori som du använder påverkar hur du skapar och distribuerar principen.

- **Konfigurationsprinciper**: Används ofta för att hantera säkerhetsinställningar och -funktioner på dina enheter, inklusive åtkomst till företagsresurser. Kom igång på [Enhetsprofiler i Intune](device-profiles.md).
- **Efterlevnadsprinciper**: Definierar de regler och inställningar som en enhet måste följa för att anses vara kompatibel med principerna för villkorlig åtkomst. Du kan också använda efterlevnadsprinciper för att övervaka och åtgärda enheters efterlevnad oberoende av villkorlig åtkomst. Kom igång med [principer för enhetsefterlevnad](device-compliance-get-started.md).
- **Principer för villkorlig åtkomst**: Hjälper till att skydda e-post och andra tjänster utifrån de villkor du anger. [Vad är villkorlig åtkomst](conditional-access.md) och [vanliga sätt att använda villkorlig åtkomst](conditional-access-intune-common-ways-use.md) är bra resurser för att komma igång.
- **Principer för registrering av företagets enheter**: Information om principer för registrering av företagets enheter finns i [Registrera iOS-enheter](ios-enroll.md).

## <a name="frequently-asked-questions-about-intune-policies"></a>Vanliga frågor om Intune-principer

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-being-deployed"></a>Hur lång tid tar det innan principerna eller apparna når mobilenheterna efter att de har distribuerats?
När en princip eller en app distribueras börjar Intune genast att uppmana enheten att kontakta Intune-tjänsten. Det här steget brukar ta mindre än fem minuter.

Om enheten inte kontaktar tjänsten för att be om principen när den första aviseringen har skickats, görs ytterligare tre försök.  Om enheten är offline (till exempel om den är avstängd eller inte är ansluten till ett nätverk) kanske den inte får aviseringarna. I så fall får enheten principen vid nästa schemalagda kontakt med Intune-tjänsten enligt följande:

| Plattform | Incheckningsfrekvens |
| --- | --- |
| iOS | Var 6:e timme | 
| Mac OS X | Var 6:e timme |
| Android | Var 8:e timme | 
| Windows Phone | Var 8:e timme | 
| Windows 8,1  | Var 8:e timme |  
| Windows 10-datorer som registrerats som enheter | Var 8:e timme | 

Om enheten nyligen har registrerats sker kontrollerna oftare enligt följande:

| Plattform | Frekvens |
| --- | --- |
| iOS | Var 15:e minut i 6 timmar och därefter var 6:e timme |  
| Mac OS X | Var 15:e minut i 6 timmar och därefter var 6:e timme | 
| Android | Var 3:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan var 8:e timme | 
| Windows Phone | Var 5:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan var 8:e timme | 
| Windows-datorer som registrerats som enheter | Var 3:e minut i 30 minuter och därefter var 8:e timme | 

Användarna kan också söka efter principer när som helst genom att öppna företagsportalappen och synkronisera enheten.

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Vilka åtgärder gör att Intune genast skickar en avisering till en enhet?
Enheter kontaktar Intune när de får en avisering som uppmanar dem att göra det, eller enligt schemalagda intervall.  När du riktar en åtgärd mot en enhet eller användare, t.ex. en rensning, låsning, återställning av lösenord, appdistribution, profildistribution (Wi-Fi, VPN, e-post osv.) eller principdistribution, försöker Intune genast att meddela enheten att den ska kontakta Intune-tjänsten.

Andra ändringar, t.ex. en uppdatering av kontaktinformationen på företagsportalen, utlöser inte en omedelbar avisering till enheter.

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-are-applied"></a>Hur vet jag vilka inställningar som tillämpas om flera principer distribueras till samma användare eller enhet?
När två eller fler principer distribueras till samma användare eller enhet så görs utvärderingen av vilken inställning som ska tillämpas på inställningsnivå:

- Inställningar för efterlevnadsprinciper har alltid högre prioritet än inställningar för konfigurationsprinciper.

- Den mest restriktiva efterlevnadsprincipinställningen tillämpas om den utvärderas och jämförs med samma inställning i en annan efterlevnadsprincip.

- Om en konfigurationsprincipinställning hamnar i konflikt med en inställning i en annan konfigurationsprincip visas konflikten i Intune. Lös dessa konflikter manuellt.

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-applies-to-the-app"></a>Vad händer om hanteringsprinciper för mobilprogram (MAM) är i konflikt med varandra? Vilken tillämpas för appen?
Konfliktvärden är de mest restriktiva inställningarna som är tillgängliga i en MAM-princip, förutom fälten för nummerinmatning (t.ex. PIN-försök före återställning).  Nummerinmatningsfälten får samma värden som då du skapar en MAM-princip i konsolen med alternativet för rekommenderade inställningar.

Konflikter uppstår om två principinställningar är samma.  Anta att du har konfigurerat två MAM-principer som är identiska förutom inställningen för kopiera/klistra in.  I detta scenario används det mest restriktiva värdet för kopierings- och inklistringsinställningen, men resten av inställningarna tillämpas så som de konfigurerats.

Om en princip distribueras till appen och börjar tillämpas, och en andra princip distribueras senare, har den första appen företräde och fortsätter att tillämpas. Den andra principen visas som i konflikt. Om båda tillämpas samtidigt, och det inte finns någon föregående princip, kommer båda att vara i konflikt. Som med alla inställningar i konflikt tillämpas de mest restriktiva värdena.

### <a name="what-happens-when-ios-custom-policies-conflict"></a>Vad händer om anpassade iOS-principer är i konflikt med varandra?
Intune utvärderar inte nyttolasten för Apple Configuration-filer eller anpassade OMA-URI-principer (Open Mobile Alliance Uniform Resource Identifier). Den fungerar bara som själva leveransmekanismen.

När du distribuerar en anpassad princip bör du bekräfta att de konfigurerade inställningarna inte är i konflikt med efterlevnadsprinciper, konfigurationsprinciper eller andra anpassade principer. Om en anpassad princip har inställningar som är i konflikt med varandra tillämpas dessa inställningar i slumpmässig ordning.

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>Vad händer när en princip tas bort eller inte längre är tillämplig?
När du tar bort en princip, eller när du tar bort en enhet från en grupp som har en distribuerad princip, tas principer och inställningar bort från enheten enligt följande listor.

#### <a name="enrolled-devices"></a>Registrerade enheter

- Wi-Fi-, VPN-, certifikat- och e-postprofiler – De här profilerna tas bort från alla registrerade enheter som stöds.
- Alla andra principtyper:
  - **Windows- och Android-enheter**: Inställningarna tas inte bort från enheten.
  - **Windows Phone 8.1-enheter**: Följande inställningar tas bort:
    - Kräv ett lösenord för att låsa upp mobila enheter
    - Tillåt enkla lösenord
    - Minsta längd på lösenord
    - Lösenordstyp krävs
    - Lösenordets giltighetstid (i dagar)
    - Kom ihåg tidigare lösenord
    - Antal tillåtna, upprepad felinloggningar innan enheten rensas
    - Antal minuters inaktivitet innan lösenord krävs
    - Krävd lösenordstyp – minsta antal tecken
    - Tillåt kamera
    - Filkryptering på mobil enhet
    - Tillåt flyttbara lagringsenheter
    - Tillåt webbläsare
    - Tillåt appbutik
    - Tillåt skärmbild
    - Tillåt geolokalisering
    - Tillåt Microsoft-konto
    - Tillåt kopiera och klistra in
    - Tillåt Wi-Fi -delning
    - Tillåt automatisk anslutning till kostnadsfria, trådlösa surfpunkter
    - Tillåt rapportering av trådlösa surfpunkter
    - Tillåt rensning
    - Tillåt Bluetooth
    - Tillåt NFC
    - Tillåt Wi-Fi

  - **iOS**: Alla inställningar tas bort, utom:
    - Tillåt röstroaming
    - Tillåt dataroaming
    - Tillåt automatisk synkronisering vid roaming

### <a name="where-can-i-find-help-troubleshooting-policies"></a>Var kan jag få hjälp med att felsöka principer?

Se [Felsöka principer](troubleshoot-policies-in-microsoft-intune.md).
