---
title: "Konfigurera en tjänst för kostnadsuppföljning av telekommunikation | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Konfigurera Saaswedo-tjänsten för kostnadsuppföljning av telekommunikation till att integreras med Intune."
keywords: Saaswedo
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 915d61344a3c1d388305dd51b1e2463bd2e32770
ms.openlocfilehash: 8d94fec099e1dc8918077062fb73b94a5973ea96

---

# <a name="set-up-a-telecom-expense-management-service-in-intune-azure-preview"></a>Konfigurera en tjänst för kostnadsuppföljning av telekommunikation i Intune Azure-förhandsversionen
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune har integrerats med Datalert-lösningen för kostnadsuppföljning av telekommunikation från tredjepartsprogramutvecklaren Saaswedo. Datalert är ett program för kostnadsuppföljning av telekommunikation i realtid, där du kan hantera dataanvändningen och undvika kostsam och oväntad överförbrukning av data och nätverksväxling i dina Intune-hanterade enheter. Med Intunes integrering med Datalert kan du centralt ange, övervaka och upprätthålla begränsningar för nätverksväxling och inrikes dataanvändning med hjälp av automatiserade varningar när du överskrider definierade tröskelvärden. Du kan konfigurera tjänsten om du vill tillämpa olika åtgärder på enskilda personer eller grupper av slutanvändare, inklusive att inaktivera nätverksväxling när användarna överskrider tröskelvärdet. Rapporter med information om övervakning och dataanvändning är tillgängliga från Datalerts hanteringskonsol.

Innan du kan använda Datalert-tjänsten med Intune måste du konfigurera inställningarna i Datalert-konsolen och i Intune. Anslutningen måste vara aktiverad för Datalert-tjänsten och för Intune. Om Datalert-sidan av anslutningen är aktiverad men inte Intune-sidan, tar Intune emot kommunikationen men ignorerar den.

>[!NOTE]
>Om du vill aktivera den här funktionen i din utvärderingsversion [kontaktar du Microsofts support](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) för aktivering och Datalerts support för de programvarulicenser som krävs.

## <a name="supported-platforms"></a>Plattformar som stöds

- Samsung Knox
- iOS 8.0 och senare

## <a name="prerequisites"></a>Förutsättningar

- En prenumeration på Microsoft Intune
- En prenumeration på Datalerts tjänst för kostnadsuppföljning av telekommunikation

## <a name="list-of-telecom-expense-management-providers"></a>Lista med leverantörer för kostnadsuppföljning av telekommunikation

Intune kan för närvarande integreras med följande leverantörer för kostnadsuppföljning av telekommunikation:

[Saaswedo Datalerts tjänst för kostnadsuppföljning av telekommunikation](http://www.datalert.biz/)

## <a name="configure-intune-to-work-with-the-datalert-service"></a>Konfigurera Intune så att det fungerar med Datalert-tjänsten

 

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
2. På bladet **Enhetskonfigurationen** väljer du **Konfiguration** > **Kostnadsuppföljning av telekommunikation**.
2. Under **Kostnadsuppföljning av telekommunikation** väljer du **Anslutningsstatus**.

3. Välj **Lista över tjänstleverantörer inom kostnadsuppföljning av telekommunikation** och välj sedan leverantören i listan. En sida som är specifik för din leverantör öppnas. För Saaswedo öppnas sidan Datalert. Du måste kontakta Saaswedo Datalert för att köpa en prenumeration.

4. I **Datalert**-hanteringskonsolen:

    a. Gå till fliken **Inställningar** och sedan till avsnittet **MDM-konfiguration**.

    b. Välj **Lås upp** så att du kan ange inställningarna på sidan.

    c. För **Server MDM** väljer du **Microsoft Intune**.

    d. Som **Klient-ID** anger du ditt klient-ID för Intune och väljer knappen **Anslutning**. När du väljer **Anslutning** kontrollerar Datalert med Intune för att se till att det inte finns några befintliga Datalert-anslutningar med Intune. Efter några sekunder visas Microsofts inloggningssida, följt av Datalert Azure-autentiseringen.

    e. På sidan med Microsoft-autentisering väljer du **Godkänn**. Du omdirigeras till Datalerts ”Tack”-sida som stängs efter några sekunder. Datalert verifierar anslutningen och visar gröna bockmarkeringar bredvid listan med objekt som har verifierats. Om verifieringen misslyckas, visas ett meddelande i rött. Om detta händer kan du kontakta Datalert Support för att få hjälp.

5. Vänta några minuter. Gå sedan till Azure-portalen och kontrollera att anslutningsstatus visas som **Aktiv**. 

    >[!NOTE]
    >Om du vill aktivera den här funktionen i utvärderingsversionen av klienten kan du [kontakta Microsoft support](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

6. Gå tillbaka till Datalert-hanteringskonsolen och konfigurera dina datarader:

    a. Gå till fliken **Inställningar**.

    b. Gå till guiden **Installation** och följ anvisningarna i guiden.



Datalert-tjänsten är nu aktiv och startar övervakningen av dataanvändningen. Den inaktiverar dessutom mobil- och nätverksväxlingsdata på enheter som överskrider de konfigurerade användningsbegränsningarna.

## <a name="turning-off-the-datalert-service"></a>Stänga av Datalert-tjänsten

Om du inaktiverar Datalert-tjänsten i Azure-portalen:

- Alla åtgärder som har tillämpats på enheter, på grund av tidigare överskridna användningsbegränsningar, återställs.
- Användarna blockeras inte längre från åtkomst till data och nätverksväxling.
- Intune kan fortfarande ta emot signaler från tjänsten, men ignorerar dem.

**Stänga av tjänsten**

1. På bladet **Kostnadsuppföljning av telekommunikation** i Azure-portalen väljer du **Inaktivera**.

2. Välj **Spara**.

## <a name="viewing-data-usage-and-roaming-reports"></a>Visa dataanvändning och nätverksväxlingsrapporter

För tillfället är dataanvändningsrapporter endast tillgängliga i Saaswedos Datalert-hanteringskonsol.



<!--HONumber=Feb17_HO2-->


