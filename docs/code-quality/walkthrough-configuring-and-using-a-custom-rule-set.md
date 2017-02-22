---
title: "Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Codeanalyse, exemplarische Vorgehensweisen"
  - "Codeanalyse, Regelsätze"
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 40
caps.handback.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird erläutert, wie Codeanalysetools verwendet werden, die konfiguriert wurden, um in einer Klassenbibliothek einen benutzerdefinierten *Regelsatz* zu verwenden.  Sie können einen Regelsatz auswählen, der sich auf den Projekttyp bezieht, den Sie für die Projektmappe angegeben haben. Sie können auch andere Regelsätze auswählen, um eine bestimmte Anforderung zu erfüllen, z. B. das Überprüfen von Legacycode auf Probleme, die ohne Unterbrechung behoben werden können.  In beiden Fällen können Sie die Regelsätze an Ihre Projektanforderungen anpassen.  
  
 In dieser exemplarischen Vorgehensweise führen Sie die folgenden Schritte aus:  
  
-   Erstellen Sie eine Klassenbibliothek.  
  
-   Wählen Sie den Codeanalyse\-Regelsatz **Grundlegende Microsoft\-Regeln für Entwurfsrichtlinien** aus.  
  
-   Fügen Sie der Klasse den eigenen Code hinzu.  
  
-   Führen Sie die Codeanalyse aus.  
  
-   Passen Sie den Regelsatz an.  
  
-   Führen Sie die Codeanalyse aus und überprüfen Sie, wie sich der angepasste Regelsatz auswirkt.  
  
## Vorbereitungsmaßnahmen  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] oder [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## Verwenden von Regelsätzen zur Codeanalyse  
 Erstellen Sie zunächst eine einfache Klassenbibliothek.  
  
#### Erstellen einer Klassenbibliothek  
  
1.  Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** unter **Projekttypen** auf **Visual C\#**.  
  
3.  Wählen Sie unter **Visual C\#** die Option **Klassenbibliothek** aus.  
  
4.  Geben Sie im Textfeld **Name** "RuleSetSample" ein, und klicken Sie auf **OK**.  
  
 Anschließend wählen Sie den Regelsatz **Grundlegende Microsoft\-Regeln für Entwurfsrichtlinien** aus und speichern diesen im Projekt.  
  
#### Auswählen eines Codeanalyse\-Regelsatzes  
  
1.  Klicken Sie im Menü **Analyse** auf **Codeanalyse für RuleSetSample konfigurieren**.  
  
     Die Konfigurationseinstellungen für die Codeanalyse werden angezeigt.  
  
2.  Wählen Sie in der Dropdownliste **Diesen Regelsatz ausführen** die Option **Alle Microsoft\-Regeln** aus.  
  
     Weitere Informationen über die verfügbaren Regelsätze finden Sie unter [Codeanalyse\-Regelsatzreferenz](../code-quality/code-analysis-rule-set-reference.md).  
  
     Klicken Sie im Menü Datei auf **Ausgewählte Elemente speichern**, um die Projektdatei mit Informationen zum ausgewählten Regelsatz und dessen Einstellungen zu aktualisieren.  
  
    > [!TIP]
    >  In einer realen Situation sollten Sie zur Priorisierung der Probleme im Rahmen einer Codeanalyse mit dem Mindestregelsatz beginnen und zunächst die infrage kommenden Probleme beheben, bevor Sie inkrementell weitere Regeln oder Regelsätze hinzufügen, um zusätzliche Probleme zu suchen und zu beheben.  
  
 Im nächsten Schritt wird der Klassenbibliothek Code hinzugefügt, um Verstöße gegen die Codeanalyseregel CA1704 \("Bezeichner sollten korrekt geschrieben werden"\) zu veranschaulichen.  Weitere Informationen finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### Hinzufügen von eigenem Code  
  
-   Öffnen Sie im Projektmappen\-Explorer die Datei "Class1.cs", und ersetzen Sie den vorhandenen Code wie folgt:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace RuleSetSample  
    {  
        public class Class1  
        {  
            //The variable parameter names "a" and "b" will cause  
            //the warning CA 1704 Microsoft.Naming "Consider   
            //providing a more meaningful name" to fire  
            public int AddIntegers(int a, int b)  
            {  
  
                int sum = a + b;  
  
                return (sum);  
            }  
        }  
    }  
  
    ```  
  
 Jetzt können Sie die Codeanalyse für das RuleSetSample\-Projekt ausführen und nach Fehlern und Warnungen suchen, die im Fenster "Fehlerliste" angezeigt werden.  
  
#### Ausführen der Codeanalyse für das RuleSetSample\-Projekt  
  
1.  Klicken Sie im Menü **Analyse** auf **Codeanalyse für RuleSetSample ausführen**.  
  
2.  Klicken Sie im Fenster "Fehlerliste" auf **Warnungen** und dann auf die Spaltenüberschrift **Beschreibung**, um die Warnungen alphanumerisch zu sortieren.  
  
     In einer realen Anwendung würden Sie nun die relevanten Regelverstöße korrigieren oder entsprechende Regeln deaktivieren oder unterdrücken, wenn eine entsprechende Korrektur nicht infrage kommt.  Weitere Informationen finden Sie unter [Unterdrücken von Warnungen mithilfe des SuppressMessage\-Attributs](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3.  Beachten Sie die CA1704\-Warnungen.  Diese Regelverletzungen deuten darauf hin, dass Sie einen aussagekräftigeren Namen für die Parameter angeben sollten. Sie könnten das Problem im Code korrigieren, oder Sie können die Regel deaktivieren, wie nachfolgend erläutert.  
  
 Im nächsten Schritt wird der Regelsatz so angepasst, dass die CA1704\-Warnung \("Bezeichner sollten korrekt geschrieben werden"\) ausgeschlossen wird.  
  
#### Anpassen des Regelsatzes für das Projekt zum Deaktivieren einer bestimmten Regel  
  
1.  Klicken Sie im Menü **Analyse** auf **Codeanalyse für RuleSetSample konfigurieren**.  
  
2.  Vergewissern Sie sich in der Dropdownliste **Diesen Regelsatz ausführen**, dass immer noch der Regelsatz **Alle Microsoft\-Regeln** ausgewählt ist, und klicken Sie auf **Öffnen**.  Die Seite des Regelsatzes wird angezeigt.  
  
3.  Erweitern Sie den Kategorieknoten "Microsoft.Naming", und wählen Sie die CA1704\-Warnung aus.  
  
4.  Wählen Sie in der Spalte **Aktion** den Eintrag **Keine** aus. Dadurch wird verhindert, dass CA1704 als Warnung oder Fehler im Fenster "Fehlerliste" angezeigt wird.  
  
     Dies ist ein guter Zeitpunkt, sich mit den verschiedenen Symbolleistenschaltflächen und den Filteroptionen vertraut zu machen.  Beispielsweise können Sie die Dropdownliste **Gruppieren nach** verwenden, um die Suche nach einer bestimmten Regel oder einer Kategorie von Regeln zu vereinfachen.  Sie können auch die Schaltfläche **Deaktivierte Regeln ausblenden** in der Regelsatzseiten\-Symbolleiste verwenden, um alle Regeln in der Spalte **Aktion** anzuzeigen oder auszublenden, die auf **Keine** festgelegt wurden.  Dies kann hilfreich sein, wenn Sie nach allen deaktivierten Regeln suchen und überprüfen möchten, ob diese Einstellungen beibehalten werden sollen.  
  
5.  Klicken Sie im Menü Ansicht auf Eigenschaftenfenster.  Geben Sie im Eigenschaftenfenster im Feld Name den Namen **My Custom Rule Set** ein.  Dadurch wird der Anzeigename des neuen Regelsatzes in der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-IDE geändert.  
  
6.  Klicken Sie im Menü **Datei** auf **Alle Microsoft\-Regeln.ruleset speichern**, um den benutzerdefinierten Regelsatz zu speichern.  Navigieren Sie zum Stammordner des Projekts.  Geben Sie im Feld **Dateiname** den Namen "MyCustomRuleSet" ein.  Der benutzerdefinierte Regelsatz kann jetzt ausgewählt und im Projekt verwendet werden.  
  
 Nachdem Sie den neuen Regelsatz erstellt haben, müssen Sie die Projekteinstellungen konfigurieren, um anzugeben, dass Sie den neuen Regelsatz verwenden möchten.  
  
#### Angeben des neuen Regelsatzes zur Verwendung im Projekt  
  
1.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** aus.  
  
2.  Klicken Sie auf der Registerkarte **Eigenschaften** auf **Codeanalyse**.  
  
     In der Dropdownliste **Diesen Regelsatz ausführen** klicken Sie auf **\<Durchsuchen Sie.\>**.  Navigieren Sie zum Stammordner des Codeprojekts, und wählen Sie "MyCustomRuleSet.ruleset" aus.  Dies ist der neue Regelsatz, den Sie in der vorangehenden Prozedur erstellt haben.  
  
3.  Klicken Sie im Menü **Datei** auf **Speichern**, um die Projektkonfiguration zu speichern.  Der benutzerdefinierte Regelsatz kann jetzt mit dem Projekt verwendet werden.  
  
 Abschließend führen Sie die Codeanalyse erneut aus und verwenden dazu den Regelsatz "MyCustomRuleSet".  Beachten Sie, dass der Leistungsregelverstoß CA1704 nicht im Fenster "Fehlerliste" angezeigt wird.  
  
#### Erneutes Ausführen der Codeanalyse im RuleSetSample\-Projekt  
  
1.  Klicken Sie im Menü **Analyse** auf **Codeanalyse für RuleSetSample ausführen**.  
  
2.  Beachten Sie, dass die CA1704\-Warnung für die Regel "Bezeichner sollten korrekt geschrieben werden" im Fenster "Fehlerliste" nicht mehr angezeigt wird, wenn Sie auf **Warnungen** klicken.  
  
## Siehe auch  
 [Gewusst wie: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Codeanalyse\-Regelsatzreferenz](../code-quality/code-analysis-rule-set-reference.md)