---
title: Skapa WiFi-profile med i förväg delad nyckel – Microsoft Intune – Azure | Micrososft Docs
description: Använd en anpassad profil för att skapa en Wi-Fi-profil med en i förväg delad nyckel och hämta exempel på XML-kod för Android-, Windows- och EAP-baserade Wi-Fi-profiler i Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a7250471e698d32a305755147943311d2150f0b2
ms.sourcegitcommit: a27a9c4cae47be50807aa3c890f0d5c0c023f04a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/29/2018
ms.locfileid: "52618194"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key---intune"></a>Använd en anpassad enhetsprofil för att skapa en Wi-Fi-profil med en i förväg delad nyckel – Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I förväg delade nycklar (PSK) används vanligtvis för att autentisera användare i WiFi-nätverk eller trådlösa nätverk. Med Intune kan du skapa en WiFi-profil med en i förväg delad nyckel. Skapa profilen med funktionen för **anpassade enhetsprofiler** i Intune. I den här artikeln finns även några exempel på hur du skapar en EAP-baserade Wi-Fi-profil.

> [!IMPORTANT]
>- En i förväg delad nyckel med Windows 10 visar ett reparationsfel i Intune. När detta sker tilldelas den trådlösa nätverksprofilen till enheten och profilen fungerar som förväntat.
>- Om du exporterar en trådlös nätverksprofil som innehåller en i förväg delad nyckel, måste filen vara skyddad. Nyckeln är i oformaterad text, så det är ditt ansvar att skydda den.

## <a name="before-you-begin"></a>Innan du börjar

- Det kan vara lättare att kopiera koden från en dator som ansluter till det nätverket, enligt beskrivningen längre ned i den här artikeln.
- Du kan lägga till flera nätverk och nycklar genom att lägga till fler OMA-URI-inställningar.
- För iOS konfigurerar du profilen med Apple Configurator på en Mac-dator.
- PSK kräver en sträng med 64 hexadecimala siffror eller en lösenfras med 8 till 63 utskrivbara ASCII-tecken. Vissa tecken, till exempel asterisk (*), stöds inte.

## <a name="create-a-custom-profile"></a>Skapa en anpassad profil
Du kan skapa en anpassad profil med en i förväg delad nyckel för en Android-, Windows- eller EAP-baserad Wi-Fi-profil. Om du vill skapa profilen med Azure-portalen kan du läsa om att [skapa anpassade enhetsinställningar](custom-settings-configure.md). När du skapar en enhetsprofil väljer du **Anpassad** för din enhetsplattform. Markera inte Wi-Fi-profilen. När du väljer anpassad ska du se till att: 

1. Ange ett namn och en beskrivning av profilen.
2. Lägga till en ny OMA-URI-inställning med följande egenskaper: 

   a. Ange ett namn på den här inställningen för Wi-Fi-nätverk.

   b. (Valfritt) Ange en beskrivning av OMA-URI-inställningen eller lämna den tom.

   c. Ange **Datatyp** till **Sträng**.

   d. **OMA-URI**:

   - **För Android**: ./Vendor/MSFT/WiFi/Profile/SSID/Settings
   - **För Windows**: ./Vendor/MSFT/WiFi/Profile/SSID/WlanXml

     > [!NOTE]
     > Se till att ta med punkttecknet i början.

     SSID är det SSID som du skapar principen för. Ange till exempel `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

   e. **Värdefält** är där du klistrar in XML-koden. Se exemplen i den här artikeln. Uppdatera varje värde så att det matchar dina nätverksinställningar. I avsnittet med kommentarer om koden finns tips.
3. Välj **OK**, spara och tilldela sedan principen.

    > [!NOTE]
    > Den här principen kan bara tilldelas till användargrupper.

Nästa gång varje enhet checkar in tillämpas principen och en Wi-Fi-profil skapas på enheten. Enheten kan därefter ansluta till nätverket automatiskt.

## <a name="android-or-windows-wi-fi-profile-example"></a>Exempel på Wi-Fi-profil för Android eller Windows

Följande exempel på XML-koden för en Wi-Fi-profil för Android eller Windows. Exemplet tillhandahålls för att visa rätt format och ge mer information. Det är bara ett exempel och är inte avsett som en rekommenderad konfiguration för din miljö.

> [!IMPORTANT]
>
> `<protected>false</protected>` måste vara inställt på **falskt**. När det är inställt på **sant** kan det orsaka att enheten förväntar sig ett krypterat lösenord och försöka att dekryptera det, vilket kan resultera i en misslyckad anslutning.
>
>  `<hex>53534944</hex>` bör vara inställt på det hexadecimala värdet `<name><SSID of wifi profile></name>`.
>  Windows 10-enheter kan returnera ett falskt *0x87D1FDE8 Reparationen misslyckades*-felmeddelande, men enheten innehåller ändå profilen.

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

## <a name="eap-based-wi-fi-profile-example"></a>Exempel på EAP-baserad Wi-Fi-profil
Följande exempel innehåller XML-koden för en EAP-baserad Wi-Fi-profil: Exemplet ges för att visa rätt format och ge mer information. Det är bara ett exempel och är inte avsett som en rekommenderad konfiguration för din miljö.


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
Du kan också skapa en XML-fil utifrån en befintlig Wi-Fi-anslutning genom att följa dessa steg: 

1. På en dator som är ansluten till, eller som nyligen har anslutits till det trådlösa nätverket, öppnar du mappen `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}`.

   Det är bäst att använda en dator som inte har för många anslutna trådlösa nätverk. Då kan du behöva leta igenom varje profil för att hitta den som är rätt.

2. Sök igenom XML-filerna för att hitta filen med rätt namn.
3. När du har hittat rätt XML-fil kopierar du och klistrar in XML-koden i fältet **Data** på sidan OMA-URI-inställningar.

## <a name="best-practices"></a>Rekommenderade metoder
- Innan du distribuerar en Wi-Fi-profil med PSK måste du kontrollera att enheten kan ansluta till slutpunkten direkt.

- När du roterar nycklar (lösenord eller lösenfraser) ska du beräkna driftstopp och planera distributioner på lämpligt sätt. Överväg att skicka nya Wi-Fi-profiler under ledig tid. Varna även användarna om att anslutningsmöjligheterna kan påverkas.

- Om du vill garantera en smidig övergång ska du se till att slutanvändarens enhet har en alternativ anslutning till Internet. Slutanvändaren måste till exempel kunna växla tillbaka till gäst-WiFi (eller något annat WiFi-nätverk) eller ha mobilanslutning för att kommunicera med Intune. Den extra anslutningen gör att användaren kan fortsätta att få principuppdateringar när företags-WiFi-profilen uppdateras på enheten.
