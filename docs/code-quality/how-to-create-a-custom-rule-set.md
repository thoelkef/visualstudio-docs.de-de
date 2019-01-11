---
title: Erstellen Sie einen benutzerdefinierten Regelsatz für Codeanalyse
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2a0b2de9450fc2e9350371b08f4a3a9bf8d9c1b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53929915"
---
# <a name="customize-a-rule-set"></a>Anpassen eines Regelsatzes

Sie können einen benutzerdefinierten Regelsatz, um bestimmte projektanforderungen für die Codeanalyse erstellen.

## <a name="create-a-custom-rule-set"></a>Erstellen eines benutzerdefinierten Regelsatzes

Um eine benutzerdefinierte Regel erstellen, öffnen Sie eine integrierte Regel legen Sie in der **Regelsatz-Editor**. Von dort aus können Sie hinzufügen oder entfernen Sie bestimmte Regeln, und Sie können ändern, dass die Aktion, die auftritt, wenn gegen eine Regel verstoßen wird&mdash;z. B. Anzeigen einer Warnung oder einen Fehler.

1. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**.

2. Auf der **Eigenschaften** Seiten, auf die **Codeanalyse** Registerkarte.

3. In der **diesen Regelsatz ausführen** Dropdown-Listenfeld, führen Sie einen der folgenden:

   - Wählen Sie den Regelsatz aus, den Sie anpassen möchten.

     \- oder –

   - Wählen Sie  **\<durchsuchen... >** an einen vorhandenen Regelsatz ist nicht in der Liste.

4. Wählen Sie **öffnen** zu Regeln in den Regelsatz-Editor anzuzeigen.

Sie können auch erstellen eine neuen Regelsatzdatei aus der **neue Datei** Dialogfeld:

1. Wählen Sie **Datei** > **neu** > **Datei**, oder drücken Sie **STRG**+**N**.

2. In der **neue Datei** wählen Sie im Dialogfeld die **allgemeine** Kategorie auf der linken Seite, und wählen Sie dann **Codeanalyse-Regelsatz**.

3. Wählen Sie **öffnen**.

   Die neue *ruleSet* Datei wird in dem Regelsatz-Editor geöffnet.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Erstellen Sie eine benutzerdefinierte Regel aus mehreren Regelsätzen

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Projekts, und wählen Sie dann **Eigenschaften**.

2. Auf der **Eigenschaften** Seiten, auf die **Codeanalyse** Registerkarte.

3. Wählen Sie  **\<auswählen, die mehrere Regelsätze... >** aus **diesen Regelsatz ausführen**.

4. In der **Regelsätze hinzufügen oder Entfernen von** Dialogfeld Wählen Sie die Regelsätze, die Sie in der neue Regelsatz enthalten sein soll.

   ![Fügen Sie hinzu oder entfernen Sie die Regel (Dialogfeld)](media/add-remove-rule-sets.png)

5. Wählen Sie **speichern**, geben Sie einen Namen für die *ruleSet* Datei, und wählen Sie dann **speichern**.

   Der neue Regelsatz ausgewählt ist, der **diesen Regelsatz ausführen** Liste.

6. Wählen Sie **öffnen** zu den neuen Regelsatz, der in den Regelsatz-Editor zu öffnen.

### <a name="rule-precedence"></a>Rangfolge der Regeln

- Ist die gleiche Regel aufgeführten zwei oder mehr Vorkommen in einer Regel, die von unterschiedlichem Schweregrad festlegen, generiert der Compiler einen Fehler aus. Zum Beispiel:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Ist die gleiche Regel aufgeführten zwei oder mehr Vorkommen in einem Regelsatz mit der *gleichen* Schweregrad, möglicherweise die folgende Warnung angezeigt der **Fehlerliste**:

   **CA0063: Fehler beim Laden der Regelsatzdatei "\[Ihre] ruleSet ' oder eine ihrer abhängigen Regelsatzdateien Dateien festgelegt. Die Datei entspricht nicht das regelschema für die Gruppe.**

- Wenn Sie einen untergeordneten Regelsatz mit der Regel enthält eine **Include** Tag und die untergeordneten und übergeordneten Regelsätze beide Listen Sie die gleiche Regel jedoch von unterschiedlichem Schweregrad, klicken Sie dann der Schweregrad in den übergeordneten Regelsatz Vorrang. Zum Beispiel:

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>Name und Beschreibung

Um den Anzeigenamen des einen Regelsatzes ändern, die im Editor geöffnet ist, öffnen die **Eigenschaften** Fenster durch Auswahl **Ansicht** > **Fenster "Eigenschaften"** in der Menüleiste. Geben Sie den Anzeigenamen in den **Namen** Feld. Sie können auch eine Beschreibung für den Regelsatz eingeben.

## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie eine Regel festgelegt haben, besteht der nächste Schritt, um die Regeln anpassen, hinzufügen oder Entfernen von Regeln oder ändern den Schweregrad von Regelverstößen.

> [!div class="nextstepaction"]
> [Ändern von Regeln in den Regelsatz-editor](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Codeanalyse-Regelsatzreferenz](../code-quality/rule-set-reference.md)