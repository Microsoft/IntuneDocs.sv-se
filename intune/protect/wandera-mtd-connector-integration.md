---
title: Konfigurera integrering av Wandera Mobile Threat Protection med Intune
titleSuffix: Intune on Azure
description: Konfigurera Wandera Mobile Threat Protection med Microsoft Intune för att styra mobil enhetsåtkomst till företagets resurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d90e3757ced90bea21e4033b6baa93bfa201b1f2
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514225"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>Integrera Wandera Mobile Threat Protection med Intune  

Utför följande steg när du ska integrera Wandera Mobile Threat Defense-lösningen med Intune.  

> [!NOTE]
> Den här Mobile Threat Defense-leverantören stöds inte för oregistrerade enheter.

## <a name="before-you-begin"></a>Innan du börjar  

Innan du påbörjar processen för att integrera Wandera med Intune behöver du uppfylla följande förhandskrav:
- Microsoft Intune-prenumeration  
- Azure Active Directory-administratörsautentiseringsuppgifter som beviljar följande behörigheter:  
  - Logga in och läsa användarprofil  
  - Gå till katalogen som den inloggade användaren  
  - Läs katalogdata  
  - Skicka enhetsinformation till Intune  

- Wandera-prenumeration:
  - Ett eller flera Wandera-konton med licenser för EMM Connect  
  - Ett konto med superadministratörsbehörighet i Wandera  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Appauktorisering för Wandera Mobile Threat Defense  

Appauktoriseringsprocess för Wandera Mobile Threat Defense:  
- Tillåt att Wandera Mobile Threat Defense-tjänsten förmedlar information om enhetens hälsostatus till Intune.  
- Wandera synkroniserar med Azure AD-registreringsgruppmedlemskap för att fylla enhetens databas.  
- Tillåt administratörsportalen för Wandera RADAR att använda Azure AD enkel inloggning (SSO).  
- Låt Wandera Mobile Threat Defense-appen logga in med enkel inloggning för Azure AD.  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>Ställ in Mobile Threat Defense-integrering  
Installation av *EMM Connect* för Wandera kräver en engångskonfiguration som du utför i konsolerna för både Intune och Wandera. Konfigurationsprocessen tar cirka 15 minuter. Du kan slutföra konfigurationen utan att samordna med supporten för Wandera.  

### <a name="enable-support-for-wandera-in-intune"></a>Aktivera stöd för Wandera i Intune

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Administration av klientorganisation** > **Anslutning och token** > **Skydd mot mobilhot** > **Lägg till**.
3. På sidan **Lägg till anslutningsapp** använder du listrutan och väljer **Wandera**. Välj sedan **Skapa**.  
4. I Mobile Threat Defense-rutan väljer du MTD-anslutningsappen **Wandera** i listan över anslutningsappar för att öppna fönstret *Redigera anslutningsapp*. Välj **Öppna administratörskonsolen för Wandera** för att öppna [RADAR](https://radar.wandera.com/login), Wandera-administratörskonsolen, och logga in. 
5. I Wandera-konsolen går du till **Inställningar** > **EMM-integrering**. Välj fliken**EMM-anslutning**. Använd listrutan *EMM-leverantör* och välj *Microsoft Intune*.

   ![Välj Intune](./media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

6. Välj **Bevilja** för att öppna en anslutning till Intune-portalen. Logga in med dina administratörsautentiseringsuppgifter för Intune, markera kryssrutan och **Godkänn** sedan behörigheterna för begäran.  

   ![Redigera behörigheter](./media/wandera-mtd-connector-integration/permissions.png) 

7. Wandera slutför anslutningen och återgår till administratörskonsolen RADAR. Upprepa processen för att **Bevilja** åtkomst till ytterligare konfigurationer efter behov.  

   ![Integreringar och behörigheter](./media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

8. I konsolen RADAR kopierar du namnet på gruppen **SyncOnly** som visas under **EMM-etikett**. Du använder det här namnet för att konfigurera en grupp i Intune som ska synkroniseras med Wandera.

   ![Synkroniseringsgrupp](./media/wandera-mtd-connector-integration/sync-group-name.png) 

9. Gå tillbaka till [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-konsolen och redigera Wandera MTD-anslutningsprogrammet. Ställ tillgängliga växlar som **På** och **spara** konfigurationen.  

   ![Aktivera Wandera](./media/wandera-mtd-connector-integration/enable-wandera.png) 

Intune och Wandera är nu anslutna.  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>Konfigurera program och synkroniseringsgrupp för Wandera  
Om du vill distribuera Wandera lägger du till Wandera-mobilappar för de plattformar du använder (iOS och Android) till Intune och tilldelar dem till en specifik grupp för synkronisering: gruppen *SyncOnly*. 

Följande stycken och procedurer vägleder dig genom den här processen.

Om du behöver mer information om den här processen från Wandera kan du logga in på Wandera [RADAR](https://radar.wandera.com/login). Gå till **Inställningar** > **EMM-integrering**, välj fliken **App Push** och välj sedan **Microsoft Intune**. Fliken App Push uppdateras med anvisningar som är specika för Intune.  

### <a name="add-the-wandera-apps"></a>Lägg till Wandera-appar  
Skapa klientappar i Intune för att distribuera Wandera-appen till Android- och iOS/iPadOS-enheter. Se [Lägg till MTD-appar](mtd-apps-ios-app-configuration-policy-add-assign.md) för specifika procedurer och anpassad information för Wandera-appar.  

När du har skapat apparna kan du återvända hit för att skapa synkroniseringsgruppen och tilldela appar.

### <a name="create-the-synchronization-group-and-assign-the-apps"></a>Skapa synkroniseringsgruppen och tilldela appar

1. I konsolen RADAR hämtar du namnet på gruppen **SyncOnly** som visas under **EMM-etikett**. Du kan ha sparat det här namnet i steg 7 under [aktivering av stöd för Wandera i Intune](#enable-support-for-wandera-in-intune). Använd det här namnet som namn på gruppen i Intune för synkronisering med Wandera.  

2. I administrationscentret för Endpoint Manager går du till **Grupper** och väljer **Ny grupp**. Ange följande för att konfigurera synkroniseringsgruppen för användning av Wandera:
   - **Grupptyp**: **Säkerhet**
   - **Gruppnamn:** Ange namnet **SyncOnly** som du hämtade från administrationskonsolen Wandera RADAR.

   ![konfigurera synkroniseringsgruppen](./media/wandera-mtd-connector-integration/configure-sync-group.png)

3. Välj **Medlemmar** och tilldela grupper som innehåller Android och iOS/iPadOS-enheter som du vill använda med Wandera.

4. Spara gruppen genom att välja **Skapa**.

Mer information finns i [Distribuera appar](../apps/apps-deploy.md)

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>Tilldela Wandera-appararna till synkroniseringsgruppen  
Upprepa följande procedur för Wandera-appen som du skapat för iOS/iPadOS och Android.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** och välj Wandera-appen.
3. Välj **Tilldelninar** och sedan **Lägg till grupp**.  
4. Välj **Krävs** för *Tilldelningstyp* i fönstret *Lägg till grupp*.
5. Välj **inkluderade grupper**, och sedan **Välj de grupper som ska ingå**. Ange den grupp som du skapade för Wandera-synkronisering och klicka sedan på **Välj** > **OK** > **OK**. Välj **Spara** för att slutföra grupptilldelningen. 

## <a name="next-steps"></a>Nästa steg  
Nu när du har konfigurerat integrationen kan du börja konfigurera principer, ställa in villkorlig åtkomst och visa rapporter i Wandera-administratörskonsolen. Läs mer om att hantera och konfigurera Wandera i [Kom igång-guiden för Support Center](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started) i Wandera-dokumentationen. 
