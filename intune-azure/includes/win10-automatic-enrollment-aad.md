## <a name="enable-windows-10-automatic-enrollment"></a>Aktivera automatisk registrering i Windows 10

Den automatiska registreringen gör att användarna kan registrera sina företagsägda eller privata Windows 10-datorer och Windows 10 Mobile-enheter i Intune genom att lägga till ett arbetskonto eller skolkonto och godkänna att datorn/enheten hanteras. Svårare än så är det inte. Användarens enhet registreras och ansluts till Azure Active Directory i bakgrunden. När enheten har registrerats hanteras den med Intune.

**Krav**
- Azure Active Directory Premium-prenumeration ([provprenumeration](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune-prenumeration


### <a name="configure-automatic-mdm-enrollment"></a>Konfigurera automatisk MDM-registrering

1. Logga in på [Azure-hanteringsportalen](https://portal.azure.com) (https://manage.windowsazure.com) och välj **Azure Active Directory**.

  ![Skärmbild av Azure-portalen](../media/auto-enroll-azure-main.png)

2. Välj **Mobility (MDM och MAM)**.

  ![Skärmbild av Azure-portalen](../media/auto-enroll-mdm.png)

3. Välj **Microsoft Intune**.

  ![Skärmbild av Azure-portalen](../media/auto-enroll-intune.png)

4. Konfigurera vilka användare som registreras automatiskt.

  ![Skärmbild av Azure-portalen](../media/auto-enroll-scope.png)

  Använd standardvärdena för följande URL:er:
  - **MDM-registrering**
  - **MDM-villkor**
  - **MDM-efterlevnad**

5. Ange vilka användares enheter som ska hanteras av Microsoft Intune. Dessa användares Windows 10-enheter registreras automatiskt för hantering med Microsoft Intune.

  - **Alla**
  - **GRUPPER**
  - **Inga**

6. Välj **Spara**.
