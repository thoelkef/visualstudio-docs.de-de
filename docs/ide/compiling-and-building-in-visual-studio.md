---
title: Kompilieren und Erstellen in Visual Studio
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 39242fc5b95b583ee153e5be5fc562fb49eb4d46
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924221"
---
# <a name="compile-and-build-in-visual-studio"></a>Kompilieren und Erstellen in Visual Studio

Durch das Ausführen eines Builds werden zu jedem beliebigen Zeitpunkt während eines Entwicklungszyklus Assemblys und ausführbare Anwendungen aus dem Quellcode erstellt. Grundsätzlich ist der Buildprozess bei vielen verschiedenen Projekttypen sehr ähnlich, unter anderem bei Windows, ASP.NET und mobilen Apps. Auch bei Programmiersprachen wie C#, Visual Basic, C++ und F# ist der Buildprozess sehr ähnlich.

Indem Sie Ihren Code häufig erstellen, können Sie Kompilierzeitfehler wie zum Beispiel falsche Syntax, falsch geschriebene Schlüsselwörter und Typenkonflikte früher identifizieren. Sie können auch Laufzeitfehler, z.B. Logik- und Semantikfehler, erkennen und beheben, indem Sie regelmäßig Debugversionen des Codes erstellen und ausführen.

Ein erfolgreicher Build ist im Wesentlichen eine Überprüfung, dass der Quellcode der Anwendung die richtige Syntax enthält und alle statischen Verweise auf Bibliotheken, Assemblys und andere Komponenten gelöst wurden. Hierdurch wird eine ausführbare Datei erzeugt, die auf ihre ordnungsgemäße Funktion geprüft werden kann. Dies kann sowohl in einer [Debugumgebung](../debugger/index.md) geschehen als auch über eine Vielzahl manueller und automatisierter Tests, die die [Codequalität verbessern](../test/improve-code-quality.md). Sobald die Anwendung vollständig getestet ist, können Sie eine Releaseversion zur Bereitstellung für Ihre Kunden kompilieren. Eine Einführung in diesen Vorgang finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md).

Innerhalb der Visual Studio-Produktfamilie gibt es drei Methoden, die Sie zum Erstellen einer Anwendung verwenden können: die Visual Studio-IDE, die MSBuild-Befehlszeilentools und Team Foundation Build in Visual Studio Team Services:

| Erstellungsmethode | Vorteile |
| --- |--- | --- |
| IDE |- Direktes Erstellen von Builds und Testen in einem Debugger<br />- Ausführen von Multiprozessorbuilds für C++- und C#-Projekte<br />- Anpassen verschiedener Aspekte des Buildsystems |
| MSBuild-Befehlszeile| - Erstellen von Projekten, ohne Visual Studio zu installieren<br />- Ausführen von Multiprozessorbuilds für alle Projekttypen<br />- Anpassen der meisten Bereiche des Buildsystems|
| Team Foundation Build | - Automatisieren des Buildprozesses als Teil einer fortlaufenden Integration oder einer fortlaufenden Zustellpipeline<br />- Anwenden von automatisierten Tests mit jedem Build<br />- Verwenden der praktisch unbegrenzten cloudbasierten Ressourcen für Ihren Buildprozesse<br />- Anpassen des Buildworkflows und Erstellen von Buildaktivitäten zum Ausführen benutzerdefinierter Aufgaben|

Die Dokumentation in diesem Bereich geht näher auf den IDE-basierten Buildprozess ein. Weitere Informationen zu den anderen Methoden finden Sie unter [MSBuild](../msbuild/msbuild.md) und [Continuous integration and deployment (Fortlaufende Integration und Bereitstellung)](https://www.visualstudio.com/docs/build/overview).

## <a name="overview-of-building-from-the-ide"></a>Überblick: Erstellen aus der IDE

Wenn Sie ein Projekt erstellen, erstellt Visual Studio Standardbuildkonfigurationen für das Projekt und die Projektmappe, die das Projekt enthält.  Diese Konfigurationen definieren, wie die Projektmappen und Projekte erstellt und bereitgestellt werden. Insbesondere die Projektkonfigurationen sind eindeutig für die jeweilige Zielplattform (z.B. Windows oder Linux) und den Buildtyp (z.B. Debug oder Release). Sie können diese Konfigurationen beliebig bearbeiten und nach Bedarf eigene Konfigurationen erstellen.

Eine erste Einführung zum Erstellen in der IDE finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Anwendung](walkthrough-building-an-application.md).

Unter [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) finden Sie Informationen zur Anpassung verschiedener Aspekte, die Sie an diesem Prozess vornehmen können. Diese Anpassungen beinhalten das [Ändern des Ausgabeverzeichnisses](how-to-change-the-build-output-directory.md), das [Angeben benutzerdefinierter Ereignisse](specifying-custom-build-events-in-visual-studio.md), das [Verwalten von Projektabhängigkeiten](how-to-create-and-remove-project-dependencies.md), das [Verwalten von Buildprotokolldateien](how-to-view-save-and-configure-build-log-files.md) und das [Unterdrücken von Compilerwarnungen](how-to-suppress-compiler-warnings.md).

Eine Vielzahl weiterer Aufgaben finden Sie hier:
- [Grundlagen der Buildkonfiguration](understanding-build-configurations.md)
- [Grundlagen zu Buildplattformen](understanding-build-platforms.md)
- [Verwalten von Projekt- und Projektmappeneigenschaften](managing-project-and-solution-properties.md)
- Geben Sie Buildereignisse in [C#](how-to-specify-build-events-csharp.md) und [Visual Basic](how-to-specify-build-events-visual-basic.md) an.
- [Festlegen von Buildoptionen](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Build Multiple Projects in Parallel (Paralleles Erstellen mehrerer Projekte)](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="see-also"></a>Siehe auch

- [Erstellen von Websites](http://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)