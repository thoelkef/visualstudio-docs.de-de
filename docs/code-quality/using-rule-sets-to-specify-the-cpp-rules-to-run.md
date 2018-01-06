---
title: "Mithilfe der Regel an die C++-Regeln für die Ausführung legt | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f78a3f48ce6e8d08134694bc03c80f9c2e9b3363
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung
In [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] und [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], können Sie erstellen und ändern Sie eine benutzerdefinierte *Regelsatz* um bestimmte projektanforderungen mit der Codeanalyse zu erfüllen. Zum Erstellen eines benutzerdefinierten Regelsatzes für C++ festgelegt, muss ein C/C++-Projekt in Visual Studio-IDE geöffnet werden. Sie öffnen Sie einen standard-Regelsatz im Regelsatz-Editor und dann hinzufügen oder entfernen bestimmte Regeln und optional die Aktion, die bei der Codeanalyse feststellt, dass es sich bei einem Verstoß gegen eine Regel ändern.  
  
 Zum Erstellen eines neuen benutzerdefinierten Regelsatzes speichern Sie diesen unter einem neuen Dateinamen. Der benutzerdefinierte Regelsatz wird dem Projekt automatisch zugewiesen.  
  
## <a name="opening-the-rule-set-editor"></a>Öffnen des Regelsatz-Editors  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>So erstellen Sie eine benutzerdefinierte Regel aus einem einzelnen vorhandenen Regelsatz  
  
1.  Klicken Sie im Projektmappen-Explorer das Kontextmenü für das Projekt zu öffnen, und wählen Sie dann **Eigenschaften**.  
  
2.  Auf der **Eigenschaften** Registerkarte **Codeanalyse**.  
  
3.  In der **Regelsatz** Dropdown-Liste, führen Sie einen der folgenden:  
  
    -   Wählen Sie den Regelsatz, den Sie anpassen möchten.  
  
     \- oder –  
  
    -   Wählen Sie  **\<durchsuchen... >** Geben Sie einen vorhandenen Regelsatz ist nicht in der Liste.  
  
4.  Wählen Sie **öffnen** auf die Regeln im Regelsatz-Editor anzuzeigen.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>So ändern Sie einen Regelsatz im Regelsatz-Editor  
  
-   Der Anzeigename des Regelsatzes, zum Ändern der **Ansicht** Menü wählen **Fenster "Eigenschaften"**. Geben Sie den Anzeigenamen in der **Namen** Feld. Der Anzeigename kann sich vom Dateinamen unterscheiden.  
  
-   Wenn Sie einem benutzerdefinierten Regelsatz alle Regeln der Gruppe hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Gruppe. Wenn Sie alle Regeln der Gruppe entfernen möchten, deaktivieren Sie das Kontrollkästchen.  
  
-   Wenn Sie dem benutzerdefinierten Regelsatz eine bestimmte Regel hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Regel. Wenn Sie die Regel aus dem Regelsatz entfernen möchten, deaktivieren Sie das zugehörige Kontrollkästchen.  
  
-   Um die Aktion ausführt, wenn es sich bei einem Verstoß gegen eine Regel in einer Codeanalyse zu ändern, wählen Sie die **Aktion** Feld für die Regel, und wählen Sie dann einen der folgenden Werte:  
  
     **Warnhinweis anzeigen,** -wird eine Warnung generiert.  
  
     **Fehler beim** -generiert einen Fehler.  
  
     **Keine** -deaktiviert die Regel. Diese Aktion ist mit der Aktion identisch, die beim Entfernen der Regel aus dem Regelsatz ausgeführt wird.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>So gruppieren, filtern oder ändert Sie Felder auf der Symbolleiste des Regelsatz-Editors  
  
-   Um die Regeln in allen Gruppen erweitern möchten, wählen Sie **alle erweitern**.  
  
-   Um die Regeln in allen Gruppen reduzieren möchten, wählen Sie **alle reduzieren**.  
  
-   Wählen Sie das Feld aus, um das Feld ändern, die Regeln gruppiert werden, die **Group By** Liste. Um die Regeln ohne Gruppierung anzuzeigen, wählen Sie  **\<None >**.  
  
-   Wählen Sie zum Hinzufügen oder Entfernen von Feldern in Regelspalten, **Spaltenoptionen**.  
  
-   Ausblenden von Regeln, die auf der aktuellen Projektmappe nicht anwendbar sind, wählen Sie **Ausblenden von Regeln, die nicht für die aktuelle Projektmappe gelten**.  
  
-   Zum Wechseln zwischen dem ein- und Ausblenden von Regeln, die die Fehleraktion zugewiesen sind, wählen Sie **Regeln angezeigt, die Codeanalysefehler generieren können**.  
  
-   Zum Wechseln zwischen dem ein- und Ausblenden von Regeln, die die Warnaktion zugewiesen sind, wählen Sie **Regeln angezeigt, die codeanalysewarnungen generieren können**.  
  
-   So wechseln Sie zwischen dem ein- und Ausblenden von Regeln, die zugewiesen wurden die **keine** Aktion, wählen Sie **Regeln angezeigt, die nicht aktiviert sind**.  
  
-   Wählen Sie zum Hinzufügen oder Entfernen von Microsoft-hinzuzufügen dem aktuellen Regelsatz Standardregelsätze, **Add- oder Remove untergeordnete Regelsätze**.