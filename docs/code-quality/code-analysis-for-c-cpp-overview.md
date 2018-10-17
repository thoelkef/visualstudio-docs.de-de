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
ms.openlocfilehash: 35f694d9cc397800249dd9b4acd86bf63d22ad93
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320708"
---
# <a name="code-analysis-for-cc-overview"></a>Codeanalyse für C/C++-Übersicht

Die C/C++-Codeanalysetool bietet Informationen zu möglichen Fehlern im C/C++-Quellcode. Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL-Zeigern sowie Speicher- und Ressourcenverluste. Das Tool kann auch ausgeführt Überprüfungen im Hinblick auf die [C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integration von IDE (integrierte Entwicklungsumgebung)

Das Codeanalysetool ist vollständig in Visual Studio-IDE integriert.

Während des Buildprozesses werden Sie alle Warnungen für den Quellcode generiert in der Fehlerliste angezeigt. Sie können auf den Quellcode, der die Warnung verursacht hat, navigieren, und sehen Sie weitere Informationen zu den Ursachen und mögliche Lösungen des Problems.

## <a name="command-line-support"></a>Befehlszeilenunterstützung

Sie können auch das Tool über die Befehlszeile verwenden, wie im folgenden Beispiel gezeigt:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 Version 15.7 und höher** können Sie das Tool über die Befehlszeile in beliebige Buildsysteme, einschließlich CMake ausführen.

## <a name="pragma-support"></a>#pragma-Unterstützung

Sie können die `#pragma` Richtlinie Warnungen als Fehler behandeln, aktivieren oder Deaktivieren von Warnungen und Unterdrücken von Warnungen für einzelne Zeilen von Code. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Codeanalyseeigenschaften für C/C++-Projekte](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Unterstützung von Kommentaren

Anmerkungen verbessern, die Genauigkeit der Codeanalyse. Anmerkungen enthalten zusätzliche Informationen zu vorab und nachträglich Bedingungen zu Funktionsparametern und Rückgabetypen. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben zusätzlicher Codeinformationen mit __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Analysetool wird als Teil der Eincheckrichtlinie ausgeführt.

Sie möchten erfordern, dass Source Code Einchecken stets bestimmte Richtlinien beachtet werden. Insbesondere möchten Sie sicherstellen, dass die Analyse als Schritt von den neuesten lokalen Build ausgeführt wurde. Weitere Informationen zum Aktivieren der Eincheckrichtlinie für die Analyse finden Sie unter [erstellen und Verwenden von Code Codeanalyse-Eincheckrichtlinien](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Team Build-integration

Sie können die integrierten Funktionen des Buildsystems verwenden, zur Ausführung von Code Analysetool als einen Schritt des der [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] Buildprozess. Weitere Informationen finden Sie unter [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Codeanalyse für C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Exemplarische Vorgehensweise: Analysieren von C/C++-Code auf Fehler](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Codeanalyse für C/C++-Warnungen](code-analysis-for-c-cpp-warnings.md)
- [Verwenden der Überprüfungen für C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [C++ Core Guidelines Überprüfungsprogramm Verweis](code-analysis-for-cpp-corecheck.md)
- [Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analysieren der Qualität von Treiber mit Codeanalysetools](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Codeanalyse für Treiberwarnungen](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
