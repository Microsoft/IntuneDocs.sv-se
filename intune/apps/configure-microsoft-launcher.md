---
title: Konfigurera Microsoft Launcher för Android Enterprise med Intune
titleSuffix: ''
description: Använd Intune-konfigurationsprinciper med Microsoft Launcher.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1dc2e2ce7e19933accdb1063ccacf99fa3f54b09
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563953"
---
# <a name="configure-microsoft-launcher"></a>Konfigurera Microsoft Launcher

Microsoft Launcher är en Android-app som gör att användare kan anpassa sin telefon, hålla ordning när de är på resa och gå över från att jobba via telefonen till datorn. 

På fullständigt hanterade Android Enterprise-enheter kan IT-företagsadministratörer anpassa startskärmen för hanterade enheter genom att välja bakgrundsbild, appar och ikonpositioner. Detta standardiserar utseendet för alla hanterade Android-enheter på olika OEM-enheter och systemversioner. 

## <a name="how-to-configure-the-microsoft-managed-home-screen-app"></a>Så här konfigurerar du Microsofts hanterade hemskärmsapp 

Gå till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välj **Appar** > **Appkonfigurationsprinciper**. Lägg till en konfigurationsprincip för **Hanterade enheter** som kör **Android** och välj **Microsoft Launcher** som den tillhörande appen. Klicka på **Konfigurationsinställningar** om du vill konfigurera de olika tillgängliga inställningarna för Hanterad startskärm. 

## <a name="choosing-a-configuration-settings-format"></a>Välja ett format för konfigurationsinställningar 

Det finns två metoder som du kan använda för att definiera konfigurationsinställningarna för Hanterad startskärm: 

- Med **Configuration Designer** kan du konfigurera inställningar med ett lättanvänt användargränssnitt som låter dig slå på och stänga av funktioner och ange värden. Det finns några inaktiverade konfigurationsnycklar med värdetyp BundleArray i den här metoden. Du kan endast konfigurera konfigurationsnycklarna genom att ange JSON-data. 

- Med **JSON-data** kan du definiera alla möjliga konfigurationsnycklar med ett JSON-skript. 

Om du lägger till egenskaper med **Configuration Designer** kan du automatiskt konvertera egenskaperna till JSON genom att välja **Ange JSON-data** på listrutan **Format för konfigurationsinställningar** enligt nedan.

   ![Format för konfigurationsinställningar – Använd Configuration Designer](./media/configure-microsoft-launcher/configure-microsoft-launcher-01.png)

## <a name="using-configuration-designer"></a>Använda Configuration Designer

Med Configuration designer kan du välja förinställda inställningar och deras associerade värden.

   ![Format för konfigurationsinställningar – Ange JSON-data](./media/configure-microsoft-launcher/configure-microsoft-launcher-02.png)

I följande tabell visas tillgängliga konfigurationsnycklar, värdetyper, standardvärden och beskrivningar för Microsoft Launcher. Beskrivningen innehåller förväntat enhetsbeteende baserat på de valda värdena. Konfigurationsnycklar som är inaktiverade i Configuration Designer visas inte i tabellen.

|    Konfigurationsnyckel    |    Värdetyp    |    Standardvärde    |    Beskrivning     |
|---------------------------------------------------|------------------|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Typ av registrering    |    Sträng     |    Standardvärde    |    Gör att du kan ange den registreringstyp som den här principen ska gälla för. För närvarande refererar värdet **Default** (Standard) till **CorporateOwnedBuisnessOnly**. Det finns för närvarande inga andra registreringstyper som stöds.        JSON-nyckelnamn: management_mode_key        |
|    Användarändring av startskärmens appordning tillåts    |    Boolesk    |    Sant    |    Gör att du kan ange om inställningen för **appordning på startskärmen** kan ändras av slutanvändaren.<ul><li>Om den ställs in på **True** (Sant) tillämpas bara appordningen som definieras i principen för den första distributionen. Därefter kommer principen inte att tillämpas för att respektera ändringar som användaren har gjort.</li><li>Om den ställs in på **False** (Falskt) tillämpas appordningen vid varje synkronisering.</li></ul><br>**Obs:** Startskärmens appordning kan bara konfigureras via JSON-redigeraren.<br><br>JSON-nyckelnamn:<br>`com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed`    |
|    Ange storlek för rutnät    |    Sträng    |    Automatisk    |    Gör att du kan ange rutnätsstorlek för appar som ska placeras på startskärmen. Du kan ange antalet apprader och kolumner för att definiera rutnätets storlek i följande format: `columns;rows`. Om du definierar rutnätsstorleken ska det maximala antalet appar som visas på en rad på startskärmen vara antalet rader som du anger, och det maximala antalet appar som ska visas i en kolumn i startskärmen ska vara antalet kolumner som du anger.<br><br>        JSON-nyckelnamn:<br>`com.microsoft.launcher.HomeScreen.GridSize`    |
|    Ange enhetens bakgrundsbild    |    Sträng    |    Null    |    Gör att du kan ange en valfri bakgrundsbild genom att ange URL:en för den bild du vill ha som bakgrundsbild.<br><br>JSON-nyckelnamn:<br>`com.microsoft.launcher.Wallpaper.URL`    |
|    Användarändring för att ange enhetens bakgrundsbild tillåts    |    Bool    |    Sant    |    Gör att du kan ange om inställningen för att ange enhetens bakgrundsbild kan ändras av slutanvändaren.<ul><li>Om den ställs in på **True** (Sant) tillämpas bara bakgrundsbilden i principen för den första distributionen. Därefter kommer principen inte att tillämpas för att respektera ändringar som användaren har gjort.</li><li>Om den ställs in på **False** (Falskt) tillämpas bakgrundsbilden vid varje synkronisering.</li></ul><br>JSON-nyckelnamn:<br>`com.microsoft.launcher.Wallpaper.URL.UserChangeAllowed`        |
|    Aktivera feed    |    Boolesk    |    Sant    |    Gör att du kan aktivera startfeeden på enheten när användaren sveper åt höger på startskärmen.<ul><li>Om den ställs in på **True** (Sant) aktiveras feeden.</li><li>Om den ställs in på **False** (Falskt) inaktiveras feeden.</li></ul><br>JSON-nyckelnamn:<br>`com.microsoft.launcher.Feed.Enabled`    |
|    Användarändring för att aktivera feed tillåts    |    Boolesk    |    Sant    |     Gör att du kan ange om inställningen **Aktivera feed** kan ändras av slutanvändaren.<ul><li>Om den ställs in på **True** (Sant) tillämpas bara feeden för den första distributionen. Därefter kommer principen inte att tillämpas för att respektera ändringar som användaren har gjort.</li><li>Om den ställs in på **False** (Falskt) tillämpas feeden vid varje synkronisering.</li></ul><br>JSON-nyckelnamn:`com.microsoft.launcher.Feed.Enabled.UserChangeAllowed`    |

## <a name="enter-json-data"></a>Ange JSON-data

Ange JSON-data om du vill konfigurera alla tillgängliga inställningar för Microsoft Launcher samt de inställningar som är inaktiverade i **Configuration Designer**, enligt nedan.

   ![Configuration Designer – JSON-data](./media/configure-microsoft-launcher/configure-microsoft-launcher-03.png)

Förutom listan över konfigurerbara inställningar som anges i Configuration Designer-tabellen (ovan) innehåller följande tabell konfigurationsnycklar som du bara kan konfigurera via JSON-data.

|    Konfigurationsnyckel    |    Värdetyp    |    Standardvärde    |    Beskrivning     |
|----------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Ange tillåtna program<br>JSON-nyckel:`com.microsoft.launcher.HomeScreen.Applications`    |    BundleArray    | Se: [Ange tillåtna program](configure-microsoft-launcher.md#set-allow-listed-applications)</sup>    |    Gör att du kan definiera en uppsättning appar som ska visas på startskärmen bland apparna som är installerade på enheten. Du kan definiera appar genom att ange paketnamnet för de appar som du vill göra synliga. Till exempel skulle `com.android.settings` göra inställningar tillgängliga på startskärmen. Apparna som du godkänner i det här avsnittet bör vara installerade på enheten för att kunna visas på startskärmen.<p>Egenskaper:<ul><li>**Paket:** Namn på programpaketet</li><li>**Klass:** Programaktiviteten, som är specifik för en viss appsida. Den skulle använda standardappsidan om det här värdet är tomt.</li></ul>      |
|    Appordning på startskärmen<br>JSON-nyckel: `com.microsoft.launcher.HomeScreen.AppOrder`    |    BundleArray    |    Se: [Appordning på startskärmen](configure-microsoft-launcher.md#home-screen-app-order)      |    Gör att du kan ange appordningen på startskärmen.<p>Egenskaper:<br><ul><li>**Typ:** Den enda typ som stöds är `application`.</li><li>**Position:** Programikonplatsen på startskärmen. Det här börjar från position 1 högst upp till vänster och går från vänster till höger, uppifrån och ned.</li><li>**Paket:** Namn på programpaketet.</li><li>**Klass:** Programaktiviteten, som är specifik för en viss appsida. Standardappsidan används om det här värdet är tomt.</li></ul>    |

### <a name="set-allow-listed-applications"></a>Ange tillåtna program

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.Applications",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

### <a name="home-screen-app-order"></a>Appordning på startskärmen

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.AppOrder",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "type",
                    "valueString": "application"
                },
                {
                    "key": "position",
                    "valueInteger": 0
                },
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

Här följer ett exempel på ett JSON-skript med alla tillgängliga konfigurationsnycklar:

```JSON
{
    "kind": "androidenterprise#managedConfiguration", 
    "productId": "app:com.microsoft.launcher", 
    "managedProperty": [
        {
            "key": "management_mode_key", 
            "valueString": "Default"
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable", 
            "valueBool": true
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url", 
            "valueBool": "http://www.contoso.com/wallpaper.png"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.GridSize", 
            "valueString": "5;5"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.Applications", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 17
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 18
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 19
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }
    ]
}
```

## <a name="next-steps"></a>Nästa steg

- Mer information om fullständigt hanterade Android Enterprise-enheter finns i [Konfigurera Intune-registrering av fullständigt hanterade Android Enterprise-enheter](../enrollment/android-fully-managed-enroll.md).
