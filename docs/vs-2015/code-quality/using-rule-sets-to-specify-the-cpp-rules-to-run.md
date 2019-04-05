---
title: Mit Regel legt fest, an der C++-Regeln für die Ausführung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 55ce3ac93f280d5b5cd29fdc533035dc32cbaa8c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957953"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] und [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], können Sie erstellen und ändern Sie eine benutzerdefinierte *Regelsatz* um bestimmte projektanforderungen mit der Codeanalyse zu erfüllen. Legen Sie zum Erstellen einer benutzerdefinierte C++-Regel muss ein C-/C++-Projekt in Visual Studio-IDE geöffnet. Sie öffnen Sie dann einen standard-Regelsatz im Regelsatz-Editor, und klicken Sie dann hinzufügen oder entfernen bestimmte Regeln und optional ändern die Aktion, die tritt auf, wenn der Codeanalyse festgestellt, dass eine Regel verletzt wurde.  
  
 Zum Erstellen eines neuen benutzerdefinierten Regelsatzes speichern Sie diesen unter einem neuen Dateinamen. Der benutzerdefinierte Regelsatz wird dem Projekt automatisch zugewiesen.  
  
## <a name="opening-the-rule-set-editor"></a>Öffnen des Regelsatz-Editors  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>So erstellen Sie eine benutzerdefinierte Regel aus einem einzelnen vorhandenen Regelsatz  
  
1. Klicken Sie im Projektmappen-Explorer das Kontextmenü für das Projekt, und wählen Sie dann **Eigenschaften**.  
  
2. Auf der **Eigenschaften** Registerkarte **Codeanalyse**.  
  
3. In der **Regelsatz** Dropdown-Listenfeld, führen Sie einen der folgenden:  
  
   - Wählen Sie den Regelsatz, den Sie anpassen möchten.  
  
     \- oder –  
  
   - Wählen Sie  **\<durchsuchen... >** an einen vorhandenen Regelsatz ist nicht in der Liste.  
  
4. Wählen Sie **öffnen** zu Regeln in den Regelsatz-Editor anzuzeigen.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>So ändern Sie einen Regelsatz im Regelsatz-Editor  
  
-   So ändern Sie den Anzeigenamen des Regelsatzes auf die **Ansicht** Menü wählen **Fenster "Eigenschaften"**. Geben Sie den Anzeigenamen in den **Namen** Feld. Der Anzeigename kann sich vom Dateinamen unterscheiden.  
  
-   Wenn Sie einem benutzerdefinierten Regelsatz alle Regeln der Gruppe hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Gruppe. Wenn Sie alle Regeln der Gruppe entfernen möchten, deaktivieren Sie das Kontrollkästchen.  
  
-   Wenn Sie dem benutzerdefinierten Regelsatz eine bestimmte Regel hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Regel. Wenn Sie die Regel aus dem Regelsatz entfernen möchten, deaktivieren Sie das zugehörige Kontrollkästchen.  
  
-   Wählen Sie zum Ändern der Aktion ausgeführt, wenn in einer Codeanalyse gegen eine Regel verstoßen wird die **Aktion** Feld für die Regel, und wählen Sie dann eine der folgenden Werte:  
  
     **Warnhinweis anzeigen,** – wird eine Warnung generiert.  
  
     **Fehler** -generiert einen Fehler.  
  
     **Keine** -deaktiviert die Regel. Diese Aktion ist mit der Aktion identisch, die beim Entfernen der Regel aus dem Regelsatz ausgeführt wird.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>So gruppieren, filtern oder ändert Sie Felder auf der Symbolleiste des Regelsatz-Editors  
  
-   Um die Regeln in allen Gruppen erweitern möchten, wählen Sie **alle erweitern**.  
  
-   Um die Regeln in allen Gruppen reduzieren möchten, wählen Sie **alle reduzieren**.  
  
-   Wählen Sie das Feld aus, um das Feld ändern, die Regeln gruppiert werden, die **Group By** Liste. Um die Regeln ohne Gruppierung anzuzeigen, wählen Sie  **\<None >**.  
  
-   Wählen Sie zum Hinzufügen oder entfernen in Regelspalten Felder, **Spaltenoptionen**.  
  
-   Wählen Sie zum Ausblenden von Regeln, die nicht für die aktuelle Projektmappe gelten, **Ausblenden von Regeln, die nicht für die aktuelle Projektmappe gelten**.  
  
-   Wählen Sie zum Wechseln zwischen anzeigen und Ausblenden von Regeln, die die Fehleraktion zugewiesen sind, **Anzeigen von Regeln, die Codeanalysefehler generieren können**.  
  
-   Wählen Sie zum Wechseln zwischen anzeigen und Ausblenden von Regeln, die die Warnaktion zugewiesen sind, **Anzeigen von Regeln, die codeanalysewarnungen generieren können**.  
  
-   Zum Umschalten zwischen einblenden und Ausblenden von Regeln, die zugewiesen werden die **keine** Aktion wählen **Regeln, die nicht aktiviert werden anzeigen**.  
  
-   Wählen Sie zum Hinzufügen oder entfernen Microsoft-auf dem aktuellen Regelsatz Standardregelsätze, **hinzufügen oder Entfernen von untergeordnete Regelsätze**.
