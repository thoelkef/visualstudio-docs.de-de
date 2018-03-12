---
title: Mithilfe der Regel wird auf Gruppe Codeanalyseregeln | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 265ca57904cb47c52ecaf6ba260e726da9b8a063
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2018
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln

Wenn Sie die Codeanalyse in Visual Studio konfigurieren, können Sie auswählen, aus einer Liste von integrierten Microsoft *-Regelsätze*. Ein Regelsatz ist eine logische Gruppierung von Codeanalyseregeln, die gezielte Probleme und bestimmte Bedingungen identifizieren. Beispielsweise können Sie einen Regelsatz, der mit dem Code auf öffentlich verfügbare APIs überprüft anwenden, oder Sie können einen Regelsatz, der nur die empfohlenen Mindestregeln enthält anwenden. Sie können auch einen Regelsatz anwenden, der alle Regeln enthält.

Sie können anpassen ein Regelsatzes durch Hinzufügen oder Löschen von Regeln oder durch Ändern der Regeln angezeigt werden die **Fehlerliste** -Fenster als Warnungen oder Fehler. Benutzerdefinierte Regelsätze können Sie an Ihre spezielle Entwicklungsumgebung anpassen. Beim Anpassen eines Regelsatzes finden Sie auf der Regelsatzseite hilfreiche Such- und Filtertools.

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Praktische Erfahrung:** die Codeanalysetools Geben Sie eine benutzerdefinierte Regel legen Sie zum Suchen und Beheben von Problemen in einer einfachen .NET Framework-Anwendung verwenden.|- [Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Konfigurieren der Codeanalyse für ein Projekt:** wählen Sie einen vorhandenen Regelsatz für ein Projekt, eine Website oder eine Projektmappe.|- [Vorgehensweise: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />- [Verwenden von Regelsätzen an die C++-Regeln für die Ausführung](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />- [Vorgehensweise: Konfigurieren der Codeanalyse für eine ASP.NET-Webanwendung](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />- [Vorgehensweise: Angeben von Regelsätzen für mehrere Projekte in einer Projektmappe](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Anpassen eines Regelsatzes:** Geben Sie Regeln, um auf Ihr Projekt anzuwenden.|- [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Verstehen der integrierten Regelsätze:** Codeanalyseregeln, aus denen die integrierten Regelsätze anzeigen.|- [Regel zur Codeanalyse festlegen Verweis.](../code-quality/code-analysis-rule-set-reference.md)|
|**Codeanalyse in Team Foundation Server zu integrieren:** [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] Einchecken Richtlinien aktivieren Softwareentwicklungsteams messbar, um sicherzustellen, dass Sie Code Einchecken stets einen gemeinsamen Satz von Code Analysis-Standards zu erfüllen.|- [Vorgehensweise: Synchronisieren der Regelsätze für Codeprojekte mit der Team Project-Eincheckrichtlinie](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|