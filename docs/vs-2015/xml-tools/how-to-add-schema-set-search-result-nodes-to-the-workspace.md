---
title: 'Gewusst wie: Hinzufügen von Schema Satz-Suchergebnis Knoten zum Arbeitsbereich | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b34be331ad3ec67e2c3bd8d9ecc500cd256b1b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666553"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Gewusst wie: Hinzufügen von Knoten aus Schemaset-Suchergebnissen zum Arbeitsbereich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird erläutert, wie dem Arbeitsbereich Knoten hinzugefügt werden, die im XML-Schema-Explorer als Ergebnis einer Schlüsselwortsuche hervorgehoben sind.

> [!NOTE]
> Dem [Arbeitsbereich](../xml-tools/xml-schema-designer-workspace.md) können nur globale Knoten hinzugefügt werden.

 In diesem Beispiel wird das Beispiel-Bestell [Schema](../xml-tools/sample-xsd-file-purchase-order-schema.md)verwendet.

### <a name="to-add-schema-set-result-nodes"></a>So fügen Sie Knoten aus Ergebnissen einer Schemasetsuche hinzu

1. Befolgen Sie die Schritte unter Gewusst [wie: Erstellen und Bearbeiten einer XSD-Schema Datei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Geben Sie „purchaseOrder“ in das Suchtextfeld auf der [XML-Explorer](../xml-tools/xml-schema-explorer.md)-Symbolleiste ein, und klicken Sie auf die Suchschaltfläche.

     ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     Die Suchergebnisse werden im XML-Schema-Explorer hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.

3. Fügen Sie die Suchergebnisse dem Arbeitsbereich hinzu, indem Sie im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **Hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken.

     ![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     Der `purchaseOrder`-Knoten und der `PurchaseOrderType`-Knoten werden nebeneinander auf der Entwurfsoberfläche der [Diagrammansicht](../xml-tools/graph-view.md) angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.
