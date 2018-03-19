---
title: "Inställningar av begränsningar i Microsoft Intune-enheter för Windows Phone 8.1"
titleSuffix: 
description: "Läs vilka Intune-inställningar du kan använda för att kontrollera enhetsinställningar och funktioner på enheter som kör Windows Phone 8.1."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 808c8e9ac1ef944b69ae8e548c62d4c6366820d0
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-windows-phone-81-device-restriction-settings"></a>Inställningar för enhetsbegränsningar för Windows Phone 8.1-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I den här artikeln visas inställningarna av enhetsbegränsningar som du kan konfigurera för enheter som kör Windows Phone 8.1.


## <a name="general"></a>Allmänt

-   **Kamera** – Tillåter eller blockerar kameran på enheten.
-   **Kopiera och klistra in** – Tillåter eller blockerar kopierings- och inklistringsfunktioner på enheter.
-   **Flyttbara lagringsmedia** – Tillåter att enheten använder flyttbara lagringsmedia, t.ex. SD-kort.
-   **Geoplats** – Gör att enheten använder platsinformation.
-   **Microsoft-konto** – Tillåter eller blockerar användaren från att länka ett Microsoft-konto till enheten.
-   **Skärmdump** – Låter användaren fånga innehållet på skärmen som en bildfil.
-   **Sändning av diagnostikdata** – Gör att enheten skickar diagnostikinformation till Microsoft.
-   **Synkronisering av anpassade e-postkonton** – Gör det möjligt för enheten att ansluta till andra e-postkonton än Microsoft-e-postkonton.

## <a name="password"></a>Lösenord

-   **Lösenord** – Kräver att användaren måste ange ett lösenord för att få åtkomst till enheten.
    -   **Krav på lösenordstyp** – Anger vilken typ av lösenord som krävs, t.ex. enbart alfanumeriskt eller numeriskt.
    -   **Minsta längd på lösenord** – Anger det minsta antalet tecken som lösenordet måste innehålla.
    -   **Enkla lösenord** – Anger att enkla lösenord kan användas, t.ex. 0000 och 1234.
    -   **Antal felaktiga inloggningar innan enheten rensas** – Anger hur många gånger ett felaktigt lösenord kan anges innan enheten rensas.
    -   **Maximalt antal minuter av inaktivitet innan skärmen låses** – Anger hur lång tid en enhet måste vara i viloläge innan skärmen låses automatiskt.
    -   **Lösenordets giltighetstid (dagar)** – Anger antal dagar innan lösenordet för enheten måste ändras.
    -   **Förhindra återanvändning av tidigare lösenord** – Anger hur många tidigare använda lösenord som koms ihåg.
-   **Kryptering** – Kräver att data på mobila enheter som stöds krypteras.

## <a name="app-store"></a>Appbutik

-   **Appbutik** – Tillåter att användarna ansluter till appbutiken från enheten.

## <a name="restricted-apps"></a>Begränsade appar

Du kan konfigurera en av följande listor i listan med begränsade appar:

Listan **Blockerade appar** – Ange de appar (som inte hanteras av Intune) som användarna inte får installera och köra.
Listan **Tillåtna appar** – Ange de appar som användare tillåts att installera. Appar som hanteras av Intune tillåts automatiskt.

Konfigurera listan genom att klicka på **Lägg till**, ange ett namn, t.ex. appens utgivare samt webbadressen till appen i appbutiken.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Så här anger du webbadressen till appen i butiken

Om du vill ange en app-URL i listan över tillåtna och blockerade appar använder du följande format:

Gå till sidan [Windows Phone Store](https://www.microsoft.com/store/apps/windows-phone) och sök efter den app du vill använda.

Öppna appens sida och kopiera webbadressen till Urklipp. Nu kan du använda den som webbadress i listan över tillåtna eller blockerade appar.

Exempel: Sök i butiken efter Skype-appen. Webbadressen som du använder är **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.



### <a name="additional-options"></a>Ytterligare alternativ

Du kan också klicka på **Importera** för att fylla i listan från en csv-fil i formatet <*app-url*>, <*appnamn*> <app publisher> eller klicka på**Exportera**Exportera för att skapa en csv-fil med innehållet i listan över begränsade appar i samma format.


## <a name="browser"></a>Webbläsare

-   **Webbläsare** – Tillåter eller blockerar den inbyggda webbläsaren på enheter.

## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning

-   **Wi-Fi** – Aktiverar eller inaktiverar Wi-Fi-funktioner på enheten.
-   **Trådlös Internetdelning** – Tillåter att trådlös Internetdelning används på enheten.
-   **Anslut automatiskt till trådlösa surfpunkter** – Gör att enheten ansluter automatiskt till kostnadsfria trådlösa surfpunkter och att den automatiskt godkänner användningsvillkoren.
-   **Rapportering om trådlösa surfzoner** – Skickar information om Wi-Fi-anslutningar så att användaren lättare kan upptäcka närliggande anslutningar.
-   **NFC** – Aktiverar eller inaktiverar åtgärder som använder närfältskommunikation på de enheter som stöds.
-   **Bluetooth** – Aktiverar eller inaktiverar Bluetooth-funktionen på enheten.
