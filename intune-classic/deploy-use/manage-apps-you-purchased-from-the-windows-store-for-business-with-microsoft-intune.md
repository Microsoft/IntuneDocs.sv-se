---
title: Hantera Microsoft Store för företag-appar
description: Anslut Microsoft Intune till Microsoft Store för företag om du vill hantera och distribuera volyminköpta appar från Intune-konsolen
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 02/02/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 50fc27efc34ab6c13fad714e41be0d87c5ab0df9
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Hantera appar som du har köpt från Microsoft Store för företag med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I [Microsoft Store för företag](https://www.microsoft.com/business-store) kan du söka efter och köpa appar för din organisation, separat eller i volym. Genom att ansluta butiken till Microsoft Intune kan du hantera volyminköpta appar från Intune-konsolen. Exempel:
* Du kan synkronisera listan över appar som du har köpt från Windows Store med Intune.
* Appar som är synkroniserade visas i administrationskonsolen för Intune och du kan distribuera dem precis som andra appar.
* Du kan spåra hur många licenser som är tillgängliga och hur många som används i administrationskonsolen för Intune.
* Intune blockerar distribution och installation av appar om det inte finns tillräckligt många tillgängliga licenser.

## <a name="before-you-start"></a>Innan du börjar
Granska följande information innan du börjar synkronisera och distribuera appar från Microsoft Store för företag:
* Du måste konfigurera Intune som utfärdare för hantering av mobila enheter för din organisation. Se [Krav för att registrera enheter i Microsoft Intune](prerequisites-for-enrollment.md) för mer information.
* Du måste ha registrerat dig för ett konto i Microsoft Store för företag.
* När du har associerat ett konto i Windows Store för företag med Intune kan du inte ändra till ett annat konto i framtiden.
* Appar som köpts från butiken kan inte manuellt läggas till i eller tas bort från Intune. De kan endast synkroniseras med Microsoft Store för företag.
* Intune synkroniserar bara online-licensierade appar som du har köpt från Microsoft Store för företag.
* Enheterna måste vara anslutna till Active Directory Domain Services eller arbetsplatsanslutna om du vill använda den här funktionen.
* Registrerade enheter måste använda 1511-versionen av Windows 10.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Koppla ditt konto för Microsoft Store för företag till Intune
Innan du aktiverar synkronisering i Intune-konsolen måste du konfigurera ditt Windows Store-konto för att använda Intune som ett hanteringsverktyg:
1. Se till att du loggar in i Windows Store för företag med samma klientkonto som du använder för att logga in på Intune.
2. Välj **Inställningar** > **Hanteringsverktyg** i Business Store.
3. Välj **Lägg till ett hanteringsverktyg** och välj **Microsoft Intune** på sidan Hanteringsverktyg.

> [!NOTE]
> Om du använder fler än ett hanteringsverktyg för att distribuera appar från Microsoft Store för företag kunde du tidigare bara koppla ett av dem till Microsoft Store för företag. Du kan nu koppla flera hanteringsverktyg till butiken, exempelvis Intune och Configuration Manager.

Du kan nu fortsätta och konfigurera synkronisering i Intune-konsolen.

## <a name="configure-synchronization"></a>Konfigurera synkronisering

1. Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och välj **Admin**.
2. På arbetsytan **Administration** expanderar du **Hantering av mobila enheter** > **Windows** och väljer sedan **Store för företag**.
3. Gör följande på sidan **Microsoft Store för företag**:
 * Klicka på länken till registreringen för Microsoft Store för företag om du inte redan har gjort det.
 * När du har registrerat dig väljer du **Konfigurera synkronisering**.
4. Välj **Aktivera synkronisering för Microsoft Store för företag** i dialogrutan **Konfigurera appsynkronisering för Microsoft Store för företag**.
5. Välj det språk du vill att appar från Microsoft Store för företag ska visas med i Intune-konsolen från listrutan **Språk**. De kommer att installeras i slutanvändarens språk när det är tillgängligt oavsett vilket språk de visas i.
6. Klicka på **OK**.

## <a name="synchronize-apps"></a>Synkronisera appar

1. På sidan **Microsoft Store för företag** väljer du **Synkronisera nu** för att synkronisera de appar som du har köpt från butiken med Intune.
2. Välj **Appar** > **Volyminköpsappar** på arbetsytan **Appar**, så ser du de appar du kan distribuera, och du kan kontrollera att dina inköpta appar har importerats korrekt. Appar i den här noden visas med det totala antalet licenser som du äger, och antalet licenser som finns tillgängliga.
Du kan t.ex. köpa företagsportalsappen (licensierad online) från Microsoft Store för företag, synkronisera den med Intune-konsolen och distribuera den som en obligatorisk app till de obligatoriska Windows 10-enheterna. 


## <a name="deploy-apps"></a>Distribuera appar

Du kan distribuera appar från Windows Store på samma sätt som du distribuerar andra Intune-appar. Mer information finns i [Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).
När du distribuerar en app från Microsoft Store för företag används en licens för varje användare som installerar appen. Om du använder alla tillgängliga licenser för en distribuerad app kommer du inte att kunna distribuera fler kopior. Du måste vidta någon av följande åtgärder:
* Avinstallera appen från vissa enheter.
* Minska omfånget för den aktuella distributionen för att fokusera på de användare som du har tillräckligt många licenser för.
* Köpa fler kopior av appen från Microsoft Store för företag.

> [!Important]
> Distribuerade appar är bara tillgängliga för den användare som ursprungligen registrerat enheten. Inga andra användare kan komma åt appen.


### <a name="see-also"></a>Se även
[Lägg till appar för mobila enheter i Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)
