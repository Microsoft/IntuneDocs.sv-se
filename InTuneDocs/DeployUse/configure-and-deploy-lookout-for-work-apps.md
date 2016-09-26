---
title: Distribuera Lookout for work-appen | Microsoft Intune
description: "Konfigurera och distribuera Lookout for work-appar för Android."
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9c2ffb5fe497d56d8250fe3dec7db606c2067a1c
ms.openlocfilehash: c43104ff199e1800bfded35154d2be0cfd0c40f3


---

# Konfigurera och distribuera Lookout for work-appar
I den här versionen stöds Lookout for work-appen på Android-enheter med 4.1 och senare.
## Android
Det här avsnittet beskriver hur du konfigurerar och distribuerar Lookout for work-appen för Android-enheter som är registrerad i Intune.  
* Steg ett: I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) går du till **Appar** och väljer **Lägg till appar**.   
* Steg två: På utgivarens **Programvaruinstallation**-sida väljer du **Extern länk**, och anger följande URL: https://play.google.com/store/apps/details?id=com.lookout.enterprise
>[!NOTE]
>Klicka inte på rutan för att kräva en hanterad webbläsare.

* Steg tre: Fyll i följande på sidan **Programvarubeskrivning**:
  * **Utgivare:** Lookout Mobile Security
  * **Namn:** Lookout for Work
  * **Beskrivning:** Lookout tillhandahåller det bästa skyddet mot mobila hot för att skydda din enhet. När appen Lookout är installerad på enheten skyddar den din enhet från hot och varnar dig och din företagsadministratör om några hittas.
  * **Kategori:** Datorhantering
* Steg fyra: Vid slutförande visas meddelandet **Dataöverföringen till Microsoft Intune har slutförts**.

När du klickar på **Appar** i Intune-konsolen kommer du nu se Lookout for Work-appen i listan ![skärmbild av Intune-administratörskonsolens appar som visar Lookout for work-appar i listan](../media/mtp/lookout-app-listed-intune-console.png)

Steg fem: Nu kan Intune distribuera appen Lookout for work för Android.   Du kan distribuera appen till användare genom att välja Lookout for Work-appen som visas på skärmbilden ovan och markera **Hantera distribuering**.

Du måste markera samma användare som har lagts till i alternativet Registreringshantering i Lookout MTP-konsolen.  Se steg tre i [configure your subscription with Lookout MTP section](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) (avsnittet konfigurera din prenumeration med Lookout MTP) för information om att lägga till användargrupper i Lookout MTP.
>[!IMPORTANT]
> Appdistributionsguiden för Intune kan inte använda Azure AD-användargrupper utan använder istället Intune-användargrupper. Därför måste du skapa en Intune-användargrupp baserat på Azure AD-användargruppen som har registrerats i Lookout MTP-konsolen enligt beskrivningarna i [den här](plan-your-user-and-device-groups.md)artikeln.

Steg sex: Välj alternativet **Nödvändig installation** för att kräva att Lookout-appen installeras på användarens enhet.

### Enhetsaktivering
Med alternativet **Nödvändig installation** valt för distribution kommer Intune att skicka Lookout for work-appen till enheten.   

När användaren öppnar Lookout for Work på enheten uppmanas de att aktivera appen och att välja alternativet att logga in med Azure Active Directory. En detaljerad genomgång som visar vad slutanvändaren ska göra finns i följande avsnitt:

* [Du uppmanas att installera Lookout for Work på din Android-enhet](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Du måste åtgärda ett hot som Lookout for Work har hittat på din Android-enhet](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## Nästa steg
* [Aktivera regeln för skydd mot enhetshot i policyn för efterlevnad](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Sep16_HO2-->


