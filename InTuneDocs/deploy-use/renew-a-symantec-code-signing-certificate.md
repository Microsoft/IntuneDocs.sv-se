---
title: "Förnya ett Symantec-kodsigneringscertifikat för företag för användning med Intune | Microsoft Docs"
description: "Instruktioner för hur du förnyar Symantec-certifikat som används för att hantera vissa Windows-enheter och mobila Windows Phone-enheter"
keywords: 
author: staciebarker
ms.author: stabar
manager: angerobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c4813044-a925-4273-b0ec-e992fd55850a
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 928e4e8097b9cd326e0863a45b183226a7eae056
ms.openlocfilehash: acd1ab3a988adc4fee2a57ff4be82bac8e92a435


---

# <a name="renew-a-symantec-enterprise-code-signing-certificate-for-windows-devices"></a>Förnya ett Symantec-kodsigneringscertifikat för företag för Windows-enheter

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Symantec-certifikatet som används för att distribuera Windows- och Windows Phone-mobilappar måste förnyas regelbundet.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Så här förnyar du Symantec-företagscertifikatet för kodsignering

1.  Ett e-postmeddelande om förnyelsen skickas från Symantec ungefär 14 dagar innan certifikatet upphör att gälla. E-postmeddelandet innehåller anvisningar från Symantec om att du bör förnya ditt företagscertifikat.

    Mer information om Symantec-certifikat finns på [www.symantec.com](http://www.symantec.com). Du kan också ringa 1-877-438-8776 eller 1-650-426-3400.

2.  Gå till webbplatsen (exempel: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) och logga in med Symantec Publisher ID och e-postadressen som är associerade med certifikatet. Kom ihåg att använda samma dator för att starta förnyelsen som du använde för att hämta certifikatet.

3.  När förnyelsen är godkänd och betald kan du hämta certifikatet.

## <a name="how-to-install-the-updated-certificate-for-windows-phone-80"></a>Hur du installerar det uppdaterade certifikatet för Windows Phone 8.0

1.  Hämta och signera den senaste företagsportalen för Windows Phone här: [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Öppna din Intune-administratörskonsol ([https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)) och välj **Admin**, **Hantering av mobila enheter** &gt; **Windows Phone** och klicka på **Överför signerad app**.

3.  Överför den nyligen signerade företagsportalen. Du behöver den nyligen signerade SSP.xap och den nya PFX-filen som du har fått från Symantec eller den programregistreringstoken som har skapats med den nya PFX-filen.

4.  När överföringen är klar, ta bort den gamla företagsportalen i arbetsytan **Programvara** i Intune hanteringskonsol.

5.  Signera alla branschspecifika program för företaget en gång till med samma certifikat. Överför och ersätt sedan befintliga program.

Att tillhandahålla en signerad SSP.xap-fil är för närvarande det enda sättet att tillhandahålla det uppdaterade kodsigneringscertifikatet. För att ge stöd åt signerade företagsappar måste du logga in och överföra en företagsportalapp, även om användarna kommer att installera företagsportalappen från Store.

## <a name="how-to-install-the-updated-certificate-for-windows-phone-81-and-later-devices"></a>Hur du installerar det uppdaterade certifikatet för Windows Phone 8.1 och senare enheter

1.  Hämta och signera den senaste företagsportalen för Windows Phone från Download Center här: [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Öppna din [Intune-administratörskonsol](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com) och välj **Admin** &gt; **Hantering av mobila enheter** &gt; **Windows Phone** och klicka på **Överför signerad app**.

3.  Överför den nyligen signerade företagsportalen. Du behöver den nyligen signerade SSP.xap och den nya PFX-filen som du har fått från Symantec eller den programregistreringstoken som har skapats med den nya PFX-filen.

4.  När uppladdningen är klar tar du bort den gamla företagsportalversionen i arbetsytan **Programvara**  .

5.  Signera alla nya och uppdaterade branschspecifika företagsappar med det nya certifikatet. Befintliga program behöver inte vara signeras på nytt eller omdistribueras.


### <a name="see-also"></a>Se även
[Konfigurera hantering av Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md)
[Konfigurera hantering av Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->

