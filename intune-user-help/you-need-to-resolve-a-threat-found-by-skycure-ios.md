---
title: Lösa hot som upptäckts av Symantec Endpoint Protection Mobile för iOS | Microsoft Docs
description: Lär dig hur du löser säkerhets-, virus- och apphot som har hittats på en iOS-enhet.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b40595f0-a399-4aa1-aa6f-344c2a1cb883
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8353b704df7ebdc648e5b223b80e656ca05956a
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848686"
---
# <a name="resolve-a-threat-found-by-symantec-endpoint-protection-mobile"></a>Lösa ett hot som hittas av Symantec Endpoint Protection Mobile

Symantec Endpoint Protection (SEP) Mobile är en tjänst för skydd mot mobila hot som identifierar potentiella hot på Android-enheter. Dessa hot rapporteras till företagsportalappen och visas som olösta, ej kompatibla problem. Om enheten identifieras som ej kompatibel kanske du inte kan:

* Ansluta till företagets e-post
* Ansluta till företagets Wi-Fi
* Ansluta till SharePoint Online
* Synkronisera företagsfiler med OneDrive
* Få åtkomst till företagsappar

Den här artikeln beskriver hur du får åtkomst till företagets resurser när SEP Mobile identifierar ett säkerhets- eller apphot.  

## <a name="troubleshoot-a-virus-or-security-threat"></a>Felsöka ett virus- eller säkerhetshot

1. Du får ett meddelande som liknar det i skärmbilden nedan när du försöker få åtkomst till företagets e-post eller webbplatser. Tryck på länken till **enhetshanteringsportalen** för att öppna [företagsportalens webbplats](https://portal.manage.microsoft.com/devices).

    ![Exempel på skärmbild av ett felmeddelande för Lookout for Work, med en länk till företagsportalens webbplats och en blå OK-knapp.](./media/mtd-go-to-device-management-portal-android.png)  

2. Välj din enhet.  
3. Läs varningen som visas under enheten. Den ger dig instruktioner för hur du öppnar SEP Mobile för att åtgärda virus- eller säkerhetshotet.    

    ![Exempel på skärmbild av enhetssidan i företagsportalen, som visar varningen från SEP Mobile.](./media/CP-lookout-virus-banner-1808.png)

## <a name="troubleshoot-an-app-threat"></a>Felsöka ett apphot

Om du installerar en app som ses som ett hot mot din enhet får du ett meddelande i appen SEP Mobile. Om den berörda appen finns kvar på enheten kan du inte komma åt företagsresurser.  

Lös detta genom att välja appen i listan över hot i SEP Mobile. Följ sedan anvisningarna på skärmen för att ta bort och avinstallera appen.  

Behöver du fortfarande hjälp? Kontakta företagets support. Du hittar kontaktinformationen på [Företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).   

