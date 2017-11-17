---
title: "Verbessern der Codequalität mit der Team Project in der Eincheckrichtlinien | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5b421f5512e51d83e7f6e4edfbbe2869a1484200
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt
Wenn Sie Team Foundation-Versionskontrolle (TFVC) verwenden, können Sie Eincheckrichtlinien für Teamprojekte erstellen, um Vorgehensweisen für besseren Code und eine effizientere Gruppenentwicklung zu erzwingen. Eincheckrichtlinien sind Regeln, die auf Teamprojektebene festgelegt und auf Entwicklercomputern erzwungen werden, bevor Code eingecheckt werden kann.  
  
 Sie können diese Eincheckrichtlinien für das Teamprojekt angeben:  
  
-   **Builds**: Erfordert, dass Buildunterbrechungen, die während eines Builds erstellt wurden, vor einem neuen Einchecken korrigiert werden müssen.  
  
-   **Changeset-Kommentare**: Erfordert, dass Benutzer beim Einchecken von Änderungen Kommentare eingeben.  
  
-   **Codeanalyse**: Erfordert, dass vor dem Einchecken eine Codeanalyse ausgeführt wird.  
  
-   **Arbeitsaufgaben**: Erfordert, dass dem Eincheckvorgang mindestens eine Arbeitsaufgabe zugeordnet ist.  
  
> [!IMPORTANT]
>  Eincheckrichtlinien können nur verwendet werden, wenn eine Verbindung mit [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)]besteht.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Unterstützender Inhalt|  
|----------|------------------------|  
|**Eincheckrichtlinien erstellen und verwenden:** Eincheckrichtlinien werden mit den Teamprojekteinstellungen von [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]erstellt.|[Festlegen und Erzwingen von Quality Gates](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Eincheckrichtlinien für die Codeanalyse erstellen und verwenden:** Sie können aus einem Standardsatz von Codeanalyseregeln auswählen, oder Sie können einen benutzerdefinierten Satz erstellen.|[Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>Verwandte Aufgaben  
  
|Aufgabe|Unterstützender Inhalt|  
|----------|------------------------|  
|**Entwicklungsumgebung vorbereiten:** Bevor Sie Code erstellen oder ändern, müssen Sie die Entwicklungs- und Testumgebung mit dem entsprechenden Quellcode einrichten. Wenn Sie Datenbanken verwenden, benötigen Sie außerdem Zugriff auf die Offlinedarstellung der Datenbanken.|[Einrichten von Entwicklungsumgebungen](http://msdn.microsoft.com/en-us/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Codeanalyse im Entwicklungsprozess verwenden:** Teammitglieder führen die Codeanalyse auf ihren Entwicklungscomputern durch. In Visual Studio werden Codeanalysen für einzelne Codeprojekte von Entwicklern konfiguriert und ausgeführt, im Rahmen der Ausführung gefundene Probleme werden angezeigt und analysiert, und Arbeitsaufgaben für Warnungen werden erstellt.|[Analysieren der Anwendungsqualität](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Komponententests erstellen und ausführen:** Komponententests ermöglichen Entwicklern und Testern, die Methoden der Klassen in C#-, Visual Basic .NET- und C++-Projekten schnell auf logische Fehler hin zu überprüfen. Ein Komponententest kann einmal erstellt und jedes Mal ausgeführt werden, wenn der Quellcode geändert wurde, um sicherzustellen, dass keine Fehler eingebaut wurden.|[Komponententest für Code](../test/unit-test-your-code.md)|  
|**Arbeitsaufgaben und Fehler nachverfolgen:** Mit Arbeitsaufgaben können Sie Ihre Arbeit sowie Informationen über das Teamprojekt nachverfolgen und verwalten. Eine Arbeitsaufgabe ist ein Datenbankeintrag, den [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] zum Nachverfolgen der Zuordnung und des Status der Arbeit verwendet. Sie können verschiedene Typen von Arbeitsaufgaben verwenden, um unterschiedliche Arten von Arbeiten nachzuverfolgen, z. B. Kundenanforderungen, Produktfehler oder Entwicklungsaufgaben.|[Nachverfolgen der Arbeit und Verwalten von Workflows &#91; umgeleitet &#93;](http://msdn.microsoft.com/en-us/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
### <a name="guidance"></a>Empfehlungen  
 [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 2: Unit Testing: Testing the Inside (Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests)](http://go.microsoft.com/fwlink/?LinkID=255188)