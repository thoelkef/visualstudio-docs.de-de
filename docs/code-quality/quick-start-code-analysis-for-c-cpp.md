---
title: "Schnellstart: Codeanalyse f&#252;r C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "C/C++-Codeanalyse"
  - "Codeanalyse, C/C++"
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Schnellstart: Codeanalyse f&#252;r C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Qualität Ihrer Anwendung verbessern, indem Codeanalysen für C oder C\+\+\-Code regelmäßig ausgeführt werden.  Damit können Sie allgemeine Probleme, Verstöße gegen guten Programmierstil oder Fehler, die nur schwer durch Tests ermittelt werden, finden.  Codeanalysewarnungen unterscheiden sich von Compilerfehler und \-Warnungen, da die Codeanalyse nach bestimmten Codeschemata sucht, die gültig sind, jedoch weiterhin für Sie oder andere Personen, die den Code verwenden, Probleme verursachen können.  
  
## In diesem Thema  
  
-   [Konfigurieren von Regelsätzen für ein Projekt](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
-   [Codeanalyse ausführen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
-   [Analysieren und Auflösen von Codeanalysewarnungen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
-   [Unterdrücken von Codeanalysewarnungen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
-   [Erstellen von Arbeitsaufgaben für Codeanalysewarnungen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
-   [Suchen und Filtern der Ergebnisse der Codeanalyse](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
##  <a name="BKMK_ConfigureRuleSets"></a> Konfigurieren von Regelsätzen für ein Projekt  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Projektnamen und wählen Sie **Eigenschaften** aus.  
  
2.  Die folgenden Schritte sind optional:  
  
    1.  Wählen Sie in den Listen **Konfiguration** und **Plattform** die Buildkonfiguration und die Zielplattform.  
  
    2.  Standardmäßig meldet die Codeanalyse keine Warnungen zu Code, der automatisch von Tools von Drittanbietern generiert wird.  Um Warnungen zu generiertem Code anzuzeigen, deaktivieren Sie das Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken**.  
  
        > [!NOTE]
        >  Allerdings werden durch diese Option keine Codeanalysefehler und \-warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten.  Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.  
  
3.  Um die Codeanalyse immer auszuführen, wenn das Projekt mit der ausgewählten Konfiguration erstellt wird, aktivieren Sie das Kontrollkästchen für **Codeanalyse für C\/C\+\+ für Build aktivieren** .  Sie können die Codeanalyse auch manuell ausführen, indem Sie das Menü **Analysieren** öffnen und **Codeanalyse ausführen***Projektname* wählen.  
  
4.  Führen Sie für die Liste **Diesen Regelsatz ausführen** einen der folgenden Schritte aus:  
  
    -   Wählen Sie den Regelsatz, den Sie verwenden möchten.  
  
    -   Wählen Sie **\<Durchsuchen...\>**, um einen vorhandenen benutzerdefinierten Regelsatz anzugeben, der nicht in der Liste aufgeführt ist.  
  
    -   Definieren Sie einen benutzerdefinierten Regelsatz.  
  
         Weitere Informationen finden Sie unter dem Link zum [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### Standard\-C\/C\+\+\-Regelsätze  
 Visual Studio enthält zwei Standardregelsätze für systemeigenen Code:  
  
|Regelsatz|Beschreibung|  
|---------------|------------------|  
|Von Microsoft empfohlene Mindestregeln für eigene Projekte|Dieser Regelsatz zielt auf die kritischsten Probleme in Ihrem systemeigenen Code ab, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürzen.  Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre eigenen Projekte erstellen.|  
|Von Microsoft empfohlene Regeln für eigene Projekte|Dieser Regelsatz umfasst eine Vielzahl von Problemen.  Sie enthält alle Regeln in den von Microsoft empfohlenen Mindestregeln für eigene Projekte|  
  
##  <a name="BKMK_Run"></a> Codeanalyse ausführen  
 Auf der Codeanalyseseite von den Eigenschaftenseiten des Projekts können Sie die Codeanalyse so konfigurieren, dass Sie bei jedem Erstellen des Projekts ausgeführt wird.  Sie können die Codeanalyse auch manuell ausführen.  
  
 Zum Ausführen der Codeanalyse in einer Projektmappe:  
  
-   Im **Build** Menü wählen Sie **Ausführen der Codeanalyse für Projektmappe**.  
  
 Zum Ausführen der Codeanalyse in einem Projekt:  
  
-   Wählen Sie im Projektmappen\-Explorer den Namen des Projektes aus.  
  
-   Im **Build** Menü wählen Sie **Ausführen der Codeanalyse für** *Projektname*.  
  
 Das Projekt oder die Projektmappe wird kompiliert und Codeanalyse wird ausgeführt.  Ergebnisse werden im Fenster "Codeanalyse" angezeigt.  
  
##  <a name="BKMK_Analyze"></a> Analysieren und Auflösen von Codeanalysewarnungen  
 Um eine bestimmte Warnung zu analysieren, wählen Sie den Titel der Warnung im Fenster "Codeanalyse" aus.  Die Warnung wird erweitert, um weitere Informationen zu diesem Problem anzuzeigen.  Wenn möglich, zeigt die Codeanalyse die Zeilennummern und Analyselogik, die zu der Warnung geführt hat.  Ausführliche Informationen zur Warnung, einschließlich der möglichen Lösungen für das Problem, wählen Sie die Warnungs\-Id, um das Hilfethema für diese Meldung in der MSND Bibliothek anzuzeigen.  
  
 Wenn Sie eine Warnung erweitern, wird die Codezeile, die die Warnung verursacht hat im Code\-Editor von Visual Studio hervorgehoben.  
  
 Nachdem Sie das Problem verstanden haben, können Sie es in Ihrem Code beheben.  Wiederholen Sie die Codeanalyse, um sicherzustellen, dass die Warnung nicht mehr im Codeanalysefenster angezeigt wird und dass die Lösung des Problems keine neuen Warnungen ausgelöst hat.  
  
> [!TIP]
>  Sie können die Codeanalyse aus dem Codeanalysefenster erneut ausführen.  Wählen Sie die **Analysieren** Schaltfläche und wählen Sie den Bereich der Analyse.  Sie können die Analyse für die gesamte Projektmappe oder für ein ausgewähltes Projekt erneut ausführen.  
  
##  <a name="BKMK_Suppress"></a> Unterdrücken von Codeanalysewarnungen  
 Manchmal möchten Sie möglicherweise eine Codeanalysewarnung nicht beheben.  Sie können entscheiden, dass die Auflösung der Warnung zu viel Neuprogrammierung in Bezug auf die Wahrscheinlichkeit erfordert, dass das Problem in einer beliebigen realen Implementierung Ihres Codes auftritt.   Oder Sie gehen davon aus, dass die Analyse, die in der Warnung verwendet wird, für den jeweiligen Kontext ungeeignet ist.  Sie können individuelle Warnungen unterdrücken, sodass sie nicht mehr im Codeanalysefenster angezeigt werden.  
  
 Zum Unterdrücken einer Warnung:  
  
1.  Wenn die ausführliche Information nicht angezeigt wird, wählen Sie den Titel der Warnung, um sie zu erweitern.  
  
2.  Wählen Sie den **Aktionen** Link am unteren Rand der Warnung.  
  
3.  Wählen Sie **Meldung unterdrücken** und wählen Sie dann **In Quelle**.  
  
 Unterdrücken einer Meldung fügt `#pragma warning (disable:`*WarningId*`)` ein, die die Warnung für die Codezeile unterdrückt.  
  
##  <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> Erstellen von Arbeitsaufgaben für Codeanalysewarnungen  
 Features für die Arbeitsaufgabenverfolgung können Sie in Visual Studio protokollieren.  Um dieses Feature verwenden zu können, müssen Sie sich mit einer Instanz von Team Foundation Server verbinden.  
  
 **Erstellen eine Arbeitsaufgabe für eine oder mehrere Warnungen für C\/C\+\+\-Code**  
  
1.  Klicken Sie im Codeanalysefenster die Warnungen, um sie zu erweitern und auszuwählen.  
  
2.  Wählen Sie im Kontextmenü für die Warnungen **Arbeitsaufgabe erstellen** und wählen Sie dann den Arbeitsaufgabentyp.  
  
3.  Visual Studio erstellt eine einzelne Arbeitsaufgabe für die ausgewählten Warnungen und zeigt die Arbeitsaufgabe in einem Dokumentfenster der IDE.  
  
4.  Geben Sie zusätzliche Informationen ein und wählen Sie dann **Arbeitsaufgabe speichern**.  
  
##  <a name="BKMK_Search"></a> Suchen und Filtern der Ergebnisse der Codeanalyse  
 Sie können lange Listen mit Warnmeldungen durchsuchen und Sie können Warnungen in Projektmappen mit mehreren Projekten filtern.  
  
1.  **Um Warnungen nach Titel oder Warnungs\-Id zu filtern**: Geben Sie das Schlüsselwort in das **Filter** Textfeld ein.  
  
2.  **Filter\-Warnungen nach Projekten**: Wählen Sie in einer Projektmappe mit mehreren Projekten ein oder mehrere Projekte in der Liste oben rechts im Codeanalysefenster aus.  Wählen Sie den Namen der Projektmappe, um alle Warnungen anzuzeigen.  
  
3.  **Filter\-Warnungen nach Schweregrad**: Standardmäßig wird Codeanalysen ein Schweregrad der**Warnung** zugewiesen.  Sie können den Schweregrad einer oder mehrerer Meldungen als **Fehler** in einem benutzerdefinierten Regelsatz zuweisen.  Wählen Sie entweder **Warnung** oder **Fehler**, um die Meldungen anzuzeigen, die dem jeweiligen Schweregrad zugewiesen sind.  Wählen Sie **Alle**, um alle Meldungen anzuzeigen.