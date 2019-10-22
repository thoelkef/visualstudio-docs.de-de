---
title: Analysieren der Anwendungsqualität mit Code Analyse Tools | Microsoft-Dokumentation
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
ms.openlocfilehash: c0b46c8efb681a067d5a9e74369ed73c43f1568f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671104"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analysieren der Anwendungsqualität mit Codeanalysetools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Abschnitt wird die [Qualität der Qualität von verwaltetem Code analysiert](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) : Visual Studio-Code Analyse für verwalteten Code stellt Informationen zu verwalteten Assemblys bereit, z. b. Verstöße gegen die Programmier-und Entwurfs Regeln, die im Microsoft .net Richtlinien. In diesen Warnmeldungen werden alle relevanten Probleme im Zusammenhang mit Programmierung und Entwurf benannt. Nach Möglichkeit wird außerdem angegeben, wie das jeweilige Problem gelöst werden kann.

 [Analysieren der cC++ /Code-Qualität mithilfe der Code Analyse](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) dasC++ c/Code-Analysetool stellt Entwicklern Informationen zu möglichen Fehlern im cC++ /Quellcode-Code zur Verfügung. Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL-Zeigern sowie Speicher- und Ressourcenverluste.

 [Verwenden von Regelsätzen zum Gruppieren von Code Analyse Regeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Wählen Sie die *Regelsätze* aus, die auf das Projekt angewendet werden

 [Anwendungsfehler bei der Code Analyse](../code-quality/code-analysis-application-errors.md) Beheben Sie Fehler in der Code Analysefunktion.

 [Verbessern der Code Qualität mit Eincheck Richtlinien für das Team Projekt](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) Wenn Sie Team Foundation-Versionskontrolle (tfvc) verwenden, können Sie Eincheck Richtlinien für Team Projekte erstellen, die Methoden erzwingen, die zu besserer Code und effizienterer Gruppenentwicklung führen. Eincheckrichtlinien sind Regeln, die auf Teamprojektebene festgelegt und auf Entwicklercomputern erzwungen werden, bevor Code eingecheckt werden kann.

### <a name="code-analysis-for-drivers"></a>Codeanalyse für Treiber
 Codeanalysetools können die Stabilität und Zuverlässigkeit des Treibers durch die systematische Analyse des Treiberquellcodes verbessern.

 [Analysieren der Treiber Qualität mithilfe von Code Analyse Tools](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) Die Code Analyse für Treiber ist ein statisches Überprüfungs Tool zur Kompilierzeit, das grundlegende Codierungsfehler in C und C++ Programmen erkennt und ein spezielles Modul umfasst, das zum Erkennen von Fehlern in (hauptsächlich) Kernelmodustreiber-Code konzipiert ist. Der Static Driver Verifier (Statisches Treiber-Prüfmodul, SDV) ist ein statisches Überprüfungstool, das systematisch den Quellcode von Windows-Kernelmodustreibern analysiert. SDV ermittelt, ob der Treiber ordnungsgemäß mit dem Windows-Betriebssystemkernel interagiert.

 [Code Analyse für Treiber Warnungen](http://go.microsoft.com/fwlink/?LinkId=225920) Beschreibt die Warnungen, die die Code Analyse für Treiber meldet, wenn ein möglicher Fehler im Treiber Code erkannt wird.

## <a name="related-tasks"></a>Verwandte Aufgaben
 [Messen von Komplexität und Verwaltbarkeit von verwaltetem Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Beschreibung hier einfügen.

 Komponenten [Tests für Ihren Code](../test/unit-test-your-code.md) Beschreibung hier einfügen.
