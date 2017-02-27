---
title: "Gewusst wie: Hinzuf&#252;gen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# Gewusst wie: Hinzuf&#252;gen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie dem [Arbeitsbereich des XML\-Schema\-Designers](../xml-tools/xml-schema-designer-workspace.md) Knoten aus dem XML\-Schema\-Explorer hinzugefügt werden.Knoten können einer XSD\-Designer\-Ansicht per Drag & Drop oder über das Kontextmenü des XML\-Schema\-Explorers hinzugefügt werden.Sie können auch Knoten hinzufügen, die als Ergebnis einer Suche zurückgegeben wurden und im XML\-Schema\-Explorer hervorgehoben sind.Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Knoten aus Schemaset\-Suchergebnissen zum Arbeitsbereich](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).  
  
> [!NOTE]
>  Dem [Arbeitsbereich des XML\-Schema\-Designers](../xml-tools/xml-schema-designer-workspace.md) können nur globale Knoten hinzugefügt werden.  
  
### So fügen Sie Knoten über das Kontextmenü des XML\-Explorers hinzu  
  
1.  Führen Sie die in [Gewusst wie: Erstellen und Bearbeiten einer XSD\-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md) beschriebenen Schritte aus.  
  
2.  Klicken Sie im XSD\-Explorer mit der rechten Maustaste auf den `PurchaseOrderType`\-Knoten.Wählen Sie **In Diagrammansicht anzeigen** aus.  
  
     Der `purchaseOrderType`\-Knoten wird auf der Entwurfsoberfläche der Diagrammansicht angezeigt.  
  
### So verschieben Sie Knoten per Drag & Drop in eine Ansicht  
  
1.  Klicken Sie mit der rechten Maustaste auf den `PurchaseOrderType`\-Knoten in der Diagrammansicht.Wählen Sie **In XML\-Schema\-Explorer anzeigen** aus.  
  
     Der Knoten wird im XML\-Schema\-Explorer hervorgehoben.  
  
2.  Klicken Sie mit der rechten Maustaste auf den `PurchaseOrderType`\-Knoten im XML\-Schema\-Explorer, und wählen Sie **Alle Verweise anzeigen** aus.  
  
     Der `purchaseOrder`\-Knoten wird hervorgehoben.  
  
3.  Ziehen Sie den `purchaseOrder`\-Knoten in die Diagrammansicht.  
  
     Der `purchaseOrder`\-Knoten und der `PurchaseOrderType`\-Knoten werden nebeneinander auf der Entwurfsoberfläche der Diagrammansicht angezeigt.Da die zwei Knoten miteinander verknüpft sind \(das `purchaseOrder`\-Element ist vom `PurchaseOrderType`\-Typ\), wird ein Pfeil zwischen den Elementen gezeichnet.  
  
### So fügen Sie Knoten mithilfe der Suchfunktion des Schema\-Explorers hinzu  
  
1.  Geben Sie "purchaseOrder" in das Suchtextfeld auf der [XML\-Explorer](../xml-tools/xml-schema-explorer.md)\-Symbolleiste ein, und klicken Sie auf die Suchschaltfläche.  
  
     ![Schlüsselwortsuche im XML&#45;Schema&#45;Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Die Suchergebnisse werden im XML\-Schema\-Explorer hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.  
  
2.  Fügen Sie die Suchergebnisse dem Arbeitsbereich hinzu, indem Sie im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **Hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken.  
  
     ![Suchergebnis im XML&#45;Schema&#45;Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Der `purchaseOrder`\-Knoten und der `PurchaseOrderType`\-Knoten werden nebeneinander auf der Entwurfsoberfläche der [Diagrammansicht](../xml-tools/graph-view.md) angezeigt.Da die zwei Knoten miteinander verknüpft sind \(das `purchaseOrder`\-Element ist vom `PurchaseOrderType`\-Typ\), wird ein Pfeil zwischen den Elementen gezeichnet.  
  
## Siehe auch  
 [XML\-Schema\-Explorer](../xml-tools/xml-schema-explorer.md)