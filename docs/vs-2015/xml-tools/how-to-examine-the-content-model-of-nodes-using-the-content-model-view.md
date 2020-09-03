---
title: 'Vorgehensweise: Untersuchen des Inhalts Modells von Knoten mithilfe der Inhalts Modell Ansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ddadcb0fbd772a5638bf6023b8cf6c18fbd270d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670855"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Gewusst wie: Untersuchen des Inhaltsmodells von Knoten in der Inhaltsmodellansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird das Untersuchen der Knoten in der [Inhaltsmodellansicht](../xml-tools/content-model-view.md) beschrieben.

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an

1. Erstellen Sie eine neue XML-Schemadatei.

2. Klicken Sie auf **XML-Editor verwenden, um die zugrunde liegende XML-Schema Datei in der Start Ansicht anzuzeigen und zu bearbeiten** .

3. Kopieren Sie den XML-Schema Beispielcode aus dem [Beispiel-XML-Schema: Bestell Schema](../xml-tools/sample-xsd-file-purchase-order-schema.md) , und fügen Sie ihn ein, um den Code zu ersetzen, der standardmäßig der neuen XSD-Datei hinzugefügt wurde.

4. Wählen Sie im `purchaseOrder` Schema-Explorer das Element aus, indem Sie im XML-Editor mit der rechten Maustaste `purchaseOrder` auf das Element klicken und **im XML-Explorer anzeigen**auswählen.

5. Klicken Sie im XML-Explorer mit der rechten Maustaste auf `purchaseOrder`, und wählen Sie **In Inhaltsmodellansicht anzeigen** aus.

     Das `purchaseOrder`-Element wird auf der Entwurfsoberfläche der Inhaltsmodellansicht angezeigt.

6. Erweitern Sie die Knoten `shipTo`, `billTo` und `items`, indem Sie auf jeden Knoten doppelklicken oder auf den Doppelpfeil rechts neben jedem Knoten klicken.

     Die Knoten des `purchaseOrder`-Elements werden jetzt erweitert, und Sie können das Inhaltsmodell des Elements sehen.

7. Klicken Sie auf einen Knoten unter dem `purchaseOrder`-Element, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.

8. Klicken Sie auf der XSD-Symbolleiste auf die Schaltfläche **Dokumentation anzeigen** , um die Dokumentation zu wechseln. Die Dokumentation kann auch über das Kontextmenü der Entwurfsoberfläche ein- und ausgeblendet werden.

9. Klicken Sie auf den `purchaseOrder` Knoten, und wählen Sie **Beispiel-XML generieren** aus, um das XML-Instanzdokument anzuzeigen.
