---
title: 'Exemplarische Vorgehensweise: Konfigurieren und verwenden einen benutzerdefinierten Regelsatz | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b9a7046930d12ebb940820eb25c4563b0a3213e3
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes

In dieser exemplarischen Vorgehensweise wird gezeigt, wie mit Codeanalysetools, die konfiguriert wurden, um einen angepassten *Regelsatz* auf eine Klassenbibliothek. Sie können einen Regelsatz auswählen, der bezieht sich auf den Projekttyp, den Sie für die Projektmappe angegeben haben, oder Sie können auswählen, dass alternative Regelsätzen erfüllt eine bestimmte Anforderung z. B. Scans Legacycode für Probleme, die auf eine nicht unterbrechende Weise behoben werden können. In beiden Fällen können die Regelsätze auch angepasst werden, um sie an Ihre projektanforderungen eine Feinabstimmung durchzuführen.  
  
In dieser exemplarischen Vorgehensweise werden Sie diese Prozesse durchlaufen:  
  
-   Erstellen Sie eine Klassenbibliothek.  
  
-   Wählen Sie die **grundlegende Microsoft-Regeln für Entwurfsrichtlinien** Codeanalyse-Regelsatz.  
  
-   Fügen Sie Ihren eigenen Code für die Klasse.  
  
-   Codeanalyse ausführen.  
  
-   Anpassen des Regelsatzes.  
  
-   Ausführen der Codeanalyse und angezeigt wie die Regel Anpassung Verhalten funktioniert festgelegt ist.  
  
## <a name="using-rule-sets-with-code-analysis"></a>Verwenden die Regel legt fest, mit der Codeanalyse

Erstellen Sie zunächst eine einfache Klassenbibliothek.  
  
### <a name="create-a-class-library"></a>Erstellen einer Klassenbibliothek  
  
1.  Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld unter **Projekttypen**, klicken Sie auf **Visual C#-**.  
  
3.  Klicken Sie unter **Visual C#-**Option **-Klassenbibliothek**.  
  
4.  In der **Namen** Textfeld **RuleSetSample** , und klicken Sie dann auf **OK**.  
  
 Wählen Sie als Nächstes die **grundlegende Microsoft-Regeln für Entwurfsrichtlinien** Regelsatz aus, und speichern Sie sie in Ihrem Projekt.  
  
### <a name="select-a-code-analysis-rule-set"></a>Wählen Sie einen Codeanalyse-Regelsatz  
  
1.  Auf der **analysieren** Menü klicken Sie auf **Konfigurieren der Codeanalyse für RuleSetSample**.  
  
     Die Konfigurationseinstellungen für die Codeanalyse werden angezeigt.  
  
2.  In der **diesen Regelsatz ausführen** Dropdown-Liste **Microsoft alle Regeln**.  
  
     Weitere Informationen zu den verfügbaren Regelsätzen finden Sie unter [Code Analysis-regelsatzreferenz](../code-quality/code-analysis-rule-set-reference.md).  
  
     Klicken Sie auf das Menü Datei auf **ausgewählte Elemente speichern** können Sie die Projektdatei mit Informationen zu den Regelsatz, den Sie ausgewählt und dessen Einstellungen.  
  
    > [!TIP]
    >  In einer realen Situation wird empfohlen, für die Priorisierung von welche Probleme, Sie mit der Codeanalyse möchten, verwenden zum Einstieg die **Mindestregeln** Regelsatz und gewünschten Probleme behoben werden, und klicken Sie dann inkrementell hinzufügen Weitere Regeln oder die Regel wird zum Suchen und beheben die Probleme.  
  
 Anschließend fügen Sie Code, der verwendet wird, um Verstöße gegen die CA1704 veranschaulichen-Klassenbibliothek "Bezeichner sollten korrekt geschrieben" Codeanalyseregel. Weitere Informationen finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
### <a name="add-your-own-code"></a>Fügen Sie Ihren eigenen code  
  
-   Öffnen Sie im Projektmappen-Explorer die Datei "Class1.cs", und Ersetzen Sie den vorhandenen Code durch Folgendes:  
  
    ```csharp
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
  
Jetzt können Sie führen die Codeanalyse für das RuleSetSample-Projekt, und suchen Sie nach Fehler und Warnungen im Fenster "Fehlerliste" generiert.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Ausführen der Codeanalyse für das RuleSetSample-Projekt  
  
1.  Auf der **analysieren** Menü klicken Sie auf **Ausführen der Codeanalyse für RuleSetSample**.  
  
2.  Klicken Sie im Fenster Fehlerliste auf **Warnungen** , und klicken Sie dann auf die **Beschreibung** Spaltenheader, um die Warnungen sortieren alphanumerisch.  
  
     In einer realen Anwendung würde Sie korrigieren und zu diesem Zeitpunkt Regelverstöße beheben oder optional deaktivieren oder eine Regel zu unterdrücken, sofern Sie ermittelt, dass sie nicht Folgendes zu korrigieren und war. Weitere Informationen finden Sie unter [unterdrücken Sie Warnungen mithilfe des SuppressMessage-Attributs](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3.  Beachten Sie die CA1704 Warnungen aus. Diese Verletzungen dieser Regel weisen darauf hin, dass Sie "sollten einen aussagekräftigeren Namen für die Parameter." Konnte, beheben das Problem in Ihrem Code aus, oder Sie können die Regel deaktivieren, wie in der nächsten Prozedur beschrieben.  
  
 Als Nächstes passen Sie den Regelsatz, um die Warnung CA1704 auszuschließen, "Bezeichner sollten korrekt geschrieben werden".  
  
### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Anpassen des Regelsatzes für das Projekt in eine bestimmte Regel deaktivieren  
  
1.  Auf der **analysieren** Menü klicken Sie auf **Konfigurieren der Codeanalyse für RuleSetSample**.  
  
2.  In der **diesen Regelsatz ausführen** Dropdown-Liste, überprüfen Sie, ob die **Microsoft alle Regeln** Regel Satz markiert ist, und klicken Sie dann auf **öffnen**. Die Seite des Regelsatzes wird angezeigt.  
  
3.  Erweitern Sie den Kategorieknoten Microsoft.Naming, und wählen Sie dann die CA1704-Warnung.  
  
4.  Klicken Sie unter der **Aktion** Spalte **None.** Dadurch wird verhindert, dass CA1704 als Warnung oder Fehler im Fenster "Fehlerliste" angezeigt.  
  
     Jetzt ist ein guter Zeitpunkt zum Experimentieren mit verschiedenen Schaltflächen der Symbolleiste und Filteroptionen, mit diesen vertraut machen. Beispielsweise können Sie die **Group By** Dropdown-Liste als Hilfe bei der Suche nach einer bestimmten Regel oder eine Kategorie von Regeln. Ein weiteres Beispiel ist die Verwendung der **deaktivierte Regeln ausblenden** Schaltfläche in der Regel Symbolleiste auszublenden oder anzuzeigen alle Regeln mit der **Aktion** Spaltensatz zu **keine**. Dies kann nützlich sein, wenn für alle Regeln zu durchsuchen, in denen Sie deaktiviert haben, um sicherzustellen, dass trotzdem sollen sie deaktiviert werden sollen.  
  
5.  Klicken Sie im Menü Ansicht auf Eigenschaftenfenster. Typ **Meine benutzerdefinierten Regelsatz** im Feld "Name" im Eigenschaftenfenster für das Tool. Dies ändert den Anzeigenamen des neuen Regelsatzes der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IDE.  
  
6.  Auf der **Datei** Menü klicken Sie auf **alle Microsoft-Regeln.ruleSet** legen Sie die benutzerdefinierte Regel zu speichern. Navigieren Sie zum Stammordner des Projekts. In **der Dateiname** Textfeld **"MyCustomRuleSet"**. Der benutzerdefinierte Regelsatz kann jetzt für die Verwendung mit Ihrem Projekt ausgewählt werden.  
  
Mit Ihrer neuen Regelsatz, der erstellt wird müssen Sie jetzt so konfigurieren Sie die projekteinstellungen, um anzugeben, dass die neue Regel, die mit ihm festgelegt werden soll.  
  
### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Geben Sie den neuen Regelsatz für die Verwendung mit Ihrem Projekt  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste des Projekts, und wählen Sie dann **Eigenschaften**.  
  
2.  In der **Eigenschaften** auf **Codeanalyse**.  
  
     In der **diesen Regelsatz ausführen** Dropdown-Liste, klicken Sie auf  **\<durchsuchen... >**. Navigieren Sie zum Stammordner des Codeprojekts, und wählen Sie dann **"MyCustomRuleSet.RuleSet" aus**. Dies ist der neue Regelsatz, den Sie im vorherigen Verfahren erstellt haben.  
  
3.  Auf der **Datei** Menü klicken Sie auf **speichern** die Projektkonfiguration zu speichern. Der benutzerdefinierte Regelsatz kann jetzt mit Ihrem Projekt verwendet werden.  
  
 Abschließend führen Sie die Codeanalyse erneut mit Ihrer Regelsatz "MyCustomRuleSet". Beachten Sie, dass das Fenster "Fehlerliste" Verstoß gegen eine Codeanalyseregel die CA1704 Leistung nicht angezeigt wird.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Ausführen der Codeanalyse für das Projekt RuleSetSample zum zweiten Mal  
  
1.  Auf der **analysieren** Menü klicken Sie auf **Ausführen der Codeanalyse für RuleSetSample**.  
  
2.  Im Fenster Fehlerliste Beachten Sie, dass wenn Sie auf **Warnungen**, nicht mehr die CA1704 Warnung Verstöße für die Regel "Bezeichner sollten korrekt geschrieben werden" angezeigt.  
  
## <a name="see-also"></a>Siehe auch

[Vorgehensweise: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
[Codeanalyse-Regelsatzreferenz](../code-quality/code-analysis-rule-set-reference.md)