---
title: "Vad är villkorlig åtkomst? | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Lär dig hur du anger de villkor som användare och enheter måste uppfylla för att få åtkomst till företagets resurser i Microsoft förhandsversion av Intune Azure."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 41931f64db969c82f79e007c4be9e68b7caf4ce9
ms.openlocfilehash: 20696fb2dc0126aa224e779738cedb4f95f666e8


---

# <a name="what-is-conditional-access"></a>Vad är villkorlig åtkomst?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


I det här avsnittet beskriver vi villkorlig åtkomst som gäller för Enterprise Mobility + Security, därefter beskriver vi funktioner för villkorlig åtkomst i Intune.

Villkorlig åtkomst från Enterprise Mobility + Security (EMS) utnyttjar kraften i Azure Active Directory Premium och Microsoft Intune för att tillhandahålla den kontroll du behöver för att skydda företagets data, samtidigt som det ger användarna en upplevelse som gör att de utföra sitt arbete på bästa sätt från en valfri enhet.

Med villkorlig åtkomst kan du kan definiera villkor som begränsar åtkomsten till företagets data baserat på plats, enhet och användare och programmets känslighet.

Ur enhetsperspektiv arbetar Intune och Azure Active Directory tillsammans för att se till att endast hanterade och kompatibla enheter får åtkomst till e-post och Office 365-tjänster. Du kan till exempel ange en princip i Azure Active Directory för att endast göra det möjligt för datorer som är anslutna till en domän, eller mobila enheter som är registrerade i ett program för mobil enhetshantering som Intune, till att få åtkomst till Office 365-tjänster. Du kan använda Intune för att ange en kompabilitetsprofil för enheter som utvärderar enhetens kompatibilitetsstatus. Kompatibilitetsstatusen rapporteras till Azure Active Directory för att användas för verkställande av principer i Azure Active Directory när användaren försöker få åtkomst till företagets resurser. Mer information om enhetskompatibilitet i Intune finns i [Vad är enhetsefterlevnad?](/intune-azure/set-device-compliance/what-is-device-compliance)

Villkorlig åtkomst för molnappar, till exempel Exchange Online, kan konfigureras via Azure Active Directory. Mer information finns i den här [artikeln](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access-azure-portal).

## <a name="on-premises-conditional-access-in-intune"></a>Lokal villkorlig åtkomst i Intune

Villkorlig åtkomst i Intune kan användas för att tillåta eller blockera åtkomst till **Exchange On-premises** baserat på enhetshantering och registrering.

Profilinställningar för enhetsefterlevnad används för att utvärdera enhetens kompatibilitet. Villkorlig åtkomst använder utvärderingen för att tillåta eller blockera åtkomst till Exchange On-premises. När villkorlig åtkomst använd i kombination med en profil för enhetsefterlevnad ges endast kompatibla enheter åtkomst till Exchange On-premises. Du kan konfigurera avancerade inställningar i villkorlig åtkomst för detaljerad kontroll, som att till exempel tillåta eller blockera vissa plattformar eller omedelbart blockera enheter som inte hanteras av Intune.

Profilen för enhetsefterlevnad och villkorlig åtkomst tilldelas till användaren. Alla olika enheter som användaren använder för att få åtkomst till Exchange On-premises kontrolleras. Tänk på att en efterlevnadsprofil måste tilldelas enhetsanvändaren för att enhetens efterlevnad ska kunna utvärderas. Om ingen efterlevnadsprincip har distribuerats till användaren behandlas enheten som kompatibel och inga åtkomstbegränsningar tillämpas.

När en enhet inte uppfyller de angivna villkoren leds slutanvändaren genom en process för att registrera enheten och åtgärda de problem som gör att enheten inte är kompatibel.

## <a name="next-steps"></a>Nästa steg

[Skapa en princip för villkorlig åtkomst för Exchange On-premises](create-conditional-access-policy-for-exchange-on-premises.md)

[Konfigurera villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access-azure-portal)



<!--HONumber=Feb17_HO1-->


