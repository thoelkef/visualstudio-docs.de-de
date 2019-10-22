---
title: UML-Modellelemente aus IDataObject Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66b4ffc312af89aa5852a1f4dad62fd328176df3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666075"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Abrufen von UML-Modellelementen aus IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn der Benutzer Elemente aus einer Quelle in ein Diagramm zieht, werden diese Elemente in einem `System.Windows.Forms.IDataObject` codiert. Die Codierung hängt vom Typ des Quellobjekts ab. Das folgende Fragment zeigt, wie die Elemente abgerufen werden, wenn die Quelle ein UML-Diagramm ist.

> [!NOTE]
> Die meisten Vorgänge, die Sie für UML-Modelle ausführen müssen, können mithilfe der Typen in ausgeführt werden, die in den Assemblys " **Microsoft. VisualStudio. Uml. Interfaces** " und " **Microsoft. VisualStudio. architecturetools. Extensibility**" definiert sind. Zu diesem Zweck müssen Sie jedoch einige Klassen verwenden, die Teil der Implementierung der UML-Modellierungstools sind. `ShapeElement` in diesem Fragment ist z. B. nicht mit der UML-Klasse `IShape` identisch. Um das Risiko von Inkonsistenzen im UML-Modell und in den Diagrammen zu reduzieren, sollten die Methoden nun dann für diese Implementierungsklassen verwendet werden, wenn es keine Alternative gibt.

## <a name="code-sample"></a>Codebeispiel
 Das Projekt muss auf die folgenden [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] Assemblys verweisen:

 **Microsoft. VisualStudio. Modeling. SDK. Versions**

 **Microsoft. VisualStudio. Modeling. SDK. Diagramms. Versions**

 **System. Windows. Forms**

```
using Microsoft.VisualStudio.Modeling;
  // for ElementGroupPrototype
using Microsoft.VisualStudio.Modeling.Diagrams;
  // for ShapeElement, DiagramDragEventArgs, DiagramPointEventArgs
… 
  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
                  (DiagramDragEventArgs dragEvent)
  {
     //ElementGroupPrototype is the container for
     //dragged and copied elements and toolbox items.
     ElementGroupPrototype prototype =
        dragEvent.Data.
        GetData(typeof(ElementGroupPrototype))
                     as ElementGroupPrototype;
     // Locate the originals in the implementation store.
     IElementDirectory implementationDirectory =
        dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

     return  prototype.ProtoElements.Select(
       prototypeElement =>
       {
          ModelElement element = implementationDirectory
                .FindElement(prototypeElement.ElementId);
          ShapeElement shapeElement = element as ShapeElement;
          if (shapeElement != null)
          {
            // Dragged from a diagram.
            return shapeElement.ModelElement as IElement;
          }
          else
          {
            // Dragged from UML Model Explorer.
            return element as IElement;
          }
        });
    }
```

 Weitere Informationen zu `ElementGroupPrototype` und den `Store`, in denen die UML-Modellierungstools implementiert sind, finden Sie unter [Modellierungs-SDK für Visual Studio-domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="see-also"></a>Siehe auch
 [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md) [Definieren eines Menübefehls in einem Modellierungs Diagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
