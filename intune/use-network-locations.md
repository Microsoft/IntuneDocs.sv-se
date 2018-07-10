---
title: Binda Android-enheter efter nätverksplats i Microsoft Intune – Azure | Microsoft Docs
description: Skapa eller konfigurera nätverksplatser i Microsoft Intune för Android-enheter. Du kan märka enheter som inkompatibla baserat på enhetens nätverksplats. Om enheten ansluter utanför nätverksplatsen kan du blockera åtkomsten till företagsresurser.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ayesham
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 988407d6d736b669854ef8420b71a092765162b7
ms.sourcegitcommit: 445fcf9e2a185e5c987334cad398bce71383be03
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843131"
---
# <a name="use-locations-network-fence-in-intune"></a>Använda platser (nätverksstängsel) i Intune

Du kanske vill blockera åtkomsten till ett företagsnätverk om en enhet lämnar en plats. Du kan göra det med funktionen **Platser** i Intune. 

Du kan skapa en nätverksplatsbaserad efterlevnadsprincip, eller nätverksstängsel. Principen kräver att enheter är anslutna till ett arbetsplatsnätverk för att vara kompatibla. Den här principen kan användas med principer för villkorlig åtkomst så att enheter *endast* har åtkomst till arbetsresurser när de är anslutna till arbetsplatsnätverket. När enheten inte är ansluten till arbetsplatsnätverket blir den inkompatibel och kan inte längre komma åt arbetsresurser.

Föreställ dig följande scenario:

På din tillverkningsanläggning använder vissa anställda Android-enheter. En medarbetare tar med sin Android-enhet utanför anläggningen. För att förhindra obehörig åtkomst kan du:

1. Skapa en plats med ett IPv4-adressintervall och till exempel ge den namnet **Tillverkningsanläggning**.
2. Skapa en efterlevnadsprincip som kräver att enheterna är anslutna till företagsnätverket och tilldela den här principen.
3. Om enheten lämnar tillverkningsanläggningen betraktas den som inkompatibel och har inte längre åtkomst till företagsresurser.

Dessutom kan du lägga till [åtgärder vid inkompatibilitet](#configure-the-actions-for-noncompliance). När enheten är tillbaka lokalt på anläggningen och på nätverksplatsen får den återigen åtkomst till företagsresurser.

## <a name="prerequisites"></a>Krav

Så här skapar du en platsbaserad efterlevnadsprincip:

- Skapa en nätverksplats som IPV4-nätverksintervall för gateway-servern, DHCP-servern och/eller DNS-servern som enheterna ansluter till.
- Skapa efterlevnadsprincipen som använder dessa platser och som definierar de åtgärder som ska vidtas när enheten inte längre är ansluten till nätverksplatsen.
- Android-enheter med version 6.0 och senare, med den uppdaterade företagsportalappen

## <a name="create-a-location"></a>Skapa en plats

1. Välj **Enhetsefterlevnad** > **Platser** > **Skapa** i Intune.

2. Ange följande egenskaper:  

   - Obligatoriskt. Ange ett **namn** för platsen, t.ex. **Tillverkningsanläggning** eller **Byggnad 44-säker**.
   - Valfritt. Ange ett **IPv4-intervall** med CIDR-notation (Classless Interdomain Routing), t.ex. `aaa.bbb.ccc.ddd/n`.
   - Valfritt. Ange **IPv4-gateway-adressen**, t.ex. `aaa.bbb.ccc.ddd`.
   - Valfritt. Ange **IPv4 DHCP-serveradressen**, t.ex. `aaa.bbb.ccc.ddd`.
   - Valfritt. Ange en lista med **IPv4 DNS-serveradresser**. Den här inställningen använder **matchning av deluppsättningar**. Om IPv4 DNS-servrarna på enheten utgör deluppsättningar av de angivna värdena anses enheten vara innanför stängslet. Var noga med att ange en adress per rad, så här:  
     `aaa.bbb.ccc.ddd`  
     `aaa.bbb.ccc.ddd`
   - Valfritt. Ange en lista över **DNS-suffix**. Den här inställningen använder **matchning av deluppsättningar**. Om DNS-suffixen på enheten utgör deluppsättningar av de angivna värdena anses enheten vara innanför stängslet. Var noga med att ange ett domännamn per rad, så här:  
     `contoso.com`  
     `contoso.org`

3. **Spara** ändringarna.

## <a name="create-the-location-compliance-policy"></a>Skapa principen för platsefterlevnad

När du skapar efterlevnadsprincipen väljer du **Android** för **Plattform**. I **Platser** kan du välja en eller flera av de nätverksplatser som du har lagt till. Dessa platser är en del av nätverksstängslet som du skapar för enheterna.

Mer information finns i avsnittet [Skapa den nätverksplatsbaserade efterlevnadsprincipen](compliance-policy-create-android.md#locations).

## <a name="configure-the-actions-for-noncompliance"></a>Konfigurera åtgärderna för inkompatibilitet

När du har skapat efterlevnadsprincipen tillämpas standardåtgärden för inkompatibilitet för enheten. Du kan lägga till fler åtgärder. Du kan till exempel lägga till en åtgärd som skickar ett e-postmeddelande till användaren när enheten inte längre är kompatibel med platserna.

Mer information finns i avsnittet [Lägga till åtgärder för inkompatibilitet](actions-for-noncompliance.md).

## <a name="company-portal-app"></a>Företagsportalappen

När enheten är ansluten till dina platser visas den som kompatibel i företagsportalappen. När enheten inte är ansluten till någon av platserna visas enheten som inkompatibel.

## <a name="next-steps"></a>Nästa steg
[Övervaka principer för enhetsefterlevnad](compliance-policy-monitor.md)  
[Komma igång med efterlevnadsprinciper](device-compliance-get-started.md)
