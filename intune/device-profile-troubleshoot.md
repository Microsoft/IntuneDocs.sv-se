---
title: "Felsöka enhetsprofiler i Microsoft Intune"
titlesuffix: Azure portal
description: "Om du kört fast, kan du använda det här ämnet för att hjälpa dig läsa problem med Intune-enhetsprofiler.”"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 1/17/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0bc5ad6e0467fe8a8c98c1ad2d71b967c18b8233
ms.sourcegitcommit: 967a7c23b863123398c40b812e2eb02c921a0afe
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/18/2018
---
# <a name="troubleshooting-device-profiles-in-microsoft-intune"></a>Felsöka enhetsprofiler i Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Informationen i det här avsnittet kan användas för att felsöka vanliga problem runt enhetsprofiler i Intune.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Varför får inte en användare en ny profil vid ändring av lösenord eller lösenfras i en befintlig Wi-Fi-profil? 
När du skapar en Wi-Fi-profil för ett företag, distribuerar profilen till en grupp, ändrar lösenordet och sparar profilen kanske du förväntar dig att användaren får den nya profilen. Det kan dock hända att användaren inte får den nya profilen. 

Minimera detta problem genom att se till att du har ett gäst-Wi-Fi konfigurerat så att användaren hamnar i gäst-Wi-Fi om inte företagets Wi-Fi fungerar. Inställningen för att ansluta automatiskt måste aktiveras. Den här Wi-Fi-gästprofilen måste distribueras till alla användare.

Det finns några ytterligare metoder som du kan använda:
- Eftersom Wi-Fi-nätverket du ansluter till använder ett lösenord eller en lösenfras ser du till att du kan ansluta till Wi-Fi-routern direkt. Du kan testa med en iOS-enhet.
- När du har lyckats ansluta till Wi-Fi-slutpunkten (Wi-Fi-routern) noterar du SSID och autentiseringsuppgifter som används (det här är lösenordet eller lösenfrasen).
- Ange SSID och autentiseringsuppgifter (lösenord eller lösenfras) i fältet I förväg delad nyckel. 
- Distribuera till en testgrupp som har ett begränsat antal användare, gärna endast till IT-avdelningen. 
- Synkronisera iOS-enheten mot Intune. Registrera om du inte redan har gjort det. 
- Testa att ansluta till samma Wi-Fi-slutpunkt (som nämns i det första steget) igen.
- Distribuera till större grupper och till slut till alla förväntade användare i organisationen. 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>Hur lång tid tar det innan principerna eller apparna når mobilenheterna efter att de har tilldelats?
När en princip eller app tilldelas börjar Intune genast att uppmana enheten att kontakta Intune-tjänsten. Detta brukar ta mindre än fem minuter.

Om enheten inte kontaktar tjänsten för att be om principen när den första aviseringen har skickats, görs ytterligare tre försök. Om enheten är offline (till exempel om den är avstängd eller inte är ansluten till ett nätverk) kanske den inte får aviseringarna. I så fall får enheten principen vid nästa schemalagda kontakt med Intune-tjänsten enligt följande:

- iOS och macOS: var sjätte timme.
- Android: var åttonde timme.
- Windows Phone: var åttonde timme.
- Windows 8.1- och Windows 10-datorer som har registrerats som enheter: var åttonde timme.

Om enheten precis har registrerats sker kontrollerna oftare enligt följande:

- iOS och macOS: var 15:e minut i sex timmar och därefter var sjätte timme.
- Android: var tredje minut i 15 minuter, därefter var 15:e minut i två timmar och sedan var åttonde timme.
- Windows Phone: var femte minut i 15 minuter, därefter var 15:e minut i två timmar och sedan var åttonde timme.
- Windows-datorer som registrerats som enheter: var tredje minut i 30 minuter och därefter var åttonde timme.

Användarna kan också söka efter principer när som helst genom att öppna företagsportalappen och synkronisera enheten.

För enheter utan användartillhörighet kan synkroniseringsfrekvensen omedelbart efter registreringen variera mellan några timmar till en dag eller mer. Intune skickar begäranden med olika intervall för att en enhet ska checka in hos tjänsten. Det är dock fortfarande enheten som måste göra det. Det går inte att förutse hur lång tid det tar för en enhet att slutföra den incheckningen efter den första registreringen, beroende på typ av enhetsregistrering och de principer och profiler som är tilldelade till en enhet. När enheten väl har registrerats och alla inledande principer har verkställts bör dock enheten kontrollera om det finns nya principer ungefär var sjätte timme.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Vilka åtgärder gör att Intune genast skickar en avisering till en enhet?
Enheter kontaktar Intune antingen när de får en avisering som uppmanar dem att göra det, eller enligt schemalagda intervall. När du specifikt riktar en åtgärd mot en enhet eller användare, t.ex. en rensning, låsning, återställning av lösenord, apptilldelning, profiltilldelning (Wi-Fi, VPN, e-post o.s.v.) eller principtilldelning, börjar Intune genast att försöka meddela enheten att den ska kontakta Intune-tjänsten för att få dessa uppdateringar.

Andra ändringar, t.ex. en uppdatering av kontaktinformationen på företagsportalen, utlöser inte en omedelbar avisering till enheter.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Hur vet jag vilka inställningar som tillämpas om flera principer tilldelas samma användare eller enhet?
När två eller fler principer tilldelas samma användare eller enhet så görs utvärderingen av vilken inställning som ska tillämpas på inställningsnivå:

-   Inställningar för efterlevnadsprinciper har alltid högre prioritet än inställningar för konfigurationsprinciper.

-   Den mest restriktiva efterlevnadsprincipinställningen tillämpas om den utvärderas och jämförs med samma inställning i en annan efterlevnadsprincip.

-   Om en konfigurationsprincipinställning hamnar i konflikt med en inställning i en annan konfigurationsprincip visas konflikten i Azure Portal. Du måste lösa dessa konflikter manuellt.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Vad händer när appskyddsprinciper står i konflikt med varandra? Vilken används för appen?
Konfliktvärden är de mest restriktiva inställningarna som är tillgängliga i en appskyddsprincip, förutom fälten för nummerinmatning (t.ex. PIN-försök före återställning). Nummerinmatningsfälten får samma värden som då du skapar en MAM-princip i konsolen med alternativet för rekommenderade inställningar.

Konflikter uppstår om två profilinställningar är samma. Anta att du har konfigurerat två MAM-principer som är identiska förutom inställningen för kopiera/klistra in. I detta scenario används det mest restriktiva värdet för kopierings- och inklistringsinställningen, men resten av inställningarna tillämpas så som de konfigurerats.

Om en profil tilldelas appen och börjar tillämpas, och en andra profil tilldelas senare, har den första profilen företräde och fortsätter att tillämpas, medan den andra visas som i konflikt. Om båda tillämpas samtidigt, och det inte finns någon föregående profil, kommer båda att vara i konflikt. Som med alla inställningar i konflikt tillämpas de mest restriktiva värdena.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Vad händer om anpassade iOS-principer är i konflikt med varandra?
Intune utvärderar inte nyttolasten för Apple Configuration-filer eller anpassade OMA-URI-profiler (Open Mobile Alliance Uniform Resource Identifier). Den fungerar bara som själva leveransmekanismen.

När du tilldelar en anpassad profil bör du se till att de konfigurerade inställningarna inte är i konflikt med efterlevnadsprinciper, konfigurationsprinciper eller andra anpassade principer. Om en anpassad profil har inställningar som är i konflikt med varandra tillämpas dessa inställningar i slumpmässig ordning.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Vad händer när en profil tas bort eller inte längre är tillämplig?
När du tar bort en profil, eller när du tar bort en enhet från en grupp som en profil hade tilldelats, tas profilen och inställningarna bort från enheten enligt följande listor.

### <a name="enrolled-devices"></a>Registrerade enheter

- Wi-Fi-, VPN-, certifikat- och e-postprofiler – De här profilerna tas bort från alla registrerade enheter som stöds.
- Alla andra profiltyper:
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
        - Tillåt fabriksåterställning
        - Tillåt Bluetooth
        - Tillåt NFC
        - Tillåt Wi-Fi

    - **iOS**: Alla inställningar tas bort, utom:
        - Tillåt röstroaming
        - Tillåt dataroaming
        - Tillåt automatisk synkronisering vid roaming

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Jag ändrade en enhets begränsningsprofil, men ändringarna har inte börjar gälla
Windows Phone-enheter tillåter inte att säkerheten minskas för säkerhetsprinciper som har ställts in via MDM eller EAS när de väl har ställts in. Som om du exempelvis ställer in **minsta antalet tecken för lösenord** till 8 och sedan försöker att minska det till 4. Den mer restriktiva profilen har redan tillämpats för enheten.

Du kan, beroende på enhetsplattform, vara tvungen att återställa säkerhetsprinciperna om du vill ändra profilen till ett mindre säkert värde.
I Windows sveper du till exempel in från höger på skrivbordet så öppnas menyraden för **Snabbknappar** och väljer **Inställningar** &gt; **Kontrollpanelen**. Välj appleten **Användarkonton** .
På den vänstra navigeringsmenyn finns länken **Återställ säkerhetsprinciper** längst ned. Välj den och klicka sedan på **Återställ principer**.
Andra MDM-enheter, som Android, Windows Phone 8.1 och senare och iOS, kan behöva dras tillbaka och sedan registreras på nytt för tjänsten för att du ska kunna tillämpa en mindre begränsande profil.


### <a name="next-steps"></a>Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).