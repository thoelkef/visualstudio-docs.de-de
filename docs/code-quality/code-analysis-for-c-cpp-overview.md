---
title: Übersicht über die Codeanalyse für C/C++
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: ea576ba794350e6cee6b20f8ef9adb62f82a9c51
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031565"
---
# <a name="code-analysis-for-cc-overview"></a>Codeanalyse für C/C++-Übersicht

Die C/C++-Codeanalysetool bietet Informationen zu möglichen Fehlern im C/C++-Quellcode. Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL-Zeigern sowie Speicher- und Ressourcenverluste. Ausführen des Tools kann auch Überprüfungen für die [C++ Core Richtlinien](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integration in die IDE (integrated Development Environment)

Das Codeanalysetool ist vollständig in Visual Studio-IDE integriert.

Werden Sie während des Buildprozesses für den Quellcode generierten Warnungen in der Fehlerliste angezeigt. Sie können navigieren, auf den Quellcode, die die Warnung verursacht hat, und können Sie zusätzliche Informationen über die Ursache und mögliche Lösungen des Problems anzeigen.

## <a name="command-line-support"></a>Befehlszeilenunterstützung

Sie können auch das Analysetool über die Befehlszeile verwenden, wie im folgenden Beispiel gezeigt:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 15.7 und höher** können Sie das Tool über die Befehlszeile mit jedem Buildsystem, einschließlich CMake ausführen.

## <a name="pragma-support"></a>#pragma-Unterstützung

Sie können die `#pragma` Richtlinie Warnungen als Fehler behandeln; aktivieren oder Deaktivieren von Warnungen und Unterdrücken von Warnungen für die einzelnen Codezeilen. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Codeanalyseeigenschaften für C/C++-Projekte](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Unterstützung von Kommentaren

Anmerkungen verbessern, die Genauigkeit für die Codeanalyse. Anmerkungen enthalten zusätzliche Informationen zu vorab und nachträglich Bedingungen zum Funktionsparameter und Rückgabetypen. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben zusätzlicher Codeinformationen mit __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Ausführen von Analysetool im Rahmen der Eincheckrichtlinie

Möglicherweise möchten erfordern, dass Source Code Einchecken stets bestimmte Richtlinien beachtet werden. Insbesondere, möchten Sie sicherstellen, dass der Analyse als Schritt des letzten lokalen Builds ausgeführt wurde. Weitere Informationen zum Aktivieren der Eincheckrichtlinie für die Analyse finden Sie unter [erstellen und Verwenden von Code Analysis-Eincheckrichtlinien](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Team Build-integration

Sie können die integrierten Funktionen des Buildsystems verwenden, um Codeanalysetool als einem Schritt ausgeführt der [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] Buildprozess. Weitere Informationen finden Sie unter [Build and release](/vsts/build-release/index) (Build und Release).

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Codeanalyse für C/C++-](quick-start-code-analysis-for-c-cpp.md)
- [Exemplarische Vorgehensweise: Analysieren von C/C++-Code für Fehler](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Codeanalyse für C/C++-Warnungen](code-analysis-for-c-cpp-warnings.md)
- [Verwenden der Überprüfungen für C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [C++-Core-Richtlinien Überprüfungsprogramm Verweis](code-analysis-for-cpp-corecheck.md)
- [Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analysieren der Qualität von Treiber mit Codeanalysetools](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Codeanalyse für Treiberwarnungen](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
