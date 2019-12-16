---
title: Installera Skydd mot mobilhot på din mobila enhet
description: Lär dig installera Skydd mot mobilhot på din mobila enhet.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7f395a9cedc72a8184cfe3e29d6fcd3117a1473d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72980364"
---
# <a name="install-mobile-threat-defense"></a>Installera Skydd mot mobilhot   

Som en del av din organisations säkerhets krav kan du behöva installera en MTD-leverantörs app (Mobile Threat försvar). Den här typen av app identifierar och varnar dig för hot på enheten, till exempel misstänkta appar, nätverk eller OS-sårbarheter.  

Om du inte har den nödvändiga MTD-appen blockeras du från att logga in på skyddade appar med ditt arbets-eller skol konto. I den här artikeln får du lära dig [hur du installerar en MTD-app](set-up-mobile-threat-defense.md#install-app) för att bli avblockerad.  

Det finns flera olika MTD-leverantörs appar som kan installeras; din organisation meddelar dig vilken som ska användas. 


## <a name="information-your-organization-can-see"></a>Information som din organisation kan se   

Din organisation kan inte se några data, till exempel texter, e-post och bilder, i dina personliga appar. MTD-appen rapporterar information om dina appar, till exempel namn och version, i din organisation. Den faktiska informationen som rapporteras beror på vilken MTD-leverantör företaget använder. Din organisation kan se:   

* Appnamn  
* App-ID: Det unika namn som identifierar appen i Google Play.  
* Appversion och kort versionsnummer: De specifika versionsnumren för en app.  
* Appsamling (bundle) och dynamisk storlek: Mängden utrymme en app använder på din enhet. 


## <a name="install-app"></a>Installera app    
När du loggar in på en skyddad App uppmanas du automatiskt att installera en MTD-app. Slutför installationen genom att följa stegen på skärmen. Använd stegen i det här avsnittet för ytterligare hjälp.  
 
Du kan också uppmanas att registrera din enhet. Registreringen är nödvändig för att bekräfta din identitet och ansluta ditt skol-eller arbets konto till din enhet. Om du inte är registrerad guidas du automatiskt genom den installationen innan du installerar MTD-appen. När du kommer till skärmen **Hämta åtkomst** kan du starta installations stegen.  

Mer information om enhets registrering finns i [Registrera din personliga enhet i din organisations nätverk](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network).  

### <a name="ios-setup"></a>iOS-installation  

1. På sidan **Hämta åtkomst** följer du anvisningarna för att installera MTD-appen som krävs av din organisation.   
2. Gå tillbaka till sidan **Hämta åtkomst** och välj **Öppna**.  
3. MTD-appen ber om behörighet att öppna Microsoft Authenticator. Välj **Öppna**. 
4. Välj ditt arbets konto för att logga in. 
5. Vänta medan MTD-appen söker igenom din enhet efter säkerhetshot. 
6. Gå tillbaka till skolan eller arbets appen som du ursprungligen försökte komma åt. I det här läget kan din organisation uppmana dig att konfigurera andra säkerhets krav för appar, till exempel skapa en PIN-kod.   
7. Du bör nu ha åtkomst till appen. Om du fortfarande är blockerad:  
    * På sidan **Hämta åtkomst** väljer du **Check igen**.  
    * Gå till MTD-appen och Sök efter befintliga hot. Slutför de rekommenderade stegen för att lösa hotet och få åtkomst.    

### <a name="android-setup"></a>Android-konfigurering 

1. På sidan **Hämta åtkomst** följer du anvisningarna för att installera MTD-appen som krävs av din organisation.  
2. Gå tillbaka till sidan **Hämta åtkomst** och välj **Öppna**.  
3. MTD-appen ber om tillåtelse att komma åt vissa delar av enheten, om det behövs. För att den här appen ska fungera korrekt måste du **tillåta** åtkomst till kontakter. De begärda behörigheterna varierar mellan MTD-leverantörer.  
4. Välj ditt arbets konto för att logga in.  
5. Vänta medan MTD-appen söker igenom din enhet efter säkerhetshot.  
6. Gå tillbaka till skolan eller arbets appen som du ursprungligen försökte komma åt. I det här läget kan din organisation uppmana dig att konfigurera andra säkerhets krav för appar, till exempel skapa en PIN-kod.  
7. Du bör nu ha åtkomst till appen. Om du fortfarande är blockerad:  
    * På sidan **Hämta åtkomst** väljer du **Check igen**.  
    * Gå till MTD-appen och Sök efter befintliga hot. Slutför de rekommenderade stegen för att lösa hotet och få åtkomst.  

### <a name="installation-failed"></a>Installationen misslyckades  

Kontakta din IT-support om installationen Miss lyckas. Gå till [Företagsportal-webbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980) och leta upp din organisations kontaktuppgifter.  

Du kan också skicka dina app-loggar till IT-support-personen för att ge dem mer sammanhang om installationen.  
* Android-användare: [överför och skicka loggar via e-post](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android) från företagsportal.   

* iOS-enhet användare: [Hämta och skicka dina loggar](https://docs.microsoft.com/intune/apps/manage-microsoft-edge#use-microsoft-edge-on-ios-to-access-managed-app-logs) från Microsoft Edge för iOS.  

## <a name="resolve-a-threat"></a>Lösa ett hot  
Om ett hot överskrider organisationens definierade hotnivå kommer din organisation antingen att:  
   
* Blockera åtkomst: blockerar dig från att använda din organisations skyddade appar när du är inloggad på ditt arbets-eller skol konto.  
* Rensa data: tar bort dina arbets-eller skol data från en eller flera av organisationens skyddade appar.  

Öppna appen MTD på enheten för att lösa ett hot och få åtkomst till den. Läs igenom den tillhandahållna informationen för att lära dig hur hotet kan påverka din enhet och hur du kan lösa det. När du har följt stegen för att lösa hotet går du tillbaka till MTD-appen och startar en ny genomsökning. Det kan ta några minuter att få åtkomst till din organisation.  

## <a name="next-steps"></a>Nästa steg  

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).

