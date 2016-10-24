---
title: "Felsökningsprinciper | Microsoft Intune"
description: "Felsöka problem med principkonfiguration."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e95db6d0ccbe350984f11ce08749b700c2f5ad01
ms.openlocfilehash: fbc18b12c00a4b61f7419731c6b4306b583638cc


---

# Felsökningsprinciper i Microsoft Intune

Börja här om du har problem med att distribuera och hantera principer med Intune. Det här avsnittet innehåller några vanliga problem du kan stöta på samt lösningar på problemen.

## Allmänna frågor

### Har en distribuerad princip tillämpats på enheten?
**Problem:** Du är osäker på om en princip har tillämpats korrekt.

I Intune-administratörskonsolen har varje enhet en principflik under **Egenskaper för enhet**. Varje princip har ett **Avsett värde** och en **Status**. Det avsedda värdet är vad du hade för avsikt att uppnå när du tilldelade principen. Statusen är vad som i själva verket har tillämpats när samtliga principer som gäller för enheten och de begränsningar och krav som gäller för maskinvara och operativsystem bedöms tillsammans. Möjliga statusar:

-   **Överensstämmer**: Enheten har tagit emot principen och rapporterar till tjänsten att den överensstämmer med inställningen.

-   **Inte tillämpligt**: Principinställningen är inte tillämplig. Till exempel kan e-postinställningar för iOS-enheter inte tillämpas för en Android-enhet.

-   **Väntar**: Principen skickades till enheten men har inte rapporterat statusen till tjänsten. Exempelvis kräver kryptering på Android att användaren aktiverar kryptering och kan därför vara ”väntande”.

På skärmbilden nedan ser du två tydliga exempel:

-   **Tillåt enkla lösenord** har getts värdet **Ja**, vilket kan ses i kolumnen **Avsett värde** , men dess **Status** är **Saknas**. Detta beror på det faktum att enkla lösenord inte stöds för Android-enheter.

-   Den utökade principposten **E-postinställningar för iOS-enheter** tillämpas inte heller på den här enheten, eftersom det är en Android-enhet.

![Intune-enhetsprincip](../media/Intune-Device-Policy-v.2.jpg)

> [!NOTE]
> Kom ihåg att om två principer med olika begränsningsnivåer tillämpas på samma enhet eller användare, så tillämpas i praktiken den mer restriktiva principen.


## Problem med registrerade enheter

### Avisering: Det gick inte att spara åtkomstregler i Exchange
**Problem**: Du får aviseringen **Det gick inte att spara åtkomstregler i Exchange**  i administrationskonsolen.

Om du har skapat principer på arbetsytan Exchange On-premises-princip under administrationskonsolen men använder O365, tillämpas inte de konfigurerade principinställningarna av Intune. Observera principkällan från aviseringen.  Ta bort de gamla reglerna under arbetsytan för Exchange On-premises-princip då dessa är globala Exchange-regler i Intune för lokal Exchange och inte är relevanta för O365. Skapa sedan en ny princip för O365.

### Det går inte att ändra säkerhetsprincipen för olika registrerade enheter
Windows Phone-enheter tillåter inte att säkerheten minskas för säkerhetsprinciper som har ställts in via MDM eller EAS när de väl har ställts in. Som om du exempelvis ställer in **minsta antalet tecken för lösenord** till 8 och sedan försöker att minska det till 4. Den mer restriktiva principen har redan tillämpats för enheten.

Du kan, beroende på enhetsplattform, vara tvungen att återställa säkerhetsprinciperna om du vill ändra principen till ett mindre säkert värde.
I Windows sveper du till exempel in från höger på skrivbordet så öppnas menyraden för **Snabbknappar** och väljer **Inställningar** &gt; **Kontrollpanelen**.  Välj appleten **Användarkonton** .
I den vänstra navigeringsmenyn finns länken **Återställ säkerhetsprinciper** längst ned. Välj den och klicka sedan på **Återställ principer**.
Andra MDM-enheter, som Android, Windows Phone 8.1 och senare och iOS, kan behöva dras tillbaka och sedan registreras på nytt för tjänsten för att du ska kunna tillämpa en mindre begränsande princip.

## Problem med datorer som kör Intune-programklienten

### Principrelaterade Microsoft Intune-fel i policyplatform.log
För Windows-datorer som hanteras med Intune-programklienten kan principfel i filen policyplatform.log bero på att andra inställningar än standardinställningarna används i Windows User Account Control (UAC) på enheten. Andra inställningar än UAC-standardinställningarna kan påverka Microsoft Intune-klientinstallationer och principkörning.

#### Så här löser du problem i UAC

1.  Dra tillbaka datorn genom att följa anvisningarna i [Dra tillbaka enheter från hantering i Microsoft Intune](/intune/deploy-use/retire-devices-from-microsoft-intune-management).

2.  Vänta 20 minuter tills klientprogrammet har tagits bort.

    > [!NOTE]
    > Försök inte att ta bort klienten från Program och funktioner.

3.  Skriv **UAC** på startmenyn för att öppna inställningarna för User Account Control.

4.  Dra meddelandereglaget till standardinställningen.

### Fel: Det går inte att hämta värdet från datorn, 0x80041013
Detta kan inträffa om tiden på det lokala systemet är felsynkroniserat med fem minuter eller mer. Om tiden på den lokala datorn inte är rätt synkroniserad misslyckas säkra transaktioner eftersom tidsstämplarna blir ogiltiga.

Du löser problemet genom att ange en tid i det lokala systemet så nära Internettiden som möjligt, eller genom att ange tiden på domänkontrollanterna i nätverket.








### Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Oct16_HO2-->


