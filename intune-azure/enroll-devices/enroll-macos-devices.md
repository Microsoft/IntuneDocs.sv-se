---
title: "Registrera macOS-enheter i Intune | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs mer om hur du registrerar macOS-enheter i Intune Azure-förhandsversionen."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 1/3/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2affcdbcdfcd690d671c7b20f9d1e14a74f764
ms.openlocfilehash: 171175689adca027181f3da4d05222117de97e13


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Registrera macOS-enheter i Intune Azure-förhandsversionen

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Du kan hantera macOS-enheter om du är Intune-administratör. Som standard tillåter Azure-portalen att användarna registrerar sina macOS-enheter. Du behöver bara säga till användarna att gå till [företagsportalens webbplats](http://portal.manage.microsoft.com) och registrera sin macOS-enhet. 

## <a name="prerequisites"></a>Förutsättningar

Uppfyll följande krav innan du konfigurerar registreringen av macOS-enheter:

- [Konfigurera domäner](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Ange MDM-utfärdare](set-mdm-authority.md)
- [Skapa grupper](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Konfigurera företagsportalen](/intune-azure/manage-apps/company-portal-app.md)
- Tilldela användarlicenser i [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Hämta ett Apple MDM-pushcertifikat](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>Konfigurera registrering av macOS

Som standard har Intune redan ställts in så att registrering av macOS-enheter är tillåten. 

Om du vill visa inställningen för att tillåta eller blockera att macOS-enheter registreras, går du till Intune-bladet i Azure-portalen och väljer **Registrering** > **Registreringsbegränsningar**. 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurserna

Registreringsinstruktioner för slutanvändare finns i [Registrera din macOS-enhet i Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos). Registreringsprocessen förklarar för användarna vad de kan förvänta sig och vad IT-administratörer kan och inte kan se på deras enheter.

Information om andra slutanvändaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Använda en iOS- eller macOS-enhet med Intune](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)


<!--HONumber=Feb17_HO1-->


