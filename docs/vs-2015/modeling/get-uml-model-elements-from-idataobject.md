---
title: Abrufen von UML-Modellelementen aus IDataObject | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a5f60338a8a856b4c6ef8fa913d6d7168ff67bb9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427036"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Abrufen von UML-Modellelementen aus IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn der Benutzer Elemente aus einer Quelle in ein Diagramm zieht, werden diese Elemente in einem `System.Windows.Forms.IDataObject` codiert. Die Codierung hängt vom Typ des Quellobjekts ab. Das folgende Fragment zeigt, wie die Elemente abgerufen werden, wenn die Quelle ein UML-Diagramm ist.  
  
> [!NOTE]
> Die meisten Vorgänge, die Sie für die Sie für UML-Modelle können ausgeführt werden, mithilfe der Typen in definiert, in den Assemblys **Microsoft.VisualStudio.Uml.Interfaces** und  **Microsoft.VisualStudio.ArchitectureTools.Extensibility**. Zu diesem Zweck müssen Sie jedoch einige Klassen verwenden, die Teil der Implementierung der UML-Modellierungstools sind. `ShapeElement` in diesem Fragment ist z. B. nicht mit der UML-Klasse `IShape` identisch. Um das Risiko von Inkonsistenzen im UML-Modell und in den Diagrammen zu reduzieren, sollten die Methoden nun dann für diese Implementierungsklassen verwendet werden, wenn es keine Alternative gibt.  
  
## <a name="code-sample"></a>Codebeispiel  
 Das Projekt muss die folgenden verweisen [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] Assemblys:  
  
 **Microsoft.VisualStudio.Modeling.Sdk.[version]**  
  
 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]**  
  
 **System.Windows.Forms**  
  
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
  
 Weitere Informationen zu `ElementGroupPrototype` und `Store` in dem die UML-Modellierungstools implementiert werden, finden Sie unter [Modellierungs-SDK für Visual Studio - domänenspezifische Sprachen](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md)   
 [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
