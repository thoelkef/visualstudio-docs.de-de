---
title: Verbessern der Code Qualität mit Eincheck Richtlinien für das Team Projekt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eaf95bdba84d116198bf332e3cf2725f5e95e614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75848232"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Team Foundation-Versionskontrolle (TFVC) verwenden, können Sie Eincheckrichtlinien für Teamprojekte erstellen, um Vorgehensweisen für besseren Code und eine effizientere Gruppenentwicklung zu erzwingen. Eincheckrichtlinien sind Regeln, die auf Teamprojektebene festgelegt und auf Entwicklercomputern erzwungen werden, bevor Code eingecheckt werden kann.

 Sie können diese Eincheckrichtlinien für das Teamprojekt angeben:

- **Builds**: Erfordert, dass Buildunterbrechungen, die während eines Builds erstellt wurden, vor einem neuen Einchecken korrigiert werden müssen.

- **Changeset-Kommentare**: Erfordert, dass Benutzer beim Einchecken von Änderungen Kommentare eingeben.

- **Codeanalyse**: Erfordert, dass vor dem Einchecken eine Codeanalyse ausgeführt wird.

- **Arbeitselemente**: Erfordert, dass dem Eincheckvorgang mindestens ein Arbeitselement zugeordnet ist.

> [!IMPORTANT]
> Eincheckrichtlinien können nur verwendet werden, wenn eine Verbindung mit [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)]besteht.

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Hilfreiche Themen|
|----------|------------------------|
|**Eincheckrichtlinien erstellen und verwenden:** Eincheckrichtlinien werden mit den Teamprojekteinstellungen von [!INCLUDE[esprscc](../includes/esprscc-md.md)]erstellt.|[Festlegen und Erzwingen von Quality Gates](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Eincheckrichtlinien für die Codeanalyse erstellen und verwenden:** Sie können aus einem Standardsatz von Codeanalyseregeln auswählen, oder Sie können einen benutzerdefinierten Satz erstellen.|[Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>Related Tasks

|Aufgabe|Hilfreiche Themen|
|----------|------------------------|
|**Entwicklungsumgebung vorbereiten:** Bevor Sie Code erstellen oder ändern, müssen Sie die Entwicklungs- und Testumgebung mit dem entsprechenden Quellcode einrichten. Wenn Sie Datenbanken verwenden, benötigen Sie außerdem Zugriff auf die Offlinedarstellung der Datenbanken.|[Einrichten von Entwicklungsumgebungen](https://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|
|**Codeanalyse im Entwicklungsprozess verwenden:** Teammitglieder führen die Codeanalyse auf ihren Entwicklungscomputern durch. In Visual Studio werden Codeanalysen für einzelne Codeprojekte von Entwicklern konfiguriert und ausgeführt, im Rahmen der Ausführung gefundene Probleme werden angezeigt und analysiert, und Arbeitselemente für Warnungen werden erstellt.|[Analysieren der Anwendungsqualität](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**Komponententests erstellen und ausführen:** Komponententests ermöglichen Entwicklern und Testern, die Methoden der Klassen in C#-, Visual Basic .NET- und C++-Projekten schnell auf logische Fehler hin zu überprüfen. Ein Komponententest kann einmal erstellt und jedes Mal ausgeführt werden, wenn der Quellcode geändert wurde, um sicherzustellen, dass keine Fehler eingebaut wurden.|[Komponententests für Ihren Code](../test/unit-test-your-code.md)|
|**Arbeitselemente und Fehler nachverfolgen:** Mit Arbeitselementen können Sie Ihre Arbeit sowie Informationen über das Teamprojekt nachverfolgen und verwalten. Ein Arbeitselement ist ein Datenbankeintrag, den [!INCLUDE[esprfound](../includes/esprfound-md.md)] zum Nachverfolgen der Zuordnung und des Status der Arbeit verwendet. Sie können verschiedene Typen von Arbeitselementen verwenden, um unterschiedliche Arten von Arbeiten nachzuverfolgen, z. B. Kundenanforderungen, Produktfehler oder Entwicklungsaufgaben.|[Nachverfolgen von Arbeit und Verwalten von Workflow &#91;umgeleitet&#93;](https://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|

## <a name="external-resources"></a>Externe Ressourcen

### <a name="guidance"></a>Anleitungen
 [Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests](https://msdn.microsoft.com/library/jj159340.aspx)
