---
title: Analysieren der Anwendungsqualität mit Codeanalysetools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1b62ac482d18bc8844045d90d32f4d48416daeca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515012"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analysieren der Anwendungsqualität mit Codeanalysetools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Analysieren der Anwendungsqualität mit Codeanalysetools](https://docs.microsoft.com/visualstudio/code-quality/analyzing-application-quality-by-using-code-analysis-tools).  
  
In diesem Abschnitt  
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 Die Visual Studio Codeanalyse für verwalteten Code stellt Informationen zu verwalteten Assemblys bereit, z. B. über Verletzungen der in den Microsoft .NET Framework-Entwurfsrichtlinien dargelegten Programmierungs- und Entwurfsregeln. In diesen Warnmeldungen werden alle relevanten Probleme im Zusammenhang mit Programmierung und Entwurf benannt. Nach Möglichkeit wird außerdem angegeben, wie das jeweilige Problem gelöst werden kann.  
  
 [Analysieren der Qualität von C/C++-Code mit der Codeanalyse](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md)  
 Das Codeanalysetool für C/C++ liefert Entwicklern Informationen zu möglichen Fehlern im C/C++-Quellcode. Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL-Zeigern sowie Speicher- und Ressourcenverluste.  
  
 [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)  
 Wählen Sie aus, und erstellen Sie *-Regelsätze* zu Ihrem Projekt anwenden.  
  
 [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)  
 Beheben Sie Fehler in der Codeanalysefunktion.  
  
 [Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)  
 Mit Team Foundation-Versionskontrolle (TFVC) können Sie Eincheckrichtlinien für Teamprojekte erstellen, um Vorgehensweisen für die Erstellung besseren Codes und eine effizientere Gruppenentwicklung zu erzwingen. Eincheckrichtlinien sind Regeln, die auf Teamprojektebene festgelegt und auf Entwicklercomputern erzwungen werden, bevor Code eingecheckt werden kann.  
  
### <a name="code-analysis-for-drivers"></a>Codeanalyse für Treiber  
 Codeanalysetools können die Stabilität und Zuverlässigkeit des Treibers durch die systematische Analyse des Treiberquellcodes verbessern.  
  
 [Analysieren der Treiberqualität mit Codeanalysetools](http://go.microsoft.com/fwlink/?LinkId=227618)  
 Die Codeanalyse für Treiber ist ein statisches Überprüfungstool zur Kompilierzeit, das grundlegende Codierungsfehler in C- und C++-Programmen erkennt. Sie enthält ein spezialisiertes Modul zur Erkennung von Fehlern im (hauptsächlichen) Kernelmodustreibercode. Der Static Driver Verifier (Statisches Treiber-Prüfmodul, SDV) ist ein statisches Überprüfungstool, das systematisch den Quellcode von Windows-Kernelmodustreibern analysiert. SDV ermittelt, ob der Treiber ordnungsgemäß mit dem Windows-Betriebssystemkernel interagiert.  
  
 [Codeanalyse für Treiberwarnungen](http://go.microsoft.com/fwlink/?LinkId=225920)  
 Beschreibt die Warnungen, die die Codeanalyse für Treiber meldet, wenn ein möglicher Fehler im Treibercode erkannt wird.  
  
## <a name="related-tasks"></a>Verwandte Aufgaben  
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)  
 Beschreibung hier einfügen.  
  
 [Komponententest für Code](../test/unit-test-your-code.md)  
 Beschreibung hier einfügen.



