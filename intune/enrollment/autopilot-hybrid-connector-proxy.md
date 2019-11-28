---
title: Konfigurera proxyinställningar för Intune-anslutningsappen för Active Directory
description: Beskriver hur du konfigurerar Intune-anslutningsappen för Active Directory till att fungera med befintliga lokala proxyservrar.
keywords: ''
author: master11218
ms.author: erikje
manager: dougeby
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a1af2e7c8aff281e04e92344b3e2c762bb23e0a
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465763"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>Arbeta med befintliga lokala proxyservrar

Den här artikeln förklarar hur du konfigurerar Intune-anslutningsappen för Active Directory till att fungera med utgående proxyservrar. Den är avsedd för kunder med nätverksmiljöer som har befintliga proxyservrar.

Mer information om hur anslutningsappar fungerar finns i avsnittet om att [förstå anslutningsappar för Azure AD-programproxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors).

## <a name="bypass-outbound-proxies"></a>Kringgå utgående proxyservrar

Anslutningsappar har underliggande OS-komponenter som gör att utgående begäranden. De här komponenterna försöker automatiskt hitta en proxyserver i nätverket med hjälp av Web Proxy Auto-Discovery (WPAD).

OS-komponenterna försöker hitta en proxyserver genom att utföra en DNS-sökning efter wpad.domänsuffix. Om sökningen matchar i DNS görs en HTTP-begäran till IP-adressen för wpad.dat. Den här begäran blir proxykonfigurationsskriptet i din miljö. Anslutningsappen använder det här skriptet för att välja en utgående proxyserver. Anslutningsappens trafik kommer dock kanske inte igenom på grund av ytterligare konfigurationsinställningar som behövs på proxyn.

Du kan konfigurera anslutningsappen till att kringgå den lokala proxyn för att säkerställa att den använder direktanslutning till Azure-tjänsterna. Vi rekommenderar den här metoden förutsatt att din nätverksprincip tillåter det, eftersom det innebär att det blir en färre konfiguration att underhålla.

Om du vill inaktivera utgående proxyanvändning för anslutningsappen redigerar du filen :\Program Files\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config och lägger till proxyadressen och proxyporten i det avsnitt som visas i det här kodexemplet:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

För att säkerställa att Connector Updater-tjänsten kringgår proxyn gör du en liknande ändring i C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

Se till att göra kopior av originalfilerna i fall du behöver återställa till de standardmässiga .config-filerna.

När konfigurationsfilerna har ändrats behöver du starta om Intune-anslutningsapptjänsten. 

1. Öppna **services.msc**.
2. Leta upp och välj **Intune ODJConnector-tjänsten**.
3. Välj **Starta om**.

![Skärmbild av omstart av tjänsten](./media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>Nästa steg

[Hantera dina enheter](../remote-actions/device-management.md)
