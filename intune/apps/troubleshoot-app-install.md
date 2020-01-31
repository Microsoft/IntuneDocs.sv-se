---
title: Felsöka appinstallationsproblem
titleSuffix: Microsoft Intune
description: Använd felsökningsfönstret i Microsoft Intune om du vill felsöka appinstallationsproblem.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be66f99006b06dce9f9bfe21eafa9f2be302e7b9
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540987"
---
# <a name="troubleshoot-app-installation-issues"></a>Felsöka appinstallationsproblem

På Microsoft Intune MDM-hanterade enheter kan ibland appinstallationer misslyckas. När dessa appinstallationer misslyckas, kan det vara en utmaning att förstå felorsaken eller felsöka problemet. Microsoft Intune tillhandahåller information om appinstallationsfel som tillåter supportansvariga och Intune-administratörer att visa information som underlättar användarnas begäran om hjälp. Felsökningsfönstret i Intune ger information om felet, inklusive information om hanterade appar på en användares enhet. Information om en apps livscykel från början till slut ges under varje enskild enhet i fönstret **Hanterade appar**. Du kan visa installationsrelaterad information, t.ex. när appen har skapats, ändrats, inriktats och levereras till en enhet. 

> [!NOTE]
> Specifik information om felkoder vid appinstallation finns i [Referens för fel vid Intune-appinstallation](~/apps/app-install-error-codes.md).

## <a name="app-troubleshooting-details"></a>Information om felsökning av appar

Intune tillhandahåller appfelsökningsinformation baserad på de appar som installerats på en viss användares enhet.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Välj **Felsök + support**.
4. Klicka på **Välj användare** om du vill välja en användare att felsöka. Fönstret **Välj användare** visas.
5. Välj en användare genom att skriva namnet eller e-postadressen. Klicka på **Nästa** längst ner i fönstret. Felsökningsinformationen för användaren visas i fönstret **Felsökning**. 
6. Välj den enhet som du vill felsöka i listan **Enheter**.
    ![Felsökningsfönstret i Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. Välj **Hanterade appar** i det valda enhetsfönstret. En lista över hanterade appar visas.
    ![Information om en specifik enhet som hanteras av Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. Välj en app i listan där **Installationsstatus** indikerar ett fel.
    ![En vald app som visar information om installationsfel.](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > Samma app kan tilldelas till flera grupper, men med olika avsedda åtgärder (avsikter) för appen. En löst avsikt för en app kan t.ex. visa **Exkluderad** om appen har exkluderats för en användare under apptilldelningen. Mer information finns i [Lösa konflikter mellan appavsikter](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Om ett installationsfel inträffar för en app som krävs kan varken du eller supporten synkronisera enheten och försöka installera appen igen.

Problemet indikeras i informationen om appinstallationsfel. Du kan använda den här informationen för att komma fram till vilket som är det bästa sättet att lösa problemet på. Mer information om felsökning av problem med appinstallation finns i [Fel vid installation av Android-appar](app-install-error-codes.md#android-app-installation-errors) och [Fel vid installation av iOS-appar](app-install-error-codes.md#ios-app-installation-errors).

> [!Note]  
> Du kan också få åtkomst till **felsökningsfönstret** genom att gå till: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>Appinstallation som riktas till användargrupp når inte enheten
Överväg följande åtgärder när det är problem med installation av appar:
- Om appen inte visas i Företagsportal ser du till att appen distribueras med avsikten **Tillgänglig** och att användaren kommer åt Företagsportal med den enhetstyp som stöds av appen.
- För Windows BYOD-enheter måste användaren lägga till ett arbetskonto till enheten.
- Kontrollera om användaren är över AAD-enhetsgränsen:
  1. Gå till [Azure Active Directory-enhetsinställningarna](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId).
  2. Notera det värde som angetts för **Maximalt antal enheter per användare**.
  3. Gå till [Azure Active Directory-användare](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers).
  4. Välj den berörda användaren och klicka på **Enheter**.
  5. Om användaren är över den angivna gränsen tar du bort eventuella inaktuella poster som inte längre behövs.
- För iOS DEP-enheter kontrollerar du att användaren anges som **Registrerad av användare** i Intune-fönstret för enhetsöversikt. Om NA visas distribuerar du en konfigurationsprincip för Intune-företagsportalen. Mer information finns i [Konfigurera Företagsportalappen](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Felsökning av Win32-appinstallationen

Välj Win32-appen som distribuerats med Intune-hanteringstillägget. Du kan välja alternativet **Samla in loggar** om installationen av Win32-appen misslyckas. 

> [!IMPORTANT]
> Alternativet **Samla in loggar** är inte aktiverat om Win32-appen har installerats korrekt på enheten.<p>Innan du kan samla in logginformation för Win32-appen måste Intune-hanteringstillägget installeras på Windows-klienten. Intune-hanteringstillägget installeras när ett PowerShell-skript eller en Win32-app distribueras till en användare eller en enhetssäkerhetsgrupp. Mer information finns i avsnittet med [förhandskrav för Intune-hanteringstillägget](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Samla in loggfil

Om du vill samla in installationsloggarna för Win32-appen följer du stegen i avsnittet med [information om felsökning av appar](troubleshoot-app-install.md#app-troubleshooting-details). Fortsätt sedan med följande steg:

1. Klicka på alternativet **Samla in loggar** i fönstret **Installationsinformation**.

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. Ange sökvägar med loggfilnamn för att börja samla in loggfiler och klicka på **OK**.

    > [!NOTE]
    > Logginsamlingen tar mindre än två timmar. Följande filtyper stöds: *.log, .txt, .dmp, .cab, .zip, .xml, .evtx och .evtl*. Högst 25 sökvägar är tillåtna.

3. När loggfilerna har samlats in kan du välja länken **loggar** för att ladda ned loggfilerna.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Ett meddelande visas som anger att loggarna för apparna har samlats in.

#### <a name="win32-log-collection-requirements"></a>Krav för Win32-logginsamling

Det finns särskilda krav som du måste följa för att samla in loggfiler:

- Du måste ange den fullständiga sökvägen. 
- Du kan ange miljövariabler för logginsamling, till exempel följande:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Endast exakta filnamnstillägg är tillåtna, till exempel:<br>
  *.log,.txt,.dmp,.cab,.zip,.xml*
- Du kan ladda upp loggfiler på högst 60 MB eller högst 25 filer, beroende på vilken gräns som nås först. 
- Du kan samla in Win32-appinstallationsloggar för appar som uppfyller apptilldelningsavsikten Krävs, Tillgänglig eller Avinstallera.
- Lagrade loggar krypteras för att skydda personligt identifierbar information som finns i loggarna.
- När du öppnar supportbegäranden om Win32-appfel bifogar du associerade felloggar genom att följa stegen ovan.

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Felsöka appar från Microsoft Store

Informationen i avsnittet [Troubleshooting packaging, deployment, and query of Windows Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (Felsöka paketering, distribution och frågor för Windows Store-appar) hjälper dig att felsöka vanliga problem som kan uppstå när du installerar appar från Microsoft Store, oavsett om du gör det med Intune eller på annat sätt.

## <a name="app-troubleshooting-resources"></a>Appfelsökningsresurser
- [Distribuera Visio och Project som en del av din Office Pro Plus-distribution](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Vidta åtgärder för att säkerställa att MSfB-appar distribueras via Intune-installation i Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Felsöka MSI-appdistributioner i Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Metodtips för programvarudistribution till den klassiska Windows PC-agenten i Intune](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Nästa steg

- Ytterligare information om felsökning av Intune information finns i [Använd felsökningsportalen för att hjälpa företagets användare](../fundamentals/help-desk-operators.md). 
- Lär dig om kända problem i Microsoft Intune. Mer information finns i [Kundframgång för Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- Behöver du mer hjälp? Se [Ta reda på hur du kan få support för Microsoft Intune](../fundamentals/get-support.md).
