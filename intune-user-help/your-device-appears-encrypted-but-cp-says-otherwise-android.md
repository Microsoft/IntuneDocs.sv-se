---
title: Det verkar som om din Android-enhet är krypterad | Microsoft Docs
description: Lös krypterings status i Företagsportal och Microsoft Intune App
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/14/2019
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
ms.openlocfilehash: caae22e59e8adb6952e9a69ff03c575ae4467b2d
ms.sourcegitcommit: 6a946a055a2014e00a4ca9d71986727a4ebbc777
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238981"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>Enheten är krypterad men appar säger annars

Om Företagsportal eller Microsoft Intunes appen säger att enheten inte är krypterad, men du är säker på att den är, kan du prova med stegen i den här artikeln.  

## <a name="add-a-startup-pin"></a>Lägga till en start PIN-kod

På vissa Android-enheter måste du skapa en start-PIN-kod för att se till att enheten är skyddad. Platsen för den här inställningen kommer att finnas i enhetens **inställnings** app. Namnet och platsen för inställningen kan variera. I Samsung Galaxy-S7 kallas inställningen till exempel **säker start**. Om du vill aktivera det och skapa ett lösen ord går du till **Inställningar** > **Lås skärmen och säkerhet** > **säker start**.  

## <a name="encrypt-the-entire-device"></a>Kryptera hela enheten

Det här avsnittet gäller endast för Företagsportal-appen. Med vissa enheter kan du välja mellan att kryptera hela enheten eller bara det använda utrymmet. Välj alternativet för att kryptera hela enheten. Om du har valt att bara kryptera det använda utrymmet:

1. [Ta bort den här enheten från företagsportalen](unenroll-your-device-from-intune-android.md).
2. Dekryptera använt utrymme.  
3. Kryptera hela enheten.  
4. Omregistrera enheten.  

## <a name="downgrade-your-version-of-android"></a>Nedgradera din version av Android

Det här avsnittet gäller endast för Företagsportal-appen. Om enheten ger dig alternativet att nedgradera till Android 6.0 och senare gör du det. Det finns en risk för dataförlust om du nedgraderar din enhet. I annat fall rekommenderar vi att du kontaktar företagets support för att lösa problemet. Leta upp kontaktuppgifter till företagets support på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="specific-manufacturer-issues"></a>Problem med vissa tillverkare

På vissa Android-enheter med version 7.0 och senare krypteras data på ett sätt som strider mot vissa standarder för Android-plattformen. Dessa krypterings metoder sätter i risk för enhets information. Därför stöds inte dessa enheter.

En icke-uttömmande lista över Android-enheter som stöds finns i artikeln [operativ system och webbläsare som stöds i Intune](https://docs.microsoft.com/intune/supported-devices-browsers#supported-samsung-knox-standard-devices). Om enheten inte finns med i listan kan du läsa tillverkaren av enheten eller kontakta en support tekniker.

> [!Note]
> Microsoft arbetar med tillverkare för att åtgärda eventuella problem som vi påträffar under testning eller som användarna rapporterar till oss. Vi uppdaterar den här artikeln när ny information är tillgänglig.

## <a name="update-devices"></a>Uppdatera enheter

Om du inte har uppdaterat enheten till den senaste versionen av Android går du till enhetens **inställnings** app och väljer **Uppdatera**.  

## <a name="next-steps"></a>Nästa steg

Behöver du fortfarande hjälp? Kontakta företagets support (du hittar kontaktinformation på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980)) eller skriv till <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-teamet</a>.  
