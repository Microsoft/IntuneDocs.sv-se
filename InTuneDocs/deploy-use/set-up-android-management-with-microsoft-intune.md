---
title: Konfigurera Android-hantering | Microsoft Docs
description: "Aktivera hantering av mobila enheter (MDM) för Android- och KNOX Standard-enheter med Microsoft Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbe5cad1-3e0d-41a9-966b-738156089700
ms.reviewer: lacranda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26ddc03985ab8a4959a1d2c9a47e77f042ab9310
ms.openlocfilehash: 6b74c09c37970429d3eaa571db655854d592a2fe


---

# <a name="set-up-android-device-management"></a>Konfigurera Android-enhetshantering

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Som Intune-administratör kan du aktivera hanteringen av Android-enheter, inklusive Samsung Knox Standard-enheter, från företagsportalen. Användarna kan sedan registrera sina enheter med hjälp av företagsportalappen som finns på Google Play.

1.  **Konfigurera Intune**<br>
    Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [utfärdare av mobilenhetshantering](prerequisites-for-enrollment.md#step-2-set-mdm-authority) och genom att konfigurera MDM.

2.  **Android-registrering är aktiverat**<br>
    Inga ytterligare konfigurationer i Intune-konsolen behövs för att aktivera registrering av mobila enheter för Android.

3.  **Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurser.**

    Registreringsinstruktioner för slutanvändare finns i [Registrera din Android-enhet i Intune](../enduser/enroll-your-device-in-intune-android.md). Registreringsprocessen förklarar för användarna vad de kan förvänta sig och vad IT-administratörer kan och inte kan se på deras enheter.

    Information om andra slutanvändaraktiviteter finns i de här artiklarna:
  - [Resurser om slutanvändarupplevelsen med Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
  - [Vägledning för slutanvändare för Android-enheter](../enduser/using-your-android-device-with-intune.md)

På grund av avsaknad av Google Play-butik i Kina måste Android-enheter hämta Företagsportalen från kinesiska appmarknadsplatser. Företagsportalappen för Android blir tillgänglig för hämtning på följande platser:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

Företagsportalappen för Android använder Google Play-tjänster för att kommunicera med Microsoft Intune-tjänsten. Eftersom Google Play-tjänster ännu inte är tillgängliga i Kina, kan utförandet av någon av följande aktiviteter ta upp till 8 timmar att slutföra. 

|Administrationskonsolen för Intune| Intune-företagsportalsapp för Android |Intune-företagsportalens webbplats|   
|---|---|---|
|Fullständig rensning| Ta bort en fjärransluten enhet| Ta bort enhet (lokal och fjärransluten)|
|Selektiv rensning| Återställ enhet| Återställ enhet|
|Nya eller uppdaterade appdistributioner| Installera tillgängliga branschspecifika appar| Återställning av enhetens lösenord|
|Fjärrlåsning|||
|Återställning av lösenord|||

### <a name="see-also"></a>Se även
[Krav för att registrera enheter i Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Jan17_HO1-->


