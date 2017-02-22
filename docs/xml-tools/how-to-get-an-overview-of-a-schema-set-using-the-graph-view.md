---
title: "Gewusst wie: Anzeigen einer &#220;bersicht &#252;ber ein Schemaset in der Diagrammansicht | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Anzeigen einer &#220;bersicht &#252;ber ein Schemaset in der Diagrammansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie mithilfe der [Diagrammansicht](../xml-tools/graph-view.md) eine allgemeine Ansicht der Knoten in einem Schemaset und der Beziehungen zwischen den Knoten anzeigen.  
  
### So erstellen Sie eine neue XSD\-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an  
  
1.  Erstellen Sie eine neue XML\-Schemadatei, und speichern Sie die Datei unter dem Namen "Relationships.xsd".  
  
2.  Klicken Sie in der Ausgangsansicht auf den Link **Verwenden Sie den XML\-Editor, um die zugrunde liegende XML\-Schemadatei anzuzeigen und zu bearbeiten**.  
  
3.  Kopieren Sie den XML\-Schemabeispielcode aus [XML\-Beispielschema: Beziehungen](../xml-tools/sample-xsd-file-relationships.md), und fügen Sie ihn ein, um den Standardcode zu ersetzen, der der neuen XSD\-Datei hinzugefügt wurde.  
  
4.  Klicken Sie mit der rechten Maustaste an einer beliebigen Stelle im XML\-Editor, und wählen Sie **Ansicht\-Designer** aus.  
  
5.  Wählen Sie auf der XSD\-Symbolleiste die Diagrammansicht aus.  
  
6.  Markieren Sie im XML\-Schema\-Explorer den Knoten **Schemaset**, und ziehen Sie den Knoten von der Entwurfsoberfläche in die Diagrammansicht.Nun sollten alle globalen Knoten und Verbindungspfeile zwischen den Knoten mit Beziehungen angezeigt werden.  
  
     ![Diagrammansicht](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  Klicken Sie auf der Entwurfsoberfläche auf einen Knoten, und überprüfen Sie in der Breadcrumb\-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.  
  
8.  Klicken Sie auf der Entwurfsoberfläche mit der rechten Maustaste auf einen Elementknoten, und wählen Sie **Beispiel\-XML generieren** aus, um das XML\-Instanzdokument anzuzeigen.