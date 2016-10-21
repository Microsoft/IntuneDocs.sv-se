---
title: Konfigurera din prenumeration med Lookout MTP | Microsoft Intune
description: "Detta avsnitt tillhandahåller information om hur du konfigurerar Lookout MTP."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2196ff03975df1f8969e1522f7af459343694d
ms.openlocfilehash: 530a34c7c75a4fa73cbb62873e2d28883b91b57e


---

# Konfigurera din prenumeration för Lookout mobilt skydd
För att göra din prenumeration redo för Lookout MTP-tjänsten behöver Lookout-supporten (enterprisesupport@lookout.com) följande information om din Azure Active Directory (AD Azure)-prenumeration. 

* **Azure AD-klient-ID**
* **Azure AD-gruppobjekt-ID** för **fullständig** Lookout MTP-konsolåtkomst
* **Azure AD-gruppobjekt-ID** för **begränsad** Lookout MTP-konsolåtkomst (valfritt)

Använd det följande avsnittet för att samla in den information du måste förse Lookout-supportteamet med.  

## Hämta din Azure AD-information
### Azure AD-klient-ID
Logga in på [Azure AD-hanteringsportalen](https://manage.windowsazure.com) och välj din prenumeration. 

![skärmbild av Azure AD-sidan som visar namnet på klienten](../media/mtp/aad_tenant_name.png) När du väljer namnet på din prenumeration kommer URL:en som skapas att innehålla ditt prenumerations-ID.  Om du har problem med att hitta ditt prenumerations-ID kan du läsa den här [Microsoft support-artikeln](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) och få hjälp.   
### Hämta din Azure AD-grupp-ID
Lookout MTP-konsolen stöder två åtkomstnivåer:  
* **Fullständig åtkomst:** Azure AD-administratören kan skapa en grupp för användare som kommer att ha fullständig åtkomst och de kan även skapa en grupp med användare som har begränsad tillgång.  Endast användare i dessa grupper kommer att kunna logga in till **Lookout MTP-konsolen**.
* **Begränsad åtkomst:** Användarna i den här gruppen kommer inte ha åtkomst till ett flertal konfigurations- och registreringsrelaterade moduler i Lookout MTP-konsolen, och ha skrivskyddad åtkomst till **Säkerhetsprincip**-modulen i Lookout MTP-konsolen.  

Mer information om behörigheterna finner du i [den här artikeln](https://personal.support.lookout.com/hc/en-us/articles/114094105653) på webbplatsen Lookout.

**Grupp-objekt-ID:t** finns på **egenskapssidan** för gruppen i **Azure AD-hanteringskonsolen**.

![skärmbild av egenskapssidan med Grupp-ID-fältet markerat](../media/mtp/aad_group_object_id.png)

Kontakta Lookout-supporten (e-post: enterprisesupport@lookout.com) när du har samlat in den här informationen.

Lookout-supporten kommer att samarbeta med din primära kontakt för att publicera din prenumeration och skapa ditt företagskonto för Lookout MTP med hjälp av informationen som du samlat in.


## Konfigurera din prenumeration med Lookout MTP
### Steg ett: Konfigurera MTP
När Lookout-supporten har skapat ditt företagskonto för Lookout MTP kan du logga in i Lookout MTP-konsolen.   Ett e-postmeddelande från Lookout skickas till den primära kontakten för ditt företag med en länk till inloggnings-url-adressen: https://aad.lookout.com/les?action=consent

Du måste använda ett användarkonto med Azure AD-rollen Global administratör när du loggar in i Lookout MTP-konsolen första gången eftersom Lookout MTP kräver detta för att registrera din Azure AD-klient.   Efterföljande inloggningar kräver inte att användaren har Azure AD-behörighet på den här nivån.  När du loggar in för första gången visas en sida för godkännande av villkor. Välj **Acceptera** för att slutföra registreringen.

![skärmbild som visar inloggningssidan första gången användaren loggar in i Lookout MTP-konsolen](../media/mtp/lookout_mtp_initial_login.png) När du har accepterat och godkänt villkoren omdirigeras du till Lookout MTP-konsolen. Efterföljande inloggningar efter den första registreringen kan göras med hjälp av URL-adressen: https://aad.lookout.com

Se [troubleshooting article](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration) (felsökningsartikeln)  om du får problem med inloggningen.

Nästa steg beskriver de uppgifter som du måste utföra för att slutföra konfigurationen av Lookout MTP i [Lookout MTP Console](https://aad.lookout.com) (Lookout MTP-konsolen).

### Steg 2: Konfigurera Intune Connector

1.  I Lookout MTP-konsolen går du till **System**-modulen, väljer **Kopplingar** och sedan **Intune**.

  ![skärmbild som visar Lookout MTP-konsolen med fliken för anslutningar öppen och alternativet Intune markerat](../media/mtp/lookout_mtp_setup-intune-connector.png)

2.  Konfigurera pulsslagsfrekvensen i minuter i alternativen för anslutningsinställningar.  Intune-anslutningen är nu klar.  

  ![skärmbild av fliken för anslutningsinställningar som visar hur pulsslagsfrekvensen konfigurerats](../media/mtp/lookout-mtp-connection-settings.png)

### Steg tre: Konfigurera registrering av grupper
För alternativet **Enrollment Management** (Registreringshantering), ange ett antal användare vars enheter ska registreras med Lookout. Det är rekommenderat att börja med en liten grupp användare för att testa och bekanta dig med hur integrationen fungerar.  När du är nöjd med testresultaten kan du utöka registreringen till andra grupper av användare.

Ange först en Azure AD-säkerhetsgrupp som du tycker skulle vara en bra grupp användare att registrera i Lookout MTP för att komma igång med registreringsgrupper. När gruppen har skapats i Azure AD går du till alternativet **Enrollment Management** (Registreringshantering) i Lookout MTP-konsolen och lägger till Azure AD-säkerhetsgruppen **Visningsnamn** för registrering.

När en användare finns i en grupp för registrering registreras alla dennes enheter som identifieras och har stöd i Azure AD, och dessa enheter kan aktiveras i Lookout MTP.  Första gången de öppnar Lookout for Work-appen på en enhet som stöds så aktiveras enheten i Lookout MTP.
![skärmbild som visar sidan registrering av Intune-anslutning](../media/mtp/lookout-mtp-enrollment.png)

Det rekommenderas att använda de inställningar som är standard (fem minuter) för tidsintervallerna då nya enheter eftersöks.

>[!IMPORTANT]
> Visningsnamnet är skiftlägeskänslig.  Använd det **Visningsnamn** som visas på sidan **Egenskaper** i säkerhetsgruppen i Azure-portalen. Observera i bilden nedan att visningsnamnet på sidan **Egenskaper** i säkerhetsgruppen är en kamelnotation.  Rubriken är dock helt skriven i gemener och bör inte användas för att komma in i Lookout MTP-konsolen.
>![skärmbild av egenskaper-sidan för Azure Active Directory-tjänsten i Azure-portalen](../media/mtp/aad-group-display-name.png)

Den aktuella versionen har följande begränsningar:  
* Det finns ingen validering av visningsnamn för grupper.  Se till att använda värdet i fältet **VISNINGSNAMN** för Azure AD-säkerhetsgruppen som visas i Azure-portalen.
* Det finns inte stöd för att skapa grupper i grupper för närvarande.  Specificerade Azure AD-säkerhetsgrupper får endast innehålla användare och inte kapslade grupper.


### Steg fyra: Konfigurera programtillståndssynkronisering
För alternativet **Synkronisering av programtillstånd** anger du vilken typ av data som ska skickas till Intune.  Du måste för närvarande aktivera både enhetsstatus och hotstatus för att Intune-Lookout-integrationen ska fungera korrekt.  De här verktygen är aktiverade som standard.
### Steg fem: Konfigurera information om e-postmottagare av felrapporter
Ange den e-postadress som ska ta emot felrapporter i alternativet **Error Management** (Felhantering).

![skärmbild som visar sidan för felhantering för Intune Connector](../media/mtp/lookout-mtp-connector-error-notifications.png)

### Steg sex: Konfigurera e-postaviseringar
Logga in i [Lookout MTP-konsolen](https://aad.lookout.com) med det användarkonto som ska ta emot meddelanden om du vill ta emot e-postaviseringar för hot. Under fliken **Inställningar** i **System**-modulen väljer du den önskade typen av meddelanden och sätter dem på **PÅ**. Spara ändringarna.

![skärmbild som visar sidan för inställningar där användarkontot visas](../media/mtp/lookout-mtp-email-notifications.png) Om du inte längre vill ta emot e-postaviseringar väljer du alternativet **AV** för meddelanden och sparar ändringarna.
### Steg sju: Konfigurera hotklassificering
Lookout MTP klassificerar olika typer av mobila hot . [Lookout MTP-hotklassificeringar](http://personal.support.lookout.com/hc/en-us/articles/114094130693) är kopplade till standardrisknivåer. Dessa kan ändras när som helst för att passa företagets krav.

![skärmbild av sidan för principer som visar hot och klassificeringar](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Risknivåerna som anges här är en viktig aspekt av MTP eftersom Intune-integrationen beräknar enhetens efterlevnad enligt dessa risknivåer vid körning. Intune-administratören anger med andra ord en regel i principen för att identifiera att en enhet är icke-kompatibel om den har ett aktivt hot med miniminivån: hög, medel eller låg. Principen för hotklassificering i MTP styr direkt efterlevnadsberäkningen för enheten i Intune.

## Bevakar registreringen
När installationen är klar börjar Lookout MTP avsöka Azure AD efter enheter som motsvarar de angivna registreringsgrupperna.  Du hittar information om de enheter som registrerats i modulen Enheter.  Den första statusen för enheterna är ”väntar”.  Enhetens status ändras när Lookout for Work-appen har installerats, öppnats och aktiverats på enheten.  Mer information om hur du skickar Lookout for work-appen till enheten finner du i artikeln [Configure and deploy Lookout for work apps](configure-and-deploy-lookout-for-work-apps.md) (Konfigurera och distribuera Lookout for work-appar).
## Nästa steg
[Aktivera anslutning till Lookout MTP i Intune](enable-lookout-mtp-connection-in-intune.md)



<!--HONumber=Sep16_HO3-->


