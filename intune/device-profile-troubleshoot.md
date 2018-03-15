---
title: "Felsöka enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs"
description: "Vanliga problem med enhetsprofiler i Microsoft Intune i Azure Portal, till exempel angående profiländringar som inte tillämpas för vissa användare eller enheter, hur lång tid det tar för en ny princip att överföras till enheter, vilka inställningar som tillämpas när det finns flera principer och vad som händer när en profil tas bort eller flyttas"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 1/17/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73bac7c139a0dd42734ce6528172aeba2cb7b40c
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="common-issues-and-resolutions-with-device-profiles-in-microsoft-intune"></a>Vanliga problem och lösningar med enhetsprofiler i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Felsök vanliga problem med enhetsprofiler i Intune.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Varför får inte en användare en ny profil vid ändring av lösenord eller lösenfras i en befintlig Wi-Fi-profil? 
Anta att du skapar en Wi-Fi-profil för ett företag, distribuerar profilen till en grupp, ändrar lösenordet och sparar profilen. När profilen ändras får vissa användare inte den nya profilen.

Du kan undvika det här problemet genom att ställa in gäst-Wi-Fi. Om inte företagets Wi-Fi fungerar kan användarna ansluta till gäst-Wi-Fi. Se till att du aktiverar inställningarna för automatisk anslutning. Distribuera gäst-Wi-Fi-profilen till alla användare.

Ytterligare rekommendationer:  

- Eftersom Wi-Fi-nätverket du ansluter till använder ett lösenord eller en lösenfras ser du till att du kan ansluta direkt till Wi-Fi-routern. Du kan testa med en iOS-enhet.
- När du har lyckats ansluta till Wi-Fi-slutpunkten (Wi-Fi-routern) noterar du SSID och autentiseringsuppgifter som används (det här värdet är lösenordet eller lösenfrasen).
- Ange SSID och autentiseringsuppgifter (lösenord eller lösenfras) i fältet I förväg delad nyckel. 
- Distribuera till en testgrupp som har ett begränsat antal användare, gärna endast till IT-avdelningen. 
- Synkronisera iOS-enheten mot Intune. Registrera om du inte redan har gjort det. 
- Testa att ansluta till samma Wi-Fi-slutpunkt (som nämns i det första steget) igen.
- Distribuera till större grupper och till slut till alla förväntade användare i organisationen. 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>Hur lång tid tar det innan principerna eller apparna når mobilenheterna efter att de har tilldelats?
När en princip eller en app tilldelas börjar Intune genast att uppmana enheten att kontakta Intune-tjänsten. Denna avisering brukar ta mindre än fem minuter.

Om enheten inte kontaktar tjänsten för att be om principen när den första aviseringen har skickats, görs ytterligare tre försök. Om enheten är offline (till exempel om den är avstängd eller inte är ansluten till ett nätverk) kanske den inte får aviseringarna. I så fall får enheten principen vid nästa schemalagda kontakt med Intune-tjänsten enligt följande:

- iOS och macOS: var sjätte timme
- Android: var åttonde timme
- Windows Phone: var åttonde timme
- Windows 8.1- och Windows 10-datorer som har registrerats som enheter: var åttonde timme

Om enheten nyligen har registrerats sker kontrollerna oftare enligt följande:

- iOS och macOS: var 15:e minut i sex timmar och därefter var sjätte timme
- Android: var tredje minut i 15 minuter, därefter var 15:e minut i två timmar och sedan var åttonde timme
- Windows Phone: var femte minut i 15 minuter, därefter var 15:e minut i två timmar och sedan var åttonde timme
- Windows-datorer som registrerats som enheter: var tredje minut i 30 minuter och därefter var åttonde timme

Användarna kan också söka efter principer när som helst genom att öppna företagsportalappen och synkronisera enheten.

För enheter utan användartillhörighet kan synkroniseringsfrekvensen omedelbart efter registreringen variera mellan några timmar till en dag eller mer. Intune skickar begäranden med olika intervall för att en enhet ska checka in hos tjänsten. Det är dock fortfarande enheten som måste göra det. Det går inte att förutse hur lång tid det tar för en enhet att slutföra incheckningen efter den första registreringen. Tiden beror på vilken typ av enhetsregistrering och vilka principer och profiler som har tilldelats till en enhet. När enheten väl har registrerats och alla inledande principer tillämpas kontrollerar enheten normalt om det finns nya principer ungefär var sjätte timme.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Vilka åtgärder gör att Intune genast skickar en avisering till en enhet?
Enheter kontaktar Intune när de får en avisering eller enligt schemalagda intervall. När du riktar en åtgärd mot en enhet eller användare, t.ex. en rensning, låsning, återställning av lösenord, apptilldelning, profiltilldelning eller principtilldelning, meddelar Intune genast enheten att den ska kontakta Intune-tjänsten för att få dessa uppdateringar.

Andra ändringar, t.ex. en uppdatering av kontaktinformationen på företagsportalen, utlöser inte en omedelbar avisering till enheter.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Hur vet jag vilka inställningar som tillämpas om flera principer tilldelas samma användare eller enhet?
Om två eller flera principer tilldelas till samma användare eller enhet avgörs vilka inställningar som ska tillämpas på inställningsnivå:

-   Inställningar för efterlevnadsprinciper har alltid högre prioritet än inställningar för konfigurationsprinciper.

-   Om en efterlevnadsprincip utvärderas mot samma inställning i en annan efterlevnadsprincip gäller den mest restriktiva efterlevnadsprincipen.

-   Om en konfigurationsprincipinställning hamnar i konflikt med en inställning i en annan konfigurationsprincip visas konflikten i Azure Portal. I så fall löses dessa konflikter manuellt.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Vad händer när appskyddsprinciper står i konflikt med varandra? Vilken används för appen?
Konfliktvärden är de mest restriktiva inställningarna som är tillgängliga i en appskyddsprincip, förutom fälten för nummerinmatning (t.ex. PIN-försök före återställning). Nummerinmatningsfälten får samma värden som då du skapar en MAM-princip i konsolen med alternativet för rekommenderade inställningar.

Konflikter uppstår om två profilinställningar är samma. Anta att du har konfigurerat två MAM-principer som är identiska förutom inställningen för kopiera/klistra in. I detta scenario används det mest restriktiva värdet för kopierings- och inklistringsinställningen, men resten av inställningarna tillämpas så som de konfigurerats.

Om en profil tilldelas appen och börjar tillämpas, och en andra profil tilldelas senare, har den första profilen företräde och fortsätter att tillämpas, medan den andra visas som i konflikt. Om båda tillämpas samtidigt, och det inte finns någon föregående profil, kommer båda att vara i konflikt. Som med alla inställningar i konflikt tillämpas de mest restriktiva värdena.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Vad händer om anpassade iOS-principer är i konflikt med varandra?
Intune utvärderar inte nyttolasten för Apple Configuration-filer eller anpassade OMA-URI-profiler (Open Mobile Alliance Uniform Resource Identifier). Den fungerar bara som själva leveransmekanismen.

När du tilldelar en anpassad profil bör du se till att de konfigurerade inställningarna inte är i konflikt med efterlevnadsprinciper, konfigurationsprinciper eller andra anpassade principer. Om en anpassad profil och dess inställningar står i konflikt tillämpas inställningarna slumpmässigt.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Vad händer när en profil tas bort eller inte längre är tillämplig?
När du tar bort en profil, eller när du tar bort en enhet från en grupp som har den profilen, tas profilen och inställningarna bort från enheten enligt följande listor:

- Wi-Fi-, VPN-, certifikat- och e-postprofiler – De här profilerna tas bort från alla registrerade enheter som stöds.
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
        - Tillåt fabriksåterställning
        - Tillåt Bluetooth
        - Tillåt NFC
        - Tillåt Wi-Fi

    - **iOS**: Alla inställningar tas bort, utom:
        - Tillåt röstroaming
        - Tillåt dataroaming
        - Tillåt automatisk synkronisering vid roaming

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Jag ändrade en enhets begränsningsprofil, men ändringarna har inte börjar gälla
Windows Phone-enheter tillåter inte att säkerheten minskas för säkerhetsprinciper som har ställts in med hjälp av MDM eller EAS när de väl har ställts in. Som om du exempelvis ställer in **minsta antalet tecken för lösenord** till 8 och sedan försöker att minska det till 4. Den mer restriktiva profilen har redan tillämpats för enheten.

Du kan, beroende på enhetsplattform, sedan återställa säkerhetsprinciperna om du vill ändra profilen till ett mindre säkert värde. I Windows sveper du till exempel från höger på skrivbordet och väljer **Inställningar** > **Kontrollpanelen**. Välj appleten **Användarkonton** .

Längst ned på den vänstra navigeringsmenyn finns länken **Återställ säkerhetsprinciper**. Markera den och välj sedan **Återställ principer**. Andra MDM-enheter, som Android, Windows Phone 8.1 och senare och iOS, kan behöva dras tillbaka och sedan registreras på nytt för tjänsten för att du ska kunna tillämpa en mindre begränsande profil.

## <a name="next-steps"></a>Nästa steg
Behöver du mer hjälp? Se [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).