---
title: "Analysieren der Qualität von verwaltetem Code mithilfe der Codeanalyse | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 2008ac649302d87cc2d45274de3fdb1981aa571d
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2018
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analysieren der Qualität von verwaltetem Code mit der Codeanalyse
Sie können die Codeanalysetools in Visual Studio verwenden, um potenzielle Probleme im Code, wie z. B. nicht sicheren Datenzugriff, Verwendungsverstöße oder Probleme mit dem Entwurf, zu ermitteln. Die Codeanalyse funktioniert in .NET Framework-Anwendungen, systemeigenen Anwendungen (C und C++) und Datenbankanwendungen. Codeanalyse für verwalteten Code organisiert Regeln in *-Regelsätze* , bestimmte Codeprobleme abzielen.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Allgemeine Aufgaben|Unterstützender Inhalt|  
|------------------|------------------------|  
|**Praktische Erfahrung:** Grundlagen der Codeanalyse durch Korrigieren von Fehlern in einer einfachen .NET Framework-Anwendung.|-   [Exemplarische Vorgehensweise: Analysieren von verwaltetem Code auf Codefehler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Konfigurieren der Codeanalyse für ein Projekt:** Regeln für verwalteten Code sind in Regelsätzen, die auf bestimmte Bereiche, z. B. Sicherheit und Entwurf abzielen organisiert. Sie können einen der Microsoft-Standardregelsätze verwenden oder einen eigenen Regelsatz erstellen.|-   [Codeanalyse für verwalteten Code (Übersicht)](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Mithilfe der Regel wird auf Gruppe von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Unterdrücken von Warnungen mithilfe des SuppressMessage-Attributs](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Ausführen der Codeanalyse:** können Sie angeben, Codeanalyse automatisch jedes Mal ausgeführt werden, die eine Projektkonfiguration erstellt wird, und Sie können Codeanalyse manuell ausführen, auf ein Projekt.|-   [Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Vorgehensweise: Manuelles Ausführen der Codeanalyse](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analysieren der Ergebnisse der Codeanalyse:** Fehler und Warnungen der Codeanalyse im codeanalysefenster aufgeführt sind. Sie können den Titel einer Warnung oder eines Fehlers auswählen, um weitere Informationen zur Warnung anzuzeigen und um die Quellcodezeile anzuzeigen bzw. hervorzuheben, die die Regel ausgelöst hat. Sie können die ID der Warnung auswählen, um ausführliche Informationen in der MSDN Library anzuzeigen, die Informationen und Beispiele zur Behebung des Problems enthält.|-   [Vorgehensweise: Anzeigen von Fehlern in verwaltetem Code](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Codeanalyse für verwalteten Code (Warnungen)](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Warnungen nach CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Anonyme Methoden und Codeanalyse](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Der Entwicklungslebenszyklus integriert Codeanalyse:** Eincheckrichtlinien in [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] Entwicklungsteams aktivieren, um sicherzustellen, dass der gesamte Eincheckvorgänge code einen gemeinsamen Satz von Code Analysis-Standards zu erfüllen. Das Erstellen eines Arbeitselements für einen Verstoß gegen eine Codeanalyseregel ist eine einfache Prozedur, die Sie im Fenster „Fehlerliste“ ausführen können.|-   [Verbessern der Codequalität mit der Team Project in der Eincheckrichtlinien](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Vorgehensweise: Synchronisieren der Regelsätze für Codeprojekte mit der Team Project-Eincheckrichtlinie](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Vorgehensweise: Erstellen einer Arbeitsaufgabe für einen Fehler in verwaltetem Code](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|