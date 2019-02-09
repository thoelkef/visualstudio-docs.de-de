---
title: Hinzufügen von Knoten aus XML-Schema-Suchergebnissen zum Arbeitsbereich
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7cb8e66292a1cdb393401d180bd8b9f8691dc8f0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913927"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Vorgehensweise: Hinzufügen von Knoten aus Schema-Suchergebnissen zum Arbeitsbereich

In diesem Thema wird erläutert, wie zum Hinzufügen von Knoten, die in hervorgehoben sind der **XML-Schema-Explorer** als Ergebnis einer Schlüsselwortsuche im Arbeitsbereich.

> [!NOTE]
> Nur globale Knoten hinzugefügt werden können, um die [Arbeitsbereich](../xml-tools/xml-schema-designer-workspace.md).


 Dieses Beispiel verwendet das Beispiel [Bestellungsschema](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>So fügen Sie Knoten aus Ergebnissen einer Schemasetsuche hinzu

1.  Führen Sie die Schritte in [Vorgehensweise: Erstellen und Bearbeiten einer XSD-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Geben Sie "PurchaseOrder" in das Suchfeld ein, der die [XML-Explorer](../xml-tools/xml-schema-explorer.md) Symbolleiste, und klicken Sie auf die Schaltfläche "Suchen".

     ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif)

     In die Suchergebnissen hervorgehoben sind der **XML-Schema-Explorer** und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.

3.  Die Ergebnisse der Suche zu Arbeitsbereich hinzufügen, indem Sie auf die **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** auf den Bereich auf die Schaltfläche.

     ![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Die `purchaseOrder` Knoten und die `PurchaseOrderType` -Knoten werden nebeneinander auf der Entwurfsoberfläche des der [Diagrammansicht](../xml-tools/graph-view.md). Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.