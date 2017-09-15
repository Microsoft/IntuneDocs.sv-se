---
title: Distribuera appar till Android for Work-enheter
titlesuffix: Azure portal
description: "Använd det här ämnet för att synkronisera och distribuera appar till Android for Work-enheter från Google Play for Work Store.”"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 06/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 803f1475a220e52a0f7d8a41d58f0a5337ff6555
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Så här tilldelar du appar till Android for Work-enheter med Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Du tilldelar appar till Android for Work-enheter på ett annat sätt än när du tilldelar dem till vanliga Android-enheter. Alla appar som du installerar för Android for Work kommer från Google Play for Work-butiken. Du kan logga in i butiken, bläddra efter de appar som du vill ha och godkänna dem.
Programmet visas sedan i noden **Licensierade appar** i Azure-portalen. Härifrån kan du hantera tilldelningen av appen på samma sätt som du tilldelar andra appar.

Om du har skapat dina egna verksamhetsspecifika appar, kan du även tilldela dem på följande sätt:
- Registrera dig för ett Google-utvecklarkonto som låter dig publicera appar på ett privat område i Google Play-butiken.
- Synkronisera apparna med Intune.

## <a name="before-you-start"></a>Innan du börjar

Kontrollera att du har konfigurerat Intune och Android for Work så att de fungerar tillsammans i arbetsbelastningen **Enhetsregistrering** i Azure-portalen.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Synkronisera en app från Google Play for Work-butiken

1. Gå till [Google Play for Work store](https://play.google.com/work) (Google Play for Work-butiken). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.
2. Sök i butiken efter den app som du vill tilldela med hjälp av Intune.
3. På sidan för den app som du har valt trycker du på **Godkänn**. I det här exemplet har du valt appen Microsoft Excel.<br>
  ![Exempel på hur du godkänner en app](media/approve.png)
4. Ett fönster för appen öppnas där du uppmanas att tilldela behörigheter till appen för att utföra olika åtgärder. Välj **Godkänn** för att fortsätta.<br>
  ![Exempel på hur du godkänner appbehörigheter](media/approve-app-permissions.png)
5. Appen godkänns och visas i IT-administrationskonsolen.

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Publicera och synkronisera en verksamhetsspecifik app från Google Play for Work-butiken

1. Gå till Google Play-utvecklarkonsolen [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work. Om du loggar in för första gången måste du registrera dig och betala en avgift för att bli medlem i Google-utvecklarprogrammet.
3. I konsolen väljer du **Lägg till nytt program**.
4. Du kan överföra och tillhandahålla information om din app på samma sätt som du publicerar en app i Google Play-butiken. Du måste dock välja inställningen **Only make this application available to my organization (Gör det här programmet tillgängligt endast för min organisation) (<*organisationsnamn*>)**:<br>
  ![Alternativ för att endast göra appen tillgänglig för din organisation](media/restrict.png)<br>
Detta säkerställer att appen endast är tillgänglig för din organisation och inte är tillgänglig i den offentliga Google Play-butiken.
Mer information om hur du överför och publicerar Android-appar finns i [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469) (Hjälp med Google-utvecklarkonsolen).
5. När du har publicerat din app går du till [Google Play for Work store](https://play.google.com/work) (Google Play for Work-butiken). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.
6. Kontrollera att du kan se appen som du har publicerat i noden **appar** i butiken. Appen godkänns automatiskt för att synkroniseras med Intune.

## <a name="assign-an-android-for-work-app"></a>Tilldela en Android for Work-app

Om du har godkänt en app från butiken men inte ser den i noden **licensierade appar** i arbetsbelastningen **mobilappar**, kan du framtvinga en omedelbar synkronisering genom att göra följande:

1. Logga in på Azure-portalen.
2. Välj **Mobilappar** på **Intune**-bladet.
3. Välj **Installation** > **Android for Work** i arbetsbelastningen **Mobilappar**.
4. På bladet Android for Work väljer du **Synkronisera nu**.
5. Sidan visar även tid och status för den senaste synkroniseringen.

När appen visas i noden **licensierade appar** i arbetsbelastningen **mobilappar** kan du [tilldela den på samma sätt som du gör med andra appar](/intune-azure/manage-apps/deploy-apps). Du kan endast tilldela appen till grupper av användare.

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



