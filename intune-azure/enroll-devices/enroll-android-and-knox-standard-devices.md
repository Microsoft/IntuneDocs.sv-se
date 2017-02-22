---
title: "Registrera Android-enheter i Intune | Intune Azure-förhandsbeskrivning | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Information om hur du registrerar Android-enheter i Intune Azure-förhandsversionen."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: edd6303f3bb05dfff758cbb7d4bd08e21f083998


---

# <a name="enroll-android-devices"></a>Registrera Android-enheter

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Som Intune-administratör kan du aktivera hanteringen av Android-enheter, inklusive Samsung Knox Standard-enheter, från företagsportalen. Användarna kan sedan registrera sina enheter med hjälp av företagsportalappen som finns på Google Play.

## <a name="prerequisite"></a>Krav

Du måste ange MDM-utfärdare för **Microsoft Intune** så att du kan hantera mobila enheter. Fler anvisningar finns i [Ange MDM-utfärdare](set-mdm-authority.md). Du anger det här objektet bara en gång, och det är när du först konfigurerar Intune för hantering av mobila enheter. Så det kan hända att du redan har gjort de här inställningarna. 

## <a name="set-up-android-enrollment"></a>Konfigurera Android-registrering

Som standard ställs Intune in så att registrering av Android- och Samsung Knox Standard-enheter tillåts. 

Om du vill visa inställningen för att tillåta eller blockera Android-enheter från registrering, går du till Intune-bladet i Azure-portalen och väljer **Registrering** > **Registreringsbegränsningar**. 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurserna

Registreringsinstruktioner för slutanvändare finns i [Registrera din Android-enhet i Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android). Registreringsprocessen förklarar för användarna vad de kan förvänta sig och vad IT-administratörer kan och inte kan se på deras enheter.

Information om andra slutanvändaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Använda en Android-enhet med Intune](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)


<!--HONumber=Feb17_HO1-->


