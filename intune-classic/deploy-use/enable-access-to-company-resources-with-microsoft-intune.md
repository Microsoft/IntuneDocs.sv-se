---
title: "Ge åtkomst till företagsresurser"
description: "Wi-Fi-, VPN- och e-postprofiler fungerar tillsammans så att användarna får åtkomst till de filer och resurser som de behöver."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dd8dd4e-e165-4d0c-97b7-b3e86ebab909
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 515dde28e55524895137ed46ee517e900cdae20c
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="enable-access-to-company-resources-with-microsoft-intune"></a>Ge åtkomst till företagsresurser med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Wi-Fi-, VPN- och e-postprofiler i Microsoft Intune fungerar tillsammans så att användarna får åtkomst till de filer och resurser som de behöver för att utföra sitt arbete, oavsett var de befinner sig. Certifikatprofiler hjälper till att säkra den åtkomsten.

## <a name="wi-fi-profileswi-fi-connections-in-microsoft-intunemd-and-supported-platforms"></a>[Wi-Fi-profiler](wi-fi-connections-in-microsoft-intune.md) och plattformar som stöds

Distribuera trådlösa nätverksinställningar till användarna. Inställningarna gör det enkelt för användarna att ansluta till företagets nätverk.
#### <a name="supported-platforms"></a>Plattformar som stöds

|Windows 8.1 och senare|Windows Phone 8.1 och senare|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|Ja (du kan importera en Windows Wi-Fi-profil)|Ja (du kan konfigurera OMA-URI) |Ja|Ja|Ja|

## <a name="vpn-profilesvpn-connections-in-microsoft-intunemd-and-supported-platforms"></a>[VPN-profiler](vpn-connections-in-microsoft-intune.md) och plattformar som stöds
Distribuera VPN-inställningar till dina användare. Inställningarna gör det enkelt för användarna att ansluta till resurser i företagets nätverk.

|Windows 8.1 och senare|Windows Phone 8.1 och senare|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|Ja|Ja|Ja|Ja|Ja|

## <a name="email-profilesconfigure-access-to-corporate-email-using-email-profiles-with-microsoft-intunemd-and-supported-platforms"></a>[E-postprofiler](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md) och plattformar som stöds
Skapa, distribuera och övervaka inbyggda e-postklientinställningar på enheter i organisationen.

|Windows 8.1 och senare|Windows Phone 8.1 och senare|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|Nej|Ja|Ja|Nej|Ja|
> [!NOTE]
> [I det här blogginlägget från Intune-teamet](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/19/using-oma-uri-to-create-custom-wi-fi-profiles-for-windows-phone-8-1/) finns information om hur du konfigurerar Windows Phone 8.1 Wi-Fi-profiler med OMA-URI.

## <a name="certificate-profilessecure-resource-access-with-certificate-profilesmd-and-supported-platforms"></a>[Certifikatprofiler](secure-resource-access-with-certificate-profiles.md) och plattformar som stöds
Hjälper till med att säkra åtkomst till företagsresurser som trådlösa nätverk och VPN-anslutningar.

|Windows 8.1 och senare|Windows Phone 8.1 och senare|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|Ja|Ja|Ja|Ja|Ja|
