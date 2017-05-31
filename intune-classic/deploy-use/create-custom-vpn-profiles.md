---
title: "Anpassade konfigurationer för VPN-profiler i Microsoft Intune | Microsoft Docs"
description: "Använd anpassade konfigurationer för att skapa VPN-profiler i Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 5216730e9736ff4b20abfb19058e82b995d82813
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="custom-configurations-for-microsoft-intune-vpn-profiles"></a>Anpassade konfigurationer för VPN-profiler i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="create-a-custom-configuration"></a>Skapa en anpassad konfiguration
Du kan använda anpassade konfigurationsprinciper i Intune för att skapa VPN-profiler för:

* Enheter som kör Android 4 och senare
* Android for Work-enheter
* Registrerade enheter som kör Windows 8.1 och senare
* Enheter som kör Windows Phone 8.1 och senare
* Registrerade enheter som kör Windows 10 desktop och senare
* Enhet som kör Windows 10 Mobile

Den här typen av princip kan vara praktisk när VPN-standardprinciperna i Intune inte innehåller de inställningar som du vill använda.

## <a name="to-create-a-custom-configuration-policy"></a>Skapa en anpassad konfigurationsprincip:

   1. I [Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Princip** > **Lägg till princip** > *Expandera plattform* > **Anpassad konfiguration** > **Skapa princip**.
   2. Ange ett namn för principen.
   3. För varje URI-inställning som du vill ange väljer du **Lägg till** och anger önskad information. Här är ett exempel:

   ![Dialogrutan för anpassad konfiguration av VPN-profil](./media/Intune_Add_VPN_URI.png)

   4.  När du har angett alla URI-inställningar väljer du **Spara princip** och distribuerar sedan principen.

[Distribuera sedan principen](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy) som vanligt.

## <a name="example-uri-settings"></a>Exempel på URI-inställningar

Dessa inställningar kan användas för att skapa en anpassad konfiguration för VPN i det fiktiva företaget Contoso.
Fullständig information om alla inställningar som du kan använda finns i [VPNv2 CSP](https://msdn.microsoft.com/library/windows/hardware/dn914776.aspx).

**Intern Contoso VPN (IKEv2):**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

**vpn.contoso.com**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

**Ikev2<br />** ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

**SplitTunnel**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

**Eap**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration
``` xml
<EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
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
            <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </PerformServerValidation>
            <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </AcceptServerName>
         </EapType>
      </Eap>
   </Config>
</EapHostConfig>
```
**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal**<br />
Sant

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials**<br />
1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address**<br />
10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize**<br />
8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn**<br />
true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id**<br />
%PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Vid eventuella frågor om hur dessa inställningar ska användas eller för mer information om vad de gör kan kunderna vända sig till [CSP-dokumentationen (Configuration Service Provider)](https://msdn.microsoft.com/library/windows/hardware/dn914776(v=vs.85).aspx).

## <a name="uri-settings-for-android-per-app-vpn-on-pulsesecure"></a>URI-inställningar för Android per-app-VPN på PulseSecure
### <a name="custom-uri-for-package-list"></a>ANPASSAD URI FÖR PAKETLISTA
-  Datatyp = Sträng
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/Name/PackageList
-  Värde = Paketlista avskild med avgränsare.
   - Avgränsare: semikolon (;), kolon (:), kommatecken (,), lodstreck (|)

Exempel:
- com.android.chrome
- com.android.chrome;com.android.browser

### <a name="custom-uri-for-mode-optional"></a>ANPASSAD URI FÖR LÄGE (VALFRITT)
- Datatyp = Sträng
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> Anteckningar
> - Använd samma *namn* som tilldelades till den anpassade profilen
> - Möjliga värden: *GLOBAL*, *WHITELIST*, *BLACKLIST*
> - Anges som standard som *GLOBAL* om ingen PackageList anges (bakåtkompatibilitet med systemomfattande profiler)
> - Anges som standard som *WHITELIST* om en PackageList anges


### <a name="see-also"></a>Se även
[VPN-anslutningar i Microsoft Intune](vpn-connections-in-microsoft-intune.md)

