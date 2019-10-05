---
title: Konfigurieren der Codeanalyse
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
ms.openlocfilehash: 86aa308369ef93792126c7f8da5f59f94ef0c02a
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975116"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Vorgehensweise: Legacy Analyse für verwalteten Code konfigurieren

In Visual Studio können Sie aus einer Liste von Code Analyse- [Regelsätzen](../code-quality/rule-set-reference.md) auswählen, die auf ein Projekt mit verwaltetem Code angewendet werden sollen. In der Standardeinstellung die **Microsoft-Mindestregeln** Regelsatz ausgewählt ist, aber Sie können bei Bedarf einen anderen Regelsatz anwenden. Regelsätze können auf eine oder mehrere Projekte in einer Projektmappe angewendet werden.

> [!NOTE]
> Dieser Artikel bezieht sich auf die Legacy Analyse und nicht auf [.NET Compiler Platform basierte Code Analysen](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Konfigurieren eines Regelsatzes für ein .NET Framework Projekt

1. Öffnen der **Codeanalyse** Registerkarte auf den Eigenschaftenseiten des Projekts. Dies ist in einem der folgenden Arten möglich:

   - In **Projektmappen-Explorer**, wählen Sie das Projekt. Wählen Sie auf der Menüleiste **analysieren** > **Codeanalyse konfigurieren** > **für \<Projektname >** .

   - Mit der rechten Maustaste in des Projekts im **Projektmappen-Explorer** , und wählen Sie **Eigenschaften**, und wählen Sie dann die **Codeanalyse** Registerkarte.

2. In der **Konfiguration** und **Plattform** Listen, wählen Sie die Buildplattform und die Zielplattform.

::: moniker range="vs-2017"

3. Wenn Sie die Code Analyse bei jedem Erstellen des Projekts mithilfe der ausgewählten Konfiguration ausführen möchten, wählen Sie **Code Analyse beim Build aktivieren aus**. Sie können die Codeanalyse auch manuell ausführen, indem Sie auswählen **analysieren** > **Codeanalyse ausführen** > **Ausführen der Codeanalyse für \<Projektname >** .

::: moniker-end

::: moniker range=">=vs-2019"

3. Wenn Sie die Code Analyse bei jedem Erstellen des Projekts mithilfe der ausgewählten Konfiguration ausführen möchten, wählen Sie im Abschnitt **binäre Analyse** Module die Option **im Build ausführen** aus. Sie können die Codeanalyse auch manuell ausführen, indem Sie auswählen **analysieren** > **Codeanalyse ausführen** > **Ausführen der Codeanalyse für \<Projektname >** .

::: moniker-end

4. Um Warnungen zu generiertem Code anzuzeigen, deaktivieren Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.

    > [!NOTE]
    > Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Sie können den Quellcode für ein Formular oder eine Vorlage anzeigen und verwalten und werden nicht überschrieben.

::: moniker range="vs-2017"

5. In der **diesen Regelsatz ausführen** aufzulisten, führen Sie eine der folgenden:

::: moniker-end

::: moniker range=">=vs-2019"

5. Führen Sie in der Liste **aktive Regeln** einen der folgenden Schritte aus:

::: moniker-end

    - Wählen Sie den Regelsatz, den Sie verwenden möchten.

    - Wählen Sie **\<browse >** aus, um einen vorhandenen benutzerdefinierten Regelsatz zu suchen, der nicht in der Liste enthalten ist.

    - Definieren einer [benutzerdefinierten Regelsatz](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Angeben von Regelsätzen für mehrere Projekte in einer Projektmappe

Standardmäßig werden alle verwalteten Projekten einer Projektmappe zugewiesen der *Microsoft-Mindestregeln* code Codeanalyse-Regelsatz. Sie können ändern, dass die Regelsätze, die den Projekten einer Projektmappe im zugewiesen sind, die **Eigenschaften** im Dialogfeld für die Lösung.

1. Öffnen Sie die Lösung in Visual Studio.

2. Auf der **analysieren** , wählen Sie im Menü **Codeanalyse für Projektmappe konfigurieren**.

3. Erweitern Sie ggf. **allgemeine Eigenschaften**, und wählen Sie dann **Codeanalyseeinstellungen**.

4. Sie können einen Regelsatz für ein oder mehrere Projekte angeben:

    - Um einen Regelsatz für ein einzelnes Projekt anzugeben, wählen Sie den Namen des Projekts.

    - Um einen Regelsatz für mehrere Projekte angeben möchten, halten Sie die **STRG** , und wählen Sie den Projektnamen.

    - Um alle Projekte in der Projektmappe angeben möchten, halten Sie die **UMSCHALT** , und klicken Sie in der Projektliste.

5. Wählen Sie die **Regelsatz** Feld eines Projekts, und wählen Sie dann der Namen der Regel festlegen, dass Sie anwenden möchten.

## <a name="see-also"></a>Siehe auch

- [Codeanalyse-Regelsatzreferenz](../code-quality/rule-set-reference.md)