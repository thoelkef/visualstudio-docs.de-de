---
title: Übersicht über Visual Studio-Erweiterbarkeit von geöffneten Ordnern | Microsoft-Dokumentation
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d213a7add358c46f7088f504d8c54352cda44a1c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905978"
---
# <a name="open-folder-extensibility"></a>Ordner Erweiterbarkeit öffnen

Mit dem Feature "Ordner öffnen" können Benutzer jede beliebige Codebasis in Visual Studio öffnen, ohne dass Projekt-oder [Projektmappendateien](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) benötigt werden. Der Ordner öffnen bietet die Features, die Benutzer von Visual Studio erwarten, z. b.:

* Projektmappen-Explorer Integration und Search
* Farbliche Farbgebung des Editors
* Gehe zu Navigation
* Suche in Dateien suchen

Bei Verwendung mit Workloads wie z. b. für die .net-und C++-Entwicklung erhalten Benutzer auch Folgendes:

* Umfassende IntelliSense-Funktionen
* Sprachspezifische Funktionalität

Mit dem geöffneten Ordner können Erweiterungs Autoren umfassende Funktionen für jede beliebige Sprache erstellen. Es gibt APIs, mit denen das entwickeln, Debuggen und die Symbol Suche für eine beliebige Datei in der Codebasis eines Benutzers unterstützt wird. Aktuelle Extender können vorhandene Visual Studio-Features aktualisieren, um Code zu verstehen, ohne Projekte oder eine Projekt Mappe zu unterstützen.

## <a name="an-api-without-project-systems"></a>Eine API ohne Projektsysteme

In der Vergangenheit hat Visual Studio nur die Dateien in einer Projekt Mappe und deren Projekte mithilfe von Projekt Systemen verstanden. Ein Projekt System ist verantwortlich für die Funktionalität und die Benutzerinteraktionen eines geladenen Projekts. Es versteht, welche Dateien das Projekt enthält, die visuelle Darstellung des Projekt Inhalts, Abhängigkeiten von anderen Projekten und die Änderung der zugrunde liegenden Projektdatei. Diese Hierarchien und Funktionen werden von anderen Komponenten im Auftrag des Benutzers bearbeitet. Nicht alle Codebasen werden in einer Projekt-und Projektmappenstruktur gut dargestellt. In C++ für Linux geschriebene Skriptsprachen und Open Source-Code sind gute Beispiele. Mit Open Folder bietet Visual Studio Benutzern eine neue Möglichkeit, mit Ihrem Quellcode zu interagieren.

Die Open Folder-APIs befinden sich unter dem `Microsoft.VisualStudio.Workspace.*` -Namespace und stehen für Extender zum erzeugen und Nutzen von Daten oder Aktionen im Zusammenhang mit Dateien im geöffneten Ordner zur Verfügung. Erweiterungen können diese APIs verwenden, um Funktionen für viele Bereiche bereitzustellen, einschließlich:

- [Arbeitsbereiche](workspaces.md) : der Ausgangspunkt der Erweiterbarkeit offener Ordner ist der Arbeitsbereich und seine APIs.
- [Datei Kontexte und Aktionen](workspace-file-contexts.md) : Datei spezifische Code Intelligenz, die über Datei Kontexte bereitgestellt wird.
- [Indizierung](workspace-indexing.md) : sammeln und Speichern von Daten über geöffnete Ordner Arbeitsbereiche.
- [Sprachdienste](workspace-language-services.md) : integrieren Sie Sprachdienste in Arbeitsbereiche für geöffnete Ordner.
- [Build](workspace-build.md) -Buildunterstützung für geöffnete Ordner Arbeitsbereiche.

Für Funktionen, die die folgenden Typen verwenden, müssen neue APIs zur Unterstützung des geöffneten Ordners übernommen werden:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Feedback, Kommentare, Probleme

Öffnen Sie den Ordner, und die `Microsoft.VisualStudio.Workspace.*` APIs befinden sich in der aktiven Entwicklung. Wenn ein unerwartetes Verhalten auftritt, sehen Sie sich die bekannten Probleme für die betreffende Version an. Die [Entwickler Community](https://developercommunity.visualstudio.com) ist der empfohlene Ort, um Probleme zu beheben und Probleme zu beheben. Für jedes Feedback empfehlen wir dringend eine ausführliche Beschreibung Ihres Problems. Schließen Sie die Visual Studio-Version ein, die Sie entwickeln, die von Ihnen verwendeten APIs (sowohl das, was Sie implementiert haben, als auch das, mit dem Sie interagieren), das erwartete Ergebnis und das tatsächliche Ergebnis. Fügen Sie, wenn möglich, ein Dump des devenv.exe Prozesses ein. Verwenden Sie die Problemverfolgung von GitHub, um Feedback zu dieser und zugehörigen Dokumentation zu geben.

## <a name="next-steps"></a>Nächste Schritte

* [Arbeitsbereiche](workspaces.md) : erfahren Sie mehr über die Arbeitsbereichs-API für geöffnete Ordner.