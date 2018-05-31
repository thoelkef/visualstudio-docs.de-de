---
title: Häufig gestellte Fragen zur Migration der VLSC-Verwaltung | Microsoft-Dokumentation
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/13/2018
ms.topic: Get-Started-Article
description: Häufig gestellte Fragen zur Migration der Volume License Service Center-Verwaltung
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: e4dda4264ae48903e98166346f9e2569ab1e4da0
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34336125"
---
# <a name="visual-studio-subscriptions-administration-migration"></a>Migration der Verwaltung von Visual Studio-Abonnements

In den nächsten Monaten wird die Verwaltung von Visual Studio-Abonnements (früher MSDN-Abonnements) geändert. Heute können Sie Visual Studio-Abonnements über Volumenlizenzierung erwerben, und die Abonnements werden im Volume License Service Center-Portal (VLSC) verwaltet. Ein neues Verwaltungsportal wird erstellt, und Visual Studio-Abonnements werden künftig im neuen Portal verwaltet. Zusätzlich zu den vorhandenen Vorgängen aus dem VLSC ermöglicht das neue Portal unbegrenzte Massenzuweisungen, Nachverfolgen und Filtern von Abonnements und die Nutzung von Azure Active Directory (Azure AD) zur Zugriffsverwaltung. Das neue Visual Studio-Verwaltungsportal finden Sie unter: [https://manage.visualstudio.com](https://manage.visualstudio.com). 

> [!Note] 
> Diese Migration hat keinen Einfluss auf MPSA-Kunden. 

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

### <a name="why-is-it-changing"></a>Warum diese Änderung?
Mit dem neuen Portal wird die Verwaltung von Visual Studio-Abonnements optimiert. Die Verwaltung von Visual Studio-Abonnements erfolgt dann nur noch über das Portal, unabhängig davon, wie die Abonnements erworben wurden. Das neue Portal verwendet eine neue Plattform, die Azure AD ermöglicht und uns zukunftsfähig macht. Darüber hinaus weist es eine aktualisierte Benutzeroberfläche auf, die die Navigation und Verwendung vereinfacht und so die Administratoreffizienz erhöht.

### <a name="who-will-be-impacted"></a>Wer ist betroffen? 
Die Änderung wirkt sich auf alle Kunden aus, die über aktive Volumenlizenzverträge verfügen und Visual Studio-Abonnements über die Volumenlizenzierung erworben haben. 

### <a name="when-is-it-changing"></a>Wann erfolgt diese Änderung?
Dies ist ein gewaltiger Übergang, und er wird in Phasen durchgeführt, bis alle Kunden mit aktiven Volumenlizenzverträgen für Visual Studio-Abonnements zum neuen Verwaltungsportal migriert wurden. Die Migration begann im ersten Quartal 2017. Wir werden unsere Volumenlizenzkunden im Vorfeld über die Woche ihrer geplanten Migration benachrichtigen.  

### <a name="does-my-organization-need-to-sign-up-for-azure-active-directory-azure-ad"></a>Muss sich meine Organisation für Azure Active Directory (Azure AD) registrieren?
Ihre Organisation muss sich nicht für Azure AD registrieren, jedoch können Sie dies jederzeit tun. Wenn Sie Azure AD integrieren möchten, können Sie dazu den kostenlosen Free-Tarif für Azure AD nutzen. Mit Azure Active Directory schützen Sie Ihre Organisation mit erhöhter Sicherheit, Kontrolle und langfristiger Zuverlässigkeit. Wenn Sie jedoch noch nicht für Azure AD bereit sind, können Sie weiterhin so wie zurzeit Ihre Microsoft-Konten (MSAs) verwenden. 

### <a name="how-do-i-know-when-my-organization-will-be-migrated"></a>Wie erfahre ich, wann meine Organisation migriert wird?
Primäre Kontakte/Ansprechpartner erhalten eine Woche vor der Migration Ihrer Organisation eine E-Mail von uns, mit der Sie zum Durchführen des Onboardingprozesses aufgefordert werden. Abonnement-Manager erhalten ebenfalls eine E-Mail mit der Mitteilung, dass wir die primären Kontakte/Ansprechpartner kontaktiert und Details zur Sicherstellung des erfolgreichen Onboardings bereitgestellt haben. Erfahren Sie, wie Sie [die primären Kontakte/Ansprechpartner Ihrer Organisation finden](#How-do-I-find-out-who-my-Primary-or-Notices-Contact-is?). 

### <a name="is-onboarding-different-from-migration"></a>Unterscheidet sich das Onboarding von der Migration?
Ja.  In diesem Prozess gibt es zwei Phasen. Durch das Einrichten (oder Onboarding) Ihrer Organisation vor der Migration wird sichergestellt, dass Ihre Arbeit als Administrator nicht unterbrochen wird. Wenn wir die Informationen Ihrer Organisation migriert haben, können Sie Visual Studio-Abonnements im neuen Portal verwalten. Wenn die primären Kontakte/Ansprechpartner das Onboarding nicht vor der Migration durchführen, wird der Abonnement-Manager blockiert und kann Abonnements nicht verwalten, bis Sie den Onboardingprozess abgeschlossen haben. 

### <a name="what-is-the-onboarding-process"></a>Was ist der Onboardingprozess?
Eine E-Mail wird an die primären Kontakte und Ansprechpartner gesendet, um sie aufzufordern, den Onboardingprozess durchzuführen. Anweisungen für den Prozess finden Sie weiter unten. 
1.  **Die eigene öffentliche Kundennummer ermitteln und sich damit anmelden:**

    a.  Die E-Mail an die primären Kontakte und Ansprechpartner enthält jeweils einen persönlichen Link sowie die letzten drei Ziffern ihrer öffentlichen Kundennummer (Public Customer Number, PCN).* 

    b.  Der primäre Ansprechpartner muss sich im VLSC anmelden, um die gesamte PCN zu erhalten. (Anweisungen zum Ermitteln der PCN finden Sie unten.) 

    c.  Nachdem die primären Ansprechpartner ihre jeweilige PCN ermittelt haben, müssen sie auf ihre persönlichen Links klicken, woraufhin sie zum Anmelden aufgefordert werden. Sie können sich mit ihrem Geschäfts-, Schul- oder Unikonto (sofern Ihre Organisation bei Azure AD registriert ist) oder einem Microsoft-Konto (MSA) anmelden (wenn Ihre Organisation nicht bei Azure AD registriert ist). 

    d.  Als Nächstes müssen sie die PCN eingeben. 

2.  **Ihre Administratoren einrichten:**

    Nach dem Eingeben der PCN wird die Seite aufgerufen, auf sie der Superadministratoren und Administratoren (vormals Abonnement-Manager) hinzufügen können. Im Idealfall sollte dies vor dem Migrationsdatum Ihrer Organisation durchgeführt werden, damit bei der Verwaltung Ihrer Abonnements keine Unterbrechungen auftreten. 

3.  **Auf das neue Portal zur Verwaltung von Abonnements zugreifen:** Nach der Migration Ihrer Organisation werden die Superadministratoren und Administratoren per E-Mail gebeten, auf das neue Portal zuzugreifen und die Abonnements zu verwalten. 

> [!NOTE] 
> Wenn die primären Kontakte oder Ansprechpartner mehr als eine E-Mail erhalten, bedeutet dies, dass sie mehrere PCNs besitzen. Sie müssen den Prozess mithilfe der persönlichen Links für die PCNs abschließen, die jeweils in den E-Mails genannt werden. 

### <a name="what-is-the-difference-between-a-super-admin-and-an-administrator"></a>Was ist der Unterschied zwischen einem Superadministrator und einem Administrator?
Wenn sich der primäre Kontakt oder Ansprechpartner zum ersten Mal anmeldet, wird er automatisch als Superadministrator eingerichtet. Superadministratoren können durch Hinzufügen/Löschen anderer Superadministratoren oder Administratoren den Administratorzugriff auf Abonnements sowie die Abonnements selbst verwalten. Der Superadministrator kann neben sich selbst andere Superadministratoren zuweisen.

Administratoren (vormals Abonnement-Manager) können nur Abonnements verwalten, sie können nicht steuern, wer Zugriff zum Verwalten von Abonnements erhält. 

### <a name="how-will-i-as-an-administrator-onboard-to-the-new-portal"></a>Wie führe ich als Administrator das Onboarding in das neue Portal durch?
Primäre Kontakte und Ansprechpartner Ihrer Organisation erhalten eine E-Mail mit einem persönlichen Link, mit dem sie auf eine Seite gelangen, auf der sie sich mit einem Geschäfts-, Schul- oder Unikonto, unterstützt von Azure Active Directory (Azure AD), oder persönlichen MSAs anmelden können. Wenn sie angemeldet sind, müssen sie die öffentliche Kundennummer (Public Customer Number, PCN) oder Autorisierungsnummer Ihrer Organisation eingeben, um die Vereinbarungen zu überprüfen. Sie werden dann als Superadministrator eingerichtet und können wie Sie andere Administratoren hinzufügen, um Visual Studio-Abonnements zu verwalten. 

### <a name="where-do-i-manage-subscriptions-if-my-organization-has-been-onboarded-but-hasnt-been-migrated"></a>Wo verwalte ich Abonnements, nachdem meine Organisation das Onboarding durchgeführt hat, aber noch nicht migriert wurde? 
Sie verwalten Abonnements weiterhin über das VLSC, bis Sie die E-Mail zu Visual Studio-Abonnements erhalten, in der Sie informiert werden, dass Ihre Organisation migriert wurde und das neue Portal für die Verwaltung nutzen kann. 

### <a name="where-can-i-locate-my-organizations-public-customer-number-pcn-or-authorization-number"></a>Wie finde ich die öffentliche Kundennummer (Public Customer Number, PCN) oder Autorisierungsnummer meiner Organisation?
Melden Sie sich beim [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) an, und folgen Sie dem folgenden Pfad: **Abonnements** > **Visual Studio-Abonnements**. Die PCN befindet sich unterhalb der **Ergebnisse für Vereinbarung/öffentliche Kundennummer**. Eine ausführliche Anleitung zum Suchen Ihrer PCN finden Sie in diesem [Hilfeartikel](/find-pcn/). 

### <a name="how-do-i-find-out-who-my-primary-or-notices-contact-is"></a>Wie finde ich heraus, wer mein primärer Kontakt oder Ansprechpartner ist?
Melden Sie sich beim [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) an, und folgen Sie dem folgenden Pfad: **Lizenzen > Beziehungszusammenfassung**. Wählen Sie Ihre **Lizenzierungs-ID > Kontakte** aus. Eine ausführliche Anleitung zum Suchen Ihres primären Kontakts oder Ansprechpartners finden Sie in diesem [Hilfeartikel](find-primary-contact.md). 

### <a name="what-if-my-primary-or-notices-contact-is-gone-no-longer-with-the-company-or-not-available-to-complete-onboarding"></a>Was geschieht, wenn mein primärer Kontakt oder Ansprechpartner nicht mehr im Unternehmen oder nicht verfügbar ist, um das Onboarding durchzuführen?
Sie müssen sich [an den Support wenden](https://www.visualstudio.com/subscriptions/support/#talktous) und die E-Mail-Adresse angeben, die Sie zum Verwalten von Abonnements im VLSC verwendet haben. Nach der Überprüfung kann der Support Sie beim Onboardingprozess unterstützen. 

### <a name="what-will-happen-with-renewing-customers"></a>Was passiert mit Kunden, die eine Verlängerung abschließen? 
Kunden, die eine Verlängerung abschließen, sollten die Verlängerung ihrer Abonnements wie gewohnt fortsetzen, da Verlängerungen nicht von der Migration betroffen sind. 

### <a name="should-my-organization-wait-to-set-up-a-new-agreement-in-the-new-system-rather-than-renew-an-existing-agreement"></a>Sollte meine Organisation warten, um eine neue Vereinbarung im neuen System einzurichten, statt eine vorhandene Vereinbarung zu verlängern? 
Nein.  Die Migration wirkt sich nicht auf das Erstellen oder Verlängern von Vereinbarungen aus. 

### <a name="what-if-my-organizations-agreement-is-in-the-grace-period-during-the-transition-will-they-also-be-migrated"></a>Was geschieht, wenn sich die Vereinbarung meiner Organisation während des Übergangs in der Karenzzeit befindet? Wird sie dennoch migriert?
Ja, wenn die Vereinbarung weiterhin aktiv ist, wird Ihre Organisation migriert. 

### <a name="what-if-my-organization-has-over-claimed-in-the-current-system-will-we-still-be-migrated-to-the-new-system"></a>Was geschieht, wenn meine Organisation das aktuelle System übermäßig in Anspruch genommen hat? Werden wir dennoch zum neuen System migriert? 
Ja, Ihre Organisation wird dennoch zum neuen System migriert. Die Möglichkeit einer übermäßigen Inanspruchnahme (bei Vereinbarungstypen, die dies zulassen) ist im neuen System vorhanden. 

### <a name="what-if-my-organization-has-more-than-one-subscription-assigned-to-a-single-useremail-address"></a>Was geschieht, wenn meine Organisation über mehrere Abonnements verfügt, die einem einzelnen Benutzer/einer E-Mail-Adresse zugewiesen sind?
Ihre Organisation wird dennoch migriert.  Sie können jedoch diesem Benutzer/der E-Mail-Adresse keine weiteren Abonnements der gleichen Ebene (d.h. Professional, Enterprise usw.) zuweisen. Alle Abonnements der gleichen Ebene, die bei der Migration dieselbe E-Mail-Adresse aufweisen, werden weiterhin angezeigt, aber Administratoren müssen die E-Mail-Adressen ändern, damit sie eindeutig sind. Mehrere Abonnements der gleichen Ebene können im neuen Portal nicht einem einzelnen Benutzer/einer E-Mail-Adresse zugewiesen werden.

### <a name="where-can-i-find-the-most-up-to-date-information-about-the-migration"></a>Wo finde ich aktuelle Informationen zur Migration? 
Aktuelle Informationen bezüglich dieser Migration finden Sie auf unserer [Webseite](https://aka.ms/vs-admin) für Administratoren von Visual Studio-Abonnements. Wenn Sie Unterstützung benötigen, sehen Sie sich die [Supportseite](http://www.visualstudio.com/subscriptions/support/#!collections/962-subscriptions) für Visual Studio-Abonnements an, die Informationen zur Selbsthilfe und Kontaktdaten für den Support enthält. In den nächsten Monaten werden wir weitere Updates auf der Webseite für Administratoren und per E-Mail bereitstellen, damit dieser Übergang mit Leichtigkeit durchgeführt werden kann. 

## <a name="resources-and-support-information"></a>Ressourcen und Supportinformationen
- [Administratorwebseite](https://www.visualstudio.com/subscriptions-administration/)

- [Support](https://www.visualstudio.com/subscriptions/support/) für Visual Studio-Abonnements und die Verwaltung. 

- [Suchen der PCN](find-pcn.md)

- [Suchen des primären Kontakts oder des Ansprechpartners](find-primary-contact.md) 

- [Video](https://www.youtube.com/watch?v=ZmnywYGSFMg&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=1&t=0s) für das Onboarding Ihrer Organisation und die Verwaltung von Administratoren 
