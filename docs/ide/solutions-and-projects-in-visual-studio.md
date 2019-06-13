---
title: Projektmappen und Projekte
ms.date: 10/05/2017
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42a8dbc2fd9a6fc89b0be62271b048f8275a82b2
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432198"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Projektmappen und Projekte in Visual Studio

In diesem Artikel wird das Konzept eines *Projekts* und einer *Projektmappe* in Visual Studio erläutert. Darüber hinaus werden die Vorgehensweise beim Erstellen eines neuen Projekts sowie das Toolfenster **Projektmappen-Explorer** kurz beschrieben.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Projekte und Projektmappen in Visual Studio für Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projekte

Wenn Sie eine App, eine Website, ein Plug-In usw. in Visual Studio erstellen, beginnen Sie mit einem *Projekt*. Ein Projekt enthält alle Quellcodedateien, Symbole, Bilder, Datendateien usw., die in eine ausführbare Datei, Bibliothek oder Website kompiliert werden. Ein Projekt enthält außerdem die Compilereinstellungen und andere Konfigurationsdateien, die möglicherweise von verschiedenen Diensten und Komponenten benötigt werden, mit denen Ihr Programm kommuniziert.

> [!NOTE]
> Der Code muss in Visual Studio nicht mithilfe von Projektmappen oder Projekten bearbeitet, erstellt und gedebuggt werden. Zum Debuggen öffnen Sie einfach in Visual Studio den Ordner, der die Quelldateien enthält, und beginnen mit dem Bearbeiten. Weitere Informationen finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Ein Projekt ist eine XML-Datei mit einer Erweiterung wie *VBPROJ*, *CSPROJ* oder *VCXPROJ*. Diese Datei enthält eine virtuelle Ordnerhierarchie und Pfade zu allen Elementen im Projekt. Sie enthält außerdem die Buildeinstellungen.

> [!TIP]
> Entladen Sie ein Projekt zunächst, indem Sie im **Projektmappen-Explorer** auf den Namen des Projekts klicken, das Kontextmenü per Rechtsklick öffnen und auf **Projekt entladen** klicken, um den Inhalt einer Projektdatei in Visual Studio anzuzeigen. Öffnen Sie erneut das Kontextmenü, und wählen Sie **\<Projektname\> bearbeiten** aus.

In Visual Studio wird die Projektdatei im **Projektmappen-Explorer** verwendet, um Projektinhalte und Einstellungen anzuzeigen. Wenn Sie das Projekt kompilieren, verwendet die MSBuild-Engine die Projektdatei, um die ausführbare Datei zu erstellen. Sie können Projekte auch so anpassen, dass andere Arten von Ausgaben produziert werden.

## <a name="solutions"></a>Projektmappen

Projekte befinden sich in *Projektmappen*. Trotz der englischen Bezeichnung „Solution“ ist eine Projektmappe keine „Lösung“. Eine Projektmappe ist lediglich ein Container für ein oder mehrere zusammengehörige Projekte sowie Buildinformationen, Visual Studio-Fenstereinstellungen und jegliche weitere Dateien, die zu keinem bestimmten Projekt gehören. Eine Projektmappe wird von einer Textdatei (mit der Erweiterung *SLN*) in einem individuellen Format beschrieben. Dieses sollte nicht manuell bearbeitet werden.

Visual Studio speichert die Einstellungen von Projektmappen in zwei Dateitypen (*SLN* und *SUO*):

|Erweiterung|name|Beschreibung|
|---------------|----------|-----------------|
|.sln|Visual Studio-Projektmappe|Organisiert Projekte, Projektelemente und Projektmappenelemente in einer Projektmappe.|
|.suo|Benutzeroptionen bei Projektmappen|Speichert Einstellungen und Anpassungen (z.B. Breakpoints) auf Benutzerebene.|

## <a name="create-new-projects"></a>Neue Projekte erstellen

Ein neues Projekt lässt sich am einfachsten über eine Projektvorlage für einen bestimmten Anwendungs- oder Websitetyp erstellen. Eine Projektvorlage besteht aus mehreren grundlegenden und vorab generierten Codedateien, Konfigurationsdateien, Objekten und Einstellungen. Diese Vorlagen finden Sie in dem Dialogfeld, in dem Sie ein neues Projekt erstellen (**Datei** > **Neu** > **Projekt**). Weitere Informationen finden Sie unter [Erstellen eines neuen Projekts in Visual Studio](create-new-project.md) und [Erstellen von Projektmappen und Projekten](../ide/creating-solutions-and-projects.md).

Wenn Sie Ihre Projekte häufig auf eine bestimmte Weise anpassen, können Sie eine benutzerdefinierte Projektvorlage erstellen, die Sie dann zum Erstellen neuer Projekte verwenden können. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

Wenn Sie ein neues Projekt erstellen, wird es standardmäßig unter *%USERPROFILE%\source\repos* gespeichert. Sie können diesen Speicherort in der Einstellung **Projektspeicherort** unter **Extras** > **Optionen** > **Projekte und Projektmappen** > **Speicherorte** ändern. Weitere Informationen finden Sie auf der Seite [„Projekte und Projektmappen“, Dialogfeld „Optionen“](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Projektmappen-Explorer

Nachdem Sie ein neues Projekt erstellt haben, können Sie mit dem **Projektmappen-Explorer** Projekte und Projektmappen sowie zugehörige Elemente anzeigen und verwalten. Die folgende Abbildung zeigt den **Projektmappen-Explorer** mit einer C#-Projektmappe, die zwei Projekte enthält:

![Projektmappen-Explorer](../ide/media/vs2015_solution_explorer.png)

Viele Menübefehle sind über das Kontextmenü verschiedener Elemente im **Projektmappen-Explorer** verfügbar. Diese Befehle umfassen das Erstellen eines Projekts, das Verwalten von NuGet-Paketen, das Hinzufügen einer Referenz, das Umbenennen einer Datei und das Ausführen von Tests, um nur einige zu nennen. Die Symbolleiste oben im **Projektmappen-Explorer** bietet Schaltflächen, mit denen Sie von einer Projektmappenansicht zu einer Ordneransicht wechseln, ausgeblendete Dateien anzeigen, alle Knoten reduzieren und viele weitere Aktionen ausführen können.

Bei ASP.NET Core-Projekten können Sie die Schachtelung von Dateien im **Projektmappen-Explorer** anpassen. Weitere Informationen finden Sie unter [Anpassen der Dateischachtelung im Projektmappen-Explorer](file-nesting-solution-explorer.md).

## <a name="see-also"></a>Siehe auch

- [Visual Studio-IDE](../get-started/visual-studio-ide.md)
- [Projekte und Projektmappen (Visual Studio für Mac)](/visualstudio/mac/projects-and-solutions)
- [Hinzufügen und Entfernen von Projektelementen (Visual Studio für Mac)](/visualstudio/mac/add-and-remove-project-items)
