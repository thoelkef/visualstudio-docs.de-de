---
title: Übersicht über Erweiterbarkeit von Visual Studio "Ordner öffnen" | Microsoft-Dokumentation
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2bb74703f639848d643f536edf620e30b1836310
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986010"
---
# <a name="open-folder-extensibility"></a>Öffnen Sie die Ordner-Erweiterbarkeit

Die [Ordner öffnen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Feature ermöglicht Benutzern, öffnen Sie eine Codebasis in Visual Studio, ohne die Notwendigkeit Projektmappen- oder Projektdateien. "Ordner öffnen" bietet wie z. B. Funktionen, die Anwender von Visual Studio erwarten:

* Integration von Projektmappen-Explorer, und suchen
* Farbliche Kennzeichnung von Editor
* Gehe zu-navigation
* Suchen in Dateien suchen

Bei Verwendung mit Workloads z. B. für .NET und C++-Entwicklung erhalten auch Benutzer:

* Rich-Intellisense
* Language-spezifische Funktionen

Mit "Ordner öffnen" können die Ersteller von Erweiterungen Funktionsumfang für beliebige Sprachen erstellen. Es werden APIs zum Erstellen, Debuggen und Symbolsuche die Unterstützung für jede Datei in einem vom Benutzer codebase. Aktuelle Extender können ihre vorhandenen Visual Studio-Funktionen zum Verstehen von Code ohne die Sicherung von Projekten oder eine Lösung aktualisieren.

## <a name="an-api-without-project-systems"></a>Eine API ohne Projektsystemen

Visual Studio wird in der Vergangenheit nur Dateien in einer Projektmappe und deren Projekte mithilfe von Projektsystemen verstanden. Ein Projektsystem ist verantwortlich für die Funktionen und Interaktionen von einem anderen geladenen Projekt. Es versteht ihr Projekt die Dateien enthält, die visuelle Darstellung des Inhalts Projekt, Abhängigkeiten von anderen Projekten und Änderung der zugrunde liegenden Projektdatei. Es ist durch diese Hierarchien und die Funktionen, die anderen Komponenten im Auftrag des Benutzers funktionieren. Nicht alle Codebasen werden auch in einer Projekt- und Projektmappendateien Struktur dargestellt. Skriptsprachen und Open-Source-Code für Linux in C++ geschrieben sind gute Beispiele für. Mit "Ordner öffnen" bietet Visual Studio Benutzer eine neue Möglichkeit der Interaktion mit ihren Quellcode an.

Die Ordner-öffnen-APIs befinden sich unter dem `Microsoft.VisualStudio.Workspace.*` Namespace und stehen für Extender, erstellen und Nutzen von Daten oder Aktionen, um Dateien in "Ordner öffnen". Erweiterungen können diese APIs verwenden, um Funktionalität für viele Bereiche, einschließlich bereitzustellen:

- [Arbeitsbereiche](workspaces.md) : das Starten des geöffneten Ordner Erweiterbarkeit wird der Arbeitsbereich und die APIs.
- [Datei Kontexte und Aktionen](workspace-file-contexts.md) -spezifischen Code Intelligence über dateikontexte bereitgestellten Datei.
- [Indizierung](workspace-indexing.md) – sammeln und Beibehalten von Daten über "Ordner öffnen" Arbeitsbereiche.
- [Sprachdienste](workspace-language-services.md) -Sprachdienste in "Ordner öffnen" Arbeitsbereiche zu integrieren.
- [Erstellen Sie](workspace-build.md) -Unterstützung für "Ordner öffnen" Arbeitsbereiche zu erstellen.

Funktionen, die die folgenden Typen verwenden, müssen Sie neue APIs zur Unterstützung von "Ordner öffnen" zu übernehmen:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Feedback, Kommentare, Probleme

Öffnen Sie Ordner und die `Microsoft.VisualStudio.Workspace.*` APIs sind in der aktiven Entwicklung. Wenn Sie ein unerwartetes Verhalten auftreten, dann finden Sie die bekannten Probleme für die Version von Interesse sind. [Entwickler-Community](https://developercommunity.visualstudio.com) ist der empfohlene Platz zum Abstimmen und Probleme zu erstellen. Für jedes Feedback empfehlen wir dringend eine ausführliche Beschreibung Ihres Problems. Enthalten Sie, die Visual Studio-Version, die, der Sie entwickeln, die APIs, die Sie verwenden (was Sie implementiert haben und welche Interaktion mit sind), das erwartete Ergebnis und dem tatsächlichen Ergebnis. Falls möglich, sollten Sie ein Speicherabbild des Prozesses devenv.exe. Verwenden GitHubs-Problem, die für das Bereitstellen von Feedback dazu und verwandten Dokumentation.

## <a name="next-steps"></a>Nächste Schritte

* [Arbeitsbereiche](workspaces.md) -erfahren Sie mehr über den "Ordner öffnen" Arbeitsbereich-API.