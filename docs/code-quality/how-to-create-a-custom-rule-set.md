---
title: Erstellen einer benutzerdefinierten Codeanalyseregel Teilmenge in Visual Studio
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3b1d9b436c3e3be4f241d18791744085be4ece9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="custom-rule-sets"></a>Benutzerdefinierte Regelsätze

Erstellen Sie eine benutzerdefinierte *Regelsatz* um projektspezifische Anforderungen für die Codeanalyse zu erfüllen.

## <a name="create-a-custom-rule-set"></a>Erstellen eines benutzerdefinierten Regelsatzes

Eine benutzerdefinierte Regel zu erstellen, öffnen Sie einen integrierte Regelsatz in der **Regelsatz-Editor**. Von dort aus können Sie hinzufügen oder entfernen Sie bestimmte Regeln, und Sie können die Aktion, die bei einem Verstoß eine Regel gegen ändern&mdash;beispielsweise angezeigt wird, eine Warnung oder einen Fehler.

1. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**.

2. Auf der **Eigenschaften** Seiten, wählen die **Codeanalyse** Registerkarte.

3. In der **diesen Regelsatz ausführen** Dropdown-Liste, führen Sie einen der folgenden:

    - Wählen Sie den Regelsatz aus, den Sie anpassen möchten.

     \- oder –

    - Wählen Sie  **\<durchsuchen... >** Geben Sie einen vorhandenen Regelsatz ist nicht in der Liste.

4. Wählen Sie **öffnen** auf die Regeln im Regelsatz-Editor anzuzeigen.

Sie können auch eine neue Regelsatzdatei aus erstellen die **neue Datei** Dialogfeld:

1. Wählen Sie **Datei** > **neu** > **Datei**, oder drücken Sie **STRG**+**N**.

2. In der **neue Datei** wählen Sie im Dialogfeld die **allgemeine** Kategorie auf der linken Seite und wählen Sie dann **Codeanalyse-Regelsatz**.

3. Wählen Sie **öffnen**.

   Die neue *ruleSet* Datei in dem Regelsatz-Editor wird geöffnet.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Erstellen eines benutzerdefinierten Regelsatzes aus mehreren Regelsätze

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste des Projekts, und wählen Sie dann **Eigenschaften**.

2. Auf der **Eigenschaften** Seiten, wählen die **Codeanalyse** Registerkarte.

3. Wählen Sie  **\<auswählen, die mehrere Regelsätzen... >** aus **diesen Regelsatz ausführen**.

4. In der **hinzufügen oder Entfernen von Regelsätzen** (Dialogfeld), wählen Sie die Regel Sie wird in Ihrer neuen Regelsatz enthalten sein soll.

   ![Fügen Sie hinzu oder entfernen Sie die Regel (Dialogfeld)](media/add-remove-rule-sets.png)

5. Wählen Sie **speichern unter**, geben Sie einen Namen für die *ruleSet* Datei, und wählen Sie dann **speichern**.

   Neuen Regelsatz ausgewählt ist, der **diesen Regelsatz ausführen** Liste.

6. Wählen Sie **öffnen** zu den neuen Regelsatz im Regelsatz-Editor zu öffnen.

## <a name="name-and-description"></a>Name und Beschreibung

Um den Anzeigenamen des einen Regelsatzes ändern, die im Editor geöffnet ist, öffnen die **Eigenschaften** Fenster dazu **Ansicht** > **Fenster "Eigenschaften"** in der Menüleiste. Geben Sie den Anzeigenamen in der **Namen** Feld. Sie können auch eine Beschreibung für den Regelsatz eingeben.

## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie eine Regel festgelegt haben, besteht der nächste Schritt die Regeln durch Hinzufügen oder Entfernen von Regeln oder ändern den Schweregrad der Verletzungen von Schwellenwertregeln anpassen.

> [!div class="nextstepaction"]
> [Bearbeiten Sie Regeln im Regelsatz-editor](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Codeanalyse-Regelsatzreferenz](../code-quality/rule-set-reference.md)