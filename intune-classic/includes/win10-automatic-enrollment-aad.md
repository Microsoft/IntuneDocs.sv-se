---
ms.openlocfilehash: fbfff91d2993becc99e2132285bef78d245ff50e
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61497948"
---
## <a name="enable-windows-10-automatic-enrollment"></a>Aktivera automatisk registrering i Windows 10

Med automatisk registrering kan användarna registrera sina Windows 10-enheter i Intune genom att lägga till sina arbetskonton till sina egna enheter, eller ansluta sina företagsägda enheter till din Azure Active Directory. Användarens enhet registreras och ansluts till Azure Active Directory i bakgrunden. När enheten har registrerats hanteras den med Intune.

**Förutsättningar**
- Azure Active Directory Premium-prenumeration ([provprenumeration](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune-prenumeration


### <a name="configure-automatic-mdm-enrollment"></a>Konfigurera automatisk MDM-registrering

1. Logga in på [Azure-hanteringsportalen](https://portal.azure.com) (https://manage.windowsazure.com) och välj **Azure Active Directory**.

   ![Skärmbild av Azure-portalen](../media/auto-enroll-azure-main.png)

2. Välj **Mobility (MDM och MAM)**.

   ![Skärmbild av Azure-portalen](../media/auto-enroll-mdm.png)

3. Välj **Microsoft Intune**.

   ![Skärmbild av Azure-portalen](../media/auto-enroll-intune.png)

4. Konfigurera **MDM-användaromfattning**. Ange vilka användares enheter som ska hanteras av Microsoft Intune. Dessa användares Windows 10-enheter registreras automatiskt för hantering med Microsoft Intune.

   - **Inga**
   - **Vissa**
   - **Alla**

   ![Skärmbild av Azure-portalen](../media/auto-enroll-scope.png)

5. Använd standardvärdena för följande URL:er:
   - **Webbadress till MDM-användarvillkor**
   - **Webbadress till MDM-identifiering**
   - **Webbadress till MDM-kompatibilitet**

6. Välj **Spara**.

Som standard är inte tvåfaktorautentisering aktiverat för tjänsten. Tvåfaktorautentisering rekommenderas dock när du registrerar en enhet. Innan du kräver en tvåfaktorautentisering för tjänsten måste du konfigurera en provider för tvåfaktorautentisering i Azure Active Directory och konfigurera dina användarkonton för multifaktorautentisering. Se [Komma igång med Azure Multi-Factor Authentication-servern](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
