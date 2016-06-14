---
# required metadata

title: Anpassade konfigurationer för VPN-profiler | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Anpassade konfigurationer för VPN-profiler

## Skapa en anpassad konfiguration
Du kan använda anpassade konfigurationer för att skapa VPN-profiler i Intune. Skapa en anpassad konfiguration:

   1. Gå till Intune-administratörskonsolen och välj **Princip** -> **Lägg till princip** -> *<Expand platform>* -> **Anpassad konfiguration** -> **Skapa princip**.
   2. Ange ett namn för principen.
   3. För varje URI-inställning klickar du på **Lägg till** och anger önskad information. Här är ett exempel:

   ![Dialogrutan för anpassad konfiguration av VPN-profil](./media/Intune_Add_VPN_URI.png)

   4.  När du har angett alla URI-inställningar klickar du på **Spara princip** och distribuerar sedan principen.

## Distribuera en konfigurationsprincip

1.  Välj den princip på arbetsytan **Princip** som du vill distribuera och klicka sedan på **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** :

    -   **Om du vill distribuera principen** markerar du en eller flera grupper som du vill distribuera principen till och klickar sedan på **Lägg till** &gt; **OK**.

    -   **Om du vill stänga dialogrutan utan att distribuera den** – Klicka på **Avbryt**.

När du väljer en distribuerad princip visas ytterligare information om distributionen i den nedre delen av principlistan.

##Exempel på URI-inställningar för en anpassad konfiguration av VPN-profil Följande är exempelposter för URI-värden för att skapa en anpassad konfiguration för VPN i det fiktiva företaget Contoso. Mer information, t.ex. om datatypen för varje post, finns i [VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx)

Native Contoso VPN (IKEv2): ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

vpn.contoso.com ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2 ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

Eap ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration &lt;EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;EapMethod&gt;&lt;Type xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;13&lt;/Type&gt;&lt;VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"&gt;&lt;Type&gt;13&lt;/Type&gt;&lt;EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt;&lt;PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;

**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal** Sant

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials** 1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address** 10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize** 8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn** sant

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id** %PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Vid eventuella frågor om hur dessa inställningar ska användas eller för mer information om vad de utför kan kunden vända sig till CSP-dokumentationen: https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx

## URI-inställningar för Android per-app-VPN på PulseSecure
### ANPASSAD URI FÖR PAKETLISTA 
-  Datatyp = Sträng
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/<Name>/PackageList 
-  Värde = Paketlista avskild med avgränsare.
   - Avgränsare: semikolon (;), kolon (:), kommatecken (,), lodstreck (|)

Exempel: 
- com.android.chrome
- com.android.chrome;com.android.browser

### ANPASSAD URI FÖR LÄGE (VALFRITT)
- Datatyp = Sträng
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode 

> Anteckningar
> - Använd samma *namn* som tilldelades till den anpassade profilen
> - Möjliga värden: *GLOBAL*, *WHITELIST*, *BLACKLIST*
> - Anges som standard som *GLOBAL* om ingen PackageList anges (bakåtkompatibilitet med systemomfattande profiler)
> - Anges som standard som *WHITELIST* om en PackageList anges


### Se även
(VPN-anslutningar i Microsoft Intune)[vpn-connections-in-microsoft-intune.md]


<!--HONumber=May16_HO2-->


