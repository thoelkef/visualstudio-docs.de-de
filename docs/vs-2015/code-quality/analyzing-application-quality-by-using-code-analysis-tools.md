---
title: Analyzing Application Quality by Using Code Analysis Tools | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8b85bbad909a05bacab361a49cc7e029482ad606
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291202"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analysieren der Anwendungsqualität mit Codeanalysetools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In This Section [Analyzing Managed Code Quality](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) Visual Studio code analysis for managed code provides information about managed assemblies, such as violations of the programming and design rules set forth in the Microsoft .NET Framework Design Guidelines. In diesen Warnmeldungen werden alle relevanten Probleme im Zusammenhang mit Programmierung und Entwurf benannt. Nach Möglichkeit wird außerdem angegeben, wie das jeweilige Problem gelöst werden kann.

 [Analyzing C/C++ Code Quality by Using Code Analysis](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) The C/C++ Code Analysis tool provides information to developers about possible defects in their C/C++ source code. Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL-Zeigern sowie Speicher- und Ressourcenverluste.

 [Using Rule Sets to Group Code Analysis Rules](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Select and create *rule sets* to apply to your project.

 [Code Analysis Application Errors](../code-quality/code-analysis-application-errors.md) Fix errors in the code analysis functionality.

 [Enhancing Code Quality with Team Project Check-in Policies](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) When you use Team Foundation Version Control (TFVC), you can create check-in policies for your team projects that enforce practices that lead to better code and more efficient group development. Eincheckrichtlinien sind Regeln, die auf Teamprojektebene festgelegt und auf Entwicklercomputern erzwungen werden, bevor Code eingecheckt werden kann.

### <a name="code-analysis-for-drivers"></a>Codeanalyse für Treiber
 Codeanalysetools können die Stabilität und Zuverlässigkeit des Treibers durch die systematische Analyse des Treiberquellcodes verbessern.

 [Analyzing Driver Quality by Using Code Analysis Tools](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) Code Analysis for Drivers is a compile-time static verification tool that detects basic coding errors in C and C++ programs and includes a specialized module that is designed to detect errors in (primarily) kernel-mode driver code. Der Static Driver Verifier (Statisches Treiber-Prüfmodul, SDV) ist ein statisches Überprüfungstool, das systematisch den Quellcode von Windows-Kernelmodustreibern analysiert. SDV ermittelt, ob der Treiber ordnungsgemäß mit dem Windows-Betriebssystemkernel interagiert.

 [Code Analysis for Drivers Warnings](https://go.microsoft.com/fwlink/?LinkId=225920) Describes the warnings that the Code Analysis for Drivers reports when it detects a possible error in driver code.

## <a name="related-tasks"></a>Verwandte Aufgaben
 [Measuring Complexity and Maintainability of Managed Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Insert description here.

 [Unit Test Your Code](../test/unit-test-your-code.md) Insert description here.
