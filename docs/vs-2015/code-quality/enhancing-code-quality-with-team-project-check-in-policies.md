---
title: Verbessern der Codequalität mit der Team Project Check-in-Richtlinien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 31859128aed64ec6a1182f085685b2e82e485f84
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437071"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Team Foundation-Versionskontrolle (TFVC) verwenden, können Sie Eincheckrichtlinien für Teamprojekte erstellen, um Vorgehensweisen für besseren Code und eine effizientere Gruppenentwicklung zu erzwingen. Eincheckrichtlinien sind Regeln, die auf Teamprojektebene festgelegt und auf Entwicklercomputern erzwungen werden, bevor Code eingecheckt werden kann.  
  
 Sie können diese Eincheckrichtlinien für das Teamprojekt angeben:  
  
- **Builds**: Erfordert, dass Buildunterbrechungen, die während eines Builds erstellt wurden, die vor einem neuen Einchecken korrigiert werden müssen.  
  
- **Changeset-Kommentare**: Erfordert, dass Benutzer beim Einchecken von Änderungen Kommentare eingeben.  
  
- **Codeanalyse**: Erfordert, dass die Codeanalyse vor dem Einchecken ausgeführt wird.  
  
- **Typen von Arbeitselementen**: Erfordert, dass eine oder mehrere Arbeitsaufgaben mit dem Eincheckvorgang verknüpft werden.  
  
> [!IMPORTANT]
> Eincheckrichtlinien können nur verwendet werden, wenn eine Verbindung mit [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)]besteht.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Unterstützender Inhalt|  
|----------|------------------------|  
|**Erstellen Sie und verwenden Sie die Check-in-Richtlinien:** Sie erstellen die Check-in-Richtlinien mit den Teamprojekteinstellungen von [!INCLUDE[esprscc](../includes/esprscc-md.md)].|[Festlegen und Erzwingen von Quality Gates](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Erstellen und Verwenden von Eincheckrichtlinien für die Analyse:** Sie können aus einem Standardsatz von Codeanalyseregeln auswählen, oder Sie können einen benutzerdefinierten Satz erstellen.|[Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>Verwandte Aufgaben  
  
|Aufgabe|Unterstützender Inhalt|  
|----------|------------------------|  
|**Richten Sie Ihre Entwicklungsumgebung:** Bevor Sie können Code erstellen oder ändern, müssen Sie richten Sie Ihre Entwicklung und testumgebungen mit dem entsprechenden Quellcode. Wenn Sie Datenbanken verwenden, benötigen Sie außerdem Zugriff auf die Offlinedarstellung der Datenbanken.|[Einrichten von Entwicklungsumgebungen](http://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Verwenden Sie Codeanalyse im Entwicklungsprozess:** Teammitglieder führen die Codeanalyse auf ihren Entwicklungscomputern. In Visual Studio werden Codeanalysen für einzelne Codeprojekte von Entwicklern konfiguriert und ausgeführt, im Rahmen der Ausführung gefundene Probleme werden angezeigt und analysiert, und Arbeitselemente für Warnungen werden erstellt.|[Analysieren der Anwendungsqualität](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Erstellen und Ausführen von Komponententests:** Komponententests können Entwickler und Tester schnell auf logische Fehler in den Methoden der Klassen in überprüfen C#, Visual Basic .NET und C++-Projekte. Ein Komponententest kann einmal erstellt und jedes Mal ausgeführt werden, wenn der Quellcode geändert wurde, um sicherzustellen, dass keine Fehler eingebaut wurden.|[Komponententest für Code](../test/unit-test-your-code.md)|  
|**Nachverfolgen Sie Arbeitsaufgaben und Fehler:** Sie können Arbeitsaufgaben nachverfolgen und verwalten Ihre Arbeit sowie Informationen über das Teamprojekt verwenden. Ein Arbeitselement ist ein Datenbankeintrag, den [!INCLUDE[esprfound](../includes/esprfound-md.md)] zum Nachverfolgen der Zuordnung und des Status der Arbeit verwendet. Sie können verschiedene Typen von Arbeitselementen verwenden, um unterschiedliche Arten von Arbeiten nachzuverfolgen, z. B. Kundenanforderungen, Produktfehler oder Entwicklungsaufgaben.|[Arbeitsnachverfolgung und workflowverwaltung &#91;umgeleitet&#93;](http://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
### <a name="guidance"></a>Empfehlungen  
 [Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententest: Interne Tests](http://go.microsoft.com/fwlink/?LinkID=255188)
