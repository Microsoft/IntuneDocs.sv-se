---
# required metadata

title: Dags att registrera enheter i Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Dags att registrera enheter i Microsoft Intune
Om du vill låta anställda registrera mobila enheter (inklusive Android, iOS och Windows Phone och Windows-datorer) med Intune måste du aktivera registrering av enheter. Om du vill tillåta registrering måste du ange en utfärdare för hantering av mobila enheter, konfigurera Intunes företagsportal, tilldela licenser och aktivera registrering för enhetsplattformen.

## <a name="BKMK_Set_MDM_Authority"></a>Ange auktoritet för hantering av mobila enheter
Utfärdaren för hantering av mobila enheter definierar den hanteringstjänst som har behörighet att hantera en uppsättning enheter. Alternativ för MDM-utfärdare kan vara själva Intune och Configuration Manager med Intune. Om Configuration Manager anges som utfärdare för hanteringen kan inga andra tjänster användas för hantering av mobila enheter.

>[!IMPORTANT]
> Överväg noggrant om du vill hantera mobila enheter endast med hjälp av Intune (onlinetjänst) eller System Center Configuration Manager med Intune (lokal programvarulösning i samband med onlinetjänsten). När du har angivit utfärdare för hantering av mobila enheter går det inte att ändra den.



1.  I [Microsoft Intune-administratörskonsolen](http://manage.microsoft.com) klickar du på **Admin** &gt; **Hantering av mobila enheter**

2.  Klicka på **Ange auktoritet för hantering av mobila enheter** i **Uppgiftslistan**. Dialogrutan **Ange MDM-auktoritet** öppnas.

    ![Dialogrutan Ange MDM-auktoritet](../media/intune-mdm-authority.png)

3.  Intune begär bekräftelse på att du vill ha Intune som MDM-utfärdare. Markera kryssrutan och klicka sedan på **Ja** om du vill använda Microsoft Intune för att hantera mobila enheter.

## Konfigurera Intune-företagsportalen och tilldela licenser
Med Intune-företagsportalen kan användare få åtkomst till företagsresurser som appar, hitta supportinformation och registrera och avregistrera enheter. Innan du registrerar enheter bör du [konfigurera företagsportalen](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-7). Du måste också [tilldela användarlicenser](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-4) för att ge åtkomst till Intune.

## Konfigurera enhetshantering
När du har konfigurerat MDM-utfärdare måste du konfigurera enhetshantering för de operativsystem som organisationen vill ha stöd för. Stegen för att konfigurera enhetshantering varierar beroende på operativsystem. I Android OS krävs till exempel inte att du gör någonting i Intune-administratörskonsolen. Å andra sidan kräver Windows och iOS en förtroenderelation mellan enheter och Intune för att tillåta hantering.

> [!div class="op_single_selector"]
- [Konfigurera Android-hantering med Microsoft Intune](set-up-android-management-with-microsoft-intune.md)
- [Set up iOS and Mac management with Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Konfigurera hantering av Windows Phone med Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md)
- [Konfigurera Windows-enhetshantering med Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md)

Du kan också:
 - Använda [kontot för enhetsregistreringshanterare](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) för att registrera flera enheter
 - [Ange företagsägda enheter med hjälp av IMEI-nummer](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) för att registrera enheter och målprincip


<!--HONumber=May16_HO2-->


