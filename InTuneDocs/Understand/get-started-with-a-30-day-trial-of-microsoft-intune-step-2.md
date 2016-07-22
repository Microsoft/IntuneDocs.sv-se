---
# required metadata

title: Lägg till användare till din 30-dagars utvärderingsversion av Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9e40999b-46f7-447b-8974-72af82bec7ef

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Lägg till användare till din 30-dagars utvärderingsversion av Microsoft Intune
Nu när du har lagt upp ditt konto, ska du använda antingen guiden **Nya användare** för att lägga till enskilda användarkonton till Intune eller guiden **Lägg till användare i grupp** för att lägga till användare i grupp (se anvisningarna i det här avsnittet).  Det är viktigt att du förstår hur Intune hanterar administratörskonton innan du börjar.

En innehavaradministratör använder Office 365-administrationscentret för att lägga till användare i **gruppen Användare**i Microsoft Intunes. När man lägger till användare till  **gruppen Användare** tilldelas Intune-prenumerationslicenser till användare och användarna visas i Microsoft Intune-administrationskonsolen.

Administratörskonton för Intune skapas inte i Office 365-administrationscentret som vanliga användarkonton. I stället tilldelar du antingen läsbehörighet eller fullständig  administratörsbehörighet till användare med hjälp av administrationskonsolen på arbetsytan **Administration**  under **Administration Management**. Tjänsteadministratörer som endast har tilldelats läsbehörighet kan inte ändra Intune-inställningar, men de kan visa data och köra rapporter. Tjänsteadministratörer med fullständig åtkomst har all tillgänglig administrativ behörighet.

Du kan visa information om innehavaradministratören med hjälp av Intune-administrationskonsolen men du kan inte skapa innehavaradministratörer där. Som standard blir prenumerationsägaren innehavaradministratör för din Microsoft Intune-tjänst och har fullständig åtkomst till både Office 365-administrationscentret och Intune-administrationskonsolen. Vi rekommenderar att du skapar minst ett extra innehavaradministratörskonto genom att använda Office 365-administrationscentret för att delegera aktiviteter och se till att du inte blir utelåst från ditt Intune-tjänsteadministratörskonto om du skulle glömma lösenordet.

## Lägga till enskilda användarkonton
Använd följande steg om du vill skapa fler användarkonton för din utvärderingsinnehavare. Kom ihåg att varje användarkonto som du lägger till räknas av mot de 100 licenser som är tillgängliga som en del av din kostnadsfria Intune-utvärderingsversion.

1.  I [Office 365-administrationscentret](http://go.microsoft.com/fwlink/p/?LinkId=698854) väljer du **Lägg till användare** &gt; **Ny**&gt; **Användare** för att starta guiden **Nya användare**.

2.  Fyll i de obligatoriska fälten på sidan **Information** .

3.  Ange användarens **plats** på sidan **Inställningar** .

4.  Acceptera standardinställningarna och tilldela användarens konto en licens för Intune genom att välja **Nästa** på sidan **Grupp**.

5.  Du kan ange upp till fem e-postadresser på sidan **E-post** som ska ta emot aviseringar om användarnamnet och temporära lösenord till kontot. Avgränsa flera e-postadresser med semikolon (;). När du är klar väljer du **Skapa** för att lägga till användaren till din prenumeration.

6.  På sidan **Resultat** kan du visa det nya kontonamnet och dess tillfälliga lösenord. Intune skapar automatiskt det tillfälliga lösenordet.

7.  När den nya användaren visas i Office 365-administrationscentret kontrollerar du att den nya användaren skapades:

    1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/) väljer du **Administratör** &gt; **Företagsportal** och bläddrar sedan till längst ned på sidan. Kopiera den URL som visas under **Intune-företagsportalen**

    2.  Öppna ett nytt webbläsarfönster i ”sekretessläge” (välj **Verktyg** &gt; **InPrivate-surfning** i Internet Explorer) eller öppna ett nytt webbläsarfönster på en annan enhet och gå sedan till den URL som du kopierade i föregående steg. När användare loggar in för första gången måste de ange ett nytt lösenord för kontot.

## Lägga till användare i grupp
Du kan lägga till användare i grupp till Intune med hjälp av guiden **Lägg till användare** i grupp för att överföra en fil med kommaseparerade värden (CSV) som innehåller användardata. Länkar i guiden medför att du kan  ladda ned en tom mall och en exempel-CSV-fil. Den första raden i CSV-filen måste innehålla, i rätt ordning, var och en av kolumnetiketterna för användardata. Sedan måste du för varje användare i För varje användare i CSV-filen måste du sedan inkludera **användarnamnet** (t.ex. **bob@contoso.com**) och ett **visningsnamn** (t.ex. **Bob Kelly**

1.  I [Office 365-administrationscentret](http://go.microsoft.com/fwlink/p/?LinkId=698854) väljer du **Användare** &gt; **Ny**

2.  Välj **Masstillägg** för att starta guiden Masstillägg av användare.

3.  På sidan **Välj fil** väljer du **Bläddra** för att ange och läsa in en befintlig CSV-fil från datorn. Du kan också hämta en exempelfil i CSV-format eller en tom mallfil med hjälp av länkarna i guiden.

4.  På sidan **Verifiering** granskar du resultaten och väljer sedan på **Visa** för att se ytterligare information.

5.  På sidan **Inställningar** bekräftar du att inloggningsstatusen är **Tillåten** och anger **plats**. Dessa inställningar gäller för alla användarkonton som lagts till av CSV-filen.

6.  På sidan **Grupp** väljer du **Nästa** för att acceptera standardinställningarna och tilldela användarkontot en Intune-licens. Som standard är kryssrutan markerad, vilket tilldelar varje konto en licens för Intune.

7.  Du kan ange upp till fem e-postadresser på sidan **E-post** , för att ta emot aviseringar om användarnamn och temporära lösenord som Intune skapar för varje konto. Avgränsa flera e-postadresser med semikolon (;). Välj **Skapa** om du vill lägga till användarna till din prenumeration.

8.  På sidan **Resultat** kan du visa kontonamn och tillfälliga lösenord för varje användarkonto.

Varje användarkonto som du har lagt till genom att importera det visas nu i noden **Användare** i Office 365-administrationscentret. När nya användare loggar in för första gången måste de ange ett nytt lösenord för sitt användarkonto.

### Nästa steg
Gratulerar! Du har precis slutfört steg 2 i genomgången av *Microsoft Intune-utvärderingen*.

>[!div class="step-by-step"]

>[&larr; **Registrera dig för en utvärdering**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)     [**Skapa grupper** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)  


<!--HONumber=May16_HO2-->


