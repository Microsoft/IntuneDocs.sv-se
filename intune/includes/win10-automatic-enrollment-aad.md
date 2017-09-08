## <a name="enable-windows-10-automatic-enrollment"></a>Aktivera automatisk registrering i Windows 10

Med automatisk registrering kan användarna registrera sina Windows 10-enheter i Intune. Användarna registrerar genom att lägga till sina arbetskonton till sina personligt ägda enheter eller genom att ansluta sina företagsägda enheter till Azure Active Directory. Enheten registreras och ansluts till Azure Active Directory i bakgrunden. När enheten har registrerats hanteras den med Intune.

**Krav**
- Azure Active Directory Premium-prenumeration ([provprenumeration](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune-prenumeration


### <a name="configure-automatic-mdm-enrollment"></a>Konfigurera automatisk MDM-registrering

1. Logga in på [Azure Portal](https://portal.azure.com) och välj **Azure Active Directory**.

  ![Skärmbild av Azure-portalen](../media/auto-enroll-azure-main.png)

2. Välj **Mobility (MDM och MAM)**.

  ![Skärmbild av Azure-portalen](../media/auto-enroll-mdm.png)

3. Välj **Microsoft Intune**.

  ![Skärmbild av Azure-portalen](../media/auto-enroll-intune.png)

4. Konfigurera **MDM-användaromfattning**. Ange vilka användares enheter som ska hanteras av Microsoft Intune. Dessa Windows 10-enheter kan registreras automatiskt för hantering med Microsoft Intune.

  - **Inga**
  - **Vissa**
  - **Alla**

   ![Skärmbild av Azure-portalen](../media/auto-enroll-scope.png)

5. Använd standardvärdena för följande URL:er:
    - **Webbadress till MDM-användarvillkor**
    - **Webbadress till MDM-identifiering**
    - **Webbadress till MDM-kompatibilitet**

    > [!IMPORTANT]
    > Om både **MAM-användaromfattning** och automatisk MDM-registrering (**MDM-användaromfattning**) är aktiverat för en grupp så är endast MAM aktiverat. Endast MAM läggs till för användare i gruppen när de arbetsplatsansluter personliga enheter. Enheter MDM-registreras inte automatiskt.

6. Välj **Spara**.

Som standard är inte tvåfaktorautentisering aktiverat för tjänsten. Tvåfaktorautentisering rekommenderas dock när du registrerar en enhet. För att aktivera tvåfaktorautentisering konfigurerar du en provider för tvåfaktorautentisering i Azure AD och konfigurerar dina användarkonton för multifaktorautentisering. Se [Komma igång med Azure Multi-Factor Authentication-servern](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
