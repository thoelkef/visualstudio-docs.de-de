---
title: "Gewusst wie: Hinzuf&#252;gen von Knoten aus Schemaset-Suchergebnissen zum Arbeitsbereich | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# Gewusst wie: Hinzuf&#252;gen von Knoten aus Schemaset-Suchergebnissen zum Arbeitsbereich
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird erläutert, wie dem Arbeitsbereich Knoten hinzugefügt werden, die im XML\-Schema\-Explorer als Ergebnis einer Schlüsselwortsuche hervorgehoben sind.  
  
> [!NOTE]
>  Dem [Arbeitsbereich](../xml-tools/xml-schema-designer-workspace.md) können nur globale Knoten hinzugefügt werden.  
  
 In diesem Beispiel wird das Beispiel\-[Bestellungsschema](../xml-tools/sample-xsd-file-purchase-order-schema.md) verwendet.  
  
### So fügen Sie Knoten aus Ergebnissen einer Schemasetsuche hinzu  
  
1.  Führen Sie die in [Gewusst wie: Erstellen und Bearbeiten einer XSD\-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md) beschriebenen Schritte aus.  
  
2.  Geben Sie "purchaseOrder" in das Suchtextfeld auf der [XML\-Explorer](../xml-tools/xml-schema-explorer.md)\-Symbolleiste ein, und klicken Sie auf die Suchschaltfläche.  
  
     ![Schlüsselwortsuche im XML&#45;Schema&#45;Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Die Suchergebnisse werden im XML\-Schema\-Explorer hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.  
  
3.  Fügen Sie die Suchergebnisse dem Arbeitsbereich hinzu, indem Sie im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **Hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken.  
  
     ![Suchergebnis im XML&#45;Schema&#45;Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Der `purchaseOrder`\-Knoten und der `PurchaseOrderType`\-Knoten werden nebeneinander auf der Entwurfsoberfläche der [Diagrammansicht](../xml-tools/graph-view.md) angezeigt.Da die zwei Knoten miteinander verknüpft sind \(das `purchaseOrder`\-Element ist vom `PurchaseOrderType`\-Typ\), wird ein Pfeil zwischen den Elementen gezeichnet.