---
title: 'Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8239afd1cf4e8c0a5e702f2b0e4ed64408cada09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645740"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie Code Analysetools verwenden, die für die Verwendung eines angepassten *Regelsatzes* für eine Klassenbibliothek konfiguriert wurden. Sie können einen Regelsatz auswählen, der sich auf den Projekttyp bezieht, den Sie für die Projekt Mappe angegeben haben, oder Sie können alternative Regelsätze auswählen, um einen bestimmten Bedarf zu erfüllen, z. b. das Scannen von Legacy Code auf Probleme, die auf eine nicht unterbrechende Weise korrigiert werden In beiden Fällen können die Regelsätze auch angepasst werden, um Sie an die Projektanforderungen anzupassen.

 In dieser exemplarischen Vorgehensweise werden die folgenden Prozesse schrittweise durchlaufen:

- Erstellen Sie eine Klassenbibliothek.

- Wählen Sie den Regelsatz Regeln für die Code Analyse von **Microsoft Basic** aus.

- Fügen Sie der-Klasse ihren eigenen Code hinzu.

- Ausführen der Code Analyse.

- Passen Sie den Regelsatz an.

- Ausführen der Code Analyse und Anzeigen der Funktionsweise des Regelsatz-Anpassungs Verhaltens

## <a name="prerequisites"></a>Erforderliche Voraussetzungen

- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]oder [!INCLUDE[vsPro](../includes/vspro-md.md)]

## <a name="using-rule-sets-with-code-analysis"></a>Verwenden von Regelsätzen mit der Code Analyse
 Erstellen Sie zunächst eine einfache Klassenbibliothek.

#### <a name="create-a-class-library"></a>Erstellen einer Klassenbibliothek

1. Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Projekt**.

2. Klicken Sie im Dialogfeld **Neues Projekt** unter **Projekttypen**auf **Visualisierung C#** .

3. Wählen Sie unter **C#Visual**die Option **Klassenbibliothek**aus.

4. Geben Sie im Textfeld **Name den Namen** **RuleSetSample** ein, und klicken Sie dann auf **OK**.

   Wählen Sie als nächstes den Regelsatz **Microsoft Basic-Entwurfs Richtlinien Regeln** aus, und speichern Sie ihn mit Ihrem Projekt.

#### <a name="select-a-code-analysis-rule-set"></a>Code Analyse-Regelsatz auswählen

1. Klicken Sie im Menü **analysieren** auf **Code Analyse für RuleSetSample konfigurieren**.

    Die Konfigurationseinstellungen für die Code Analyse werden angezeigt.

2. Wählen Sie in der Dropdown Liste **diesen Regelsatz ausführen** die Option **Microsoft alle Regeln**aus.

    Weitere Informationen zu den verfügbaren Regelsätzen finden Sie unter [Referenz zur Code Analyse-Regel Satz](../code-quality/code-analysis-rule-set-reference.md).

    Klicken Sie im Menü Datei auf **ausgewählte Elemente speichern** , um die Projektdatei mit Informationen über den ausgewählten Regelsatz und seine Einstellungen zu aktualisieren.

   > [!TIP]
   > In einer realen Situation empfiehlt es sich, für die Priorisierung von Problemen, die Sie mit der Code Analyse als Ziel verwenden möchten, mit dem Regel Satz für **Empfohlene Regeln** zu beginnen und die gewünschten Probleme zu beheben und dann inkrementell weitere Regeln oder Regelsätze hinzuzufügen. Suchen und beheben Sie die zusätzlichen Probleme.

   Als Nächstes fügen Sie der-Klassenbibliothek Code hinzu, der verwendet wird, um Verstöße gegen die CA1704 "Bezeichner sollten korrekt geschrieben werden" zu veranschaulichen. Weitere Informationen finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

#### <a name="add-your-own-code"></a>Eigenen Code hinzufügen

- Öffnen Sie in Projektmappen-Explorer die Datei Class1.cs, und ersetzen Sie den vorhandenen Code durch Folgendes:

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

  Nun können Sie die Code Analyse für das RuleSetSample-Projekt ausführen und nach Fehlern und Warnungen suchen, die im Fehlerliste Fenster generiert wurden.

#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Ausführen der Code Analyse für das RuleSetSample-Projekt

1. Klicken Sie im Menü **analysieren** **auf Code Analyse für RuleSetSample ausführen**.

2. Klicken Sie im Fenster Fehlerliste auf **Warnungen** , und klicken Sie dann auf den **Beschreibungs** Spaltenheader, um die Warnungen alphanumerisch zu sortieren.

    In einer realen Anwendung würden Sie alle Regel Verletzungen beheben, die zu diesem Zeitpunkt behoben werden müssen, oder Sie können eine Regel deaktivieren oder unterdrücken, wenn Sie festgestellt haben, dass Sie nicht behoben werden sollte. Weitere Informationen finden Sie unter [Suppress Warnings By Using the SuppressMessage Attribute (Unterdrücken von Warnungen mithilfe des SuppressMessage-Attributs)](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

3. Beachten Sie die CA1704-Warnungen. Diese Verstöße gegen diese Regel weisen darauf hin, dass Sie einen aussagekräftigeren Namen für die Parameter angeben sollten. Sie können das Problem in Ihrem Code beheben, oder Sie können die Regel deaktivieren, wie im nächsten Verfahren erläutert.

   Anschließend passen Sie den Regelsatz so an, dass die CA1704-Warnung, "Bezeichner sollten korrekt geschrieben werden", ausgeschlossen wird.

#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Anpassen des Regelsatzes für das Projekt, um eine bestimmte Regel zu deaktivieren

1. Klicken Sie im Menü **analysieren** auf **Code Analyse für RuleSetSample konfigurieren**.

2. Überprüfen Sie in der Dropdown Liste **diesen Regelsatz ausführen** , ob der Regelsatz **Microsoft alle Regeln** weiterhin hervorgehoben ist, und klicken Sie dann auf **Öffnen**. Die Seite Regelsatz wird angezeigt.

3. Erweitern Sie den Knoten Microsoft. Naming Category, und wählen Sie dann die CA1704-Warnung aus.

4. Wählen Sie unter der Spalte **Aktion** die Option **keine aus.** Dadurch wird verhindert, dass CA1704 im Fenster Fehlerliste als Warnung oder Fehler angezeigt wird.

    Nun wäre es ein guter Zeitpunkt, mit den verschiedenen Symbolleisten-Schaltflächen und Filteroptionen zu experimentieren, um sich mit Ihnen vertraut zu machen. Beispielsweise können Sie mithilfe der Dropdown Liste **Gruppieren nach** eine bestimmte Regel oder eine bestimmte Kategorie von Regeln suchen. Ein weiteres Beispiel ist, dass Sie die Schaltfläche **Deaktivierte Regeln ausblenden** auf der Symbolleiste Regel Satz Seiten verwenden können, um alle Regeln auszublenden oder anzuzeigen, bei denen die Spalte **Aktion** auf **keine**festgelegt ist. Dies kann hilfreich sein, wenn Sie nach Regeln suchen möchten, die Sie deaktiviert haben, um zu überprüfen, ob Sie Sie noch deaktivieren möchten.

5. Klicken Sie im Menü Ansicht auf Eigenschaften Fenster. Geben Sie im Eigenschaften Tool Fenster im Feld Name den **benutzerdefinierten Regelsatz** ein. Dadurch wird der Anzeige Name des neuen Regelsatzes in der [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE geändert.

6. Klicken Sie im Menü **Datei** auf **Microsoft all rules. RuleSet speichern** , um den benutzerdefinierten Regelsatz zu speichern. Navigieren Sie zum Stamm Ordner des Projekts. Geben Sie im Textfeld **Dateiname den Namen** **MyCustomRuleSet**ein. Der benutzerdefinierte Regelsatz kann jetzt für die Verwendung mit dem Projekt ausgewählt werden.

   Nachdem Sie den neuen Regelsatz erstellt haben, müssen Sie die Projekteinstellungen jetzt konfigurieren, um anzugeben, dass Sie den neuen Regelsatz mit dem Regelsatz verwenden möchten.

#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Geben Sie den neuen Regelsatz für die Verwendung mit Ihrem Projekt an.

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**aus.

2. Klicken Sie auf der Registerkarte **Eigenschaften** auf **Code Analyse**.

    Klicken Sie in der Dropdown Liste **diesen Regelsatz ausführen** auf **\<Browse.. >** . Navigieren Sie zum Stamm Ordner des Code Projekts, und wählen Sie dann **MyCustomRuleSet. RuleSet**aus. Dies ist der neue Regelsatz, den Sie im vorherigen Verfahren erstellt haben.

3. Klicken Sie im Menü **Datei** auf **Speichern** , um die Projekt Konfiguration zu speichern. Der benutzerdefinierte Regelsatz kann nun mit dem Projekt verwendet werden.

   Schließlich führen Sie die Code Analyse erneut aus, indem Sie Ihren MyCustomRuleSet-Regelsatz verwenden. Beachten Sie, dass im Fehlerliste Fenster die Verletzung der Leistungs Regel CA1704 nicht angezeigt wird.

#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Ausführen der Code Analyse für das RuleSetSample-Projekt zum zweiten Mal

1. Klicken Sie im Menü **analysieren** **auf Code Analyse für RuleSetSample ausführen**.

2. Beachten Sie, dass beim Klicken auf **Warnungen**im Fehlerliste Fenster die Regel "CA1704 Warning" (Bezeichner sollten korrekt geschrieben werden) nicht mehr angezeigt wird.

## <a name="see-also"></a>Siehe auch
 Gewusst [wie: Konfigurieren der Code Analyse für einen](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [Code Analyse-Regelsatz Verweis](../code-quality/code-analysis-rule-set-reference.md) für ein verwaltetes Code Projekt
