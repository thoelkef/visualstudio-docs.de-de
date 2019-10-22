---
title: Öffnen eines UML-Modells mithilfe der Visual Studio-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 694f10fb0af440513331aa6e76dbf9a59a16d340
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668507"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Öffnen eines UML-Modells über die Visual Studio-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Modelle und Diagramme auch über die API in der Visual Studio-Benutzeroberfläche öffnen.

 Wenn Sie lediglich ein Modell im Programmcode lesen möchten, ohne dass es dem Benutzer angezeigt wird, können Sie die folgenden Methoden verwenden:

- Der Modellbus von Visual Studio ermöglicht den Zugriff auf Modelle und die darin enthaltenen Elemente und bietet eine Standardmethode zum Erstellen von Links zwischen Modellen. Weitere Informationen finden Sie unter [integrieren von UML-Modellen in andere Modelle und Tools](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Ein Modell kann im schreibgeschützten Modus geöffnet werden. Weitere Informationen finden Sie unter [Lesen eines UML-Modells im Programmcode](../modeling/read-a-uml-model-in-program-code.md).

## <a name="Showing"></a>Öffnen von Modellen und Diagrammen in Visual Studio
 Verwenden Sie die Visual Studio-Standard-API `EnvDTE.DTE`, um ein Modell auf der Benutzeroberfläche zu öffnen. Für Modellierungsprojektelemente können zwei hilfreiche Umwandlungen ausgeführt werden:

- `EnvDTE.Project` kann in `IModelingProject` umgewandelt werden (und umgekehrt), sofern es sich bei dem Projekt um ein Modellierungsprojekt handelt und das Projekt in der aktuellen Anwendungsdomäne geladen ist.

- `EnvDTE.ProjectItem` kann zu `IDiagramContext` umgewandelt werden (und umgekehrt), wenn es sich bei dem Element um ein UML-Diagramm handelt.

  Für das folgende Beispiel müssen vom Projekt die folgenden Verweise importiert werden:

- EnvDTE

- Microsoft.VisualStudio.ArchitectureTools.Extensibility

- Microsoft.VisualStudio.Modeling.Sdk.[Version]

- Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[Version]

- Microsoft.VisualStudio.Shell.Immutable.[version]

- Microsoft.VisualStudio.Uml.Interfaces

- System.ComponentModel.Composition

  In diesem Beispiel wird ein UML-Modell in Visual Studio geöffnet:

```
using EnvDTE; // Visual Studio API for loading diagrams
using
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   // for ICommandExtension and other handler types
using Microsoft.VisualStudio.Uml.Classes;
   // for basic UML types
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   // for model construction methods
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
                             // for IDiagram
...
```

 In einer Visual Studio-Erweiterung können Sie diese Deklaration vornehmen, um Zugriff auf den Hostdienstanbieter zu erhalten:

```
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}
...
```

 In einer Methode können Sie auf ein Projekt (beispielsweise das aktuelle Projekt) zugreifen:

```
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;
IModelingProject modelingProject = project as IModelingProject;
if (modelingProject == null) return; // not a modeling project

// Access the model's store and contents.
IModelStore store = modelingProject.Store;
foreach (IElement element in store.Root.OwnedElements) {...}

// Open all the project's diagrams.
foreach (ProjectItem item in project.ProjectItems)
{
     IDiagramContext modelingItem = item as IDiagramContext;
     if (modelingItem == null)
         continue; // not a model diagram
     IDiagram diagram = modelingItem.CurrentDiagram;
     if (diagram == null)
     {
        // Diagram is closed. Open it.
        item.Open().Activate();
        diagram = modelingItem.CurrentDiagram;
     }
     // Access the shapes.
     foreach (IShape<IElement> shape
               in diagram.GetChildShapes<IElement>())
     {
       IElement displayedElement = shape.Element;
       ...
     }
   }
}
```

## <a name="see-also"></a>Siehe auch
 [Programmieren mit der UML-API Erweitern von](../modeling/programming-with-the-uml-api.md) [UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)
