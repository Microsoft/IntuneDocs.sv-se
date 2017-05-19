---
title: "Distribuera och övervaka en efterlevnadsprincip | Microsoft Docs"
description: "Följ instruktionerna i det här avsnittet om du vill distribuera och övervaka en enhetsefterlevnadsprincip."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 59c107b9431d4e2925b13d09ab3e01a25c8351fa


---

# <a name="deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune"></a>Distribuera och övervaka en enhetsefterlevnadsprincip i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="deploy-a-compliance-policy"></a>Distribuera en efterlevnadsprincip
Distribuera efterlevnadsprincipen som du har [skapat](create-a-device-compliance-policy-in-microsoft-intune.md) till en eller flera grupper av användare i din organisation. När en efterlevnadsprincip distribueras till en användare så kontrolleras om användarens enheter uppfyller efterlevnadskraven.

1.  På arbetsytan **Princip** markerar du den princip som du vill distribuera och väljer sedan **Hantera distribution**.
![Skärmbild av sidan efterlevnadsprincip som visar menyalternativet Hantera distribution överst](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  I dialogrutan **Hantera distribution** väljer du en eller flera grupper dit du vill distribuera principen och väljer sedan **Lägg till** > **OK**.
![Skärmbild av dialogrutan Hantera distribution](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png) Använd Active Directory-grupper som du redan har skapat och synkroniserat med Intune, eller skapa dessa grupper manuellt i Intune-konsolen. Mer information om hur du distribuerar principer finns i [Distribuera en konfigurationsprincip](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Använd statussammanfattningen och aviseringarna på sidan **Översikt** på arbetsytan **Principer** för att identifiera problem med principer som kräver din uppmärksamhet. Dessutom visas en statussammanfattning på arbetsytan **Instrumentpanel** .

> [!IMPORTANT]
> Om du inte har distribuerat en efterlevnadsprincip och aktiverar en Exchange-princip för villkorlig åtkomst har alla målenheter åtkomst.

## <a name="monitor-the-compliance-policy"></a>Övervaka efterlevnadsprincipen

#### <a name="to-view-devices-that-do-not-conform-to-a-compliance-policy"></a>Om du vill visa enheter som inte följer en efterlevnadsprincip

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Grupper** > **Alla enheter**.

2.  Dubbelklicka på namnet på en enhet i listan med enheter.

3.  Välj fliken **Princip** för att se en lista över principerna för den enheten.

4.  I listrutan **Filter** väljer du **Uppfyller inte efterlevnadsprincip**.
![Skärmbild som visar en lista över alternativ i filterlistan](./media/intune-sa-3e-view-device-noncompliance.png)

#### <a name="to-view-the-health-attestation-reports"></a>Så här visar du hälsoattesteringsrapporterna

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Rapporter**.

2.  På sidan **Hälsoattesteringsrapport – Skapa en ny rapport** kan du visa en rapport med alla hälsoattesteringsdata för Windows 10 som Intune har samlat in. Du kan också skapa en rapport med en delmängd data med hjälp av filter. Filtren kan baseras på enhetstyp, operativsystem eller endast en delmängd datapunkter.

## <a name="how-intune-resolves-policy-conflicts"></a>Så här löser Intune principkonflikter
Principkonflikter kan uppstå när flera Intune-principer används på en enhet. Om principinställningarna överlappar varandra löser Intune eventuella konflikter med hjälp av följande regler:

-   Om de motstridiga inställningarna gäller en Intune-konfigurationsprincip och en efterlevnadsprincip, prioriteras inställningarna i efterlevnadsprincipen framför inställningarna i konfigurationsprincipen. Detta gäller även om inställningarna i konfigurationsprincipen är säkrare.

-   Om du har distribuerat flera efterlevnadsprinciper använder Intune den säkraste av dessa principer.

## <a name="next-steps"></a>Nästa steg
Information om hur du använder efterlevnadsprincipen med principer för villkorlig åtkomst för att kontrollera åtkomsten till tjänster i din organisation finns i [Begränsa åtkomst till e-post och O365-tjänster](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).


### <a name="see-also"></a>Se även
[Introduktion till efterlevnadsprinciper för enheter i Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


