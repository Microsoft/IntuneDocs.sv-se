---
title: Hur du tilldelar enhetsprofiler med Intune
titlesuffix: Azure portal
description: "När du har skapat en enhetsprofil i Intune, kan du använda det här ämnet för att lära dig hur du tilldelar den till enheter.”"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ba1438fe9227e0c7933fda7e9a2b60c8d4a5dca4
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-assign-microsoft-intune-device-profiles"></a>Så här tilldelar du enhetsprofiler i Microsoft Intune

## <a name="assign-a-device-profile"></a>Tilldela en enhetsprofil

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
1. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
2. I listan över profilblad väljer du den profil som du vill hantera och sedan **Hantera** > **Tilldelningar** på bladet <*profilnamn*> **Rapporter** .
3. På nästa blad väljer du antingen **Inkludera** (t.ex. grupper) eller **Exkludera** (för att utesluta grupper). Välj därefter **Välj grupper**.
![Inkludera och exkludera grupper från en profiltilldelning.](./media/group-include-exclude.png)
4. Gå till bladet **Välj grupper** och välj de Azure AD-grupper som du vill inkludera eller exkludera från tilldelningen. Du kan hålla ned **CTRL**-tangenten för att markera flera grupper.
4. När du är klar väljer du **Välj** på bladet **Välj grupper**.



## <a name="how-to-exclude-groups-from-a-device-profile-assignment"></a>Så här inkluderar och exkluderar du grupper från en enhetsprofiltilldelning

Med hjälp av Intunes profiler för enhetskonfiguration kan du exkludera grupper från principtilldelningen. Du kan t.ex. tilldela en enhetsprofil till gruppen **Alla företagsanvändare**, men välja att exkludera alla användare som även är medlemmar i gruppen **Ledningsgrupp**.

När du exkluderar grupper från en tilldelning bör du exkludera endast användargrupper eller endast enhetsgrupper – du får inte blanda grupperna. Intune tar inte hänsyn till några kopplingar mellan användare och specifika enheter vid exkludering av grupper. Om du väljer att inkludera användargrupper och samtidigt exkludera enhetsgrupper kommer du aldrig att få önskat resultat. Om du blandar grupper, eller om någon annan konflikt skulle uppstå, äger inkludering företräde.

Säg att du t.ex. vill tilldela en profil till alla enheter i din organisation, med undantag för allmänt tillgängliga informationsdatorer (kiosker). Du inkluderar gruppen **Alla användare**, men exkluderar gruppen **Alla enheter**.

Då tilldelas alla användare och deras enheter samma princip, även om användarens enhet ingår i gruppen **Alla enheter**. 

Exkluderingsfunktionen tittar bara på direkta medlemmar av gruppen, ingen hänsyn tas till de enheter som eventuellt finns kopplade till användaren. Enheter som saknar användare tilldelas emellertid ingen princip, eftersom de inte är kopplade till någon i gruppen **Alla användare**. 

Om du inkluderar **Alla enheter**, men exkluderar **Alla användare**, tilldelas alla enheter samma princip. Avsikten är i det här fallet att undanta enheter som är kopplade till en användare. Det kommer dock inte att fungera, eftersom exkluderingsfunktionen endast tittar på direkta medlemmar av gruppen. 

>[!Tip]
>Exkluderingsfunktionen kan för närvarande inte användas tillsammans med kompatibilitetsprinciper eller apptilldelningar. Om du vill exkludera medlemmar från en tilldelning kan du använda värdena Tillgängligt respektive Inte tillämpligt. Du kan t.ex. tilldela en app till **Alla företagsanvändare** genom att välja värdet **Tillgängligt** och därefter ange värdet **Ej tillämpligt** för **Ledningsgrupp**. Appen tilldelas till alla användare *utom* användare i **Ledningsgrupp**. Om du tilldelar appen till **Alla företagsanvändare** med värdet **Obligatoriskt** går det dock inte att exkludera **Ledningsgrupp**.
 
    
## <a name="next-steps"></a>Nästa steg
Se [Övervaka enhetsprofiler](device-profile-monitor.md) för information som hjälper dig att övervaka tilldelningar av enhetsprofiler.
