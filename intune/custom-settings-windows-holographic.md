---
title: "Anpassade inställningar i Microsoft Intune för Windows Holographic for Business-enheter"
titlesuffix: 
description: "Läs om inställningarna som du kan använda i en anpassad Windows Holographic for Business-profil."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 3/6/2018
ms.article: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b95d891d1dfaecbce182fde4a2221255a7e1eb06
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-holographic-for-business"></a>Anpassade enhetsinställningar i Microsoft Intune för enheter som kör Windows Holographic for Business

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Använd Microsoft Intunes **anpassade** profil för Windows Holographic for Business för att distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på enheter. Windows Holographic for Business gör många inställningar för konfigurationstjänstleverantörer tillgängliga. En översikt över CSP finns i [Introduction to configuration service providers (CSPs) for IT pros](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) (Introduktion till konfigurationstjänstleverantörer (CSP:er) för IT-proffs). Specifika CSP:er som stöds av Windows Holographic visas i [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSP:er som stöds i Windows Holographic).

Kom ihåg att om du letar efter en viss inställning så innehåller [enhetsbegränsningsprofilen i Windows Holographic for Business](device-restrictions-windows-holographic.md) många inställningar som är inbyggda och som innebär att du inte behöver ange några anpassade värden.

1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](custom-settings-configure.md).
2. I **Skapa profil** väljer du **Inställningar** för att lägga till en eller flera OMA-URI-inställningar.
3. På sidan **Anpassade OMA-URI-inställningar** klickar du på **Lägg till** för att lägga till ett nytt värde. Du kan också klicka på **Exportera** för att skapa en lista över alla värden som du har konfigurerat i en fil med kommaseparerade värden (CSV).
4. Ange följande information för varje OMA-URI-inställning som du vill lägga till:
    - **Inställningsnamn** – Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Inställningsbeskrivning** – Ange en beskrivning för inställningen.
    - **Datatyp** – Välj bland:
        - **Sträng**
        - **Sträng (XML)**
        - **Datum och tid**
        - **Heltal**
        - **Flyttal**
        - **Boolesk**
    - **OMA-URI (skiftlägeskänslig)** – Ange den OMA-URI som du vill tillhandahålla en inställning för.
    - **Värde** – Ange det värde som ska associeras med den OMA-URI som du har angett.
1. När du är klar går du tillbaka till **Skapa profil** och trycker på **Skapa**.
Profilen skapas och visas i profillistan.

## <a name="recommended-custom-settings"></a>Rekommenderade anpassade inställningar

Följande inställningar är användbara för enheter som kör Windows Holographic for Business:


|Inställningsnamn|OMA-URI|Datatyp  |
|---------|---------|---------|
|[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)|./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Heltal<br>0 – inte tillåten<br>1 – tillåten (standard)|
|[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)|./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Heltal<br>0 – inte tillåten<br>1 – tillåten (standard)|
|[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)|./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Heltal<br>0 – Uppdateringstjänsten är inte tillåten <br>1 – Uppdateringstjänsten är tillåten (standard).|
|[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)|./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|Sträng<br>URL – Enheten söker efter uppdateringar från WSUS-servern med angiven URL.<br>Inte konfigurerad – Enheten söker efter uppdateringar från Microsoft Update.|
|[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)|./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Heltal<br>0 – Inte konfigurerat. Enheten installerar alla tillämpliga uppdateringar.<br>1 – Enheten installerar endast uppdateringar som både är tillämpliga och finns i listan med godkända uppdateringar. Ställ in principen på 1 om IT-avdelningen vill styra distributionen av uppdateringar till enheter, till exempel när testning krävs före distributionen.|
|[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)|./Vendor/MSFT/Update/ApprovedUpdates<br><br>**Viktigt!**<br>Du måste läsa och godkänna uppdateringens användaravtal åt dina slutanvändare. Om detta inte utförs uppstår en juridisk säkerhetsöverträdelse eller ett avtalsbrott.|Nod för godkännanden av uppdateringar och licensavtal åt slutanvändaren.|
[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)|./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br><br>**Viktigt!**<br>I AppLocker CSP-artikeln används undantagna XML-exempel. Om du vill konfigurera inställningarna med anpassade Intune-profiler, måste du använda vanlig XML.|Sträng<br>Mer information finns i artikeln om [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp). 

## <a name="how-to-find-the-policies-you-can-configure"></a>Så här hittar du de principer som du kan konfigurera

Du hittar en fullständig lista över alla konfigurationstjänstleverantörer (CSP:er) som Windows Holographic har stöd för i [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSP:er som stöds i Windows Holographic). Alla inställningar är inte kompatibla med alla versioner av Windows Holographic. I tabellen i Windows-artikeln visas vilka versioner som stöds för varje CSP.

Dessutom stöder Intune inte alla inställningar som anges i artikeln. Om du vill veta om Intune har stöd för den inställning som du vill använda, kan du öppna artikeln för den inställningen. Varje inställningssida visar den åtgärd som stöds. Om du vill arbeta med Intune måste inställningen ha stöd för åtgärderna **Lägg till** eller **Ersätt**.
