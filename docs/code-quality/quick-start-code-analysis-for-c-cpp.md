---
title: 'Schnellstart: Codeanalyse für C/C++'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 3aefc42e77c6ccaf14a426a26e12b81b49bb5632
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818762"
---
# <a name="quickstart-code-analysis-for-cc"></a>Schnellstart: Codeanalyse für C/C++

Sie können die Qualität Ihrer Anwendung verbessern, indem Codeanalysen für C oder C++-Code regelmäßig ausgeführt werden. Damit können Sie allgemeine Probleme, Verstöße gegen guten Programmierstil oder Fehler, die nur schwer durch Tests ermittelt werden, finden. Codeanalysewarnungen unterscheiden sich von Compilerfehlern und -warnungen, da die Codeanalyse nach bestimmten Codeschemata sucht, die gültig sind, jedoch Probleme für Sie oder andere Personen bereiten können, die den Code verwenden.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurieren von Regelsätzen für ein Projekt

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektnamen, und wählen Sie dann **Eigenschaften**.

2. Die folgenden Schritte sind optional:

    1. In der **Konfiguration** und **Plattform** Listen, wählen Sie die Buildplattform und die Zielplattform.

    2. Standardmäßig meldet die Codeanalyse keine Warnungen zu Code, der automatisch von Tools von Drittanbietern generiert wird. Um Warnungen zu generiertem Code anzuzeigen, deaktivieren Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.

        > [!NOTE]
        > Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.

3. Codeanalyse ausführen jedes Mal, wenn das Projekt mit der ausgewählten Konfiguration erstellt wird, wählen die **Codeanalyse für C/C++ auf Build aktivieren** Kontrollkästchen. Sie können die Codeanalyse auch manuell ausführen, indem Sie öffnen die **analysieren** Menü auswählen und dann **Ausführen der Codeanalyse für** *ProjectName*.

4. In der **diesen Regelsatz ausführen** aufzulisten, führen Sie eine der folgenden:

    - Wählen Sie den Regelsatz, den Sie verwenden möchten.

    - Wählen Sie  **\<durchsuchen... >** einen vorhandenen benutzerdefinierten Regelsatz anzugeben, ist nicht in der Liste.

    - Definieren einer [benutzerdefinierten Regelsatz](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Standard-C/C++-Regelsätze

Visual Studio enthält zwei Standardregelsätze für systemeigenen Code:

|Regelsatz|Beschreibung|
|--------------|-----------------|
|Von Microsoft empfohlene Mindestregeln für eigene Projekte|Dieser Regelsatz zielt auf die kritischsten Probleme in Ihrem systemeigenen Code ab, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürzen. Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre eigenen Projekte erstellen.|
|Von Microsoft empfohlene Regeln für eigene Projekte|Dieser Regelsatz umfasst eine Vielzahl von Problemen. Sie enthält alle Regeln in den von Microsoft empfohlenen Mindestregeln für eigene Projekte|

## <a name="run-code-analysis"></a>Codeanalyse ausführen

Auf der Codeanalyseseite von den Eigenschaftenseiten des Projekts können Sie die Codeanalyse so konfigurieren, dass Sie bei jedem Erstellen des Projekts ausgeführt wird. Sie können die Codeanalyse auch manuell ausführen.

Zum Ausführen der Codeanalyse in einer Projektmappe:

- Wählen Sie im Menü **Build** die Option **Codeanalyse für Lösung ausführen** aus.

Zum Ausführen der Codeanalyse in einem Projekt:

1. Wählen Sie im Projektmappen-Explorer den Namen des Projektes aus.

2. Auf der **erstellen** Menü wählen **Ausführen der Codeanalyse für** *Projektname*.

   Das Projekt oder die Projektmappe wird kompiliert und Codeanalyse wird ausgeführt. Ergebnisse werden in der Fehlerliste angezeigt.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analysieren und Auflösen von Codeanalysewarnungen

Um eine bestimmte Warnung zu analysieren, wählen Sie den Titel der Warnung, die in der Fehlerliste. Die Warnung wird erweitert, um weitere Informationen zu diesem Problem anzuzeigen. Wenn möglich, zeigt die Codeanalyse die Zeilennummern und Analyselogik, die zu der Warnung geführt hat. Ausführliche Informationen zur Warnung, einschließlich der möglichen Lösungen für das Problem wählen Sie die Warnungs-ID, um die entsprechenden Onlinehilfethema anzuzeigen.

Wenn Sie eine Warnung auswählen, wird die Zeile des Codes, der die Warnung verursacht hat, im Visual Studio Code-Editor hervorgehoben.

Nachdem Sie das Problem verstanden haben, können Sie es in Ihrem Code beheben. Klicken Sie dann erneut ausführen Sie Codeanalyse, um sicherzustellen, dass die Warnung nicht mehr angezeigt, in der Fehlerliste enthalten wird und dass nicht der Fall der Korrektur ist neuen Warnungen ausgelöst.

## <a name="suppress-code-analysis-warnings"></a>Unterdrücken von codeanalysewarnungen

Mitunter möchten Sie möglicherweise darauf verzichten, eine Codeanalysewarnung zu korrigieren. So kann es beispielsweise vorkommen, dass das Auflösen der Warnung im Verhältnis zur Wahrscheinlichkeit, dass das Problem in einer realen Implementierung des Codes auftritt, eine zu große Bearbeitung des Codes erfordert. Oder Sie gehen davon aus, dass die für die Warnung verwendete Analyse für den jeweiligen Kontext ungeeignet ist. Sie können Warnungen unterdrücken, sodass sie nicht mehr in der Fehlerliste angezeigt werden.

So unterdrücken Sie eine Warnung

1. Wenn die ausführliche Information nicht angezeigt wird, wählen Sie den Titel der Warnung, um sie zu erweitern.

2. Wählen Sie unten in der Warnung den Link **Aktionen** aus.

3. Wählen Sie **Meldung unterdrücken** und wählen Sie dann **In Quelle**.

   Unterdrücken einer Meldung fügt `#pragma warning (disable:[warning ID])` , die die Warnung für die Codezeile unterdrückt.

## <a name="create-work-items-for-code-analysis-warnings"></a>Erstellen von Arbeitselementen für codeanalysewarnungen

Funktionen für die Arbeitsaufgabenverfolgung können Sie in Visual Studio protokollieren. Um diese Funktion verwenden zu können, müssen Sie sich mit einer Instanz von Team Foundation Server verbinden.

**Um ein Arbeitselement für eine oder mehrere Warnungen für C/C++-Code zu erstellen.**

1. Erweitern Sie in der Fehlerliste, und wählen Sie die Warnungen

2. Wählen Sie auf das Kontextmenü für die Warnungen, **Arbeitsaufgabe erstellen**, und wählen Sie dann den Arbeitselementtyp.

3. Visual Studio erstellt ein einzelnes Arbeitselement für die ausgewählten Warnungen und zeigt das Arbeitselement in einem Dokumentfenster der IDE.

4. Fügen Sie zusätzliche Informationen hinzu, und wählen Sie dann **Arbeitsaufgabe speichern**.

## <a name="search-and-filter-code-analysis-results"></a>Ergebnisse der Codeanalyse Such- und Filterfunktionen

Sie können lange Listen mit Warnmeldungen durchsuchen und Warnungen in Projektmappen mit mehreren Projekten filtern.

- **Filter-Warnungen nach Titel oder Warnungs-Id**: Geben Sie das Schlüsselwort in das Suchfeld.

- **Filter-Warnungen nach Schweregrad**: in der Standardeinstellung werden Codeanalysen einen Schweregrad der zugewiesen **Warnung**. Sie können den Schweregrad der eine oder mehrere Nachrichten als zuweisen **Fehler** in einer benutzerdefinierten Regel festgelegt. Auf der **Schweregrad** Spalte die **Fehlerliste**, wählen Sie das Dropdown-Pfeil und dann auf das Symbol "Filter". Wählen Sie **Warnung** oder **Fehler** nur die Meldungen angezeigt, die den jeweiligen Schweregrad zugewiesen sind. Wählen Sie **Alles markieren** um alle Meldungen anzuzeigen.

## <a name="see-also"></a>Siehe auch

[Codeanalyse für C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)