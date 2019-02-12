---
title: Tilldela Managed Google Play-appar till Android enterprise-enheter
titlesuffix: Microsoft Intune
description: Förstå hur du synkroniserar och tilldelar appar till Android enterprise-enheter från Managed Google Play Butik.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b68206fd2170dd2bc156d844ae83caafaa08180
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836582"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Lägg till hanterade Google Play-appar till Android enterprise-enheter med Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android enterprise är ett program för Android-arbetsprofilenheter, dedikerade enheter/kioskenheter samt fullständigt hanterade enheter. För Android-arbetsprofilenheter är Android enterprise en uppsättning funktioner och tjänster som avgränsar personliga appar och data från arbetsappar och data. Android enterprise ger tillgång till ytterligare hanteringsalternativ och sekretess när Android-enheter används i arbetet. Intune hjälper dig att distribuera appar och inställningar till Android-arbetsprofilenheter för att se till att arbetsrelaterad och personlig information hålls isär. Alla appar som du installerar på Android-arbetsprofilenheter kommer från Managed Google Play Butik. Hur du tilldelar appar till Android-arbetsprofilenheter skiljer sig från hur du tilldelar dem till vanliga Android-enheter. Du kan logga in i butiken, bläddra efter de appar som du vill ha och godkänna dem. Appen visas sedan i noden **Licensierade appar** i Azure Portal och du kan hantera tilldelning av appen precis som för alla andra appar.

Om du har skapat dina egna verksamhetsspecifika appar, kan du även tilldela dem på följande sätt:
- Registrera dig för ett Google-utvecklarkonto som låter dig publicera appar på ett privat område i Google Play-butiken.
- Synkronisera apparna med Intune.

## <a name="before-you-start"></a>Innan du börjar

Kontrollera att du har konfigurerat Intune och Android-arbetsprofiler så att de fungerar tillsammans i arbetsbelastningen **Enhetsregistrering** i Azure Portal. Mer information finns i [Registrera Android-enheter](android-work-profile-enroll.md).

>[!NOTE]
>När du arbetar med Microsoft Intune, rekommenderar vi att du använder antingen webbläsaren Google Chrome eller Microsoft Edge.

## <a name="managed-google-play-app-type"></a>Hanterade Google Play-apptyper 
Den **hanterade Google Play**-apptypen gör att du kan lägga till mer specifikt [hanterade Google Play-appar](https://play.google.com/work/search?q=microsoft&c=apps) till Intune. Som Intune-administratör kan du bläddra, söka, godkänna, synkronisera och tilldela godkända hanterad Google Play-appar i Intune.  Du behöver inte längre bläddra till den hantera Google Play-konsolen separat och du behöver inte längre autentisera dig på nytt. 

> [!NOTE]
> Om du vill synkronisera en hanterad Google Play-app med Intune finns mer information i [Synkronisera en hanterad Google Play-app med Intune](apps-add-android-for-work.md#synchronize-a-managed-google-play-app-with-intune-alternative)

## <a name="add-a-managed-google-play-app-using-intune"></a>Lägg till en hanterad Google Play-app med Intune

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**.  
    Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Klientappar** > **Appar**.
5. Välj **Lägg till** i fönsterrutan **Appar**.
6. I listrutan **Apptyp** väljer du **Hanterat Google Play-konto**.
7. Välj **Hanterat Google Play – godkända appar** för att söka efter godkända appar för hanterat Google Play-konto.
8. Klicka på varje app som du vill inkludera. Sedan, c
9. Klicka på **Godkänn** för att godkänna den hanterade Google Play-appen och klicka på **Godkänn** för att acceptera appens behörigheter. 
10. Klicka på **OK** för att inkludera appen.
11. Klicka på **Lägg till** i **App**-fönstret för att synkronisera med den hanterade Google Play-tjänsten.

## <a name="synchronize-a-managed-google-play-app-with-intune-alternative"></a>Synkronisera en hanterad Google Play-app med Intune (alternativ)
Om du vill synkronisera en hanterad Google Play-app med Intune i stället för att lägga till den direkt med hjälp av Intune kan du använda följande steg.

> [!IMPORTANT]
> Informationen nedan är en alternativ metod för att lägga till en hanterad Google Play-app med Intune enligt beskrivningen ovan.

### <a name="synchronize-an-app-from-the-managed-google-play-store"></a>Synkronisera en app från Managed Google Play Butik

1. Gå till [Managed Google Play Butik](https://play.google.com/work). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android enterprise.
2. Sök i butiken och välj app som du vill tilldela med hjälp av Intune.
3. På sidan som visar appen, väljer du **Godkänn**.  
    I följande exempel har Microsoft Excel-appen valts.

    ![Knappen Godkänn i Managed Google Play Butik](media/approve.png)
    
   Ett fönster för appen öppnas där du uppmanas att tilldela behörigheter till appen för att utföra olika åtgärder. 

4. Välj **Godkänn** för att godkänna appbehörigheterna och fortsätta.

    ![Knappen Godkänn för app-behörigheter](media/approve-app-permissions.png)

5. Välj ett alternativ för att hantera nya begäranden om app-behörighet och välj sedan **Spara**.

    ![Alternativ för att hantera nya begäranden om app-behörighet](media/approve-app-settings.png)

    Appen godkänns och den visas i IT-administrationskonsolen. Därefter kan du [synkronisera Android-arbetsprofilappen med Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune). 

### <a name="sync-a-managed-google-play-app-with-intune"></a>Synkronisera en Managed Google Play-app med Intune

Om du har godkänt en app från butiken men inte ser den i noden **licensierade appar** i arbetsbelastningen **Klientappar**, kan du framtvinga en omedelbar synkronisering genom att göra följande:

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar** i **Intune**-fönstret.
4. I arbetsbelastningsfönstret **Klientappar** under **Installation** väljer du **Hanterat Google Play-konto**.
5. I fönstret **Hanterat Google Play-konto** väljer du **Uppdatera**.  
    Sidan uppdaterar tid och status för den senaste synkroniseringen.
6. I arbetsbelastningsfönstret **Klientappar** väljer du **Appar**.  
    Den nya tillgängliga Managed Google Play-appen visas.

## <a name="assigning-the-managed-google-play-app"></a>Tilldela den hanterade Google Play-appen

När appen visas i noden **Applicenser** i arbetsbelastningsfönstret **Klientappar** kan du [tilldela den på samma sätt som du gör med andra appar](/intune-azure/manage-apps/deploy-apps) genom att tilldela appen till grupper eller användare.

När du har tilldelat appen installeras den på de enheter som du har som mål. Användaren av enheten behöver inte godkänna installationen.

## <a name="manage-android-enterprise-app-permissions"></a>Hantera behörigheter för Android enterprise-app
Android enterprise kräver att du godkänner appar i den Managed Google Play-webbkonsolen innan du synkroniserar dem med Intune och tilldelar dem till användarna. Eftersom Android enterprise låter dig distribuera dessa appar till användarnas enheter tyst och automatiskt måste du acceptera appens behörigheter för alla användare. Användare ser inga programbehörigheter när de installerar apparna, så det är viktigt att du har förstått dessa behörigheter.

När apputvecklare uppdaterar behörigheter med en ny version av appen tillåts de inte automatiskt, även om du har godkänt tidigare behörigheter. Enheter som kör den tidigare versionen av appen kan fortfarande använda den. Appen uppgraderas dock inte förrän de nya behörigheterna har godkänts. Enheter utan appen installerar den inte förrän du har godkänt dess nya behörigheter.

### <a name="update-app-permissions"></a>Uppdatera app-behörigheter

Du bör regelbundet besöka den hanterade Google Play-konsolen för att söka efter nya behörigheter. Du kan konfigurera Google Play att skicka dig eller andra ett e-postmeddelande när nya behörigheter krävs för en godkänd app. Om du tilldelar en app och noterar att den inte installeras på enheterna, söker du efter nya behörigheter genom att göra följande:

1. Gå till [Google Play](https://play.google.com/work).
2. Logga in med det Google-konto som du använde för att publicera och godkänna apparna.
3. Välj fliken **Uppdateringar** och kontrollera om några appar behöver en uppdatering.  
    Alla listade appar kräver nya behörigheter och tilldelas inte innan de tillämpas.

Du kan också konfigurera Google Play att automatiskt godkänna app-behörigheter på nytt skilt för varje app. 

## <a name="working-with-a-line-of-business-app-from-the-managed-google-play-store"></a>Arbeta med en verksamhetsspecifik app från Managed Google Play Butik

1. Logga in till [Google Play Developer Console](https://play.google.com/apps/publish) med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android enterprise.  
    Om du loggar in för första gången måste du registrera dig och betala en avgift för att bli medlem i Google-utvecklarprogrammet.
2. I konsolen väljer du **Lägg till nytt program**.
3. Du kan överföra och tillhandahålla information om din app på samma sätt som du publicerar en app i Google Play-butiken. Du måste dock välja **Gör det här programmet tillgängligt endast för min organisation (<*organisationsnamn*>)**.

    ![Gör appen tillgänglig endast för din organisation](media/restrict.png)

    Den här åtgärden gör bara appen tillgänglig för din organisation. Den blir inte tillgänglig på i offentliga Google Play-butiken.

    Mer information om att ladda upp och publicerar Android-appar finns i [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469) (Hjälp med Google-utvecklarkonsolen).
4. När du har publicerat din app kan du logga in på [Managed Google Play Butik](https://play.google.com/work) med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android för företag.
5. I noden **Appar** i butiken, kontrollerar du att den app som du har publicerat visas.  
    Appen godkänns automatiskt för att synkroniseras med Intune.

## <a name="delete-managed-google-play-apps"></a>Radera hanterade Google Play-appar 
Du kommer att kunna ta bort hanterade Google Play-appar från Microsoft Intune om nödvändigt. Om du vill ta bort en hanterad Google Play-app öppnar du Microsoft Intune i Azure-portalen och väljer **Klientappar** > **Appar**. Från listan över appar väljer du ellipserna (...) till höger om den hanterade Google Play-appen och väljer sedan **Ta bort** från den visade listan. När du tar bort en hanterad Google Play-app från applistan blir den hanterade Google Play-appen automatiskt ej godkänd.

## <a name="next-steps"></a>Nästa steg

- [Tilldela appar till grupper](apps-deploy.md) 

