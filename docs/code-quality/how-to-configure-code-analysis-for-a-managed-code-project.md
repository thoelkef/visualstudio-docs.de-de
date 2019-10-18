---
title: Konfigurieren der Code Analyse
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f1bfa8c6e5260fb4afd20b882e2bdfc718647f4b
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448982"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Vorgehensweise: Konfigurieren der Legacy Analyse für verwalteten Code

In Visual Studio können Sie aus einer Liste von Code Analyse- [Regelsätzen](../code-quality/rule-set-reference.md) auswählen, die auf ein Projekt mit verwaltetem Code angewendet werden sollen. Standardmäßig ist der Regelsatz **Microsoft-Mindestregeln empfohlen** ausgewählt. Sie können jedoch bei Bedarf einen anderen Regelsatz anwenden. Regelsätze können auf ein oder mehrere Projekte in einer Projekt Mappe angewendet werden.

> [!NOTE]
> Dieser Artikel bezieht sich auf die Legacy Analyse und nicht auf [.NET Compiler Platform basierte Code Analysen](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Konfigurieren eines Regelsatzes für ein .NET Framework Projekt

1. Öffnen Sie die Registerkarte **Code Analyse** auf den Eigenschaften Seiten des Projekts. Dies kann auf eine der folgenden Arten erfolgen:

   - Wählen Sie in **Projektmappen-Explorer**das Projekt aus. Wählen Sie in der Menüleiste **analysieren** aus,  >  die**Code Analyse**  > **für \<projectname >** konfigurieren.

   - Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**und dann die Registerkarte **Code Analyse** aus.

2. Wählen Sie in den Listen **Konfiguration** und **Plattform** die Buildkonfiguration und die Zielplattform aus.

::: moniker range="vs-2017"

3. Wenn Sie die Code Analyse bei jedem Erstellen des Projekts mithilfe der ausgewählten Konfiguration ausführen möchten, wählen Sie **Code Analyse beim Build aktivieren aus**. Sie können die Code Analyse auch manuell ausführen, indem Sie **analysieren**  > **Code Analyse ausführen**  > **Code Analyse auf \<projectname >** ausführen auswählen.

::: moniker-end

::: moniker range=">=vs-2019"

3. Wenn Sie die Code Analyse bei jedem Erstellen des Projekts mithilfe der ausgewählten Konfiguration ausführen möchten, wählen Sie im Abschnitt **binäre Analyse** Module die Option **im Build ausführen** aus. Sie können die Code Analyse auch manuell ausführen, indem Sie **analysieren**  > **Code Analyse ausführen**  > **Code Analyse auf \<projectname >** ausführen auswählen.

::: moniker-end

4. Um Warnungen aus generiertem Code anzuzeigen, deaktivieren Sie das Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken** .

    > [!NOTE]
    > Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Sie können den Quellcode für ein Formular oder eine Vorlage anzeigen und verwalten und werden nicht überschrieben.

::: moniker range="vs-2017"

5. Führen Sie in der Liste **diesen Regelsatz ausführen** einen der folgenden Schritte aus:

::: moniker-end

::: moniker range=">=vs-2019"

5. Führen Sie in der Liste **aktive Regeln** einen der folgenden Schritte aus:

::: moniker-end

    - Wählen Sie den Regelsatz aus, den Sie verwenden möchten.

    - Wählen Sie **\<Browse >** aus, um einen vorhandenen benutzerdefinierten Regelsatz zu suchen, der nicht in der Liste enthalten ist.

    - Definieren Sie einen [benutzerdefinierten Regelsatz](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Angeben von Regelsätzen für mehrere Projekte in einer Projekt Mappe

Standardmäßig wird allen verwalteten Projekten einer Projekt Mappe der Code Analyse-Regelsatz der *empfohlenen Microsoft-Regeln* zugewiesen. Sie können die Regelsätze ändern, die den Projekten einer Projekt Mappe im Dialogfeld **Eigenschaften** für die Lösung zugewiesen sind.

1. Öffnen Sie die Lösung in Visual Studio.

2. Wählen Sie im Menü **analysieren** die Option **Code Analyse für Projekt Mappe konfigurieren aus**.

3. Erweitern Sie ggf. **Allgemeine Eigenschaften**, und wählen Sie dann **Code Analyse Einstellungen**aus.

4. Sie können einen Regelsatz für ein oder mehrere Projekte angeben:

    - Um einen Regelsatz für ein einzelnes Projekt anzugeben, wählen Sie den Projektnamen aus.

    - Halten Sie die **STRG** -Taste gedrückt, und wählen Sie die Projektnamen aus, um einen Regelsatz für mehrere Projekte anzugeben.

    - Wenn Sie alle Projekte in der Projekt Mappe angeben möchten, halten Sie die **UMSCHALT** Taste gedrückt, und klicken Sie in die Projektliste.

5. Wählen Sie das Feld **Regelsatz** eines Projekts aus, und wählen Sie dann den Namen des Regelsatzes aus, den Sie anwenden möchten.

## <a name="see-also"></a>Siehe auch

- [Codeanalyse-Regelsatzreferenz](../code-quality/rule-set-reference.md)
