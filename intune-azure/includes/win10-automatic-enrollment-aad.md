## <a name="set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium"></a>Konfigurera Windows 10 och Windows 10 Mobile, automatisk registrering med Azure Active Directory Premium

Den automatiska registreringen gör att användarna kan registrera sina företagsägda eller privata Windows 10-datorer och Windows 10 Mobile-enheter i Intune genom att lägga till ett arbetskonto eller skolkonto och godkänna att datorn/enheten hanteras. Svårare än så är det inte. Användarens enhet registreras och ansluts till Azure Active Directory i bakgrunden. När enheten har registrerats hanteras den med Intune.

**Krav**
- Azure Active Directory Premium-prenumeration ([provprenumeration](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune-prenumeration


### <a name="configure-automatic-mdm-enrollment"></a>Konfigurera automatisk MDM-registrering

1. Gå till noden **Active Directory** på [Azure-hanteringsportalen](https://portal.azure.com) (https://manage.windowsazure.com) och välj din katalog.

2. Välj fliken **Program**. **Microsoft Intune** visas i listan över program.

    ![Azure AD-appar med Microsoft Intune](../media/aad-intune-app.png)

3. Välj pilen för **Microsoft Intune**. En sida öppnas där du kan konfigurera Microsoft Intune.

4. Välj **Konfigurera** och börja konfigurera automatisk MDM-registrering med Microsoft Intune.

5. Ange URL: er för Intune:

  - **MDM Enrollment URL** (URL för MDM-registrering) – Använd standardvärdet.
  - **URL för MDM-villkor** – Använd standardvärdet. Denna URL visar villkoren för användarna när de registrerar enheter.
  - **URL för MDM-efterlevnad** – Använd standardvärdet. Om en enhet inte är kompatibel visas ett **Åtkomst nekas**-meddelande med denna URL. URL:en pekar till en sida som förklarar för användarna varför deras enhet inte uppfyller kraven för principen och vad de kan göra för att enheten ska uppfylla kraven igen.

6.  Ange vilka användares enheter som ska hanteras av Microsoft Intune. Dessa användares Windows 10-enheter registreras automatiskt för hantering med Microsoft Intune.

  - **Alla**
  - **GRUPPER**
  - **Inga**

7. Välj **Spara**.


<!--HONumber=Feb17_HO2-->


