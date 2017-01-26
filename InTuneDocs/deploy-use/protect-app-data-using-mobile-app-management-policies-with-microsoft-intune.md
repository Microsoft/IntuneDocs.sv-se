---
title: "Skydda appdata med hanteringsprinciper för mobila appar (MAM) | Microsoft Docs"
description: "I det här avsnittet beskrivs hur du kan använda hanteringsprinciper för mobila appar för att skydda dina företagsdata, förhindra dataförlust och hålla isär privat och arbetsrelaterad information."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: af067236e27a65c52c78107fefdb956ad0fd5aa5
ms.openlocfilehash: b4672b19517f1871a276000c6e8f5d01c0280e35


---

# <a name="protect-app-data-using-mobile-application-management-policies-with-microsoft-intune"></a>Skydda data med hanteringsprinciper för mobilprogram i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="how-you-can-protect-app-data"></a>Hur du kan skydda appdata
Dina anställda använder mobila enheter för både personliga och arbetsrelaterade uppgifter. Samtidigt som du vill se till att de anställda kan vara produktiva vill du även förhindra dataförlust, både avsiktlig och oavsiktlig.  Dessutom kan vill du ha möjlighet att skydda företagets data som de anställda har åtkomst till via enheter som du inte hanterar.

Du kan skydda företaget genom att använda Intunes hanteringsprinciper för mobila appar (MAM). Eftersom Intunes MAM-principer kan användas **oberoende av en hanteringslösning för mobila enheter (MDM)** kan du använda dem för att skydda företagets data både om du registrerar eller inte registrerar enheter i en enhetshanteringslösning. Genom att implementera **principer på appnivå** kan du begränsa åtkomsten till företagsresurser och hålla data inom IT-avdelningens kontroll.

Du kan konfigurera MAM-principer för appar som körs på enheter som:

-   **Har registrerats i Microsoft Intune:** Enheter i den här kategorin är vanligtvis företagsägda enheter.

-   **Har registrerats i en MDM-lösning från tredje part:** Enheter i den här kategorin är vanligtvis företagsägda enheter.

  > [!NOTE]
  > Vi rekommenderar inte att du använder MAM-principer vid hantering av mobila program från tredje part eller säkra behållarlösningar.

-   **Inte har registrerara i någon MDM-lösning:** Enheter i den här kategorin är vanligtvis personalägda enheter som inte hanteras eller som inte har registrerats i Intune eller någon annan MDM-lösning.

> [!IMPORTANT]
> Du kan skapa hanteringsprinciper för mobila appar för Office-mobilappar som ansluter till Office 365-tjänster. MAM-principer stöds inte för appar som ansluter till lokala Exchange-, Skype för företag- eller SharePoint-tjänster.

## <a name="benefits-of-using-mam-policies"></a>Fördelar med att använda MAM-principer

-   **De bidrar till att skydda dina företagsdata på appnivå.** Eftersom mobilappshantering inte kräver enhetshantering kan du skydda företagets data på både hanterade och ohanterade enheter. Eftersom hanteringen är uppbyggd kring användaridentiteten krävs ingen enhetshantering.

-   **Användarproduktiviteten påverkas inte och principerna tillämpas inte när appen används i en privat kontext.** Principerna tillämpas endast i arbetssammanhang, vilket ger dig möjlighet att skydda företagets data utan att röra personliga data.

Det finns ytterligare fördelar med att använda MDM med MAM-principer. Företag kan använda MAM med och utan MDM på samma gång. En medarbetare kan t.ex. använda en såväl en företagsutfärdad telefon som en personlig surfplatta. I det här fallet registreras företagets telefon i MDM och skyddas av MAM-principer, och den personliga enheten skyddas endast av MAM-principer.

- **MDM ser till att enheten är skyddad.** Du kan till exempel behöva en PIN-kod för att få åtkomst till enheten, eller så kan du distribuera hanterade appar till enheten. Du kan också distribuera appar till enheter via MDM-lösningen, vilket ger dig större kontroll över apphanteringen.

- **MAM-principer ser till att det finns skydd på appnivå.** Du kan t.ex. ha en princip som kräver en PIN-kod för att öppna en app i arbetssammanhang, som förhindrar data från att delas mellan appar och som förhindrar att företagets appdata sparas på en personlig lagringsplats.

## <a name="devices-that-support-mam"></a>Enheter som stöder MAM
MAM-principer stöds för närvarande på:
-   iOS 8.1 eller senare
-   Android 4 eller senare

>[!NOTE]
>Windows-enheter stöds inte i MAM utan registreringsscenario. När du registrerar Windows 10-enheter med Intune kan du använda Windows Information Protection, som innehåller liknande funktioner. Mer information finns i avsnittet om hur du [skyddar dina företagsdata med hjälp av Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).


##  <a name="how-mam-policies-protect-app-data"></a>Hur MAM-principer skyddar appdata

###  <a name="apps-without-mam-policies"></a>Appar utan MAM-principer

![Bild som visar hur data kan flyttas fritt mellan appar när inga MAM-principer tillämpas](../media/Apps_without_MAM_policies.png)

När du använder appar utan begränsningar kan företagsrelaterade och personliga data blandas. Företagsdata skulle kunna hamna på t.ex. personliga lagringsplatser eller överföras till appar som du inte har kontroll över, vilket kan leda till dataförluster. Pilarna i diagrammet visar hur data flyttas utan begränsningar mellan appar (företagsdata och personliga data) och till lagringsplatser.

### <a name="data-protection-with-mam-policies"></a>Dataskydd med MAM-principer

![Bild som visar hur företagsdata skyddas när MAM-principer tillämpas](../media/Apps_with_mobile_app_policies.png)

Du kan använda MAM-principer för att förhindra att företagets data sparas till enhetens lokala lagring och begränsa dataflyttningen till andra appar som inte skyddas av MAM-principer. Exempel på inställningar för MAM-principer är:
- Dataflyttningsprinciper som **Förhindra spara som** och **Begränsa klipp ut, kopiera och klistra in**.
- Åtkomstprincipsinställningar som **Kräv enkel PIN för åtkomst** och **Blockera hanterade appar från att köras på jailbrokade eller rotade enheter**.

### <a name="data-protection-with-mam-policies-on-devices-that-are-managed-by-a-mdm-solution"></a>Dataskydd med MAM-principer på enheter som hanteras av en MDM-lösning

![Bild som visar hur MAM-principer fungerar på BYOD-enheter](../media/MAM_BYOD_November.png)

**För enheter som har registrerats i en MDM-lösning**: Det föregående diagrammet visar vilka skyddsnivåer som MDM- och MAM-principerna kan erbjuda tillsammans.

MDM-lösningen:

-   Registrerar enheten.

-   Distribuerar appar till enheten.

-   Tillhandahåller fortlöpande enhetskompatibilitet och hantering.

**MAM-principer ger extra värde eftersom de:**

-   Bidrar till att skydda företagsdata från att läckas till konsumentappar och tjänster.

-   Använder begränsningar (spara som, urklipp, PIN-kod osv) för mobilappar.

-   Rensar företagsdata från appar utan att ta bort dessa appar från enheten.


### <a name="data-protection-with-mam-policies-for-devices-without-enrollment"></a>Dataskydd med MAM-principer för enheter utan registrering

![Bild som visar hur MAM-principer fungerar på hanterade enheter](../media/MAM_ManagedDevices_November.png)

Det föregående diagrammet visar hur dataskyddsprinciper fungerar på appnivå utan MDM.

För BYOD-enheter som inte har registrerats i någon MDM-lösning kan MAM-principer skydda företagets data på appnivå.

Det finns dock vissa begränsningar som du bör känna till:

-   Du kan inte distribuera appar till enheten. Användaren måste hämta apparna från butiken.

-   Du kan inte etablera certifikatprofiler på enheterna.

-   Du kan inte konfigurera företagets Wi-Fi- och VPN-inställningar på de här enheterna.


## <a name="multi-identity"></a>Flera identiteter

Med appar som stöder flera identiteter kan du använda olika konton (arbetskonton och privata konton) för att få åtkomst till samma appar, medan MAM-principerna enbart tillämpas när apparna används i ett arbetssammanhang.  

Om en användare t.ex. startar appen OneDrive med sitt arbetskonto kan hen inte flytta filerna till en personlig lagringsplats. Om användaren däremot använder OneDrive med ett personligt konto kan hen kopiera och flytta data från sin personliga OneDrive utan begränsningar.  

Alla mobila Office-appar stöder multiidentitetsåtkomst.

##  <a name="next-steps"></a>Nästa steg
- [Förbered dig för att konfigurera hanteringsprinciper för mobilappar](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

- [Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Jan17_HO4-->


