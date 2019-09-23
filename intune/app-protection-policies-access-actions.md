---
title: Rensa data med villkorsstyrda startåtgärder för skyddsprincip
titleSuffix: Microsoft Intune
description: Lär dig hur du selektivt rensar data med villkorsstyrda startåtgärder för appskyddsprinciper i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a038f55f6dbdd894742a8712c878e77557a77210
ms.sourcegitcommit: 27e63a96d15bc4062af68c2764905631bd928e7b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71061548"
---
# <a name="selectively-wipe-data-using-app-protection-policy-conditional-launch-actions-in-intune"></a>Rensar data selektivt med villkorsstyrda startåtgärder för appskyddsprinciper i Intune

Med Intune-appskyddsprinciper kan du konfigurera inställningar för att blockera slutanvändare från att komma åt en företagsapp eller ett företagskonto. Dessa inställningar riktar in sig på dataförflyttning och åtkomstkrav som anges av organisationen för sådant som jailbroken enheter och minsta OS-versioner.
 
Du kan uttryckligen välja att rensa ditt företags data från slutanvändarens enhet som en åtgärd att vidta för icke-kompatibilitet genom att använda dessa inställningar. För vissa inställningar kan du konfigurera flera åtgärder, till exempel blockera åtkomst och rensa data utifrån olika angivna värden.

## <a name="create-an-app-protection-policy-using-conditional-launch-actions"></a>Skapa en app med villkorsstyrda startåtgärder för skyddsprincip

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. I **Intune**-fönstret väljer du **Klientappar** > **Principer för appskydd**.
4. Klicka på **Lägg till en princip** (du kan även redigera en befintlig princip). 
5. Klicka på **Konfigurera obligatoriska inställningar** för att se listan över inställningar tillgängliga för konfiguration för principen. 
6. När du rullar ned i fönstret Inställningar visas avsnittet **Villkorsstyrda startåtgärder** med en redigerbar tabell.

    ![Skärmbild av åtkomståtgärder för Intune-appskydd](./media/apps-selective-wipe-access-actions01.png)

7. Välj en **inställning** och ange det **värde** som användare måste uppfylla för att logga in på företagsappen. 
8. Välj den **åtgärd** du vill vidta att om användarna inte uppfyller dina krav. I vissa fall kan flera åtgärder konfigureras för en och samma inställning. Mer information finns i [Hur du skapar och tilldelar skyddsprinciper för appar](app-protection-policies.md).

>[!NOTE]
> Om du vill använda inställningen **Enhetsmodeller eller enhetstillverkare** anger du en semikolonavgränsad lista över enhetsmodell-ID:n (iOS) eller enhetstillverkare (Android). Undvik blanksteg i listor med flera värden. De här värdena är inte skiftlägeskänsliga. 

## <a name="policy-settings"></a>Principinställningar 

Tabellen över inställningar för appskyddsprinciper har kolumner för **Inställning**, **Värde** och **Åtgärd**.

### <a name="ios-policy-settings"></a>iOS-principinställningar
För iOS kan du konfigurera åtgärder för följande inställningar med hjälp av listrutan **Inställning**:
- Högsta antal PIN-försök
- Offline-respitperiod
- Jailbrokade/rotade enheter
- Lägsta operativsystemversion
- Lägsta appversion
- Lägsta SDK-version
- Enhetsmodell(er)

Om du vill använda inställningen **Enhetsmodell(er)** anger du en semikolonavgränsad lista över iOS-modellidentifierare. Du hittar en iOS-modellidentifierare under kolumnen Enhetstyp i [Supportdokumentationen för HockeyApp](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types).<br>
Exempel på indata: *iPhone5,2;iPhone5,3*

På slutanvändarens enheter kan Intune-klienten utföra åtgärder baserat på en enkel matchning av enhetsmodellsträngar som angetts i Intune för programskyddsprinciper. Matchningen beror helt på vad enheten rapporterar. Du (IT-administratören) uppmuntras säkerställa att det avsedda beteendet fungerar genom att testa den här inställningen baserat på en rad olika enhetstillverkare och modeller som är riktade till en liten användargrupp. Standardvärdet är **Inte konfigurerat**.<br>
Ange en av följande åtgärder: 
- Tillåt angivna (Blockera icke-angivna)
- Tillåt angivna (Rensa icke-angivna)

**Vad händer om IT-administratören matar in en annan lista över iOS-modellidentifierare mellan principer för samma appar för samma användare i Intune?**<br>
När konflikter uppstår mellan två appskyddsprinciper för konfigurerade värden använder Intune normalt den mest restriktiva metoden. Den resulterande principen som skickas till målappen och som öppnas av den aktuella Intune-användaren är därför en del av de listade iOS modellidentifierarna i *Princip A* och *Princip B* som riktas till samma kombination av app/användare. *Princip A* specificerar till exempel ”iPhone5,2;iPhone5,3” medan *Princip B* specificerar”iPhone5,3”. Den resulterande principen för Intune-användaren som påverkas av både *Princip A* och *Princip B* blir då ”iPhone5,3”. 

### <a name="android-policy-settings"></a>Principinställningar för Android

För Android kan du konfigurera åtgärder för följande inställningar med hjälp av listrutan **Inställning**:
- Högsta antal PIN-försök
- Offline-respitperiod
- Jailbrokade/rotade enheter
- Lägsta operativsystemversion
- Lägsta appversion
- Lägsta korrigeringsversion
- Enhetstillverkare
- SafetyNet-enhetsattestering
- Hotgenomsökning för appar

Om du vill använda inställningen **Enhetstillverkare** anger du en semikolonavgränsad lista över Android-tillverkare. Du hittar Android-tillverkaren av en enhet under Enhetsinställningar.<br>
Exempel på indata: *Tillverkare A;Tillverkare B* 

>[!NOTE]
> Nedan visas några vanliga tillverkare som har rapporterats från enheter med Intune. Dessa kan användas som indata: Asus;Blackberry;Bq;Gionee;Google;Hmd global;Htc;Huawei;Infinix;Kyocera;Lemobile;Lenovo;Lge;Motorola;Oneplus;Oppo;Samsung;Sharp;Sony;Tecno;Vivo;Vodafone;Xiaomi;Zte;Zuk

På slutanvändarens enheter kan Intune-klienten utföra åtgärder baserat på en enkel matchning av enhetsmodellsträngar som angetts i Intune för programskyddsprinciper. Matchningen beror helt på vad enheten rapporterar. Du (IT-administratören) uppmuntras att säkerställa att det avsedda beteendet fungerar genom att testa den här inställningen baserat på en rad olika enhetstillverkare och modeller som är riktade till en liten användargrupp. Standardvärdet är **Inte konfigurerat**.<br>
Ange en av följande åtgärder: 
- Tillåt angivna (Blockera på icke-angivna)
- Tillåt angivna (Rensa på icke-angivna)

**Vad händer om IT-administratören matar in en annan lista över Android-tillverkare mellan principer för samma appar för samma användare i Intune?**<br>
När konflikter uppstår mellan två appskyddsprinciper för konfigurerade värden använder Intune normalt den mest restriktiva metoden. Den resulterande principen som skickas till målappen och som öppnas av den aktuella Intune-användaren är därför vara en del av de listade Android-tillverkarna i *Princip A* och *Princip B* som riktas till samma kombination av app/användare. *Princip A* specificerar t.ex ”Google,Samsung” medan *Princip B* specificerar”Google”. Den resulterande principen för Intune-användaren som påverkas av både *Princip A* och *Princip B* blir då ”Google”. 

### <a name="additional-settings-and-actions"></a>Ytterligare inställningar och åtgärder 

Som standard har tabellen ifyllda rader som inställningar konfigurerade för **Offlinerespittid** och **Högsta antal PIN-försök** om inställningen **Kräv PIN-kod för åtkomst** är inställd på **Ja**.
 
Om du vill konfigurera en inställning väljer du en inställning i listrutan under kolumnen **Inställning**. När en inställning har valts aktiveras den redigerbara textrutan under kolumnen **Värde** på amma rad, om ett värde måste anges. Dessutom aktiveras listrutan under kolumnen **Åtgärd** med de villkorsstyrda startåtgärder som gäller för inställningen. 

Följande lista innehåller den vanliga listan över åtgärder:
- **Blockera åtkomst** – blockera användaren från att komma åt företagsappen.
- **Rensa data** – rensa företagsdata från slutanvändarens enhet.
- **Varna** – ange dialogruta till slutanvändaren som ett varningsmeddelande.

I vissa fall, till exempel inställningen **Lägsta operativsystemversion**, kan du konfigurera inställningen för att utföra alla tillämpliga åtgärder baserat på olika versionsnummer. 

![Skärmbild av åtkomståtgärder för Intune-appskydd – Lägsta operativsystemversion](./media/apps-selective-wipe-access-actions05.png)

När en inställning konfigureras fullständigt visas raden i en skrivskyddad vy och är tillgänglig att redigeras när som helst. Dessutom har raden en tillgänglig listruta för val i kolumnen **Inställning**. Inställningar som redan har konfigurerats och inte tillåter flera åtgärder kan inte väljas i listrutan.

## <a name="next-steps"></a>Nästa steg

Mer information om Intune-appskyddsprinciper finns här:
- [Hur du skapar och tilldelar skyddsprinciper för appar](app-protection-policies.md)
- [Inställningar för iOS-appskyddsprinciper](app-protection-policy-settings-ios.md)
- [Inställningar för Android-appskyddsprinciper i Microsoft Intune](app-protection-policy-settings-android.md) 
