---
title: Übersicht über die Visual Studio geöffneten Ordner Extensibility | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 1bbe9638777bc672a0cec494498a38f4bd8ce1f4
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="open-folder-extensibility"></a>Öffnen Sie die Ordner-Erweiterbarkeit

Die [Ordner öffnen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Funktion ermöglicht Benutzern das Öffnen einer Codebasis ohne die Notwendigkeit von Projektmappen- oder Projektdateien in Visual Studio. Ordner öffnen bietet die Benutzern Funktionen wie z. B. von Visual Studio erwarten:

* Integration von Projektmappen-Explorer und suchen
* Farbliche Kennzeichnung von Editor
* Gehe zu-navigation
* Suchen in Dateien suchen

Bei Verwendung mit Arbeitsauslastungen wie für .NET und C++-Entwicklung finden auch Benutzer:

* Rich Intellisense
* Sprachspezifische Funktionen

Ordner öffnen können Autoren von Erweiterung umfangreiche Funktionen für jede Sprache erstellen. Es sind APIs zum Erstellen, Debuggen und Symbolsuche zu unterstützen, für jede Datei in einem Benutzer-CodeBase hinzufügen. Aktuelle Extender können ihre vorhandenen Visual Studio-Funktionen zum Verstehen von Code ohne Sicherung des Projekt-oder einer Projektmappe aktualisieren.

## <a name="an-api-without-project-systems"></a>Eine API ohne Projektsystemen

Visual Studio, in der Vergangenheit nur Dateien in einer Projektmappe und deren Projekte mithilfe von Projektsystemen verstanden. Ein Projektsystem ist verantwortlich für die Funktionalität und Interaktionen von einem anderen geladenen Projekt. Er erkennt, was ihr Projekt Dateien enthält, die visuelle Darstellung des Inhalts Projekt Abhängigkeiten von anderen Projekten und Änderung der zugrunde liegenden Projekt die Datei. Es ist über diese Hierarchien und Funktionen, die anderen Komponenten im Auftrag des Benutzers geeignet sind. Nicht alle Codebasen werden auch in einer Struktur Projekt- und Projektmappendateien dargestellt. Skriptsprachen und Open-Source-Code für Linux in C++ geschrieben sind gute Beispiele für. Mit Ordner öffnen bietet Visual Studio eine neue Art der Interaktion mit ihrem Quellcode-Benutzer.

Die geöffneten Ordner APIs befinden sich unter dem `Microsoft.VisualStudio.Workspace.*` Namespace und stehen für Extender erstellen und Nutzen von Daten oder Aktionen, um Dateien im Ordner öffnen. Erweiterungen können diese APIs verwenden, um Funktionalität für viele Bereiche, einschließlich bereitzustellen:

- [Arbeitsbereiche](workspaces.md) – der Punkt des geöffneten Ordner Erweiterbarkeit hinzugekommen ist dem Arbeitsbereich und seine APIs.
- [Datei Kontexte und Aktionen](workspace-file-contexts.md) -Datei bestimmten Code Intelligence über Kontexte Datei bereitgestellt.
- [Indizierung](workspace-indexing.md) – erfasst und Beibehalten von Daten über Arbeitsbereiche geöffneten Ordner.
- [Sprachdienste](workspace-language-services.md) -Sprachdienste in Ordner öffnen Arbeitsbereiche integrieren.
- [Erstellen Sie](workspace-build.md) -Unterstützung für den Ordner öffnen Arbeitsbereiche zu erstellen.

Übernehmen der neuen APIs zur Unterstützung von Ordner öffnen müssen Funktionen, die die folgenden Datentypen verwendet werden:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Feedback, Kommentare, Probleme

Öffnen Sie Ordner und die `Microsoft.VisualStudio.Workspace.*` APIs sind in der aktiven Entwicklung. Wenn unerwartete angezeigt wird, dann finden Sie die bekannten Probleme für die Version von Interesse sind. Die Entwickler-Community ist der empfohlene Ort zum abstimmen möchten, und erstellen alle Probleme. Jedes Feedback empfehlen wir dringend eine ausführliche Beschreibung Ihres Problems. Schließen Sie die Visual Studio-Version, der Sie für entwickeln, die APIs, die Sie verwenden (was Sie implementiert haben und welche Interaktion mit sind), das erwartete Ergebnis und dem tatsächlichen Ergebnis. Wenn möglich, ein Speicherabbild des Prozesses devenv.exe einschließen Verwenden GitHubs-problemverfolgung für das Bereitstellen von Feedback für diese und verwandte Dokumentation.

## <a name="next-steps"></a>Nächste Schritte

* [Arbeitsbereiche](workspaces.md) -erfahren Sie mehr über den Ordner öffnen Arbeitsbereich API.