---
title: Projektmappen und Projekte in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 10/5/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4d242a74bd1eaef86e3465d53aa148429af42f7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="solutions-and-projects-in-visual-studio"></a>Projektmappen und Projekte in Visual Studio

## <a name="projects"></a>Projekte

Wenn Sie eine App, eine Website, ein Plug-In usw. in Visual Studio erstellen, beginnen Sie mit einem *Projekt*. Ein Projekt enthält alle Quellcodedateien, Symbole, Bilder, Datendateien usw., die in eine ausführbare Datei, Bibliothek oder Website kompiliert werden. Ein Projekt enthält außerdem die Compilereinstellungen und andere Konfigurationsdateien, die möglicherweise von verschiedenen Diensten und Komponenten benötigt werden, mit denen Ihr Programm kommuniziert.

> [!NOTE]
> Der Code muss in Visual Studio nicht mithilfe von Projektmappen oder Projekten bearbeitet, erstellt und gedebuggt werden. Zum Debuggen öffnen Sie einfach in Visual Studio den Ordner, der die Quelldateien enthält, und beginnen mit dem Bearbeiten. Weitere Informationen finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Ein Projekt ist eine XML-Datei mit einer Erweiterung wie .vbproj, .csproj oder .vcxproj. Diese Datei enthält eine virtuelle Ordnerhierarchie und Pfade zu allen Elementen im Projekt. Sie enthält außerdem die Buildeinstellungen.

> [!TIP]
> Um einen Blick auf den Inhalt einer Projektdatei in Visual Studio zu werfen, entladen Sie das Projekt zuerst, indem Sie im Projektmappen-Explorer auf den Namen des Projekts klicken, über einen Rechtsklick das Kontextmenü öffnen und auf **Projekt entladen** klicken. Öffnen Sie erneut das Kontextmenü, und wählen Sie **\<Projektname\> bearbeiten** aus.

In Visual Studio wird die Projektdatei im Projektmappen-Explorer verwendet, um Projektinhalte und Einstellungen anzuzeigen. Wenn Sie das Projekt kompilieren, verwendet das MSBuild-Modul die Projektdatei, um die ausführbare Datei zu erstellen. Sie können Projekte auch so anpassen, dass andere Arten von Ausgaben produziert werden.

## <a name="solutions"></a>Projektmappen

Projekte befinden sich in *Projektmappen*. Eine Projektmappe enthält mindestens ein oder mehrere zusammengehörige Projekte sowie Buildinformationen, Visual Studio-Fenstereinstellungen sowie beliebige weitere Dateien, die zu keinem bestimmten Projekt gehören. Eine Projektmappe wird von einer Textdatei ( mit der Erweiterung .sln) in einem individuellen Format beschrieben; dieses sollte nicht manuell bearbeitet werden.

Einer Projektmappe ist eine *SUO*-Datei zugeordnet, in der Einstellungen und Konfigurationsinformationen für jeden Benutzer gespeichert sind, der am Projekt gearbeitet hat.

## <a name="creating-new-projects"></a>Erstellen neuer Projekte

Ein neues Projekt lässt sich am einfachsten über eine Projektvorlage für einen bestimmten Anwendungs- oder Websitetyp erstellen. Eine Projektvorlage besteht aus mehreren grundlegenden und vorab generierten Codedateien, Konfigurationsdateien, Objekten und Einstellungen. Diese Vorlagen finden Sie im Dialogfeld **Neues Projekt** oder **Neue Website**, wenn Sie **Datei**, **Neu**, **Projekt** oder **Datei**, **Neu**, **Website** auswählen. Weitere Informationen finden Sie unter [Erstellen von Projekten und Projektmappen](../ide/creating-solutions-and-projects.md).

Sie können auch benutzerdefinierte Projekte und Elementvorlagen erstellen. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

## <a name="managing-projects-in-solution-explorer"></a>Verwalten von Projekten im Projektmappen-Explorer

Nachdem Sie ein neues Projekt erstellt haben, können Sie mit dem **Projektmappen-Explorer** Projekte und Projektmappen sowie zugehörige Elemente anzeigen und verwalten. Die folgende Abbildung zeigt den Projektmappen-Explorer mit einer C#-Projektmappe, die zwei Projekte enthält.

![Projektmappen-Explorer](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")

## <a name="see-also"></a>Siehe auch

[Visual Studio-IDE](../ide/visual-studio-ide.md)
