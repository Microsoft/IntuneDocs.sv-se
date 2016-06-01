---
# required metadata

title: Vad händer om du återställer en enhet med hjälp av företagsportalen? | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1ee6e275-d1ec-4da3-bbef-d5da2c61a02a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Vad händer om du återställer en enhet med hjälp av företagsportalen?

När du använder företagsportalen eller företagsportalens webbplats för att återställa en Windows-enhet kan vissa appar och inställningar på enheten raderas, bland annat vissa personliga data. Det som händer på varje enskild enhet beror på typen av enhet och hur du använder den, enligt beskrivning i följande tabell. Anvisningar om hur du återställer en enhet som förlorats eller stulits finns i [Återställa (radera) en enhet som förlorats eller stulits](reset-erase-your-lost-or-stolen-device-windows.md)

|Enhetskonfiguration och hantering|Enhetstyp|
|---------------------------------------|---------------|
|Din IT-administratör hanterar din mobila enhet|**Windows 10, Windows Phone 8.1 och Windows Phone 8**</br>Enheten visas inte längre på företagsportalen och företagsportalen försöker återställa enheten till tillverkarens standardinställningar. Personliga data, appar och inställningar tas bort.<br /><br />**Windows RT**<br />Det går inte att återställa en Windows RT-enhet såvida den inte enbart används för e-post.|
|Enheten har enbart åtkomst till företagets e-post|**Windows Phone 8.1 och Windows Phone 8**<br />Enheten visas inte längre på företagsportalen och ditt företags-e-postkonto tas bort och alla meddelanden som inte har sparats raderas.<br /><br />**Windows RT**<br />Enheten visas inte längre på företagsportalen och ditt företags-e-postkonto tas bort och alla meddelanden som inte har sparats raderas.<br /><br />**Datorer med Windows 7 eller Windows Vista**<br />Det går inte att återställa en dator med Windows 7 eller tidigare som bara används för e-post.<br /><br />**Datorer med Windows 8.1 och Windows 8**<br />Enheten visas inte längre på företagsportalen och ditt företags-e-postkonto tas bort och alla meddelanden som inte har sparats raderas.|
|Stationära och bärbara datorer|**Datorer med Windows 8.1 och Windows 8**<br />Det går inte att återställa en dator med Windows 8 eller Windows 8.1 såvida den inte enbart används för e-post.<br /><br />**Datorer med Windows 7 eller Windows Vista**<br />Det går inte att återställa en dator med Windows 7 eller tidigare.|

### Se även
[Att använda din Windowsenhet med Intune](using-your-windows-device-with-intune.md)

<!--HONumber=May16_HO2-->


