---
title: 'Vorgehensweise: Hinzufügen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f38760e6a04bd9e88fd4ff6e8c9d31f30ba27647
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783253"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Vorgehensweise: Hinzufügen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich

In diesem Thema wird erläutert, wie Sie zum Hinzufügen von Knoten der [XML-Schema-Designer-Arbeitsbereich](../xml-tools/xml-schema-designer-workspace.md) aus der **XML-Schema-Explorer**. Dies kann erreicht werden, per Drag & Drop von Knoten aus der **XML-Schema-Explorer** auf einer XSD-Designer-Ansicht oder über die **XML-Schema-Explorer** Kontextmenü. Sie können auch Knoten, die hervorgehoben werden, als Ergebnis einer Suche durch Hinzufügen der **XML-Schema-Explorer**. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Knoten aus Schema-Suchergebnissen zum Arbeitsbereich](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Nur globale Knoten hinzugefügt werden können, um die [XML-Schema-Designer-Arbeitsbereich](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Zum Hinzufügen von Knoten über das Kontextmenü des XML-Explorer

1. Führen Sie die Schritte in [Vorgehensweise: Erstellen und Bearbeiten einer XSD-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Klicken Sie mit der rechten Maustaste auf die `PurchaseOrderType` Knoten im XSD-Explorer. Wählen Sie **in Diagrammansicht anzeigen**.

     Der `purchaseOrderType`-Knoten wird auf der Entwurfsoberfläche der Diagrammansicht angezeigt.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>So verschieben Sie Knoten per Drag &amp; Drop in eine Ansicht

1. Mit der rechten Maustaste auf die `PurchaseOrderType` Knoten in der Diagrammansicht angezeigt. Wählen Sie **im XML-Schema-Explorer anzeigen**.

     Der Knoten wird hervorgehoben, der **XML-Schema-Explorer**.

2. Klicken Sie mit der rechten Maustaste auf die `PurchaseOrderType` Knoten in der **XML-Schema-Explorer** , und wählen Sie **alle Verweise anzeigen**.

     Der `purchaseOrder`-Knoten wird hervorgehoben.

3. Ziehen Sie den `purchaseOrder`-Knoten in die Diagrammansicht.

     Der `purchaseOrder`-Knoten und der `PurchaseOrderType`-Knoten werden nebeneinander auf der Entwurfsoberfläche der Diagrammansicht angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>So fügen Sie Knoten mithilfe der Suchfunktion des Schema-Explorers hinzu

1. Geben Sie "PurchaseOrder" in das Suchfeld ein, der die [XML-Explorer](../xml-tools/xml-schema-explorer.md) Symbolleiste, und klicken Sie auf die Schaltfläche "Suchen".

     ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif)

     In die Suchergebnissen hervorgehoben sind der **XML-Schema-Explorer** und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.

2. Die Ergebnisse der Suche zu Arbeitsbereich hinzufügen, indem Sie auf die **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** auf den Bereich auf die Schaltfläche.

     ![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Die `purchaseOrder` Knoten und die `PurchaseOrderType` -Knoten werden nebeneinander auf der Entwurfsoberfläche des der [Diagrammansicht](../xml-tools/graph-view.md). Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)