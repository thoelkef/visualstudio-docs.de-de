---
title: Hinzufügen von Suchergebnis Knoten für XML-Schema Sätze zum Arbeitsbereich
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2718c08b36ff9ef3ca8ae06f7d511cacb8fa73c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923653"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Vorgehensweise: Hinzufügen von Knoten aus Schemaset-Suchergebnissen zum Arbeitsbereich

In diesem Thema wird erläutert, wie Knoten, die im **XML-Schema-Explorer** hervorgehoben sind, als Ergebnis einer Schlüsselwort Suche im Arbeitsbereich hinzugefügt werden.

> [!NOTE]
> Dem [Arbeitsbereich](../xml-tools/xml-schema-designer-workspace.md)können nur globale Knoten hinzugefügt werden.

In diesem Beispiel wird das Beispiel-Bestell [Schema](../xml-tools/sample-xsd-file-purchase-order-schema.md)verwendet.

## <a name="to-add-schema-set-result-nodes"></a>So fügen Sie Knoten aus Ergebnissen einer Schemasetsuche hinzu

1. Befolgen Sie die Schritte [unter Gewusst wie: Erstellen und bearbeiten Sie eine XSD-](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)Schema Datei.

2. Geben Sie "PurchaseOrder" in das Such Textfeld der [XML-Explorer](../xml-tools/xml-schema-explorer.md) -Symbolleiste ein, und klicken Sie auf die Schaltfläche "suchen".

     ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif)

     Die Suchergebnisse werden im XML- **Schema-Explorer** hervorgehoben und auf der vertikalen Schiebe Leiste durch Ticks gekennzeichnet.

3. Fügen Sie die Suchergebnisse dem Arbeitsbereich hinzu, indem Sie im Zusammenfassungs Ergebnisbereich auf die Schaltfläche **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken

     ![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Der `purchaseOrder` Knoten und der `PurchaseOrderType` Knoten werden nebeneinander auf der Entwurfs Oberfläche der [Diagramm Ansicht](../xml-tools/graph-view.md)angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.