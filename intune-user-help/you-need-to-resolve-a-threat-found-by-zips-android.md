---
title: Lösa hot som upptäckts av Zimperium zIPS på Android
description: Lär dig hur du löser säkerhets- och apphot som har hittats på en Android-enhet.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ffbb656-93cd-4e0b-96c0-c5038cd2cf31
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: c5aebe07259e2fcee009e97bc3c12d7c02933360
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55846935"
---
# <a name="resolve-a-threat-found-by-zimperium-zips"></a>Åtgärda ett hot som Zimperium zIPS har påträffat

Zimperium zIPS är en tjänst för skydd mot mobila hot som identifierar potentiella hot på Android-enheter. Dessa hot rapporteras till företagsportalappen och visas som olösta, ej kompatibla problem. Om enheten identifieras som ej kompatibel kanske du inte kan:

* Ansluta till företagets e-post
* Ansluta till företagets Wi-Fi
* Ansluta till SharePoint Online
* Synkronisera företagsfiler med OneDrive
* Få åtkomst till företagsappar

Den här artikeln beskriver hur du kan känna igen hotaviseringar från Zimperium zIPS och vad du kan göra för att lösa dem. 

## <a name="troubleshoot-virus-or-security-threat"></a>Felsöka virus- eller säkerhetshot  
När ett virus- eller säkerhetshot identifieras agerar Zimperium zIPS enligt organisationens åtkomstprinciper. Företagets åtkomstprinciper kan förhindra att du kommer åt arbetets nätverk, appar och e-post från enheten.  

Zimperium zIPS uppmanar dig att vidta åtgärder för att återfå den åtkomst som du har förlorat. Välj hotet och följ instruktionerna i appen för att lösa det.

Eftersom appen är integrerad med företagets MDM-provider kan du även se en varning om begränsad åtkomst till företagsportalappen. Varningen ger dig instruktioner om att öppna Zimperium zIPS för att åtgärda virus- eller säkerhetshotet.  

  ![Exempel på skärmbild av enhetssidan i företagsportalen, som visar varningen från Zimperium zIPS.](./media/CP-lookout-virus-banner-1808.png)  

Välj varningsmeddelandet som visas under berörd enhet. Zimperium zIPS öppnas med information om hur du eliminerar hotet.  

## <a name="resolve-an-app-threat"></a>Lösa ett apphot

Om du installerar en app som ses som ett hot mot din enhet får du ett meddelande i Zimperium zIPS. Om den berörda appen finns kvar på enheten kan du inte komma åt företagsresurser.  

Lös detta genom att välja appen i listan över hot i Zimperium zIPS. Följ sedan anvisningarna på skärmen för att ta bort och avinstallera appen.    

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980). 
