---
title: Felsöka enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Vanliga frågor och svar om enhetsprinciper och profiler, till exempel profiländringar som inte tillämpas på användare eller enheter, hur lång tid det tar för en ny princip att överföras till enheter, vilka inställningar som tillämpas när det finns flera principer och vad som händer när en profil tas bort eller flyttas med Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/15/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7779e265680ded1b5d5d5b670bcf694376ee8016
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72494409"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Vanliga frågor, problem och lösningar med enhetsprinciper och profiler i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Få svar på vanliga frågor när du arbetar med enhetsprofiler och principer i Intune. I denna artikel visas också listor med incheckningsintervall, mer information om konflikter och mycket mer.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Varför får inte en användare en ny profil vid ändring av lösenord eller lösenfras i en befintlig Wi-Fi-profil?

Anta att du skapar en Wi-Fi-profil för ett företag, distribuerar profilen till en grupp, ändrar lösenordet och sparar profilen. När profilen ändras får vissa användare inte den nya profilen.

Du kan undvika det här problemet genom att ställa in gäst-Wi-Fi. Om inte företagets Wi-Fi fungerar kan användarna ansluta till gäst-Wi-Fi. Se till att du aktiverar inställningarna för automatisk anslutning. Distribuera gäst-Wi-Fi-profilen till alla användare.

Ytterligare rekommendationer:  

- Om Wi-Fi-nätverket som du ansluter till använder ett lösenord eller en lösenfras, ser du till att du kan ansluta direkt till Wi-Fi-routern. Du kan testa med en iOS-enhet.
- När du har lyckats ansluta till Wi-Fi-slutpunkten (Wi-Fi-routern) noterar du SSID och autentiseringsuppgifter som används (det här värdet är lösenordet eller lösenfrasen).
- Ange SSID och autentiseringsuppgifter (lösenord eller lösenfras) i fältet I förväg delad nyckel. 
- Distribuera till en testgrupp som har ett begränsat antal användare, gärna endast till IT-avdelningen. 
- Synkronisera iOS-enheten mot Intune. Registrera om du inte redan har gjort det. 
- Testa att ansluta till samma Wi-Fi-slutpunkt (som nämns i det första steget) igen.
- Distribuera till större grupper och till slut till alla förväntade användare i organisationen. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>Hur lång tid tar det innan principerna, profilerna eller apparna når enheterna efter att de har tilldelats?

Senaste gången Intune aviserade enheten om att checka in på Intune. Aviseringstiderna varierar, ibland upp till flera timmar. Dessa aviseringstider varierar också mellan olika plattformar.

Om enheten inte checkar in för att hämta principen eller profilen efter den första aviseringen, gör Intune ytterligare tre försök. Om enheten är offline (till exempel om den är avstängd eller inte är ansluten till ett nätverk) kanske den inte får aviseringarna. I så fall får enheten principen eller profilen vid nästa schemalagda incheckning på Intune-tjänsten, enligt följande **uppskattning**:

| Plattform | Uppdateringscykel|
| --- | --- |
| iOS | Ungefär var 8:e timme |
| macOS | Ungefär var 8:e timme |
| Android | Ungefär var 8:e timme |
| Windows 10-datorer som registrerats som enheter | Ungefär var 8:e timme |
| Windows Phone | Ungefär var 8:e timme |
| Windows 8,1 | Ungefär var 8:e timme |

Om enheten nyligen har registrerats sker efterlevnads- och konfigurationsincheckningarna oftare, vilket **uppskattas** till cirka:

| Plattform | Frekvens |
| --- | --- |
| iOS | Var 15:e minut i 1 timmar och därefter var omkring 8:e timme |  
| macOS | Var 15:e minut i 1 timmar och därefter var omkring 8:e timme | 
| Android | Var 3:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan omkring var 8:e timme | 
| Windows 10-datorer som registrerats som enheter | Var 3:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan omkring var 8:e timme | 
| Windows Phone | Var 5:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan omkring var 8:e timme | 
| Windows 8,1 | Var 5:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan omkring var 8:e timme | 

Användarna kan när de vill öppna företagsportalappen, **Inställningar** > **Synkronisera** för att omedelbart söka efter profil- eller principuppdateringar.

För enheter utan användartillhörighet kan synkroniseringsfrekvensen omedelbart efter registreringen variera mellan några timmar till en dag eller mer. Intune skickar begäranden med olika intervall för att en enhet ska kunna checka in på Intune. Det är dock fortfarande enheten som måste checka in. Efter den första registreringen är det svårt att veta hur lång tid det tar att slutföra incheckningen. Det beror också på typen av enhetsregistrering och de principer och profiler som har tilldelats till en enhet. När enheten har registrerats och alla inledande principer och profiler har tillämpats söker enheten efter nya principer och profiler om var 6–8: e timme, baserat på när enheten registrerar i Intune.

Vi rekommenderar att du kontrollerar att enheterna är online i minst åtta timmar i följd för att få bästa möjliga resultat.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Vilka åtgärder gör att Intune genast skickar en avisering till en enhet?

Det finns olika åtgärder som utlöser en aviseringe, till exempel när en princip, profil eller app tilldelas (eller tilldelningen tas bort), uppdateras, tas bort och så vidare. De här åtgärdstiderna varierar mellan olika plattformar.

Enheter checkar in på Intune när de får en avisering eller enligt schemalagda intervall. När du riktar en åtgärd mot en enhet eller användare, t.ex. en låsning, återställning av lösenord, app, profil- eller principtilldelning, meddelar Intune genast enheten att den ska checka in för att få dessa uppdateringar.

Andra ändringar, t.ex. en uppdatering av kontaktinformationen på företagsportalappen, utlöser inte en omedelbar avisering till enheter.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Hur vet jag vilka inställningar som tillämpas om flera principer tilldelas samma användare eller enhet?

När två eller fler principer tilldelas samma användare eller enhet, tillämpas den inställning som angivits på enskild inställningsnivå:

- Inställningar för efterlevnadsprinciper har alltid högre prioritet än inställningar för konfigurationsprofiler.

- Om en efterlevnadsprincip utvärderas mot samma inställning i en annan efterlevnadsprincip, tillämpas den mest restriktiva efterlevnadsprincipen.

- Om en inställning av en konfigurationsprincip hamnar i konflikt med en inställning i en annan konfigurationsprincip, visas konflikten i Intune. Lös dessa konflikter manuellt.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Vad händer när appskyddsprinciper står i konflikt med varandra? Vilken används för appen?

Konfliktvärden är de mest restriktiva inställningarna som är tillgängliga i en appskyddsprincip, *förutom* fälten för nummerinmatning (t.ex. antal PIN-försök före återställning). Nummerinmatningsfälten ställs in på samma sätt som när du skapar en MAM-princip med alternativet för rekommenderade inställningar.

Konflikter uppstår om två profilinställningar är likadana. Anta att du har konfigurerat två MAM-principer som är identiska förutom inställningen för kopiera/klistra in. I detta scenario används det mest restriktiva värdet för kopierings- och inklistringsinställningen, men resten av inställningarna tillämpas så som de konfigurerats.

En princip distribueras till appen och börjar gälla. En andra princip distribueras. I det här scenariot får den första principen företräde och fortsätter att tillämpas. Den andra principen visar en konflikt. Om båda tillämpas samtidigt, och det inte finns någon föregående princip, kommer båda att vara i konflikt. Som med alla inställningar i konflikt tillämpas de mest restriktiva värdena.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Vad händer om anpassade iOS-principer är i konflikt med varandra?

Intune utvärderar inte nyttolasten för Apple Configuration-filer eller anpassade OMA-URI-principer (Open Mobile Alliance Uniform Resource Identifier). Den fungerar bara som själva leveransmekanismen.

När du tilldelar en anpassad princip bör du kontrollera att de konfigurerade inställningarna inte är i konflikt med efterlevnadsprinciper, konfigurationsprinciper eller andra anpassade principer. Om en anpassad princip och dess inställningar står i konflikt, tillämpas inställningarna slumpmässigt.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Vad händer när en profil tas bort eller inte längre är tillämplig?

När du tar bort en profil, eller när du tar bort en enhet från en grupp som har den profilen, tas profilen och inställningarna bort från enheten enligt följande beskrivning:

- Wi-Fi, VPN, certifikat och e-postprofiler: Dessa profiler tas bort från alla registrerade enheter som stöds.
- Alla andra profiltyper:  

  - **Windows- och Android-enheter**: Inställningarna tas inte bort från enheten
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

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Jag ändrade en enhets begränsningsprofil, men ändringarna har inte börjar gälla

När Windows Phone-enheter är konfigurerade tillåts inte att säkerheten minskas för säkerhetsprinciper som har ställts in med hjälp av MDM eller EAS. Du ställer exempelvis in **Minsta antalet tecken för lösenord** till 8. Därefter försöker du minska det till 4. Den mer restriktiva profilen har redan tillämpats för enheten.

Om du vill ändra profilen till ett mindre säkert värde återställer du säkerhetsprinciperna. I Windows 8.1. sveper du till exempel från höger på skrivbordet och väljer **Inställningar** > **Kontrollpanelen**. Välj appleten **Användarkonton** . Längst ned i den vänstra navigeringsmenyn finns länken **Återställ säkerhetsprinciper**. Markera den och välj sedan **Återställ principer**.

Andra MDM-enheter, som Android, Windows Phone 8.1 och senare, iOS och Windows 10, kan behöva dras tillbaka och sedan registreras på nytt i Intune för att du ska kunna tillämpa en mindre begränsande profil.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Vissa inställningar i en Windows 10-profil returnerar ”ej tillämpligt”

Vissa inställningar på Windows 10-enheter kan visas som ”ej tillämpligt”. När det sker stöds inte just den inställningen på den versionen eller utgåvan av Windows som körs på enheten. Meddelandet kan visas av följande orsaker:

- Inställningen är bara tillgänglig för nyare versioner av Windows och inte den aktuella versionen av operativsystem (OS) på enheten.
- Inställningen är bara tillgänglig för vissa Windows-utgåvor eller vissa SKU:er, som Home, Professional, Enterprise och Education.

Mer information om versions- och SKU-krav för olika inställningar finns i [referensartikeln för konfigurationsprovider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>Nästa steg

Behöver du mer hjälp? Se [Ta reda på hur du kan få support för Microsoft Intune](../fundamentals/get-support.md).
