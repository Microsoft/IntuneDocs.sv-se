---
title: Windows-enhetsregistrering i Intune-företagsportalen | Microsoft Docs
description: Kom igång med att registrera en Windows-enhet i företagsportalen
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9f29e2d737dfd7bef709f239d6c8506c3bb746c
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196884"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Windows-enhetsregistrering i Intune-företagsportalen  

Registrera din Windows-enhet i Intune-företagsportalappen för att få säker åtkomst till appar, e-postmeddelanden och filer som hör till arbetet eller skolan. Om din organisation kräver eller rekommenderar vissa appar, till exempel Office eller OneDrive, får du dem antingen under registreringen eller så är de tillgängliga i företagsportalen efter registreringen.  

Du kan registrera Windows 10-enheter via företagsportalens webbplats *eller* appen. Om du registrerar en enhet med en tidigare version av Windows måste du registrera enheten via företagsportalens webbplats.  

## <a name="install-company-portal-app"></a>Installera företagsportalappen  
Du har kanske redan företagsportalappen installerad på din enhet. Sök efter appen i listan __Alla appar__.  Om du inte ser företagsportalen i applistan kan du följa de här stegen för att installera den.  

1. Öppna **Microsoft Store** på din enhet.

2. I fältet **Sök** skriver du **Företagsportal**.

3. I listan med resultat väljer du **Företagsportal** > **Installera**.

4. Välj antingen **Installera** eller på **Ledigt**. Det finns ingen skillnad mellan de här två alternativen; orden visas baserat på hur din organisation har konfigurerat appen.  

## <a name="find-windows-10-version-number"></a>Hitta versionsnumret för Windows 10  
Registreringssteg skiljer sig åt för olika versioner av Windows 10-enheter. Följande steg beskriver hur du hittar versionsnumret för skrivbordsenheter och mobila enheter med Windows 10. När du känner till din version fortsätter du till de rekommenderade registreringsstegen.  

### <a name="windows-10-desktop-devices"></a>Windows 10 Desktop-enheter  

1. Gå till **Start**.

2. I sökfältet skriver du frasen ”om din dator”. Välj __Om din dator__ från resultatet.  


   ![search settings for about your pc](media/searching_for_about_your_pc.png)  

3. Rulla ned till **Windows-specifikationer** och leta upp den **Version** av Windows 10 som är installerad på din dator.  


   ![Om din dator i Windows 10 Desktop](media/settings_about_pc.png)  

4. Om du har version  

    *  __1607 eller senare__: Registrera din enhet via [**Inställningar** > **Konto** > **Åtkomst till arbete eller skola** ](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 eller tidigare__: Registrera din enhet via [**Inställningar** > **Konto** > **Ditt konto** ](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

### <a name="windows-10-mobile-devices"></a>Windows 10 Mobile-enheter       

1.  Gå till __alla appar__ och välj appen __Inställningar__.  
2.  Välj __System__ > __Om__.      
3.  Under __Enhetsinformation__ letar du upp __Version__.  
4. Om du har version  

    *  __1607 eller senare__: Registrera din enhet via [**Inställningar** > **Åtkomst till arbete eller skola** ](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 eller senare__: Registrera din enhet via [**Inställningar** > **Konton** ](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

## <a name="enroll-non-windows-10-devices"></a>Registrera icke-Windows 10-enheter  
Använd följande artiklar för att registrera andra Windows-enheter som stöds via företagsportalens webbplats:   
* [Windows 8.1- eller Windows RT 8.1-enhet](enroll-your-W81-or-rt81-windows.md)  
* [Windows Phone 8.1-enhet](enroll-your-wp81-windows.md)    

## <a name="it-administrator-support"></a>IT-administratörssupport  
Om du är IT-administratör och stöter på problem när du registrerar enheter kan du läsa [Felsöka problem med registrering av Windows-enhet i Microsoft Intune](https://support.microsoft.com/help/4469913). Den här artikeln innehåller vanliga fel, deras orsaker och stegen för att lösa dem.  

## <a name="next-steps"></a>Nästa steg  
Nu när du känner till de enheter som stöds och ditt Windows 10-versionsnummer fortsätter du till rekommenderad registreringsartikel.  
 
Mer information om enhetshantering, företagsportalen och hur både används i skolor och på arbetet finns i följande artiklar:  
* [Använda hanterade enheter för att få åtkomst arbets- eller skolresurs](use-managed-devices-to-get-work-done.md)  
* [Vad händer när du registrerar din enhet i Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [Vilken information kan min organisation se när jag registrerar min enhet?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

Behöver du hjälp? Kontakta företagssupporten. [Gå till företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980) och leta upp din organisations IT-kontaktuppgifter.  
