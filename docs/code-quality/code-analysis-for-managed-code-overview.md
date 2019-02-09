---
title: Statische Codeanalyse für verwalteten code
ms.date: 03/26/2018
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0da99377a6e0f5405029c0ac194484de3a3a1c90
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909140"
---
# <a name="overview-of-static-code-analysis-for-managed-code-in-visual-studio"></a>Übersicht über die statische Codeanalyse für verwalteten Code in Visual Studio

Visual Studio 2017 können Codeanalyse für verwalteten Code ausführen, gibt es zwei Möglichkeiten: mit *FxCop* statische Analysen für verwalteten Assemblys sowie die moderner *Roslyn-Analysetools*. Dieses Thema behandelt die Analyse von statischem Code FxCop. Weitere Informationen zum Analysieren von Code mithilfe von Code-Analyzer finden Sie unter [Übersicht der Roslyn-Analysetools](../code-quality/roslyn-analyzers-overview.md).

Die Codeanalyse für verwalteten Code analysiert verwaltete Assemblys und erstellt einen Bericht mit Informationen zu diesen Assemblys, in dem z. B. Verletzungen der in den Microsoft .NET Framework-Entwurfsrichtlinien festgelegten Programmierungs- und Entwurfsregeln gemeldet werden.

Das Analysetool stellt die während einer Analyse durchgeführten Prüfungen als Warnmeldungen dar. In diesen Warnmeldungen werden alle relevanten Probleme im Zusammenhang mit Programmierung und Entwurf benannt. Nach Möglichkeit wird außerdem angegeben, wie das jeweilige Problem gelöst werden kann.

> [!NOTE]
> Analyse von statischem Code wird für .NET Core und .NET Standard-Projekte in Visual Studio nicht unterstützt. Wenn Sie die Codeanalyse für ein Projekt für .NET Core oder .NET Standard als Teil von Msbuild ausführen, sehen Sie eine Fehlermeldung ähnlich **Fehler: CA0055 : Plattform für konnte nicht identifiziert \<your.dll >**. Verwenden Sie zum Analysieren von Code in Projekten auf .NET Core oder .NET Standard [Roslyn-Analysetools](../code-quality/roslyn-analyzers-overview.md) stattdessen.

## <a name="ide-integrated-development-environment-integration"></a>Integration von IDE (integrierte Entwicklungsumgebung)

Sie können die Codeanalyse manuell oder automatisch auf das Projekt ausführen.

Um die Codeanalyse immer auszuführen, die Sie ein Projekt erstellen, wählen Sie **Codeanalyse für Build aktivieren** auf der Eigenschaftenseite des Projekts. Weitere Informationen finden Sie unter [Vorgehensweise: Enable and Disable Automatic Code Analysis (Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse)](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Die Codeanalyse manuell an einem Projekt ausführen, wählen Sie in der Menüleiste **analysieren** > **Codeanalyse ausführen** > **Ausführen der Codeanalyse für \<Projekt >**.

## <a name="rule-sets"></a>Regelsätze

Codeanalyseregeln für verwalteten Code werden in [Regelsätze](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) gruppiert. Sie können eines der Microsoft-Standardregelsätze verwenden, oder Sie können [Erstellen eines benutzerdefinierten Regelsatzes](../code-quality/how-to-create-a-custom-rule-set.md) auf eine bestimmte Anforderung zu erfüllen.

## <a name="suppress-warnings"></a>Unterdrücken von Warnungen

Es kann häufig hilfreich sein anzugeben, dass eine Warnung nicht zutreffend ist. Entwickler und andere Personen, die später möglicherweise den Code überprüfen, wissen dann, dass eine Warnung untersucht und unterdrückt oder ignoriert wurde.

Unterdrückung von Warnungen im Quellcode wird über benutzerdefinierte Attribute implementiert. Fügen Sie zum Unterdrücken einer Warnung das Attribut `SuppressMessage` zum Quellcode hinzu, wie im folgenden Beispiel dargestellt:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Weitere Informationen finden Sie unter [Unterdrücken von Warnungen](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Wenn Sie ein Projekt in Visual Studio 2017 migrieren, können Sie plötzlich eine große Anzahl von Warnungen der Codeanalyse ausgesetzt sind. Wenn Sie nicht möchten Sie die Warnungen beheben und sofort produktiv werden soll, können Sie *Baseline* den Analyse-Zustand des Projekts. Von der **analysieren** , wählen Sie im Menü **Codeanalyse ausführen und aktive Probleme unterdrücken**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ausführen der Codeanalyse im Rahmen der Eincheckrichtlinien

In einer Organisation ist es sinnvoll festzulegen, dass beim Einchecken stets bestimmte Richtlinien beachtet werden müssen. Insbesondere die folgenden Richtlinien sollten eingehalten werden:

- Es gibt keine Buildfehler im Code eingecheckt wird.

- Die Codeanalyse wird als Teil des neuesten Builds ausgeführt.

Die Einhaltung dieser Vorgaben können Sie durch das Definieren von Eincheckrichtlinien gewährleisten. Weitere Informationen finden Sie unter [Verbessern der Codequalität mit Eincheckrichtlinien für das Projekt](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Team Build-integration

Sie können die integrierten Funktionen des Buildsystems verwenden, um das Analysetool im Rahmen des Buildprozesses auszuführen. Weitere Informationen finden Sie unter [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Roslyn-Analysetools](../code-quality/roslyn-analyzers-overview.md)
- [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Vorgehensweise: Enable and Disable Automatic Code Analysis (Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse)](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
