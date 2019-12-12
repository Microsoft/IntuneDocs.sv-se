---
title: Felsöka registreringen av din Windows 10-enhet | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/11/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 4ab630b6-47ff-443b-a2a5-be23388bcea7
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: bbc251479652079cb33b1ca4dd08103103b91aa9
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508192"
---
# <a name="troubleshoot-your-windows-10-device-enrollment"></a>Felsöka registreringen av din Windows 10-enhet
Om du har registrerat enheten, men ändå inte kan komma åt e-post och filer för ditt arbete eller din skola kan du prova följande felsökningssteg.  

1. Ta en titt på de två följande skärmarna och se om någon av dem liknar vad du ser på din enhet. Följ de steg som gäller för den skärm som du ser på din enhet.

    Om denna skärm visas följer du stegen i [Felsökningssteg att följa om du ser Åtkomst för arbete eller skola](#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).

    ![settings-accounts-access-work-or-school](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    Om denna skärm visas följer du stegen i [Felsökningssteg att följa om du ser Ditt konto](#troubleshooting-steps-to-follow-if-you-see-your-account).

    ![settings-accounts-your-account](./media/W10-enroll-2-accounts-your-account.png)

## <a name="troubleshooting-steps-to-follow-if-you-see-access-work-or-school"></a>Felsökningssteg att följa om du ser ”Åtkomst till arbete eller skola”

1. Om du följde stegen ovan men ändå inte har åtkomst till din e-post eller dina filer på arbetet eller i skolan går du tillbaka till **Åtkomst för arbete eller skola**.

2. Gör något av följande:

   - Om du ser en anslutning som liknar bilden nedan, så tryck på den och kontrollera sedan om alternativen Hantera, Information och Koppla från visas. Om dessa alternativ visas innebär det att du är registrerad och ansluten.

     ![validate-successful-enrollment](./media/w10-enroll-rs1-validate-successful-enrollment.png)

   - Om anslutningsinformationen ovan inte visas, eller om vissa alternativ saknas, trycker du på **Anslut**. Anslut sedan genom att logga in med dina autentiseringsuppgifter för arbetsplats- eller skolkonto.  

## <a name="troubleshooting-steps-to-follow-if-you-see-your-account"></a>Felsökningssteg att följa om du ser ”Ditt konto”

Om du följde stegen ovan men ändå inte har åtkomst till din e-post, dina filer eller annan information på arbetet eller i skolan, så gå tillbaka till **Konton** och tryck på **Åtkomst till arbetsplats**.

- Om du ser ditt arbets- eller skolkonto är du ansluten.  

- Om du inte ser ditt arbets- eller skolkonto trycker du på **Anslut** och loggar in med dina användaruppgifter.

## <a name="troubleshooting-steps-to-follow-if-you-see-set-up-a-work-or-school-account"></a>Felsökningssteg att följa om du ser ”Skapa ett arbets- eller skolkonto”

Om du ser meddelandet <strong>Det gick inte att automatiskt identifiera en hanteringsslutpunkt som matchar användarnamnet. Kontrollera användarnamnet och försök igen. Ange URL:en till hanteringsslutpunkten om du känner till den.</strong> ska du inte försöka ange ditt användarnamn och lösenord på nytt. Om det fortfarande inte fungerar ska du kontakta företagets support för att få information om den webbplats du ska ange i textrutan <strong>Hanteringsslutpunkt</strong>. Detta är en webbplats som troligtvis har formatet <strong>www.dittföretag.onmicrosoft.com</strong>.

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).
