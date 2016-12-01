---
title: "Mobila enheter och webbläsare som stöds | Microsoft Intune"
description: "Mobila enheter och datorer som Intune stöder"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aeeccfa4-0f14-447e-a3df-c8435c8a4bb2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 149f3a3310907d131affeaad4bd372aa60be9206
ms.openlocfilehash: 80541567c535cfeb7fca3eda3c9143f4b11d7abb


---

# <a name="supported-mobile-devices-and-computers"></a>Mobila enheter och datorer som stöds

Du kan registrera enheterna och sedan hantera följande enhetstyper:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

Om du registrerar enheterna får du [dessa funktioner](/Intune/get-started/choose-how-to-manage-devices).

Alternativt kan du hantera Windows-datorer med Intune PC-klientprogramvaran. Intune PC-klientprogramvaran stöder Windows 7 och senare, förutom Windows 10 Home. Genom att hantera datorer med klientprogramvaran får du tillgång till [dessa funktioner](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

Kunder med Enterprise Management Suite kan även använda Azure Active Directory (Azure AD) för att registrera Windows 10-enheter.

## <a name="microsoft-intune-supported-web-browsers"></a>Webbläsare som stöds av Microsoft Intune

Olika administrativa uppgifter kräver att du använder en av följande administrativa webbplatser.

- [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune-administratörskonsolen](https://admin.manage.microsoft.com/)

> [!Note]
> Administrationskonsolen stöder inte Microsoft Edge och mobila webbläsare eftersom de inte stöder [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). Intune-konsolen håller på att migreras från Silverlight-miljön. När det är klart kommer alla Intunes funktioner för hantering av mobila enheter och program att [göras tillgängliga på den nya Microsoft Azure-portalen](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).

|Intune-funktion |Webbläsare som stöds|
|---------|---------|
|Förbättringar i administrationskonsolen för Intune     |  Internet Explorer 10 eller senare<br /><br />Google Chrome (versioner före version 42)<br /><br />Mozilla Firefox med Silverlight aktiverat<br /><br />**Obs!** Microsoft Edge och mobila webbläsare har inte stöd i administratörskonsolen.                      
|Administrationsportalen för Office 365     |Alla webbläsare, inklusive mobila webbläsare och hanterade webbläsare  |
|Företagsportalens webbplats     |**På mobila enheter:** använd standardwebbläsaren för varje plattform som stöds   <br /><br />**På Windows-datorer:** Internet Explorer 10 eller senare eller Microsoft Edge<br /><br />**På Mac OS X 10.9 eller senare:** Apple Safari    |

> [!Note]
> Administrationskonsolen stöder inte Microsoft Edge och mobila webbläsare eftersom de inte stöder [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). Intune-konsolen håller på att migreras från Silverlight-miljön. När det är klart kommer alla Intunes funktioner för hantering av mobila enheter och program att [göras tillgängliga på den nya Microsoft Azure-portalen](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).

### <a name="office-365-portalhttpgomicrosoftcomfwlinkplinkid698854"></a>[Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**Använd portalen som en innehavaradministratör när du vill hantera din prenumeration**, inklusive följande uppgifter när de tillåts av din administratörsroll:

- Hantera användarkonton för prenumerationen och konfigurera katalogsynkronisering från din lokala Active Directory.
- Hantera grupper av användare, s.k. säkerhetsgrupper.
- Tilldela licenser till användare för att använda Intune.
- Konfigurera det domännamn som du använder med din prenumeration. Domännamnet definierar det konto som användare loggar in med.
- Hantera fakturerings- och köpinformation för din prenumeration, inklusive antalet licenser som du har, eller mängden molnlagringsutrymme som du kan använda.
- Hitta länkar för att visa hälsotillståndet för Intune-tjänsten.
- Som innehavaradministratör kan du logga in på Office 365-portalen för att hantera prenumerationen, även om ditt konto inte har tilldelats någon licens för att använda Intune.
- Alla användare som har en licens för Intune, men som är inte administratörer, kan använda portalen för att återställa sina kontolösenord och redigera sina profiler.
- För att få åtkomst till Office 365-portalen måste ditt konto har inloggningsstatusen **Tillåten**. Denna status skiljer sig från att ha en licens för prenumerationen. Som standard har alla användarkonton statusen **Tillåten**.


### <a name="microsoft-intune-administrator-consolehttpsmanagemicrosoftcom"></a>[Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/)

**Som tjänstadministratör kan du använda portalen för att hantera dagliga uppgifter**, som bl.a.:

- Ange principer för datorer och mobila enheter.
- Överföra och distribuera programvara, som t.ex. programuppdateringar och appar.
- Hantera Endpoint Protection på datorer.
- Visa enhetsstatus och köra rapporter.
- Logga in på den här portalen. Du måste antingen ha behörighet som tjänsteadministratör eller vara en innehavaradministratör med den globala administratörsrollen för att logga in på den här portalen.


Endast användare med behörighet som tjänsteadministratör eller innehavaradministratören med den globala administratörsrollen kan logga in på den här portalen. Om du vill få åtkomst till administrationskonsolen måste kontot ha en licens för att använda Intune och inloggningsstatusen **Tillåten**.



<!--HONumber=Nov16_HO4-->


