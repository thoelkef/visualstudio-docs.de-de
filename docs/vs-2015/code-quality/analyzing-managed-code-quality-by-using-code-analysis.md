---
title: Analysieren der Qualität von verwaltetem Code mit der Code Analyse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d5f0646f26226e9895414db512681e0a7a71faa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671120"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analysieren der Qualität von verwaltetem Code mit der Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Codeanalysetools in Visual Studio verwenden, um potenzielle Probleme im Code, wie z. B. nicht sicheren Datenzugriff, Verwendungsverstöße oder Probleme mit dem Entwurf, zu ermitteln. Die Codeanalyse funktioniert in .NET Framework-Anwendungen, systemeigenen Anwendungen (C und C++) und Datenbankanwendungen. Die Code Analyse für verwalteten Code organisiert Regeln in *Regelsätzen* , die bestimmte Codierungs Probleme als Ziel haben.

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Allgemeine Aufgaben|Unterstützender Inhalt|
|------------------|------------------------|
|**Praktische Übungen:** Erlernen Sie die Grundlagen der Code Analyse, indem Sie Fehler in einer einfachen .NET Framework Anwendung korrigieren.|-    Exemplarische Vorgehensweise[: Analysieren von verwaltetem Code auf Code Fehler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|
|**Konfigurieren Sie die Code Analyse für ein Projekt:** Regeln für verwalteten Code sind in Regelsätzen organisiert, die auf bestimmte Bereiche abzielen, z. b. Sicherheit und Entwurf. Sie können einen der Microsoft-Standardregelsätze verwenden oder einen eigenen Regelsatz erstellen.|[Übersicht über -    Code Analyse für verwalteten Code](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Verwenden von Regelsätzen zum Gruppieren von Code Analyse Regeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-    unter[drücken von Warnungen mithilfe des SuppressMessage-Attributs](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|
|**Code Analyse ausführen:** Sie können angeben, dass die Code Analyse bei der Erstellung einer Projekt Konfiguration automatisch ausgeführt werden soll, und Sie können die Code Analyse manuell in einem Projekt ausführen.|-    Gewusst[wie: Aktivieren und Deaktivieren der automatischen Code Analyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-    Gewusst[wie: Manuelles Ausführen der Code Analyse](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|
|**Code Analyseergebnisse analysieren:** Warnungen und Fehler in der Code Analyse werden im Fenster "Code Analyse" aufgeführt. Sie können den Titel einer Warnung oder eines Fehlers auswählen, um weitere Informationen zur Warnung anzuzeigen und um die Quellcodezeile anzuzeigen bzw. hervorzuheben, die die Regel ausgelöst hat. Sie können die ID der Warnung auswählen, um ausführliche Informationen in der MSDN Library anzuzeigen, die Informationen und Beispiele zur Behebung des Problems enthält.|-    Gewusst[wie: Anzeigen von Fehlern in verwaltetem Code](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Code Analyse für Warnungen für verwalteten Code](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Warnungen nach CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Anonyme Methoden und Code Analyse](../code-quality/anonymous-methods-and-code-analysis.md)|
|**Integrieren der Code Analyse in den Entwicklungs Lebenszyklus:** Check-in-Richtlinien in [!INCLUDE[esprscc](../includes/esprscc-md.md)] ermöglichen Entwicklungsteams, sicherzustellen, dass alle Code-Check-ins einen allgemeinen Satz von Code Analyse Standards erfüllen. Das Erstellen eines Arbeitselements für einen Verstoß gegen eine Codeanalyseregel ist eine einfache Prozedur, die Sie im Fenster „Fehlerliste“ ausführen können.|-   [verbessern der Code Qualität mit Eincheck Richtlinien für das Team Projekt](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-    Gewusst[wie: Synchronisieren von Code Projekt-Regelsätzen mit der Eincheck Richtlinie für Team Projekte](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-    Gewusst[wie: Erstellen einer Arbeitsaufgabe für einen Fehler in verwaltetem Code](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
