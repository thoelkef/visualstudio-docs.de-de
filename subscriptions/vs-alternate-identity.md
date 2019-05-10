---
title: Identitäten für Visual Studio-Abonnenten
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 04/10/2018
ms.topic: conceptual
description: Hinzufügen einer alternativen Identität zu Ihrem Visual Studio-Abonnement, die für Azure DevOps und Azure verwendet werden kann
searchscope: vs subscription
ms.openlocfilehash: 63a372d4a0e0e70a008f86a36aae73516bf42458
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62428075"
---
# <a name="identities-for-visual-studio-subscribers"></a>Identitäten für Visual Studio-Abonnenten

Wenn Sie ein Visual Studio-Abonnement aktivieren, wird die Identität (oder das Konto) damit verknüpft, die Sie während der Aktivierung des Abonnements verwendet haben. Dadurch können Sie im [Visual Studio-Portal für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs), in Azure DevOps und in Azure erkannt werden.

In Azure DevOps wird der Status Ihres Visual Studio-Abonnements bei jeder Anmeldung überprüft. Zudem werden Features automatisch in jeder Organisation zur Verfügung gestellt, in der Sie Mitglied sind.
Da diese Features in den Abonnementvorteilen enthalten sind, ist es kostenlos, Sie einer beliebigen Azure DevOps-Organisation als Mitglied hinzuzufügen, wenn Sie eine Identität verwenden, die mit Ihrem Visual Studio-Abonnement verknüpft ist.

In Azure wird der Status Ihres Visual Studio-Abonnements überprüft, wenn Sie Ihre [monatliche Azure-Gutschrift](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) aktivieren, bei der es sich um einen Vorteil für Abonnenten handelt.

Innerhalb des [Visual Studio-Portals für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs) können Sie zusätzlich zu der Identität, die Sie für die Aktivierung verwendet haben, eine **alternative Identität** hinzufügen. Mittlerweile ist es möglich, eine alternative Identität hinzuzufügen, wenn Sie ein Microsoft-Konto verwendet haben, um Ihr Abonnement zu aktivieren. So können Sie auch ein Geschäfts-, Schul- oder Unikonto (das Sie zum Anmelden in Visual Studio, Office 365 oder Ihrem Geschäfts-, Schul- oder Uninetzwerk verwenden) hinzufügen und auf Azure DevOps über Ihr persönliches sowie über Ihr Geschäfts-, Schul- oder Unikonto zugreifen.

## <a name="add-an-alternate-account-to-your-visual-studio-subscription"></a>Hinzufügen eines alternativen Kontos zu Ihrem Visual Studio-Abonnement

Wenn Sie Ihrem Visual Studio-Abonnement ein alternatives Konto hinzufügen, haben Sie Zugriff auf Abonnementvorteile wie Azure DevOps und Azure, obwohl Sie eine andere Identität als die dem Abonnement zugewiesene verwenden. In der Vergangenheit war diese Funktion nur verfügbar, wenn Ihr Visual Studio-Konto einem Microsoft-Konto zugewiesen war. Jetzt wurde diese Funktion auf Geschäfts-, Schul- oder Unikonten in Azure Active Directory (Azure AD) erweitert.

Dadurch wird dem anderen Konto keine Kopie des Abonnements zur Verfügung gestellt. Stattdessen haben Sie die Möglichkeit, auf beide Vorteile über verschiedene Konten zuzugreifen.

Sie können für alle Abonnements ein Geschäfts-, Schul- oder Unikonto hinzufügen, damit Sie mit dem Konto alle Vorteile nutzen können, für die eine Anmeldung erforderlich ist (Visual Studio-IDE, Azure DevOps und Azure).

### <a name="add-the-alternate-account"></a>Hinzufügen des alternativen Kontos

1. Melden Sie sich mit Ihrem Microsoft-Konto (https://my.visualstudio.com) beim Abonnentenportal für Visual Studio an.

2. Wechseln Sie zu **Abonnements**.

    > [!div class="mx-imgBorder"]
    > ![Hinzufügen eines alternativen Kontos: Navigieren zu Abonnements im VS-Portal](_img/vs-alternate-identity/my-vs-subscriptions.png)

3. Klicken Sie auf **Add alternate account** (Alternatives Konto hinzufügen).
    > [!div class="mx-imgBorder"]
    > ![Auswahl von „Choose add alternate account“ (Alternatives Konto hinzufügen)](_img/vs-alternate-identity/choose-add-alternate-account.png)

4. Fügen Sie Ihr Geschäfts-, Schul- oder Unikonto hinzu.
    > [!div class="mx-imgBorder"]
    > ![Hinzufügen eines Geschäfts-, Schul- oder Unikontos](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto bei Azure DevOps an (https://{ihrkonto}.visualstudio.com).
    > [!div class="mx-imgBorder"]
    > ![Verwenden Ihres Geschäfts-, Schul- oder Unikontos](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

Ihr alternatives Konto wird dem Visual Studio-Abonnement hinzugefügt, sodass beide Identitäten die Abonnementvorteile nutzen können, für die eine Anmeldung mit dem alternativen Konto erforderlich ist (IDE, Azure DevOps und Azure).

## <a name="faq"></a>FAQ

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>Frage:  Warum erkennt Azure DevOps mich nicht als Visual Studio-Abonnent?

Antwort: Azure DevOps sollte Ihr Abonnement automatisch erkennen, wenn Sie sich mit Ihrer primären oder alternativen Identität anmelden. Wenn dies nicht der Fall ist, können Sie Folgendes ausprobieren:

* Überprüfen Sie, ob Sie über ein aktives Visual Studio-Abonnement verfügen, das [Azure DevOps als Vorteil enthält](vs-azure-devops.md).

* Vergewissern Sie sich, dass Sie ein Konto bzw. eine Identität verwenden, bei dem bzw. der es sich um die primäre oder alternative Identität für Ihr Visual Studio-Abonnement handelt.

* Besuchen Sie das [Visual Studio-Portal für Abonnenten](https://my.visualstudio.com?wt.mc_id=o~msft~docs) mindestens einmal, bevor Sie sich bei Azure DevOps anmelden.

Wenn Azure DevOps Ihr Abonnement weiterhin nicht erkennt, [wenden Sie sich an den Support](https://visualstudio.microsoft.com/team-services/support/).
