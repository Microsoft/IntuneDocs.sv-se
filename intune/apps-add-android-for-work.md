---
title: Distribuera appar till Android for Work-enheter
titlesuffix: Microsoft Intune
description: "Förstå hur man synkroniserar och tilldelar appar till Android for Work-enheter från Google Play for Work Store."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e3b5a742fb480cf9c4c77106b849eebb95ad2439
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Så här tilldelar du appar till Android for Work-enheter med Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Android for Work är ett program för Android-enheter. Alla appar som du installerar på Android for Work-enheter kommer från Google Play for Work-butiken. Du tilldelar appar till Android for Work-enheter på ett annat sätt än när du tilldelar dem till vanliga Android-enheter. Du kan logga in i butiken, bläddra efter de appar som du vill ha och godkänna dem. Programmet visas sedan i noden **Licensierade appar** i Azure-portalen. Härifrån kan du hantera tilldelningen av appen på samma sätt som du tilldelar andra appar.

Om du har skapat dina egna verksamhetsspecifika appar, kan du även tilldela dem på följande sätt:
- Registrera dig för ett Google-utvecklarkonto som låter dig publicera appar på ett privat område i Google Play-butiken.
- Synkronisera apparna med Intune.

## <a name="before-you-start"></a>Innan du börjar

Kontrollera att du har konfigurerat Intune och Android for Work så att de fungerar tillsammans i arbetsbelastningen **Enhetsregistrering** i Azure-portalen.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Synkronisera en app från Google Play for Work-butiken

1. Gå till [Google Play for Work store](https://play.google.com/work) (Google Play for Work-butiken). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.
2. Sök i butiken och välj app som du vill tilldela med hjälp av Intune.
3. Välj **Godkänn** på sidan som visar appen. Följande exempel visar att Microsoft Excel-appen har valts.</br>

    ![Exempel – Godkänna app i Google Play for Work-butiken](media/approve.png)</br>
    
  Ett fönster för appen öppnas där du uppmanas att tilldela behörigheter till appen för att utföra olika åtgärder. 

4. Välj **Godkänn** för att godkänna appbehörigheterna och fortsätta.</br>

    ![Exempel – Godkänna appbehörigheter](media/approve-app-permissions.png)

5. Välj hur du ska hantera nya begäranden om appbehörighet. Välj därefter **Spara** för att spara hur du vill att nya begäranden om appbehörighet ska hanteras.</br>

    ![Exempel – Spara nya begäranden om appbehörighet](media/approve-app-settings.png)</br>

    Appen godkänns och visas i IT-administrationskonsolen. Nu kan du [synkronisera Android for Work-appen med Intune](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-an-android-for-work-app-with-intune"></a>Synkronisera en Android for Work-app med Intune

Om du har godkänt en app från butiken men inte ser den i noden **licensierade appar** i arbetsbelastningen **mobilappar**, kan du framtvinga en omedelbar synkronisering genom att göra följande:

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning + hantering**.
3. Välj **Mobilappar** i **Intune**-fönstret.
4. I arbetsbelastningen **Mobilappar** väljer du **Android for Work** i avsnittet **Installation**.
5. I fönstret Android for Work väljer du **Synkronisera**. Sidan uppdaterar tid och status för den senaste synkroniseringen.
6. I arbetsbelastningen **Mobilappar** väljer du **Appar** för att visa de nyligen tillgängliga appen Android for Work.

När appen visas i noden **Applicenser** i arbetsbelastningen **Mobilappar** kan du [tilldela den på samma sätt som du gör med andra appar](/intune-azure/manage-apps/deploy-apps). Du kan endast tilldela appen till grupper av användare.

När du har tilldelat appen kommer den att installeras på de enheter du har valt. Användaren av enheten behöver inte godkänna installationen.

## <a name="manage-android-for-work-app-permissions"></a>Hantera appbehörigheter för Android for Work
Android for Work kräver att du godkänner appar i Googles hanterade Play-webbkonsol, innan de synkroniseras till Intune and tilldelas till användarna.  Eftersom Android for Work låter dig distribuera dessa appar till användarnas enheter tyst och automatiskt måste du acceptera appens behörigheter för alla användare.  Slutanvändare ser inga programbehörigheter när de installerar, så det är viktigt att du har läst och förstått dessa behörigheter.

När apputvecklare publicerar en ny version av appen med uppdaterade behörigheter tillåts de inte automatiskt, även om du har godkänt tidigare behörigheter. Enheter som kör den tidigare versionen av appen kan fortfarande använda den. Appen uppgraderas dock inte förrän de nya behörigheterna har godkänts. Enheter utan appen installerar den inte förrän du har godkänt dess nya behörigheter.

### <a name="how-to-update-app-permissions"></a>Så här uppdaterar du programbehörigheter

Du bör regelbundet besöka den hanterade Google Play-konsolen för att söka efter nya behörigheter. Du kan konfigurera Google Play att skicka dig eller andra ett e-postmeddelande när nya behörigheter krävs för en godkänd app. Om du tilldelar en app och noterar att den inte installeras på enheterna, söker du efter nya behörigheter med följande steg:

1. Besök http://play.google.com/work
2. Logga in med det Google-konto som du använde för att publicera och godkänna apparna.
3. Besök fliken **uppdateringar** för att se om några appar kräver en uppdatering.  Alla listade appar kräver nya behörigheter och tilldelas inte innan de tillämpas.  

Du kan också konfigurera Google Play att automatiskt godkänna appbehörigheter på nytt skilt för varje app. 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>Arbeta med en verksamhetsspecifik app från Google Play for Work-butiken

1. Gå till Google Play-utvecklarkonsolen [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work. Om du loggar in för första gången måste du registrera dig och betala en avgift för att bli medlem i Google-utvecklarprogrammet.
3. I konsolen väljer du **Lägg till nytt program**.
4. Du kan överföra och tillhandahålla information om din app på samma sätt som du publicerar en app i Google Play-butiken. Du måste dock välja inställningen ***Only make this application available to my organization (Gör det här programmet tillgängligt endast för min organisation) (<*organisationsnamn**>):</br>

    ![Alternativet för att endast göra appen tillgänglig för din organisation](media/restrict.png)</br>

Detta säkerställer att appen endast är tillgänglig för din organisation och inte är tillgänglig i den offentliga Google Play-butiken.
Mer information om hur du överför och publicerar Android-appar finns i [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469) (Hjälp med Google-utvecklarkonsolen).
5. När du har publicerat din app går du till [Google Play for Work store](https://play.google.com/work) (Google Play for Work-butiken). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.
6. Kontrollera att du kan se appen som du har publicerat i noden **appar** i butiken. Appen godkänns automatiskt för att synkroniseras med Intune.

## <a name="next-steps"></a>Nästa steg

- [Så här tilldelar du appar till grupper](apps-deploy.md)

