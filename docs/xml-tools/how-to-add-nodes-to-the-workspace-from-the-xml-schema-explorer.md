---
title: Hinzufügen von Knoten aus dem XML-Schema-Explorer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2049b8da1caa4e0af0afc52aec6e75f499d85b8b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592814"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Vorgehensweise: Hinzufügen von Knoten zum Arbeitsbereich aus dem XML-Schema-Explorer

In diesem Thema wird erläutert, wie Knoten im **XML-Schema-Explorer**zum [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md) hinzugefügt werden. Dies kann erreicht werden, indem Sie Knoten aus dem **XML-Schema-Explorer** in eine XSD-Designer-Ansicht ziehen und ablegen oder indem Sie das Kontextmenü des **XML-Schema-Explorers** verwenden. Sie können auch Knoten hinzufügen, die als Ergebnis einer Suche hervorgehoben sind, die vom **XML-Schema-Explorer**ausgeführt wird. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Schema Satz-Suchergebnis Knoten zum Arbeitsbereich](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Dem [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md)können nur globale Knoten hinzugefügt werden.

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>So fügen Sie Knoten über das Kontextmenü des XML-Explorers hinzu

1. Befolgen Sie die Schritte unter Gewusst [wie: Erstellen und Bearbeiten einer XSD-Schema Datei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Klicken Sie im XSD-Explorer mit der rechten Maustaste auf den Knoten `PurchaseOrderType`. Wählen Sie **in Diagramm Ansicht anzeigen aus**.

     Der `purchaseOrderType`-Knoten wird auf der Entwurfsoberfläche der Diagrammansicht angezeigt.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>So verschieben Sie Knoten per Drag &amp; Drop in eine Ansicht

1. Klicken Sie mit der rechten Maustaste auf den Knoten `PurchaseOrderType` in der Diagramm Ansicht. Wählen Sie **im XML-Schema-Explorer anzeigen aus**.

     Der Knoten wird im XML- **Schema-Explorer**hervorgehoben.

2. Klicken Sie mit der rechten Maustaste auf den Knoten `PurchaseOrderType` im **XML-Schema-Explorer** , und wählen Sie **alle Verweise anzeigen**.

     Der `purchaseOrder`-Knoten wird hervorgehoben.

3. Ziehen Sie den `purchaseOrder`-Knoten in die Diagrammansicht.

     Der `purchaseOrder`-Knoten und der `PurchaseOrderType`-Knoten werden nebeneinander auf der Entwurfsoberfläche der Diagrammansicht angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>So fügen Sie Knoten mithilfe der Suchfunktion des Schema-Explorers hinzu

1. Geben Sie "PurchaseOrder" in das Such Textfeld der [XML-Explorer](../xml-tools/xml-schema-explorer.md) -Symbolleiste ein, und klicken Sie auf die Schaltfläche "suchen".

     ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif)

     Die Suchergebnisse werden im XML- **Schema-Explorer** hervorgehoben und auf der vertikalen Schiebe Leiste durch Ticks gekennzeichnet.

2. Fügen Sie die Suchergebnisse dem Arbeitsbereich hinzu, indem Sie im Zusammenfassungs Ergebnisbereich auf die Schaltfläche **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken

     ![Suchergebnis des XML-Schema-Explorers](../xml-tools/media/schemaexplorersearchresult.gif)

     Der Knoten `purchaseOrder` und der Knoten `PurchaseOrderType` werden auf der Entwurfs Oberfläche der [Diagramm Ansicht](../xml-tools/graph-view.md)nebeneinander angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)
