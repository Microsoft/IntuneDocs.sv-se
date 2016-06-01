---
# required metadata

title: Registrera enheter i Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrera enheter för hantering i Intune
Hantering av mobila enheter i Microsoft Intune (MDM) använder registrering för att skapa hantering för enheterna och tillåta åtkomst till resurser. Metoden för att registrera enheter beror på enhetstyp, ägande och den hanteringsnivå som krävs. Scenarier med "bring your own device" (BYOD) och företagsägda enheter (COD) kräver en registreringsprocess. Organisationer som använder ActiveSync, antingen lokalt eller med värd i molnet, kan aktivera lättare hantering utan registreringskrav. Windows-datorer kan också hanteras med Intune-klientprogrammet.

## Aktivera registrering av enheter  
 Med registrering kan användarna få åtkomst till företagsresurser på sina personliga enheter och det gör det möjligt för administratören att se till att dessa enheter följer principer som skyddar företagets resurser. Det här är det bästa sättet att möjliggöra scenarier med "bring your own device" med Intune. Administratören måste aktivera registrering i Intune-konsolen, vilket kan kräva att man skapar en förtroenderelation med enheten och tilldelar licenser till användare. Enheten registreras sedan, normalt av användare som anger sina arbets- eller skolautentiseringsuppgifter. Enheten tar sedan emot principer från Intune och får åtkomst till resurser.

[Dags att registrera enheter i Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)

## Registrera enheter som ägs av företaget
Företagsägda enheter (COD) kan hanteras med Intune-konsolen. iOS-enheter kan registreras direkt via verktyg från Apple. Alla enhetstyper kan registreras av en administratör eller chef med hjälp av hanteraren för enhetsregistrering. Enheter med ett IMEI kan också identifieras och taggas som företagsägda för att möjliggöra COD-scenarier.

[Registrera enheter som ägs av företaget](manage-corporate-owned-devices.md)

## Hantering av mobila enheter med Exchange ActiveSync och Intune
Mobila enheter som inte är registrerade men som ansluter till Exchange ActiveSync (EAS) kan hanteras av Intune med EAS MDM-principen. Intune använder en Exchange-anslutning för att kommunicera med EAS, antingen lokalt eller med värd i molnet .



[Hantering av mobila enheter med Exchange ActiveSync och Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Hantera Windows-datorer med Intune  
Du kan också använda Microsoft Intune för att hantera Windows-datorer med datorklientprogramvaran Intune för Windows. Datorer som hanteras med Intune-klienten kan:

 - Rapportera program- och maskinvaruinventering
 - Installera skrivbordsprogram (till exempel .exe och .msi-filer)
 - Brandväggsinställningar

Datorer som hanteras med Intune-klientprogrammet kan inte rensas selektivt eller dras tillbaka, och de kan inte dra nytta av många av Intune-hanteringsfunktionerna, t.ex. villkorlig åtkomst, VPN- och Wi-Fi-inställningar eller distribution av certifikat och e-postkonfigurationer.

[Hantera Windows-datorer med Intune](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


