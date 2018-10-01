---
title: Abrufen von UML-Modellelementen aus IDataObject | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: a69a6f20fdccdce9d8795c68bf0a70c74604428b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521783"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Abrufen von UML-Modellelementen aus IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Abrufen von UML-Modellelementen aus IDataObject](https://docs.microsoft.com/visualstudio/modeling/get-uml-model-elements-from-idataobject).  
  
Wenn der Benutzer Elemente aus einer Quelle in ein Diagramm zieht, werden diese Elemente in einem `System.Windows.Forms.IDataObject` codiert. Die Codierung hängt vom Typ des Quellobjekts ab. Das folgende Fragment zeigt, wie die Elemente abgerufen werden, wenn die Quelle ein UML-Diagramm ist.  
  
> [!NOTE]
>  Die meisten Vorgänge, die Sie für die Sie für UML-Modelle können ausgeführt werden, mithilfe der Typen in definiert, in den Assemblys **Microsoft.VisualStudio.Uml.Interfaces** und  **Microsoft.VisualStudio.ArchitectureTools.Extensibility**. Zu diesem Zweck müssen Sie jedoch einige Klassen verwenden, die Teil der Implementierung der UML-Modellierungstools sind. `ShapeElement` in diesem Fragment ist z. B. nicht mit der UML-Klasse `IShape` identisch. Um das Risiko von Inkonsistenzen im UML-Modell und in den Diagrammen zu reduzieren, sollten die Methoden nun dann für diese Implementierungsklassen verwendet werden, wenn es keine Alternative gibt.  
  
## <a name="code-sample"></a>Codebeispiel  
 Das Projekt muss die folgenden verweisen [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] Assemblys:  
  
 **Microsoft.VisualStudio.Modeling.Sdk. [Version]**  
  
 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams. [Version]**  
  
 **"System.Windows.Forms"**  
  
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



