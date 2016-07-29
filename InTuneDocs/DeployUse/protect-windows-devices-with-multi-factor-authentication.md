---
title: "Multi-factor Authentication för Windows | Microsoft Intune"
description: "Intune integrerar Multi-factor Authentication (MFA) för att skydda företagets resurser."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: c1f9c60a1c79d23bab62617ed237ad982e82c39d


---

# Protect Windows devices with multi-factor authentication
Microsoft Intune integrerar multifaktorautentisering (MFA) för att skydda företagets resurser. MFA kräver autentiseringsfaktorer som textautentisering förutom användarnamn och lösenord. Intune stöder multifaktorautentisering vid registrering av Windows 8.1-enheter eller senare, Windows Phone 8.1-enheter eller Windows 10 Desktop- och Mobile-enheter.

## Krav på lokal infrastruktur för ADFS MFA
Om du vill konfigurera multifaktorautentisering behöver du:

-   **En Active Directory-domän som AD FS-servern är ansluten till.**

-   **En ADFS-server som har konfigurerats för multifaktorautentisering.** En server som kör Windows Server 2012 R2 som är konfigurerad som AD FS-server. Mer information finns i [Skydda molnet och lokala resurser med Azure Multi-Factor Authentication-server med Windows Server 2012 R2 AD FS](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

Alla servrar som anges ovan måste uppfylla systemkraven i [System Requirements and Installation Information for Windows Server 2012 R2](http://technet.microsoft.com/library/dn303418.aspx).

#### MFA med Intune
Om din organisation har en lokal IT-infrastruktur med en Active Directory-domän med AD FS (Active Directory Federation Services) kan du konfigurera MFA på federationsservern och sedan aktivera MFA för registrering i Intune. Genom att konfigurera MFA i Intune behöver användarna bara autentiseras en gång vid registreringen och kan sedan komma åt företagets resurser utan att behöva upprepa MFA-processen varje gång.

>[!NOTE]
>MFA kan krävas per användare eller per grupp på ADFS-servern.  

#### MFA utan Intune
Om du konfigurerar multifaktorautentisering på federationsservern, men inte aktiverar multifaktorautentisering för registrering i Intune måste användarna använda multifaktorautentisering varje gång de kommer åt företagsresurser (inte bara vid enhetsregistreringen).

Du kan också använda Azure Active Directory (AAD) MFA för att kräva multifaktorautentisering varje gång användarna kommer åt företagsresurser, för varje användare. AAD MFA är en molntjänst som inte kräver någon lokal IT-infrastruktur. Information om hur du ställer in AAD MFA finns i [Komma igång med Azure Multi-Factor Authentication i molnet.](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/).

## Kräver ADFS MFA under registreringen av Windows-enheter
Information om hur du aktiverar multifaktorautentisering i AD FS finns i [Manage Risk with Additional Multi-Factor Authentication for Sensitive Applications](http://technet.microsoft.com/library/dn280949.aspx).

## Konfigurera multifaktorautentisering vid enhetsregistrering i Intune
>[!Important]  
>Aktivera MFA i din Azure AD-klient eller lokala miljö innan du kräver MFA för Intune-registrering av Windows-enheter. Om du inte gör det får användarna ett felmeddelande när de försöker registrera sina Windows-enheter, eller när de försöker ansluta sina enheter till Azure AD, om automatisk registrering vid Azure AD-anslutning har konfigurerats.

1.  I Intune-administrationskonsolen klickar du på **Admin** &gt; **Hantering av mobila enheter** &gt; **Multi-Factor Authentication**.

2.  Klicka på **Konfigurera Multi-factor Authentication** och klicka sedan på **Aktivera Multi-factor Authentication**.



<!--HONumber=Jul16_HO4-->


