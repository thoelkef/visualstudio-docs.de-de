---
title: 'Vorgehensweise: Hinzufügen von Knoten aus Schema-Suchergebnissen zum Arbeitsbereich | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19157704019a949a4b2590ff277bcabd3bb320f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523601"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Gewusst wie: Hinzufügen von Knoten aus Schemaset-Suchergebnissen zum Arbeitsbereich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Hinzufügen Schemas legen Sie Knoten aus Suchergebnissen zum Arbeitsbereich](https://docs.microsoft.com/visualstudio/xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace).  
  
  
In diesem Thema wird erläutert, wie dem Arbeitsbereich Knoten hinzugefügt werden, die im XML-Schema-Explorer als Ergebnis einer Schlüsselwortsuche hervorgehoben sind.  
  
> [!NOTE]
>  Nur globale Knoten hinzugefügt werden können, um die [Arbeitsbereich](../xml-tools/xml-schema-designer-workspace.md).  
  
 Dieses Beispiel verwendet das Beispiel [Bestellungsschema](../xml-tools/sample-xsd-file-purchase-order-schema.md).  
  
### <a name="to-add-schema-set-result-nodes"></a>So fügen Sie Knoten aus Ergebnissen einer Schemasetsuche hinzu  
  
1.  Führen Sie die Schritte in [Vorgehensweise: Erstellen und Bearbeiten einer XSD-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Geben Sie "PurchaseOrder" in das Suchfeld ein, der die [XML-Explorer](../xml-tools/xml-schema-explorer.md) Symbolleiste, und klicken Sie auf die Schaltfläche "Suchen".  
  
     ![XML-Schema-Explorer-Schlüsselwortsuche](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Die Suchergebnisse werden im XML-Schema-Explorer hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.  
  
3.  Die Ergebnisse der Suche zu Arbeitsbereich hinzufügen, indem Sie auf die **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** auf den Bereich auf die Schaltfläche.  
  
     ![XML-Schema-Explorer-Suchergebnis](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Die `purchaseOrder` Knoten und die `PurchaseOrderType` -Knoten werden nebeneinander auf der Entwurfsoberfläche des der [Diagrammansicht](../xml-tools/graph-view.md). Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.



