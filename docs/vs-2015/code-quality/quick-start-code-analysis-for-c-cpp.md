---
title: 'Schnellstart: Code Analyse für C-C++ | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e9db06ec0748ce4499afb423fac03886cd763301
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278484"
---
# <a name="quick-start-code-analysis-for-cc"></a>Schnellstart: Codeanalyse für C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Qualität Ihrer Anwendung verbessern, indem Codeanalysen für C oder C++-Code regelmäßig ausgeführt werden. Damit können Sie allgemeine Probleme, Verstöße gegen guten Programmierstil oder Fehler, die nur schwer durch Tests ermittelt werden, finden. Codeanalysewarnungen unterscheiden sich von Compilerfehlern und -warnungen, da die Codeanalyse nach bestimmten Codeschemata sucht, die gültig sind, jedoch Probleme für Sie oder andere Personen bereiten können, die den Code verwenden.  
  
## <a name="in-this-topic"></a>In diesem Thema  
  
- [Konfigurieren von Regelsätzen für ein Projekt](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
- [Code Analyse ausführen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
- [Analysieren und Auflösen von Code Analyse Warnungen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
- [Unterdrücken der Codeanalysewarnungen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
- [Erstellen von Arbeitsaufgaben für Code Analyse Warnungen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
- [Durchsuchen und Filtern von Codeanalyseergebnissen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
## <a name="BKMK_ConfigureRuleSets"></a>Konfigurieren von Regelsätzen für ein Projekt  
  
1. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für den Projektnamen, und wählen Sie dann **Eigenschaften**aus.  
  
2. Die folgenden Schritte sind optional:  
  
    1. Wählen Sie in den Listen **Konfiguration** und **Plattform** die Buildkonfiguration und die Zielplattform aus.  
  
    2. Standardmäßig meldet die Codeanalyse keine Warnungen zu Code, der automatisch von Tools von Drittanbietern generiert wird. Um Warnungen aus generiertem Code anzuzeigen, deaktivieren Sie das Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken** .  
  
        > [!NOTE]
        > Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.  
  
3. Wenn Sie die Code Analyse bei jedem Erstellen des Projekts mithilfe der ausgewählten Konfiguration ausführen möchten, aktivieren Sie das Kontrollkästchen **CodeC++ Analyse für C/on-Build aktivieren** . Sie können die Code Analyse auch manuell ausführen, indem Sie das Menü **analysieren** öffnen und dann **Code Analyse für** *ProjectName*ausführen auswählen.  
  
4. Führen Sie in der Liste **diesen Regelsatz ausführen** einen der folgenden Schritte aus:  
  
    - Wählen Sie den Regelsatz, den Sie verwenden möchten.  
  
    - Wählen Sie **\<durchsuchen... >** , um einen vorhandenen benutzerdefinierten Regelsatz anzugeben, der nicht in der Liste enthalten ist.  
  
    - Definieren Sie einen benutzerdefinierten Regelsatz.  
  
         Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Standard-C/C++-Regelsätze  
 Visual Studio enthält zwei Standardregelsätze für systemeigenen Code:  
  
|Regelsatz|BESCHREIBUNG|  
|--------------|-----------------|  
|Von Microsoft empfohlene Mindestregeln für eigene Projekte|Dieser Regelsatz zielt auf die kritischsten Probleme in Ihrem nativen Code ab, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürzen. Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre eigenen Projekte erstellen.|  
|Von Microsoft empfohlene Regeln für eigene Projekte|Dieser Regelsatz umfasst eine Vielzahl von Problemen. Sie enthält alle Regeln in den von Microsoft empfohlenen Mindestregeln für eigene Projekte|  
  
## <a name="BKMK_Run"></a>Code Analyse ausführen  
 Auf der Codeanalyseseite von den Eigenschaftenseiten des Projekts können Sie die Codeanalyse so konfigurieren, dass Sie bei jedem Erstellen des Projekts ausgeführt wird. Sie können die Codeanalyse auch manuell ausführen.  
  
 Zum Ausführen der Codeanalyse in einer Projektmappe:  
  
- Wählen Sie im Menü **Build** die Option **Codeanalyse für Lösung ausführen** aus.  
  
  Zum Ausführen der Codeanalyse in einem Projekt:  
  
- Wählen Sie im Projektmappen-Explorer den Namen des Projektes aus.  
  
- Wählen Sie im Menü **Erstellen** die Option **Code Analyse für** *Projekt Name*ausführen aus.  
  
  Das Projekt oder die Projektmappe wird kompiliert und Codeanalyse wird ausgeführt. Die Ergebnisse werden im Codeanalysefenster angezeigt.  
  
## <a name="BKMK_Analyze"></a>Analysieren und Auflösen von Code Analyse Warnungen  
 Um eine bestimmte Warnung zu analysieren, wählen Sie den Titel der Warnung im Fenster "Codeanalyse" aus. Die Warnung wird erweitert, um weitere Informationen zu diesem Problem anzuzeigen. Wenn möglich, zeigt die Codeanalyse die Zeilennummern und Analyselogik, die zu der Warnung geführt hat. Ausführliche Informationen zur Warnung, einschließlich der möglichen Lösungen für das Problem, wählen Sie die Warnungs-Id, um das Hilfethema für diese Meldung in der MSND Bibliothek anzuzeigen.  
  
 Wenn Sie eine Warnung erweitern, wird die Codezeile, die die Warnung verursacht hat, im Visual Studio-Code-Editor hervorgehoben.  
  
 Nachdem Sie das Problem verstanden haben, können Sie es in Ihrem Code beheben. Wiederholen Sie dann die Codeanalyse, um sicherzustellen, dass die Warnung nicht mehr im Codeanalysefenster angezeigt wird, und dass durch die Korrektur keine neuen Warnungen ausgelöst wurden.  
  
> [!TIP]
> Sie können die Codeanalyse im Codeanalysefenster erneut ausführen. Wählen Sie die Schaltfläche **analysieren** aus, und wählen Sie den Bereich der Analyse aus. Sie können die Analyse für die gesamte Projektmappe oder für ein ausgewähltes Projekt erneut ausführen.  
  
## <a name="BKMK_Suppress"></a> Unterdrücken der Codeanalysewarnungen  
 Mitunter möchten Sie möglicherweise darauf verzichten, eine Codeanalysewarnung zu korrigieren. So kann es beispielsweise vorkommen, dass das Auflösen der Warnung im Verhältnis zur Wahrscheinlichkeit, dass das Problem in einer realen Implementierung des Codes auftritt, eine zu große Bearbeitung des Codes erfordert. Oder Sie gehen davon aus, dass die für die Warnung verwendete Analyse für den jeweiligen Kontext ungeeignet ist. Sie können Warnungen unterdrücken, sodass diese nicht mehr im Codeanalysefenster angezeigt werden.  
  
 So unterdrücken Sie eine Warnung  
  
1. Wenn die ausführliche Information nicht angezeigt wird, wählen Sie den Titel der Warnung, um sie zu erweitern.  
  
2. Wählen Sie unten in der Warnung den Link **Aktionen** aus.  
  
3. Wählen Sie **Meldung unterdrücken** und dann **in Quelle aus**.  
  
   Unterdrücken einer Meldung fügt `#pragma warning (disable:`*WarningId*`)` ein, das die Warnung für die Codezeile unterdrückt.  
  
## <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a>Erstellen von Arbeitsaufgaben für Code Analyse Warnungen  
 Funktionen für die Arbeitselementeverfolgung können Sie in Visual Studio protokollieren. Um diese Funktion verwenden zu können, müssen Sie sich mit einer Instanz von Team Foundation Server verbinden.  
  
 **So erstellen Sie ein Arbeits Element für mindestens eine C/C++ Code-Warnung**  
  
1. Klicken Sie im Codeanalysefenster die Warnungen, um sie zu erweitern und auszuwählen.  
  
2. Wählen Sie im Kontextmenü für die Warnungen **Arbeitsaufgabe erstellen**aus, und wählen Sie dann den Arbeits Elementtyp aus.  
  
3. Visual Studio erstellt ein einzelnes Arbeitselement für die ausgewählten Warnungen und zeigt das Arbeitselement in einem Dokumentfenster der IDE.  
  
4. Fügen Sie zusätzliche Informationen hinzu, und wählen Sie dann **Arbeitsaufgabe speichern**aus.  
  
## <a name="BKMK_Search"></a> Suchen und Filtern der Codeanalyseergebnisse  
 Sie können lange Listen mit Warnmeldungen durchsuchen und Warnungen in Projektmappen mit mehreren Projekten filtern.  
  
1. So **Filtern Sie Warnungen nach Titel oder Warnungs-ID**: Geben Sie das-Schlüsselwort in das **Filter** Textfeld ein.  
  
2. So **Filtern Sie Warnungen nach Projekt**: Wählen Sie in einer Projekt Mappe mit mehreren Projekten ein oder mehrere Projekte in der Liste oben rechts im Fenster "Code Analyse" aus. Wählen Sie den Namen der Projektmappe, um alle Warnungen anzuzeigen.  
  
3. So **Filtern Sie Warnungen nach Schweregrad**: Standardmäßig wird Code Analyse Nachrichten der Schweregrad " **Warnung**" zugewiesen. Sie können den Schweregrad von mindestens einer Nachricht als **Fehler** in einem benutzerdefinierten Regelsatz zuweisen. Wählen Sie entweder **Warnung** oder **Fehler** aus, um nur die Nachrichten anzuzeigen, denen der jeweilige Schweregrad zugewiesen wird. Wählen Sie **alle** aus, um alle Meldungen anzuzeigen.
