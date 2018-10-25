---
title: 'Vorgehensweise: Erstellen eines benutzerdefinierten Regelsatzes | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a5d8a5cb7e29cfd900ce81fa5f4b6253f0c49014
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812464"
---
# <a name="how-to-create-a-custom-rule-set"></a>Gewusst wie: Erstellen eines benutzerdefinierten Regelsatzes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)], und [!INCLUDE[vsPro](../includes/vspro-md.md)], können Sie erstellen und ändern Sie eine benutzerdefinierte *Regelsatz* um bestimmte projektanforderungen mit der Codeanalyse zu erfüllen. Zum Erstellen eines benutzerdefinierten Regelsatzes öffnen Sie einen oder mehrere Standardregelsätze im Regelsatz-Editor. Anschließend können Sie bestimmte Regeln hinzufügen oder entfernen sowie Sie die Aktion ändern, die ausgeführt wird, wenn von der Codeanalyse ein Verstoß gegen eine Regel festgestellt wurde.  
  
 Zum Erstellen eines neuen benutzerdefinierten Regelsatzes speichern Sie diesen unter einem neuen Dateinamen. Der benutzerdefinierte Regelsatz wird dem Projekt automatisch zugewiesen.  
  
## <a name="opening-the-rule-set-editor"></a>Öffnen des Regelsatz-Editors  
  
#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>So öffnen Sie eine leere Regelsatzdatei im Regelsatz-Editor  
  
1.  Auf der **Datei** Menü [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], zeigen Sie auf **neu** , und klicken Sie dann auf **Datei**.  
  
2.  In der **neue Datei** Dialogfeld klicken Sie auf **allgemeine** in die **installierte Vorlagen** aus, und wählen Sie dann **Codeanalyse-Regelsatz**.  
  
3.  Der Regelsatz-Editor wird angezeigt. In der Editorliste sind keine Regeln ausgewählt.  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>So erstellen Sie eine benutzerdefinierte Regel aus einem einzelnen vorhandenen Regelsatz  
  
1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Projekts, und wählen Sie dann **Eigenschaften**.  
  
2. Auf der **Eigenschaften** auf **Codeanalyse**.  
  
3. In der **Regelsatz** Dropdown-Listenfeld, führen Sie einen der folgenden:  
  
   - Wählen Sie den Regelsatz aus, den Sie anpassen möchten.  
  
     \- oder –  
  
   - Wählen Sie  **\<durchsuchen... >** an einen vorhandenen Regelsatz ist nicht in der Liste.  
  
4. Klicken Sie auf **öffnen** zu Regeln in den Regelsatz-Editor anzuzeigen.  
  
#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>So erstellen Sie einen benutzerdefinierten Regelsatz aus mehreren vorhandenen Regelsätzen  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Projekts, und wählen Sie dann **Eigenschaften**.  
  
2.  Auf der **Eigenschaften** auf **Codeanalyse**.  
  
3.  Wählen Sie  **\<auswählen, die mehrere Regelsätze... >** aus **diesen Regelsatz ausführen**.  
  
4.  In der **Regelsätze hinzufügen oder Entfernen von** wählen Sie im Dialogfeld die Regelsätze aus auf die Sie verwenden möchten, der neue Regelsatz basieren, und klicken Sie dann auf **OK**.  
  
5.  Speichern Sie den neuen Regelsatz.  
  
     Der Name der neuen Regel ausgewählt ist, der **diesen Regelsatz ausführen** Liste. Der Anzeigename des Regelsatzes kann im nächsten Schritt geändert werden.  
  
6.  (Optional) So ändern Sie den Anzeigenamen des Regelsatzes auf die **Ansicht** Menü klicken Sie auf **Fenster "Eigenschaften"**. Geben Sie den Namen in der **Namen** Feld.  
  
7.  Zum Hinzufügen zu entfernen oder ändern Sie im neuen Regelsatz einzelne Codeanalyseregeln, klicken Sie auf **öffnen**.  
  
## <a name="modifying-a-rule-set"></a>Ändern eines Regelsatzes  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>So ändern Sie einen Regelsatz im Regelsatz-Editor  
  
-   So ändern Sie den Anzeigenamen des Regelsatzes auf die **Ansicht** Menü klicken Sie auf **Fenster "Eigenschaften"**. Geben Sie den Anzeigenamen in den **Namen** Feld. Der Anzeigename kann sich vom Dateinamen unterscheiden.  
  
-   Wenn Sie einem benutzerdefinierten Regelsatz alle Regeln der Gruppe hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Gruppe. Wenn Sie alle Regeln der Gruppe entfernen möchten, deaktivieren Sie das Kontrollkästchen.  
  
-   Wenn Sie dem benutzerdefinierten Regelsatz eine bestimmte Regel hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Regel. Wenn Sie die Regel aus dem Regelsatz entfernen möchten, deaktivieren Sie das zugehörige Kontrollkästchen.  
  
-   Um die Aktion ausgeführt, wenn in einer Codeanalyse gegen eine Regel verstoßen wird zu ändern, klicken Sie in der **Aktion** Feld für die Regel, und wählen Sie eine der folgenden Werte:  
  
     **Warnhinweis anzeigen,** – wird eine Warnung generiert.  
  
     **Fehler** -generiert einen Fehler.  
  
     **Keine** -deaktiviert die Regel. Diese Aktion ist mit der Aktion identisch, die beim Entfernen der Regel aus dem Regelsatz ausgeführt wird.  
  
## <a name="changing-the-rule-set-editor-display"></a>Ändern der Anzeige im Regelsatz-Editor  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>So gruppieren, filtern oder ändert Sie Felder auf der Symbolleiste des Regelsatz-Editors  
  
-   Um die Regeln in allen Gruppen erweitern möchten, klicken Sie auf **alle erweitern**.  
  
-   Um die Regeln in allen Gruppen reduzieren möchten, klicken Sie auf **alle reduzieren**.  
  
-   Um das Feld ändern, die Regeln gruppiert werden, wählen Sie das Feld aus der **Group By** Liste. Wählen Sie zum Anzeigen der Regeln ohne Gruppierung  **\<None >**.  
  
-   Klicken Sie zum Hinzufügen oder entfernen in Regelspalten Felder, die auf **Spaltenoptionen**.  
  
-   Zum Ausblenden von Regeln, die nicht für die aktuelle Projektmappe gelten **Ausblenden von Regeln, die nicht für die aktuelle Projektmappe gelten**.  
  
-   Zum Wechseln zwischen anzeigen und Ausblenden von Regeln, die die Fehleraktion zugewiesen sind, klicken Sie auf **Anzeigen von Regeln, die Codeanalysefehler generieren können**.  
  
-   Zum Wechseln zwischen anzeigen und Ausblenden von Regeln, die die Warnaktion zugewiesen ist, klicken Sie auf **Anzeigen von Regeln, die codeanalysewarnungen generieren können**.  
  
-   Zum Umschalten zwischen einblenden und Ausblenden von Regeln, die zugewiesen sind die **keine** Aktion, klicken Sie auf **Regeln, die nicht aktiviert werden anzeigen**.  
  
-   Zum Hinzufügen oder entfernen Microsoft-auf dem aktuellen Regelsatz Standardregelsätze, klicken Sie auf **hinzufügen oder Entfernen von untergeordnete Regelsätze**.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Codeanalyse-Regelsatzreferenz](../code-quality/code-analysis-rule-set-reference.md)



