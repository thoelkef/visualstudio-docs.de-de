---
title: Übersicht über die Codeanalyse für C/C++
ms.date: 04/28/2018
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 5c4221783768f1e579ecad74fdfaf6e74214edfd
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226136"
---
# <a name="code-analysis-for-cc-overview"></a>Übersicht über die Codeanalyse für C/C++

Die C/C++-Codeanalysetool bietet Informationen zu möglichen Fehlern im C/C++-Quellcode. Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL-Zeigern sowie Speicher- und Ressourcenverluste. Das Tool kann auch ausgeführt Überprüfungen im Hinblick auf die [C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integration von IDE (integrierte Entwicklungsumgebung)

Das Codeanalysetool ist vollständig in Visual Studio-IDE integriert.

Während des Buildprozesses werden alle für den Quellcode generierten Warnungen in der Fehlerliste angezeigt. Sie können dadurch zu den Quellcodebestandteilen navigieren, die die Warnung ausgelöst haben, und zusätzliche Informationen zu den Gründen sowie mögliche Lösungen für die Probleme abrufen.

## <a name="command-line-support"></a>Befehlszeilenunterstützung

Sie können auch das Tool über die Befehlszeile verwenden, wie im folgenden Beispiel gezeigt:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 Version 15.7 und höher** können Sie das Tool über die Befehlszeile in beliebige Buildsysteme, einschließlich CMake ausführen.

## <a name="pragma-support"></a>#pragma-Unterstützung

Sie können die `#pragma` Richtlinie Warnungen als Fehler behandeln, aktivieren oder Deaktivieren von Warnungen und Unterdrücken von Warnungen für einzelne Zeilen von Code. Weitere Informationen finden Sie unter [Pragma-Direktiven und das __Pragma-Schlüsselwort](https://docs.microsoft.com/cpp/preprocessor/pragma-directives-and-the-pragma-keyword).

## <a name="annotation-support"></a>Unterstützung von Kommentaren

Mithilfe von Anmerkungen wird die Codeanalyse genauer. Sie enthalten zusätzliche Informationen zu Vorabbedingungen und nachträglichen Bedingungen für Funktionsparameter und Rückgabetypen. Weitere Informationen finden Sie unter [mithilfe von Microsoft SAL-Anmerkungen zum Reduzieren von C /C++ Codefehler](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Ausführen des Analysetools im Rahmen einer Eincheckrichtlinie

Möglicherweise möchten Sie festlegen, dass beim Quellcode-Check-In stets bestimmte Richtlinien beachtet werden müssen. Insbesondere sollten Sie sicherstellen, dass die Analyse im Rahmen des aktuellen lokalen Builds durchgeführt wurde. Weitere Informationen zum Aktivieren einer Eincheckrichtlinie für die Codeanalyse finden Sie unter [Creating and Using Code Analysis Check-In Policies (Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse)](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Team Build-integration

Sie können die in das Buildsystem integrierten Funktionen verwenden, um das Codeanalysetool im Rahmen des [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]-Buildprozesses auszuführen. Weitere Informationen finden Sie unter [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Codeanalyse für C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Exemplarische Vorgehensweise: Analysieren von C/C++-Code auf Fehler](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Codeanalyse für C/C++-Warnungen](code-analysis-for-c-cpp-warnings.md)
- [Verwenden der Überprüfungen für C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [C++ Core Guidelines Überprüfungsprogramm Verweis](code-analysis-for-cpp-corecheck.md)
- [Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analysieren der Qualität von Treiber mit Codeanalysetools](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Codeanalyse für Treiberwarnungen](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
