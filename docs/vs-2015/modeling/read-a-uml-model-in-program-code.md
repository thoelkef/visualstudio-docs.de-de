---
title: Lesen eines UML-Modells im Programmcode | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bbc55204987f4b6ea0d45c4228f6c194f1ebaf64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671312"
---
# <a name="read-a-uml-model-in-program-code"></a>Lesen eines UML-Modells im Programmcode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können mit der UML-API ein UML-Modell und die zugehörigen Diagramme laden.

## <a name="reading-a-model-in-program-code"></a><a name="Reading"></a> Lesen eines Modells im Programm Code
 Verwenden Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], um auf den Inhalt eines Modells zuzugreifen, ohne ihn in einem `ModelingProject.LoadReadOnly()`-Fenster anzuzeigen.

 Beispiel:

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

 Beispiel:

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
 Bei vielen Anwendungen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] können Sie mithilfe von ModelBus auf Modelle und Elemente innerhalb der Anwendungen verweisen, und zwar mit größerer Stabilität und flexibler als mit den in diesem Thema beschriebenen Methoden. Diese Funktion stellt eine Standardmethode zum Erstellen von Links zwischen beliebigen Elementen im gleichen oder in unterschiedlichen Modellen bereit. Weitere Informationen finden Sie unter [integrieren von UML-Modellen in andere Modelle und Tools](../modeling/integrate-uml-models-with-other-models-and-tools.md).

 Modelle und Diagramme können auch mithilfe der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-API in der Benutzeroberfläche geöffnet werden. Weitere Informationen finden Sie unter [Öffnen eines UML-Modells mithilfe der Visual Studio-API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="stand-alone-applications"></a><a name="Standalone"></a> Eigenständige Anwendungen
 Das Beispiel im vorhergehenden Abschnitt funktioniert in Visual Studio-Erweiterungen. Es ist möglich, ein Modell in einer eigenständigen Anwendung zu lesen, Sie müssen jedoch einige Verweise auf das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekt hinzufügen.

> [!NOTE]
> Die Details im Zusammenhang mit dem Lesen von Modellen in eigenständigen Anwendungen werden sich in zukünftigen Versionen des Produkts voraussichtlich ändern. Einige Funktionen der aktuellen Version sind in zukünftigen Versionen möglicherweise nicht mehr verfügbar.

#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>So fügen Sie Verweise hinzu, um ein Modell in einer eigenständigen Anwendung zu lesen

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, in dem Sie die Anwendung aufbauen, und klicken Sie dann auf **Eigenschaften**. Legen Sie im Eigenschaften-Editor auf der Registerkarte **Anwendung** das **Ziel Framework** auf die erforderliche Version des .NET Framework fest.

2. Fügen Sie die [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]-Verweise hinzu, die Sie für den Zugriff auf UML-Modelle benötigen. In der Regel sind dies die folgenden Verweise:

   - Microsoft.VisualStudio.Uml.Interfaces.dll

   - Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll

3. Fügen Sie zusätzlich zu den in den vorherigen Abschnitten aufgeführten verweisen die folgenden Projekt Verweise aus **\Programme\Microsoft Visual Studio [Version] \common7\ide\privateassemblys**hinzu:

   - Microsoft.VisualStudio.Uml.dll

   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll

     Wenn Sie Diagramme in der Anwendung lesen möchten, benötigen Sie möglicherweise auch die folgenden Verweise:

   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll

## <a name="see-also"></a>Weitere Informationen
 [Programmieren mit der UML-API Erweitern von](../modeling/programming-with-the-uml-api.md) [UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)
