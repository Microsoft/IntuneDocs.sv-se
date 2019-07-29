---
title: Konfigurera Microsofts hanterade hemskärmsapp
titleSuffix: Microsoft Intune
description: Lär dig att konfigurera Microsofts hanterade hemskärmsapp.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b1f8308463e76b09a041bb952ad09515435c54c
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2019
ms.locfileid: "68374840"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Konfigurera Microsofts hanterade hemskärmsapp för Android Enterprise

Hanterad hemskärm är appen som används för företagsägda Android Enterprise-dedikerade enheter som har registrerats via Intune och som körs i helskärmsläge för flera appar. För de här enheterna fungerar Hanterad startskärm som ett startprogram för andra godkända appar som ska köras ovanpå dem. Hanterad startskärm ger IT-administratörer möjlighet att anpassa sina enheter och begränsa funktionerna som slutanvändare kan nå. 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>När du ska konfigurera Microsofts hanterade hemskärmsapp

Om du når inställningar via enhetskonfiguration ska du vanligtvis konfigurera inställningarna där. Om du gör det kan du spara tid, minimera fel och få ett bättre Intune-stöd. Men vissa inställningar för hanterad startskärm är för närvarande endast tillgängligt via bladet **Konfigurationsprinciper för appar** i Intune-konsolen. Med hjälp av det här dokumentet kan du lära dig att konfigurera olika inställningar, antingen med Configuration Designer eller ett JSON-skript. 

> [!NOTE]
> Det är för närvarande möjligt, och lämpligt, att ange godkända program och fästa webblänkar via **Klientappar** och **Enhetskonfiguration**. En fullständig lista över vilka inställningar som är tillgängliga i **Enhetskonfiguration** som påverkar hanterad startskärm finns i [Inställningar för särskilda enheter](device-restrictions-android-for-work.md#dedicated-device-settings).  

Gå först till Intune-konsolen i Azure-portalen och gå till **Klientappar** > **Konfigurationsprinciper för appar**. Lägg till en konfigurationsprincip för **Hanterade enheter** som kör **Android** och välj **Hanterad startskärm** som den tillhörande appen. Klicka på **Konfigurationsinställningar** om du vill konfigurera de olika tillgängliga inställningarna för Hanterad startskärm. 

## <a name="choosing-a-configuration-settings-format"></a>Välja ett format för konfigurationsinställningar

Det finns två metoder som du kan använda för att definiera konfigurationsinställningarna för Hanterad startskärm:

- Med **Configuration Designer** kan du konfigurera inställningar med ett lättanvänt användargränssnitt som låter dig slå på och stänga av funktioner och ange värden. Det finns några inaktiverade konfigurationsnycklar med värdetyp `BundleArray` i den här metoden. Du kan endast konfigurera konfigurationsnycklarna genom att ange JSON-data. 
- Med **JSON-data** kan du definiera alla möjliga konfigurationsnycklar med ett JSON-skript. 

Om du lägger till egenskaper med Configuration Designer kan du automatiskt konvertera egenskaperna till JSON genom att välja **Ange JSON-data** på listrutan **Format för konfigurationsinställningar**.

![Skärmbild av alternativen för inställningsformat för konfiguration](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>Använda Configuration Designer

Med Configuration designer kan du välja förinställda inställningar och deras associerade värden. 

![Skärmbild av tillagda konfigurationsinställningar](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

I följande tabell visas tillgängliga konfigurationsnycklar, värdetyper, standardvärden och beskrivningar för Hanterad startskärm. Beskrivningen innehåller förväntat enhetsbeteende baserat på de valda värdena. Konfigurationsnycklar som är inaktiverade i Configuration Designer visas inte i tabellen.

| Konfigurationsnyckel | Värdetyp | Standardvärde | Beskrivning |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ange storlek för rutnät | sträng | Automatisk | Gör att du kan ange rutnätsstorlek för appar som ska placeras på Hanterad startskärm. Du kan ange antalet apprader och kolumner för att definiera rutnätets storlek i följande format `columns;rows`. Om du definierar rutnätsstorleken ska det maximala antalet appar som visas på en rad på startskärmen vara antalet rader som du anger, och det maximala antalet appar som ska visas i en kolumn i startskärmen ska vara antalet kolumner som du anger. |
| Aktivera skärmrubrik | bool | TRUE | Gör att huvudrubriken kan visa olika vyer som Hanterad startskärm erbjuder, till exempel flöde eller flödeskort. Om du aktiverar den här inställningen ser enhetsanvändarna rubriken. |
| Aktivera enhetens statusfält | bool | TRUE | Aktiverar statusfältet på startskärmen (det översta fältet visar aktuella anslutningar, till exempel Wi-Fi). Om du aktiverar den här konfigurationsnyckeln kan slutanvändaren se ikonerna som visas på statusfälten som representerar anslutningar och aktiva appar. |
| Aktivera aktivitetsikon för meddelanden | bool | FALSE | Aktiverar aktivitetsikon för meddelanden för appikoner som visar antalet nya meddelanden i appen. Om du aktiverar den här inställningen ser slutanvändarna aktivitetsikoner för meddelande på appar som har olästa meddelanden. Om du fortsätter att ha konfigurationsnyckeln inaktiverad ser inte slutanvändaren eventuella aktivitetsikoner för meddelande på appar som kan innehålla olästa meddelanden. |
| Låsa startskärmen | bool | TRUE | Tar bort möjligheten för slutanvändaren att flytta runt appikoner på startskärmen. Om du aktiverar den här konfigurationsnyckeln blir appikonerna på startskärmen låsta, och slutanvändaren kan inte dra och släppa till olika rutnätsplaceringar på startskärmen. Om det ställs in på `false` kan slutanvändarna flytta runt program- och webblänksikoner på Hanterad startskärm.  |
| Ange bakgrund för enheten | sträng | Standardvärde | Gör att du kan ange en valfri bakgrundsbild genom att ange URL:en för den bild du vill ha som bakgrundsbild. |
| Ställa in storlek för appikon | heltal | 2 | Gör att du kan ange ikonstorlek för appar som visas på startskärmen. Du kan välja följande värden i den här konfigurationen för olika storlekar: 0 (minst), 1 (liten), 2 (normal), 3 (stor) och 4 (störst). |
| Ange ikon för appmappen | heltal | 0 | Gör att du kan definiera utseendet på appmapparna på startskärmen. Du kan välja utseende bland följande värden: Mörk fyrkantig(0);   mörk cirkel(1); ljus fyrkantig(2); ljus cirkel(3). |
| Aktivera gester | bool | FALSE | Gör det möjligt för slutanvändarna att tilldela olika gester, till exempel att svepa uppåt och nedåt. Om du inaktiverar den här konfigurationsnyckeln kan slutanvändarna endast svepa åt höger om det finns en andra sida och tillbaka till startsidan. |
| Aktivera vertikal rullning | bool | FALSE | Möjliggör vertikal rullning på den hanterade startskärmen. Om du aktiverar den här konfigurationsnyckeln kan slutanvändaren endast gå till olika sidor vertikalt istället för att svepa horisontellt. |
| Ställa in tema för startskärmen | sträng | Theme.Light.Blue | Du kan välja tema för startskärmen från en fördefinierad uppsättning teman med olika färger. Du kan välja följande teman genom att ange strängvärdet i följande format.   Theme.Light.Green. Ljust kan ersättas med mörkt för ett mörkt tema, och grönt kan ersättas med blått, gult, rosa, rött, orange och lila. |
| Aktivera docka | bool | FALSE | Aktiverar appdockaavsnittet längst ned på startskärmen med beständiga appar som visas och en startpunkt för alla installerade appar. Om du aktiverar den här konfigurationsnyckeln kan slutanvändaren få åtkomst till appar i dockan och även avsnittet med alla appar och gå till listan över alla installerade appar på enheterna oavsett om de har godkänts eller inte. |
| Ange skärmens orientering | heltal | 1 | Gör att du kan ange startskärmens orientering till stående eller liggande läge eller tillåt automatisk rotation. Du kan ställa in orienteringen genom att ange värden 1 (för stående läge), 2 (för liggande läge), 3 (för automatisk rotation). |
| Aktivera startskärmens flöde | bool | FALSE | Aktiverar flödet för startskärmen, som visas om du sveper åt vänster på startskärmen. Det här flödet visar annan typ av innehåll, till exempel nyheter, kalender, ofta använda appar och Cortana-röstassistentkortet osv. Om du aktiverar det här kan användaren navigera i flödet genom att svepa åt vänster på startskärmen. |
| Aktivera översiktsläge | bool | FALSE | Gör det möjligt för slutanvändarna att lägga till eller ta bort olika sidor på startskärmen som kan nås genom att användaren sveper åt höger från standardskärmen. Om du aktiverar det här kan slutanvändaren lägga till sidor till höger om standardsidan på startskärmen, ändra standardsidan och även komma åt inställningarna på den hanterade startskärmen. |
| Aktivera enhetstelemetri | bool | FALSE | Aktiverar all telemetri som samlas in för den hanterade startskärmen. Om du aktiverar det här kan Microsoft hantera enhetstelemetri, som hur många gånger en viss app startas på enheten. |
| Ange tillåtna program | bundleArray | FALSE | Gör att du kan definiera en uppsättning appar som ska visas på startskärmen bland apparna som är installerade på enheten. Du kan definiera appar genom att ange paketnamnet för de appar som du vill göra synliga. Till exempel skulle com.microsoft.emmx göra inställningar tillgängliga på startskärmen. Apparna som du godkänner i det här avsnittet bör vara installerade på enheten för att kunna visas på startskärmen. |
| Ställa in fästa webblänkar | bundleArray | FALSE | Du kan fästa webbplatser som snabbstartsikoner på startskärmen. Med den här konfigurationen kan du definiera webbadressen och lägga till den på startskärmen så att användaren kan starta webbläsaren med en tryckning. |
| Aktivera sökfält | bool | FALSE | Aktiverar sökfältet på startskärmen. Om du aktiverar det här ser enhetens användare sökfältet på startskärmen, där de kan ange vad de vill söka efter på webben. |
| Inaktivera inställningsappen | bool | FALSE | Inaktiverar inställningssidan för den hanterade startskärmen. Om du inaktiverar det här kan enhetens användare inte komma åt inställningar på den hanterade startskärmen. |
| Aktivera skärmsläckare | bool | FALSE | Aktivera eller inaktivera skärmsläckarläget. Om det är inställt på true (sant) kan du konfigurera **screen_saver_image**, **screen_saver_show_time**,   **inactive_time_to_show_screen_saver** och   **media_detect_screen_saver**. |
| Skärmsläckarbild | sträng |   | Ange webbadressen till skärmsläckarbilden. Om ingen webbadress anges visas standardskärmsläckaren på skärmen när skärmsläckaren aktiveras. Standardbilden visar appikonen för den hanterade hemskärmen.  |
| Skärmsläckaren Visa tid | heltal | 0 | Ger möjlighet att ange hur lång tid i sekunder enheten ska visa skärmsläckaren under skärmsläckarläget. Om värdet är 0 visas skärmsläckaren på obestämd tid tills enheten blir aktiv.  |
| Inaktiv tid för aktivering av skärmsläckare | heltal | 30 | Antalet sekunder som enheten är inaktiv innan skärmsläckaren utlöses. Om värdet är 0 aktiveras aldrig skärmsläckarläget. |
| Medieidentifiering innan skärmsläckare visas | bool | TRUE | Välj om enhetens skärm ska visa skärmsläckaren om ljud/video spelas på enheten. Om det är inställt på true (sant) spelar inte enheten upp ljud/video, oavsett värdet i **inactive_time_to_show_scree_saver**. Om det är inställt på false (falskt) visar skärmen skärmsläckaren enligt värdet i **inactive_time_to_show_screen_saver**.   |
| Aktivera virtuell hemknapp | bool | FALSE | Ställ in den här inställningen på `True` om du vill ge användaren åtkomst till en hemknapp för den hanterade startskärmen som skickar tillbaka användaren till den hanterade startskärmen från deras aktuella aktivitet.  |
| Typ av virtuell hemknapp | sträng | swipe_up | Använd **swipe_up** för att få åtkomst till hemknappen med en uppsvepningsgest. Använd **flyt** för att få åtkomst till en fäst, beständig hemknapp som slutanvändaren kan flytta på skärmen. |
| Indikator för batteri och signalstyrka | bool | Sant  | Om du ställer in den här inställningen på `True` visas en indikator för batteri och signalstyrka. |
| Lösenord för att avsluta låst läge för uppgift | sträng |   | Ange en kod som består av 4–6 siffror som ska användas för att tillfälligt ta bort läget för låst uppgift för felsökning. |
| Visa inställningar för trådlöst nätverk | bool | FALSE | Om du ställer in den här inställningen på `True` kan användaren aktivera eller inaktivera Wi-Fi eller ansluta till olika Wi-Fi-nätverk.  |
| Visa Bluetooth-inställning | bool | FALSE | Om du ställer in den här inställningen på `True` kan användaren aktivera eller inaktivera Bluetooth och ansluta till olika Bluetooth-aktiverade enheter.   |
| Programmen i mappen sorteras efter namn | bool | TRUE | När den inställningen är `False` visas objekt i en mapp i den angivna ordningen. Annars visas de i bokstavsordning i mappen.   |
| Programordning har aktiverats | bool | FALSE | När den här inställningen är `True` kan program, webblänkar och mappar visas i en vald ordning på den hanterade startskärmen. När den är aktiv kan du ställa in ordningen med **app_order**. Användaren kan aktivera eller inaktivera Bluetooth och ansluta till olika Bluetooth-aktiverade enheter.   |
| Programordning | bundleArray | FALSE | Du kan ange i vilken ordning program, webblänkar och mappar visas på den hanterade hemskärmen. För att använda inställningen måste **Lås hemskärmen** vara aktivt, **Ställ in rutnätsstorlek** måste ha definierats och **Aktivera programordning** måste vara inställd på `True`.   |

## <a name="enter-json-data"></a>Ange JSON-data

Ange JSON-data om du vill konfigurera alla tillgängliga inställningar för den hanterade startskärmen samt de inställningar som är inaktiverade i **Configuration Designer**.

![Skärmbild av tillagda JSON-data](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

Förutom listan över konfigurerbara inställningar som anges i **Configuration Designer**-tabellen (ovan) innehåller följande tabell konfigurationsnycklar som du bara kan konfigurera via JSON-data.

|    Konfigurationsnyckel    |    Värdetyp    |    Standardvärde    |    Beskrivning    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Ange tillåtna program    |    bundleArray    | <img alt="JSON - Example 1" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson01.png" width="300"> |    Gör att du kan definiera en uppsättning appar som ska visas på startskärmen bland apparna som är installerade på enheten. Du kan definiera appar genom att ange paketnamnet för de appar som du vill göra synliga. Till exempel skulle com.android.settings göra inställningar tillgängliga på startskärmen. Apparna som du godkänner i det här avsnittet bör vara installerade på enheten för att kunna visas på startskärmen.    |
|    Ställa in fästa webblänkar    |    bundleArray    | <img alt="JSON - Example 2" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson02.png" width="300"> |    Du kan fästa webbplatser som snabbstartsikoner på startskärmen. Med den här konfigurationen kan du definiera webbadressen och lägga till den på startskärmen så att användaren kan starta webbläsaren med en tryckning.    |
|    Skapa en hanterad mapp för gruppering av appar    |    bundleArray    | <img alt="JSON - Example 3" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson03.png" width="300"> |    Gör att du kan skapa och namnge mappar och gruppappar i de här mapparna. Slutanvändarna kan inte flytta mappar, byta namn på mappar eller flytta appar i mapparna.   Mapparna visas i den ordning som skapats och apparna i mapparna visas i alfabetisk ordning.         Obs! Alla appar som du vill gruppera i mappar måste tilldelas till enheten och måste ha lagts till på den hanterade startskärmen.     |

Här följer ett exempel på ett JSON-skript med alla tillgängliga konfigurationsnycklar:

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "com.microsoft.launcher.enterprise",
    "managedProperty": [
        {
            "key": "keep_page_header",
            "valueBool": true
        },
        {
            "key": "keep_status_bar",
            "valueBool": true
        },
        {
            "key": "show_notification_badge",
            "valueBool": false
        },
        {
            "key": "lock_home_screen",
            "valueBool": true
        },
        {
            "key": "wallpaper",
            "valueString": "default"
        },
        {
            "key": "icon_size",
            "valueInteger": 2
        },
        {
            "key": "app_folder_icon",
            "valueInteger": 0
        },
        {
            "key": "gesture_on",
            "valueBool": false
        },
        {
            "key": "vertical_scrolling",
            "valueBool": false
        },
        {
            "key": "theme",
            "valueString": "Theme.Light.Blue"
        },
        {
            "key": "dock_enable",
            "valueBool": false
        },
        {
            "key": "screen_orientation",
            "valueInteger": 1
        },
        {
            "key": "feed_enable",
            "valueBool": false
        },
        {
            "key": "allow_overview_mode",
            "valueBool": false
        },
        {
            "key": "enable_telemetry",
            "valueBool": false
        },
        {
            "key": "applications",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": “app package name here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "weblinks",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "link",
                            "valueString": “link here”
                        },
                        {
                            "key": "label",
                            "valueString": “weblink label here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "search_bar",
            "valueBool": false
        },
        {
            "key": "hide_settings",
            "valueBool": false
        },
        {
            "key": "show_virtual_home",
            "valueBool": false
        },
        {
            "key": "virtual_home_type",
            "valueString": "swipe_up"
        },
        {
            "key": "show_virtual_status_bar",
            "valueBool": true
        },
        {
            "key": "exit_lock_task_mode_code",
            "valueString": ""
        },
        {
            "key": "show_wifi_setting",
            "valueBool": false
        },
        {
            "key": "show_bluetooth_setting",
            "valueBool": false
        },
        {
            "key": "grid_size",
            "valueString": "4;5"
        },
        {
            "key": "app_order_enabled",
            "valueBool": true
        },
        {
            "key": "apps_in_folder_ordered_by_name",
            "valueBool": true
        },
        {
            "key": "app_orders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.Microsoft.emmx"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 1
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Work"
                        },
                        {
                            "key": "type",
                            "valueString": "managed_folder"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 2
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.microsoft.launcher.enterprise"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "class",
                            "valueString": "com.microsoft.launcher.launcher"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 3
                        }
                    ]
                }
            ]
        },
        {
            "key": "managed_folders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Folder name here"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.emmx"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.bing"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "link",
                                            "valueString": "https://microsoft.com/"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Example folder name 2"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.office.word"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}
```

## <a name="googles-android-device-policy-app"></a>Googles Android Device Policy-app
Nu ger Managed Home Screen-appen tillgång till Googles Android Device Policy-app. Managed Home Screen-appen är en anpassad startfunktion som används med enheter som har registrerats i Intune som AE-dedikerade (Android Enterprise) enheter som använder helskärmsläge för flera appar. Du kan komma åt Android Device Policy-appen, eller vägleda användare till Android Device Policy-appen, för support och felsökning. Den här startfunktionen är tillgänglig när enheten registreras och låses på startskärmen i Managed Home Screen. Inga ytterligare installationer behövs för att använda den här funktionen.

## <a name="next-steps"></a>Nästa steg

- Mer information om Android Enterprise-dedikerade enheter finns i [Konfigurera Intune-registrering av dedikerade Android Enterprise-enheter](android-kiosk-enroll.md).
