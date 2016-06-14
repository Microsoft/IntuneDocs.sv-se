---
# required metadata

title: Felsöka Endpoint Protection i Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Troubleshoot Endpoint Protection in Microsoft Intune

Använd informationen i det här avsnittet för att lösa problem när du använder Endpoint Protection i Microsoft Intune.

Om du inte lyckas lösa problemet med hjälp av den här informationen läser du [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md), som beskriver hur du kan få hjälp på fler sätt.


### Endpoint Protection-felmeddelanden
I det här avsnittet beskrivs möjliga orsaker och lösningar för följande fel och varningar som visas i fönstret **Status för Endpoint Protection** i [Intune-administrationskonsolen](https://manage.microsoft.com).

|Statusobjekt|Möjliga orsaker|Möjliga lösningar|
|---------------|--------------------|-----------------------|
|**Endpoint Protection-motorn är inte tillgänglig**|Motorn för Endpoint Protection i Intune är skadad eller har tagits bort.|Om motorn för Endpoint Protection i Intune är skadad kan du prova att uppdatera eller installera om programvaran.<br /><br />Om du vill framtvinga en omedelbar uppdatering klickar du på **Uppdatera** i Endpoint Protection-klientprogrammet (i verktygsfältet på hanterade datorer).<br /><br />Om motorn inte kan uppdateras måste du installera om Endpoint Protection-motorn.<br /><br />Leta upp **Microsoft Intune Endpoint Protection Agent** i listan över installerade program på Kontrollpanelen på den hanterade datorn och avinstallera programmet.<br /><br />Microsoft Online Management Update Manager identifierar programmet som saknas under nästa uppdateringssynkronisering och installerar om det på den schemalagda installationstiden.|
|**Endpoint Protection är inaktiverat**|Endpoint Protection i Intune har inaktiverats av en administratör med hjälp av en princip eller av en användare på en hanterad dator.|Om Endpoint Protection har inaktiverats kan du aktivera funktionen från [Intune-administrationskonsolen](https://manage.microsoft.com) eller från en hanterad dator. Gör något av följande:<br /><br />Du kan aktivera Endpoint Protection från [Intune-administrationskonsolen](https://manage.microsoft.com) genom att öppna arbetsytan **Princip** och sedan ändra inställningen **Aktivera Endpoint Protection** i de principer som tillämpas på datorn.<br /><br />Eller,<br /><br />om du vill aktivera Endpoint Protection från en hanterad dator, startar du Intunes Endpoint Protection-klient från meddelandefältet så uppmanas du att aktivera Endpoint Protection.|
|**Realtidsskydd är inaktiverat**|Realtidsskydd har inaktiverats av en administratör (med hjälp av en princip) eller av en användare på en hanterad dator.|Om realtidsskydd har inaktiverats kan du aktivera det från [Intune-administrationskonsolen](https://manage.microsoft.com) eller från en hanterad dator. Gör något av följande:<br /><br />Om du vill aktivera realtidsskydd från [Intune-administrationskonsolen](https://manage.microsoft.com) öppnar du arbetsytan **Princip** och ändrar sedan inställningen **Aktivera realtidsskydd** till **Ja** i principerna som tillämpas på datorn.<br /><br />Eller,<br /><br />om du vill aktivera realtidsskydd från en hanterad dator, startar du Endpoint Protection-klientprogrammet från meddelandefältet. När du gör det uppmanas du att aktivera realtidsskydd.|
|**Genomsökning av hämtningar är inaktiverat**|Hämtningsgenomsökning har inaktiverats av en administratör med hjälp av en princip eller av en användare på en hanterad dator.|Om genomsökning av hämtningar har inaktiverats kan du aktivera funktionen från [Intune-administrationskonsolen](https://manage.microsoft.com) eller från en hanterad dator. Gör något av följande:<br /><br />Om du vill aktivera genomsökning av hämtningar från [Intune-administrationskonsolen](https://manage.microsoft.com) öppnar du arbetsytan **Princip** och ändrar sedan inställningen **Sök igenom alla hämtade filer** till **Ja** i de principer som tillämpas på datorn.<br /><br />Eller,<br /><br />om du vill aktivera genomsökning av hämtningar från en hanterad dator, startar du Endpoint Protection-klientprogrammet från meddelandefältet. Klicka på fliken **Inställningar**, välj **Realtidsskydd**, markera kryssrutan **Sök igenom alla hämtade filer** och klicka sedan på **Spara ändringar**.|
|**Övervakningen av fil- och programaktivitet är inaktiverat**|Övervakningen av fil- och programaktivitet har inaktiverats av en administratör med hjälp av en princip eller av en användare på en hanterad dator.|Om övervakningen av fil- och programaktivitet har inaktiverats kan du aktivera funktionen från [Intune-administrationskonsolen](https://manage.microsoft.com) eller från en hanterad dator. Gör något av följande:<br /><br />Om du vill aktivera övervakning av fil- och programaktivitet från [Intune-administrationskonsolen](https://manage.microsoft.com) öppnar du arbetsytan **Princip** och ändrar sedan inställningen **Övervaka fil- och programaktivitet på datorn** till **Ja** i de principer som tillämpas på datorn.<br /><br />Eller,<br /><br />om du vill aktivera övervakning av fil- och programaktivitet från en hanterad dator, startar du Endpoint Protection-klientprogrammet från meddelandefältet. Klicka på fliken **Inställningar**, välj **Realtidsskydd**, markera kryssrutan **Övervaka fil- och programaktivitet på datorn** och klicka sedan på **Spara ändringar**.|
|**Beteendeövervakning är inaktiverat**|Beteendeövervakning har inaktiverats av en administratör (med hjälp av en princip) eller av en användare på en hanterad dator.|Om beteendeövervakning har inaktiverats kan du aktivera funktionen från [Intune-administrationskonsolen](https://manage.microsoft.com) eller från en hanterad dator. Gör något av följande:<br /><br />Om du vill aktivera beteendeövervakning från [Intune-administrationskonsolen](https://manage.microsoft.com) öppnar du arbetsytan **Princip**, ändrar inställningen **Aktivera beteendeövervakning** till **Ja** i principerna som tillämpas på datorn och startar sedan om den hanterade datorn.<br /><br />Eller,<br /><br />om du vill aktivera beteendeövervakning från en hanterad dator, startar du Endpoint Protection-klientprogrammet från meddelandefältet. Välj fliken **Inställningar**, välj **Realtidsskydd**, markera kryssrutan **Aktivera beteendeövervakning** och välj sedan **Spara ändringar**. Starta om datorn.|
|**Genomsökning av skript är inaktiverat**|Skriptgenomsökning har inaktiverats av en administratör (med hjälp av en princip) eller av en användare på en hanterad dator.|Om skriptgenomsökning har inaktiverats kan du aktivera funktionen från [Intune-administrationskonsolen](https://manage.microsoft.com) eller från en hanterad dator. Gör något av följande:<br /><br />Om du vill aktivera skriptgenomsökning från [Intune-administrationskonsolen](https://manage.microsoft.com) öppnar du arbetsytan **Princip** och ändrar sedan inställningen **Aktivera skriptgenomsökning** till **Ja** i de principer som tillämpas på datorn.<br /><br />Eller,<br /><br />om du vill aktivera skriptgenomsökning från en hanterad dator, startar du Endpoint Protection-klientprogrammet från meddelandefältet. Välj **Realtidsskydd** på fliken **Inställningar**, markera kryssrutan **Aktivera skriptgenomsökning** och välj sedan **Spara ändringar**.|
|**Kontrollsystem för nätverk är inaktiverat**|Nätverkskontrollsystemet har inaktiverats av en administratör med hjälp av en princip eller av en användare på en hanterad dator.|Om kontrollsystem för nätverk har inaktiverats kan du aktivera funktionen från [Intune-administrationskonsolen](https://manage.microsoft.com) eller från en hanterad dator. Gör något av följande:<br /><br />Om du vill aktivera kontrollsystem för nätverk från [Intune-administrationskonsolen](https://manage.microsoft.com) öppnar du arbetsytan **Princip**, ändrar inställningen **Aktivera kontrollsystem för nätverk** till **Ja** i de principer som tillämpas på datorn och startar sedan om den hanterade datorn.<br /><br />Eller,<br /><br />om du vill aktivera kontrollsystem för nätverk från en hanterad dator, startar du Endpoint Protection-klientprogrammet från meddelandefältet. Välj fliken **Inställningar**, välj **Realtidsskydd**, markera kryssrutan **Aktivera kontrollsystem för nätverk** och klicka sedan på **Spara ändringar**. Starta om datorn.|
|**Definitionerna för skadlig kod är inaktuella**|Datorn kanske har varit frånkopplad från Internet under en längre tid och definitionerna för skadlig kod kanske inte har uppdaterats än. Den här statusen visas när definitionerna för skadlig kod på datorn är inaktuella i 14 dagar eller mer.|Om definitionerna för skadlig kod är inaktuella kan du uppdatera definitionerna från [Intune-administrationskonsolen](https://manage.microsoft.com) eller från den hanterade datorn.<br /><br />Mer information finns i avsnittet [Skydda Windows-datorer med Endpoint Protection för Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|
|**En fullständig genomsökning är försenad**|En fullständig genomsökning har inte utförts på 14 dagar. Detta kan bero på en omstart av datorn under en fullständig genomsökning.|Om en fullständig genomsökning är försenad kan du köra en fullständig genomsökning en gång eller schemalägga återkommande fullständiga genomsökningar från [Intune-administrationskonsolen](https://manage.microsoft.com) med hjälp av informationen i avsnittet [Vanliga hanteringsuppgifter för Windows-dator med Microsoft Intune-datorklient](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).|
|**En snabbgenomsökning är försenad**|En snabbgenomsökning har inte utförts på 14 dagar. Detta kan bero på en omstart av datorn under en snabbgenomsökning.|Om snabbgenomsökningen är försenad kan du köra en snabbgenomsökning en gång eller schemalägga återkommande snabbgenomsökningar från [Intune-administrationskonsolen](https://manage.microsoft.com) med hjälp av informationen i avsnittet [Vanliga hanteringsuppgifter för Windows-dator med Microsoft Intune-datorklient](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).|
|**Ett annat program för slutpunktsskydd körs**|Ett annat program för slutpunktsskydd körs och datorn är felfri.|Om ett annat Endpoint Protection-program har installerats och Intune identifierar programmet inaktiveras Endpoint Protection automatiskt som standard. Om Intune inte identifierar det andra slutpunktsprogrammet förblir Endpoint Protection aktiverat. Mer information finns i [Skydda Windows-datorer med Endpoint Protection för Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|

### Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).


<!--HONumber=Jun16_HO1-->


