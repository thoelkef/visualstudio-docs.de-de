---
title: Analysieren der Qualität von verwaltetem Code mithilfe von Codeanalyse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d8740b79b026ade7f3da19aa4a89cacd94df17d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157121"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analysieren der Qualität von verwaltetem Code mit der Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Codeanalysetools in Visual Studio verwenden, um potenzielle Probleme im Code, wie z. B. nicht sicheren Datenzugriff, Verwendungsverstöße oder Probleme mit dem Entwurf, zu ermitteln. Die Codeanalyse funktioniert in .NET Framework-Anwendungen, systemeigenen Anwendungen (C und C++) und Datenbankanwendungen. Codeanalyse für verwalteten Code organisiert Regeln in *-Regelsätze* , auf bestimmte Codeprobleme abzielen.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Allgemeine Aufgaben|Unterstützender Inhalt|  
|------------------|------------------------|  
|**Praktische Übungen zu erhalten:** Grundlagen der Codeanalyse Korrigieren von Fehlern in einer einfachen .NET Framework-Anwendung.|-   [Exemplarische Vorgehensweise: Analysieren von verwaltetem Code im Hinblick auf Codefehler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Konfigurieren der Codeanalyse für ein Projekt:** Regeln für verwalteten Code sind in Regelsätzen organisiert, die auf bestimmte Bereiche, z. B. Sicherheit und Entwurf abzielen. Sie können einen der Microsoft-Standardregelsätze verwenden oder einen eigenen Regelsatz erstellen.|-   [Codeanalyse für verwalteten Code (Übersicht)](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Mithilfe der Regel wird auf die Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Unterdrücken von Warnungen mithilfe des SuppressMessage-Attributs](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Codeanalyse ausführen:** Sie können angeben, dass die Codeanalyse automatisch jedes Mal ausgeführt wird, die eine Projektkonfiguration erstellt wurde, und Sie können die Codeanalyse für ein Projekt manuell ausführen.|-   [Vorgehensweise: Enable and Disable Automatic Code Analysis (Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse)](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Vorgehensweise: Manuelles Ausführen der Codeanalyse](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analysieren Sie die Ergebnisse der Codeanalyse:** Fehler und Warnungen der Codeanalyse werden im Fenster "Codeanalyse" aufgeführt. Sie können den Titel einer Warnung oder eines Fehlers auswählen, um weitere Informationen zur Warnung anzuzeigen und um die Quellcodezeile anzuzeigen bzw. hervorzuheben, die die Regel ausgelöst hat. Sie können die ID der Warnung auswählen, um ausführliche Informationen in der MSDN Library anzuzeigen, die Informationen und Beispiele zur Behebung des Problems enthält.|-   [Vorgehensweise: Anzeigen von Fehlern in verwaltetem Code](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Codeanalyse für verwalteten Code (Warnungen)](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Warnungen nach CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Anonyme Methoden und Codeanalyse](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Integrieren Sie Codeanalyse und Ihren Entwicklungszyklus:** Check-in-Richtlinien in [!INCLUDE[esprscc](../includes/esprscc-md.md)] können Entwicklungsteams sicherstellen, dass alle Eincheckvorgänge code erfüllt einen gemeinsamen Satz von Codeanalysestandards entsprechen. Das Erstellen eines Arbeitselements für einen Verstoß gegen eine Codeanalyseregel ist eine einfache Prozedur, die Sie im Fenster „Fehlerliste“ ausführen können.|-   [Verbessern der Codequalität mit der Team Project Check-in-Richtlinien](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Vorgehensweise: Synchronisieren der Regelsätze für Codeprojekte mit der Team Project-Eincheckrichtlinie](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Vorgehensweise: Erstellen eines Arbeitselements für einen Fehler in verwaltetem Code](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
