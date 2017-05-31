---
title: Tilldela appar till Android for Work-enheter | Microsoft Docs
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Använd det här avsnittet för att synkronisera och sedan tilldela appar till Android for Work-enheter från Google Play for Work-butiken."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 49e86ab665d9022739c0330092734ba897ea3b02
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Så här tilldelar du appar till Android for Work-enheter med Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Du tilldelar appar till Android for Work-enheter på ett annat sätt än när du tilldelar dem till vanliga Android-enheter. Alla appar som du installerar för Android for Work kommer från Google Play for Work-butiken. Du kan logga in i butiken, bläddra efter de appar som du vill ha och godkänna dem.
Appen visas sedan i noden **Licensierade appar** i Intune-portalen. Härifrån kan du hantera tilldelningen av appen på samma sätt som du tilldelar andra appar.

Dessutom kan du tilldela de verksamhetsspecifika appar som du själv har skapat. För att göra det måste du registrera dig för en Google-utvecklarkonto som låter dig att publicera appar på en privat plats i Google Play-butiken och sedan synkronisera dem med Intune.

## <a name="before-you-start"></a>Innan du börjar

Kontrollera att du har konfigurerat Intune och Android for Work tillsammans i arbetsbelastningen **Enhetsregistrering** i Intune-portalen.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Synkronisera en app från Google Play for Work-butiken


1. Gå till [Google Play for Work store](https://play.google.com/work) (Google Play for Work-butiken). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.
2. Sök i butiken efter den app som du vill tilldela med hjälp av Intune.
3. På sidan för den app som du har valt trycker du på **Godkänn**. I det här exemplet har du valt appen Microsoft Excel.<br>
  ![Exempel på hur du godkänner en app](media/approve.png)
4. Ett fönster för appen öppnas där du uppmanas att tilldela behörigheter till appen för att utföra olika åtgärder. Du måste välja **Godkänn** för att fortsätta.<br>
  ![Exempel på hur du godkänner appbehörigheter](media/approve-app-permissions.png)
5. Efter en stund visas ett bekräftelsemeddelande om att appen har godkänts och är tillgänglig i IT-administratörskonsolen.

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Publicera och synkronisera en verksamhetsspecifik app från Google Play for Work-butiken

1. Gå till Google Play-utvecklarkonsolen [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work. Om du loggar in för första gången måste du registrera dig och betala en avgift för att bli medlem i Google-utvecklarprogrammet.
3. I konsolen väljer du **Lägg till nytt program**.
4. Du kan överföra och tillhandahålla information om din app på samma sätt som du publicerar en app i Google Play-butiken. Men du måste välja inställningen **Only make this application available to my organization(Gör det här programmet tillgängligt endast för min organisation) (<*organisationsnamn*>)** som visas nedan.<br>
  ![Alternativ för att endast göra appen tillgänglig för din organisation](media/restrict.png)<br>
Detta säkerställer att appen endast är tillgänglig för din organisation och inte är tillgänglig i den offentliga Google Play-butiken.
Mer information om hur du överför och publicerar Android-appar finns i [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469) (Hjälp med Google-utvecklarkonsolen).
5. När du har publicerat din app går du till [Google Play for Work store](https://play.google.com/work) (Google Play for Work-butiken). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.
6. Kontrollera att du kan se appen som du har publicerat i noden **appar** i butiken. Notera att den måste ha godkänts automatiskt för att synkroniseras med Intune.

## <a name="assign-an-android-for-work-app"></a>Tilldela en Android for Work-app

Om du har godkänt en app från butiken, men den ännu inte visas i noden **Licensierade appar** i arbetsbelastningen **Mobilappar**, kan du framtvinga en omedelbar synkronisering genom att göra följande:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.
4. Välj **Installation** > **Android for Work** i arbetsbelastningen **Mobilappar**.
5. På bladet Android for Work väljer du **Synkronisera nu**.
6. Sidan visar även tid och status för den senaste synkroniseringen.

När appen visas i noden **Licensierade appar** i arbetsbelastningen **Mobilappar** kan du [tilldela den på samma sätt som du gör med andra appar](/intune-azure/manage-apps/deploy-apps). Du kan endast tilldela appen till grupper av användare.

När du har tilldelat appen kommer den att installeras på de enheter du har valt. Användaren av enheten behöver inte godkänna installationen.

## <a name="manage-app-permissions"></a>Hantera programbehörigheter
Android for Work kräver att du godkänner appar i Googles hanterade Play-webbkonsol, innan de synkroniseras till Intune and tilldelas till användarna.  Eftersom Android for Work låter dig distribuera dessa appar till användarnas enheter tyst och automatiskt måste du acceptera appens behörigheter för alla användare.  Slutanvändare kan inte se några programbehörigheter när de installerar så det är viktigt att du har läst och förstått dessa behörigheter.

När apputvecklare publicerar en ny version av appen med uppdaterade behörigheter tillåts de inte automatiskt, även om du har godkänt tidigare behörigheter. Enheter som kör den gamla versionen av programmet kan fortfarande använda det, men appen uppgraderas inte förrän de nya behörigheterna har godkänts. Enheter utan appen kan inte installera den förrän du har godkänt dess nya behörigheter.

### <a name="how-to-update-app-permissions"></a>Så här uppdaterar du programbehörigheter

Du bör regelbundet besöker konsolen Google Play för att söka efter nya behörigheter. Om du tilldelar en app och noterar att den inte installeras på enheterna, söker du efter nya behörigheter med följande steg:

1. Besök http://play.google.com/work
2. Logga in med det Google-konto som du använde för att publicera och godkänna apparna.
3. Besök fliken **uppdateringar** för att se om några appar kräver en uppdatering.  Alla appar i listan kräver nya behörigheter och kan inte tilldelas utan dessa.  

