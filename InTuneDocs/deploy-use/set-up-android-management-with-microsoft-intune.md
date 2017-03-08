---
title: Konfigurera Android-hantering | Microsoft Docs
description: "Aktivera hantering av mobila enheter (MDM) för Android- och KNOX Standard-enheter med Microsoft Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbe5cad1-3e0d-41a9-966b-738156089700
ms.reviewer: lacranda
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6b99854e17e00a0dd0f91fa82fd1b79d1dfe5663
ms.openlocfilehash: 8e2588e2bb0537877f0164bc996fa973f25ea4dd
ms.lasthandoff: 02/18/2017


---

# <a name="set-up-android-device-management"></a>Konfigurera Android-enhetshantering

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Som Intune-administratör kan du aktivera hanteringen av Android-enheter, inklusive Samsung Knox Standard-enheter, från företagsportalen. Användarna kan sedan registrera sina enheter med hjälp av företagsportalappen som finns på Google Play.

Som standard tillåts Android-enheter registreras i Intune. Om du vill blockera Android-enheter från registrering loggar du in på [administrationsportalen för Microsoft Intune](http://manage.microsoft.com) med dina autentiseringsuppgifter som administratör. Välj **Admin** > **Hantering av mobila enheter** > **Registreringsregler** och avmarkera kryssrutan	**Tillåt Android-enheter**.

1.  **Konfigurera Intune**<br>
    Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [utfärdare av mobilenhetshantering](prerequisites-for-enrollment.md#step-2-set-mdm-authority) och genom att konfigurera MDM.

2.  **Android-registrering är aktiverat**<br>
    Inga ytterligare konfigurationer i Intune-konsolen behövs för att aktivera registrering av mobila enheter för Android.

3.  **Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurser.**

    Registreringsinstruktioner för slutanvändare finns i [Registrera din Android-enhet i Intune](../enduser/enroll-your-device-in-intune-android.md). Registreringsprocessen förklarar för användarna vad de kan förvänta sig och vad IT-administratörer kan och inte kan se på deras enheter.

    Information om andra slutanvändaraktiviteter finns i de här artiklarna:
  - [Resurser om slutanvändarupplevelsen med Microsoft Intune](how-to-educate-your-end-users-about-microsoft-intune.md)
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

