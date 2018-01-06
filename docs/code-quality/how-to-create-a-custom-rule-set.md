---
title: 'Vorgehensweise: Erstellen eines benutzerdefinierten Regelsatzes | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.addremoverulesets
helpviewer_keywords: Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 36b5e9e0a3ca0a994547679ba71e545b4235b6c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-rule-set"></a>Gewusst wie: Erstellen eines benutzerdefinierten Regelsatzes
In [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)], und [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], können Sie erstellen und ändern Sie eine benutzerdefinierte *Regelsatz* um bestimmte projektanforderungen mit der Codeanalyse zu erfüllen. Zum Erstellen eines benutzerdefinierten Regelsatzes öffnen Sie einen oder mehrere Standardregelsätze im Regelsatz-Editor. Anschließend können Sie bestimmte Regeln hinzufügen oder entfernen sowie Sie die Aktion ändern, die ausgeführt wird, wenn von der Codeanalyse ein Verstoß gegen eine Regel festgestellt wurde.  
  
 Zum Erstellen eines neuen benutzerdefinierten Regelsatzes speichern Sie diesen unter einem neuen Dateinamen. Der benutzerdefinierte Regelsatz wird dem Projekt automatisch zugewiesen.  
  
## <a name="opening-the-rule-set-editor"></a>Öffnen des Regelsatz-Editors  
  
#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>So öffnen Sie eine leere Regelsatzdatei im Regelsatz-Editor  
  
1.  Auf der **Datei** Menü [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], zeigen Sie auf **neu** , und klicken Sie dann auf **Datei**.  
  
2.  In der **neue Datei** (Dialogfeld), klicken Sie auf **allgemeine** in der **installierte Vorlagen** aus, und wählen Sie dann **Codeanalyse-Regelsatz**.  
  
3.  Der Regelsatz-Editor wird angezeigt. In der Editorliste sind keine Regeln ausgewählt.  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>So erstellen Sie eine benutzerdefinierte Regel aus einem einzelnen vorhandenen Regelsatz  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste des Projekts, und wählen Sie dann **Eigenschaften**.  
  
2.  Auf der **Eigenschaften** auf **Codeanalyse**.  
  
3.  In der **Regelsatz** Dropdown-Liste, führen Sie einen der folgenden:  
  
    -   Wählen Sie den Regelsatz aus, den Sie anpassen möchten.  
  
     \- oder –  
  
    -   Wählen Sie  **\<durchsuchen... >** Geben Sie einen vorhandenen Regelsatz ist nicht in der Liste.  
  
4.  Klicken Sie auf **öffnen** auf die Regeln im Regelsatz-Editor anzuzeigen.  
  
#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>So erstellen Sie einen benutzerdefinierten Regelsatz aus mehreren vorhandenen Regelsätzen  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste des Projekts, und wählen Sie dann **Eigenschaften**.  
  
2.  Auf der **Eigenschaften** auf **Codeanalyse**.  
  
3.  Wählen Sie  **\<auswählen, die mehrere Regelsätzen... >** aus **diesen Regelsatz ausführen**.  
  
4.  In der **Regelsätze hinzufügen oder entfernen Sie** wählen Sie im Dialogfeld die Regel aktiviert werden soll der neuen Regelsatz basieren, und klicken Sie dann auf **OK**.  
  
5.  Speichern Sie den neuen Regelsatz.  
  
     Der Name des neuen Regelsatzes ist ausgewählt, der **diesen Regelsatz ausführen** Liste. Der Anzeigename des Regelsatzes kann im nächsten Schritt geändert werden.  
  
6.  (Optional) Der Anzeigename des Regelsatzes, zum Ändern der **Ansicht** Menü klicken Sie auf **Fenster "Eigenschaften"**. Geben Sie den Namen in der **Namen** Feld.  
  
7.  Zum Hinzufügen zu entfernen, oder ändern Sie im neuen Regelsatz einzelne Codeanalyseregeln, klicken Sie auf **öffnen**.  
  
## <a name="modifying-a-rule-set"></a>Ändern eines Regelsatzes  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>So ändern Sie einen Regelsatz im Regelsatz-Editor  
  
-   Der Anzeigename des Regelsatzes, zum Ändern der **Ansicht** Menü klicken Sie auf **Fenster "Eigenschaften"**. Geben Sie den Anzeigenamen in der **Namen** Feld. Der Anzeigename kann sich vom Dateinamen unterscheiden.  
  
-   Wenn Sie einem benutzerdefinierten Regelsatz alle Regeln der Gruppe hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Gruppe. Wenn Sie alle Regeln der Gruppe entfernen möchten, deaktivieren Sie das Kontrollkästchen.  
  
-   Wenn Sie dem benutzerdefinierten Regelsatz eine bestimmte Regel hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Regel. Wenn Sie die Regel aus dem Regelsatz entfernen möchten, deaktivieren Sie das zugehörige Kontrollkästchen.  
  
-   Um die Aktion ausführt, wenn es sich bei einem Verstoß gegen eine Regel in einer Codeanalyse zu ändern, klicken Sie in der **Aktion** Feld für die Regel, und wählen Sie dann einen der folgenden Werte:  
  
     **Warnhinweis anzeigen,** -wird eine Warnung generiert.  
  
     **Fehler beim** -generiert einen Fehler.  
  
     **Keine** -deaktiviert die Regel. Diese Aktion ist mit der Aktion identisch, die beim Entfernen der Regel aus dem Regelsatz ausgeführt wird.  
  
## <a name="changing-the-rule-set-editor-display"></a>Ändern der Anzeige im Regelsatz-Editor  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>So gruppieren, filtern oder ändert Sie Felder auf der Symbolleiste des Regelsatz-Editors  
  
-   Um die Regeln in allen Gruppen erweitern möchten, klicken Sie auf **alle erweitern**.  
  
-   Um die Regeln in allen Gruppen reduzieren möchten, klicken Sie auf **alle reduzieren**.  
  
-   Um das Feld ändern, die Regeln gruppiert werden, wählen Sie das Feld aus der **Group By** Liste. Um die Regeln ohne Gruppierung anzuzeigen, wählen Sie  **\<None >**.  
  
-   Klicken Sie zum Hinzufügen oder entfernen in Regelspalten Felder, die auf **Spaltenoptionen**.  
  
-   So blenden Sie Regeln aus, die nicht für die aktuelle Projektmappe gelten **Ausblenden von Regeln, die nicht für die aktuelle Projektmappe gelten**.  
  
-   Zum Wechseln zwischen dem ein- und Ausblenden von Regeln, die die Fehleraktion zugewiesen sind, klicken Sie auf **Regeln angezeigt, die Codeanalysefehler generieren können**.  
  
-   Zum Wechseln zwischen dem ein- und Ausblenden von Regeln, die die Warnaktion zugewiesen sind, klicken Sie auf **Regeln angezeigt, die codeanalysewarnungen generieren können**.  
  
-   So wechseln Sie zwischen dem ein- und Ausblenden von Regeln, die zugewiesen wurden die **keine** Aktionen aufgeführt, klicken Sie auf **Regeln angezeigt, die nicht aktiviert sind**.  
  
-   Zum Hinzufügen oder Entfernen von Microsoft-hinzuzufügen dem aktuellen Regelsatz Standardregelsätze, klicken Sie auf **Add- oder Remove untergeordnete Regelsätze**.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Codeanalyse-Regelsatzreferenz](../code-quality/code-analysis-rule-set-reference.md)