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
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- projects [Visual Studio], setting up
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca3094b3bfe35381236798164fa18e58304bae3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="solutions-and-projects-in-visual-studio"></a>Projektmappen und Projekte in Visual Studio
Wenn Sie eine App, eine Website, ein Plug-In usw. in Visual Studio erstellen, beginnen Sie mit einem *Projekt*. In funktionaler Hinsicht enthält ein Projekt alle Quellcodedateien, Symbole, Bilder, Datendateien und alles andere, was zu einem ausführbaren Programm, einer Website o. Ä. kompiliert werden soll oder für die Kompilierung benötigt wird. Ein Projekt enthält außerdem alle Compilereinstellungen und andere Konfigurationsdateien, die möglicherweise von verschiedenen Diensten und Komponenten benötigt werden, mit denen Ihr Programm kommuniziert.  

> [!NOTE]
>  Sie müssen weder Projektmappen noch Projekte verwenden, wenn Sie nicht möchten. Sie können die Dateien einfach in Visual Studio öffnen und mit der Bearbeitung Ihres Codes beginnen. Weitere Informationen finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).  

Eine Projektdatei (.vbproj, .csproj, .vcxproj) ist eine XML-Datei, die eine virtuelle Ordnerhierarchie mit Pfaden zu allen Elementen im Projekt definiert. Sie enthält außerdem die Buildeinstellungen. Um den Inhalt einer Projektdatei anzuzeigen, können Sie den Projektnamen im Projektmappen-Explorer auswählen. Führen Sie anschließend im Kontextmenü einen Rechtsklick aus, und wählen Sie **Projekt entladen** aus. Öffnen Sie erneut das Kontextmenü, und wählen Sie **\<Projektname\> bearbeiten** aus.  

In Visual Studio wird die Projektdatei im Projektmappen-Explorer verwendet, um Projektinhalte und Einstellungen anzuzeigen. Wenn Sie das Projekt kompilieren, verwendet das MSBuild-Modul die Projektdatei, um die ausführbare Datei zu erstellen. Sie können Projekte auch so anpassen, dass andere Arten von Ausgaben produziert werden.  

Eine *Projektmappe* enthält in funktionaler Hinsicht und im Dateisystem ein Projekt, das wiederum mindestens ein verwandtes Projekt sowie Buildinformationen, Visual Studio-Fenstereinstellungen sowie beliebige weitere Dateien, die nicht mit einem bestimmten Projekt verknüpft sind, enthalten kann. Eine Projektmappe wird von einer Textdatei (.sln) in einem individuellen Format beschrieben; diese soll normalerweise nicht manuell bearbeitet werden.  

Einer Projektmappe ist eine *SUO*-Datei zugeordnet, in der Einstellungen und Konfigurationsinformationen für jeden Benutzer gespeichert sind, der am Projekt gearbeitet hat.  

 Das folgende Diagramm zeigt die Beziehung zwischen Projekten und Projektmappen und die Elemente, die sie logisch enthalten.  

 ![Visual Studio-Projekte und -Projektmappen](../ide/media/vside-project-diagram.png)  

## <a name="creating-new-projects"></a>Erstellen neuer Projekte  
 Die einfachste Möglichkeit zum Erstellen eines neuen Projekts ist eine vordefinierte Projektvorlage, die eine Reihe grundlegender vorab generierter Codedateien, Konfigurationsdateien, Objekte und Einstellungen für die ersten Schritte mit einer bestimmten Anwendungsart oder Website in einer bestimmten Programmiersprache enthält. Diese Vorlagen finden Sie im Dialogfeld **Neues Projekt** oder **Neue Website**, wenn Sie **Datei**, **Neu**, **Projekt** oder **Datei**, **Neu**, **Website** auswählen. Weitere Informationen finden Sie unter [Erstellen von Projekten und Projektmappen](../ide/creating-solutions-and-projects.md).  

Sie können auch benutzerdefinierte Projekte und Elementvorlagen erstellen. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).  

## <a name="managing-projects-in-solution-explorer"></a>Verwalten von Projekten im Projektmappen-Explorer  
 Nachdem Sie ein neues Projekt erstellt haben, verwenden Sie den **Projektmappen-Explorer** , um Projekte und Projektmappen sowie zugehörige Elemente anzuzeigen und zu verwalten. Die folgende Abbildung zeigt den Projektmappen-Explorer mit einer C#-Projektmappe, die zwei Projekte enthält.  

 ![Projektmappen-Explorer](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>In diesem Abschnitt  

-   [Erstellen von Projektmappen und Projekten](../ide/creating-solutions-and-projects.md)  

-   [Hinzufügen und Entfernen von Projektelementen](../ide/adding-and-removing-project-items.md)  

-   [Managing Project and Solution Properties (Verwalten von Projekt- und Projektmappeneigenschaften)](../ide/managing-project-and-solution-properties.md)  

-   [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)  

-   [Anwendungseigenschaften](../ide/application-properties.md)  

-   [Verwalten der Signierung von Assemblys und Manifesten](../ide/managing-assembly-and-manifest-signing.md)  

-   [Vorgehensweise: Angeben eines Anwendungssymbols (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [Festlegen einer bestimmten .NET-Framework-Zielversion](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>Siehe auch  
 [Visual Studio-IDE](../ide/visual-studio-ide.md)
