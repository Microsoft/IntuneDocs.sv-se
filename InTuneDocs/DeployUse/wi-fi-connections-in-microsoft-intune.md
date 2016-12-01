---
title: Wi-Fi-anslutningar | Microsoft Intune
description: "Använd Wi-Fi-profiler för att hjälpa användarna att ansluta till trådlösa nätverk."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: df3f5bd6f44b9de8c4f24a82c7f4e000f08aac5a
ms.openlocfilehash: c90ede1f10ca8f01e01cf2ac4aed7afb8641f02f


---

# <a name="configure-devices-to-connect-to-your-corporate-wi-fi-networks"></a>Konfigurera enheter för att ansluta till företagets trådlösa nätverk

Använd Wi-Fi-profiler i Microsoft Intune om du vill distribuera trådlösa nätverksinställningar till användare och enheter i din organisation. När du distribuerar en Wi-Fi-profil får användarna åtkomst till ditt företags trådlösa nätverk utan att de behöver göra några inställningar själva.

Anta till exempel att du installerar ett nytt Wi-Fi-nätverk med namnet **Contoso Wi-Fi** och att du vill konfigurera alla iOS-enheter så att de ansluter till det här nätverket. Så här ser processen ut:

![Processammanfattning av Wi-Fi-profil](..\media\wi-fi-process-diagram.png)

1.   Skapa en Wi-Fi-profil som innehåller alla inställningar som behövs för att ansluta till det trådlösa nätverket **Contoso Wi-Fi**.

2.   Distribuera profilen till gruppen med användare med iOS-enheter.

3.   Det nya nätverket **Contoso Wi-Fi** visas i listan över trådlösa nätverk så att användarna enkelt kan ansluta till nätverket.


## <a name="create-a-wi-fi-profile"></a>Skapa en Wi-Fi-profil

Du kan distribuera Wi-Fi-profiler till följande plattformar:

-   Android 4.0 och senare

-   Android for Work   

-   iOS 8.0 och senare

-   Mac OS X 10.9 och senare

För enheter som kör operativsystemen Windows 8.1 och Windows 10 Desktop eller Mobile kan du importera en Wi-Fi-konfigurationsprofil som tidigare exporterades till en fil. Mer information finns i [Exportera eller importera en Wi-Fi-konfigurationsprofil för Windows-enheter](#export-or-import-a-wi-fi-configuration-profile-for-windows-devices).

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Lägg till princip**.

2.  Välj en av följande principtyper och välj sedan **Skapa princip**:

    -   Wi-Fi-profil (Android 4 och senare)

    -   Wi-Fi-profil (Android for Work)

    -   Wi-Fi-profil (iOS 8.0 och senare)

    -   Wi-Fi-profil (Mac OS X 10.9 och senare)


Det finns inga rekommenderade inställningar för den här principtypen. Du måste skapa en anpassad princip.

3.  Ange ett namn och en beskrivning för profilen.

4. Ange värden för **nätverksanslutningar**.
 - **SSID (Service Set Identifier)**: Välj det här alternativet om du vill att användarna ska se nätverksnamn och inte SSID.
 - **Anslut när nätverket inte sänder sitt namn (SSID)**: Välj det här alternativet om du vill tillåta att enheterna ansluter till nätverket när det inte visas i listan med nätverk (eftersom det är dolt och inte sänder sitt namn).

5. Konfigurera **säkerhetsinställningarna** för den valda plattformen. De tillgängliga inställningarna beror på vilken säkerhetstyp du väljer. De beskrivs i [säkerhetsinställningar](#security-settings).

6. Konfigurera **proxyinställningar** (endast iOS och MAC OS X).

    |Inställningsnamn|Mer information|När ska det användas|
    |----------------|-------------------|-------------|
    |**Proxy-inställningar för den här Wi-Fi-anslutningen**|Välj inställningstyp för proxy:<br /><br />-   **Ingen** (standard)<br />-   **Manuell** – Ange URL:en och portnumret för proxyservern manuellt.<br />-   **Automatisk** – Använd en konfigurationsfil för att konfigurera proxyservern.|Alltid|
    |**Proxyserveradress** och **-portnummer**|Ange proxyserverns URL och portnummer.|Om **Proxyinställningar för den här Wi-Fi-anslutningen** har angetts till **Manuell**|
    |**URL för proxyserver**|Ange URL till den fil som innehåller inställningarna för proxyservern.|Om **Proxyinställningar för den här Wi-Fi-anslutningen** har angetts till **Automatisk**|

7.  Spara Wi-Fi-profilen

Ny princip som visas i noden **Konfigurationsprinciper** på arbetsytan **Princip** . Information om hur du distribuerar profilen finns under **Nästa steg**.

## <a name="export-or-import-a-wi-fi-configuration-profile-for-windows-devices"></a>Exportera eller importera en Wi-Fi-konfigurationsprofil för Windows-enheter

För enheter som kör operativsystemen Windows 8.1 och Windows 10 Desktop eller Mobile kan du importera en Wi-Fi-konfigurationsprofil som tidigare exporterades till en fil.

### <a name="export-a-wi-fi-profile"></a>Exportera en Wi-Fi-profil
I Windows kan du använda verktyget **netsh wlan** för att exportera en befintlig Wi-Fi-profil till en XML-fil som kan läsas av Intune. Här är vad du kan göra på en Windows-dator som redan har den nödvändiga Wi-Fi-profilen installerad:

1.  Skapa en lokal mapp för de exporterade Wi-Fi-profilerna. Skapa till exempel en mapp med namnet **c:\WiFi.**

2.  Öppna en kommandotolk som administratör.

3.  Kör kommandot `netsh wlan show profiles` och notera namnet på den profil som du vill exportera.  I det här exemplet är profilnamnet **WiFiName**.

4.  Kör det här kommandot: `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. När du gör det skapas en Wi-Fi-profilfil med namnet **Wi-Fi-WiFiName.xml** i målmappen.

### <a name="import-a-wi-fi-profile"></a>Importera en Wi-Fi-profil
Använd **Importprincipen för Windows Wi-Fi** för att importera en uppsättning Wi-Fi-inställningar som du kan distribuera till nödvändiga användar- eller enhetsgrupper.


1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) klickar du på **Princip** &gt; **Lägg till princip**.

2.  Konfigurera en princip av typen **Windows** &gt; **Importera trådlöst nätverk (Windows 8.1 och senare)**.

    Den här principen kan tillämpas på enheter som kör operativsystemen Windows 8.1 och Windows 10 Desktop och Mobile.

    Du kan bara skapa och distribuera *anpassade* Windows Wi-Fi-importprinciper. Rekommenderade inställningar är inte tillgängliga.

3.  Ange följande allmänna värden för Windows Wi-Fi-importprincip:

    |Inställningsnamn|Mer information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för Wi-Fi-profilen som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en beskrivning av Wi-Fi-profilen och annan relevant information som gör det enkelt att hitta profilen.|

4.  Ange följande värden under rubriken **Anpassad Wi-Fi-profil**:

    |Inställningsnamn|Mer information|
    |----------------|--------------------|
    |**Konfigurationsprofilfil**|Välj **Importera** för att välja XML-filen som innehåller de Wi-Fi-profilinställningar som du vill importera till Intune.|
    |**Anpassat konfigurationsprofilnamn (visas för användare)**|Välj hur du vill visa namnet på konfigurationsprofilen för Wi-Fi-nätverket, så som det visas på användarens enhet.|
    |**Information om konfigurationsprofilen**|Välj hur du vill visa XML-koden för den konfigurationsprofil du har valt.|

5.  När du är klar väljer du **Spara princip**.

6.  Ny princip som visas i noden **Konfigurationsprinciper** i arbetsytan **Principer** .

## <a name="deploy-the-profile"></a>Distribuera profilen

Eftersom en profil är en typ av princip kan du distribuera den via arbetsytan **Princip**.

1.  På arbetsytan **Princip** markerar du den princip som du vill distribuera och väljer sedan **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** :

    -   **Om du vill distribuera principen**: Välj en eller flera grupper som du vill distribuera principen till. Välj sedan **Lägg till** &gt; **OK**.

    -   **Om du vill stänga dialogrutan utan att distribuera den**: Klicka på **Avbryt**.


Sidan **Översikt** av arbetsytan **Princip** visar problem med principer som kräver din uppmärksamhet. Dessutom visas en statussammanfattning på arbetsytan Instrumentpanel.

## <a name="security-settings"></a>Säkerhetsinställningar
Dessa tabeller visar detaljerad information för de säkerhetsinställningar som är tillgängliga för Wi-Fi-profiler för Android, iOS och Mac OS X.

### <a name="security-settings-for-android-devices"></a>Säkerhetsinställningar för Android-enheter

  |Inställningsnamn|Mer information|När ska det användas|
|----------------|--------------------|-------------|
|**Säkerhetstyp**|Välj säkerhetsprotokoll för det trådlösa nätverket:<br /><br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **Ingen autentisering (öppet)** om nätverket är oskyddat.|Alltid|
|**EAP-typ**|Välj typen EAP (Extensible Authentication Protocol) som används för att autentisera säkra trådlösa anslutningar:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|Om du har valt säkerhetstypen **WPA-Enterprise/WPA2-Enterprise**.|
|**Välj rotcertifikat för serververifiering**|Markera **Välj**och välj sedan den betrodda rotcertifikatsprofil som du använde för att autentisera anslutningen. Mer information om hur du skapar den betrodda rotcertifikatsprofil finns i [Säker åtkomst till företagsresurser med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).|Om du har valt någon **EAP-typ**.|
|**Autentiseringsmetod**|Välj den autentiseringsmetod som används för anslutningen:<br /><br />-   **Certifikat** för att ange klientcertifikatet<br />-   **Användarnamn och lösenord** för att ange en annan metod för autentisering|**EAP-typen** är **PEAP** eller **EAP-TTLS**.|
|**Välj en annan metod än EAP för autentisering (inre identitet)**|Välj hur du ska autentisera anslutningen:<br /><br />-   **Inga**<br />-   **Okrypterat lösenord (PAP)**<br />-   **CHAP (Challenge Handshake Authentication Protocol)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP Version 2 (MS-CHAP v2)**<br /><br />Vilka alternativ som är tillgängliga beror på vilken EAP-typ du har valt.| **Autentiseringsmetoden** är **användarnamn och lösenord**.|
|**Aktivera identitetssekretess (yttre identitet)**|Ange vilken text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Under autentiseringen skickas den här anonyma identiteten från början. Den verkliga identifieringen skickas i en säker tunnel.|Om **EAP-typen** är **PEAP** eller **EAP-TTLS**.|
|**Välj ett certifikat för klientautentisering (identitetscertifikat)**|Markera **Välj**och välj sedan SCEP-certifikatsprofilen som användes för att autentisera anslutningen. Mer information om hur du skapar SCEP-certifikatsprofil finns i [Säker åtkomst till företagsresurser med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).|Om säkerhetstypen är **WPA-Enterprise/WPA2-Enterprise** och en **EAP-typ** är markerad.|

### <a name="security-settings-for-ios-and-mac-os-x-devices"></a>Säkerhetsinställningar för iOS- och Mac OS X-enheter

  |Inställningsnamn|Mer information|När ska det användas|
|----------------|--------------------|-------------|
|**Säkerhetstyp**|Välj säkerhetsprotokoll för det trådlösa nätverket:<br /><br />-   **WPA-Personal/WPA2-Personal**<br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **WEP**<br />-   **Ingen autentisering (öppet)** om nätverket är oskyddat.|Alltid|
|**EAP-typ**|Välj typen EAP (Extensible Authentication Protocol) som används för att autentisera säkra trådlösa anslutningar:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-AST**<br />-   **LEAP**<br />-   **EAP-SIM**|Om du har valt säkerhetstypen **WPA-Enterprise/WPA2-Enterprise**.|
|**Namn på betrodda servercertifikat**|Markera den betrodda rotcertifikatsprofil som används för att autentisera anslutningen. Mer information om hur du skapar den betrodda rotcertifikatsprofil finns i [Säker åtkomst till företagsresurser med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).|Om du har valt EAP-typen **EAP-TLS**, **PEAP**, **EAP-TTLS** eller **EAP-FAST**.|
|**Använd PAC (Protected Access Credential)**|Välj det här alternativet om du vill etablera en autentiserad tunnel mellan klienten och autentiseringsservern. En befintlig PAC-fil används om det finns en sådan.|Om **EAP-typen** är **EAP-FAST**.|
|**Etablera PAC**|Ställer in PAC-filen på dina enheter.<br /><br />När detta används kan du också välja **Etablera PAC anonymt** för att säkerställa att PAC-filen installeras utan att servern autentiseras.|Om **Använd PAC** är markerat.|
|**Autentiseringsmetod**|Välj den autentiseringsmetod som används för anslutningen:<br /><br /><ul><li>**Certifikat** för att ange klientcertifikatet</li><li>**Användarnamn och lösenord** för att ange någon av följande icke-EAP-metoder för autentisering (även kallat inre identitet):<br /><br /><ul><li>**Inga**</li><li>**Okrypterat lösenord (PAP)**</li><li>**CHAP (Challenge Handshake Authentication Protocol)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP Version 2 (MS-CHAP v2)**</li><li>**EAP-TLS**</li></ul></li></ul>|Om **EAP-typen** är **PEAP** eller **EAP-TTLS**.|
|**Välj ett certifikat för klientautentisering (identitetscertifikat)**|Markera den SCEP-certifikatsprofil som används för att autentisera anslutningen. Mer information om hur du skapar SCEP-certifikatsprofil finns i [Säker åtkomst till företagsresurser med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).|Om säkerhetstypen är **WPA-Enterprise/WPA2-Enterprise** och **EAP-typen** är **EAP-TLS**, **PEAP** eller **EAP-TTLS**.|
|**Aktivera identitetssekretess (yttre identitet)**|Ange vilken text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst.<br /><br />Under autentiseringen skickas den här anonyma identiteten från början. Den verkliga identifieringen skickas i en säker tunnel.|Om **EAP-typen** har angetts till **PEAP**, **EAP-TTLS** eller **EAP-FAST**.|


### <a name="see-also"></a>Se även
Läs om hur du skapar en Wi-Fi-profil med en i förväg delad nyckel i [Wi-Fi-profil med i förväg delad nyckel](pre-shared-key-wi-fi-profile.md).



<!--HONumber=Nov16_HO4-->


