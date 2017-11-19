---
title: "Codeanalyse für C/C++-Übersicht | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 55b1f4061d408187525c255e4ab12c3fe93eb60e
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="code-analysis-for-cc-overview"></a>Übersicht über die Codeanalyse für C/C++
Das Codeanalysetool für C/C++ liefert Entwicklern Informationen zu möglichen Fehlern im C/C++-Quellcode. Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL-Zeigern sowie Speicher- und Ressourcenverluste.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integration in die integrierte Entwicklungsumgebung (Integrated Development Environment – IDE)  
 Um die natürliche für Entwickler verwenden das Analysetool gestalten, wird er vollständig innerhalb integriert die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Werden Sie während des Buildprozesses für den Quellcode generierten Warnungen in der Fehlerliste angezeigt. Sie können navigieren, auf den Quellcode, die die Warnung verursacht hat, und können Sie zusätzliche Informationen über die Ursache und mögliche Lösungen des Problems anzeigen.  
  
## <a name="pragma-support"></a>#pragma-Unterstützung  
 Entwickler können mithilfe der `#pragma` Richtlinie Warnungen als Fehler behandeln; aktivieren oder Deaktivieren von Warnungen und Unterdrücken von Warnungen für die einzelnen Codezeilen. Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren und Deaktivieren der Codeanalyse für C/C++-Warnungen, die bestimmte](http://msdn.microsoft.com/en-us/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Unterstützung von Kommentaren  
 Anmerkungen verbessern, die Genauigkeit für die Codeanalyse. Anmerkungen enthalten zusätzliche Informationen zu vorab und nachträglich Bedingungen zum Funktionsparameter und Rückgabetypen. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben zusätzlicher Codeinformationen mit __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Ausführen von Analysetool im Rahmen der Eincheckrichtlinie  
 Möglicherweise möchten erfordern, dass Source Code Einchecken stets bestimmte Richtlinien beachtet werden. Insbesondere, möchten Sie sicherstellen, dass der Analyse als Schritt des letzten lokalen Builds ausgeführt wurde. Weitere Informationen zum Aktivieren der Eincheckrichtlinie für die Analyse finden Sie unter [erstellen und Verwenden von Code Analysis-Eincheckrichtlinien](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Team Build-Integration  
 Sie können die integrierten Funktionen des Buildsystems verwenden, um Codeanalysetool als einem Schritt ausgeführt der [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] Buildprozess. Weitere Informationen finden Sie unter [Build the application (Erstellen der Anwendung)](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Befehlszeilen-Unterstützung  
 Zusätzlich zu der vollständigen Integration in der Entwicklungsumgebung können Entwickler auch das Analysetool über die Befehlszeile verwenden, wie im folgenden Beispiel gezeigt:  
  
 `C:\>cl /analyze Sample.cpp`