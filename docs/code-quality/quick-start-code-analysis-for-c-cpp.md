---
title: 'Schnellstart: Codeanalyse für C/C++'
description: Führen Sie eine statische C++ Analyse für Code in Visual Studio aus, um häufige Codierungs Probleme und Fehler zu erkennen.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 41d5c5a5ea966d1e092e7038d2fc3734c9bd9f15
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272317"
---
# <a name="quickstart-code-analysis-for-cc"></a>Schnellstart: Codeanalyse für C/C++

Sie können die Qualität Ihrer Anwendung verbessern, indem Codeanalysen für C oder C++-Code regelmäßig ausgeführt werden. Damit können Sie allgemeine Probleme, Verstöße gegen guten Programmierstil oder Fehler, die nur schwer durch Tests ermittelt werden, finden. Codeanalysewarnungen unterscheiden sich von Compilerfehlern und -warnungen, da die Codeanalyse nach bestimmten Codeschemata sucht, die gültig sind, jedoch Probleme für Sie oder andere Personen bereiten können, die den Code verwenden.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurieren von Regelsätzen für ein Projekt

1. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für den Projektnamen, und wählen Sie dann **Eigenschaften**aus.

2. Wählen Sie optional in den Listen **Konfiguration** und **Plattform** die Buildkonfiguration und die Zielplattform aus.

3. Wenn Sie die Code Analyse bei jedem Erstellen des Projekts mithilfe der ausgewählten Konfiguration ausführen möchten, aktivieren Sie das Kontrollkästchen **Code Analyse bei Build aktivieren** . Sie können die Code Analyse auch manuell ausführen, indem Sie das Menü **analysieren** öffnen und dann **Code Analyse für** *ProjectName* ausführen oder **Code Analyse für Datei ausführen**auswählen.

4. Wählen Sie den [Regelsatz](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md) aus, den Sie verwenden möchten, oder erstellen Sie einen [benutzerdefinierten Regelsatz](../code-quality/how-to-create-a-custom-rule-set.md). Wenn Sie llvm/clang-cl verwenden, finden Sie weitere Informationen unter [Verwenden von clang-tidy in Visual Studio](../code-quality/clang-tidy.md) , um clang-saubere Analyseoptionen zu konfigurieren.

### <a name="standard-cc-rule-sets"></a>Standard-C/C++-Regelsätze

Visual Studio enthält zwei Standardregelsätze für systemeigenen Code:

|Regelsatz|Beschreibung|
|--------------|-----------------|
|Von Microsoft empfohlene Mindestregeln für eigene Projekte|Dieser Regelsatz zielt auf die kritischsten Probleme in Ihrem nativen Code ab, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürzen. Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre eigenen Projekte erstellen.|
|Von Microsoft empfohlene Regeln für eigene Projekte|Dieser Regelsatz umfasst eine Vielzahl von Problemen. Sie enthält alle Regeln in den von Microsoft empfohlenen Mindestregeln für eigene Projekte|

## <a name="run-code-analysis"></a>Codeanalyse ausführen

Auf der Seite "Code Analyse" der Seite "Projekteigenschaften" können Sie die Code Analyse so konfigurieren, dass Sie jedes Mal ausgeführt wird, wenn Sie das Projekt erstellen. Sie können die Codeanalyse auch manuell ausführen.

Zum Ausführen der Codeanalyse in einer Projektmappe:

- Wählen Sie im Menü **Erstellen** die Option **Code Analyse für Projekt Mappe ausführen aus**.

Zum Ausführen der Codeanalyse in einem Projekt:

1. Wählen Sie im Projektmappen-Explorer den Namen des Projekts aus.

2. Wählen Sie im Menü **Erstellen** die Option **Code Analyse für** *Projekt Name*ausführen aus.

So führen Sie die Code Analyse für eine Datei aus:

1. Wählen Sie im Projektmappen-Explorer den Namen der Datei aus.

2. Wählen Sie im Menü **Erstellen** die Option **Code Analyse für Datei ausführen aus** , oder drücken Sie **STRG + UMSCHALT + ALT + F7**.

   Das Projekt oder die Projektmappe wird kompiliert und Codeanalyse wird ausgeführt. Die Ergebnisse werden in der Fehlerliste angezeigt.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analysieren und Auflösen von Codeanalysewarnungen

Wählen Sie den Titel der Warnung im Fehlerliste aus, um eine bestimmte Warnung zu analysieren. Die Warnung wird erweitert, um weitere Informationen zu diesem Problem anzuzeigen. Wenn möglich, zeigt die Codeanalyse die Zeilennummern und Analyselogik, die zu der Warnung geführt hat. Um ausführliche Informationen zur Warnung, einschließlich möglicher Lösungen für das Problem, zu erhalten, wählen Sie die Warnungs-ID aus, um das entsprechende Online Hilfethema anzuzeigen.

Wenn Sie eine Warnung auswählen, wird die Codezeile, die die Warnung verursacht hat, im Visual Studio-Code-Editor hervorgehoben.

Nachdem Sie das Problem verstanden haben, können Sie es in Ihrem Code beheben. Führen Sie dann die Code Analyse erneut aus, um sicherzustellen, dass die Warnung nicht mehr in der Fehlerliste angezeigt wird, und dass die Korrektur keine neuen Warnungen ausgelöst hat.

## <a name="suppress-code-analysis-warnings"></a>Code Analyse Warnungen unterdrücken

Mitunter möchten Sie möglicherweise darauf verzichten, eine Codeanalysewarnung zu korrigieren. So kann es beispielsweise vorkommen, dass das Auflösen der Warnung im Verhältnis zur Wahrscheinlichkeit, dass das Problem in einer realen Implementierung des Codes auftritt, eine zu große Bearbeitung des Codes erfordert. Oder Sie gehen davon aus, dass die für die Warnung verwendete Analyse für den jeweiligen Kontext ungeeignet ist. Sie können einzelne Warnungen unterdrücken, sodass Sie nicht mehr in der Fehlerliste angezeigt werden.

So unterdrücken Sie eine Warnung

1. Wenn die ausführliche Information nicht angezeigt wird, wählen Sie den Titel der Warnung, um sie zu erweitern.

2. Wählen Sie unten in der Warnung den Link **Aktionen** aus.

3. Wählen Sie **Meldung unterdrücken** und dann **in Quelle aus**.

   Wenn Sie eine Meldung unterdrücken, werden `#pragma warning (disable:[warning ID])` eingefügt, die die Warnung für die Codezeile unterdrückt.

## <a name="create-work-items-for-code-analysis-warnings"></a>Erstellen von Arbeitsaufgaben für Code Analyse Warnungen

Funktionen für die Arbeitselementeverfolgung können Sie in Visual Studio protokollieren. Um diese Funktion verwenden zu können, müssen Sie sich mit einer Instanz von Team Foundation Server verbinden.

**So erstellen Sie ein Arbeits Element für mindestens eine C/C++ Code-Warnung**

1. Erweitern Sie im Fehlerliste die Option Warnungen, und wählen Sie Sie aus.

2. Wählen Sie im Kontextmenü für die Warnungen **Arbeitsaufgabe erstellen**aus, und wählen Sie dann den Arbeits Elementtyp aus.

3. Visual Studio erstellt ein einzelnes Arbeitselement für die ausgewählten Warnungen und zeigt das Arbeitselement in einem Dokumentfenster der IDE.

4. Fügen Sie zusätzliche Informationen hinzu, und wählen Sie dann **Arbeitsaufgabe speichern**aus.

## <a name="search-and-filter-code-analysis-results"></a>Code Analyseergebnisse suchen und Filtern

Sie können lange Listen mit Warnmeldungen durchsuchen und Warnungen in Projektmappen mit mehreren Projekten filtern.

- So **Filtern Sie Warnungen nach Titel oder Warnungs-ID**: Geben Sie das Schlüsselwort in das Suchfeld ein.

- So **Filtern Sie Warnungen nach Schweregrad**: Standardmäßig wird Code Analyse Nachrichten der Schweregrad " **Warnung**" zugewiesen. Sie können den Schweregrad von mindestens einer Nachricht als **Fehler** in einem benutzerdefinierten Regelsatz zuweisen. Wählen Sie in der Spalte **Schweregrad** des **Fehlerliste**den Dropdown Pfeil und dann das Filter Symbol aus. Wählen Sie **Warnung** oder **Fehler** aus, um nur die Nachrichten anzuzeigen, die dem jeweiligen Schweregrad zugewiesen sind. Wählen Sie **Alle auswählen** aus, um alle Meldungen anzuzeigen.

## <a name="see-also"></a>Siehe auch

- [Code Analyse für C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
