---
title: Endpoint Protection för Windows-datorer
titleSuffix: Microsoft Intune
description: Skydda dina hanterade datorer med Endpoint Protection och få realtidsskydd mot skadlig kod.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 002241bf-6cd0-4c75-a4f0-891ac7e6721a
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: c19c02c8d4c9ece66d03b3510071bb90e7f35ad3
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047522"
---
# <a name="help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune"></a>Skydda Windows-datorer med Endpoint Protection för Microsoft Intune

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Microsoft Intune kan hjälpa dig att skydda dina hanterade datorer med Endpoint Protection som ger realtidsskydd mot skadlig kod, bibehåller uppdaterade definitioner för skadlig kod och skannar datorer automatiskt. Endpoint Protection innehåller dessutom verktyg som hjälper dig att hantera och övervaka angrepp från skadlig kod.

Om du ännu inte har installerat Intune-klienten på dina datorer, se [Installera Windows PC-klienten med Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Använd informationen i de följande avsnitten som hjälp när du konfigurerar, distribuerar och övervakar Endpoint Protection.

## <a name="choose-when-to-use-endpoint-protection"></a>Välj när Endpoint Protection ska användas
Som IT-administratör är en av dina högsta prioriteter att hålla datorer som du hanterar fria från skadlig programvara och virus. Innan du distribuerar Intune på Windows-datorerna i din organisation bör du bestämma hur datorerna ska skyddas genom att välja ett av följande alternativ och konfigurera inställningarna för associerade principer:


|                                                                                                                                                                       Du vill:                                                                                                                                                                        |                                                                                                       Principinställningar för Endpoint Protection                                                                                                        |                                                                                                                                                  Mer information                                                                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                             Använd Microsoft Intune Endpoint Protection endast när inget slutpunktsskyddsprogram från tredje part har installerats.<br /><br />Du kan använda Microsoft Intune Endpoint Protection på alla datorer där ett slutpunktsskyddsprogram från tredje part inte har installerats.                                              | Installera Endpoint Protection = <strong>Ja</strong><br /><br />Aktivera Endpoint Protection = <strong>Ja</strong><br /><br />Installera Endpoint Protection även om ett slutpunktsskyddsprogram från tredje part har installerats = <strong>Nej</strong>  |                                                                      Om ett slutpunktsskyddsprogram från tredje part upptäcks är Microsoft Intune Endpoint Protection inte installerat, alternativt avinstallerat om det tidigare var installerat.                                                                       |
| Använd Microsoft Intune Endpoint Protection även om ett slutpunktsskyddsprogram från tredje part har installerats.<br /><br />Med den här metoden körs Microsoft Intune Endpoint Protection och ett slutpunktsskyddsprogram från tredje part parallellt. Eftersom detta kan medföra sämre prestanda rekommenderar vi inte en sådan konfiguration. | Installera Endpoint Protection = <strong>Ja</strong><br /><br />Aktivera Endpoint Protection = <strong>Ja</strong><br /><br />Installera Endpoint Protection även om ett slutpunktsskyddsprogram från tredje part har installerats = <strong>Ja</strong> |                        Använd när:<br /><br />- Du vill växla till att använda Microsoft Intune Endpoint Protection.<br />- Du distribuerar en ny klient som ska använda Microsoft Intune Endpoint Protection.<br />- Du uppgraderar en klient som ska använda Microsoft Intune Endpoint Protection                         |
|                                                                                                             Använd Intune utan Microsoft Intune Endpoint Protection. Istället kommer du förlita dig på ett slutpunktsskyddsprogram från tredje part.                                                                                                             |                                                                                                Installera Endpoint Protection = <strong>Nej</strong>                                                                                                 | Om du inte använder ett slutpunktsskyddsprogram från tredje part rekommenderas inte den här konfigurationen eftersom den kan uttsätta organisationens datorer för skadlig programvara eller andra attacker.<br /><br />Microsoft Intune Endpoint Protection installeras inte och avinstalleras om det har installerats tidigare. |

Om du vill växla från ditt aktuella slutpunktsskydd till Microsoft Intune Endpoint Protection, gör du följande:

1.  Låt ditt aktuella slutpunktsskyddprogram köra medan du distribuerar Intune-klientprogramvaran på dessa datorer.

2.  Bekräfta att Microsoft Intune Endpoint Protection har installerats och skyddar klientdatorerna.

3.  Ta bort från slutpunktsskyddprogram från tredje part så här:

    -   Installera ett avinstallationsverktyg med hjälp av programvarudistribution för Intune som tillhandahålls av tillverkaren av slutpunktsskyddprogrammet. Mer information finns i [Distribuera appar med Microsoft Intune](apps-deploy.md).

    -   Ta bort från slutpunktsskyddprogram från tredje part manuellt så här:

> [!NOTE]
> Intune kommer inte att avinstallera slutpunktsskyddprogram från tredje part automatiskt.

## <a name="configure-microsoft-intune-endpoint-protection"></a>Konfigurera Microsoft Intune Endpoint Protection
Använd följande steg när du konfigurerar Endpoint Protection för Microsoft Intune.

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/) väljer du **Princip** > **Lägg till princip**.

2.  Expandera **Datorhantering** och välj sedan **Inställningar för Microsoft Intune Agent**. Välj **Skapa och distribuera en anpassad princip** för att ange en princip för Endpoint Protection-inställningar. Tryck sedan på knappen **Skapa princip**.

Du kan använda de rekommenderade inställningarna eller anpassa inställningarna. Om du behöver mer information om hur du skapar och distribuerar principer läser du artikeln [Vanliga hanteringsuppgifter för Windows-datorer med Microsoft Intune-datorklienten](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

  ![Endpoint Protection-inställningar](media/pol-sa-pc-endpoint-policy.png)

Du kan visa den distribuerade principen för Endpoint Protection på sidan **Alla principer** på arbetsytan **Principer**.

## <a name="specify-endpoint-protection-service-settings"></a>Specificera Serviceinställningar för Endpoint Protection

|                                                 Principinställningar                                                  |                                                                                                                                                                                                                                                                                                                                                                                                             Information                                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                  <strong>Installera Endpoint Protection</strong>                                   | Ställ in på <strong>Ja</strong> för att installera Endpoint Protection på hanterade datorer. Om ett slutpunktsskyddsprogram från tredje part upptäcks under installationen kan Endpoint Protection inte installeras om inte inställningen <strong>Installera Endpoint Protection även om ett slutpunktsskyddsprogram från tredje part har installerats</strong> har angetts till <strong>Ja</strong>. <strong>Obs!</strong> Intune Endpoint Protection installeras på hanterade datorer som standard. Om du inte vill installera Endpoint Protection på hanterade datorer måste du uttryckligen ställa in principen till <strong>Nej</strong>. Om Endpoint Protection redan har installerats och principen uppdateras till <strong>Nej</strong> kommer Endpoint Protection-klienten att avinstalleras.<br />Rekommenderat värde: <strong>Ja</strong> |
| <strong>Installera Endpoint Protection även om ett slutpunktsskyddsprogram från tredje part har installerats</strong> |                                                                                                                                                                                                                                                                                                                Ställa in på <strong>Ja</strong> för att installera Microsoft Intune Endpoint Protection även om ett slutpunktsskyddsprogram från tredje part har identifierats.<br /><br />Rekommenderat värde: <strong>Ja</strong>                                                                                                                                                                                                                                                                                                                |
|                                   <strong>Aktivera Endpoint Protection</strong>                                   |                                                                                                                                                                                                            Ange till <strong>Ja</strong> för att aktivera Microsoft Intune Endpoint Protection på datorer som har Endpoint Protection-klienten.<br /><br />Om värdet är <strong>Nej</strong> och Microsoft Intune Endpoint Protection har installerats kommer Endpoint Protection-klientens användargränssnitt inte att visas för användare och alla skyddsfunktioner kommer att avaktiveras.<br /><br />Rekommenderat värde: <strong>Ja</strong>                                                                                                                                                                                                             |
|                                       <strong>Inaktivera klientens användargränssnitt</strong>                                        |                                                                                                                                                                                                                                                                                                      Ställ in på <strong>Ja</strong> om du vill dölja Microsoft Intune Endpoint Protection-klientens användargränssnitt från användare (kräver en omstart av klienten för att träda i kraft).<br /><br />Rekommenderat värde: <strong>Nej</strong>                                                                                                                                                                                                                                                                                                       |
| <strong>Installera Endpoint Protection även om ett slutpunktsskyddsprogram från tredje part har installerats</strong> |                                                                                                                                                                                                                                                                                                       Ställ in på <strong>Ja</strong> för att tvinga igenom installationen av Microsoft Intune Endpoint Protection även om ett slutpunktsskyddsprogram från tredje part har identifierats.<br /><br />Rekommenderat värde: <strong>Nej</strong>                                                                                                                                                                                                                                                                                                       |
|                    <strong>Skapa systemåterställningspunkt före korrigering av skadlig kod</strong>                    |                                                                                                                                                                                                                                                                                                                                 Ange till <strong>Ja</strong> att skapa en återställningspunkt för Windows-systemet innan du påbörjar åtgärder mot skadlig kod.<br /><br />Rekommenderat värde: <strong>Ja</strong>                                                                                                                                                                                                                                                                                                                                  |
|                                 <strong>Spåra löst skadlig kod (dagar)</strong>                                  |                                                                                                                                                                                                                                                                                      Gör att Endpoint Protection kan spåra skadlig kod som har åtgärdats under en viss tid så att du kan kontrollera datorer som har påverkats tidigare manuellt.<br /><br />Du kan ange ett värde mellan 0 och 30 dagar.<br /><br />Rekommenderat värde: <strong>7 dagar</strong>                                                                                                                                                                                                                                                                                       |

Om du har ställt in principvärden för inställningarna **Installera Endpoint Protection** och **Aktivera Endpoint Protection** till **Ja** och principvärdet för **Installera Endpoint Protection även om ett slutpunktsskyddsprogram från tredje part har installerats** som **Nej**, kommer Microsoft Intune Endpoint Protection att identifiera att en annat program för slutpunktsskydd har installerats. Det innebär att Endpoint Protection inte kommer att installeras, eller avinstalleras om det redan är installerat. Microsoft Intune Endpoint Protection rapporterar dock om hälsotillståndet för det andra programmet för slutpunktsskydd i Intune.

  Microsoft Security Essentials aviserar dig med realtidsskydd när potentiella hot, till exempel virus och spionprogram, försöker installeras eller köras på datorn. Den tidpunkt då det händer visas ett meddelande i meddelandefältet till höger i aktivitetsfältet.

### <a name="specify-real-time-protection-settings"></a>Specificera inställningar för realtidsskydd

|Principinställningar|Information|
|------------------|--------------------|
|**Aktivera realtidsskydd**|Aktiverar övervakning och skanning för alla filer och program som nås. Blockerar också skadliga filer och program innan de kan köras på datorer.<br /><br />Rekommenderat värde: **Ja**|
|**Sök igenom alla hämtningar**|Aktiverar skanning av alla filer och bifogade filer som hämtas från internet till datorer.<br /><br />Rekommenderat värde: **Ja**|
|**Övervaka fil- och programaktivitet på datorer**|Aktiverar övervakning av inkommande och utgående filer samt programaktivitet på datorer. Med den här inställningen kan Endpoint Protection övervaka när filer och program startar och varnar om att åtgärder som de vidtar eller åtgärder som vidtas på dem.<br /><br />Rekommenderat värde: **Ja**|
|**Övervakade filer**|Låter dig välja om endast inkommande, endast utgående eller om alla filer ska övervakas.<br /><br />Rekommenderat värde: **Övervaka alla filer**|
|**Aktivera prestandaövervakning**|Gör det möjligt för Microsoft Intune Endpoint Protection att kontrollera vissa mönster på misstänkt aktivitet på klientdatorer.<br /><br />Rekommenderat värde: **Ja**|
|**Aktivera kontrollsystem för nätverk**|Aktiverar kontrollsystem för nätverk (NIS) på klientdatorer. NIS använder signaturer för kända problem från [Microsoft Malware Protection Center](https://go.microsoft.com/fwlink/?LinkId=234249) för att identifiera och blockera skadlig nätverkstrafik.<br /><br />Rekommenderat värde: **Ja**|

  ![Realtidsinställningar för Endpoint Protection](media/pol-sa-pc-policy-realtime.png)

### <a name="specify-scan-schedule-settings"></a>Specificera inställningar för schemalagd skanning

|Principinställningar|Mer information|
|------------------|--------------------|
|**Schemalägg daglig snabbsökning**|Schemalägger en daglig snabbgenomgång av både vanliga och viktiga systemfiler på datorer. Den här snabbgenomgången har minimal inverkan på prestandan.<br /><br />Rekommenderat värde: **Ja**|
|**Kör en snabbsökning om du har missat två fullständiga sökningar i rad**|Konfigurerar Endpoint Protection för att köra en snabbskanning på datorer automatiskt om de har missat två på varandra följande snabbskanningar.<br /><br />Rekommenderat värde: **Ja**|
|**Schemalägg fullständig sökning**|Konfigurerar en fullständig skanning av alla filer och resurser på de lokala datorernas hårddiskar. Skanningen kan ta tid och kan påverka datorprestandan (hur lång tid det tar beror på hur många filer och resurser som genomsöks).<br /><br />Rekommenderat värde: **Nej**|
|**Kör en fullständig sökning om du har missat två fullständiga sökningar i rad**|Konfigurerar Endpoint Protection för att köra en fullständig skanning på datorer automatiskt om de har missat två på varandra följande skanningar.<br /><br />Rekommenderat värde: Inte konfigurerat|

### <a name="specify-scan-options-settings"></a>Specificera inställningar för skanning

|Principinställningar|Information|
|------------------|--------------------|
|**Kör en fullständig sökning när Endpoint Protection har installerats**|Ange som **Ja** för att låta Endpoint Protection att köra en fullständig skanning automatiskt när det har installerats på datorerna. Skanningen körs endast när datorerna är inaktiva för att minimera effekten på produktiviteten för användaren.<br /><br />Rekommenderat värde: **Ja**|
|**Kör en fullständig sökning automatiskt när borttagning av skadlig programvara kräver uppföljning**|Ange till **Ja** så att Endpoint Protection automatiskt genomsöker hela systemet på datorer efter borttagning av skadlig kod för att bekräfta att andra filer inte påverkas.<br /><br />Rekommenderat värde: **Ja**|
|**Starta en schemalagd sökning endast när datorn är inaktiv**|Ange till **Ja** för att förhindra schemalagda skanningar från att starta när datorer används så att förlust av användarproduktivitet förebyggs.<br /><br />Rekommenderat värde: **Ja**|
|**Sök efter de senaste definitionerna för skadlig kod innan sökningen startas**|Ange till **Ja** så att Endpoint Protection söker automatiskt efter de senaste definitionerna för skadlig kod innan en skanning på datorer påbörjas.<br /><br />Rekommenderat värde: **Ja**|
|**Sök igenom arkivfiler**|Ange till **Ja** för att konfigurera Endpoint Protection till att söka efter skadlig kod i arkivfiler (till exempel ZIP- eller CAB-filer) på datorer.<br /><br />Rekommenderat värde: **Nej**|
|**Sök igenom e-postmeddelanden**|Ange till **Ja** för att konfigurera Endpoint Protection så att inkommande e-postmeddelanden skannas när de hämtas till datorerna.<br /><br />Rekommenderat värde: **Ja**|
|**Sök igenom filer öppnade från delade nätverksmappar**|Ange till **Ja** att konfigurera Endpoint Protection så att filer som öppnas från delade nätverksmappar skannas. Detta är vanligen filer som kan nås via en Universal Naming Convention (UNC)-sökväg. Om den här funktionen aktiveras kan problem för användare som har läsbehörighet inträffa eftersom de inte kan ta bort skadlig kod.<br /><br />Rekommenderat värde: **Nej**|
|**Sök igenom mappade nätverksenheter**|Ange till **Ja** för att konfigurera Endpoint Protection så att filer på mappade nätverksenheter skannas. Om den här funktionen aktiveras kan problem för användare som har läsbehörighet inträffa eftersom de inte kan ta bort skadlig kod.<br /><br />Rekommenderat värde: **Nej**|
|**Sök igenom flyttbara enheter**|Ange till **Ja** för att konfigurera Endpoint Protection till att skanna efter skadlig kod och oönskad programvara i flyttbara enheter, till exempel USB-minnen, när du skannar hela datorn.<br /><br />Rekommenderat värde: **Ja**|
|**Begränsa processoranvändning under en sökning**|Konfigurerar högsta procentandelen av CPU-kapaciteten som kan användas vid schemalagda skanningar på datorer. Du kan ange ett värde mellan 1 och 100 procent.<br /><br />Rekommenderat värde: **50%**|

### <a name="choose-default-actions-settings"></a>Välj standardinställningar för åtgärder

Inställningen **Välj hur Endpoint Protection åtgärdar skadlig kod för följande varningsnivåer** anger den standardåtgärd som Endpoint Protection vidtar när skadlig programvara på olika varningsnivåer upptäcks. Du kan ta bort den skadliga koden, sätta den i karantän eller utföra Microsofts rekommenderade åtgärd för varje varningsnivå.

Rekommenderat värde: **Rekommenderad åtgärd** som låter Endpoint Protection rekommendera en åtgärd.   

### <a name="decide-whether-to-choose-the-excluded-files-and-folders-settings"></a>Bestäm om du vill välja inställningar för exkluderade filer och mappar

Inställningen **Filer och mappar som ska undantas när du kör en skanning eller använder realtidsskydd** undantar vissa filer och mappar när en sökning körs eller när realtidsskydd används på datorer.

### <a name="decide-whether-to-choose-the-excluded-processes-settings"></a>Bestäm om du vill välja inställningar för exkluderade processer

Inställningen **Processer att undanta när en sökning körs eller när realtidsskyddet används** undantar vissa processer när en sökning körs eller när realtidsskydd används på datorer. Du kan endast utesluta filer med följande filtillägg: **.exe**, **.com** eller **.scr**.

### <a name="decide-whether-to-choose-the-excluded-file-types-settings"></a>Bestäm om du vill välja inställningar för exkluderade filtyper

Inställningen **Filnamnstillägg att undanta när en sökning körs eller när realtidsskyddet används** undantar vissa filnamnstillägg när en sökning körs eller när realtidsskydd används på datorer.

### <a name="specify-microsoft-active-protection-service-settings"></a>Ange Microsoft Active Protection Service-inställningar
Microsoft Active Protection Service är en online-community som hjälper dig att bestämma hur du ska svara på potentiella hot. Gruppen kan även stoppa spridning av nya infektioner av skadlig kod. Du kan **Delta i Microsoft Active Protection Service** genom att välja **Ja** och sedan ange din **medlemskapsnivå**:
  - **Grundläggande** – skickar grundläggande information till Microsoft om skadlig kod som upptäckts. Här ingår varifrån programmet kommer, vilka åtgärder som du har utfört eller som Endpoint Protection vidtar automatiskt samt om åtgärderna hade önskat resultat.
  - **Avancerad** – skickar information till Microsoft om skadlig programvara, spionprogram och oönskad programvara. Här ingår information om programvarans plats, filnamn, hur programvaran fungerar och hur den påverkar din dator.

Du kan också **Ta emot dynamiska definitioner baserat på Microsoft Active Protection Service-rapporter**.

## <a name="choose-management-tasks-for-endpoint-protection"></a>Välj hanteringsuppgifter för Endpoint Protection
Följande hjälper dig att utföra olika hanteringsuppgifter på hanterade datorer som kör Endpoint Protection:
- Uppdatera definitioner för skadlig kod
  - Intune-konsolen – Från arbetsytan **Grupper** markerar du de datorer som du vill uppdatera. Välj **Fjärruppgifter** &gt; **Uppdatera definitioner för skadlig kod**.
  - Hanterad dator - Starta Endpoint Protection-klientprogrammet från meddelandefältet i Windows. Välj fliken **Uppdatera** och därefter **Uppdatera**.
- Sök efter skadlig kod:
  - Intune-konsolen – Från arbetsytan **Grupper** markerar du de datorer som du vill skanna. Välj **Köra en fullständig skanning skadlig kod** eller **Kör en snabb skanning av skadlig kod**.
  - Hanterad dator - Starta Endpoint Protection-klientprogrammet från meddelandefältet i Windows. Markera **Snabb**, **Fullständig**, eller **Anpassad**, och välj sedan **Sök nu**.

Du kan visa statusen för en fjärraktivitet genom att trycka på länken **Fjärraktiviteter** i det nedre högra hörnet av Intune-konsolen. Dialogrutan **Aktivitetsstatus** visar aktuella fjärrhanteringsaktiviteter, aktivitetsstatus, enhetsnamn och eventuella rapporterade fel. Där finns även en länk till felsökningsinformation, om det är lämpligt.

## <a name="monitor-endpoint-protection"></a>Övervaka Endpoint Protection
Du övervaka status för skadlig kod på datorer med hjälp av arbetsytan **Skydd** i [administrationskonsolen för Microsoft Intune](https://manage.microsoft.com/). Den här arbetsytan innehåller två sidor:
- **Översikt av skydd** – Visar viktiga problem som länkar som du kan trycka på för mer information. Problem som kan visas är:
  - **Förekomst av skadlig kod som behöver åtgärder** – Klicka på länken om du vill se en lista över problem och åtgärder som krävs för att lösa problemen. Du kan utforska ytterligare detaljer i listan för att se vilka datorer som påverkas.
  - **Datorer med skadlig kod som behöver åtgärder** – Klicka på länken om du vill se en lista över alla datorer med olösta problem med skadlig kod samt åtgärder som krävs för att lösa problemen.
  - **Enheter som inte är skyddade** – Klicka på länken om du vill se datorer som inte skyddas av någon programvara för slutpunktsskydd eftersom inga program har installerats eller eftersom det finns ett fel. Välj en dator om du vill visa mer information.
  - **Enheter med ett annat slutpunktsskyddprogram körs** – Klicka på länken om du vill se datorer som kör ett slutpunktsskyddprogram från tredje part.
- **All skadlig kod** – Visar en lista över all aktiv skadlig kod som finns på dina datorer. Listan innehåller detaljer om alla datorer som påverkas av en viss typ av skadlig kod, eller kan du välja en av följande uppgifter:
  - **Visa egenskaper** – öppnar sidan med mer information om den valda skadliga koden.
  - **Lär dig mer om den här skadliga koden** – öppnar ett ämne från Microsoft Malware Protection Center med mer information om den skadliga koden.

> [!IMPORTANT]
> Arbetsytan **Skydd** visas inte i administrationskonsolen förrän du har installerat klienten och hanterar har minst en datorklient.

  ![Övervaka Endpoint Protection](media/pol-sa-ep-monitor.png)

### <a name="how-to-view-recent-detection-paths-for-malware-on-computers"></a>Hur man visar de senaste upptäckta sökvägar för sabotageprogram på datorer
Intune kan visa sökvägar för upp till 10 av de senaste upptäckta fallen av skadlig kod på en enhet. **Senast upptäckt sökväg** är inaktiverad som standard. När du vill aktivera den här visningen:

1. I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) klickar du på **Grupper** > **Alla enheter** > **Alla datorer**.
2. Högerklicka på den dator vars senaste sökvägar du vill visa och välj **Egenskaper**.
3. Välj **Skadlig kod** på flikarna längst upp.

   ![Välj fliken Skadlig kod och klicka sedan på kryssrutan Senaste sökvägar](media/malware-path-column.png)
4. Högerklicka på en kolumnrubrik. En lista över tillgängliga kolumner visas. Tryck på kryssrutan **Senaste upptäckta sökvägar** i listan. Kolumnen **Senaste upptäckta sökvägar** visas på skärmen och visar upp till de 10 senaste tillfällena av skadlig kod som upptäckts på enheten.

## <a name="run-a-malware-scan-or-update-malware-definitions-on-a-computer"></a>Köra en sökning efter skadlig kod eller uppdatera definitionerna för skadlig kod på en dator
Intune kan antingen köra en fullständig sökning eller snabbsökning efter skadlig kod med Endpoint Protection eller Windows Defender på en fjärrhanterad dator som har Intune-klienten installerad.

1. I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) går du till **Grupper** > **Översikt** > **Alla enheter** > **Alla datorer** och sedan markerar du den dator som du vill använda.

2. Klicka på listrutan **Fjärråtgärder** och välj sedan aktiviteten som du vill köra på fjärrdatorn.

## <a name="need-more-help"></a>Behöver du mer hjälp?
Mer hjälp och support finns i [Felsöka slutpunktsskydd i Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md).

### <a name="see-also"></a>Se även
[Principer för att skydda Windows-datorer](policies-to-protect-windows-pcs-in-microsoft-intune.md)
