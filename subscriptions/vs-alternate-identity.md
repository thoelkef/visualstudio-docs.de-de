---
title: Identitäten für Visual Studio-Abonnenten
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 04/10/2018
ms.topic: conceptual
description: Hinzufügen einer alternativen Identität zu Ihrem Visual Studio-Abonnement, das für Visual Studio Team Services (VSTS) und Azure verwendet werden kann
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: vs subscription
ms.openlocfilehash: 9a83f78f35b9533c554c81cecd181c00eca05568
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Identitäten für Visual Studio-Abonnenten

Wenn Sie ein Visual Studio-Abonnement aktivieren, wird die Identität (oder das Konto) damit verknüpft, die Sie während der Aktivierung des Abonnements verwendet haben. Dadurch können Sie im [Visual Studio-Portal für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs), in VSTS und in Azure erkannt werden.

In VSTS wird der Status Ihres Visual Studio-Abonnements bei jeder Anmeldung überprüft. Zudem werden Features automatisch in jedem Konto zur Verfügung gestellt, bei dem Sie Mitglied sind.
Da diese Features in den Vorteilen für Abonnenten enthalten sind, ist es kostenlos, Sie als Mitglied zu einem beliebigen VSTS-Konto hinzuzufügen, wenn Sie eine Identität verwenden, die mit Ihrem Visual Studio-Abonnement verknüpft ist.

In Azure wird der Status Ihres Visual Studio-Abonnements überprüft, wenn Sie Ihre [monatliche Azure-Gutschrift](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) aktivieren, bei der es sich um einen Vorteil für Abonnenten handelt.

Innerhalb des [Visual Studio-Portals für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs) können Sie zusätzlich zu der Identität, die Sie für die Aktivierung verwendet haben, eine **alternative Identität** hinzufügen. Mittlerweile ist es möglich, eine alternative Identität hinzuzufügen, wenn Sie ein Microsoft-Konto verwendet haben, um Ihr Abonnement zu aktivieren. Dadurch können Sie ebenfalls ein Geschäfts-, Schul- oder Unikonto (das Sie verwenden, wenn Sie sich bei Visual Studio, Office 365 oder in Ihrem Geschäfts-, Schul- oder Uninetzwerk anmelden) hinzufügen und auf VSTS über Ihr persönliches sowie über Ihr Geschäfts-, Schul- oder Unikonto zugreifen.

## <a name="add-an-alternate-account-to-your-visual-studio-subscription"></a>Hinzufügen eines alternativen Kontos zu Ihrem Visual Studio-Abonnement

Wenn Sie ein alternatives Konto zu Ihrem Visual Studio-Abonnement hinzufügen, haben Sie Zugriff auf Abonnementvorteile wie VSTS und Azure, obwohl Sie eine andere Identität als die dem Abonnement zugewiesene verwenden. In der Vergangenheit war diese Funktion nur verfügbar, wenn Ihr Visual Studio-Konto einem Microsoft-Konto zugewiesen war. Jetzt wurde diese Funktion auf Geschäfts-, Schul- oder Unikonten in Azure Active Directory (Azure AD) erweitert.

Dadurch wird dem anderen Konto keine Kopie des Abonnements zur Verfügung gestellt. Stattdessen haben Sie die Möglichkeit, auf beide Vorteile über verschiedene Konten zuzugreifen.

Sie können für alle Abonnements ein Geschäfts-, Schul- oder Unikonto hinzufügen, damit Sie Ihr Konto mit den Vorteilen verwenden können, für die eine Anmeldung erforderlich ist (Visual Studio-IDE, VSTS und Azure).

### <a name="prerequisites"></a>Erforderliche Komponenten

* [Berechtigungen eines VSTS-Projektsammlungsadministrators oder eines Kontobesitzers](https://docs.microsoft.com/en-us/vsts/accounts/faq-add-delete-users#find-owner).

* Zur Verwendung eines alternatives Kontos muss Ihr Abonnement entweder Visual Studio Team Services oder Microsoft Azure einschließen.

> [!Note]
> Sie können Ihre Abonnementvorteile zwar weiterhin mit der alternativen ID verwenden, Ihr Konto ist dann aber immer noch Ihrem ursprünglichen Konto zugewiesen.

### <a name="add-the-alternate-account"></a>Hinzufügen des alternativen Kontos

1. Melden Sie sich mit Ihrem Microsoft-Konto bei Visual Studio an (https://{Ihr_Konto}.visualstudio.com).

2. Wechseln Sie zu **Abonnements**.

  ![Fügen Sie ein alternatives Konto hinzu, und wechseln Sie zu „Abonnements“ in Visual Studio.](_img/vs-alternate-identity/my-vs-subscriptions.png)

3. Klicken Sie auf **Add alternate account** (Alternatives Konto hinzufügen).

  ![Auswahl von „Choose add alternate account“ (Alternatives Konto hinzufügen) ](_img/vs-alternate-identity/choose-add-alternate-account.png)

4. Fügen Sie Ihr Geschäfts-, Schul- oder Unikonto hinzu.

  ![Hinzufügen eines Geschäfts-, Schul- oder Unikontos](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto bei Visual Studio (https://{Ihr_Konto}.visualstudio.com) an.

  ![Verwenden Ihres Geschäfts-, Schul- oder Unikontos](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

  Ihr alternatives Konto wird dem Visual Studio-Abonnement hinzugefügt, sodass beide Identitäten die Abonnementvorteile nutzen können, für die eine Anmeldung mit dem alternativen Konto erforderlich ist (IDE, VSTS und Azure).

Weitere Informationen zum Hinzufügen eines alternativen Kontos finden Sie auf der Seite [Häufig gestellte Fragen zu Visual Studio](https://www.visualstudio.com/my/myvsfaq#alternate).

## <a name="faq"></a>FAQ

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>F: Warum erkennt VSTS mich nicht als VSTS-Abonnenten?
A: VSTS sollte Ihr Abonnement automatisch erkennen, wenn Sie sich mit Ihrer primären oder alternativen Identität anmelden. Wenn dies nicht der Fall ist, können Sie Folgendes ausprobieren:

* Überprüfen Sie, ob Sie über ein aktives Visual Studio-Abonnement verfügen, das [VSTS als Vorteil enthält](vs-vsts.md).

* Vergewissern Sie sich, dass Sie ein Konto bzw. eine Identität verwenden, bei dem bzw. der es sich um die primäre oder alternative Identität für Ihr Visual Studio-Abonnement handelt.

* Besuchen Sie das [Visual Studio-Portal für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs) mindestens einmal, bevor Sie sich bei VSTS anmelden.

Wenn VSTS Ihr Abonnement weiterhin nicht erkennt, [kontaktieren Sie den Support](https://www.visualstudio.com/team-services/support/).
