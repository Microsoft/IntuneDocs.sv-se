---
title: Det verkar som om din Android-enhet är krypterad | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55935b2f69f9573d8df5ea5ca32fb4587c652b26
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389470"
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>Din Android-enhet verkar vara krypterad, men inte enligt företagsportalen

När du krypterar en enhet kodar du informationen på den med hjälp av en hemlig nyckel som bara du känner till. Detta förhindrar att obehöriga användare kan komma åt enheten. Många organisationer kräver att deras användare krypterar sina Android-enheter innan de kan komma åt företagets filer, e-post eller data.

## <a name="common-issues"></a>Vanliga problem

Nyare versioner av Android-, särskilt från och med v7.0, kräver ett startlösenord för att se till att enheten är helt krypterad. Olika enhetstillverkare har olika beskrivningar och platser för startlösenord. Den här inställningen brukar kallas för ”Säker start”. 

## <a name="solutions"></a>Lösningar

### <a name="add-a-startup-pin"></a>Lägga till en start PIN-kod

På vissa Android-enheter måste du skapa en start-PIN-kod för att se till att enheten är skyddad. Det finns flera versioner av Android från många olika tillverkare. Du kan försöka att åtgärda problemet genom att hitta en plats i inställningsappen där det här alternativet kan aktiveras. Till exempel i Samsung Galaxy S7 aktiverar du säker start genom att gå till **Inställningar** > **Låsskärm och säkerhet** > **Säker start**.  

### <a name="encrypt-the-entire-device"></a>Kryptera hela enheten

Med vissa enheter kan du välja mellan att kryptera hela enheten eller bara det använda utrymmet. Välj helst att kryptera hela enheten och inte ”bara det använda utrymmet.” Om du redan har krypterat endast det använda utrymmet:

1. [Ta bort den här enheten från företagsportalen](unenroll-your-device-from-intune-android.md)
2. Dekryptera använt utrymme
3. Kryptera hela enheten
4. Omregistrera enheten

### <a name="downgrade-your-version-of-android"></a>Nedgradera din version av Android

Om enheten erbjuder möjligheten att nedgradera till Android 6.0+ ska du göra det. Det finns en risk för dataförlust om du nedgraderar din enhet. I annat fall rekommenderar vi att du kontaktar företagets support för att lösa problemet. Kontaktinformation till företagets support finns på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).

## <a name="specific-manufacturer-issues"></a>Problem med vissa tillverkare

På vissa Android-enheter med version 7.0 och senare krypteras data på ett sätt som strider mot vissa standarder för Android-plattformen. Det kan se ut som dessa enheter är krypterade även när de är helt nya. Intune identifierar dessa enheters krypteringsmetoder som osäkra metoder som utsätter informationen på enheten för risk. Den här risken handlar först och främst om angripare som har fysisk åtkomst till enheten.

> [!Note]
> Microsoft arbetar med tillverkare för att åtgärda eventuella problem som vi påträffar under testning eller som användarna rapporterar till oss. Vi uppdaterar den här artikeln när ny information är tillgänglig. 

## <a name="known-devices"></a>Kända enheter

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>Kända enheter som kan uppdateras för att åtgärda problemet

Om du inte har uppdaterat enheten till den senaste versionen av Android, går du till enhetens **inställningar** och välj **uppdatering**. Dessa enheter kan se ut som icke kompatibla förrän du har uppdaterat:  

- Huawei Honor 8
- Huawei P9

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>Kända enheter som inte kan uppdateras för att åtgärda problemet
Följande enheter visas alltid krypterad och kan inte användas för att komma åt företagets resurser. Om du vill komma åt företagets resurser, måste du använda en annan enhet.  

- Huawei Mate 8
- OPPO-enheter
- Vivo-enheter
- Xiaomi Mi-smartphones
