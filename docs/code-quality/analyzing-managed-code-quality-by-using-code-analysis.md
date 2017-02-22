---
title: "Analysieren der Qualit&#228;t von verwaltetem Code mit der Codeanalyse | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Codeanalyse, verwalteter Code"
  - "Analyse für verwalteten Code"
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Analysieren der Qualit&#228;t von verwaltetem Code mit der Codeanalyse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Codeanalysetools in Visual Studio verwenden, um potenzielle Probleme im Code, wie z. B. nicht sicheren Datenzugriff, Verwendungsverstöße oder Probleme mit dem Entwurf, zu ermitteln.  Die Codeanalyse funktioniert in .NET Framework\-Anwendungen, systemeigenen Anwendungen \(C und C\+\+\) und Datenbankanwendungen.  Die Codeanalyse für verwalteten Code organisiert Regeln in *Regelsätzen*, die auf bestimmte Codeprobleme abzielen.  
  
## Allgemeine Aufgaben  
  
|Allgemeine Aufgaben|Unterstützender Inhalt|  
|-------------------------|----------------------------|  
|**Praktische Übungen:** Erlernen Sie die Grundlagen der Codeanalyse, indem Sie Fehler in einer einfachen .NET Framework\-Anwendung beheben.|-   [Exemplarische Vorgehensweise: Analysieren von verwaltetem Code auf Codefehler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Konfigurieren Sie die Codeanalyse für ein Projekt:** Regeln für verwalteten Code sind in Regelsätzen organisiert, die auf bestimmte Bereiche abzielen, z. B. Sicherheit und Entwurf.  Sie können einen der Microsoft\-Standardregelsätze verwenden oder einen eigenen Regelsatz erstellen.|-   [Übersicht über die Analyse von verwaltetem Code](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Unterdrücken von Warnungen mithilfe des SuppressMessage\-Attributs](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Führen Sie die Codeanalyse aus:** Sie können angeben, dass die Codeanalyse automatisch jedes Mal ausgeführt wird, wenn eine Projektkonfiguration erstellt wird; Sie können die Codeanalyse auch manuell für ein Projekt ausführen.|-   [Gewusst wie: Aktivieren und Deaktivieren der automatischen Codeanalyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Gewusst wie: Manuelles Ausführen der Codeanalyse](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analysieren Sie die Ergebnisse der Codeanalyse:**Die Warnungen und Fehler der Codeanalyse sind im Fenster "Codeanalyse" aufgeführt.  Sie können den Titel einer Warnung oder eines Fehlers auswählen, um weitere Informationen zur Warnung anzuzeigen und um die Quellcodezeile anzuzeigen bzw. hervorzuheben, die die Regel ausgelöst hat.  Sie können die ID der Warnung auswählen, um ausführliche Informationen in der MSDN Library anzuzeigen, die Informationen und Beispiele zur Behebung des Problems enthält.|-   [Gewusst wie: Anzeigen von Fehlern in verwaltetem Code](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Warnungen bei der Analyse von verwaltetem Code](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Warnungen nach CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Anonyme Methoden und Codeanalyse](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Integrieren der Codeanalyse in den Entwicklungslebenszyklus:** Mithilfe der Eincheckrichtlinien von [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] können Entwicklungsteams sicherstellen, dass alle Eincheckvorgänge für Code allgemeinen Codeanalysestandards entsprechen.  Das Erstellen einer Arbeitsaufgabe für einen Verstoß gegen eine Codeanalyseregel ist eine einfache Prozedur, die Sie im Fenster "Fehlerliste" ausführen können.|-   [Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Gewusst wie: Synchronisieren der Regelsätze für Codeprojekte mit der Team Project\-Eincheckrichtlinie](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Gewusst wie: Erstellen einer Arbeitsaufgabe für einen Fehler in verwaltetem Code](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|