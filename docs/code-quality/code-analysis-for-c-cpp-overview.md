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
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 515b9b7eb1b1a4d2dbee6329be782386b8370338
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806309"
---
# <a name="code-analysis-for-cc-overview"></a>Übersicht über die Codeanalyse für C/C++

Das c/C++ Code Analysis-Tool stellt Informationen zu möglichen Fehlern in Ihrem cC++ /Quellcode-Code bereit. Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL-Zeigern sowie Speicher- und Ressourcenverluste. Das Tool kann auch Überprüfungen anhand der [ C++ wichtigsten Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)ausführen.

## <a name="ide-integrated-development-environment-integration"></a>Integration der IDE (integrierte Entwicklungsumgebung)

Das Code Analysetool ist vollständig in die Visual Studio-IDE integriert.

Während des Buildprozesses werden alle für den Quellcode generierten Warnungen in der Fehlerliste angezeigt. Sie können dadurch zu den Quellcodebestandteilen navigieren, die die Warnung ausgelöst haben, und zusätzliche Informationen zu den Gründen sowie mögliche Lösungen für die Probleme abrufen.

## <a name="command-line-support"></a>Befehlszeilen Unterstützung

Sie können das Analysetool auch über die Befehlszeile verwenden, wie im folgenden Beispiel gezeigt:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 Version 15,7 und höher:** Sie können das Tool in der Befehlszeile mit jedem Buildsystem ausführen, einschließlich cmake.

## <a name="pragma-support"></a>#pragma Unterstützung

Sie können die `#pragma`-Direktive verwenden, um Warnungen als Fehler zu behandeln. Aktivieren oder deaktivieren Sie Warnungen, und unterdrücken Sie Warnungen für einzelne Codezeilen. Weitere Informationen finden Sie unter [Pragma-Direktiven und das __Pragma-Schlüsselwort](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword).

## <a name="annotation-support"></a>Unterstützung der Anmerkung

Mithilfe von Anmerkungen wird die Codeanalyse genauer. Sie enthalten zusätzliche Informationen zu Vorabbedingungen und nachträglichen Bedingungen für Funktionsparameter und Rückgabetypen. Weitere Informationen finden Sie unter [Verwenden von Sal-Anmerkungen zum Reduzieren vonC++ C/Code-Fehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md).

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Ausführen des Analysetools im Rahmen einer Eincheckrichtlinie

Möglicherweise möchten Sie festlegen, dass beim Quellcode-Check-In stets bestimmte Richtlinien beachtet werden müssen. Insbesondere sollten Sie sicherstellen, dass die Analyse im Rahmen des aktuellen lokalen Builds durchgeführt wurde. Weitere Informationen zum Aktivieren einer Eincheck Richtlinie für die Code Analyse finden Sie unter [Erstellen und Verwenden von Eincheck Richtlinien für die Code Analyse](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Team Build-Integration

Sie können die in das Buildsystem integrierten Funktionen verwenden, um das Codeanalysetool im Rahmen des [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]-Buildprozesses auszuführen. Weitere Informationen finden Sie unter [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Code Analyse für C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Exemplarische Vorgehensweise: analysierenC++ von C/Code auf Fehler](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Codeanalyse für C/C++-Warnungen](code-analysis-for-c-cpp-warnings.md)
- [Verwenden der Überprüfungen für C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [C++Referenz zu Kern Richtlinien Prüfung](code-analysis-for-cpp-corecheck.md)
- [Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analysieren der Treiber Qualität mithilfe von Code Analyse Tools](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Code Analyse für Treiber Warnungen](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
