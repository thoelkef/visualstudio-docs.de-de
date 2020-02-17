---
title: Verwenden von Regelsätzen zum angeben C++ der zu testenden Regeln | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: ff105af1d817613b324e1158130457eb906c753f
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277855"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] und [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)]können Sie einen benutzerdefinierten *Regelsatz* erstellen und ändern, um bestimmte Projektanforderungen zu erfüllen, die mit der Code Analyse verknüpft sind. Um einen benutzerdefinierten C++ Regelsatz zu erstellen, mussC++ ein C/-Projekt in der Visual Studio-IDE geöffnet sein. Öffnen Sie dann einen Standardregel Satz im Regelsatz-Editor, und fügen Sie bestimmte Regeln hinzu bzw. entfernen Sie Sie, und ändern Sie optional die Aktion, die auftritt, wenn die Code Analyse festlegt, dass eine Regel verletzt wurde.  
  
 Zum Erstellen eines neuen benutzerdefinierten Regelsatzes speichern Sie diesen unter einem neuen Dateinamen. Der benutzerdefinierte Regelsatz wird dem Projekt automatisch zugewiesen.  
  
## <a name="opening-the-rule-set-editor"></a>Öffnen des Regelsatz-Editors  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>So erstellen Sie eine benutzerdefinierte Regel aus einem einzelnen vorhandenen Regelsatz  
  
1. Öffnen Sie in Projektmappen-Explorer das Kontextmenü für das Projekt, und wählen Sie dann **Eigenschaften**aus.  
  
2. Wählen Sie auf der Registerkarte **Eigenschaften** die Option **Code Analyse**aus.  
  
3. Führen Sie in der Dropdown Liste **Regelsatz** einen der folgenden Schritte aus:  
  
   - Wählen Sie den Regelsatz aus, den Sie anpassen möchten.  
  
     \- oder –  
  
   - Wählen Sie **\<durchsuchen... >** , um einen vorhandenen Regelsatz anzugeben, der nicht in der Liste enthalten ist.  
  
4. Wählen Sie **Öffnen** aus, um die Regeln im Regelsatz-Editor anzuzeigen.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>So ändern Sie einen Regelsatz im Regelsatz-Editor  
  
- Um den anzeigen amen des Regelsatzes zu ändern, wählen Sie im Menü **Ansicht** die Option **Eigenschaften Fenster**aus. Geben Sie den anzeigen Amen in das Feld **Name** ein. Der Anzeigename kann sich vom Dateinamen unterscheiden.  
  
- Wenn Sie einem benutzerdefinierten Regelsatz alle Regeln der Gruppe hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Gruppe. Wenn Sie alle Regeln der Gruppe entfernen möchten, deaktivieren Sie das Kontrollkästchen.  
  
- Wenn Sie dem benutzerdefinierten Regelsatz eine bestimmte Regel hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Regel. Wenn Sie die Regel aus dem Regelsatz entfernen möchten, deaktivieren Sie das zugehörige Kontrollkästchen.  
  
- Um die Aktion zu ändern, die durchgeführt wird, wenn eine Regel in einer Code Analyse verletzt wird, wählen Sie das Feld **Aktion** für die Regel aus, und wählen Sie dann einen der folgenden Werte aus:  
  
     **Warnung: generiert** eine Warnung.  
  
     **Fehler** -generiert einen Fehler.  
  
     **Keine** : deaktiviert die Regel. Diese Aktion ist mit der Aktion identisch, die beim Entfernen der Regel aus dem Regelsatz ausgeführt wird.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>So gruppieren, filtern oder ändert Sie Felder auf der Symbolleiste des Regelsatz-Editors  
  
- Um die Regeln in allen Gruppen zu erweitern, wählen Sie **Alle erweitern**aus.  
  
- Um die Regeln in allen Gruppen zu reduzieren, wählen Sie **alle**reduzieren aus.  
  
- Wenn Sie das Feld ändern möchten, nach dem Regeln gruppiert werden, wählen Sie das Feld aus der Liste **Gruppieren nach** aus. Wählen Sie **\<keine >** aus, um die Regeln nicht gruppiert anzuzeigen.  
  
- Wählen Sie **Spaltenoptionen**aus, um Felder in Regel Spalten hinzuzufügen oder zu entfernen.  
  
- Um Regeln auszublenden, die nicht für die aktuelle Projekt Mappe gelten, wählen Sie **Regeln ausblenden aus, die nicht auf die aktuelle**Projekt Mappe angewendet werden.  
  
- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Fehler Aktion zugewiesen ist, wählen Sie **Regeln anzeigen, die Code Analysefehler generieren können**.  
  
- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Warnungs Aktion zugewiesen ist, wählen Sie **Regeln anzeigen, die Code Analyse Warnungen generieren können**aus.  
  
- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Aktion **keine** zugewiesen ist, wählen Sie **nicht aktivierte Regeln anzeigen**aus.  
  
- Um dem aktuellen Regelsatz Microsoft-Standardregel Sätze hinzuzufügen oder daraus zu entfernen, wählen Sie untergeordnete **Regelsätze hinzufügen oder entfernen**aus.
