---
title: Codeanalyse für verwalteten Code
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e306d19dcf10e929bfb6432e6b6eb585996657f
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550851"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Übersicht über die Code Analyse für verwalteten Code in Visual Studio

Visual Studio kann eine Code Analyse von verwaltetem Code auf zweierlei Weise durchführen: mit [Legacy Analyse](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), auch als "FxCop Static Analysis of Managed Assemblys" bezeichnet, und mit den moderneren .NET Compiler Platform basierten [Code](../code-quality/roslyn-analyzers-overview.md)Analysemodulen. In diesem Thema wird die Legacy Analyse behandelt. Weitere Informationen zur .NET Compiler Platform basierten Code Analyse finden Sie unter [Übersicht über .NET Compiler Platform-basierte Analysen](../code-quality/roslyn-analyzers-overview.md).

Die Code Analyse für verwalteten Code analysiert verwaltete Assemblys und meldet Informationen über die Assemblys, z. b. Verstöße gegen die Programmier-und Entwurfs Regeln, die in den [.net-Entwurfs Richtlinien](/dotnet/standard/design-guidelines/)festgelegt sind

Das Analysetool stellt die während einer Analyse durchgeführten Prüfungen als Warnmeldungen dar. In diesen Warnmeldungen werden alle relevanten Probleme im Zusammenhang mit Programmierung und Entwurf benannt. Nach Möglichkeit wird außerdem angegeben, wie das jeweilige Problem gelöst werden kann.

> [!NOTE]
> Die Legacy Analyse (statische Code Analyse) wird für .net Core-und .NET Standard-Projekte in Visual Studio nicht unterstützt. Wenn Sie die Code Analyse in einem .net Core-oder .NET Standard Projekt als Teil von MSBuild ausführen, wird eine Fehlermeldung ähnlich **der folgenden angezeigt: CA0055 : Die Plattform für \<die DLL->** konnte nicht identifiziert werden. Verwenden Sie stattdessen [Code Analysen](../code-quality/roslyn-analyzers-overview.md) , um Code in .net Core-oder .NET Standard Projekten zu analysieren.

## <a name="ide-integrated-development-environment-integration"></a>Integration der IDE (integrierte Entwicklungsumgebung)

Sie können die Code Analyse für Ihr Projekt manuell oder automatisch ausführen.

Um die Code Analyse jedes Mal auszuführen, wenn Sie ein Projekt erstellen, wählen Sie auf der Eigenschaften Seite des Projekts die Option **Code Analyse für Build aktivieren aus** . Weitere Informationen finden Sie unter [Vorgehensweise: Enable and Disable Automatic Code Analysis (Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse)](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Um die Code Analyse für ein Projekt manuell auszuführen, wählen Sie in der Menüleiste **Analyse** > **Ausführen Code Analyse** > ausführen**Code \<Analyse für Projekt >** aus.

## <a name="rule-sets"></a>Regelsätze

Codeanalyseregeln für verwalteten Code werden in [Regelsätze](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) gruppiert. Sie können einen der Standardregel Sätze von Microsoft verwenden, oder Sie können [einen benutzerdefinierten Regelsatz erstellen](../code-quality/how-to-create-a-custom-rule-set.md) , um einen bestimmten Bedarf zu erfüllen.

## <a name="suppress-warnings"></a>Unterdrücken von Warnungen

Es kann häufig hilfreich sein anzugeben, dass eine Warnung nicht zutreffend ist. Entwickler und andere Personen, die später möglicherweise den Code überprüfen, wissen dann, dass eine Warnung untersucht und unterdrückt oder ignoriert wurde.

Die Quell Unterdrückung von Warnungen wird durch benutzerdefinierte Attribute implementiert. Fügen Sie zum Unterdrücken einer Warnung das Attribut `SuppressMessage` zum Quellcode hinzu, wie im folgenden Beispiel dargestellt:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Weitere Informationen finden Sie unter unter [drücken von Warnungen](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Wenn Sie ein Projekt zu Visual Studio 2017 oder Visual Studio 2019 migrieren, kann es vorkommen, dass eine große Anzahl von Code Analyse Warnungen angezeigt wird. Wenn Sie nicht bereit sind, die Warnungen zu beheben und sofort produktiv zu arbeiten, können Sie den Analyse Status Ihres Projekts als *Grundlage* festlegen. Wählen Sie im Menü **analysieren** die Option **Code Analyse ausführen und aktive Probleme unterdrücken**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ausführen der Codeanalyse im Rahmen der Eincheckrichtlinien

In einer Organisation ist es sinnvoll festzulegen, dass beim Einchecken stets bestimmte Richtlinien beachtet werden müssen. Insbesondere die folgenden Richtlinien sollten eingehalten werden:

- Beim Einchecken von Code sind keine Buildfehler vorhanden.

- Die Code Analyse wird als Teil des letzten Builds ausgeführt.

Die Einhaltung dieser Vorgaben können Sie durch das Definieren von Eincheckrichtlinien gewährleisten. Weitere Informationen finden Sie unter [verbessern der Code Qualität mit Project Check-in-Richtlinien](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Team Build-Integration

Sie können die integrierten Features des Buildsystems verwenden, um das Analysetool im Rahmen des Buildprozesses auszuführen. Weitere Informationen finden Sie unter [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Siehe auch

- [Übersicht über .NET Compiler Platform-basierte Analysetools](../code-quality/roslyn-analyzers-overview.md)
- [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Vorgehensweise: Enable and Disable Automatic Code Analysis (Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse)](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
