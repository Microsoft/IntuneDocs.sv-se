---
title: Konfigurera Android for Work
description: "Aktivera hantering av mobila enheter (MDM) för Android for Work-enheter med Microsoft Intune."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: b3a961bdf754100f1a48258290a635add8e03053
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="enable-enrollment-of-android-for-work-devices"></a>Aktivera registrering av Android for Work-enheter

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Om du vill aktivera hantering av Android for Work-enheter så måste du lägga till en Android for Work-bindning i Intune. Om du vill registrera enheter som har stöd för Android for Work men som tidigare registrerades som vanliga Android-enheter, måste enheterna avregistreras och sedan registreras igen.

## <a name="add-android-for-work-binding-for-intune"></a>Lägg till Android for Work-bindning för Intune

1. **Konfigurera Intune**<br>
Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [utfärdare av mobilenhetshantering](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-8#enable-device-enrollment) och genom att konfigurera MDM.

2. **Konfigurera Android for Work-bindning**<br>
    Öppna [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) som Intune-administratör, gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **Android for Work** och klicka på **Konfigurera** för att öppna Google Plays webbplats för Android for Work. Det här kommer att öppna en ny flik i webbläsaren.

3. **Logga in på Google**<br>
   Logga in på Googles inloggningssida med det Google-konto som ska associeras med alla hanteringsuppgifter för Android for Work för den här klienten. Det här är det Google-konto som delas av organisationens IT-administratörer och som används för att hantera och publicera appar i Play for Work-konsolen.

4. **Ange organisationsinformation**<br>
   Ange företagets namn för **Organisationsnamn**. *Microsoft Intune* ska visas som **Enterprise mobility management (EMM)-provider**. Godkänn Android for Work-avtalet och klicka sedan på **Bekräfta**. Din begäran kommer att behandlas.

## <a name="specify-android-for-work-enrollment-settings"></a>Ange inställningar för registrering av Android for Work
   Android for Work stöds endast på vissa Android-enheter. Se Googles [Android for Work requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") (Krav för Android for Work).  Alla enheter som har stöd för Android for Work stöder även konventionell Android-hantering.  Intune gör det möjligt att ange hur enheter med stöd för Android for Work ska hanteras:

   - **Manage all devices as Android** (Hantera alla enheter som Android) – Alla Android-enheter, inklusive enheter som stöder Android for Work, registreras som konventionella Android-enheter.
   - **Manage all devices as Android for Work** (Hantera alla enheter som Android for Work) – Alla enheter som stöder Android for Work registreras som Android for Work-enheter. Alla Android-enheter som inte stöder Android for Work registreras som konventionella Android-enheter.
   - **Manage supported devices for users only in these user groups as Android for Work** (Hantera enheter som stöds endast för användare i dessa användargrupper som Android for Work) – Gör det möjligt att rikta Android for Work-hantering till en begränsad uppsättning användare. Endast medlemmar i de valda grupperna som registrerar en enhet som har stöd för Android for Work registreras som Android for Work-enheter. Alla andra registreras som Android-enheter. Detta är användbart vid pilottester av Android for Work.

## <a name="next-steps-for-android-for-work"></a>Nästa steg för Android for Work
När du har konfigurerat Android for Work-bindning och inställningar kan du göra följande:
- [Distribuera Android for Work-appar](android-for-work-apps.md)
- [Lägga till konfigurationsprinciper för Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="unbinding-your-android-for-work-administrative-account"></a>Ta bort bindning för ditt administratörskonto för Android for Work

Du kan inaktivera Android for Work-registrering och hantering. Klicka på **Ta bort bindning** i Intune-administrationskonsolen för att ta bort alla registrerade Android for Work-enheter från registreringen och ta bort relationen mellan Android for Work-kontot och Intune.

### <a name="how-to-unbind-an-android-for-work-account"></a>Så här tar du bort bindningen för ett Android for Work-konto

1. **Ta bort en Android for Work-bindning**<br>
    Öppna [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) som administratör, gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **Android for Work** och tryck på **Ta bort bindning**.

2. **Godkänn borttagningen av Android for Work-bindningen**<br>
  Klicka på **Ja** att ta bort bindningen och avregistrera alla Android for Work-enheter från Intune.
