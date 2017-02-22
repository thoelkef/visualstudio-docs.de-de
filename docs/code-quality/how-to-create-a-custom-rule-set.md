---
title: "Gewusst wie: Erstellen eines benutzerdefinierten Regelsatzes | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.addremoverulesets"
helpviewer_keywords: 
  - "Development Edition, Regelsätze"
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Erstellen eines benutzerdefinierten Regelsatzes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] und [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] können Sie einen benutzerdefinierten *Regelsatz* erstellen und ändern, um bestimmte Projektanforderungen für die Codeanalyse zu erfüllen.  Zum Erstellen eines benutzerdefinierten Regelsatzes öffnen Sie einen oder mehrere Standardregelsätze im Regelsatz\-Editor.  Anschließend können Sie bestimmte Regeln hinzufügen oder entfernen sowie Sie die Aktion ändern, die ausgeführt wird, wenn von der Codeanalyse ein Verstoß gegen eine Regel festgestellt wurde.  
  
 Zum Erstellen eines neuen benutzerdefinierten Regelsatzes speichern Sie diesen unter einem neuen Dateinamen.  Der benutzerdefinierte Regelsatz wird dem Projekt automatisch zugewiesen.  
  
## Öffnen des Regelsatz\-Editors  
  
#### So öffnen Sie eine leere Regelsatzdatei im Regelsatz\-Editor  
  
1.  Zeigen Sie in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] im Menü **Datei** auf **Neu**, und klicken Sie anschließend auf **Datei**.  
  
2.  Klicken Sie im Dialogfeld **Neue Datei** in die Liste **Installierte Vorlagen** auf **Allgemein**, und wählen Sie dann **Codeanalyse\-Regelsatz** aus.  
  
3.  Der Regelsatz\-Editor wird angezeigt.  In der Editorliste sind keine Regeln ausgewählt.  
  
#### So erstellen Sie eine benutzerdefinierte Regel aus einem einzelnen vorhandenen Regelsatz  
  
1.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** aus.  
  
2.  Klicken Sie auf der Registerkarte **Eigenschaften** auf **Codeanalyse**.  
  
3.  Führen Sie in der Dropdownliste **Regelsatz** einen der folgenden Schritte aus:  
  
    -   Wählen Sie den Regelsatz aus, den Sie anpassen möchten.  
  
     – oder –  
  
    -   Wählen Sie **\<Durchsuchen\>** aus, um einen vorhandenen Regelsatz anzugeben, der nicht in der Liste aufgeführt ist.  
  
4.  Klicken Sie auf **Öffnen**, um die Regeln im Regelsatz\-Editor anzuzeigen.  
  
#### So erstellen Sie einen benutzerdefinierten Regelsatz aus mehreren vorhandenen Regelsätzen  
  
1.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** aus.  
  
2.  Klicken Sie auf der Registerkarte **Eigenschaften** auf **Codeanalyse**.  
  
3.  Wählen Sie unter **Diesen Regelsatz ausführen** die Option **\<Mehrere Regelsätze auswählen...\>** aus.  
  
4.  Wählen Sie im Dialogfeld **Regelsätze hinzufügen oder entfernen** die Regelsätze aus, auf denen der neue Regelsatz basieren soll, und klicken Sie anschließend auf **OK**.  
  
5.  Speichern Sie den neuen Regelsatz.  
  
     Der Name des neuen Regelsatzes ist in der Liste **Diesen Regelsatz ausführen** ausgewählt.  Der Anzeigename des Regelsatzes kann im nächsten Schritt geändert werden.  
  
6.  \(Optional\) Klicken Sie zum Ändern des Anzeigenamens des Regelsatzes im Menü **Ansicht** auf **Eigenschaftenfenster**.  Geben Sie im Feld **Name** den gewünschten Anzeigenamen ein.  
  
7.  Wenn Sie im neuen Regelsatz einzelne Codeanalyseregeln hinzufügen, entfernen oder ändern möchten, klicken Sie auf **Öffnen**.  
  
## Ändern eines Regelsatzes  
  
#### So ändern Sie einen Regelsatz im Regelsatz\-Editor  
  
-   Klicken Sie zum Ändern des Anzeigenamens des Regelsatzes im Menü **Ansicht** auf **Eigenschaftenfenster**.  Geben Sie im Feld **Name** den gewünschten Anzeigenamen ein.  Der Anzeigename kann sich vom Dateinamen unterscheiden.  
  
-   Wenn Sie einem benutzerdefinierten Regelsatz alle Regeln der Gruppe hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Gruppe.  Wenn Sie alle Regeln der Gruppe entfernen möchten, deaktivieren Sie das Kontrollkästchen.  
  
-   Wenn Sie dem benutzerdefinierten Regelsatz eine bestimmte Regel hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Regel.  Wenn Sie die Regel aus dem Regelsatz entfernen möchten, deaktivieren Sie das zugehörige Kontrollkästchen.  
  
-   Wenn Sie die Aktion ändern möchten, die ausgeführt wird, wenn gegen eine Regel in einer Codeanalyse verstoßen wird, klicken Sie auf das Feld **Aktion** für die Regel, und wählen Sie dann einen der folgenden Werte aus:  
  
     **Warn** – erzeugt eine Warnung.  
  
     **Error**\- erzeugt einen Fehler.  
  
     **None** \- deaktiviert die Regel.  Diese Aktion ist mit der Aktion identisch, die beim Entfernen der Regel aus dem Regelsatz ausgeführt wird.  
  
## Ändern der Anzeige im Regelsatz\-Editor  
  
#### So gruppieren, filtern oder ändert Sie Felder auf der Symbolleiste des Regelsatz\-Editors  
  
-   Wenn Sie die Regeln in allen Gruppen erweitern möchten, klicken Sie auf **Alle erweitern**.  
  
-   Wenn Sie die Regeln in allen Gruppen reduzieren möchten, klicken Sie auf **Alle reduzieren.**  
  
-   Wenn Sie das Feld ändern möchten, anhand dessen Regeln gruppiert werden, wählen Sie das Feld in der Liste **Gruppieren nach** aus.  Wenn Sie die Regeln ohne Gruppierung anzeigen möchten, wählen Sie **\<Keine\>** aus.  
  
-   Wenn Sie in Regelspalten Felder hinzufügen oder entfernen möchten, klicken Sie auf **Spaltenoptionen**.  
  
-   Wenn Sie Regeln ausblenden möchten, die nicht für die aktuelle Projektmappe gelten, aktivieren Sie **Regeln ausblenden, die auf die aktuelle Projektmappe nicht zutreffen**.  
  
-   Wenn Sie zwischen dem Ein\- und Ausblenden von Regeln wechseln möchten, denen die Fehleraktion zugewiesen ist, klicken Sie auf **Regeln anzeigen, die Codeanalysefehler generieren können**.  
  
-   Wenn Sie zwischen dem Ein\- und Ausblenden von Regeln wechseln möchten, denen die Warnaktion zugewiesen ist, klicken Sie auf **Regeln anzeigen, die Codeanalysewarnungen generieren können**.  
  
-   Wenn Sie zwischen dem Ein\- und Ausblenden von Regeln wechseln möchten, denen explizit keine Aktion zugewiesen ist, klicken Sie auf **Nicht aktivierte Regeln anzeigen**.  
  
-   Wenn Sie dem aktuellen Regelsatz Microsoft\-Standardregelsätze hinzuzufügen oder aus diesem entfernen möchten, klicken Sie auf **Untergeordnete Regelsätze hinzufügen oder entfernen**.  
  
## Siehe auch  
 [Gewusst wie: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Codeanalyse\-Regelsatzreferenz](../code-quality/code-analysis-rule-set-reference.md)