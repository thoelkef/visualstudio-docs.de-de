---
title: "&#220;bersicht &#252;ber die Codeanalyse f&#252;r C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "#pragma-Direktiven, Codeanalyse"
  - "Anmerkungen, Codeanalyse"
  - "Buildintegration, Codeanalyse"
  - "C, Codeanalyse"
  - "C/C++-Codeanalyse"
  - "C++, Codeanalyse"
  - "Eincheckrichtlinien, Codeanalyse"
  - "Codeanalysetool"
  - "Codeanalyse, C/C++"
  - "Befehlszeile, Codeanalyse"
  - "IDE, Codeanalyse"
  - "pragma-Direktive, Codeanalyse"
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &#220;bersicht &#252;ber die Codeanalyse f&#252;r C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Codeanalysetool für C\/C\+\+ liefert Entwicklern Informationen zu möglichen Fehlern im C\/C\+\+\-Quellcode.  Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL\-Zeigern sowie Speicher\- und Ressourcenverluste.  
  
## Integration in die integrierte Entwicklungsumgebung \(Integrated Development Environment – IDE\)  
 Das Analysetool ist vollständig in die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE integriert, um den Entwicklern die Verwendung so leicht wie möglich zu machen.  Während des Buildprozesses werden alle für den Quellcode generierten Warnungen in der Fehlerliste angezeigt.  Sie können zum Quellcode navigieren, der die Warnung verursacht hat, und Sie können weitere Informationen zur Ursache und zu möglichen Problemlösungen anzeigen.  
  
## \#pragma\-Unterstützung  
 Mit der `#pragma`\-Direktive können Entwickler Warnungen als Fehler behandeln, Warnungen aktivieren oder deaktivieren sowie Warnungen für einzelne Codezeilen unterdrücken.  Weitere Informationen finden Sie unter [How to: Enable and Disable Code Analysis for Specific C\/C\+\+ Warnings](http://msdn.microsoft.com/de-de/910b8518-71f1-4b2e-b012-70647795642a).  
  
## Unterstützung von Anmerkungen  
 Durch Anmerkungen kann die Genauigkeit der Codeanalyse gesteigert werden.  Anmerkungen enthalten zusätzliche Informationen zu Vor\- und Nachbedingungen für Funktionsparameter und Rückgabetypen.  Weitere Informationen finden Sie unter [Gewusst wie: Angeben zusätzlicher Codeinformationen mit \_\_analysis\_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## Ausführen des Analysetools im Rahmen der Eincheckrichtlinien  
 Es kann sinnvoll sein, dass bei jedem Einchecken von Quellcode bestimmte Richtlinien beachtet werden müssen.  Möglicherweise möchten Sie vor allem sicherstellen, dass die Analyse als Schritt des letzten lokalen Builds ausgeführt wurde.  Weitere Informationen zum Aktivieren einer Eincheckrichtlinie für die Codeanalyse finden Sie unter [Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## Team Build\-Integration  
 Mit den integrierten Funktionen des Buildsystems können Sie das Codeanalysetool als Schritt des [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]\-Buildprozesses ausführen.  Weitere Informationen finden Sie unter [Erstellen der Anwendung](../Topic/Build%20the%20application.md).  
  
## Befehlszeilenunterstützung  
 Das Analysetool ist nicht nur vollständig in die Entwicklungsumgebung integriert, sondern kann auch über die Befehlszeile verwendet werden, wie im folgenden Beispiel gezeigt:  
  
 `C:\>cl /analyze Sample.cpp`