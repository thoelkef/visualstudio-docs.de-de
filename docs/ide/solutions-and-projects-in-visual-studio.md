---
title: Projektmappen und Projekte
ms.date: 10/05/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.newproject
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items [Visual Studio]
- solutions [Visual Studio]
- project items [Visual Studio]
- solutions [Visual Studio], designing
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba0ed54e8acd28be3f267d83473f9514f471ef4a
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349308"
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

Projekte befinden sich in *Projektmappen*. Eine Projektmappe enthält mindestens ein oder mehrere zusammengehörige Projekte sowie Buildinformationen, Visual Studio-Fenstereinstellungen sowie beliebige weitere Dateien, die zu keinem bestimmten Projekt gehören. Eine Projektmappe wird von einer Textdatei (mit der Erweiterung *SLN*) in einem individuellen Format beschrieben. Dieses sollte nicht manuell bearbeitet werden.

Visual Studio speichert die Einstellungen von Projektmappen in zwei Dateitypen (*SLN* und *SUO*):

|Erweiterung|name|Beschreibung |
|---------------|----------|-----------------|
|.sln|Visual Studio-Projektmappe|Organisiert Projekte, Projektelemente und Projektmappenelemente in einer Projektmappe.|
|.suo|Benutzeroptionen bei Projektmappen|Speichert Einstellungen und Anpassungen (z.B. Breakpoints) auf Benutzerebene.|

## <a name="create-new-projects"></a>Neue Projekte erstellen

Ein neues Projekt lässt sich am einfachsten über eine Projektvorlage für einen bestimmten Anwendungs- oder Websitetyp erstellen. Eine Projektvorlage besteht aus mehreren grundlegenden und vorab generierten Codedateien, Konfigurationsdateien, Objekten und Einstellungen. Diese Vorlagen finden Sie im Dialogfeld **Neues Projekt**, wenn Sie **Datei** > **Neu** > **Projekt** auswählen. Weitere Informationen finden Sie unter [Erstellen von Projekten und Projektmappen](../ide/creating-solutions-and-projects.md).

Sie können auch benutzerdefinierte Projekte und Elementvorlagen erstellen. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

## <a name="manage-projects-in-solution-explorer"></a>Verwalten von Projekten im Projektmappen-Explorer

Nachdem Sie ein neues Projekt erstellt haben, können Sie mit dem **Projektmappen-Explorer** Projekte und Projektmappen sowie zugehörige Elemente anzeigen und verwalten. Die folgende Abbildung zeigt den **Projektmappen-Explorer** mit einer C#-Projektmappe, die zwei Projekte enthält:

![Projektmappen-Explorer](../ide/media/vs2015_solution_explorer.png)

## <a name="see-also"></a>Siehe auch

- [Visual Studio-IDE](../ide/visual-studio-ide.md)
- [Projekte und Projektmappen (Visual Studio für Mac)](/visualstudio/mac/projects-and-solutions)
- [Hinzufügen und Entfernen von Projektelementen (Visual Studio für Mac)](/visualstudio/mac/add-and-remove-project-items)