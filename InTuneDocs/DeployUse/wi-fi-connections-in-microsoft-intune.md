---
# required metadata

title: Wi-Fi-anslutningar | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

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

För enheter som kör Windows 8.1 och senare kan du importera en Wi-Fi-konfigurationsprofil som tidigare exporterats till en fil. Mer information finns i Importera en Wi-Fi-profil senare i det här avsnittet.

## Skapa en Wi-Fi-profil

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) klickar du på **Princip** &gt; **Lägg till princip**

2.  Välj en av följande principtyper och klicka sedan på **Skapa princip**:

    -   **Wi-Fi-profil (Android 4 och senare)**

    -   **Wi-Fi-profil (iOS 7.1 och senare)**

    -   **Wi-Fi-profil (Mac OS X 10.9 och senare)**

    Det finns inga rekommenderade inställningar för den här principtypen. Du måste skapa en anpassad princip.

3.  Ange ett namn och en beskrivning för profilen.

4. Ange värdena för **nätverksanslutningar** :

  |Inställning|Mer information| **Nätverksnamn**| Ange ett beskrivande namn för det trådlösa nätverket. Det här är namnet som visas på användarnas enheter när de väljer ett nätverk.|

5. **SSID (Service Set Identifier)**| Ange SSID för det trådlösa nätverk som enheterna ska ansluta till. SSID är skiftlägeskänsligt och visas inte för användarna.|

  #### **Anslut automatiskt när det här nätverket är inom räckhåll**| Välj det här alternativet om enheterna ska ansluta automatiskt till det trådlösa nätverket när det är inom räckhåll.|

  **Anslut när nätverket inte sänder sitt namn (SSID)**|Välj det här alternativet om du vill tillåta att enheterna ansluter till nätverket när det inte visas i listan med nätverk (eftersom det är dolt och inte sänder sitt namn).|<br /><br />-   **Konfigurera **säkerhetsinställningarna** för den valda plattformen.**<br />-   De tillgängliga inställningarna beror på vilken säkerhetstyp du väljer.<br /><br />-   **För Android-enheter**<br />-   **|Inställningens namn|Mer information|Använd när:|**<br />-   **Säkerhetstyp**| Välj säkerhetsprotokoll för det trådlösa nätverket: WPA-Enterprise/WPA2-Enterprise<br /><br />-   **Ingen autentisering (öppet)** om nätverket är oskyddat.|Alltid|<br />-   **EAP-typ**|Välj EAP-typen (Extensible Authentication Protocol) som används för att autentisera skyddade trådlösa anslutningar:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   ****EAP-TTLS**|Du har valt säkerhetstypen **WPA-Enterprise/WPA2-Enterprise**.|**<br />-   ****Välj rotcertifikat för serververifiering**| Klicka på **Välj** och välj sedan den betrodda rotcertifikatprofil som används för att autentisera anslutningen.**<br />-   ****Viktigt!** Information om hur du skapar betrodda rotcertifikatprofiler finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).| En **EAP-typ** har valts. |**<br /><br />**Autentiseringsmetod**|Välj autentiseringsmetod för anslutningen: **Certifikat** för att ange klientcertifikatet **Användarnamn och lösenord** om du vill ange en annan metod för autentisering|**EAP-typen** är **PEAP** eller **EAP-TTLS** **Välj en annan metod än EAP för autentisering (inre identitet)**|Välj hur du ska autentisera anslutningen:

  #### Inga

  Okrypterat lösenord (PAP)<br /><br />-   **CHAP (Challenge Handshake Authentication Protocol)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP Version 2 (MS-CHAP v2)**<br />-   De tillgängliga alternativen beror på vilken EAP-typ du valt.|**Autentiseringsmetod** är **Användarnamn och lösenord**<br /><br />-   ****Aktivera identitetssekretess (yttre identitet)**|Ange texten som skickas som svar på en begäran om EAP-identitet.**<br />-   **Den här texten kan ha vilket värde som helst.**<br />-   **Vid autentiseringen skickas den här anonyma identiteten först, följt av den verkliga identifieringen som skickas i en säker tunnel.|**EAP-typen** är **PEAP** eller **EAP-TTLS****<br />-   ****Välj ett klientcertifikat för klientautentisering (identitetscertifikat)**|Klicka på **Välj** och sedan på SCEP-certifikatprofilen som används för att autentisera anslutningen.**<br />-   ****Viktigt!** Information om hur du skapar en SCEP-certifikatprofil finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).|Säkerhetstypen är **WPA-Enterprise/WPA2-Enterprise** och en **EAP-typ** har valts.|**<br />-   För iOS- och Mac OS X-enheter |Inställningens namn|Mer information|Använd när:| **Säkerhetstyp**|Välj säkerhetsprotokollet för trådlösa nätverk:<br /><br />WPA-Personal/WPA2-Personal<br /><br /><ul><li>WPA-Enterprise/WPA2-Enterprise</li><li>WEP<br /><br /><ul><li>****Ingen autentisering (öppet)** om nätverket är oskyddat.|Alltid|**</li><li>****EAP-typ**|Välj EAP-typen (Extensible Authentication Protocol) som används för att autentisera skyddade trådlösa anslutningar:**</li><li>**EAP-TLS**</li><li>**PEAP**</li><li>**EAP-TLS**</li><li>**EAP-AST**</li></ul></li></ul>LEAP **EAP-SIM**|Du har valt säkerhetstypen **WPA-Enterprise/WPA2-Enterprise** **Namn på betrodda servercertifikat**|Välj den betrodda rotcertifikatprofil som används för att autentisera anslutningen.<br /><br />**Viktigt!** Information om hur du skapar en betrodd rotcertifikatprofil finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).|Du har valt EAP-typen **EAP-TLS**, **PEAP**, **EAP-TTLS** eller **EAP-FAST**

6. **Använd Protected Access Credential (PAC)**|Välj den här inställningen om du vill använda skyddade autentiseringsuppgifter för att upprätta en autentiserad tunnel mellan klienten och autentiseringsservern.

    |En befintlig PAC-fil används om den finns.|**EAP-typen** är **EAP-FAST**|**Etablera PAC**|Etablerar PAC-filen till dina enheter.|När den används kan du även välja **Etablera PAC anonymt** för att säkerställa att PAC-filen etableras utan att servern autentiseras.|**Använd PACK (Protected Access Credential)** har valts.||
    |----------------|-------------------|-------------|
    |****Autentiseringsmetod**|Välj autentiseringsmetoden som används för anslutningen:**|**Certifikat** för att ange klientcertifikatet<br /><br />-   **Användarnamn och lösenord** för att ange någon av följande icke-EAP-metoder för autentisering (även kallat inre identitet):<br />-   Inga<br />-   Okrypterat lösenord (PAP)|CHAP (Challenge Handshake Authentication Protocol)|
    |Microsoft CHAP (MS-CHAP)|Microsoft CHAP Version 2 (MS-CHAP v2)|EAP-TLS|
    |**|**EAP-typen** är **PEAP** eller **EAP-TTLS****|**Välj ett klientcertifikat för klientautentisering (identitetscertifikat)**|Välj SCEP-certifikatprofilen som används för att autentisera anslutningen.|**Viktigt!** Information om hur du skapar en SCEP-certifikatprofil finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).|När säkerhetstypen är **WPA-Enterprise/WPA2-Enterprise** och **EAP-typen** är **EAP-TLS**, **PEAP** eller **EAP-TTLS**|

7.  **Aktivera identitetssekretess (yttre identitet)**|Ange texten som skickas som svar på en begäran om EAP-identitet.

Den här texten kan ha vilket värde som helst. Under autentiseringen skickas den här anonyma identiteten först, följt av den verkliga identifieringen som skickas i en säker tunnel.|När **EAP-typen** är **PEAP**, **EAP-TTLS** eller **EAP-FAST**

## (endast iOS och MAC OS X) Konfigurera **Proxyinställningar**

### Inställningsnamn
Mer information Använd när:

1.  Proxy-inställningar för den här Wi-Fi-anslutningen

2.  Välj inställningstyp för proxy:

3.  **Ingen** (standard)  **Manuell** – Ange URL:en och portnumret för proxyservern manuellt.

4.  **Automatisk** – Använd en konfigurationsfil för att konfigurera proxyservern.

## Alltid
**Proxyserveradress** och **-portnummer** Ange proxyserverns URL och portnummer.

1.  **Proxyinställningar för den här Wi-Fi-anslutningen** har angetts till **Manuell**

2.  URL för proxyserver

    Ange URL till den fil som innehåller inställningarna för proxyservern. **Proxyinställningar för den här Wi-Fi-anslutningen** har angetts till **Automatisk**

3.  Spara Wi-Fi-profilen

    |Ny princip som visas i noden **Konfigurationsprinciper** på arbetsytan **Princip** .|Information om hur du distribuerar profilen finns under **Nästa steg**.|
    |----------------|--------------------|
    |**Exportera eller importera en Wi-Fi-konfigurationsprofil (endast Windows 8.1 och senare)**|Exportera en Wi-Fi-profil|
    |**I Windows kan du använda verktyget **netsh wlan** för att exportera en befintlig Wi-Fi-profil till en XML-fil som kan läsas av Intune.**|Följ stegen nedan på en Windows-dator som redan har nödvändig WiFi-profil installerad.|

4.  Skapa en lokal mapp för de exporterade W-Fi-profilerna, till exempel c:\WiFi

    |Öppna en kommandotolk som administratör.|Kör kommandot `netsh wlan show profiles` och notera namnet på den profil som du vill exportera.|
    |----------------|--------------------|
    |**I det här exemplet är profilnamnet *WiFiName***|Kör det här kommandot: `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. När du gör det skapas en Wi-Fi-profilfil med namnet ”Wi-Fi-WiFiName.xml” i målmappen.|
    |**Importera en Wi-Fi-profil**|Använd **Importprincipen för Windows Wi-Fi** för att importera en uppsättning Wi-Fi-inställningar som du kan distribuera till nödvändiga användar- eller enhetsgrupper.|
    |**Stegen som du följer för att exportera en Wi-Fi-profil beskrivs i**|I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) klickar du på **Princip** &gt; **Lägg till princip**|

5.  Konfigurera en princip av typen **Windows** &gt; **Windows Wi-Fi-importprincip**

6.  Du kan bara skapa och distribuera anpassade Windows Wi-Fi-importprinciper.

## Rekommenderade inställningar är inte tillgängliga.

1.  Ange följande allmänna värden för Windows Wi-Fi-importprincip:

2.  Inställningsnamn

    -   Mer information

    -   Namn


Ange ett unikt namn för Wi-Fi-profilen som hjälper dig att identifiera den i Intune-konsolen. Beskrivning


<!--HONumber=May16_HO2-->


