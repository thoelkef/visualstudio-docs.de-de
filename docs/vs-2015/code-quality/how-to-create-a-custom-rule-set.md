---
title: 'Vorgehensweise: Erstellen eines benutzerdefinierten Regelsatzes | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e4aef02a2bb320112d7d268da28cf66b1ec6751
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657449"
---
# <a name="how-to-create-a-custom-rule-set"></a>Gewusst wie: Erstellen eines benutzerdefinierten Regelsatzes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] und [!INCLUDE[vsPro](../includes/vspro-md.md)] können Sie einen benutzerdefinierten *Regelsatz* erstellen und ändern, um bestimmte Projektanforderungen zu erfüllen, die mit der Code Analyse verknüpft sind. Zum Erstellen eines benutzerdefinierten Regelsatzes öffnen Sie einen oder mehrere Standardregelsätze im Regelsatz-Editor. Anschließend können Sie bestimmte Regeln hinzufügen oder entfernen sowie Sie die Aktion ändern, die ausgeführt wird, wenn von der Codeanalyse ein Verstoß gegen eine Regel festgestellt wurde.

 Zum Erstellen eines neuen benutzerdefinierten Regelsatzes speichern Sie diesen unter einem neuen Dateinamen. Der benutzerdefinierte Regelsatz wird dem Projekt automatisch zugewiesen.

## <a name="opening-the-rule-set-editor"></a>Öffnen des Regelsatz-Editors

#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>So öffnen Sie eine leere Regelsatzdatei im Regelsatz-Editor

1. Zeigen Sie im Menü **Datei** von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] auf **neu** , und klicken Sie dann auf **Datei**.

2. Klicken Sie im Dialogfeld **neue Datei** in der Liste **installierte Vorlagen** auf **Allgemein** , und wählen Sie dann **Code Analyse-Regelsatz**aus.

3. Der Regelsatz-Editor wird angezeigt. In der Editorliste sind keine Regeln ausgewählt.

#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>So erstellen Sie eine benutzerdefinierte Regel aus einem einzelnen vorhandenen Regelsatz

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**aus.

2. Klicken Sie auf der Registerkarte **Eigenschaften** auf **Code Analyse**.

3. Führen Sie in der Dropdown Liste **Regelsatz** einen der folgenden Schritte aus:

   - Wählen Sie den Regelsatz aus, den Sie anpassen möchten.

     \- oder -

   - **@No__t_1Browse auswählen... >** , um einen vorhandenen Regelsatz anzugeben, der nicht in der Liste enthalten ist.

4. Klicken Sie auf **Öffnen** , um die Regeln im Regelsatz-Editor anzuzeigen.

#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>So erstellen Sie einen benutzerdefinierten Regelsatz aus mehreren vorhandenen Regelsätzen

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**aus.

2. Klicken Sie auf der Registerkarte **Eigenschaften** auf **Code Analyse**.

3. Wählen Sie **\<Choose mehrere Regelsätze aus... >** aus **diesen Regelsatz ausführen**.

4. Wählen Sie im Dialogfeld **Regelsätze hinzufügen oder entfernen** die Regelsätze aus, auf denen Sie den neuen Regelsatz aufbauen möchten, und klicken Sie dann auf **OK**.

5. Speichern Sie den neuen Regelsatz.

     Der Name des neuen Regelsatzes wird in der Liste **diesen Regelsatz ausführen** ausgewählt. Der Anzeigename des Regelsatzes kann im nächsten Schritt geändert werden.

6. Optionale Um den anzeigen amen des Regelsatzes zu ändern, klicken Sie im Menü **Ansicht** auf **Eigenschaften Fenster**. Geben Sie den anzeigen Amen in das Feld **Name** ein.

7. Klicken Sie auf **Öffnen**, um bestimmte Code Analyse Regeln im neuen Regelsatz hinzuzufügen, zu entfernen oder zu ändern.

## <a name="modifying-a-rule-set"></a>Ändern eines Regelsatzes

#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>So ändern Sie einen Regelsatz im Regelsatz-Editor

- Um den anzeigen amen des Regelsatzes zu ändern, klicken Sie im Menü **Ansicht** auf **Eigenschaften Fenster**. Geben Sie den anzeigen Amen in das Feld **Name** ein. Der Anzeigename kann sich vom Dateinamen unterscheiden.

- Wenn Sie einem benutzerdefinierten Regelsatz alle Regeln der Gruppe hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Gruppe. Wenn Sie alle Regeln der Gruppe entfernen möchten, deaktivieren Sie das Kontrollkästchen.

- Wenn Sie dem benutzerdefinierten Regelsatz eine bestimmte Regel hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Regel. Wenn Sie die Regel aus dem Regelsatz entfernen möchten, deaktivieren Sie das zugehörige Kontrollkästchen.

- Um die Aktion zu ändern, die durchgeführt wird, wenn eine Regel in einer Code Analyse verletzt wird, klicken Sie in das Feld **Aktion** für die Regel, und wählen Sie dann einen der folgenden Werte aus:

     **Warnung: generiert** eine Warnung.

     **Fehler** -generiert einen Fehler.

     **Keine** : deaktiviert die Regel. Diese Aktion ist mit der Aktion identisch, die beim Entfernen der Regel aus dem Regelsatz ausgeführt wird.

## <a name="changing-the-rule-set-editor-display"></a>Ändern der Anzeige im Regelsatz-Editor

#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>So gruppieren, filtern oder ändert Sie Felder auf der Symbolleiste des Regelsatz-Editors

- Um die Regeln in allen Gruppen zu erweitern, klicken Sie auf **Alle erweitern**.

- Klicken Sie auf **alle**reduzieren, um die Regeln in allen Gruppen zu reduzieren.

- Wenn Sie das Feld ändern möchten, nach dem Regeln gruppiert werden, wählen Sie das Feld aus der Liste **Gruppieren nach** aus. Wählen Sie **\<None >** aus, um die Regeln nicht gruppiert anzuzeigen.

- Zum Hinzufügen oder Entfernen von Feldern in Regel Spalten klicken Sie auf **Spaltenoptionen**.

- Um Regeln auszublenden, die nicht für die aktuelle Projekt Mappe gelten, blenden Sie Regeln aus, **die nicht auf die aktuelle**Projekt Mappe angewendet werden.

- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Fehler Aktion zugewiesen ist, klicken Sie auf **Regeln anzeigen, die Code Analysefehler generieren können**.

- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Warnungs Aktion zugewiesen ist, klicken Sie auf **Regeln anzeigen, die Code Analyse Warnungen generieren können**.

- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Aktion **keine** zugewiesen ist, klicken Sie auf **nicht aktivierte Regeln anzeigen**.

- Um dem aktuellen Regelsatz Microsoft-Standardregel Sätze hinzuzufügen oder daraus zu entfernen, klicken Sie auf untergeordnete **Regelsätze hinzufügen oder entfernen**.

## <a name="see-also"></a>Siehe auch
 Gewusst [wie: Konfigurieren der Code Analyse für einen](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [Code Analyse-Regelsatz Verweis](../code-quality/code-analysis-rule-set-reference.md) für ein verwaltetes Code Projekt
