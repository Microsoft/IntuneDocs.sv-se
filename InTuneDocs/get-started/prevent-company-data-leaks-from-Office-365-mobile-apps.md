---
title: "Förhindra företagsdataläckor från Office 365-mobilappar | Microsoft Docs"
description: "Använd Intune för att skydda din organisations data med MAM-principer för hantering av mobilappar som förhindrar läckage av företagsdata från Office 365-mobilappar eller andra affärsappar (LOB)."
keywords: 
author: jeffgilb
ms.author: jeffgilb
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 19be3de7-539c-49f5-8c46-5363b987fef9
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f268cf29461447306d0f5c3ca06d541d9a03a49d
ms.openlocfilehash: 0288ecd940d650304d83b7dd5803a56f69b936f7


---

# <a name="quick-start-guide-prevent-company-data-leaks-from-office-365-mobile-apps"></a>Snabbstartsguide: Förhindra företagsdataläckor från Office 365-mobilappar

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Med Microsoft Intune kan du skydda organisationens data med hanteringsprinciper för mobilprogram (MAM) som skyddar mot företagsdataläckor från Office 365-mobilappar eller andra verksamhetsspecifika appar. Du kan också använda Intune MAM-principer utan att användarna registrerar sina enheter i Intunes hantering av mobilenheter (MDM). Om du har användare som inte vill registrera sin iOS- eller Android-enhet i en Microsoft MDM-lösning (Intune, Configuration Manager eller EAS), om du vill skydda företagsdata utan att hantera användarnas enheter eller om du redan använder en annan lösning än Microsoft MDM, kan Intune ändå hjälpa dig att öka datasäkerheten i ditt företag.   

## <a name="is-this-quick-start-guide-right-for-me"></a>Är den här snabbstartsguiden rätt för mig?
Vill du ge användarna åtkomst till data i Office 365 och verksamhetsspecifika appar på deras iOS- och Android-enheter utan att kräva enhetsregistrering i en MDM-lösning, men ändå ha kontroll över vad de kan och inte kan göra med dessa data (till exempel kopiera och klistra in data i egna appar)?

I så fall kan du ange MAM-principer för Office 365-mobilappar på iOS- och Android-enheter med Microsoft Intune, till exempel ange begränsningar för att klippa ut, kopiera och klistra in data, förhindra ”spara som” och ange PIN-kodskrav. Du kan också fjärrensa MAM-skyddade data.  På så sätt kan du skydda företagsdata utan att kräva att användarna registrerar sina enheter i en MDM-lösning. Och får samtidigt en bra användarupplevelse i Office-mobilapparna.

## <a name="how-do-i-do-it"></a>Hur gör jag?
1.    Läs grundläggande information om [hur Intunes hantering av mobilprogram (MAM)](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) fungerar.
2.    Ta reda på [vad du behöver göra innan du kan skapa MAM-principer](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) i Azure Portal.
3.    [Skapa och distribuera MAM-principer](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) med Intune.

### <a name="additional-information"></a>Ytterligare information:
- [Slutanvändarupplevelse](/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune) med MAM-aktiverade appar.
- [Förbereda verksamhetsspecifika appar för MAM med Intune](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
- <a href="https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners" target="_blank"> Lista över Microsoft Intune-partner &rarr;</a> som tillhandahåller MAM-aktiverade appar.

## <a name="what-should-i-do-next"></a>Vad ska jag göra sedan?
[Migrera från en annan lösning än Microsoft MDM till Microsoft Intune](/intune/deploy-use/migrate-to-intune)

[Registrera enheter i Intune MDM](/intune/deploy-use/enroll-devices-in-microsoft-intune)



<!--HONumber=Dec16_HO3-->


