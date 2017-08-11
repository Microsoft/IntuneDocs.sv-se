---
title: Registrera Android-enheter i Intune
titleSuffix: Intune on Azure
description: "Läs hur du registrerar Android-enheter i Intune.”"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 183e60af4d6174c18fc3883f2cdd9827505d2aba
ms.sourcegitcommit: 2ee1e8248814d74cef80b609a8e43f59fa0b2618
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/09/2017
---
# <a name="enroll-android-devices"></a>Registrera Android-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som Intune-administratör kan du hantera Android-enheter, inklusive Samsung Knox Standard-enheter. Du kan också hantera arbetsprofilen på [Android for Work-enheter](#enable-enrollment-of-android-for-work-devices).

Enheter som kör Samsung KNOX Standard har stöd för hantering av flera användare med Intune. Det innebär att användarna kan logga in och ut från enheten med sina autentiseringsuppgifter för Azure AD. Enheten hanteras centralt oavsett om den används eller inte. När användarna loggar in får de tillgång till appar och dessutom verkställs eventuella principer som gäller för dem. Alla appdata rensas när användaren loggar ut.

## <a name="prerequisite"></a>Krav

Du måste ange MDM-utfärdare för **Microsoft Intune** så att du kan hantera mobila enheter. Fler anvisningar finns i [Ange MDM-utfärdare](mdm-authority-set.md). Du anger det här objektet bara när du konfigurerar Intune för hantering av mobila enheter.

## <a name="set-up-android-enrollment"></a>Konfigurera Android-registrering

Som standard tillåter Intune registrering av Android- och Samsung Knox Standard-enheter.

Se [Ange begränsningar för enhetstyp](enrollment-restrictions-set.md) för att blockera Android-enheter eller endast blockera personligt ägda Android-enheter från registrering.

Användarna måste registrera sina enheter genom att hämta Intunes företagsportalapp som är tillgänglig från Google Play och sedan öppna appen och följa anvisningarna för att registrera sig för att aktivera hantering av enheter. När Android-enheter hanteras kan du [tilldela efterlevnadsprinciper](compliance-policy-create-android.md), [hantera appar](app-management.md) med mera.

## <a name="enable-enrollment-of-android-for-work-devices"></a>Aktivera registrering av Android for Work-enheter

Om du vill aktivera hantering av arbetsprofilen på enheter som har [stöd för Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012), måste du lägga till en Android for Work-bindning i Intune. Om du vill registrera enheter som har stöd för Android for Work men som tidigare registrerades som vanliga Android-enheter, måste enheterna avregistreras och sedan registreras igen.

## <a name="add-android-for-work-binding-for-intune"></a>Lägg till Android for Work-bindning för Intune

1. **Konfigurera Intune MDM**<br>
Om du inte redan gjort det, förbereder du för hantering av mobila enheter genom att ange **Microsoft Intune** som [utfärdare för hantering av mobila enheter](mdm-authority-set.md).
2. **Konfigurera Android for Work-bindning**<br>
    Som Intune-administratör väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune** i Azure-portalen.

    1. På bladet **Intune** väljer du **Enhetsregistrering**, > **Android for Work-registrering**. Klicka sedan på **Konfigurera** för att öppna Google Play-webbplatsen Android for Work. Det här kommer att öppna en ny flik i webbläsaren.
  ![Skärmbild som visar länk till Konfigurera Android for Work-bindning](./media/android-work-bind.png)

    2. **Logga in på Google**<br>
   Logga in på Googles inloggningssida med det Google-konto som ska associeras med alla hanteringsuppgifter för Android for Work för den här klienten. Det här är det Google-konto som delas av organisationens IT-administratörer och som används för att hantera och publicera appar i Play for Work-konsolen.

    3. **Ange organisationsinformation**<br>
   Ange företagets namn för **Organisationsnamn**. *Microsoft Intune* ska visas som **Enterprise mobility management (EMM)-provider**. Godkänn Android for Work-avtalet och klicka sedan på **Bekräfta**. Din begäran kommer att behandlas.

## <a name="specify-android-for-work-enrollment-settings"></a>Ange inställningar för registrering av Android for Work
   Android for Work stöds endast på vissa Android-enheter. Se Googles [Android for Work requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") (Krav för Android for Work). Alla enheter som har stöd för Android for Work stöder även konventionell Android-hantering.  Intune gör det möjligt att ange hur enheter med stöd för Android for Work ska hanteras:

   - **Manage all devices as Android** (Hantera alla enheter som Android) – Alla Android-enheter, inklusive enheter som stöder Android for Work, registreras som konventionella Android-enheter.
   - **Manage all devices as Android for Work** (Hantera alla enheter som Android for Work) – Alla enheter som stöder Android for Work registreras som Android for Work-enheter. Alla Android-enheter som inte stöder Android for Work registreras som konventionella Android-enheter.
   - **Manage supported devices for users only in these user groups as Android for Work** (Hantera enheter som stöds endast för användare i dessa användargrupper som Android for Work) – Gör det möjligt att rikta Android for Work-hantering till en begränsad uppsättning användare. Endast medlemmar i de valda grupperna som registrerar en enhet som har stöd för Android for Work registreras som Android for Work-enheter. Alla andra registreras som Android-enheter. Detta är användbart vid pilottester av Android for Work.

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurserna

Du måste instruera slutanvändarna att de ska gå till Google Play för att hämta Intune-företagsportalappen, öppna appen och följa anvisningarna för att registrera sina enheter. Appen hjälper användarna genom registreringsprocessen och förklarar vad de kan förvänta sig och vad IT-administratörer kan och inte kan se på deras enheter.

Du kan även skicka dem en länk till stegen för registrering online: [Registrera en Android-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android).

Information om andra slutanvändaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](end-user-educate.md)
- [Använda en Android-enhet med Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbinding-your-android-for-work-administrative-account"></a>Ta bort bindning för ditt administratörskonto för Android for Work

Du kan inaktivera Android for Work-registrering och hantering. Klicka på **Ta bort bindning** i Intune-administrationskonsolen för att ta bort alla registrerade Android for Work-enheter från registreringen och ta bort relationen mellan Android for Work-kontot och Intune.

### <a name="how-to-unbind-an-android-for-work-account"></a>Så här tar du bort bindningen för ett Android for Work-konto

1. **Ta bort en Android for Work-bindning**<br>
    Som Intune-administratör väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune** i Azure-portalen.  På bladet **Intune** väljer du **Enhetsregistrering**, > **Android for Work-registrering** och klickar sedan på **Ta bort bindning**.

2. **Godkänn borttagningen av Android for Work-bindningen**<br>
  Klicka på **Ja** att ta bort bindningen och avregistrera alla Android for Work-enheter från Intune.
