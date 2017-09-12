---
title: "Skapa en Wi-Fi-profil med en i förväg delad nyckel"
titleSuffix: Azure portal
description: "Använd en anpassad Intune-profil för att skapa en trådlös profil med en i förväg delad nyckel.”"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c524acc403d6a1c041aa0dcea0948c2707202e03
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="use-a-microsoft-intune-custom-device-profile-to-create-a-wi-fi-profile-with-a-pre-shared-key"></a>Använd en anpassad enhetsprofil för Microsoft Intune för att skapa en Wi-Fi-profil med en i förväg delad nyckel
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Så här använder du Intunes **anpassade enhetsprofiler** för att skapa en trådlös profil med en i förväg delad nyckel. Det här avsnittet innehåller även ett exempel på hur du skapar en EAP-baserad Wi-Fi-profil.

> [!NOTE]
-   Det kan vara lättare att kopiera koden från en dator som ansluter till det nätverket, enligt beskrivningen nedan.
- För Android kan du även använda den här [PSK-generatorn för Android](http://johnathonb.com/2015/05/intune-android-pre-shared-key-generator/) som tillhandahålls av Johnathon Biersack.
-   Du kan lägga till flera nätverk och nycklar genom att lägga till fler OMA-URI-inställningar.
-  För iOS konfigurerar du profilen med Apple Configurator på en Mac-dator. Du kan också använda den här [PSK-generatorn för mobil konfiguration för iOS](http://johnathonb.com/2015/05/intune-ios-psk-mobile-config-generator/) som tillhandahålls av Johnathon Biersack.


1.  Om du vill skapa en trådlös profil med en i förväg delad nyckel för Android eller Windows eller en EAP-baserad trådlös profil, väljer du **Anpassad** för den enhetsplattformen när du skapar en enhetsprincip, i stället för en trådlös profil.

2.  Ange ett namn och en beskrivning.
3.  Lägg till en ny OMA-URI-inställning:

   a.   Ange ett namn på den här inställningen för Wi-Fi-nätverk.

   b.   Ange en beskrivning av OMA-URI-inställningen eller lämna tomt.

   c.   **Datatyp**: Ange som **Sträng**.

   d.   **OMA-URI**:

    - **För Android**: ./Vendor/MSFT/WiFi/Profile/<SSID>/Settings
    - **För Windows**: ./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml

    > [!NOTE]
Se till att ta med punkttecknet i början.

    SSID är det SSID som du skapar principen för. Till exempel `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`

  e. **Värdefält** är där du klistrar in XML-koden. Här är ett exempel. Varje värde ska anpassas till nätverksinställningarna. Se avsnittet med kommentarer om koden för tips.
4. Välj **OK**, spara och tilldela sedan principen.

    > [!NOTE]
    > Den här principen kan bara tilldelas till användargrupper.

Nästa gång varje enhet checkar in tillämpas principen och en Wi-Fi-profil skapas på enheten. Enheten kan ansluta till nätverket automatiskt.

## <a name="android-or-windows-wi-fi-profile"></a>Wi-Fi-profil för Android eller Windows

Här är ett exempel på XML-koden för en Wi-Fi-profil för Android eller Windows:

> [!IMPORTANT]
>
> `<protected>false</protected>` måste vara inställt på **falskt** eftersom **sant** kan göra att enheten förväntar sig ett krypterat lösenord och därför försöker dekryptera det, vilket kan resultera i en misslyckad anslutning.
>
>  `<hex>53534944</hex>` bör vara inställt på det hexadecimala värdet `<name><SSID of wifi profile></name>`.
>  Windows 10-enheter kan returnera ett falskt *0x87D1FDE8 Reparationen misslyckades*-felmeddelande, men kommer ändå att ha etablerats med profilen.

```
<!--
<Name of wifi profile> = Name of profile
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Password to connect to the network
x>53534944</hex> should be set to the hexadecimal value of <name><SSID of wifi profile></name>
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
        <keyType>networkKey</keyType>
        <protected>false</protected>
        <keyMaterial>MyPassword</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

## <a name="eap-based-wi-fi-profile"></a>EAP-baserad Wi-Fi-profil
Här är ett exempel på XML-koden för en EAP-baserad Wi-Fi-profil:

```
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
Du kan också skapa en XML-fil utifrån en befintlig Wi-Fi-anslutning:
1. På en dator som är ansluten till eller nyligen har anslutit till det trådlösa nätverket öppnar du följande mapp: C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}.

    Det är bäst att använda en dator som inte har anslutit till många trådlösa nätverk, eftersom du måste söka igenom alla profiler för att hitta rätt.
3.     Sök igenom XML-filerna för att hitta den med rätt namn.
4.     När du har hittat rätt XML-fil kopierar du och klistrar in XML-koden i fältet Data på sidan OMA-URI-inställningar.
