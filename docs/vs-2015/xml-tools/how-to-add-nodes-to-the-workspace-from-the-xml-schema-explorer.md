---
title: 'Vorgehensweise: Hinzufügen von Knoten mit dem Arbeitsbereich aus der XML-Schema-Explorer | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a6ef4e4e019406d9c317ccd90eabcb89e25a6f36
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220102"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Gewusst wie: Hinzufügen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In diesem Thema wird erläutert, wie Sie zum Hinzufügen von Knoten der [XML-Schema-Designer-Arbeitsbereich](../xml-tools/xml-schema-designer-workspace.md) vom XML-Schema-Explorer. Knoten können einer XSD-Designer-Ansicht per Drag & Drop oder über das Kontextmenü des XML-Schema-Explorers hinzugefügt werden. Sie können auch Knoten hinzufügen, die als Ergebnis einer Suche zurückgegeben wurden und im XML-Schema-Explorer hervorgehoben sind. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen Schemas legen Sie Knoten aus Suchergebnissen zum Arbeitsbereich](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).  
  
> [!NOTE]
>  Nur globale Knoten hinzugefügt werden können, um die [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md).  
  
### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>So fügen Sie Knoten über das Kontextmenü des XML-Explorers hinzu  
  
1.  Führen Sie die Schritte in [Vorgehensweise: Erstellen und Bearbeiten einer XSD-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Klicken Sie im XSD-Explorer mit der rechten Maustaste auf den `PurchaseOrderType`-Knoten. Wählen Sie **in Diagrammansicht anzeigen**.  
  
     Der `purchaseOrderType`-Knoten wird auf der Entwurfsoberfläche der Diagrammansicht angezeigt.  
  
### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>So verschieben Sie Knoten per Drag & Drop in eine Ansicht  
  
1.  Klicken Sie mit der rechten Maustaste auf den `PurchaseOrderType`-Knoten in der Diagrammansicht. Wählen Sie **im XML-Schema-Explorer anzeigen**.  
  
     Der Knoten wird im XML-Schema-Explorer hervorgehoben.  
  
2.  Klicken Sie mit der rechten Maustaste auf die `PurchaseOrderType` Knoten im XML-Schema-Explorer, und wählen **alle Verweise anzeigen**.  
  
     Der `purchaseOrder`-Knoten wird hervorgehoben.  
  
3.  Ziehen Sie den `purchaseOrder`-Knoten in die Diagrammansicht.  
  
     Der `purchaseOrder`-Knoten und der `PurchaseOrderType`-Knoten werden nebeneinander auf der Entwurfsoberfläche der Diagrammansicht angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.  
  
### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>So fügen Sie Knoten mithilfe der Suchfunktion des Schema-Explorers hinzu  
  
1.  Geben Sie "PurchaseOrder" in das Suchfeld ein, der die [XML-Explorer](../xml-tools/xml-schema-explorer.md) Symbolleiste, und klicken Sie auf die Schaltfläche "Suchen".  
  
     ![XML-Schema-Explorer-Schlüsselwortsuche](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Die Suchergebnisse werden im XML-Schema-Explorer hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.  
  
2.  Die Ergebnisse der Suche zu Arbeitsbereich hinzufügen, indem Sie auf die **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** auf den Bereich auf die Schaltfläche.  
  
     ![XML-Schema-Explorer-Suchergebnis](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Die `purchaseOrder` Knoten und die `PurchaseOrderType` -Knoten werden nebeneinander auf der Entwurfsoberfläche des der [Diagrammansicht](../xml-tools/graph-view.md). Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)



