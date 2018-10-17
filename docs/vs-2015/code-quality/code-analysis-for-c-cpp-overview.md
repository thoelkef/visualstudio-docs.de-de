---
title: Codeanalyse für C / C++-Übersicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
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
caps.latest.revision: 27
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 42de573efcc44437eddf0e7d098681d05c094131
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222039"
---
# <a name="code-analysis-for-cc-overview"></a>Übersicht über die Codeanalyse für C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Codeanalysetool für C/C++ liefert Entwicklern Informationen zu möglichen Fehlern im C/C++-Quellcode. Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL-Zeigern sowie Speicher- und Ressourcenverluste.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integration in die integrierte Entwicklungsumgebung (Integrated Development Environment – IDE)  
 Damit natürliche für Entwickler, die vom Analysetool verwenden können, es ist vollständig integriert in die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Während des Buildprozesses werden Sie alle Warnungen für den Quellcode generiert in der Fehlerliste angezeigt. Sie können auf den Quellcode, der die Warnung verursacht hat, navigieren, und sehen Sie weitere Informationen zu den Ursachen und mögliche Lösungen des Problems.  
  
## <a name="pragma-support"></a>#pragma-Unterstützung  
 Entwickler können mithilfe der `#pragma` Richtlinie Warnungen als Fehler behandeln, aktivieren oder Deaktivieren von Warnungen und Unterdrücken von Warnungen für einzelne Zeilen von Code. Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren und Deaktivieren von Codeanalyse für C/C++-Warnungen, die bestimmte](http://msdn.microsoft.com/en-us/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Unterstützung von Kommentaren  
 Anmerkungen verbessern, die Genauigkeit der Codeanalyse. Anmerkungen enthalten zusätzliche Informationen zu vorab und nachträglich Bedingungen zu Funktionsparametern und Rückgabetypen. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben zusätzlicher Codeinformationen mit __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Analysetool wird als Teil der Eincheckrichtlinie ausgeführt.  
 Sie möchten erfordern, dass Source Code Einchecken stets bestimmte Richtlinien beachtet werden. Insbesondere möchten Sie sicherstellen, dass die Analyse als Schritt von den neuesten lokalen Build ausgeführt wurde. Weitere Informationen zum Aktivieren der Eincheckrichtlinie für die Analyse finden Sie unter [erstellen und Verwenden von Code Codeanalyse-Eincheckrichtlinien](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Team Build-Integration  
 Sie können die integrierten Funktionen des Buildsystems verwenden, zur Ausführung von Code Analysetool als einen Schritt des der [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] Buildprozess. Weitere Informationen finden Sie unter [Build the application (Erstellen der Anwendung)](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Befehlszeilenunterstützung  
 Zusätzlich zu der vollständigen Integration in der Entwicklungsumgebung können Entwickler auch das Analysetool für die Befehlszeile verwenden, wie im folgenden Beispiel gezeigt:  
  
 `C:\>cl /analyze Sample.cpp`



