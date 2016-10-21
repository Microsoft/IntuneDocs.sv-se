---
title: "Multi-factor Authentication för Windows | Microsoft Intune"
description: "Intune integrerar Multi-factor Authentication (MFA) för att skydda företagets resurser."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0ced62efd04803943cbbfd8cecef907409a03c0b
ms.openlocfilehash: 00d63fa55cd29c938dd082e2eff240f08319e01a


---

# Protect Windows devices with multi-factor authentication
Microsoft Intune integrerar multifaktorautentisering (MFA) för att skydda företagets resurser. MFA kräver autentiseringsfaktorer, till exempel textautentisering, utöver användarnamn och lösenord. Intune stöder multifaktorautentisering vid registrering av Windows 8.1-enheter eller senare, Windows Phone 8.1-enheter eller Windows 10 Desktop- och Mobile-enheter.

## Krav på lokal infrastruktur för ADFS MFA
Om du vill konfigurera multifaktorautentisering behöver du:

-   Automatisk registrering som beskrivs i [Set up Windows device management](set-up-windows-device-management-with-microsoft-intune.md) (Konfigurera enhetshantering för Windows).
-   **En Active Directory-domän som AD FS-servern är ansluten till.**

-   **En ADFS-server som har konfigurerats för multifaktorautentisering.** En server som kör Windows Server 2012 R2 och är konfigurerad som en ADFS-server. Mer information finns i [Skydda molnet och lokala resurser med Azure Multi-Factor Authentication-server med Windows Server 2012 R2 AD FS](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

Servrarna måste uppfylla systemkraven i [Systemkrav och installationsinformation för Windows Server 2012 R2](http://technet.microsoft.com/library/dn303418.aspx).

 


#### MFA med Intune
Om din organisation har en lokal IT-infrastruktur med en Active Directory-domän med ADFS (Active Directory Federation Services) kan du konfigurera MFA på federationsservern och sedan aktivera MFA för registrering i Intune. Genom att konfigurera MFA i Intune behöver användarna bara autentiseras en gång vid registreringen och kan sedan komma åt företagets resurser utan att behöva upprepa MFA-processen varje gång.

>[!NOTE]
>MFA kan krävas per användare eller per grupp på ADFS-servern.  

#### MFA utan Intune
Om du konfigurerar MFA på federationsservern, men inte aktiverar MFA för registrering i Intune måste användarna använda MFA varje gång de kommer åt företagsresurser (inte bara vid enhetsregistreringen).

Du kan också använda Azure Active Directory (Azure AD) MFA för att kräva MFA för varje användare varje gång användarna kommer åt företagsresurser. Azure AD MFA är en molntjänst som inte kräver någon lokal IT-infrastruktur. Information om hur du ställer in Azure AD MFA finns i [Komma igång med Azure Multi-Factor Authentication i molnet.](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/).

## Kräver ADFS MFA under registreringen av Windows-enheter
Information om hur du aktiverar multifaktorautentisering i AD FS finns i [Manage Risk with Additional Multi-Factor Authentication for Sensitive Applications](http://technet.microsoft.com/library/dn280949.aspx).

## Konfigurera multifaktorautentisering vid enhetsregistrering i Intune
>[!Important]  
>Aktivera MFA i din Azure AD-klient eller lokala miljö innan du kräver MFA för Intune-registrering av Windows-enheter. Om du inte gör det får användare som försöker registrera sina Windows-enheter eller försöker ansluta sina enheter till Azure AD ett felmeddelande om automatisk registrering vid Azure AD-anslutning har konfigurerats.

1.  I Intune-administratörskonsolen väljer du **Admin** &gt; **Hantering av mobila enheter** &gt; **Multi-Factor Authentication**.

2.  Välj **Konfigurera Multi-factor Authentication** och välj sedan **Aktivera Multi-factor Authentication**.



<!--HONumber=Sep16_HO3-->


