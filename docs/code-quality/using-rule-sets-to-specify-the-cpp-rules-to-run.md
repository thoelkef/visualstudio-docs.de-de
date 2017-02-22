---
title: "Verwenden von Regels&#228;tzen zum Festlegen von C++-Regeln f&#252;r die Ausf&#252;hrung | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Verwenden von Regels&#228;tzen zum Festlegen von C++-Regeln f&#252;r die Ausf&#252;hrung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] und [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] können Sie einen benutzerdefinierten *Regelsatz* erstellen und ändern, um bestimmte Projektanforderungen für die Codeanalyse zu erfüllen.  Um einen benutzerdefinierten C\+\+\-Regelsatz zu erstellen, muss Projekt eine \/C \+\+ in der Visual Studio\-Entwicklungsumgebung geöffnet sein.  Sie öffnen einen Standardregelsatz im Regelsatz\-Editor und anschließend fügen hinzu oder entfernen bestimmte Regeln und optional die Aktion ändern, die auftritt, wenn eine Codeanalyse bestimmt, dass eine Regel verstoßen wurde.  
  
 Zum Erstellen eines neuen benutzerdefinierten Regelsatzes speichern Sie diesen unter einem neuen Dateinamen.  Der benutzerdefinierte Regelsatz wird dem Projekt automatisch zugewiesen.  
  
## Öffnen des Regelsatz\-Editors  
  
#### So erstellen Sie eine benutzerdefinierte Regel aus einem einzelnen vorhandenen Regelsatz  
  
1.  In Projektmappen\-Explorer öffnen Explorer, das Kontextmenü für das Projekt und dann **Eigenschaften** aus.  
  
2.  Auf der Registerkarte **Eigenschaften** wählen Sie **Codeanalyse** aus.  
  
3.  Führen Sie in der Dropdownliste **Regelsatz** einen der folgenden Schritte aus:  
  
    -   Wählen Sie den Regelsatz, den Sie anpassen möchten.  
  
     – oder –  
  
    -   Wählen **\<Durchsuchen...\>**, um einen vorhandenen Regelsatz anzugeben, der nicht in der Liste ist.  
  
4.  Wählen **Öffnen**, um die Regeln im Regelsatz\-Editor anzuzeigen.  
  
#### So ändern Sie einen Regelsatz im Regelsatz\-Editor  
  
-   Um der Anzeigename des Regelsatzes, im Menü **Ansicht** zu ändern, wählen Sie **Eigenschaftenfenster** aus.  Geben Sie im Feld **Name** den gewünschten Anzeigenamen ein.  Der Anzeigename kann sich vom Dateinamen unterscheiden.  
  
-   Wenn Sie einem benutzerdefinierten Regelsatz alle Regeln der Gruppe hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Gruppe.  Wenn Sie alle Regeln der Gruppe entfernen möchten, deaktivieren Sie das Kontrollkästchen.  
  
-   Wenn Sie dem benutzerdefinierten Regelsatz eine bestimmte Regel hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Regel.  Wenn Sie die Regel aus dem Regelsatz entfernen möchten, deaktivieren Sie das zugehörige Kontrollkästchen.  
  
-   Wenn Sie die Aktion ändern wenn eine Regel in einer Codeanalyse verstoßen wird, wählen Sie das Feld **Aktion** für die Regel und wählen Sie dann einen der folgenden Werte aus:  
  
     **Warn** – erzeugt eine Warnung.  
  
     **Error**\- erzeugt einen Fehler.  
  
     **None** \- deaktiviert die Regel.  Diese Aktion ist mit der Aktion identisch, die beim Entfernen der Regel aus dem Regelsatz ausgeführt wird.  
  
#### So gruppieren, filtern oder ändert Sie Felder auf der Symbolleiste des Regelsatz\-Editors  
  
-   Wenn Sie die Regeln in allen Gruppen erweitern, wählen Sie **Alle erweitern** aus.  
  
-   Wenn Sie die Regeln in allen Gruppen reduzieren, wählen Sie **Alle reduzieren** aus.  
  
-   Um das Feld ändern möchten anhand dessen Regeln gruppiert werden, wählen Sie das Feld in der Liste **Gruppieren nach**.  Wenn Sie die Regeln ohne Gruppierung anzeigen möchten, wählen Sie **\<Keine\>** aus.  
  
-   Wenn Sie in Regelspalten Felder hinzuzufügen oder zu entfernen, wählen Sie **Spaltenoptionen** aus.  
  
-   Um Regeln auszublenden die nicht für die aktuelle Projektmappe gelten, wählen Sie **Regeln ausblenden, die auf die aktuelle Projektmappe nicht zutreffen** aus.  
  
-   Um zwischen dem Ein\- und Ausblenden von Regeln wechseln denen die Fehleraktion zugewiesen ist, wählen Sie **Regeln anzeigen, die Codeanalysefehler generieren können** aus.  
  
-   Um zwischen dem Ein\- und Ausblenden von Regeln wechseln die die Warnregel Aktion zugewiesen werden, wählen Sie **Regeln anzeigen, die Codeanalysewarnungen generieren können** aus.  
  
-   Um zwischen dem Ein\- und Ausblenden von Regeln wechseln die die Aktion **Keine** zugewiesen werden, wählen Sie **Nicht aktivierte Regeln anzeigen** aus.  
  
-   So Microsoft hinzuzufügen oder zu entfernen führen Regelsätze zum aktuellen Regelsatz, **Untergeordnete Regelsätze hinzufügen oder entfernen** auswählen.