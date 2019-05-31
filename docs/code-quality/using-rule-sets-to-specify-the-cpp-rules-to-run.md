---
title: Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung
ms.date: 04/28/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: d4d7dfc1f010b860653edbe14fa7af9050bddba4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820372"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung

In Visual Studio können Sie erstellen und ändern Sie eine benutzerdefinierte *Regelsatz* um bestimmte projektanforderungen mit der Codeanalyse zu erfüllen. Die Standardregelsätze befinden sich im `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Visual Studio 2017 Version 15.7 und höher** Sie benutzerdefinierten Regelsätzen, die mit einem beliebigen Text-Editor erstellen und sie in Befehlszeilenbuilds unabhängig davon, was System erstellen, Sie verwenden, anwenden können. Weitere Informationen finden Sie unter [/ analyze: Ruleset](/cpp/build/reference/analyze-code-analysis).

Um eine benutzerdefinierte C++-Regel legen Sie in Visual Studio zu erstellen, muss eine C/C++-Projekt in Visual Studio-IDE geöffnet sein. Sie öffnen Sie dann einen standard-Regelsatz im Regelsatz-Editor, und klicken Sie dann hinzufügen oder entfernen bestimmte Regeln und optional ändern die Aktion, die tritt auf, wenn der Codeanalyse festgestellt, dass eine Regel verletzt wurde.

Zum Erstellen eines neuen benutzerdefinierten Regelsatzes speichern Sie diesen unter einem neuen Dateinamen. Der benutzerdefinierte Regelsatz wird dem Projekt automatisch zugewiesen.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>So erstellen Sie eine benutzerdefinierte Regel aus einem einzelnen vorhandenen Regelsatz

1. Klicken Sie im Projektmappen-Explorer das Kontextmenü für das Projekt, und wählen Sie dann **Eigenschaften**.

2. Auf der **Eigenschaften** Registerkarte **Codeanalyse**.

3. In der **Regelsatz** Dropdown-Listenfeld, führen Sie einen der folgenden:

   - Wählen Sie den Regelsatz, den Sie anpassen möchten.

     \- oder –

   - Wählen Sie  **\<durchsuchen... >** an einen vorhandenen Regelsatz ist nicht in der Liste.

4. Wählen Sie **öffnen** zu Regeln in den Regelsatz-Editor anzuzeigen.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>So ändern Sie einen Regelsatz im Regelsatz-Editor

- So ändern Sie den Anzeigenamen des Regelsatzes auf die **Ansicht** Menü wählen **Fenster "Eigenschaften"** . Geben Sie den Anzeigenamen in den **Namen** Feld. Der Anzeigename kann sich vom Dateinamen unterscheiden.

- Wenn Sie einem benutzerdefinierten Regelsatz alle Regeln der Gruppe hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Gruppe. Wenn Sie alle Regeln der Gruppe entfernen möchten, deaktivieren Sie das Kontrollkästchen.

- Wenn Sie dem benutzerdefinierten Regelsatz eine bestimmte Regel hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Regel. Wenn Sie die Regel aus dem Regelsatz entfernen möchten, deaktivieren Sie das zugehörige Kontrollkästchen.

- Wählen Sie zum Ändern der Aktion ausgeführt, wenn in einer Codeanalyse gegen eine Regel verstoßen wird die **Aktion** Feld für die Regel, und wählen Sie dann eine der folgenden Werte:

     **Warnhinweis anzeigen,** – wird eine Warnung generiert.

     **Fehler** -generiert einen Fehler.

     **Keine** -deaktiviert die Regel. Diese Aktion ist mit der Aktion identisch, die beim Entfernen der Regel aus dem Regelsatz ausgeführt wird.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>So gruppieren, filtern oder ändert Sie Felder auf der Symbolleiste des Regelsatz-Editors

- Um die Regeln in allen Gruppen erweitern möchten, wählen Sie **alle erweitern**.

- Um die Regeln in allen Gruppen reduzieren möchten, wählen Sie **alle reduzieren**.

- Wählen Sie das Feld aus, um das Feld ändern, die Regeln gruppiert werden, die **Group By** Liste. Um die Regeln ohne Gruppierung anzuzeigen, wählen Sie  **\<None >** .

- Wählen Sie zum Hinzufügen oder entfernen in Regelspalten Felder, **Spaltenoptionen**.

- Wählen Sie zum Ausblenden von Regeln, die nicht für die aktuelle Projektmappe gelten, **Ausblenden von Regeln, die nicht für die aktuelle Projektmappe gelten**.

- Wählen Sie zum Wechseln zwischen anzeigen und Ausblenden von Regeln, die die Fehleraktion zugewiesen sind, **Anzeigen von Regeln, die Codeanalysefehler generieren können**.

- Wählen Sie zum Wechseln zwischen anzeigen und Ausblenden von Regeln, die die Warnaktion zugewiesen sind, **Anzeigen von Regeln, die codeanalysewarnungen generieren können**.

- Zum Umschalten zwischen einblenden und Ausblenden von Regeln, die zugewiesen werden die **keine** Aktion wählen **Regeln, die nicht aktiviert werden anzeigen**.

- Wählen Sie zum Hinzufügen oder entfernen Microsoft-auf dem aktuellen Regelsatz Standardregelsätze, **hinzufügen oder Entfernen von untergeordnete Regelsätze**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Legen Sie zum Erstellen einer Regel in einem Text-editor

Können Sie einen benutzerdefinierten Regelsatz erstellen Sie in einem Text-Editor, speichern Sie sie an einem beliebigen Speicherort mit einem `.ruleset` -Erweiterung, und wenden Sie sich mit der [/ analyze: Ruleset](/cpp/build/reference/analyze-code-analysis) -Compileroption.

Das folgende Beispiel zeigt, dass eine einfache Regel Datei festgelegt, die Sie als Ausgangspunkt verwenden können:

::: moniker range="vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end
