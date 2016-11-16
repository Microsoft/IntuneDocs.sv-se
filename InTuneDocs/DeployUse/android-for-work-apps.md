---
title: Distribuera appar till Android for Work-enheter | Microsoft Intune
description: "Använd det här avsnittet för att synkronisera och sedan distribuera appar till Android for Work-enheter från Google Play for Work Store."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 32bded5047b1a08738418e3e36382eeae1a5f3b4
ms.openlocfilehash: f3b7c3a07ef3530805f4f951bcdb99cc5f7eb93d


---

# Så distribuerar du appar till Android for Work-enheter med Intune

Du distribuerar appar till Android for Work-enheter på ett annat sätt än du distribuerar dem till vanliga Android-enheter. Alla appar som du installerar för Android for Work kommer från Google Play for Work-butiken. Du kan logga in i butiken, bläddra efter de appar som du vill ha och godkänna dem.
Appen visas sedan i noden **Volyminköpsappar** i Intune-konsolen. Härifrån kan du hantera distributionen av apparna på samma sätt som du distribuerar andra appar.
Dessutom kan du distribuera dina egna verksamhetsspecifika (LOB)-appar som du har skapat. För att göra det måste du registrera dig för en Google-utvecklarkonto som låter dig att publicera appar på en privat plats i Google Play-butiken och sedan synkronisera dem med Intune.

## Innan du börjar

1. Kontrollera att du har konfigurerat Intune och Android for Work tillsammans i fliken **Admin** i Intune-konsolen.

## Synkronisera en app från Google Play for Work-butiken


1. Gå till [Google Play for Work store](https://play.google.com/work) (Google Play for Work-butiken). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.
2. Sök i butiken efter den app som du vill distribuera med hjälp av Intune.
3. På sidan för den app som du har valt trycker du på **Godkänn**. I det här exemplet har du valt appen Microsoft Excel.<br>
  ![Godkänn exempelappen](/intune/deploy-use/media/approve.png)
4. Ett fönster för appen öppnas där du uppmanas att tilldela behörigheter till appen för att utföra olika åtgärder. Du måste välja **Godkänn** för att fortsätta.<br>
  ![Exempel på att godkänna appbehörigheter](/intune/deploy-use/media/approve-app-permissions.png)
5. Efter en stund visas ett bekräftelsemeddelande om att appen har godkänts och är tillgänglig i IT-administratörskonsolen. 

## Publicera och synkronisera en verksamhetsspecifik app från Google Play for Work-butiken 

1. Gå till Google Play-utvecklarkonsolen [play.google.com/apps/publish](play.google.com/apps/publish).
2. Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work. Om du loggar in för första gången måste du registrera dig och betala en avgift för att bli medlem i Google-utvecklarprogrammet.
3. I konsolen väljer du **Lägg till nytt program**.
4. Du kan överföra och tillhandahålla information om din app på samma sätt som du publicerar en app i Google Play-butiken. Men du måste välja inställningen *Only make this application available to my organization*(Gör det här programmet tillgängligt endast för min organisation) (<*organisationsnamn*>)** som visas nedan.<br>
  ![Alternativet för att endast göra appen tillgänglig för din organisation](/intune/deploy-use/media/restrict.png)<br>
Detta säkerställer att appen endast är tillgänglig för din organisation och inte är tillgänglig i den offentliga Google Play-butiken.
Mer information om hur du överför och publicerar Android-appar finns i [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469) (Hjälp med Google-utvecklarkonsolen).
5. När du har publicerat din app går du till [Google Play for Work store](https://play.google.com/work) (Google Play for Work-butiken). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work. 
6. Kontrollera att du kan se appen som du har publicerat i noden **appar** i butiken. Notera att den måste ha godkänts automatiskt för att synkroniseras med Intune.

## Distribuera en Android for Work-app

Vanligtvis synkroniserar Intune med Google Play for Work-butiken två gånger om dagen. Om du har godkänt en app från butiken men den ännu inte visas i noden **Volyminköpta appar** i arbetsytan **Appar** kan du framtvinga en omedelbar synkronisering genom att göra följande:

1. I [Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Admin** > **Hantering av mobila enheter** > **Android for Work**.
2. På sidan **Android for Work Mobile Device Management Setup** (Konfiguration av hantering av mobila enheter med Android for Work) väljer **Synkronisera nu**.
3. Sidan visar även tid och status för den senaste synkroniseringen.

När appen visas i noden **Volyminköpta appar** i arbetsytan **appar** kan du [deploy it just like you would any other app](deploy-apps-in-microsoft-intune.md) (distribuera den på samma sätt som andra appar). Du kan endast distribuera appen till grupper av användare. För närvarande kan du bara välja åtgärderna **Nödvändig** och **Avinstallera**. Från oktober 2016 kommer vi börja lägga till distributionsåtgärden **Tillgänglig** till nya klienter. 

När du har distribuerat appen kommer den att installeras på de enheter du angett. Användaren av enheten kommer inte att bli ombedd att godkänna installationen.



<!--HONumber=Oct16_HO2-->

