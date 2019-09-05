---
title: Kompilieren und Erstellen
description: In diesem Artikel erfahren Sie, wie Sie Projekte und Projektmappen in Visual Studio für Mac kompilieren und erstellen können.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/29/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 666027835699763dd42139b0b3b20e55fe250892
ms.sourcegitcommit: fe212f8960d7882a1b0fdae9e22f008996aacf3c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222714"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilieren und Generieren in Visual Studio für Mac

Mit Visual Studio für Mac können Sie Anwendungen und Assemblys während der Entwicklung Ihres Projekts erstellen. Es ist wichtig, dass Sie häufig Builds erstellen, um Typenkonflikte, fehlerhafte Syntax, falsch geschriebene Schlüsselwörter und andere Kompilierzeitfehler im Code schnell zu erkennen. Durch das anschließende Debuggen können Sie auch Laufzeitfehler beispielsweise in Bezug auf Logik, E/A und Division durch Null finden und beheben.

Ein erfolgreicher Build bedeutet, dass der Quellcode die richtige Syntax enthält und alle statischen Verweise auf Bibliotheken, Assemblys und andere Komponenten aufgelöst werden können. Der Buildprozess erzeugt eine ausführbare Datei für die Anwendung. Diese ausführbare Datei kann dann per Debugging sowie verschiedenen Arten manueller und automatisierter Tests getestet werden, um die Codequalität zu überprüfen. Nachdem die Anwendung vollständig getestet wurde, können Sie eine Releaseversion zur Bereitstellung für Ihre Kunden kompilieren.

Auf dem Mac können Sie eine der folgenden Methoden zum Kompilieren Ihrer Anwendung verwenden: Visual Studio für Mac, MSBuild-Befehlszeilentools oder Azure Pipelines.

| Erstellungsmethode | Vorteile |
| --- |--- | --- |
| Visual Studio für Mac |- Direktes Erstellen von Builds und Testen in einem Debugger<br />- Ausführen von Multiprozessorbuilds für C#-Projekte<br />- Anpassen verschiedener Aspekte des Buildsystems |
| MSBuild-Befehlszeile| - Erstellen von Projekten, ohne Visual Studio für Mac zu installieren<br />- Ausführen von Multiprozessorbuilds für alle Projekttypen<br />- Anpassen der meisten Bereiche des Buildsystems|
| Azure Pipelines | - Automatisieren des Buildprozesses als Teil einer fortlaufenden Integration oder einer fortlaufenden Zustellpipeline<br />- Anwenden von automatisierten Tests mit jedem Build<br />– Verwenden der nahezu unbegrenzten cloudbasierten Ressourcen für Buildprozesse<br />- Anpassen des Buildworkflows und Erstellen von Buildaktivitäten zum Ausführen benutzerdefinierter Aufgaben|

Die Dokumentation in diesem Bereich geht näher auf den IDE-basierten Buildprozess ein. Weitere Informationen zum Erstellen von Anwendungsbuilds über die Befehlszeile finden Sie unter [MSBuild](/visualstudio/msbuild/msbuild). Ausführliche Informationen zum Erstellen von Anwendungsbuilds mit Azure Pipelines finden Sie unter [Azure Pipelines](/azure/devops/pipelines).


> [!NOTE]
> Dieses Thema gilt für Visual Studio für Mac. Informationen zu Visual Studio unter Windows finden Sie unter [Kompilieren und Erstellen in Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).


## <a name="building-from-the-ide"></a>Erstellen aus der IDE

Mit Visual Studio für Mac können Sie Builds umgehend erstellen und ausführen und haben die vollständige Kontrolle über Buildfunktionen. Wenn Sie ein Projekt erstellen, definiert Visual Studio für Mac eine Standardbuildkonfiguration, die den Kontext für Builds festlegt. Sie können Standardbuildkonfigurationen bearbeiten und auch selbst eine Buildkonfiguration erstellen. Das Erstellen oder Modifizieren dieser Konfigurationen aktualisiert automatisch die Projektdatei, die dann von MSBuild verwendet wird, um das Projekt zu erstellen.

Weitere Informationen zum Erstellen Ihrer eigenen Projekte und Projektmappen in der IDE finden Sie im Handbuch [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](building-and-cleaning-projects-and-solutions.md).

Mit Visual Studio für Mac können Sie auch:

* Den Ausgabepfad ändern. Diesen können Sie in den Optionen Ihres Projekts bearbeiten.

    ![Ändern des Ausgabepfads](media/compiling-and-building-image4.png)

* Den Ausführlichkeitsgrad der Buildausgabe ändern:

    ![Ändern des Ausführlichkeitsgrads des Builds](media/compiling-and-building-image5.png)

* Benutzerdefinierte Befehle vor, während oder nach dem Erstellen oder Bereinigen hinzufügen:

    ![Hinzufügen benutzerdefinierter Befehle](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Siehe auch

- [Kompilieren und Erstellen (Visual Studio unter Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)