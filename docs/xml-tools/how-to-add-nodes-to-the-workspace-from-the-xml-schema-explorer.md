---
title: 'Gewusst wie: Hinzufügen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e1f5821d3a4207d89eb62b9344cff967c73b536
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752052"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Vorgehensweise: Hinzufügen von Knoten im Arbeitsbereich "" aus der XML-Schema-Explorer

In diesem Thema wird erläutert, wie zum Hinzufügen von Knoten, um die [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md) aus der **XML-Schema-Explorer**. Dies kann erreicht werden, per Drag & Drop von Knoten aus dem **XML-Schema-Explorer** ein XSD-Designer-Ansicht oder mithilfe der **XML-Schema-Explorer** Kontextmenü. Sie können auch hinzufügen, Knoten, die als Ergebnis einer Suche von hervorgehoben sind der **XML-Schema-Explorer**. Weitere Informationen finden Sie unter [wie: Hinzufügen von Set Search Ergebnis Schemaknoten zum Arbeitsbereich](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Nur globale Knoten hinzugefügt werden können, um die [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Zum Hinzufügen von Knoten über das Kontextmenü des XML-Explorer

1.  Führen Sie die Schritte in [Vorgehensweise: Erstellen und bearbeiten eine XSD-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Klicken Sie mit der rechten Maustaste auf die `PurchaseOrderType` Knoten in der XSD-Explorer. Wählen Sie **in Diagrammansicht anzeigen**.

     Der `purchaseOrderType`-Knoten wird auf der Entwurfsoberfläche der Diagrammansicht angezeigt.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>So verschieben Sie Knoten per Drag & Drop in eine Ansicht

1.  Mit der rechten Maustaste auf die `PurchaseOrderType` Knoten in der Diagrammansicht angezeigt. Wählen Sie **im XML-Schema-Explorer anzeigen**.

     Der Knoten wird hervorgehoben, der **XML-Schema-Explorer**.

2.  Klicken Sie mit der rechten Maustaste auf die `PurchaseOrderType` Knoten in der **XML-Schema-Explorer** , und wählen Sie **alle Verweise anzeigen**.

     Der `purchaseOrder`-Knoten wird hervorgehoben.

3.  Ziehen Sie den `purchaseOrder`-Knoten in die Diagrammansicht.

     Der `purchaseOrder`-Knoten und der `PurchaseOrderType`-Knoten werden nebeneinander auf der Entwurfsoberfläche der Diagrammansicht angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>So fügen Sie Knoten mithilfe der Suchfunktion des Schema-Explorers hinzu

1.  Geben Sie "PurchaseOrder" in das Suchfeld ein, der die [XML-Explorer](../xml-tools/xml-schema-explorer.md) Symbolleiste, und klicken Sie auf die Schaltfläche "Suchen".

     ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif)

     Die Suchergebnisse werden hervorgehoben, der **XML-Schema-Explorer** und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.

2.  Die Suchergebnisse dem Arbeitsbereich hinzufügen, indem Sie auf die **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** Schaltfläche im Bereich Zusammenfassung der Ergebnisse.

     ![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Die `purchaseOrder` Knoten und die `PurchaseOrderType` -Knoten werden nebeneinander auf der Entwurfsoberfläche der der [Diagrammansicht](../xml-tools/graph-view.md). Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)