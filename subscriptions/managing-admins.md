---
title: "Verwalten von Administratorrechten im Administratorportal für Visual Studio-Abonnements"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/19/2018
Ms.topic: Get-Started-Article
Description: Learn how manage admins & super admins in the Visual Studio Subscriptions Administrator Portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 83bf27d5aaa99c2095ad8a1fafd7541df90f316b
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="managing-administrator-rights-in-the-visual-studio-subscriptions-administrator-portal"></a>Verwalten von Administratorrechten im Administratorportal für Visual Studio-Abonnements

## <a name="overview"></a>Übersicht 
Im Administratorportal für Visual Studio-Abonnements (https://manage.visualstudio.com) gibt es zwei Verwaltungsrollen:

**Superadministratoren**: Nach dem ersten Einrichten einer Organisation erhält der primäre Ansprechpartner standardmäßig die Befugnisse eines Superadministrators. Der primäre Ansprechpartner kann dann weitere Superadministrator- oder Administratorrollen zuweisen. Zusätzlich zum Verwalten von Abonnements für einzelne Abonnenten können Superadministratoren andere Administratoren und Superadministratoren hinzufügen und entfernen. Wenn im System mehr als zwei Superadministratoren existieren, kann jeder Superadministrator alle anderen bis auf die letzten zwei löschen, da diese aus Sicherheitsgründen nicht gelöscht werden können. 

**Administratoren**: Administratoren können Abonnenten innerhalb der Vereinbarungen verwalten, die der Superadministrator diesen zuweist.  Sie können Abonnements einzelnen Personen zuweisen sowie Abonnements bearbeiten, neu zuweisen oder entfernen.   (Administratoren werden von Superadministratoren benannt.)  

## <a name="adding-an-administrator-with-super-admin-rights"></a>Hinzufügen eines Administrators **mit** Superadministratorrechten:

1. Melden Sie sich beim [Administratorportal](https://manage.visualstudio.com) für Visual Studio-Abonnements mit einem Konto an, das bereits über Superadministratorrechte verfügt.

2. Klicken Sie oben auf der Seite auf die Registerkarte **Administratoren verwalten**. (Nur Superadministratoren haben Zugriff auf dieser Registerkarte.  Administratoren ohne Superadministratorrechte verwenden die Registerkarte **Abonnenten verwalten**, um einzelne Abonnenten zu verwalten.)

3. Klicken Sie auf **Hinzufügen**, um einen neuen Administrator zu erstellen. 

4. Füllen Sie im Popupfenster „Administrator hinzufügen“ alle erforderlichen Details aus.
  - Wenn Ihre Organisation bereits in Azure Active Directory (AAD) registriert ist, geben Sie den Namen in das Feld **Name** ein und wählen das richtige Element in der Dropdownliste aus. Bei neuen Benutzern muss der vollständige Namen eingegeben werden. Ignorieren Sie hierbei die Benachrichtigung *Keine Identitäten gefunden*.
  - Sobald der richtige Benutzer identifiziert wurde, wird das Feld für die E-Mail-Adresse zur Anmeldung automatisch ausgefüllt. Geben Sie die E-Mail-Adresse des neuen Administrators ein, falls noch nicht angegeben.

5. Wählen Sie die **PCN**, die der neue Administrator verwalten soll, indem Sie auf die Dropdownliste unter **Vereinbarungen** klicken. Wenn die einzubindende PCN über mehr als eine Vereinbarung verfügt, können Sie dem Administrator Zugriff auf eine beliebige Vereinbarung oder auf alle Vereinbarungen gewähren. 

**Weitere Informationen zu Vereinbarungen**: Die Dropdownfunktion unter Vereinbarungen ist deaktiviert, wenn nur eine Vereinbarung verfügbar ist.  Alle Vereinbarungen werden automatisch überprüft, wenn dem von Ihnen konfigurierten Benutzer Superadministratorrechte gewährt werden.

6. Klicken Sie auf das Feld **Superadministrator**, um für diesen Administrator Superadministratorrechte zu aktivieren.  

7. Um das Hinzufügen dieses Administrators abzuschließen, klicken Sie auf **Hinzufügen**.

**Mögliche Fehlermeldung beim Hinzufügen von Administratoren**: Einige Benutzer erhalten möglicherweise eine Fehlermeldung beim Versuch, den Administrator hinzuzufügen. Dies ist wahrscheinlich der Fall, wenn die hinzuzufügende E-Mail-Adresse des Superadministrators nicht im AAD des Unternehmens aufgeführt ist. Um den Administrator schließlich hinzuzufügen, ignorieren Sie die Fehlermeldung einfach und klicken erneut auf **Hinzufügen**. 

8. Sobald ein Superadministrator erstellt wurde, sehen Sie ihn in der Liste der Administratoren. Sein Konto wird mit einem grünen Häkchen markiert, um seinen Superadministratorstatus anzuzeigen. 

### <a name="optional--add-a-different-notification-email"></a>Optional: Fügen Sie eine andere E-Mail-Adresse für Benachrichtigungen hinzu.
Wenn Ihre Organisation über eine andere E-Mail-Adresse bzw. ein anderes Konto für den E-Mail-Empfang verfügt, haben Sie jetzt die Gelegenheit, eine „Kommunikationsadresse“ einzugeben. Wählen Sie **Andere Empfänger-E-Mail-Adresse für Benachrichtigungen hinzufügen**. 

*Beispiel*: René verwendet rene@contoso.com, wenn er sich mit den Anmeldeinformationen seines Unternehmens anmeldet.  Renés Unternehmen verwendet diese Adresse jedoch nur zum Verwalten des Verzeichniszugriffs.  Zum Senden und Empfangen von E-Mails verwendet René rene.collado@contoso.com. Das bedeutet, dass der Superadministrator für ihn eine zweite Adresse angelegt hat, um sicherzustellen, dass er die Willkommen-E-Mails empfängt.  Ist Ihr Unternehmen nicht auf diese Weise organisiert, sollte die Eingabe der E-Mail-Adresse für die Anmeldung ausreichend sein.

## <a name="adding-an-administrator-without-super-admin-rights"></a>Hinzufügen eines Administrators **ohne** Superadministratorrechte:

Um Administratoren ohne Superadministratorrechte hinzuzufügen, sollte der gleiche Prozess wie oben beschrieben durchgeführt werden, jedoch unter Berücksichtigung der folgenden Aspekte:
-  Beim Hinzufügen von Administratoren ohne Superadministratorrechte ist es nicht nötig, eine zusätzliche E-Mail-Adresse anzugeben, daher bleibt das Kontrollkästchen für den Superadministrator deaktiviert.
-  Für Benutzer ohne Superadministratorrechte wird in ihrem Profileintrag unter „Administratoren verwalten“ kein grünes Häkchen angezeigt.
