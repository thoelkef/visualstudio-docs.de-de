---
title: Projektmappen und Projekte in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 06/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.savedeferredsaveprojectonclose
- vs.untrustedtemplateopeningdocuments
- Project Properties.FullPath
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.getopenfilename
- vs.addnewitem
- vs.encoding
- vs.addexistingitem
- Project Properties.URL
- VS.SolutionExplorer
- Project Properties.FileName
- SolutionProperties.Name
- VS.SaveChangesDlg
- vs.newproject
- VS.SolutionExplorer.Selection
- SolutionProperties.Path
- vs.getdirectoryname
- vs.addexistingsolutionitem
- SolutionProperties.Description
- vs.environment.solutions
- vs.saveordiscarddeferredsaveproject
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- vs.solutionpropertypages
- vs.solutionpropertypages.startupproject
- vs.solutionpropertypages.configurationsettings
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- workspaces
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- vs.solutionpropertypages.projectdependencies
- applications [Visual Studio]
- projects [Visual Studio], setting up
- miscellaneous files
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 35
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 28dfbb85790cfda2c3d840ce2d57468b5421bee0
ms.contentlocale: de-de
ms.lasthandoff: 06/23/2017

---
# <a name="solutions-and-projects-in-visual-studio"></a>Projektmappen und Projekte in Visual Studio
Beim Erstellen einer App, Anwendung, Website, Web App und eines Skripts, Plug-ins usw. in Visual Studio beginnen Sie mit einem *Projekt*. In funktionaler Hinsicht enthält ein Projekt alle Quellcodedateien, Symbole, Bilder, Datendateien und alles andere, was zu einem ausführbaren Programm, einer Website o. Ä. kompiliert werden soll oder für die Kompilierung benötigt wird.  Ein Projekt enthält außerdem alle Compilereinstellungen und andere Konfigurationsdateien, die möglicherweise von verschiedenen Diensten und Komponenten benötigt werden, mit denen Ihr Programm kommuniziert.

> [!NOTE]
>  Sie müssen weder Projektmappen noch Projekte verwenden, wenn Sie nicht möchten. Sie können die Dateien einfach in Visual Studio öffnen und mit der Bearbeitung Ihres Codes beginnen. Weitere Informationen finden Sie unter [Öffnen von beliebigen Ordnern in Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/).


 Auf struktureller Ebene handelt es sich bei einem Projekt um eine XML-Datei (*.vbproj, \*.csproj, \*.vcxproj), die eine virtuelle Ordnerhierarchie mit Pfaden zu allen Elementen, die es enthält, und den Buildeinstellungen definiert. In Visual Studio wird die Projektdatei im Projektmappen-Explorer verwendet, um Projektinhalte und Einstellungen anzuzeigen. Wenn Sie das Projekt kompilieren, verwendet das MSBuild-Modul die Projektdatei, um die ausführbare Datei zu erstellen. Sie können Projekts auch so anpassen, dass andere Arten von Ausgaben produziert werden.  

 Eine *Projektmappe*enthält in funktionaler Hinsicht und im Dateisystem ein Projekt, das wiederum mindestens ein Projekt sowie Buildinformationen, Visual Studio-Fenstereinstellungen sowie beliebige weitere Dateien, die nicht mit einem bestimmten Projekt verknüpft sind, enthalten kann. Auf struktureller Ebene handelt es sich bei einer Projektmappe um eine Textdatei in einem nativen Format, die normalerweise nicht manuell bearbeitet werden soll.  

 Einer Projektmappe ist eine *SUO*-Datei zugeordnet, in der Einstellungen und Konfigurationsinformationen für jeden Benutzer gespeichert sind, der am Projekt gearbeitet hat.  

 Das folgende Diagramm zeigt die Beziehung zwischen Projekten und Projektmappen und die Elemente, die sie logisch enthalten.  

 ![Visual Studio-Projekte und -Projektmappen](~/ide/media/vside-project-diagram.png)  

 Sie können auch benutzerdefinierte Projekte und Elementvorlagen erstellen. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).  

## <a name="creating-new-projects"></a>Erstellen neuer Projekte  
 Die einfachste Möglichkeit zum Erstellen eines neuen Projekts ist eine vordefinierte Projektvorlage, die eine Reihe grundlegender vorab generierten Codedateien, Konfigurationsdateien, Assets und Einstellungen für die ersten Schritte mit einer bestimmten Anwendungsart oder Website in einer bestimmten Programmiersprache enthält. Diese Vorlagen finden Sie im Hauptmenü im **Dialogfeld „Neues Projekt“**, wenn Sie **Datei &#124; Neu &#124; Projekt** oder **Datei &#124; Neu &#124; Website** auswählen und dann navigieren. Weitere Informationen finden Sie unter [Erstellen von Projekten und Projektmappen](../ide/creating-solutions-and-projects.md).  

## <a name="managing-projects-in-solution-explorer"></a>Verwalten von Projekten im Projektmappen-Explorer  
 Nachdem Sie ein neues Projekt erstellt haben, verwenden Sie den **Projektmappen-Explorer** , um Projekte und Projektmappen sowie zugehörige Elemente anzuzeigen und zu verwalten. Die folgende Abbildung zeigt den Projektmappen-Explorer mit einer C#-Projektmappe, die zwei Projekte enthält.  

 ![Projektmappen-Explorer](~/ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>In diesem Abschnitt  

-   [Erstellen von Projektmappen und Projekten](../ide/creating-solutions-and-projects.md)  

-   [Hinzufügen und Entfernen von Projektelementen](../ide/adding-and-removing-project-items.md)  

-   [Verwalten von Projekt- und Projektmappeneigenschaften](../ide/managing-project-and-solution-properties.md)  

-   [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)  

-   [Anwendungseigenschaften](../ide/application-properties.md)  

-   [Verwalten der Signierung von Assemblys und Manifesten](../ide/managing-assembly-and-manifest-signing.md)  

-   [Gewusst wie: Angeben eines Anwendungssymbols (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [Festlegen einer bestimmten .NET-Framework-Version](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>Siehe auch  
 [Visual Studio-IDE](../ide/visual-studio-ide.md)

