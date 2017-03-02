---
title: "Så här skapar du anpassade VPN-profiler med Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Använd anpassade konfigurationer för att skapa VPN-profiler i Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 132844bb1d1119390b7f55cca58cecbd5b8ee90a
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Så här skapar du anpassade VPN-profiler i Microsoft Intune

## <a name="create-a-custom-configuration"></a>Skapa en anpassad konfiguration
Du kan använda anpassade konfigurationsprinciper i Intune för att skapa VPN-profiler för:

* Enheter som kör Android 4 och senare
* Registrerade enheter som kör Windows 8.1 och senare
* Enheter som kör Windows Phone 8.1 och senare
* Registrerade enheter som kör Windows 10 desktop och senare 
* Enheter som kör Windows 10 Mobile

Den här typen av princip kan vara praktisk när VPN-standardprinciperna i Intune inte innehåller de inställningar som du vill använda.

## <a name="to-create-a-custom-configuration-policy"></a>Skapa en anpassad konfigurationsprincip:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
4. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
5. Välj **Skapa profil** på profilbladet.
6. Ange **Namn** och **Beskrivning** för VPN-profilen på bladet **Skapa profil**.
7. Välj den enhetsplattform på vilken du vill tillämpa VPN-inställningarna från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för anpassade enhetsinställningar:
    - **Android**
    - **iOS** (konfigureras med en fil som du har exporterat från Apple Configurator).
    - **macOS** (konfigureras med en fil som du har exporterat från Apple Configurator).
    - **Windows Phone 8.1**
    - **Windows 10 och senare**
6. I listrutan **Profil**typ väljer du **Anpassad**.
7. På bladet **Anpassade OMA-URI-inställningar** väljer du för varje URI-inställning som du vill ange **Lägg till**, anger den begärda informationen och väljer sedan **OK**. Här är ett exempel:

   ![Dialogrutan för anpassad konfiguration av VPN-profil](./media/Intune_Add_VPN_URI.png)

4.  När du har angett alla URI-inställningar som du behöver väljer du **OK**, och klickar sedan på bladet **Skapa profil** och väljer **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](how-to-assign-device-profiles.md).

## <a name="example-uri-settings"></a>Exempel på URI-inställningar

Dessa inställningar kan användas för att skapa en anpassad konfiguration för VPN i det fiktiva företaget Contoso.
Fullständig information om alla inställningar som du kan använda finns i [VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx).

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

Kunder som har frågor om hur dessa inställningar ska användas eller som vill veta mer om vad inställningarna gör, kan läsa CSP-dokumentationen (Configuration Service Provider): https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx.

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




