---
title: Codeanalyse für verwalteten Code in Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b7b992dadb703cf1c4f73830324e9934d7525645
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920456"
---
# <a name="overview-of-code-analysis-for-managed-code"></a>Übersicht über die Codeanalyse für verwalteten code

Visual Studio-2017 analysiert verwalteten Code auf zwei Arten: mit älteren *FxCop* statische Analyse des verwalteten Assemblys, und klicken Sie mit .NET Compiler Platform *Analysen*. Dieses Thema behandelt die FxCop-Analyse für statischen Code. Weitere Informationen zum Analysieren von Code mithilfe von .NET Compiler Platform-Analyzer finden Sie unter [Übersicht der Roslyn-Analyzern](../code-quality/roslyn-analyzers-overview.md).

Die Codeanalyse für verwalteten Code analysiert verwaltete Assemblys und erstellt einen Bericht mit Informationen zu diesen Assemblys, in dem z. B. Verletzungen der in den Microsoft .NET Framework-Entwurfsrichtlinien festgelegten Programmierungs- und Entwurfsregeln gemeldet werden.

Das Analysetool stellt die während einer Analyse durchgeführten Prüfungen als Warnmeldungen dar. In diesen Warnmeldungen werden alle relevanten Probleme im Zusammenhang mit Programmierung und Entwurf benannt. Nach Möglichkeit wird außerdem angegeben, wie das jeweilige Problem gelöst werden kann.

## <a name="ide-integrated-development-environment-integration"></a>Integration in die IDE (integrated Development Environment)

Codeanalyse kann manuell oder automatisch auf das Projekt ausgeführt werden.

Codeanalyse jedes Mal ausführen, die Sie ein Projekt erstellen möchten, wählen **Codeanalyse für Build aktivieren** auf der Eigenschaftenseite des Projekts. Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Codeanalyse manuell an einem Projekt ausführen, in der Menüleiste wählen **analysieren** > **Ausführen der Codeanalyse** > **Ausführen der Codeanalyse für \<Projekt >**.

## <a name="rule-sets"></a>Regelsätze

Codeanalyseregeln für verwalteten Code in gruppiert [-Regelsätze](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Sie können einen der Microsoft-Standardregelsätze verwenden oder Sie können [Erstellen eines benutzerdefinierten Regelsatzes](../code-quality/how-to-create-a-custom-rule-set.md) auf eine bestimmte Anforderung zu erfüllen.

## <a name="suppress-warnings"></a>Warnungen unterdrücken

Es kann häufig hilfreich sein anzugeben, dass eine Warnung nicht zutreffend ist. Entwickler und andere Personen, die später möglicherweise den Code überprüfen, wissen dann, dass eine Warnung untersucht und unterdrückt oder ignoriert wurde.

In der Quelle die Unterdrückung von Warnungen wird durch benutzerdefinierte Attribute implementiert. Fügen Sie zum Unterdrücken einer Warnung das Attribut `SuppressMessage` zum Quellcode hinzu, wie im folgenden Beispiel dargestellt:

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Weitere Informationen finden Sie unter [Unterdrücken von Warnungen](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Wenn Sie ein Projekt zu Visual Studio 2017 migrieren, können Sie mit einer großen Anzahl von Warnungen der Codeanalyse plötzlich Datenwachstums. Wenn Sie sich nicht bereit sind, korrigieren Sie die Warnungen und sofort produktiv werden soll, können Sie *Baseline* den Analyse-Zustand des Projekts. Aus der **analysieren** klicken Sie im Menü **Codeanalyse ausführen und aktive Probleme unterdrückt**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ausführen der Codeanalyse im Rahmen der Eincheckrichtlinien

In einer Organisation ist es sinnvoll festzulegen, dass beim Einchecken stets bestimmte Richtlinien beachtet werden müssen. Insbesondere die folgenden Richtlinien sollten eingehalten werden:

- Es gibt keine Erstellungsfehler im Code eingecheckt wird.

- Codeanalyse wird als Teil des neuesten Builds ausgeführt.

Die Einhaltung dieser Vorgaben können Sie durch das Definieren von Eincheckrichtlinien gewährleisten. Weitere Informationen finden Sie unter [Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Team Build-integration

Sie können die integrierten Funktionen des Buildsystems verwenden, um das Analysetool im Rahmen des Buildprozesses auszuführen. Weitere Informationen finden Sie unter [erstellen und freigeben (VSTS)](/vsts/build-release/index).

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Roslyn-Analyzern](../code-quality/roslyn-analyzers-overview.md)
- [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
