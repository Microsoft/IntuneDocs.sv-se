---
title: "Felsöka villkorlig åtkomst| Microsoft Intune"
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4f79d2890c450a803bfb84ffa3c12b0de58a158c
ms.openlocfilehash: 373b9bf9794840f999d5e5b21fc411ff621a23e1


---

# Felsöka villkorlig åtkomst

I det här avsnittet beskrivs vad du kan göra om användarna inte kan få åtkomst till resurser via villkorlig åtkomst i Intune. 

### Grunder i hur du får en lyckad villkorlig åtkomst

För att villkorlig åtkomst ska fungera måste följande villkor uppfyllas:

-   Enheten måste hanteras av Intune.
-   Användaren måste vara registrerad i Azure Active Directory.
-   Enheten måste vara kompatibel med de efterlevnadsprinciper som du konfigurerat i Intune. 
-   EAS måste vara aktiverat på enheten om användaren tar emot e-post via enhetens inbyggda e-postklient i stället för via Outlook.

Du kan se dessa villkor för varje enhet i Azure-hanteringsportalen och i inventeringsrapporten för enheten.





Vanligtvis försöker en användare få åtkomst till e-post eller SharePoint och får då ett meddelande med en uppmaning om att registrera enheten. Meddelandet dirigerar användaren till företagsportalen. Här några förklaringar till varför detta sker och förslag på lösningar:

## Scenarier för modern autentisering

### Registreringsproblem

 -  Enheten är inte registrerad. Problemet kan åtgärdas genom att registrera enheten.
 -  Användaren har registrerat enheten men anslutningen till arbetsplatsen misslyckades. Användaren bör uppdatera registreringen från företagsportalen. 
 
### Efterlevnadsproblem

 -  Enheten uppfyller inte kraven för Intune-principen. Vanliga problem är krav på kryptering och lösenord. Användaren omdirigeras till företagsportalen där de kan konfigurera enheten så att den uppfyller kraven.
 -  I iOS-enheter blockeras distributionen av en kompatibel profil (som skapats av Intune-administratören) av en befintlig e-postprofil som skapats av användaren. Det här är ett vanligt problem eftersom iOS-användare vanligtvis skapar en e-postprofil och sedan gör registreringen. Företagsportalen informerar användaren om att de inte uppfyller kraven på grund av den manuellt konfigurerade e-postprofilen, och användaren uppmanas att ta bort profilen. Användaren bör ta bort e-postprofilen så att Intune-profilen kan distribueras. För att förhindra det här problemet ber du användarna att göra registreringen utan att installera en e-postprofil så att Intune kan distribuera profilen.  
 -  Det kan ta en stund innan efterlevnadsinformationen har registrerats för enheten. Vänta några minuter och försök igen.

### Principfrågor

När du skapar en efterlevnadsprincip och länkar den till en e-postprincip måste båda principerna distribueras till samma användare. Därför bör du tänka dig för när du planerar vilka principer som ska distribueras till olika grupper. Användare med endast en tillämpad princip märker troligtvis att deras enheter inte uppfyller kraven.


## Scenarier för Exchange ActiveSync


- En Android-enhet som är registrerad och uppfyller efterlevnadskraven kan fortfarande få ett karantänmeddelande när de försöker komma åt företagsresurser. Innan användarna väljer länken **Börja** måste de se till att företagsportalen inte är öppen när de försöker komma åt resurserna. Användarna måste stänga företagsportalen, försöka att få åtkomst till resurserna på nytt och sedan välja länken **Börja**.

- En pensionerad enhet kan fortfarande ha åtkomst flera timmar efter att den tagits bort. Det beror på att Exchange cachelagrar åtkomsträttigheter i 6 timmar. Överväg andra sätt att skydda data på pensionerade enheter i det här scenariot.
- Möjligt problem: det går inte att korrigera EASID till AAD. Begränsning är en vanlig orsak till detta problem. Vänta några minuter och försök igen. 

## Samla in OWA-postlådeloggar

Om Exchange-anslutningsproblemen kvarstår efter att du felsökt distributionen samlar du in OWA-postlådeloggarna innan du kontaktar Microsoft Support enligt beskrivningen i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

1. Logga in via OWA och välja inställningsikonen (kugghjulet) bredvid ditt namn i det övre högra hörnet. 
2. Välj **Alternativ**.
3. Välj **Telefon** (det kan stå **Mobila enheter**) i kolumnen till vänster.
4. Välj **Mobila enheter** på den översta menyn. 
5. Välj en enhet i listan och sedan **Starta loggning**. 
6. Välj **Ja** i popup-fönstret. 
7. Utför den åtgärd som har orsakat problemet, så att du kan återskapa det. 
8. Vänta 1 till 2 minuter och gå sedan tillbaka till telefonlistan i OWA (kontrollera att din telefon är markerad i listan) och välj **Hämta logg** på den översta menyn. 
9. Nu får du ett e-postmeddelande med en bilaga från dig själv. När du skapar ett supportärende anger du innehållet i e-postmeddelandet till Microsoft Support.


### Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Jun16_HO4-->


