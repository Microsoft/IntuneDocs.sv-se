---
title: "Kända problem i förhandsversionen av Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Mer information om kända problem i förhandsversionen"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/25/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 36b35e5311f6262c545a266003fb72b2febb277c
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Kända problem i Microsoft Intune-förhandsversionen


[!INCLUDE[azure_preview](./includes/azure_preview.md)]


Läs det här avsnittet om du ha mer information om kända problem i Intune-förhandsversionen.

Om du vill rapportera en bugg som inte visas här, [öppnar du en supportförfrågan](https://docs.microsoft.com/intune-classic/troubleshoot/get-support).

Om du vill föreslå att en ny funktion läggs till i Intune kan du skicka en rapport på vår [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console)-plats.

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>Grupper som skapats av Intune under migreringen kan påverka funktionen för andra Microsoft-produkter

När du migrerar från klassiska Intune till Azure Portal, kan det visas en ny grupp med namnet **All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Observera att den här gruppen innehåller alla användare i Azure Active Directory, inte bara Intune-licensierade användare. Detta kan orsaka problem med andra Microsoft-produkter om du förväntar dig att vissa befintliga eller nya användare inte ska vara medlemmar i några grupper.

### <a name="altering-groups-created-by-intune-during-migration-will-delay-migration"></a>Om du ändrar grupper som skapats av Intune under migreringen, kommer migreringen att försenas

Vid förberedelserna för migreringen kopieras grupper från Intune till Azure AD. Övriga ändringar som du gör i den klassiska Intune-portalen kommer att uppdateras i Azure AD-gruppen. Dock synkroniseras inte ändringar som görs i Azure AD tillbaka till den klassiska Intune-konsolen. Detta kan resultera i att migreringen till Azure-portalen misslyckas och att migreringen försenas.

### <a name="compliance-policies-from-intune-will-not-show-up-in-new-console"></a>Efterlevnadsprinciper från Intune visas inte i någon ny konsol

Alla efterlevnadsprinciper som du har skapat i den klassiska Intune-portalen har migrerats, men de visas inte i Azure-portalen. Det beror på en designändring i Azure-portalen. Efterlevnadsprinciper som du skapade i den klassiska Intune-portalen används fortfarande, men du måste visa och redigera dem i den klassiska portalen.
Dessutom syns nya efterlevnadsprinciper som du skapar i Azure-portalen inte i den klassiska portalen.
Mer information finns i [Vad är enhetsefterlevnad?](device-compliance.md).




### <a name="administration-and-accounts"></a>Administration och konton

Globala administratörer (kallas även innehavaradministratörer) kan fortsätta att utföra dagliga administrationsuppgifter utan en separat Intune- eller EMS-licens (Enterprise Mobility Suite). Om globala administratörer vill använda tjänsten, t.ex. för att registrera sina egna enheter, företagsenheter eller för att använda Intunes företagsportal, behöver de dock en Intune- eller EMS-licens precis som andra användare.

### <a name="apple-enrollment-profile-migration"></a>Migrering av Apple-registreringsprofil
Under de kommande månaderna kommer Intune att aktivera distributionshanteringen av Apples program för enhetsregistrering och Apple Configurator via nya Azure Portal. Om du tar bort Apples DEP-token och inte överför en uppdaterad token, så återställs den ursprungliga token i nya Azure Portal som en del av migreringen av ditt Intune-konto. Om du vill ta bort denna token och förhindra DEP-registrering tar du helt enkelt bort token i Azure Portal. 

### <a name="rbac-for-apple-corporate-owned-device-enrollment"></a>RBAC för registrering av företagsägda Apple-enheter
Klientens eller tjänstadministratörens Azure AD-roller är nödvändiga för att kunna utföra registrering i Apple DEP och Apple Configurator, trots att RBAC-behörigheter visas och är tillgängliga under den anpassade användarrollen. RBAC-rollstöd för dessa funktioner kommer att finnas i framtiden.

