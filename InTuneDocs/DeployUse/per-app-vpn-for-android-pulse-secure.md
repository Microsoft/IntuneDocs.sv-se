---
title: "Per app-VPN för Android med Pulse Secure | Microsoft Intune"
description: "Du kan skapa en VPN-profil per app för Android-enheter som hanteras av Intune."
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 52d9d2ad912de7bc775cde2c40c8de27a09ba2af
ms.openlocfilehash: d37630d2aaf4a260acf98a57aa2d38c95711f12b


---

# Använda en anpassad princip för att skapa en VPN-profil per app för Android-enheter

Du kan skapa en VPN-profil per app för Android-enheter som hanteras av Intune. Först måste du skapa en VPN-profil som används för anslutningstypen Pulse Secure och en princip för anpassad konfiguration som kopplar den här profilen till specifika appar. När du distribuerar dessa principer till din Android-enhet eller användargrupperna öppnar du en av de angivna apparna på dessa enheter så öppnas en VPN-anslutning för appen.

> [OBS]
> 
> Endast anslutningstypen Pulse Secure stöds för den här profilen.


### Steg 1: Skapa en VPN-profil

1. I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) klickar du på **Princip** > **Lägg till princip**.
2. Välj en mall för den nya principen genom att expandera **Android**, och välj sedan **VPN-profil (Android 4 och senare)**.

3. I mallen väljer du **Pulse Secure** som **Anslutningstyp**.
4. Slutför och spara VPN-profilen. Mer information om VPN-profiler finns i [VPN-anslutningar](vpn-connections-in-microsoft-intune.md).

> [!NOTE]
Anteckna VPN-profilnamnet för användning i nästa steg. Till exempel **MyAppVpnProfile**.

### Steg 2: Skapa en princip för anpassad konfigurering

   1. I Intune-administrationskonsolen väljer du **Princip** -> **Lägg till princip** -> **Android** -> **Anpassad konfiguration** -> **Skapa princip**.
   2. Ange ett namn för principen.
   3. Klicka på **Lägg till** under **OMA-URI-inställningar**.
   4. Ange ett namn på inställningen.
   5. Ange **Sträng** för **Datatyp**.
   6. för **OMA-URI** anger du strängen: **./Vendor/MSFT/VPN/Profile/*Namn*/PackageList**, där *Namn* är det VPN-profilnamn som du antecknade i steg 1. I vårt exempel skulle strängen vara **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
   7.   Under **Värde** anger du en semikolonavgränsad lista över paket som ska associeras med profilen.  Om du exempelvis vill att Excel och webbläsaren Google Chrome ska använda VPN-anslutningen anger du: **com.microsoft.office.excel;com.android.chrome**.


   ![Exempel på VPN-anpassad princip per app för Android](..\media\android_per_app_vpn_oma_uri.png)
#### Ange applistan som svartlistad eller vitlistad (valfritt)
Du kan ange att din lista över appar *inte* kommer att kunna använda VPN-anslutning med hjälp av värdet **SVARTLISTAT**.  Alla andra appar ansluter via VPN.

Du kan också ange att *endast* angivna appar kommer att kunna använda VPN-anslutning med hjälp av värdet **VITLISTAT**.


1.  Klicka på **Lägg till** under OMA-URI-inställningar.
2.  Ange ett namn på inställningen.
3.  Ange **Sträng** för **Datatyp**.
4.  För **OMA-URI** anger du följande sträng: **./Vendor/MSFT/VPN/Profile/*Namn*/Läge**, där *Namn* är den VPN-profil som du antecknade i steg 1. I vårt exempel skulle strängen vara **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
5.  Under **Värde** anger du **SVARTLISTAT** eller **VITLISTAT**.



### Steg 3: Distribuera båda principerna

Du måste distribuera *båda* principerna för *samma* Intune-grupp.

   1.  Välj den princip på arbetsytan **Princip** som du vill distribuera och klicka sedan på **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** :

    -   **Om du vill distribuera principen** markerar du en eller flera grupper som du vill distribuera principen till och klickar sedan på **Lägg till** &gt; **OK**.

    -   **Om du vill stänga dialogrutan utan att distribuera den** – Klicka på **Avbryt**.

En statssammanfattning och varningar på sidan **Översikt** på arbetsytan **Principer** identifierar problem med principer som kräver din uppmärksamhet. Dessutom visas en statussammanfattning på arbetsytan Instrumentpanel.



<!--HONumber=Aug16_HO1-->


