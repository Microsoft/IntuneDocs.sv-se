---
title: Wi-Fi-anslutningar | Microsoft Intune
description: "Använd VPN-profiler för att distribuera VPN-inställningar till användare och enheter i organisationen."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 271d2be675ab808365cd6869c69d386058f76ae8


---

# Wi-Fi-anslutningar i Microsoft Intune
Använd Wi-Fi-profiler i Microsoft Intune om du vill distribuera trådlösa nätverksinställningar till användare och enheter i din organisation. Med dessa inställningar blir det lättare för användarna att ansluta till trådlösa nätverk.

Anta till exempel att du installerar ett nytt Wi-Fi-nätverk med namnet **Contoso Wi-Fi** och att du vill konfigurera alla iOS-enheter så att de ansluter till det här nätverket. Så här ser processen ut:

1.   Skapa en Wi-Fi-profil som innehåller alla inställningar som behövs för att ansluta till det trådlösa nätverket **Contoso Wi-Fi**.

2. Distribuera profilen till gruppen med användare med iOS-enheter.

3.   Det nya nätverket **Contoso Wi-Fi** visas i listan över trådlösa nätverk så att användarna enkelt kan ansluta till nätverket.

Du kan distribuera Wi-Fi-profiler till följande plattformar:

-   Android 4.0 och senare

-   iOS 7.1 och senare

-   Mac OS X 10.9 och senare

För enheter som kör Windows 8.1 och Windows 10 (Desktop eller Mobile) kan du importera en Wi-Fi-konfigurationsprofil som tidigare exporterades till en fil. Mer information finns i **Importera en Wi-Fi-profil** senare i det här avsnittet.

## Skapa en Wi-Fi-profil

1.  Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och klicka på **Princip** &gt; **Lägg till princip**.

2.  Välj en av följande principtyper och klicka sedan på **Skapa princip**:

    -   **Wi-Fi-profil (Android 4 och senare)**

    -   **Wi-Fi-profil (iOS 7.1 och senare)**

    -   **Wi-Fi-profil (Mac OS X 10.9 och senare)**

    Det finns inga rekommenderade inställningar för den här principtypen. Du måste skapa en anpassad princip.

3.  Ange ett namn och en beskrivning för profilen.

4. Ange värdena för **nätverksanslutningar** :

  |Inställningar|Mer information|
|-----------|--------------------|
|**Nätverksnamn**|Ange ett beskrivande namn för det trådlösa nätverket. Det här är namnet som visas på användarnas enheter när de väljer ett nätverk.|
|**SSID (Service Set Identifier)**|Ange ett SSID för det trådlösa nätverk som enheterna ska anslutas till. SSID är skiftlägeskänsligt och visas inte för användaren.|
|**Anslut automatiskt när det här nätverket är inom räckhåll**|Välj det här alternativet om enheterna automatiskt ska ansluta till det trådlösa nätverket när det är inom räckhåll.|
|**Anslut när nätverket inte sänder sitt namn (SSID):**|Välj det här alternativet om du vill tillåta att enheterna ansluter till nätverket när det inte visas i listan med nätverk (eftersom det är dolt).|

5. Konfigurera **säkerhetsinställningarna** för den valda plattformen. De tillgängliga inställningarna beror på vilken säkerhetstyp du väljer.

  #### För Android-enheter

  |Inställningsnamn|Mer information|Använd när:|
|----------------|--------------------|-------------|
|**Säkerhetstyp**|Välj säkerhetsprotokoll för det trådlösa nätverket:<br /><br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **Ingen autentisering (öppet)** om nätverket är oskyddat.|Alltid|
|**EAP-typ**|Välj typen EAP (Extensible Authentication Protocol) som används för att autentisera säkra trådlösa anslutningar:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|Du har valt säkerhetstypen **WPA-Enterprise/WPA2-Enterprise**.|
|**Välj rotcertifikat för serververifiering**|Klicka på **Välj**och välj sedan den betrodda rotcertifikatsprofil som används för att autentisera anslutningen. **Viktigt!** Information om hur du skapar betrodda rotcertifikatprofiler finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).|Valfri **EAP-typ** är markerad.|
|**Autentiseringsmetod**|Välj autentiseringsmetod för anslutningen:<br /><br />-   **Certifikat** för att ange klientcertifikatet<br />-   **Användarnamn och lösenord** för att ange en annan metod för autentisering|**EAP-typen** är **PEAP** eller **EAP-TTLS**.|
|**Välj en annan metod än EAP för autentisering (inre identitet)**|Välj hur du ska autentisera anslutningen:<br /><br />-   **Inga**<br />-   **Okrypterat lösenord (PAP)**<br />-   **CHAP (Challenge Handshake Authentication Protocol)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP Version 2 (MS-CHAP v2)**<br /><br />Vilka alternativ som är tillgängliga beror på vilken EAP-typ du väljer.| **Autentiseringsmetoden** är **användarnamn och lösenord**.|
|**Aktivera identitetssekretess (yttre identitet)**|Ange vilken text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.|**EAP-typen** är **PEAP** eller **EAP-TTLS**.|
|**Välj ett certifikat för klientautentisering (identitetscertifikat)**|Klicka på **Välj**och välj sedan den SCEP-certifikatsprofil som ska användas för att autentisera anslutningen. **Viktigt!** Information om hur du skapar betrodda SCEP-certifikatprofiler finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).|Säkerhetstypen är **WPA-Enterprise/WPA2-Enterprise** och en **EAP-typ** är markerad.|

  #### För iOS- och Mac OS X-enheter

  |Inställningsnamn|Mer information|Använd när:|
|----------------|--------------------|-------------|
|**Säkerhetstyp**|Välj säkerhetsprotokoll för det trådlösa nätverket:<br /><br />-   **WPA-Personal/WPA2-Personal**<br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **WEP**<br />-   **Ingen autentisering (öppet)** om nätverket är oskyddat.|Alltid|
|**EAP-typ**|Välj typen EAP (Extensible Authentication Protocol) som används för att autentisera säkra trådlösa anslutningar:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-AST**<br />-   **LEAP**<br />-   **EAP-SIM**|Du har valt säkerhetstypen **WPA-Enterprise/WPA2-Enterprise**.|
|**Namn på betrodda servercertifikat**|Markera den betrodda rotcertifikatsprofil som ska användas för att autentisera anslutningen. **Viktigt!** Information om hur du skapar betrodda rotcertifikatprofiler finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).|Du har valt EAP-typen **EAP-TLS**, **PEAP**, **EAP-TTLS** eller **EAP-FAST**.|
|**Använd PAC (Protected Access Credential)**|Välj det här alternativet om du vill etablera en autentiserad tunnel mellan klienten och autentiseringsservern. En befintlig PAC-fil används om det finns en sådan.|**EAP-typen** är **EAP-FAST**.|
|**Etablera PAC**|Etablerar PAC-filen till enheterna.<br /><br />När detta används kan du också välja **Etablera PAC anonymt** för att säkerställa att PAC-filen etableras utan att servern autentiseras.|**Använd PAC** är markerat|
|**Autentiseringsmetod**|Välj den autentiseringsmetod som ska användas för anslutningen:<br /><br /><ul><li>**Certifikat** för att ange klientcertifikatet</li><li>**Användarnamn och lösenord** för att ange någon av följande icke-EAP-metoder för autentisering (även kallat inre identitet):<br /><br /><ul><li>**Inga**</li><li>**Okrypterat lösenord (PAP)**</li><li>**CHAP (Challenge Handshake Authentication Protocol)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP Version 2 (MS-CHAP v2)**</li><li>**EAP-TLS**</li></ul></li></ul>|**EAP-typen** är **PEAP** eller **EAP-TTLS**.|
|**Välj ett certifikat för klientautentisering (identitetscertifikat)**|Markera den SCEP-certifikatsprofil som ska användas för att autentisera anslutningen. **Viktigt!** Information om hur du skapar betrodda SCEP-certifikatprofiler finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).|När säkerhetstypen är **WPA-Enterprise/WPA2-Enterprise** och **EAP-typen** är **EAP-TLS**, **PEAP** eller **EAP-TTLS**.|
|**Aktivera identitetssekretess (yttre identitet)**|Ange vilken text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst.<br /><br />Under autentiseringen skickas den här anonyma identiteten från början, följd av den av den verkliga identifieringen som skickas i en säker tunnel.|Om **EAP-typen** har angetts till **PEAP**, **EAP-TTLS** eller **EAP-FAST**.|

6. (endast iOS och MAC OS X) Konfigurera **Proxyinställningar**

    |Inställningsnamn|Mer information|Använd när:|
    |----------------|-------------------|-------------|
    |**Proxy-inställningar för den här Wi-Fi-anslutningen**|Välj inställningstyp för proxy:<br /><br />-   **Ingen** (standard)<br />-   **Manuell** – Ange URL:en och portnumret för proxyservern manuellt.<br />-   **Automatisk** – Använd en konfigurationsfil för att konfigurera proxyservern.|Alltid|
    |**Proxyserveradress** och **-portnummer**|Ange proxyserverns URL och portnummer.|**Proxyinställningar för den här Wi-Fi-anslutningen** har angetts till **Manuell**|
    |**URL för proxyserver**|Ange URL till den fil som innehåller inställningarna för proxyservern.|**Proxyinställningar för den här Wi-Fi-anslutningen** har angetts till **Automatisk**|

7.  Spara Wi-Fi-profilen

Ny princip som visas i noden **Konfigurationsprinciper** på arbetsytan **Princip** . Information om hur du distribuerar profilen finns under **Nästa steg**.

## Exportera eller importera en Wi-Fi-konfigurationsprofil (endast Windows 8.1 och senare)

### Exportera en Wi-Fi-profil
I Windows kan du använda verktyget **netsh wlan** för att exportera en befintlig Wi-Fi-profil till en XML-fil som kan läsas av Intune. Följ stegen nedan på en Windows-dator som redan har nödvändig WiFi-profil installerad.

1.  Skapa en lokal mapp för de exporterade W-Fi-profilerna, till exempel c:\WiFi

2.  Öppna en kommandotolk som administratör.

3.  Kör kommandot `netsh wlan show profiles` och notera namnet på den profil som du vill exportera.  I det här exemplet är profilnamnet *WiFiName*.

4.  Kör det här kommandot: `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. När du gör det skapas en Wi-Fi-profilfil med namnet ”Wi-Fi-WiFiName.xml” i målmappen.

### Importera en Wi-Fi-profil
Använd **Importprincipen för Windows Wi-Fi** för att importera en uppsättning Wi-Fi-inställningar som du kan distribuera till nödvändiga användar- eller enhetsgrupper.


1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) klickar du på **Princip** &gt; **Lägg till princip**.

2.  Konfigurera en princip av typen **Windows** &gt; **Importera trådlöst nätverk (Windows 8.1 och senare)**.

    Den här principen kan tillämpas på enheter med Windows 8.1 och Windows 10 (Desktop och Mobile).

    Du kan bara skapa och distribuera *anpassade* Windows Wi-Fi-importprinciper. Rekommenderade inställningar är inte tillgängliga.

3.  Ange följande allmänna värden för Windows Wi-Fi-importprincip:

    |Inställningsnamn|Mer information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för Wi-Fi-profilen som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en beskrivning av Wi-Fi-profilen och annan relevant information som gör det enkelt att hitta profilen.|

4.  Ange följande värden under rubriken **Anpassad Wi-Fi-profil**:

    |Inställningsnamn|Mer information|
    |----------------|--------------------|
    |**Konfigurationsprofilsfil**|Klicka på **Importera** för att välja XML-filen som innehåller de Wi-Fi-profilinställningar som du vill importera till Intune.|
    |**Anpassat konfigurationsprofilsnamn (visas för användare)**|Visar namnet på konfigurationsprofilen för Wi-Fi-nätverket, så  som det visas på användarens enhet.|
    |**Information om konfigurationsprofilen**|Visar XML-koden för den konfigurationsprofil du har valt.|

5.  När du är klar klickar du på **Spara profilen**.

6.  Ny princip som visas i noden **Konfigurationsprinciper** i arbetsytan **Principer** .

## Distribuera principen

1.  Välj den princip på arbetsytan **Princip** som du vill distribuera och klicka sedan på **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** :

    -   **Om du vill distribuera principen** markerar du en eller flera grupper som du vill distribuera principen till och klickar sedan på **Lägg till** &gt; **OK**.

    -   **Om du vill stänga dialogrutan utan att distribuera den** – Klicka på **Avbryt**.


En statssammanfattning och varningar på sidan **Översikt** på arbetsytan **Principer** identifierar problem med principer som kräver din uppmärksamhet. Dessutom visas en statussammanfattning på arbetsytan Instrumentpanel.

### Se även
Läs om hur du skapar en Wi-Fi-profil med en i förväg delad nyckel i [Wi-Fi-profil med i förväg delad nyckel](pre-shared-key-wi-fi-profile.md)



<!--HONumber=Jul16_HO4-->


