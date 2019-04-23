---
title: Lesen ein UML-Modells im Programmcode | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 48d70901a2d616031eeed197b639f3a7bb7336c3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092993"
---
# <a name="read-a-uml-model-in-program-code"></a>Lesen eines UML-Modells im Programmcode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können mit der UML-API ein UML-Modell und die zugehörigen Diagramme laden.  
  
## <a name="Reading"></a> Lesen eines Modells im Programmcode  
 Verwenden Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], um auf den Inhalt eines Modells zuzugreifen, ohne ihn in einem `ModelingProject.LoadReadOnly()`-Fenster anzuzeigen.  
  
 Zum Beispiel:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;   
               // for IElement  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;   
               // for ModelingProject  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
               // for IModelStore  
...   
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";  
using (IModelingProjectReader projectReader =  
           ModelingProject.LoadReadOnly(projectPath))  
{  
   IModelStore store = projectReader.Store;  
   foreach (IClass umlClass in store.AllInstances<IClass>())  
   {   
       ...  
   }  
}  
```  
  
 Wenn Sie die Formen in einem Diagramm lesen möchten, müssen Sie das Projekt und dann das Diagramm lesen.  
  
 Zum Beispiel:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram  
...  
foreach (string diagramFile in projectReader. DiagramFileNames)  
{   
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);  
  foreach (IShape<IElement> shape   
         in diagram.GetChildShapes<IElement>())  
  { ... }  
}  
```  
  
## <a name="alternative-methods"></a>Alternative Methoden  
 Bei vielen Anwendungen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Modelbus können Sie Verweise auf Modelle und die darin enthaltenen Elemente mit mehr Stabilität und Flexibilität als die in diesem Thema beschriebenen Methoden. Diese Funktion stellt eine Standardmethode zum Erstellen von Links zwischen beliebigen Elementen im gleichen oder in unterschiedlichen Modellen bereit. Weitere Informationen finden Sie unter [Integrieren von UML-Modellen in andere Modelle und Tools](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 Modelle und Diagramme können auch mithilfe der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-API in der Benutzeroberfläche geöffnet werden. Weitere Informationen finden Sie unter [öffnen ein UML-Modells mithilfe der Visual Studio-API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
## <a name="Standalone"></a> Eigenständige Anwendungen  
 Das Beispiel im vorhergehenden Abschnitt funktioniert in Visual Studio-Erweiterungen. Es ist möglich, ein Modell in einer eigenständigen Anwendung zu lesen, Sie müssen jedoch einige Verweise auf das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekt hinzufügen.  
  
> [!NOTE]
>  Die Details im Zusammenhang mit dem Lesen von Modellen in eigenständigen Anwendungen werden sich in zukünftigen Versionen des Produkts voraussichtlich ändern. Einige Funktionen der aktuellen Version sind in zukünftigen Versionen möglicherweise nicht mehr verfügbar.  
  
#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>So fügen Sie Verweise hinzu, um ein Modell in einer eigenständigen Anwendung zu lesen  
  
1. Klicken Sie im Projektmappen-Explorer mit der Maustaste des Projekts, in dem Sie die Anwendung erstellen, und klicken Sie dann auf **Eigenschaften**. Im Eigenschaften-Editor in der **Anwendung** Registerkarte **Zielframework** auf die erforderliche Version von .NET Framework.  
  
2. Fügen Sie die [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]-Verweise hinzu, die Sie für den Zugriff auf UML-Modelle benötigen. In der Regel sind dies die folgenden Verweise:  
  
   - Microsoft.VisualStudio.Uml.Interfaces.dll  
  
   - Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
3. Zusätzlich zu den in den vorherigen Abschnitten aufgeführten verweisen, fügen Sie die folgenden Projektverweise aus **\Programme\Microsoft Visual Studio [Version] \Common7\IDE\PrivateAssemblies**:  
  
   - Microsoft.VisualStudio.Uml.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll  
  
     Wenn Sie Diagramme in der Anwendung lesen möchten, benötigen Sie möglicherweise auch die folgenden Verweise:  
  
   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md)   
 [Erweitern von UML-Modellen und -Diagrammen](../modeling/extend-uml-models-and-diagrams.md)
