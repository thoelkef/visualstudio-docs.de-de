---
title: "Verwenden von Regels&#228;tzen zum Gruppieren von Codeanalyseregeln | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.rulesets.learnmore"
helpviewer_keywords: 
  - "Codeanalyse, Regelsätze"
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 36
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 36
---
# Verwenden von Regels&#228;tzen zum Gruppieren von Codeanalyseregeln
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Konfigurieren der Codeanalyse in [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] oder [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]steht Ihnen eine Liste mit integrierten *Regelsätzen* von Microsoft zur Verfügung.  Ein Regelsatz ist eine logische Gruppierung von Codeanalyseregeln, die gezielte Probleme und bestimmte Bedingungen identifizieren.  Sie können z. B. einen Regelsatz anwenden, mit dem Code auf öffentlich verfügbare APIs überprüft wird, oder einen Regelsatz, der nur die empfohlenen Mindestregeln enthält.  Sie können auch einen Regelsatz anwenden, der alle Regeln enthält.  
  
 Sie können einen Regelsatz anpassen, indem Sie Regeln hinzufügen oder löschen, oder indem Sie Regeln so ändern, dass sie im Fenster **Fehlerliste** entweder als Warnungen oder als Fehler angezeigt werden.  Benutzerdefinierte Regelsätze können Sie an Ihre spezielle Entwicklungsumgebung anpassen.  Beim Anpassen eines Regelsatzes finden Sie auf der Regelsatzseite hilfreiche Such\- und Filtertools.  
  
## Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|**Praktische Übung:** Mithilfe der Codeanalysetools können Sie einen benutzerdefinierten Regelsatz angeben, um Probleme in einer einfachen .NET Framework\-Anwendung zu suchen und zu beheben.|-   [Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**Konfigurieren der Codeanalyse für ein Projekt:** Wählen Sie für ein Projekt, eine Website oder eine Projektmappe einen vorhandenen Regelsatz aus.|-   [Gewusst wie: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Verwenden von Regelsätzen zum Festlegen von C\+\+\-Regeln für die Ausführung](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Gewusst wie: Konfigurieren der Codeanalyse für eine ASP.NET\-Anwendung](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Gewusst wie: Angeben von Regelsätzen für mehrere Projekte in einer Projektmappe](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**Anpassen eines Regelsatzes:** Geben Sie Regeln an, die für das Projekt übernommen werden sollen.|-   [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**Grundlegendes zu integrierten Regelsätzen:** Zeigen Sie die Codeanalyseregeln an, aus denen die integrierten Regelsätze bestehen.|-   [Codeanalyse\-Regelsatzreferenz](../code-quality/code-analysis-rule-set-reference.md)|  
|**Integrieren der Codeanalyse in Team Foundation Server:** Mithilfe der [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]\-Eincheckrichtlinien können Entwicklerteams sicherstellen, dass alle Eincheckvorgänge für Code allgemeinen Codeanalysestandards entsprechen.|-   [Gewusst wie: Synchronisieren der Regelsätze für Codeprojekte mit der Team Project\-Eincheckrichtlinie](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|