---
title: Distribuera appar till Android for Work-enheter
titlesuffix: Microsoft Intune
description: Förstå hur man synkroniserar och tilldelar appar till Android for Work-enheter från Google Play for Work Store.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1742c33642667a9e7b8ca2f780094345959cd86c
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="assign-apps-to-android-for-work-devices-with-intune"></a>Tilldela appar till Android for Work-enheter med Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android for Work är ett program för Android-enheter. Alla appar som du installerar på Android for Work-enheter kommer från Google Play for Work-butiken. Hur du tilldelar appar till Android for Work-enheter skiljer sig från hur du tilldelar dem till vanliga Android-enheter. Du kan logga in i butiken, bläddra efter de appar som du vill ha och godkänna dem. Appen visas sedan i noden **Licensierade appar** i Azure Portal och du kan hantera tilldelning av appen precis som för alla andra appar.

Om du har skapat dina egna verksamhetsspecifika appar, kan du även tilldela dem på följande sätt:
- Registrera dig för ett Google-utvecklarkonto som låter dig publicera appar på ett privat område i Google Play-butiken.
- Synkronisera apparna med Intune.

## <a name="before-you-start"></a>Innan du börjar

Kontrollera att du har konfigurerat Intune och Android for Work så att de fungerar tillsammans i arbetsbelastningen **Enhetsregistrering** i Azure-portalen.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Synkronisera en app från Google Play for Work-butiken

1. Gå till [Google Play for Work store](https://play.google.com/work) (Google Play for Work-butiken). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.
2. Sök i butiken och välj app som du vill tilldela med hjälp av Intune.
3. På sidan som visar appen, väljer du **Godkänn**.  
    I följande exempel har Microsoft Excel-appen valts.

    ![Knappen Godkänn i Google Play for Work-butiken](media/approve.png)
    
   Ett fönster för appen öppnas där du uppmanas att tilldela behörigheter till appen för att utföra olika åtgärder. 

4. Välj **Godkänn** för att godkänna appbehörigheterna och fortsätta.

    ![Knappen Godkänn för app-behörigheter](media/approve-app-permissions.png)

5. Välj ett alternativ för att hantera nya begäranden om app-behörighet och välj sedan **Spara**.

    ![Alternativ för att hantera nya begäranden om app-behörighet](media/approve-app-settings.png)

    Appen godkänns och den visas i IT-administrationskonsolen. Härnäst kan du [synkronisera Android for Work-appen med Intune](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-an-android-for-work-app-with-intune"></a>Synkronisera en Android for Work-app med Intune

Om du har godkänt en app från butiken men inte ser den i noden **licensierade appar** i arbetsbelastningen **mobilappar**, kan du framtvinga en omedelbar synkronisering genom att göra följande:

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enheter** i **Mobilappar**-fönstret.
4. I arbetsbelastningsfönstret **Mobilappar** under **Installera**, väljer du **Android for Work**.
5. I fönstret **Android for Work** väljer du **Synkroniser**.  
    Sidan uppdaterar tid och status för den senaste synkroniseringen.
6. I arbetsbelastningsfönstret **Mobilappar** väljer du **Appar**.  
    Den nyligen tillgängliga Android for Work-appen visas.

När appen visas i noden **Applicenser** i arbetsbelastningsfönstret för **Mobilappar** kan du [tilldela den på samma sätt som du gör med andra appar](/intune-azure/manage-apps/deploy-apps). Du kan endast tilldela appen till grupper av användare.

När du har tilldelat appen installeras den på de enheter som du har som mål. Användaren av enheten behöver inte godkänna installationen.

## <a name="manage-android-for-work-app-permissions"></a>Hantera appbehörigheter för Android for Work
Android for Work kräver att du godkänner appar i den hanterade Google Play-webbkonsolen innan du synkroniserar dem med Intune och tilldelar dem till användarna. Eftersom Android for Work låter dig distribuera dessa appar till användarnas enheter tyst och automatiskt måste du acceptera appens behörigheter för alla användare. Användare ser inga programbehörigheter när de installerar apparna, så det är viktigt att du har läst och förstått dessa behörigheter.

När apputvecklare publicerar en ny version av appen med uppdaterade behörigheter tillåts de inte automatiskt, även om du har godkänt tidigare behörigheter. Enheter som kör den tidigare versionen av appen kan fortfarande använda den. Appen uppgraderas dock inte förrän de nya behörigheterna har godkänts. Enheter utan appen installerar den inte förrän du har godkänt dess nya behörigheter.

### <a name="update-app-permissions"></a>Uppdatera app-behörigheter

Du bör regelbundet besöka den hanterade Google Play-konsolen för att söka efter nya behörigheter. Du kan konfigurera Google Play att skicka dig eller andra ett e-postmeddelande när nya behörigheter krävs för en godkänd app. Om du tilldelar en app och noterar att den inte installeras på enheterna, söker du efter nya behörigheter genom att göra följande:

1. Gå till [Google Play](http://play.google.com/work).
2. Logga in med det Google-konto som du använde för att publicera och godkänna apparna.
3. Välj fliken **Uppdateringar** och kontrollera om några appar behöver en uppdatering.  
    Alla listade appar kräver nya behörigheter och tilldelas inte innan de tillämpas.

Du kan också konfigurera Google Play att automatiskt godkänna app-behörigheter på nytt skilt för varje app. 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>Arbeta med en verksamhetsspecifik app från Google Play for Work-butiken

1. Logga in till [Google Play Developer Console](https://play.google.com/apps/publish) med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.  
    Om du loggar in för första gången måste du registrera dig och betala en avgift för att bli medlem i Google-utvecklarprogrammet.
2. I konsolen väljer du **Lägg till nytt program**.
3. Du kan överföra och tillhandahålla information om din app på samma sätt som du publicerar en app i Google Play-butiken. Du måste dock välja **Gör det här programmet tillgängligt endast för min organisation (<*organisationsnamn*>)**.

    ![Gör appen tillgänglig endast för din organisation](media/restrict.png)

    Detta säkerställer att appen endast är tillgänglig för din organisation och den är inte tillgänglig i den offentliga Google Play-butiken.

    Mer information om att ladda upp och publicerar Android-appar finns i [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469) (Hjälp med Google-utvecklarkonsolen).
4. När du har publicerat din app kan du logga in på [Google Play for Work-butiken](https://play.google.com/work) med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.
5. I noden **Appar** i butiken, kontrollerar du att den app som du har publicerat visas.  
    Appen godkänns automatiskt för att synkroniseras med Intune.

## <a name="next-steps"></a>Nästa steg

- [Tilldela appar till grupper](apps-deploy.md) 

