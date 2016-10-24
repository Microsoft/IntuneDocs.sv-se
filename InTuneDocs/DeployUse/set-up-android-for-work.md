---
title: Konfigurera Android for Work-hantering | Microsoft Intune
description: "Aktivera hantering av mobila enheter (MDM) för Android for Work-enheter med Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
translationtype: Human Translation
ms.sourcegitcommit: 519b66c94f3d056e060ed11e1a3d7d6d118a94fb
ms.openlocfilehash: 5f48303dd28627f961f8c2cfd38f8977354e2724


---

# Aktivera registrering av Android for Work-enheter

Om du vill aktivera hantering av Android for Work-enheter så måste du lägga till en Android for Work-bindning i Intune. Om du vill registrera enheter som har stöd för Android for Work men som tidigare var registrerade som vanliga Android-enheter, måste enheterna avregistreras och sedan registreras igen.

## Lägg till Android for Work-bindning för Intune

1. **Konfigurera Intune**<br>
Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [utfärdare av mobilenhetshantering](prerequisites-for-enrollment.md#set-mobile-device-management-authority) och genom att konfigurera MDM.

2. **Konfigurera Android for Work-bindning**<br>
    Öppna [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) som administratör, gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **Android for Work** och tryck på **Konfigurera** för att öppna Android for Work-webbplatsen på Google Play. Det här kommer att öppna en ny flik i webbläsaren.

3. **Logga in på Google**<br>
   Logga in på Googles inloggningssida med det Google-konto som ska associeras med alla hanteringsuppgifter för Android for Work för den här klienten. Detta kan vara ett Google-konto som delas mellan administratörerna som hanterar Intune. Det här är det Google-konto som används i din organisation för att hantera och publicera appar i Play for Work-konsolen.

4. **Ange organisationsinformation**<br>
   Ange företagets namn för **Organisationsnamn**. *Microsoft Intune* ska visas som **Enterprise mobility management (EMM)-provider**. Godkänn Android for Work-avtalet och klicka sedan på **Bekräfta**. Din begäran kommer att behandlas.

## Ange inställningar för registrering av Android for Work
   Android for Work stöds endast på vissa Android-enheter. Se Googles [Android for Work requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") (Krav för Android for Work).  Alla enheter som har stöd för Android for Work stöder även konventionell Android-hantering.  Intune låter dig ange hur enheter med stöd för Android for Work ska hanteras:

   - **Manage all devices as Android** (Hantera alla enheter som Android) – (Inaktiverat) Alla Android-enheter, inklusive enheter som stöder Android for Work, registreras som konventionella Android-enheter.
   - **Manage all devices as Android for Work** (Hantera alla enheter som Android for Work) – (Aktiverat) Alla enheter som stöder Android for Work registreras som Android for Work-enheter. Alla Android-enheter som inte stöder Android for Work registreras som konventionella Android-enheter.
   - **Manage supported devices for users only in these user groups as Android for Work** (Hantera enheter som stöds endast för användare i dessa användargrupper som Android for Work) – (Test) Låter dig rikta Android for Work-hantering till en begränsad uppsättning användare. Endast medlemmar i de valda grupperna som registrerar en enhet som har stöd för Android for Work registreras som Android for Work-enheter. Alla andra registreras som Android-enheter.

## Nästa steg för Android for Work
När du har konfigurerat Android for Work-bindning och inställningar kan du göra följande:
- [Distribuera Android for Work-appar](android-for-work-apps.md)
- [Lägg till konfigurationsprinciper för Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)

## Ta bort bindning för ditt administratörskonto för Android for Work

Du kan inaktivera Android for Work-registrering och hantering. Klicka på **Ta bort bindning** för att ta bort alla registrerade Android for Work-enheter från registreringen och ta bort relationen mellan Android for Work-kontot och Intune.

### Så här tar du bort bindningen för ett Android for Work-konto

1. **Ta bort en Android for Work-bindning**<br>
    Öppna [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) som administratör, gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **Android for Work** och tryck på **Ta bort bindning**.

2. **Godkänn borttagning av Android for Work-bindning**<br>
  Klicka på **Ja** att ta bort bindningen och avregistrera alla Android for Work-enheter från Intune.



<!--HONumber=Oct16_HO2-->


