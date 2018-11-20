---
title: Programmieren mit der UML-API | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d5670b0c0806d59119e1a1af87bae5642255c5a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793177"
---
# <a name="programming-with-the-uml-api"></a>Programmieren mit der UML-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die UML-API von Visual Studio können Sie das Schreiben von Code zum Erstellen, lesen und Aktualisieren von UML-Modellen und Diagrammen. Welche Versionen von Visual Studio UML-Modelle unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 In den folgenden Themen werden die API und die API-Referenzseiten beschrieben.  
  
|Thema|Beschriebene Beispieltypen und -methoden|Beschriebene Funktionen|  
|-----------|-----------------------------------------|------------------------|  
|[Navigieren in Beziehungen mit der UML-API](../modeling/navigate-relationships-with-the-uml-api.md)|UML-Elemente und ihre Eigenschaften und Zuordnungen. Zum Beispiel "IElement" und die zugehörigen Nachfolgerelemente wie IClass, IActivity, IUseCase, IComponent, IInteraction, IModel, IPackage.|In Visual Studio entsprechen UML-Modelle der UML-Spezifikationsversion 2.1.2, die zur abgerufen werden kann die [UML-Ressourcenseite](http://go.microsoft.com/fwlink/?LinkId=160796). Jeder Typ ist eine Schnittstelle, die den gleichen Namen wie der UML-Typ hat, dem jedoch ein "I" vorangestellt ist.|  
|[Erstellen von Elementen und Beziehungen in UML-Modellen](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|Jeder Elementtyp verfügt über Methoden zum Erstellen seiner untergeordneten Elemente.|  
|[Anzeigen eines UML-Modells in Diagrammen](../modeling/display-a-uml-model-on-diagrams.md)|IShape, IDiagram<br /><br /> IShape.Move()|Jedes Element in einem Modell kann als Form in einem Diagramm dargestellt werden. In einigen Fällen können Sie für die einzelnen Objekte neue Formen erstellen. Sie können diese Formen verschieben, ihre Größe ändern, mit Farbe versehen und reduzieren oder erweitern.|  
|[Navigieren im UML-Modell](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|Das Modell wird im Modellspeicher gespeichert.<br /><br /> Über den Diagrammkontext erhalten Sie Zugriff auf das aktuelle Diagramm und den Speicher.|  
|[Verknüpfen von UML-Modellaktualisierungen mithilfe von Transaktion](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|Sie können eine Reihe von Änderungen zu einer Transaktion verknüpfen.|  
|[Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|Sie können die Funktionalität eines Diagramms erweitern, indem Sie Befehle definieren, die per Doppelklick und das Ziehen in das Diagramm aufgerufen werden.|  
|[Definieren von Validierungseinschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|Sie können Validierungsregeln definieren, mit denen Sie sicherstellen können, dass ein Modell angegebene Einschränkungen erfüllt.|  
|[Abrufen von UML-Modellelementen aus IDataObject](../modeling/get-uml-model-elements-from-idataobject.md)|IElement, IShape|Wenn ein Element aus dem UML-Modell-Explorer oder einem UML-Diagramm in ein anderes Diagramm oder eine andere Anwendung gezogen wird, wird es als IDataObject serialisiert.|  
|[Bearbeiten von UML-Sequenzdiagrammen mit der UML-API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IInteraction, ILifeline, IMessage|Das Erstellen und Aktualisieren eines Interaktionsdiagramms unterscheidet sich leicht vom Umgang mit den anderen Diagrammtypen.|  
|[Erweitern von Ebenendiagrammen](../modeling/extend-layer-diagrams.md)|ILayer, ILayerDiagram|Sie können Code schreiben, um Ebenendiagramme zu erstellen und zu bearbeiten sowie Programmcode anhand der Diagramme zu prüfen.|  
  
## <a name="about-the-implementation"></a>Informationen zur Implementierung  
 Die UML-Modellierungstools basieren auf [!INCLUDE[dsl](../includes/dsl-md.md)]. Jedes Paket und jedes Diagramm wird durch ein [!INCLUDE[dsl](../includes/dsl-md.md)]-Modell dargestellt. Die Konsistenz zwischen den Paketen und Diagrammen wird durch eine Auflistung von Regeln und anderen Methoden aufrecht erhalten.  
  
 Typen von dieser Plattform sind in einigen der Assemblys sichtbar, auf die Sie zum Schreiben von UML-Erweiterungen verweisen. Erweiterungen der UML-Tools können zwar über die [!INCLUDE[dsl](../includes/dsl-md.md)]-API erstellt werden, dabei ist jedoch Folgendes zu bedenken:  
  
-   Es kann vorkommen, dass scheinbar einfache Änderungen zu Inkonsistenzen führen und unerwartete Auswirkungen haben.  
  
-   Die Implementierung kann sich in der Zukunft ändern, sodass mit der [!INCLUDE[dsl](../includes/dsl-md.md)]-API vorgenommene Anpassungen nicht mehr funktionieren.  
  
## <a name="the-api-assemblies"></a>API-Assemblys  
 In der folgenden Tabelle werden die Assemblys für die Erweiterung der UML-Tools und die empfohlenen Namespaces zusammengefasst.  
  
|Assembly|Namespaces|Bietet Zugriff auf:|  
|--------------|----------------|-------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces|(Alle)|UML-Typen|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml>|[Methoden zur Clustererstellung](../modeling/create-elements-and-relationships-in-uml-models.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation>|[Diagramme und Formen](../modeling/display-a-uml-model-on-diagrams.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility>|[Das Modellierungsprojekt](../modeling/read-a-uml-model-in-program-code.md)|  
|Microsoft.VisualStudio.Modeling.Sdk.[Version]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[Menübefehlserweiterung](../modeling/define-a-menu-command-on-a-modeling-diagram.md).<br /><br /> [Verknüpfte Transaktionen zum Rückgängigmachen](../modeling/link-uml-model-updates-by-using-transactions.md).|  
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[Validierung](../modeling/define-validation-constraints-for-uml-models.md)|  
||(andere Namespaces)|Nur für erweiterte Verwendung empfohlen|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[Version]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[Gestenhandler](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).|  
||(andere Namespaces)|Nur für erweiterte Verwendung empfohlen|  
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|<xref:Microsoft.VisualStudio.TeamFoundation.WorkItemTracking>|[Links zu Arbeitsaufgaben](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.WorkItemTracking.Client|<xref:Microsoft.TeamFoundation.WorkItemTracking.Client>|[Arbeitsaufgaben und ihren Feldern](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.Client|<xref:Microsoft.TeamFoundation.Client>|[Arbeitsaufgaben und ihren Feldern](../modeling/define-a-work-item-link-handler.md).|  
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[Export und Import für MEF-Komponenten](../modeling/define-and-install-a-modeling-extension.md)|  
|System.Linq|<xref:System.Linq>|[Einfache Bearbeitung von Auflistungen, insbesondere bei Beziehungen](../modeling/navigate-relationships-with-the-uml-api.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)   
 [API-Referenz für UML-Modellierungserweiterbarkeit](../modeling/api-reference-for-uml-modeling-extensibility.md)



