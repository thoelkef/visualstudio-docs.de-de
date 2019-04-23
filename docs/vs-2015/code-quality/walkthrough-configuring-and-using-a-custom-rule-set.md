---
title: 'Exemplarische Vorgehensweise: Konfigurieren und verwenden einen benutzerdefinierten Regelsatz | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: da7b1f1bda7fac222d0d47c6bf2a15eaf3a8396f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052063"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise veranschaulicht, wie Code Analysetools verwenden, die einen angepassten konfiguriert wurden *Regelsatz* auf eine Klassenbibliothek. Sie können einen Regelsatz auswählen, der bezieht sich auf den Projekttyp, den Sie für Ihre Lösung angegeben haben, oder Sie können auswählen, dass alternative von Regelsätzen zum Erfüllen der benötigen z.B. die Überprüfung von legacy-Code für Probleme, die in eine nicht unterbrechende Weise behoben werden können. In beiden Fällen können die Regelsätze auch angepasst werden, um sie optimieren, die Anforderungen Ihres Projekts.  
  
 In dieser exemplarischen Vorgehensweise werden Sie diese Prozesse durchlaufen:  
  
- Erstellen Sie eine Klassenbibliothek.  
  
- Wählen Sie die **grundlegende Microsoft-Regeln für Entwurfsrichtlinien** Codeanalyse-Regelsatz.  
  
- Fügen Sie Ihren eigenen Code zur Klasse hinzu.  
  
- Codeanalyse ausführen.  
  
- Passen Sie den Regelsatz an.  
  
- Führen Sie der Codeanalyse aus aus, und sehen Sie, wie den Regelsatz Anpassung Verhalten funktioniert.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]oder [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="using-rule-sets-with-code-analysis"></a>Mit Regel legt fest, mit der Codeanalyse  
 Erstellen Sie zunächst eine einfache Klassenbibliothek.  
  
#### <a name="create-a-class-library"></a>Erstellen einer Klassenbibliothek  
  
1. Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Projekt**.  
  
2. In der **neues Projekt** Dialogfeld **Projekttypen**, klicken Sie auf **Visual C#-**.  
  
3. Klicken Sie unter **Visual C#-** Option **Klassenbibliothek**.  
  
4. In der **Namen** Textfeld **RuleSetSample** , und klicken Sie dann auf **OK**.  
  
   Wählen Sie als Nächstes die **grundlegende Microsoft-Regeln für Entwurfsrichtlinien** Regelsatz aus, und speichern Sie ihn mit Ihrem Projekt.  
  
#### <a name="select-a-code-analysis-rule-set"></a>Wählen Sie einen Regelsatz für Codeanalyse  
  
1. Auf der **analysieren** Menü klicken Sie auf **Konfigurieren der Codeanalyse für RuleSetSample**.  
  
    Die Konfigurationseinstellungen für die Codeanalyse werden angezeigt.  
  
2. In der **diesen Regelsatz ausführen** Dropdown-Liste **alle Microsoft-Regeln**.  
  
    Weitere Informationen zu den verfügbaren Regelsätze, finden Sie unter [Codeanalyse-Regelsätze ressourcensatzverweis](../code-quality/code-analysis-rule-set-reference.md).  
  
    Klicken Sie auf im Menü Datei auf **ausgewählte Elemente speichern** können Sie die Projektdatei mit Informationen zu den Regelsatz aus, die Sie ausgewählt und dessen Einstellungen.  
  
   > [!TIP]
   >  In einer realen Situation wird empfohlen, für die Priorisierung der Probleme, die Sie mit der Codeanalyse möchten verwenden für den Einstieg die **Mindestregeln** Regelsatz und beheben Sie die gewünschten Probleme und klicken Sie dann inkrementell hinzufügen Weitere Regeln oder Regelsätze legt fest, zu finden und beheben Sie die zusätzliche Probleme.  
  
   Als Nächstes werden Sie Code hinzufügen, auf die Klassenbibliothek, die verwendet wird, um Verstöße gegen die CA1704 veranschaulichen "Bezeichner sollten korrekt geschrieben werden" Codeanalyseregel. Weitere Informationen finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### <a name="add-your-own-code"></a>Fügen Sie Ihren eigenen code  
  
- Klicken Sie im Projektmappen-Explorer öffnen Sie die Datei "Class1.cs", und Ersetzen Sie den vorhandenen Code durch Folgendes:  
  
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
  
  Jetzt können Sie Codeanalyse für das Projekt RuleSetSample ausführen und suchen Sie nach Fehlern und Warnungen, die in das Fenster "Fehlerliste" generiert.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Ausführen der Codeanalyse für das Projekt RuleSetSample  
  
1. Auf der **analysieren** Menü klicken Sie auf **Codeanalyse für RuleSetSample ausführen**.  
  
2. Klicken Sie im Fenster "Fehlerliste", auf **Warnungen** , und klicken Sie dann auf die **Beschreibung** Spaltenheader, um die Warnungen sortieren alphanumerisch.  
  
    In einer echten Anwendung würden Sie beheben Sie alle Regelverstöße, korrigieren sich an diesem Punkt oder optional deaktivieren oder eine Regel unterdrücken, wenn Sie ermittelt, dass nicht zu beheben. Weitere Informationen finden Sie unter [Suppress Warnings By Using the SuppressMessage Attribute (Unterdrücken von Warnungen mithilfe des SuppressMessage-Attributs)](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3. Beachten Sie, dass die CA1704 Warnungen. Diese Verletzungen dieser Regel anzugeben, dass Sie "sollten einen aussagekräftigeren Namen für die Parameter." Konnte, beheben Sie das Problem in Ihrem Code aus, oder Sie können die Regel deaktivieren, wie in der nächsten Prozedur beschrieben.  
  
   Als Nächstes passen Sie den Regelsatz, um die Warnung CA1704 auszuschließen, "Bezeichner sollten korrekt geschrieben werden".  
  
#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Anpassen der Regel legen Sie für das Projekt für eine bestimmte Regel deaktivieren  
  
1. Auf der **analysieren** Menü klicken Sie auf **Konfigurieren der Codeanalyse für RuleSetSample**.  
  
2. In der **diesen Regelsatz ausführen** Dropdown-Liste, überprüfen Sie, ob die **alle Microsoft-Regeln** Regel Satz wird aber dennoch hervorgehoben, und klicken Sie dann auf **öffnen**. Die Seite des Regelsatzes wird angezeigt.  
  
3. Erweitern Sie den Kategorieknoten Microsoft.Naming, und wählen Sie dann auf die Warnung CA1704.  
  
4. Unter den **Aktion** Spalte **None.** Dadurch wird verhindert, dass CA1704 als Warnung oder Fehler in das Fenster "Fehlerliste" angezeigt.  
  
    Nun wäre ein guter Zeitpunkt zum Experimentieren mit verschiedenen Symbolleisten-Schaltflächen und Filteroptionen mit ihnen vertraut. Beispielsweise können Sie die **Group By** Dropdown-Liste als Hilfe bei der Suche nach einer bestimmten Regel oder einer Kategorie von Regeln. Ein weiteres Beispiel ist, dass Sie verwenden können, die **deaktivierte Regeln ausblenden** -Schaltfläche in der Regel-Symbolleiste oder Ausblenden aller Regeln mit den **Aktion** Spaltensatz zu **keine**. Dies kann nützlich sein, wenn keine Regeln gesucht werden, die Sie deaktiviert haben, um sicherzustellen, dass trotzdem sollen sie deaktiviert werden sollen.  
  
5. Klicken Sie auf das Menü "Ansicht" Fenster "Eigenschaften" aus. Typ **Meine benutzerdefinierten Regelsatz** im Feld Name, der das Toolfenster "Eigenschaften". Dies ändert den Anzeigenamen der neuen Regel legen Sie in der [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE.  
  
6. Auf der **Datei** Menü klicken Sie auf **alle Microsoft-Regeln.ruleSet** legen Sie die benutzerdefinierte Regel zu speichern. Navigieren Sie in den Stammordner des Projekts. In **Dateinamen** Textfeld **"MyCustomRuleSet"**. Der benutzerdefinierte Regelsatz kann nun für die Verwendung mit Ihrem Projekt ausgewählt werden.  
  
   Mit der neue Regelsatz, der erstellt wird müssen Sie jetzt so konfigurieren Sie die projekteinstellungen, um anzugeben, dass Sie die neue Regel festlegen, damit verwenden möchten.  
  
#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Geben Sie den neuen Regelsatz für die Verwendung mit Ihrem Projekt  
  
1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Projekts, und wählen Sie dann **Eigenschaften**.  
  
2. In der **Eigenschaften** auf **Codeanalyse**.  
  
    In der **diesen Regelsatz ausführen** Dropdown-Liste, klicken Sie auf  **\<durchsuchen... >**. Navigieren Sie in den Stammordner des Codeprojekts aus, und wählen Sie dann **"MyCustomRuleSet.RuleSet" aus**. Dies ist der neue Regelsatz, den Sie im vorherigen Verfahren erstellt haben.  
  
3. Auf der **Datei** Menü klicken Sie auf **speichern** auf die Projektkonfiguration zu speichern. Der benutzerdefinierte Regelsatz kann jetzt mit Ihrem Projekt verwendet werden.  
  
   Abschließend führen Sie die Codeanalyse erneut mit der Regelsatz "MyCustomRuleSet". Beachten Sie, dass es sich bei den CA1704 Leistung Regelverstoß nicht in das Fenster "Fehlerliste" angezeigt wird.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Codeanalyse für das Projekt RuleSetSample zum zweiten Mal ausführen.  
  
1. Auf der **analysieren** Menü klicken Sie auf **Codeanalyse für RuleSetSample ausführen**.  
  
2. Im Fenster "Fehlerliste", beachten Sie, dass wenn Sie auf **Warnungen**, nicht mehr die CA1704 Warnung Verletzungen für die Regel "Bezeichner sollten korrekt geschrieben werden." angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Codeanalyse-Regelsatzreferenz](../code-quality/code-analysis-rule-set-reference.md)
