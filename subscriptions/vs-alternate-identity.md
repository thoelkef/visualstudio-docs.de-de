---
title: Identitäten für Visual Studio-Abonnenten
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 3/15/2018
Ms.topic: Get-Started-Article
Description: How to add an alternate identity for your Visual Studio subscription, to use for VSTS and Azure.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 70bfd305ec35b562fb722fb853016c3df4240ff8
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Identitäten für Visual Studio-Abonnenten

Wenn Sie ein Visual Studio-Abonnement aktivieren, wird die Identität (oder das Konto) damit verknüpft, die Sie während der Aktivierung des Abonnements verwendet haben. Dadurch können Sie im [Visual Studio-Portal für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs), in VSTS und in Azure erkannt werden.

In VSTS wird der Status Ihres Visual Studio-Abonnements bei jeder Anmeldung überprüft. Zudem werden Features automatisch in jedem Konto zur Verfügung gestellt, bei dem Sie Mitglied sind. Da diese Features in den Vorteilen für Abonnenten enthalten sind, ist es kostenlos, Sie als Mitglied zu einem beliebigen VSTS-Konto hinzuzufügen, wenn Sie eine Identität verwenden, die mit Ihrem Visual Studio-Abonnement verknüpft ist.

In Azure wird der Status Ihres Visual Studio-Abonnements überprüft, wenn Sie Ihre [monatliche Azure-Gutschrift](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) aktivieren, bei der es sich um einen Vorteil für Abonnenten handelt.

Innerhalb des [Visual Studio-Portals für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs) können Sie zusätzlich zu der Identität, die Sie für die Aktivierung verwendet haben, eine **alternative Identität** hinzufügen. Mittlerweile ist es möglich, eine alternative Identität hinzuzufügen, wenn Sie ein Microsoft-Konto verwendet haben, um Ihr Abonnement zu aktivieren. Dadurch können Sie ebenfalls ein Geschäfts-, Schul- oder Unikonto (das Sie verwenden, wenn Sie sich bei Visual Studio, Office 365 oder in Ihrem Geschäfts-, Schul- oder Uninetzwerk anmelden) hinzufügen und auf VSTS über Ihr persönliches sowie über Ihr Geschäfts-, Schul- oder Unikonto zugreifen.

## <a name="how-to-add-an-alternate-identity-to-your-visual-studio-subscription"></a>Hinzufügen einer alternativen Identität zu Ihrem Visual Studio-Abonnement

1. Melden Sie sich im [Visual Studio-Portal für Abonnenten an](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

  > Wählen Sie „Persönliches Konto“ (Ihr Microsoft-Konto) aus, wenn Sie dazu aufgefordert werden, zwischen „Persönliches Konto“ und „Geschäfts-, Schul- oder Unikonto“ auszuwählen.
  >
  > In einigen Fällen müssen Sie diese Auswahl treffen, da Ihr Microsoft-Konto und Ihr Geschäfts-, Schul- oder Unikonto dieselbe E-Mail-Adresse verwenden. Obwohl beide Identitäten dieselbe E-Mail-Adresse verwenden, handelt es sich dabei um separate Identitäten mit unterschiedlichen Profilen, Sicherheitseinstellungen und Berechtigungen.
  >
  > Ab dem 30. März 2018 können Sie kein Microsoft-Konto mehr mithilfe einer Domäne erstellen, die in Azure Active Directory verwaltet wird. Sie können sich weiterhin anmelden, indem Sie diese E-Mail-Adresse als Geschäftskonto verwenden.

2. Wechseln Sie zur Registerkarte **Abonnements**.

  ![Auswählen von Abonnements](_img/vs-alternate-identity/choose-subscriptions-my-visual-studio-com-portal.png)

3. Wechseln Sie unter **Verwandte Links** zu **Alternatives Konto hinzufügen**.

  ![Wechseln Sie unter „Verwandte Links“ zu „Alternatives Konto hinzufügen“.](_img/vs-alternate-identity/add-alternate-account-my-visual-studio-com-portal.png)

4. Geben Sie Ihr Geschäfts-, Schul- oder Unikonto ein, und klicken Sie auf **Hinzufügen**.

  ![Eingeben Ihres Geschäfts-, Schul- oder Unikontos](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Verwenden Sie Ihr Geschäfts-, Schul- oder Unikonto, um sich bei Ihrem VSTS-Konto (```https://{youraccount}.visualstudio.com```) anzumelden. Die Informationen werden möglicherweise mit einer kurzen Verzögerung weitergegeben. Überprüfen Sie diese deshalb in 15 Minuten erneut. 

## <a name="faq"></a>FAQ

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>F: Warum erkennt VSTS mich nicht als VSTS-Abonnenten?
A: VSTS sollte Ihr Abonnement automatisch erkennen, wenn Sie sich mit Ihrer primären oder alternativen Identität anmelden. Wenn dies nicht der Fall ist, können Sie Folgendes ausprobieren:

* Überprüfen Sie, ob Sie über ein aktives Visual Studio-Abonnement verfügen, das [VSTS als Vorteil enthält](vs-vsts.md).

* Vergewissern Sie sich, dass Sie ein Konto bzw. eine Identität verwenden, bei dem bzw. der es sich um die primäre oder alternative Identität für Ihr Visual Studio-Abonnement handelt.

* Besuchen Sie das [Visual Studio-Portal für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs) mindestens einmal, bevor Sie sich bei VSTS anmelden.

Wenn VSTS Ihr Abonnement weiterhin nicht erkennt, [kontaktieren Sie den Support](https://www.visualstudio.com/team-services/support/).

