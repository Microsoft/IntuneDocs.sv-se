---
title: "Hantera Windows Store för företag-appar | Microsoft Docs"
description: "Anslut Microsoft Intune till Windows Store för företag om du vill hantera och distribuera volyminköpsappar från Intune-konsolen"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: a57ac0e6cb29dbfc87bb09c04bb372228a1d72be
ms.openlocfilehash: 34e9ce6a5c0b7cb912a54644e6323574c2e041a7


---

# <a name="manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>Hantera appar som du har köpt från Windows Store för företag med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[Windows Store för företag](https://www.microsoft.com/business-store) ger dig en plats för att söka efter och köpa appar för din organisation, enskilt eller i volym. Genom att ansluta butiken till Microsoft Intune kan du hantera volyminköpta appar från Intune-konsolen. Exempel:
* Du kan synkronisera listan över appar som du har köpt från Windows Store med Intune.
* Appar som är synkroniserade visas i administrationskonsolen för Intune och du kan distribuera dem precis som andra appar.
* Du kan spåra hur många licenser som är tillgängliga och hur många som används i administrationskonsolen för Intune.
* Intune blockerar distribution och installation av appar om det inte finns tillräckligt många tillgängliga licenser.

## <a name="before-you-start"></a>Innan du börjar
Granska följande information innan du börjar synkronisera och distribuera appar från Windows Store för företag:
* Du måste konfigurera Intune som utfärdare för hantering av mobila enheter för din organisation. Se [Krav för att registrera enheter i Microsoft Intune](prerequisites-for-enrollment.md) för mer information.
* Du måste ha registrerat dig för ett konto i Windows Store för företag.
* När du har associerat ett konto i Windows Store för företag med Intune kan du inte ändra till ett annat konto i framtiden.
* Appar som köpts från butiken kan inte manuellt läggas till i eller tas bort från Intune. De kan endast synkroniseras med Windows Store för företag.
* Intune synkroniserar bara online-licensierade appar som du har köpt från Windows Store för företag.
* Enheterna måste vara anslutna till Active Directory Domain Services eller arbetsplatsanslutna om du vill använda den här funktionen.
* Registrerade enheter måste använda 1511-versionen av Windows 10.

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>Koppla ditt konto för Windows Store för företag till Intune
Innan du aktiverar synkronisering i Intune-konsolen måste du konfigurera ditt Windows Store-konto för att använda Intune som ett hanteringsverktyg:
1. Se till att du loggar in i Windows Store för företag med samma klientkonto som du använder för att logga in på Intune.
2. Välj **Inställningar** > **Hanteringsverktyg** i Business Store.
3. Välj **Lägg till ett hanteringsverktyg** och välj **Microsoft Intune** på sidan Hanteringsverktyg.

> [!NOTE]
> Om du använder fler än ett hanteringsverktyg för att distribuera Windows Store för affärsappar kunde du tidigare bara koppla ett av dem till Windows Store för företag. Du kan nu koppla flera hanteringsverktyg till butiken, exempelvis Intune och Configuration Manager.

Du kan nu fortsätta och konfigurera synkronisering i Intune-konsolen.

## <a name="configure-synchronization"></a>Konfigurera synkronisering

1. Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och välj **Admin**.
2. På arbetsytan **Administration** expanderar du **Hantering av mobila enheter** > **Windows** och väljer sedan **Store för företag**.
3. Gör följande på sidan **Windows Store för Business**:
 * Klicka på länken till registreringen för Windows Store för företag om du inte redan gjort det.
 * När du har registrerat dig väljer du **Konfigurera synkronisering**.
4. Välj **Aktivera synkronisering för Windows Store för företag** i dialogrutan **Konfigurera appsynkronisering för Windows Store för företag**.
5. Välj det språk du vill att appar från Windows Store för företag ska visas i Intune-konsolen från listrutan **Språk**. De kommer att installeras i slutanvändarens språk när det är tillgängligt oavsett vilket språk de visas i.
6. Klicka på **OK**.

## <a name="synchronize-apps"></a>Synkronisera appar

1. På sidan **Windows Store för företag** väljer du **Synkronisera nu** för att synkronisera de appar som du har köpt från Windows Store med Intune.
2. Välj **Appar** > **Volyminköpsappar** på arbetsytan **Appar**, så ser du de appar du kan distribuera, och du kan kontrollera att dina inköpta appar har importerats korrekt. Appar i den här noden visas med det totala antalet licenser som du äger, och antalet licenser som finns tillgängliga.
Du kan t.ex. köpa företagsportalsappen (licensierad online) från Windows Store för företag, synkronisera den med Intune-konsolen och distribuera den som en obligatorisk app till de obligatoriska Windows 10-enheterna. 


## <a name="deploy-apps"></a>Distribuera appar

Du kan distribuera appar från Windows Store på samma sätt som du distribuerar andra Intune-appar. Mer information finns i [Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).
När du distribuerar en app från Windows Store för företag används en licens för varje användare som installerar appen. Om du använder alla tillgängliga licenser för en distribuerad app kommer du inte att kunna distribuera fler kopior. Du måste vidta någon av följande åtgärder:
* Avinstallera appen från vissa enheter.
* Minska omfånget för den aktuella distributionen för att fokusera på de användare som du har tillräckligt många licenser för.
* Köpa fler kopior av appen från Windows Store för företag.

> [!Important]
> Distribuerade appar är bara tillgängliga för den användare som ursprungligen registrerat enheten. Inga andra användare kan komma åt appen.


### <a name="see-also"></a>Se även
[Lägg till appar för mobila enheter i Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)



<!--HONumber=Feb17_HO1-->


