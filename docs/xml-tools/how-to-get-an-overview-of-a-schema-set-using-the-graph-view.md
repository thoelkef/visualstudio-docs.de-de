---
title: "Vorgehensweise: erhalten einen Überblick über die Diagrammansicht ein Schemaset | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d9499e9972f32998b66be23d60acb8c585776d62
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Gewusst wie: Anzeigen einer Übersicht über ein Schemaset in der Diagrammansicht
Dieses Thema beschreibt, wie die [Diagrammansicht](../xml-tools/graph-view.md) um einen allgemeinen Überblick über die Knoten in einem Schemaset und die Beziehungen zwischen den Knoten anzuzeigen.  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an  
  
1.  Erstellen Sie eine neue XML-Schemadatei, und speichern Sie die Datei unter dem Namen "Relationships.xsd".  
  
2.  Klicken Sie auf die **verwenden Sie den XML-Editor, anzeigen und bearbeiten die zugrunde liegende XML-Schemadatei** Link in der Ausgangsansicht auf.  
  
3.  Kopieren Sie die XML-schemabeispielcode aus [XML-Beispielschema: Beziehungen](../xml-tools/sample-xsd-file-relationships.md) und fügen Sie ihn, um den Standardcode zu ersetzen, der die neue XSD-Datei hinzugefügt wurde.  
  
4.  Mit der rechten Maustaste an einer beliebigen Stelle in der XML-Editor, und wählen Sie **Sicht-Designer**.  
  
5.  Wählen Sie auf der XSD-Symbolleiste die Diagrammansicht aus.  
  
6.  Wählen Sie **Schemaset** Knoten im XML-Schema-Explorer klicken und ziehen Sie den Knoten Suface der Diagrammansicht zu entwerfen. Nun sollten alle globalen Knoten und Verbindungspfeile zwischen den Knoten mit Beziehungen angezeigt werden.  
  
     ![Diagrammansicht](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  Klicken Sie auf der Entwurfsoberfläche auf einen Knoten, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.  
  
8.  Rick Klick auf einen Elementknoten, auf die Muster, die Entwurfsoberfläche, und wählen **Beispiel-XML generieren** auf die XML-Instanzdokument anzuzeigen.