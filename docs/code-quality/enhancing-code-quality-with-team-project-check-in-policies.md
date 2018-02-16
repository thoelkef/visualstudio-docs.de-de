---
title: "Verbessern der Codequalität mit der Team Project in der Eincheckrichtlinien | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c82bc929fa7633719c06569cb3dded5df651a349
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt

Wenn Sie Team Foundation-Versionskontrolle (TFVC) verwenden, können Sie Eincheckrichtlinien für Teamprojekte erstellen, um Vorgehensweisen für besseren Code und eine effizientere Gruppenentwicklung zu erzwingen. Eincheckrichtlinien sind Regeln, die auf Teamprojektebene festgelegt und auf Entwicklercomputern erzwungen werden, bevor Code eingecheckt werden kann.

Sie können diese Eincheckrichtlinien für das Teamprojekt angeben:

- **Builds**: Erfordert, dass Buildunterbrechungen, die während eines Builds erstellt wurden, vor einem neuen Einchecken korrigiert werden müssen.

- **Changeset-Kommentare**: Erfordert, dass Benutzer beim Einchecken von Änderungen Kommentare eingeben.

- **Codeanalyse**: Erfordert, dass vor dem Einchecken eine Codeanalyse ausgeführt wird.

- **Arbeitsaufgaben**: Erfordert, dass dem Eincheckvorgang mindestens eine Arbeitsaufgabe zugeordnet ist.

> [!IMPORTANT]
> Eincheckrichtlinien können nur verwendet werden, wenn eine Verbindung mit [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)]besteht.

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Unterstützender Inhalt|
|----------|------------------------|
|**Eincheckrichtlinien für die Codeanalyse erstellen und verwenden:** Sie können aus einem Standardsatz von Codeanalyseregeln auswählen, oder Sie können einen benutzerdefinierten Satz erstellen.|[Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>Verwandte Aufgaben

|Aufgabe|Unterstützender Inhalt|
|----------|------------------------|
|**Codeanalyse im Entwicklungsprozess verwenden:** Teammitglieder führen die Codeanalyse auf ihren Entwicklungscomputern durch. In Visual Studio werden Codeanalysen für einzelne Codeprojekte von Entwicklern konfiguriert und ausgeführt, im Rahmen der Ausführung gefundene Probleme werden angezeigt und analysiert, und Arbeitsaufgaben für Warnungen werden erstellt.|[Analysieren der Anwendungsqualität](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**Erstellen und Ausführen von Komponententests:** mit Komponententests erhalten Entwickler und Tester eine schnelle Möglichkeit, nach logischen Fehlern in den Methoden von Klassen in c#, Visual Basic und C++-Projekten zu suchen. Ein Komponententest kann einmal erstellt und jedes Mal ausgeführt werden, wenn der Quellcode geändert wurde, um sicherzustellen, dass keine Fehler eingebaut wurden.|[Komponententest für Code](../test/unit-test-your-code.md)|
|**Arbeitsaufgaben und Fehler nachverfolgen:** Mit Arbeitsaufgaben können Sie Ihre Arbeit sowie Informationen über das Teamprojekt nachverfolgen und verwalten. Eine Arbeitsaufgabe ist ein Datenbankeintrag, den [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] zum Nachverfolgen der Zuordnung und des Status der Arbeit verwendet. Sie können verschiedene Typen von Arbeitsaufgaben verwenden, um unterschiedliche Arten von Arbeiten nachzuverfolgen, z. B. Kundenanforderungen, Produktfehler oder Entwicklungsaufgaben.|[Typen von Arbeitsaufgaben (VSTS)](/vsts/work/work-items/index)|

## <a name="external-resources"></a>Externe Ressourcen

[Testing for Continuous Delivery with Visual Studio 2012 - Chapter 2: Unit Testing: Testing the Inside (Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests)](http://go.microsoft.com/fwlink/?LinkID=255188)