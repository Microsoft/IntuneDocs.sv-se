---
title: Felsöka principer i Microsoft Intune – Azure | Microsoft Docs
description: Vanliga problem och lösningar vid användning av principer i Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1d656dcc8c3abcf3a4b0a9c6aacbc42eb896289f
ms.sourcegitcommit: 7c70c3e0fcae7c4fa8c9e108aafb1cebb366332d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/07/2018
ms.locfileid: "44096511"
---
# <a name="troubleshoot-policies-in-intune"></a>Felsöka principer i Intune

Börja här om du har problem med att distribuera och hantera Intune-principer. Den här artikeln tar upp några vanliga problem som kan uppstå och möjliga lösningar.

## <a name="general-issues"></a>Allmänna frågor

### <a name="was-a-deployed-policy-applied-to-the-device"></a>Har en distribuerad princip tillämpats på enheten?
**Problem:** Du är osäker på om en princip tillämpas korrekt.

I Intune > **Enheter** > **Alla enheter** > välj enheten > **Enhetskonfiguration**, varje enhet visar dess principer. Varje princip har en **Status**. Statusen tillämpas när samtliga principer som gäller för enheten, inklusive begränsningarna och kraven som gäller för maskinvara och operativsystem, bedöms tillsammans. Möjliga statusar:

- **Överensstämmer**: Enheten har tagit emot principen och rapporterar till tjänsten att den överensstämmer med inställningen.

- **Inte tillämplig**: Principinställningen är inte tillämplig. Till exempel är e-postinställningar för iOS-enheter inte tillämpliga för Android-enheter.

- **Väntar**: Principen har skickats till enheten men har inte rapporterat statusen till tjänsten. Till exempel kräver kryptering på Android användaraktivering, vilket kan leda till att krypteringen väntar.

> [!NOTE]
> Om två principer med olika begränsningsnivåer tillämpas på samma enhet eller användare, tillämpas den mer restriktiva principen.

## <a name="issues-with-enrolled-devices"></a>Problem med registrerade enheter

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Avisering: Det gick inte att spara åtkomstregler i Exchange
**Problem**: Du får aviseringen **Det gick inte att spara åtkomstregler i Exchange**  i administrationskonsolen.

Om du har skapat principer på arbetsytan Exchange On-premises-princip under administrationskonsolen men använder O365, tillämpas inte de konfigurerade principinställningarna av Intune. Observera principkällan från aviseringen.  Ta bort de gamla reglerna under arbetsytan Exchange On-premises-princip. De gamla reglerna är globala Exchange-regler i Intune för lokal Exchange och är inte relevanta för O365. Skapa sedan en ny princip för O365.

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>Det går inte att ändra säkerhetsprincipen för olika registrerade enheter
Windows Phone-enheter tillåter inte att säkerheten minskas för säkerhetsprinciper som har ställts in via MDM eller EAS när de väl har ställts in. Som om du exempelvis ställer in **minsta antalet tecken för lösenord** till 8 och sedan försöker att minska det till 4. Den mer restriktiva principen har redan tillämpats för enheten.

Du kan, beroende på enhetsplattform, vara tvungen att återställa säkerhetsprinciperna om du vill ändra principen till ett mindre säkert värde.

I Windows sveper du till exempel från höger på skrivbordet för att öppna menyraden för **Snabbknappar**. Välj **Inställningar** > **Kontrollpanelen** och sedan **Användarkonton**. Till vänster väljer du länken **Återställ säkerhetsprinciper** och sedan **Återställ principer**.

Andra MDM-enheter, som Android, Windows Phone 8.1 och senare samt iOS, kan behöva tas ur bruk och sedan registreras på nytt i tjänsten för att en mindre begränsande profil ska kunna tillämpas.

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Problem med datorer som kör Intune-programklienten

Gäller för klassiska portalen.

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Principrelaterade Microsoft Intune-fel i policyplatform.log
För Windows-datorer som hanteras med Intune-programklienten kan principfel i filen policyplatform.log bero på att andra inställningar än standardinställningarna används i Windows User Account Control (UAC) på enheten. Andra inställningar än UAC-standardinställningarna kan påverka Microsoft Intune-klientinstallationer och principkörning.

#### <a name="resolve-uac-issues"></a>Lösa problem med UAC

1. Ta datorn ur bruk. Se [Ta bort enheter](devices-wipe.md).

2. Vänta 20 minuter tills klientprogrammet har tagits bort.

    > [!NOTE]
    > Försök inte att ta bort klienten från Program och funktioner.

3. Skriv **UAC** på startmenyn för att öppna inställningarna för User Account Control.

4. Dra meddelandereglaget till standardinställningen.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>Fel: Det går inte att hämta värdet från datorn, 0x80041013
Inträffar om tiden på det lokala systemet är felsynkroniserat med fem minuter eller mer. Om tiden på den lokala datorn inte är rätt synkroniserad misslyckas säkra transaktioner eftersom tidsstämplarna blir ogiltiga.

Du löser problemet genom att ange en tid i det lokala systemet så nära Internettiden som möjligt, eller genom att ange tiden på domänkontrollanterna i nätverket.

### <a name="next-steps"></a>Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen, kontaktar du Microsoft Support enligt [få support för Microsoft Intune](get-support.md).
