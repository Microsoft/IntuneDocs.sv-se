---
title: Skapa WiFi-profil med i förväg delad nyckel – Microsoft Intune – Azure | Microsoft Docs
description: Använd en anpassad profil för att skapa en Wi-Fi-profil med en i förväg delad nyckel och hämta exempel på XML-kod för Android-, Windows- och EAP-baserade Wi-Fi-profiler i Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9b56ba1515608afb6c2a0d151f5412711d49e57
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886713"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key-in-intune"></a>Använd en anpassad enhetsprofil för att skapa en Wi-Fi-profil med en i förväg delad nyckel i Intune



I förväg delade nycklar (PSK) används vanligtvis för att autentisera användare i WiFi-nätverk eller trådlösa nätverk. Med Intune kan du skapa en WiFi-profil med en i förväg delad nyckel. Skapa profilen med funktionen för **anpassade enhetsprofiler** i Intune. I den här artikeln finns även några exempel på hur du skapar en EAP-baserade Wi-Fi-profil.

Den här funktionen stöder:

- Android-enhetsadministratör
- Windows
- EAP-baserad Wi-Fi

> [!IMPORTANT]
> - En i förväg delad nyckel med Windows 10 visar ett reparationsfel i Intune. När detta sker tilldelas den trådlösa nätverksprofilen till enheten och profilen fungerar som förväntat.
> - Om du exporterar en trådlös nätverksprofil som innehåller en i förväg delad nyckel, måste filen vara skyddad. Nyckeln är i oformaterad text, så det är ditt ansvar att skydda den.

## <a name="before-you-begin"></a>Innan du börjar

- Det kan vara lättare att kopiera koden från en dator som ansluter till det nätverket, enligt beskrivningen längre ned i den här artikeln.
- Du kan lägga till flera nätverk och nycklar genom att lägga till fler OMA-URI-inställningar.
- För iOS konfigurerar du profilen med Apple Configurator på en Mac-dator.
- PSK kräver en sträng med 64 hexadecimala siffror eller en lösenfras med 8 till 63 utskrivbara ASCII-tecken. Vissa tecken, till exempel asterisk (*), stöds inte.

## <a name="create-a-custom-profile"></a>Skapa en anpassad profil

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på principen. Namnge dina principer så att du enkelt kan identifiera dem senare. Ett exempel på ett bra principnamn är **Custom OMA-URI Wi-Fi profile settings for Android devices** (Anpassade inställningar för OMA-URI Wi-Fi-profil för Android-enheter).
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj din plattform.
    - **Profiltyp**: Välj **Anpassad**.

4. I **Inställningar** väljer du **Lägg till**. Lägg till en ny OMA-URI-inställning med följande egenskaper:

    1. **Namn**: Ange ett namn för OMA-URI-inställningen.
    2. **Beskrivning**: Ange en beskrivning för OMA-URI-inställningen. Denna inställning är valfri, men rekommenderas.
    3. **OMA-URI**: Ange ett av följande alternativ:

        - **För Android**: `./Vendor/MSFT/WiFi/Profile/SSID/Settings`
        - **För Windows**: `./Vendor/MSFT/WiFi/Profile/SSID/WlanXml`

        > [!NOTE]
        > Se till att ta med punkttecknet i början.

        SSID är det SSID som du skapar principen för. Om Wi-Fi till exempel heter `Hotspot-1` anger du `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

    4. **Datatyp**: Välj **Sträng**.

    5. **Värde**: Klistra in XML-koden. Se [exemplen](#android-or-windows-wi-fi-profile-example) i den här artikeln. Uppdatera varje värde så att det matchar dina nätverksinställningar. I avsnittet med kommentarer om koden finns tips.

5. När du är klar väljer du **OK** > **Skapa** för att spara dina ändringar.

Din profil visas i profillistan. [Tilldela den här profilen](../device-profile-assign.md) till dina användargrupper. Den här principen kan bara tilldelas till användargrupper.

Nästa gång varje enhet checkar in tillämpas principen och en Wi-Fi-profil skapas på enheten. Enheten kan därefter ansluta till nätverket automatiskt.

## <a name="android-or-windows-wi-fi-profile-example"></a>Exempel på Wi-Fi-profil för Android eller Windows

Följande exempel på XML-koden för en Wi-Fi-profil för Android eller Windows. Exemplet tillhandahålls för att visa rätt format och ge mer information. Det är bara ett exempel och är inte avsett som en rekommenderad konfiguration för din miljö.

### <a name="what-you-need-to-know"></a>Vad du behöver veta

- `<protected>false</protected>` måste vara inställt på **falskt**. När det är inställt på **sant** kan det orsaka att enheten förväntar sig ett krypterat lösenord och försöka att dekryptera det, vilket kan resultera i en misslyckad anslutning.

- `<hex>53534944</hex>` bör vara inställt på det hexadecimala värdet `<name><SSID of wifi profile></name>`. Windows 10-enheter kan returnera ett falskt `x87D1FDE8 Remediation failed`-felmeddelande, men enheten innehåller ändå profilen.

- XML innehåller specialtecken, till exempel `&` (et-tecken). Användning av specialtecken kan förhindra att XML-koden fungerar som förväntat. 

### <a name="example"></a>Exempel

``` xml
<!--
<hex>53534944</hex> = The hexadecimal value of <name><SSID of wifi profile></name>
<Name of wifi profile> = Name of profile shown to users. It could be <name>Your Company's Network</name>.
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped. It could be <name>Your Company's Network</name>.
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network, such as AES.
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Plain text of the password to connect to the network
-->

<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

### <a name="eap-based-wi-fi-profile-example"></a>Exempel på EAP-baserad Wi-Fi-profil
Följande exempel på XML-koden för en EAP-baserad Wi-Fi-profil: Exemplet tillhandahålls för att visa rätt format och ge mer information. Det är bara ett exempel och är inte avsett som en rekommenderad konfiguration för din miljö.


```xml
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>Skapa XML-filen utifrån en befintlig Wi-Fi-anslutning

Du kan också skapa en XML-fil utifrån en befintlig Wi-Fi-anslutning. Använd följande steg på en Windows-dator:

1. Skapa en lokal mapp för de exporterade trådlösa profilerna, till exempel c:\WiFi.
2. Öppna en kommandotolk som administratör (Högerklicka på `cmd` > **Kör som administratör**).
3. Kör `netsh wlan show profiles`. Namnen på alla profilerna visas i listan.
4. Kör `netsh wlan export profile name="YourProfileName" folder=c:\Wifi`. Det här kommandot skapar en fil med namnet `Wi-Fi-YourProfileName.xml` i c:\Wifi.

    - Om du exporterar en profil för trådlöst nätverk som innehåller en i förväg delad nyckel måste du lägga till `key=clear` i kommandot:
  
        `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

        `key=clear` exporterar nyckeln i klartext, vilket krävs för att kunna använda profilen.

När du har XML-filen kopierar du och klistrar in XML-syntaxen i OMA-URI-inställningar > **Datatyp**. [Skapa en anpassad profil](#create-a-custom-profile) (i den här artikeln) visar stegen.

> [!TIP]
> `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}` innehåller även alla profiler i XML-format.

## <a name="best-practices"></a>Rekommenderade metoder

- Innan du distribuerar en Wi-Fi-profil med PSK måste du kontrollera att enheten kan ansluta till slutpunkten direkt.

- När du roterar nycklar (lösenord eller lösenfraser) ska du beräkna driftstopp och planera distributioner. Överväg att skicka nya Wi-Fi-profiler under ledig tid. Varna även användarna om att anslutningsmöjligheterna kan påverkas.

- Om du vill garantera en smidig övergång ska du se till att slutanvändarens enhet har en alternativ anslutning till Internet. Slutanvändaren måste till exempel kunna växla tillbaka till gäst-WiFi (eller något annat WiFi-nätverk) eller ha mobilanslutning för att kommunicera med Intune. Den extra anslutningen gör att användaren kan fortsätta att få principuppdateringar när företags-WiFi-profilen uppdateras på enheten.

## <a name="next-steps"></a>Nästa steg

Se till att du [tilldelar profilen](device-profile-assign.md) och [övervakar](device-profile-monitor.md) dess status.
