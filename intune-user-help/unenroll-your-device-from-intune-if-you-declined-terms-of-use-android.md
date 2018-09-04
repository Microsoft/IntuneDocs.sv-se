---
title: Ta bort enheten från hanteringen om du inte godkände användningsvillkoren | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 24aa876b7100f0f802ab3723cedf92a32bc7e9d7
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43149715"
---
# <a name="remove-your-device-from-management-if-you-declined-terms-of-use"></a>Ta bort enheten från hanteringen om du inte godkände ”Användningsvillkor”

Om du inte godkände användningsvillkoren när du försökte logga in på företagsportalappen, kan du inte logga in i företagsportalappen vid framtida försök. Du måste därför använda dessa anvisningar för att ta bort enheten från Intune.

När du avinstallerar företagsportalappen tar du även bort enheten från Intune. Enheten kommer inte längre att kunna komma åt företagsresurser. Mer information om vad som händer när du tar bort enheten från hantering finns i [Vad händer om du avregistrerar din enhet från Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Innan du kan avinstallera företagsportalappen måste du välja inställningen **Enhetsadministratörer** och inaktivera **Företagsportalen**. Anvisningarna kan skilja sig en aning beroende på vilken Android-enhet du har.

## <a name="removing-the-device-from-the-company-portal-app"></a>Ta bort enheten från företagsportalappen

Så här tar du bort enheten från Intune och avinstallerar företagsportalappen:

1.  Gå till **Inställningar** &gt; **Säkerhet &amp; Skärmlås** &gt; **Enhetsadministratörer**.

    Om du slutför det här steget avregistreras enheten helt.

2.  Avmarkera kryssrutan bredvid, eller inaktivera, **Företagsportal**.

    Nu kan du installera företagsportalappen.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Ta bort data som samlas in av företagsportalappen

Så här tar du bort alla data som företagsportalappen för Android lagrar på din enhet:

  - Rensa appdata i Program -> Klicka på appen -> knappen ”Rensa data”
  - Ta bort mappen \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal


Behöver du fortfarande hjälp? Kontakta företagets support (du hittar kontaktinformation på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980)) eller skriv till <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having unenrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-teamet</a>.
