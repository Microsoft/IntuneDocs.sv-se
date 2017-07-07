---
title: "Det verkar som om din Android-enhet är krypterad"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 269ad7968242f8f5ce7095c9c73347987675e846
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>Din Android-enhet verkar vara krypterad, men inte enligt företagsportalen

När du krypterar en enhet kodar du informationen på enheten med hjälp av en hemlig nyckel som bara du känner till. Det hindrar obehöriga från att kunna komma åt informationen. Organisationen kräver att du krypterar din Android-enhet för att skydda innan du kommer åt företagsfiler, -e-post eller -data som ett steg mot att se till att informationen är skyddad.

## <a name="common-issues"></a>Vanliga problem

Nyare versioner av Android-, särskilt från och med v7.0, kräver ett startlösenord för att se till att enheten är helt krypterad. Olika enhetstillverkare har olika beskrivningar och platser för startlösenord. I de flesta fall kallas detta ”säker start”. 

## <a name="solutions"></a>Lösningar

### <a name="add-a-startup-pin"></a>Lägga till en start PIN-kod

På vissa Android-enheter måste du skapa en start PIN-kod för att se till att enheten är säkrad. Det finns flera versioner av Android från många olika tillverkare. Du kan försöka att åtgärda problemet genom att hitta en plats i inställningsappen där det här alternativet kan aktiveras. Till exempel i Samsung Galaxy S7 aktiverar du säker start genom att gå till **Inställningar** > **Låsskärm och säkerhet** > **Säker start**.  

### <a name="downgrade-your-version-of-android"></a>Nedgradera din version av Android
Om enheten erbjuder möjligheten att nedgradera till Android 6.0+ ska du göra det. Det finns en risk för dataförlust om du nedgraderar din enhet. I annat fall rekommenderar vi att du kontaktar IT-administratören för att lösa problemet. Kontaktinformation för IT-administratören finns på [företagsportalens webbplats](http://portal.manage.microsoft.com).

## <a name="specific-manufacturer-issues"></a>Problem med vissa tillverkare

Vissa Android-enheter med version 7.0 + krypterar data på ett sätt som strider mot vissa standarder för Android-plattformen. Dessa enheter kan se ut som att de är krypterade, men Intune känner igen de metoder som används för att göra enhetens information tillgänglig för obehöriga användare som har fysisk åtkomst till enheten.

> [!Note]
> Microsoft arbetar med tillverkare för att åtgärda eventuella problem som vi påträffar under testning eller som användarna rapporterar till oss. Vi kommer att uppdatera den här artikeln när ny information är tillgänglig. 

## <a name="known-devices"></a>Kända enheter

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>Kända enheter som kan uppdateras för att åtgärda problemet

Om du har någon av följande enheter kan det här problemet uppstå om du inte har uppdaterat enheten till den senaste versionen av Android. Du kan installera uppdateringar för dessa enheter genom att gå till **Inställningar** > **Uppdatera**. 

- [Huawei Honor 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [Huawei P9](http://consumer.huawei.com/mobile-phones/p9/index.html)

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>Kända enheter som inte kan uppdateras för att åtgärda problemet

- [Huawei Mate 8](http://consumer.huawei.com/en/mobile-phones/mate8/index.htm)
- [Xiaomi Mi-telefoner](https://xiaomi-mi.com/mi-smartphones/)
