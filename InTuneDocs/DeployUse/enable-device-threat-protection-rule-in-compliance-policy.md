---
title: "Aktivera regeln för enhetsskydd i policyn för efterlevnad | Microsoft Intune"
description: "Aktivera regeln för skydd mot mobila hot i enhetspolicyn för efterlevnad."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fa05027e1785bb27a607aa9e31b685107a84f63f
ms.openlocfilehash: 3de68238515a2584b6f1a5785e13688097468415


---

# Aktivera regeln för skydd mot enhetshot i policyn för efterlevnad
Intune med Lookout mobilt skydd ger dig möjligheter att identifiera mobila hot och göra riskbedömningar på enheten. Du kan skapa en regler för policy för efterlevnad som inkluderar riskbedömningen för att avgöra om enheten är kompatibel. Du kan sedan använda den villkorliga åtkomstprincipen för att tillåta eller blockera åtkomst till Exchange, SharePoint och andra tjänster utifrån enhetens efterlevnad.

Om du vill att Lookout MTP-hotidentifiering ska påverka policyn för efterlevnad för enheten:

* Regeln för **Skydd mot hot på enhet** måste vara aktiverad i policyn för efterlevnad.

* Sidan **Status för Lookout** i **Intune-administratörskonsolen** måste visa **Aktiv**. Se avsnittet [Enable Lookout MTP connection in Intune](enable-lookout-mtp-connection-in-intune.md) (Aktivera Lookout MTP-anslutningen i Intune) för mer information och anvisningar om hur du aktiverar Lookout-integration.


Innan du skapar regeln för skydd mot enhetshot i policyn för efterlevnad rekommenderar vi att du [konfigurerar din prenumeration med Lookout MTP](set-up-your-subscription-with-lookout-mtp.md), [aktiverar anslutningen till Lookout i Intune](enable-lookout-mtp-connection-in-intune.md) och [konfigurerar Lookout for work-appen](configure-and-deploy-lookout-for-work-apps.md). Regeln för efterlevnad gäller endast efter att installationen har slutförts.

Om du vill aktivera regeln för skydd mot enhetshot kan du antingen använda en befintlig policy för efterlevnad eller skapa en ny.

Som en del av installationsprogrammet för Lookout MTP har du skapat en princip som klassificerar hot enligt nivåerna hög, medel och låg i [Lookout MTP-konsolen](https://aad.lookout.com). I policyn för efterlevnad för Intune använder du hotnivån för att ställa in den maximalt tillåtna hotnivån.

På sidan **Policy för efterlevnad** i **Intune-administratörskonsolen** går du till **Enhetens hälsotillstånd** och aktiverar regeln för **Skydd mot hot på enhet**. Välj sedan den högsta tillåtna hotnivån, som är en av följande:
* **Ingen (skyddad)**: Det här är det säkraste alternativet.  Detta innebär att enheten inte kan ha några hot.  Om något hot identifieras på enheten kommer den utvärderas som icke-kompatibel.  
* **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
* **Medel**: Enheten utvärderas som kompatibel om hoten som hittas på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
* **Hög**: Det här alternativet är minst säkert. I grunden innebär detta att alla hotnivåer är tillåtna och kanske är detta endast användbart om du använder den här lösningen för rapportering.

![skärmbild som visar regeln för skydd mot enhetshot i ](../media/mtp/mtp-compliance-policy-rule.png)

![skärmbild som visar alternativet för hotnivåer för regeln för skydd mot enhetshot](../media/mtp/mtp-compliance-policy-setting.png)

Om du skapar principer för villkorlig åtkomst till Office 365 och andra tjänster kommer ovanstående utvärdering av efterlevnad beaktas och icke-kompatibla enheter kommer inte att få åtkomst till företagsresurser förrän hotet har lösts.

Du kan se kompatibilitetstillståndet för en enhet på sidan **All Devices** (Alla enheter) i **Intune-administratörskonsolen**.

![skärmbild som visar enhetssidan i Intune-administratörskonsolen som visar kompatibilitetstillståndet för en enhet](../media/mtp/mtp-device-status-intune-console.png)

## Nästa steg
* Skapa princip för villkorlig åtkomst
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange On-premises](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype för företag – Online](restrict-access-to-skype-for-business-online-with-microsoft-intune,md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Sep16_HO3-->


