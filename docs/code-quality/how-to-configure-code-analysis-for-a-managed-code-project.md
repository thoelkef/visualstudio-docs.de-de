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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 98db7cda02495d207d6e9387341173ea2efe22ca
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431351"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Gewusst wie: Konfigurieren der Legacyanalyse für verwalteten Code

In Visual Studio können Sie aus einer Liste von [Codeanalyseregelsätzen](../code-quality/rule-set-reference.md) auswählen, die auf ein Projekt mit verwaltetem Code angewendet werden sollen. Standardmäßig ist der **Regelsatz "Microsoft Minimum Recommended Rules"** ausgewählt, Sie können jedoch bei Bedarf einen anderen Regelsatz anwenden. Regelsätze können auf ein oder mehrere Projekte in einer Projektmappe angewendet werden.

> [!NOTE]
> Dieser Artikel gilt für die Legacyanalyse und nicht [für .NET Compiler Platform-basierte Codeanalysatoren](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Konfigurieren eines Regelsatzes für ein .NET Framework-Projekt

1. Öffnen Sie die Registerkarte **Codeanalyse** auf den Eigenschaftenseiten des Projekts. Dafür stehen folgende Möglichkeiten zur Verfügung:

   - Wählen Sie im **Projektmappen-Explorer**das Projekt aus. Wählen Sie in der Menüleiste **die** > Option**Codeanalyse** > **für \<Projektnamen>analysieren **aus.

   - Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**aus, und wählen Sie dann die Registerkarte **Codeanalyse** aus.

2. Wählen Sie in den Listen **Konfiguration** und **Plattform** die Buildkonfiguration und die Zielplattform aus.

::: moniker range="vs-2017"

3. Um die Codeanalyse jedes Mal auszuführen, wenn das Projekt mithilfe der ausgewählten Konfiguration erstellt wird, wählen Sie **Codeanalyse beim Erstellen aktivieren**aus. Sie können die Codeanalyse auch manuell ausführen, indem Sie > **Analysecodeanalyse** > **für \<Projektnamen>** analysieren auswählen. **Analyze**

::: moniker-end

::: moniker range=">=vs-2019"

3. Um die Codeanalyse jedes Mal auszuführen, wenn das Projekt mithilfe der ausgewählten Konfiguration erstellt wird, wählen Sie **Ausführen auf Build** im Abschnitt **Binäre Analysatoren** aus. Sie können die Legacycodeanalyse auch manuell ausführen, siehe [Gewusst wie: Ausführen der Legacycodeanalyse manuell für verwalteten Code.](how-to-run-legacy-code-analysis-manually-for-managed-code.md)

::: moniker-end

4. Um Warnungen aus generiertem Code anzuzeigen, deaktivieren Sie das Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken.**

    > [!NOTE]
    > Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Sie können den Quellcode für ein Formular oder eine Vorlage anzeigen und verwalten, und er wird nicht überschrieben.

::: moniker range="vs-2017"

5. Führen Sie in der Liste **Diesen Regelsatz aus:**

::: moniker-end

::: moniker range=">=vs-2019"

5. Führen Sie in der Liste **Aktive Regeln** eine der folgenden Schritte aus:

::: moniker-end

   - Wählen Sie den Regelsatz aus, den Sie verwenden möchten.

   - Wählen Sie ** \<>durchsuchen** aus, um einen vorhandenen benutzerdefinierten Regelsatz zu finden, der nicht in der Liste enthalten ist.

   - Definieren Sie einen [benutzerdefinierten Regelsatz](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Festlegen von Regelsätzen für mehrere Projekte in einer Projektmappe

Standardmäßig wird allen verwalteten Projekten einer Projektmappe der Codeanalyseregelsatz für die Codeanalyse von *Microsoft Minimum Recommended Rules* zugewiesen. Sie können die Regelsätze ändern, die den Projekten einer Projektmappe im Dialogfeld **Eigenschaften** für die Projektmappe zugewiesen sind.

1. Öffnen Sie die Projektmappe in Visual Studio.

2. Wählen Sie im Menü **Analysieren** die Option **Codeanalyse für Lösung konfigurieren**aus.

3. Erweitern Sie ggf. **die allgemeinen Eigenschaften**, und wählen Sie dann Die **Codeanalyseeinstellungen**aus.

4. Sie können einen Regelsatz für ein oder mehrere Projekte angeben:

    - Um einen Regelsatz für ein einzelnes Projekt anzugeben, wählen Sie den Projektnamen aus.

    - Um einen Regelsatz für mehrere Projekte anzugeben, halten **Sie Strg** gedrückt, und wählen Sie die Projektnamen aus.

    - Um alle Projekte in der Projektmappe anzugeben, halten Sie **die Umschalttaste** gedrückt und klicken Sie in die Projektliste.

5. Wählen Sie das Feld **Regelsatz** eines Projekts aus, und wählen Sie dann den Namen des Regelsatzes aus, den Sie anwenden möchten.

## <a name="see-also"></a>Weitere Informationen

- [Codeanalyse-Regelsatzreferenz](../code-quality/rule-set-reference.md)
