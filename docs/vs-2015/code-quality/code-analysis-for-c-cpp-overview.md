---
title: Übersicht über die Codeanalyse für C/C++ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
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
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 1ce41cd1c0dabc94658b83aa5e2bcdc08d005fdb
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275356"
---
# <a name="code-analysis-for-cc-overview"></a>Übersicht über die Codeanalyse für C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Codeanalysetool für C/C++ liefert Entwicklern Informationen zu möglichen Fehlern im C/C++-Quellcode. Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL-Zeigern sowie Speicher- und Ressourcenverluste.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integration in die integrierte Entwicklungsumgebung (Integrated Development Environment – IDE)  
 Damit Entwickler das Analysetool ohne Umwege nutzen können, wurde es vollständig in die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-IDE integriert. Während des Buildprozesses werden alle für den Quellcode generierten Warnungen in der Fehlerliste angezeigt. Sie können dadurch zu den Quellcodebestandteilen navigieren, die die Warnung ausgelöst haben, und zusätzliche Informationen zu den Gründen sowie mögliche Lösungen für die Probleme abrufen.  
  
## <a name="pragma-support"></a>#pragma-Unterstützung  
 Entwickler können die Anweisung `#pragma` verwenden, um Warnungen als Fehler zu behandeln, um Warnungen zu (de)aktivieren und um Warnungen für einzelne Codezeilen auszublenden. Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren und Deaktivieren der Codeanalyse für bestimmte C/C++-Warnungen](https://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Anmerkungsunterstützung  
 Mithilfe von Anmerkungen wird die Codeanalyse genauer. Sie enthalten zusätzliche Informationen zu Vorabbedingungen und nachträglichen Bedingungen für Funktionsparameter und Rückgabetypen. Weitere Informationen finden Sie unter [Vorgehensweise: Specify Additional Code Information by Using __analysis_assume (Vorgehensweise: Angeben zusätzlicher Codeinformationen mit „Using __analysis_assume“)](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Ausführen des Analysetools im Rahmen einer Eincheckrichtlinie  
 Möglicherweise möchten Sie festlegen, dass beim Quellcode-Check-In stets bestimmte Richtlinien beachtet werden müssen. Insbesondere sollten Sie sicherstellen, dass die Analyse im Rahmen des aktuellen lokalen Builds durchgeführt wurde. Weitere Informationen zum Aktivieren einer Eincheckrichtlinie für die Codeanalyse finden Sie unter [Creating and Using Code Analysis Check-In Policies (Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse)](../code-quality/creating-and-using-code-analysis-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Team Build-Integration  
 Sie können die in das Buildsystem integrierten Funktionen verwenden, um das Codeanalysetool im Rahmen des [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]-Buildprozesses auszuführen. Weitere Informationen finden Sie unter [Build the application (Erstellen der Anwendung)](/azure/devops/pipelines/index).  
  
## <a name="command-line-support"></a>Befehlszeilenunterstützung  
 Das Analysetool wurde nicht nur vollständig in die Entwicklungsumgebung integriert, sondern es kann von Entwicklern auch wie im folgenden Beispiel dargestellt über die Befehlszeile verwendet werden:  
  
 `C:\>cl /analyze Sample.cpp`
