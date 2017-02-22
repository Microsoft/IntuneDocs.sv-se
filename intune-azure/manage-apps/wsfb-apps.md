---
title: "Hantera appar från Windows Store för företag | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Lär dig hur du kan synkronisera appar i Intune från Windows Store för företag och sedan tilldela och spåra dem."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a57ac0e6cb29dbfc87bb09c04bb372228a1d72be
ms.openlocfilehash: 2acb58a8fc71ae7f2e0bce127e709a678faa27cb

---

# <a name="how-to-manage-apps-you-purchased-from-the-windows-store-for-business"></a>Hantera appar som du har köpt från Windows Store för företag

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


[Windows Store för företag](https://www.microsoft.com/business-store) ger dig en plats för att söka efter och köpa appar för din organisation, enskilt eller i volym. Genom att ansluta butiken till Microsoft Intune, kan du hantera volyminköpta appar från Intune-portalen. Exempel:
* Du kan synkronisera listan över appar som du har köpt från Windows Store med Intune.
* Appar som är synkroniserade visas i administrationskonsolen för Intune och du kan tilldela dem precis som andra appar.
* Du kan spåra hur många licenser som är tillgängliga och hur många som används i administrationskonsolen för Intune.
* Intune blockerar distribution och installation av appar om det inte finns tillräckligt många tillgängliga licenser.

## <a name="before-you-start"></a>Innan du börjar
Granska följande information innan du börjar synkronisera och distribuera appar från Windows Store för företag:
* Du måste konfigurera Intune som utfärdare för hantering av mobila enheter för din organisation.
* Du måste ha registrerat dig för ett konto i Windows Store för företag.
* När du har associerat ett konto i Windows Store för företag med Intune kan du inte ändra till ett annat konto i framtiden.
* Appar som köpts från butiken kan inte manuellt läggas till i eller tas bort från Intune. De kan endast synkroniseras med Windows Store för företag.
* Intune synkroniserar bara online-licensierade appar som du har köpt från Windows Store för företag.
* För att använda den här funktionen måste enheterna vara anslutna till Active Directory Domain Services eller arbetsplatsanslutna.
* Registrerade enheter måste använda 1511-versionen av Windows 10 eller senare.

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>Koppla ditt konto för Windows Store för företag till Intune
Innan du aktiverar synkronisering i Intune-konsolen måste du konfigurera ditt Windows Store-konto för att använda Intune som ett hanteringsverktyg:
1. Se till att du loggar in i Windows Store för företag med samma klientkonto som du använder för att logga in på Intune.
2. Välj **Inställningar** > **Hanteringsverktyg** i Business Store.
3. Välj **Lägg till ett hanteringsverktyg** och välj **Microsoft Intune** på sidan Hanteringsverktyg.

> [!NOTE]
> Om du använder fler än ett hanteringsverktyg för att distribuera Windows Store för affärsappar kunde du tidigare bara koppla ett av dem till Windows Store för företag. Du kan nu koppla flera hanteringsverktyg till butiken, exempelvis Intune och Configuration Manager.

Du kan nu fortsätta och konfigurera synkronisering i Intune-konsolen.

## <a name="configure-synchronization"></a>Konfigurera synkronisering

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Hantera appar** på **Intune**-bladet.
1. På bladet **Mobilappar**, väljer du **Installationsprogrammet** > **Windows Store för företag**.
2. Klicka på **Aktivera**.
3. Om du inte redan gjort det, klickar du på länken för att registrera Windows Store för företag och kopplar kontot såsom beskrivs tidigare.
5. Välj det språk du vill att appar från Windows Store för företag ska visas i Intune-portalen från listrutan **Språk**. De kommer att installeras i slutanvändarens språk när det är tillgängligt oavsett vilket språk de visas i.
6. Klicka på **Sync** för att hämta appar som du har köpt från Windows Store i Intune.

## <a name="synchronize-apps"></a>Synkronisera appar

1. I arbetsbelastningen **Hantera appar**, väljer du **Installationsprogrammet** > **Windows Store för företag**.
2. Klicka på **Sync** för att hämta appar som du har köpt från Windows Store i Intune.

## <a name="assign-apps"></a>Tilldela appar

Du kan tilldela appar från Windows Store på samma sätt som du distribuerar andra Intune-appar. Mer information finns i [Tilldela appar till grupper med Microsoft Intune](deploy-apps.md). I stället för att tilldela appar från sidan **Alla appar** kan du tilldela dem från sidan **Licensierade appar**.

När du tilldelar en app från Windows Store för företag används en licens för varje användare som installerar appen. Om du använder alla tillgängliga licenser för en distribuerad app kommer du inte att kunna distribuera fler kopior. Du måste vidta någon av följande åtgärder:
* Avinstallera appen från vissa enheter.
* Minska omfånget för den aktuella distributionen för att fokusera på de användare som du har tillräckligt många licenser för.
* Köpa fler kopior av appen från Windows Store för företag.

> [!Important]
> Distribuerade appar är bara tillgängliga för den användare som ursprungligen registrerat enheten. Inga andra användare kan komma åt appen.



<!--HONumber=Feb17_HO1-->


